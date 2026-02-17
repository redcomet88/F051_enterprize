# F051 vue+flask企业债务舆情风险预测分析系统

> 完整项目收费，可联系QQ: 81040295 微信: mmdsj186011 注明从github来的，谢谢！
也可以关注我的B站： 麦麦大数据 https://space.bilibili.com/1583208775
> 

关注B站，私信获取！   [麦麦大数据](https://space.bilibili.com/1583208775)
编号:  F051
## 视频

[video(video-1P6YsgOS-1766205542853)(type-csdn)(url-https://live.csdn.net/v/embed/506547)(image-https://i-blog.csdnimg.cn/img_convert/70a104c02c5861d4fcb12942d982d799.jpeg)(title-F051-企业债务分析系统解说)]

## 1 系统简介
系统简介：本系统是一个基于Vue+Flask+MySQL构建的企业债务舆情风险预测分析系统。其核心功能围绕企业债务信息的采集、处理、分析与可视化展示，通过自然语言处理（NLP）和机器学习模型实现对公开舆情数据中企业债务风险的自动识别与预警。主要功能模块包括：企业信息管理、舆情数据采集与清洗、风险评分计算、风险趋势预测、可视化展示、用户权限管理等。
## 2 功能设计
该系统采用前后端分离的B/S架构模式，基于Vue.js + Flask + MySQL技术栈实现。前端通过Vue.js框架搭建响应式界面，结合Element UI组件库提供友好的用户交互体验，使用Vue-Router进行页面路由管理，Axios实现与后端的异步数据交互。Flask后端负责构建RESTful API服务，通过Blueprint组织模块结构，利用SQLAlchemy操作MySQL数据库存储企业信息、舆情数据、风险评分与预测结果等结构化数据，PyMySQL作为MySQL驱动支持。

在**舆情风险预测**功能方面，系统采用基于BERT的文本分类模型进行情感分析与风险识别，结合LSTM时序模型对债务舆情趋势进行预测，实现对企业债务风险的动态评估。
### 2.1 系统架构图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5a5d633fb8504c729be73f919bd2fc7f.png)

说明：系统整体分为三层——
- **前端展示层**：Vue.js构建可视化界面，负责用户交互与数据展示。
- **业务逻辑层**：Flask提供API接口，调用NLP模型与预测算法，完成数据处理与业务逻辑。
- **数据存储层**：MySQL数据库存储实体数据，包括企业基本信息、舆情语料、风险评分、用户信息等。

### 2.2 功能模块图
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2c048c5f55e04f35a7f0f21a15e773fc.png)
主要功能模块有：
1. 企业信息管理
2. 舆情数据采集与预处理
3. 债务风险智能评分
4. 风险趋势预测分析
5. 可视化仪表盘展示
6. 用户权限与登录注册
7. 个人设置与消息通知

## 3.1 登录 & 注册
登录注册做的是一个可以切换的登录注册界面，点击“去登录”或“去注册”可切换对应页面。
登录需要输入用户名和密码，系统后台对用户身份进行验证，通过后跳转至系统主界面。
注册功能允许新用户创建账号，需提供邮箱、用户名、密码等基本信息，并完成邮箱验证以确保账户真实性。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/892ff24a70b242d6909e80021c38474d.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8a70512de1a2482097a8e9902fb547e5.png)
## 3.2 企业信息查询
企业信息管理模块用于维护企业基本信息，如企业名称、统一社会信用代码、行业类别、所在地区、注册资本等。用户可通过该模块进行企业信息的添加、查询、修改与删除操作。管理员还可导出企业信息为Excel文件，用于外部数据分析。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/0688aaf34539415795203cf4bf49dce6.png)
## 3.3 舆情数据采集与预处理
系统通过爬虫程序定期从新闻网站、社交媒体平台等渠道抓取企业相关的公开舆情数据。采集的数据包含文章标题、正文、发布时间、来源等信息。前端通过Vue调用Flask接口触发爬虫任务，爬虫将数据存储于MySQL数据库，并通过文本清洗（去除HTML标签、停用词、分词处理）预处理，为后续分析做准备。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a5fc1caa695745d8a72407d4193603ef.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/69e6a297ada043a0adc14e2cf7127152.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/8930a5b69f3c4afaa818f13e8b22f1eb.png)

## 3.4 债务风险智能评分
系统利用NLP技术对清洗后的舆情文本进行情感分析和主题识别，判断内容是否与企业债务相关，并据此生成每条舆情的风险指数。结合BERT模型进行语义分类，综合历史舆情数据，最终计算出企业的总债务风险评分，分为低、中、高三个等级，便于用户快速评估。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/45bbe325a4b24a0596499891690f63cb.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/262bf59ff1b145afada9c5eefe620770.png)

## 3.5 风险趋势预测分析
基于时间序列分析方法（如LSTM神经网络），系统对历史舆情风险评分进行建模，预测未来一段时间内企业债务风险的变化趋势。通过训练模型识别出风险上升或下降的潜在信号，为风险预警提供科学依据。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/4f5f74f8ac794557a128ae3fa3699f68.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/5b5f26d980b949a5823c3f68ac00b1e7.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/a890e840fea94bcc9f64aa1eff3a7b3c.png)

## 3.6 可视化仪表盘展示
系统提供数据可视化功能，通过ECharts图表展示企业债务风险评分变化折线图、风险分布饼图、舆情热点词云图、预测趋势图等，帮助用户直观理解风险演化过程。用户可根据时间范围、企业名称等条件筛选数据，实现个性化分析。

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ce1c99c5a57b42169715223c4eb8a212.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ed533e7149df4331be71507a3bae89d5.png)
## 3.7 个人设置
个人设置方面包含了用户信息修改、密码修改功能。
用户信息修改中可以上传头像，完成用户的头像个性化设置，也可以修改用户其他信息，如昵称、邮箱等。
修改密码需要输入用户旧密码和新密码，验证旧密码成功后，就可以完成密码修改。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/01ec83e753b040e39a769a6d52733e04.png)

## 3.8 模型训练与知识图谱构建
后端通过Python脚本（如图中所示的“图谱生成程序”）对处理后的数据进行知识图谱构建，将企业、事件、关联实体等抽象为图结构。同时，支持用户在后台触发模型重新训练（如更新BERT分类器或LSTM预测模型），以提升预测精度。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2c1e9dbd3ac9445b87bb4dc85da74243.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/77d5a8ade51f48918bc242053aba8359.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/329296206dbf4820b497e9dbbba154e5.png)
## 3.9 词云分析
系统通过知识图谱技术，将企业债务相关的关键词、事件、人物、地点等关联起来，形成结构化知识网络。词云图展示高频出现的债务相关词汇，帮助用户快速定位关注点。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ef84f3656af34829ba22952bc6b829e4.png)

## 4 程序核心算法代码
### 4.1 代码说明
代码介绍：系统核心算法包括舆情文本分类与风险预测两部分。
- **文本分类**：使用Hugging Face Transformers库中的BERT模型，对舆情文本进行二分类（风险/非风险），并给出风险概率。
- **趋势预测**：运用LSTM模型对连续时间点的债务风险评分进行建模，预测未来风险走向。

### 4.2 流程图

（此处插入核心算法流程图）

### 4.3 代码实例

```python
# 使用BERT进行文本分类的示例代码
from transformers import AutoTokenizer, AutoModelForSequenceClassification
import torch

# 加载预训练模型
model_name = "bert-base-chinese"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=2)

# 预处理输入文本
text = "某企业因债务违约被法院强制执行"
inputs = tokenizer(text, return_tensors="pt", truncation=True, padding=True)

# 预测
with torch.no_grad():
    outputs = model(**inputs)
    predictions = torch.argmax(outputs.logits, dim=-1)

print("风险预测结果:", "高风险" if predictions.item() == 1 else "低风险")
```

```sql
-- 创建企业信息表
CREATE TABLE enterprises (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    credit_code VARCHAR(50) UNIQUE,
    industry VARCHAR(50),
    region VARCHAR(50),
    capital DECIMAL(10,2),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- 创建舆情数据表
CREATE TABLE舆情_data (
    id INT PRIMARY KEY AUTO_INCREMENT,
    enterprise_id INT,
    title TEXT,
    content TEXT,
    source VARCHAR(100),
    publish_time DATETIME,
    risk_score FLOAT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (enterprise_id) REFERENCES enterprises(id)
);
```

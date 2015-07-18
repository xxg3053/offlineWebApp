# offlineWebApp
离线的web app *Web App = html5 + css3 + javascript*

## study

* Application Cache是实际操作
* Local Storage和Web Sql 的用法
* 一个离线的web app框架

#### HTML5提供的数据持久化技术

+ Application Cache 
	本地缓存应用所需的文件
+ Local Storage & Session Storage
	键值对（key - value）存储数据
+ Web SQL
	关系数据库，通过sql访问
+ IndexDB
	索引数据库(也是通过键值对存储，数据量大，查询更快) 

#### Web SQL

+ 浏览器的本地数据库， 占用资源少、处理速度快
+ 三个核心方法
	* openDatabase:使用现有数据库或者新建
	* transaction: 事务提交或回滚
	* executeSql: 执行真实的sql查询


## 实战

* 目标：
	+ 将一个Rss新闻阅读应用改造为IOS离线App
* 提纲：
	+ 新闻阅读器的架构
	+ 代码分析
	+ 改造案例
	+ 代码修改讲解

### 功能介绍
+ 读取服务器的RSS
+ 将文章显示在主页上
+ 点击标题打开文章详情页
+ 返回主页
+ 刷新新闻

### MVC设计模式

* 控制器 Controller
	* 定义程序行为
	* 将用户动作映射到模型
	* 更新视图
	+ applicationController.js
	+ articleController.js

* 模型 Model
	* 保存数据
	* 封转数据操作
	* 通知控制器更新数据
	+ article.js
	+ database.js

* 视图 View
	* 显示模型
	* 接受用户输入
	* 将用户输入发送给控制器
	+ templates.js
	+ css文件

#### 代码

* index.html
	* 显示加载信息
	* 引入css文件
	* 引入js文件
		* jquery 框架
		* 应用代码
		* DomReady 程序入口
		* 启动App

* templates.js
	* applaction() 应用标题
	* home() 回到主页面
	* articleList() 文章列表
	* article() 文章详情
	* articleLoading() 加载提示

* applicationcontroller.js
	* start() 启动程序
		* 绑定事件
		* 显示主页面
	* route() 控制列表和文章之间的切换

* articlesscontroller.js
	* showArticleList() 显示文章列表
	* showArticle() 显示文章
	* synchronizeWithServer() 获取最新文章

* article.js
	* insertArticle() 保存
	* deleteArticle() 删除
	* 查询
		* selectBasicArticle() 文章列表
		* selectFullArticle() 单片文章

* database.js
	* 提供访问数据库的基本功能

#### 将应用离线化

* 第一步：manifest文件
* 第二步：判断离线状态
	* navigator && navigator.online
* 第三步：读取离线资源

#### IOS Web App 定制

>		`<meta name="apple-mobile-web-app-capable" content="yes" />`
		`<meta name="apple-touch-fullscreen" content="yes">`
		`<link rel="apple-touch-icon" href="icon.png" >`

#### 案例

FT中文网 [http://m.ftchinese.com/phone.html](http://m.ftchinese.com/phone.html)



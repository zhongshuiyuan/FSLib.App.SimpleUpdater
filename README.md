SimpleUpdater.NET
=======================

##简要说明

在发布应用程序时，我们经常会需要给自己的程序加上自动升级功能。.Net Framework自带的ClickOnce中有自动升级的功能，但是往往不太好用，比如必须用ClickOnce发布，安装的文件夹一个版本一个等等，我们会想要一个比较简单、甚至绿色软件也能使用的自动升级功能，这个自动升级程序就是基于这个目的而制作的。

 

为了让使用起来更加简单快捷，我对内置的功能进行了大幅度的精简和集成，最简单的情况下只需要你只需要一行代码即可实现自动更新，如下所示：

```c#
FSLib.App.SimpleUpdater.Updater.CheckUpdateSimple("http://localhost/update.xml");
```

内含测试项目&手册，更多信息请参阅下载分发包里的手册。

##发布和支持信息

###软件发布主页 [http://www.fishlee.net/soft/simple_autoupdater/](http://www.fishlee.net/soft/simple_autoupdater/)
反馈意见建议 [http://bbs.fishlee.net/](http://bbs.fishlee.net/)


##更新记录

### 4.2.0.0 [2015年6月27日]

####以下为客户端更新
* 增加组件ID检测事件
* 增加同步检测更新以及任务检测更新方式
* 增加“不存在则跳过”的文件更新逻辑
* 修正下载时进度显示的bug
* 变更当前主程序模块以及信息监测方式
* 变更行为，最低版本达不到要求也视作错误
* 部分逻辑调整，提升特定情况下检测更新的速度

####以下为打包工具更新
* 加入组件ID支持
* 变更文件列表编辑方式，新增组件ID编辑以及“不存在则跳过”逻辑
* 新增打包选项，支持使用随机包名
* 新增打包前清空目标目录的选项

### 4.0.0.0 [2015年05月07日]

* 【客户端】增加自定义引用接口 IUpdateNotify 以及 UsingAssembly() 函数，可在正式更新后依然调用自己的处理事件
* 【客户端】增加 UsingFormUI() 函数以及更新对话框基类，可以使用自己的更新界面完全替换内置界面
* 【客户端】修改WebClient初始化流程，避免后续下载包时发出的请求没有UserAgent标头
* 【客户端】修正丢失的资源文件，避免导致命令行版无法使用
* 【客户端】变更config文件配置
* 【客户端】安装文件各操作中也支持报告进度

### 3.3.1.0 [2015年04月28日]
* 【客户端】修正在根目录下更新会导致出错的BUG
* 【客户端】修正当更新信息设置为显示网页时有时可能会报ActiveX初始化异常的BUG
* 【包工具】修正当输入最小版本号不正确时没做检查导致客户端出错的BUG

###3.3.0.0 (包工具) [2015年02月07日]

* 修改升级包生成的文件名编码为UTF-8，避免在语言代码不同的系统上出现乱码


###3.0.14290.0 [2014年10月19日]

* 【客户端】升级包支持“不提示直接自动启动升级”选项
* 【客户端】升级包支持“自动结束进程”选项
* 【客户端】升级包支持“自动结束同目录下进程”选项
* 【客户端】升级包支持“强制更新否则退出软件选项”选项
* 【客户端】升级包支持“启动更新后自动解除当前进程”选项
* 【客户端】升级包支持“检测遇到错误时是否按照有更新处理”选项
* 【客户端】自动升级不再强制要求管理员权限，改为自动检测，仅在需要时才请求管理员权限
* 【客户端】升级文件安装逻辑，降低因文件安装速度过快导致出错的失败率
* 【客户端】增加多服务器支持，允许使用多个服务器地址进行更新，失败后自动切换服务器
* 【客户端】增加确保更新函数，支持在确保是最新版的情况下才继续运行
* 【客户端】多国语言资源完善
* 【客户端】其它细节调整和BUG修复
* 【包工具】增加对新增选项的支持，修复已知BUG


###2.3.8.21 [2014年7月5日]

* 支持在正式更新前Ping请求到指定地址（统计）
* 更新界面更新
* 细节更新
* 代码重构

###2.3.9 [2014年7月18日]

* 【包工具】 修正就算没有指定/build命令行的时候依然会自动构建的BUG
* 【包工具】 修正因为转短路径后因为出现了“..”导致的异常
* 【包工具】 短路径为空的时候（同级目录）显示为“.\”而不是空白。
* 【包工具】 当打开项目的时候，如果已经绑定了信息文件，则自动重新读取
* 【包工具】 增加默认更新模式选项，当没有为文件指定更新模式的时候，自动使用项目默认


###2.3.8.21 [2014年7月5日]

* 完全重构
* 支持命令行模式，支持命令行打开项目
* 支持命令行指定构建参数直接构建更新项目
* 支持三种模式构建以及无提示构建项目
* 支持绑定版本信息到指定文件，避免每次需要手动修改版本
* 支持绑定更新说明到指定文件，避免每次都需要手动更新说明
* 项目文件重新设计，不受文件位置移动的影响
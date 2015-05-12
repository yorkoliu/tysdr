SDR1.0(SHELL+Dialog+RSA)Linux主机集中式管理平台

## 系统特点 ##
### 安全性 ###
管理系统具有很好的安全性，通过2048位RSA密钥进行监控服务器与被监控服务器的认证，可以省去输入繁琐和易泄露的密码。系统管理员只要对主监控服务器做好安全配置并保管好私钥即可，被监控服务器外网远程终端默认将会被关闭，系统会定期扫描被监控服务器内/外网安全情况，生成分析结果给管理员。系统管理员可以定期更换公钥、私钥来提高安全系数。登录监控平台需要密码(perl pack加密)认证，每个操作窗口都加入会话认证，整个系统编译后的文件都是以二进制方式存放。

### 智能化 ###
监控服务器会根据被监控服务器上的应用部署相应的代理客户端，由代理客户端来检查、监控、分析本服务器的状态，分析结果将通过邮件、WEB、短信通知给系统管理员。让管理员不间隔了解到服务器的状态信息，代理客户端同时也具备管理本服务器应用的权力，当应用发生故障时它会自我修复并通知管理员。

### 易用性 ###
系统是基于Linux shell模式下的对话框展示，中文环境，同时也支持鼠标操作，功能清晰明了，操作时系统也会提示相应的文字提示，非常简单。

### 高效率 ###
新上架的服务器只要进行如下三步即可上线提供服务，即添加服务器->初始化->部署应用。如果要在多台服务器上进行一样的操作，只要选择好操作事件跟操作对象就可以了。

### 灵活性 ###
升级被监控服务器上的对象很方便，只要在监控服务器上更新好相应对象代码，系统会自动到被监控服务器上去更新它们。

### 可扩展性 ###
系统提供的高级应用功能，其它同事也可以编写自己的模块，根据不同应用可以定制不同的功能模块，系统提供这样的接口。

## 系统网络架构图 ##
> <img src='http://blog.liuts.com/attachment/201008/1280717550_622123be.gif'>
<h2>系统流程图</h2>
<blockquote><img src='http://blog.liuts.com/attachment/201008/1280719871_618455a0.jpg'>
<h2>系统主界面</h2>
<img src='http://blog.liuts.com/attachment/201008/1280717550_27996d5d.png' width='600'>
<h2>系统主要功能</h2>
</blockquote><blockquote>SDR1.0是基于Linux bash shell+mysql+python+mod_perl工具开发，功能覆盖了Linux常用常用操作，下面详细介绍系统主要功能：<br>
系统目录结构<br>
/<br>
│  add_firewall        添加防火墙<br>
│  add_server        添加服务器<br>
│  add_app          部署应用<br>
│  add_agent        部署代理<br>
│  authorized_keys      公钥<br>
│  checkonline        登录验证<br>
│  config          配制文件<br>
│  c_server_class        多选服务器列表<br>
│  go            登录<br>
│  identity          私钥<br>
│  list_server_do        选择服务器<br>
│  list_server_info      服务器信息<br>
│  main          功能选择<br>
│  msgbox          提示信息<br>
│  r_server_class        单选服务器<br>
├─tyapp          应用安装脚本<br>
│<br>
├─bin<br>
│      nohup.out        tmpfile<br>
│      syslog2mysql.sh      syslogs to mysql shell<br>
│      TyserverScan      服务器端口扫描(外网)<br>
│<br>
├─cron<br>
│      TyserverwebScan      验证WEB状态主程序<br>
│<br>
├─document<br>
│      document.txt      开发文档<br>
│<br>
├─key<br>
│      identitybak        old key<br>
│<br>
├─logs          系统操作日志目录<br>
├─tyagent          代理程序目录<br>
└─tysysadmin        前端cgi-bin目录<br>
<blockquote>├─cgi-bin<br>
│      config.pl<br>
│      index.cgi            模块入口程序<br>
│      sendmail.cgi                  邮件报警接口<br>
│<br>
├─css<br>
│      style.CSS<br>
│<br>
├─js<br>
│      copyright.js<br>
│<br>
└─modules<br>
<blockquote>└─Apache<br>
<blockquote>ServerLoglist.pm  服务器日志列表<br>
ServerScanport.pm  服务器端口扫描<br>
ServerScanweb.pm  服务器状态扫描<br>
<br>
<a href='http://blog.liuts.com/post/210/'>更多>>></a><br>
BLOG：<a href='http://blog.liuts.com'><a href='http://blog.liuts.com'>http://blog.liuts.com</a></a><br>
微博：<a href='http://t.qq.com/yorkoliu'><a href='http://t.qq.com/yorkoliu'>http://t.qq.com/yorkoliu</a></a><br>
交流QQ群：158926355
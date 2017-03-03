#git 的安装及源代码上传
#####首先去官网把git下载好，这里给大家提供个官网下载地址
https://git-scm.com/downloads
######安装完成后，在开始菜单里找到“Git”->“Git Bash”，弹出一个类似命令行窗口的东西，就说明Git安装成功！
#####安装完成后，还需要最后一步设置，在命令行输入：
``` js
 git config --global user.name "wanghongze1" //这里要填写你的用户名，设置提交人姓名
 git config --global user.email "1739392839@qq.com"  //这里要填写你的名字，设置提交人邮箱
 ```
 大家刚开始使用之前都配置了一个全局的用户名和邮箱；如果你公司的项目是放在自建的gitlab上面, 如果你不进行配置用户名和邮箱的话, 则会使用全局的, 这个时候是错误的, 正确的做法是针对公司的项目, 在项目根目录下进行单独配置用户名和邮箱.
``` js
 git config user.name "yours Name"
 git config user.email "gitlab@xx.com"
 git config --list
```
 git config --list查看当前配置, 在当前项目下面查看的配置是全局配置+当前项目的配置, 使用的时候会优先使用当前项目的配置
##源代码上传
####1.创建仓库
``` js
 mkdir testgit
 cd testgit
 pwd  //pwd命令用于显示当前目录
/Users/michael/testgit
```
####2.生成公钥
``` js
ssh-keygen -C '1739392839@qq.com' -t rsa  //这里的邮箱要换成你自己的
```
生成公钥后找到对应路径C:\Users\王宏泽\.ssh，如图
![](img\git1.png)
id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
接下来 登录github,打开” settings”中的SSH Keys页面，然后点击“Add SSH Key”,填上任意title，在Key文本框里黏贴id_rsa.pub文件的内容。
![](img\git3.jpg)
点击 Add Key，你就应该可以看到已经添加的key

####3.添加远程库
登录github上，然后在右上角找到“create a new repo”创建一个新的仓库。如图
![](img\git2.jpg)
在Repository name填入testgit，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库
目前，在GitHub上的这个testgit仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。
####4.上传源代码
``` js
git init  //在本地的项目根目录初始化一个Git仓库
git add *  //添加文件到Git仓库,可以是单文件，也可以是多文件
git commit -m "第一次提交"   //接着提交和备注，更改后常用
git remote add origin https://github.com/wanghongze1/testgit.git  //通过Git远程添加到仓库源
git push -u origin master   //上传本地当前分支代码到master分支，更改后常用
```
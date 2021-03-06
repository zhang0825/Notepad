# 1 Git的历史
Git的诞生来源于Linux系统的诞生，为了更好的管理代码，需要一个版本控制系统来管理和维护代码，因此Git由此诞生。
## 版本控制
版本控制（Revision control）是一种在开发的过程中用于管理我们对文件、目录、或工程等内容的修改历史，方便直接查看更改历史记录，备份以便恢复以前的版本的软件工程技术，简单说就是用于管理多人协同开发项目的技术。  
### 本地版本控制
记录文件每次的更新，可以对每一个版本做一个快照，或是记录补丁文件，适合个人用，如RCS.  
### 集中式版本控制
所有的版本数据都保存在服务器上，协同开发者从服务器上同步更新或上传自己的修改。所有的版本数据都存在服务器上，不联网就无法更新。    
### 分布式版本控制
所有的版本信息仓库全部同步到本地的每个用户，这样就可以在本地查看所有版本历史，可以离线在本地提交，只需在连网时push到相应的服务器或其他用户那里。由于每个用户保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，但增加了本地存储空间的占用。  
# 2 Git与Svn的对比
## 2.1 Svn
Svn是一个集中式版本控制系统，版本库是集中放在服务器上的，工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己做完的活推到中央服务器上。集中式版本控制系统必须联网才能工作，对网络带宽要求较高。
## 2.2 Git
Git是一个分布式版本控制系统，不需要服务器集中管理，每个人的电脑就是一个完美的版本库，通过本地仓库来管理本地代码，实现一个闭环过程，通过远程仓库来实现代码共享。  
### Git是目前世界上最先进的分布式版本控制系统。  
### Git Bash
Unix与Linux风格的命令行
### Git CMD
Windows风格的命令行
### Git GUI
图形界面的Git，不建议使用，尽量先熟悉常用命令。
# 3 基本的Linux命令学习
> * cd :改变目录  
> * cd.. :回退到上一个目录，直接cd进入默认目录  
> * pwd :显示当前所在的目录路径  
> * ls(ll) :都是列出当前目录中的所有文件，只不过ll(两个ll)列出的内容更为详细。  
> * touch :新建一个文件，如touch index.js就会在当前目录下新建一个index.js文件。  
> * rm :删除一个文件，rm index.js就会把index.js文件删除。  
> * mkdir :新建一个目录，就是新建一个文件夹。  
> * rm -r :删除一个文件夹，rm -r src 删除src目录。  
> * rm -rf / 切勿在Linux中尝试！删除电脑中全部文件。  
> * mv :移动文件，mv index.html src ,index.html是我们要移动的文件，src是目标文件夹，可以将目标文件移动到目标文件夹。  
> * reset : 重新初始化终端/清屏。  
> * clear :清屏。  
> * history :查看命令历史。  
> * help :帮助。  
> * exit :退出。  
> * \# :表示注释。 
# 4 Git配置
### 所有的配置文件，其实都保存在本地！
## 查看不同级别的配置文件
* 查看全局配置：`git config -l`  
* 查看系统配置：`git config --system --list`  
* 查看当前用户配置：`git config --global --list`  
## Git相关的配置文件
> * `Git\etc\gitconfig` :Git安装目录下的gitconfig   --system 系统级  
> * `C\Users\Administrator\.gitconfig` :只适用于当前登录用户的配置  --global 全局  
## 设置用户名与邮箱（用户标识，必要）
安装Git后首先要做的事情是设置自己的用户名称和e-mail地址。因为Git每次提交都会使用该信息，它被永远的嵌入到了你的提交中：
> * `git config --global user.name "zhangleyuan"`  #名称  
> * `git config --global user.email zhangleyuan4@gmail.com`   #邮箱  
## 配置环境变量
> 在Path中设置：`D\Git\cmd`即可，大多数系统会自动添加，如果没有，加上即可。  
# 5 Git基本理论
## 工作区域
Git本地有三个工作区域 ：工作目录(working Directory)、暂存区(Stage/Index)、资源库(Repository或Git Directory).如果在加上远程的git仓库(Remote Directory)就可以分为四个工作区域。  
> * `Workspace` :工作区，就是自己平时存放项目代码的地方。  
> * `Index/Stage` : 暂存区，用于临时存放自己的改动，事实上它只是一个文件，保存即将提交到文件列表信息。  
> * `Repository` : 仓库区（或本地仓库），就是安全存放数据的位置，这里面有自己提交到所有版本的数据，其中HEAD指向最新放入仓库的版本。  
> * `Remote` : 远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换，如Github或Gitee.  
## 转换关系
* `working Directory---(git add files)---Stage/Index---(git commit)---History---(git push)---Remote Directory`  #本地到远程  
* `Remote Directory---(git pull)---History---(git reset)---Stage/Index---(git checkout)---working Directory`  #远程到本地  
## 工作流程
git的工作流程一般是这样的：  
> 1.在工作目录中添加、修改文件；
> 2.将需要进行版本管理的文件放入暂存区域；
> 3.将暂存区域的文件提交到git仓库。  
因此，git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交（committed）.  
# 6 Git项目搭建
## 创建工作目录与常用指令
工作目录（WorkSpace）一般就是你希望Git帮助你管理的文件夹，可以是你项目的目录，也可以是一个空目录，建议不要有中文。
### 日常使用只要记住下图6个命令：
* `add`
* `commit`
* `push`
* `pull`
* `fetch/clone`
* `checkout`  
## 本地仓库搭建
创建本地仓库的方法有两种：一种是创建全新的仓库，另一种是克隆远程仓库。  
1.创建全新的仓库，需要用Git管理的项目的根目录执行：  
> #在当前目录新建一个Git代码库  
> `git init`  
2.执行后可以看到，仅仅在项目目录多出了一个.git目录，关于版本等的所有信息都在这个目录里面。  
## 克隆远程仓库
1.另一种方式是克隆远程仓库目录，由于是将远程服务器上的仓库完全镜像一份至本地！  
> #克隆一个项目和它的整个代码历史（版本信息）  
> `git clone [url]`
# 7 Git文件操作
## 文件4种状态
版本控制就是对文件的版本控制，要对文件进行修改，提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的的文件，或者要提交的文件没提交上。  
* `Untracked` (未跟踪) : 未跟踪，此文件在文件夹中，但并没有加入到git库，不参与版本控制，通过 `git add` 状态变为 Staged.  
* `Unmodify` (未修改) : 文件已经入库，未修改，即版本库中的文件快照内容与文件夹中完全一致，这种类型的文件有两种去处，如果它被修改，而变为 `Modified` 。如果使用 `git rm` 移出版本库，则成为 `Untracked` 文件。  
* `Modified` (已修改) : 文件已修改，仅仅是修改，并没有进行其他的操作，这个文件也有两个去处，通过 `git add` 可进入暂存 `Staged` 状态，使用 `git checkout` 则丢弃修改过，返回到 `unmodify` 状态，
这个 `git checkout` 即从库中取出文件，覆盖当前修改。
* `Staged` (已暂存) : 暂存状态，执行 `git commit` 则将修改同步到库中，这时库中的文件和本地文件又变为一致，文件为 `Unmodify` 状态。执行 `git reset HEAD filename` 取消暂存，文件状态为 `Modified`.  
## 查看文件状态
上面说文件有四种状态，通过如下命令可以查看文件的状态：  
> #查看指定文件状态  
> `git status [filename]`  

> #查看所有文件状态  
> `git status`  

> #添加所有文件到暂存区  
> `git add . ` 

> #提交暂存区中的内容到本地仓库  -m  提交信息  
> `git commit -m "消息内容"`    
## 忽略文件
有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等。  
在主目录下建立"`.gitignore`"文件，此文件有如下规则：  
> 1.忽略文件中的空行或以井号（#）开始的行将会被忽略。  
> 2.可以使用Linux通配符，例如：星号（*\）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,... }）代表可选的字符串等。  
> 3.如果名称的最前面有一个感叹号（！），表示例外规则，将不被忽略。  
> 4.如果名称的最前面是一个路径分隔符（/）,表示要忽略的文件在此目录下，而子目录中的文件不忽略。  
> 5.如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。  
```
*.txt   #忽略所有.txt结尾的文件,这样的话上传就不会被选中！  
！lib.txt    #但lib.txt除外  
/temp   #仅忽略项目根目录下的TODO文件，不包括其他目录temp  
build/  #忽略build/目录下的所有文件  
doc/*.txt   #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```
# 8 Github配置SSH公钥及创建远程仓库
设置本机绑定SSH公钥，实现免密码登录！（免密码登录，这一步挺重要的，Github是远程仓库，我们是平时工作在本地仓库！）  
> #进入C：\Users，找到.ssh目录，如果没有，则新建一个！    
> #生成公钥：`ssh-keygen`   

将公钥信息public key添加到Github账户即可！  
使用Github创建一个自己的仓库！  
将Github上的仓库克隆到本地，远程仓库就创建完成了！

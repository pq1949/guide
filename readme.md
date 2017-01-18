### Git global setup
```
git config --global user.name "pq1949"
git config --global user.email "2305220598@qq.com"
```
检查你的设置(Checking Your Settings)
如果你想检查你的设置，你可以使用 git config --list 命令来列出Git可以在该处找到的所有的设置: 
`git config --list `
### Create Repository
```
mkdir sigtest
cd sigtest
git init
touch README
git add README
git commit -m 'first commit'
git remote add origin git@17.17.29.12:pq1949/sigtest.git
git push -u origin master
```
### Existing Git Repo?
```
cd existing_git_repo
git remote add origin git@17.17.29.12:pq1949/sigtest.git
git push -u origin master
```

### checkout
检出仓库
执行如下命令以创建一个本地仓库的克隆版本：
`git clone /path/to/repository `
如果是远端服务器上的仓库，你的命令会是这个样子：
```
git clone username@host:/path/to/repository
git clone git@17.17.29.12:pq1949/sigtest.git
git clone http://1.1.1.1/pq1949/sigtest.git
```

### add and commit 
你可以提出更改（把它们添加到暂存区），使用如下命令：
```
git add <filename>
git add *
```
这是 git 基本工作流程的第一步；使用如下命令以实际提交改动：
`git commit -m "代码提交信息"`
现在，你的改动已经提交到了 HEAD，但是还没到你的远端仓库。

### push
推送改动
你的改动现在已经在本地仓库的 HEAD 中了。执行如下命令以将这些改动提交到远端仓库：
`git push origin master`
可以把 master 换成你想要推送的任何分支。 

如果你还没有克隆现有仓库，并欲将你的仓库连接到某个远程服务器，你可以使用如下命令添加：
`git remote add origin <server>`
如此你就能够将你的改动推送到所添加的服务器上去了。

### tag
Git 中的tag指向一次commit的id，通常用来给开发分支做一个标记，如标记一个版本号。

打标签

`git tag -a v1.01 -m "Relase version 1.01"`
注解：git tag 是打标签的命令，-a 是添加标签，其后要跟新标签号，-m 及后面的字符串是对该标签的注释。

提交标签到远程仓库
`git push origin --tags`
注解：就像`git push origin master` 把本地修改提交到远程仓库一样，-tags可以把本地的打的标签全部提交到远程仓库。
指定提交的标签 `git push origin [tagname]` 
`git push origin v1.5`

删除标签
`git tag -d v1.01`
注解：-d 表示删除，后面跟要删除的tag名字
删除远程标签
`git push origin :refs/tags/v1.01`
注解：就像`git push origin :branch_1` 可以删除远程仓库的分支branch_1一样， 冒号前为空表示删除远程仓库的tag。
或者`git push origin --delete tag`
```
git push origin --delete v1.01 
```
查看标签
```
git tag
```
或者
```
git tag -l
```

### branch
分支是用来将特性开发绝缘开来的。在你创建仓库的时候，master 是“默认的”分支。在其他分支上进行开发，完成后再将它们合并到主分支上。


创建一个叫做“feature_x”的分支，并切换过去：
`git checkout -b feature_x`
切换回主分支：
`git checkout master`
再把新建的分支删掉：
`git branch -d feature_x`
除非你将分支推送到远端仓库，不然该分支就是 不为他人所见的：
`git push origin <branch>`
### update and merge
要更新你的本地仓库至最新改动，执行：
`git pull`
以在你的工作目录中 获取（fetch） 并 合并（merge） 远端的改动。
要合并其他分支到你的当前分支（例如 master），执行：
`git merge <branch>`
在这两种情况下，git 都会尝试去自动合并改动。遗憾的是，这可能并非每次都成功，并可能出现冲突（conflicts）。 这时候就需要你修改这些文件来手动合并这些冲突（conflicts）。改完之后，你需要执行如下命令以将它们标记为合并成功：
`git add <filename>`
在合并改动之前，你可以使用如下命令预览差异：
`git diff <source_branch> <target_branch>`
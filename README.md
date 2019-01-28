# gitskills

## 创建版本库
--------------------------------------------------

1. git init (创建仓库)
2. git add readme.txt (文件添加到仓库)
3. git commit -m 'add readme.txt' (文件提交仓库 -m 描述提交内容)
4. git status (查看仓库当前状态)
5. git diff readme.txt (对比修改前后文件内容)

## 版本回退
--------------------------------------------------
6. git log (查看提交的日志信息 commit id) --pretty=oneline (显示较少信息) 
7. git reset --hard HEAD^ (回退上个版本)  HEAD^^(回退2个版本) HEAD~100(回退100个版本) 
8. git reflog (记录每次版本)
``` $ git reflog
      e475afc HEAD@{1}: reset: moving to HEAD^
      1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
      e475afc HEAD@{3}: commit: add distributed
      eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```
9. git reset --hard commit_id (e475afc) 可以回退到未来版本

## 撤销修改

10. git checkout -- readme.txt (文件在工作区修改全部撤销，即还未add)
11. git reset HEAD readme.txt (已经add到暂存区的修改撤销，重新放回工作区)


## 删除文件
12. git rm readme.txt -> git commit -m 'delete readme file'
13. git checkout -- readme.txt (如果是rm readme.txt 可以通过checkout 恢复该文件)

## 远程仓库
``` 创建ssh key 
    ssh-keygen -t rsa -C "youremail@example.com"
	保存在 用户目录 .ssh/id_rsa和 id_rsa.pub
	cat id_rsa.pub 得到 字符串
	添加到 github 账号管理中的 ssh key
	保证了 只有本电脑可上传代码到 远程服务器
```

## 添加远程库
```
    先在github 创建仓库
    在本地仓库运行
	git remote add origin git@github.com:michaelliao/learngit.git
	下一步 就可以把本地库的所有内容推送到远程库上
	git push -u origin master
	把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
    此后，每次本地提交后，只要有必要，就可以使用命令git push origin master推送最新修改；
```
## 从远程库克隆
14. git clone git@github.com:michaelliao/gitskills.git


## 分支管理
1. 创建与合并分支

```  
   创建dev分支 然后切换 dev 分支
   -b 参数表示创建并切换
   git checkout -b dev
	或者
   git branch dev
   git checkout dev
   
   git branch查看分支   
   * dev
     master
   
   切换分支 
   git checkout dev|master
   
   分支提交远程仓库
   (先add commit)
   git pull origin dev(分支名)
   
   分支 dev 合并到 master
   (先切换到master)
   git merge dev
   
   删除分支
  git branch -d dev
  
  查看分支：git branch

  创建分支：git branch <name>

  切换分支：git checkout <name>

  创建+切换分支：git checkout -b <name>

  合并某分支到当前分支：git merge <name>

  删除分支：git branch -d <name> 
```


## 解决冲突
---- 手动编辑为需要内容 再提交

## 分支管理策略
````
    git merge --no-fo -m 'merge with no-ff' dev
	合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。
````
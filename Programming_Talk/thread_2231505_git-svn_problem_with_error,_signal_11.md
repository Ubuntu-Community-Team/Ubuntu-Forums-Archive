---
title: "git-svn problem with error, signal 11"
date: 2014-06-26
forum: Programming Talk
---

### Post by kuba-g on 2014-06-26
Hi all,

I use kubuntu 14.04. Recently, I have installed git-svn package which was working fine until today. Every time I use git svn I get something like this at the end of output:
```

$git svn rebase
......
......
First, rewinding head to replay your work on top of it...
Fast-forwarded master to refs/remotes/git-svn.
error: git-svn died of signal 11
$git svn rebase
Current branch master is up to date.
error: git-svn died of signal 11
$

```
The same error message goes for git svn dcommit. I've searched for answer on the internet, but nothing seems to fit. 
Thanks for help in advance!

---

### Post by spjackson on 2014-06-26
Signal 11 is SIGSEGV, i.e. it's crashing with a segmentation fault. It sounds somewhat like this bug [https://bugs.launchpad.net/ubuntu/+source/git/+bug/1252097](https://bugs.launchpad.net/ubuntu/+source/git/+bug/1252097) . However, someone has written "This seems to be fixed in Ubuntu 14.04." Perhaps you have a counter example.

---


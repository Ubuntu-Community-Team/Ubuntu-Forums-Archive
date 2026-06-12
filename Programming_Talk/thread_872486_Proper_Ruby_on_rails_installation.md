---
title: "Proper Ruby on rails installation"
date: 2008-07-28
forum: Programming Talk
---

### Post by aliov_85 on 2008-07-28
Hi

In order to complete the installation I'd like to install mysql, but I'm having some issues.

> sudo apt-get install libmysql-ruby mysql-server

I got the following error:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmysql-ruby

I'm on Feisty Fawn

Thanks in advance for any help

---

### Post by henchman on 2008-07-28
hello!

as [http://packages.ubuntu.com/feisty/libmysql-ruby](http://packages.ubuntu.com/feisty/libmysql-ruby) states, the package is available for feisty in the universe repos :)

did you enable your universe repositories? if not or unsure, open /etc/apt/sources.list in your favourite editor and see if the lines 

```

deb http://de.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty universe
deb http://de.archive.ubuntu.com/ubuntu/ feisty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ feisty-updates universe

```

are uncommented (have a # in front of them). if so, remove it.

have a nice day :)

---


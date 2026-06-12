---
title: "[SOLVED] dpkg-localpurge??????"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-19
i was doing an apt-get for restricted extras and i came to this:rick@rick-laptop:~$ sudo dpkg-reconfigure localpurge
Package `localpurge' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localpurge is not installed
rick@rick-laptop:~$ sudo apt-get install localpurge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package localpurge
rick@rick-laptop:~$ sudo apt-get dpkg-localpurge
E: Invalid operation dpkg-localpurge
rick@rick-laptop:~$ sudo apt-get install dpkg-localpurge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dpkg-localpurge
rick@rick-laptop:~$ sudo dpkg-reconfigure localpurge
Package `localpurge' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: localpurge is not installed
how do i get localpurge???
rick

---

### Post by rixtr66 on 2008-07-19
never mind

---

### Post by johnystevenson on 2008-12-16
removed...

---


---
title: "Rythembox plugin issues - rythmbox crashes"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by coller_girl on 2012-03-21
here is the problem:
the rythembox programme wont load, it crashed when i enabled a plug in a while ago and has not worked at all since.
here is a pastebin of what happens when i try to open rythembox via a terminal 
[http://paste.ubuntu.com/894502/](http://paste.ubuntu.com/894502/)
 
here is an lspci of my hardware (an asus eeepc eggshell series)
[http://paste.ubuntu.com/894512/](http://paste.ubuntu.com/894512/)

the operating system is Ubuntu 


lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

---

### Post by bonzini on 2012-03-22
on the command line, you could try

rhythmbox --disable-plugins

---


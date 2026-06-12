---
title: "help! Netatalk Install error"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by yurikoster1 on 2008-11-13
hello guys :)

i managed to install netatalk in my Intrepid Ibex and even got it to connect it with my "new" Mac Mini. but it seems the netatalk package from the repositories can only send passwords in plain text so i unistalled it and tryed to follow this tutorial :
[http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/]("http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/")

sadlly when i got to the source download i got this error:

"yuri@Ubuntu:~/src/netatalk$ apt-get source netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_source_Sources - open (2 No such file or directory)
yuri@Ubuntu:~/src/netatalk$ sudo apt-get source netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_source_Sources - open (2 No such file or directory)"

can anyone help me get this done?

thanks in advance,
yuri

---

### Post by yurikoster1 on 2008-11-13
anyone?

I got the source from here([https://launchpad.net/ubuntu/intrepid/+source/netatalk/2.0.3-11ubuntu1/+files/netatalk_2.0.3.orig.tar.gz]("https://launchpad.net/ubuntu/intrepid/+source/netatalk/2.0.3-11ubuntu1/+files/netatalk_2.0.3.orig.tar.gz") but now when i try to build the dependencies (sudo apt-get build-dep netatalk) i get this error:

"yuri@Ubuntu:~/src/netatalk$ sudo apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_source_Sources - open (2 No such file or directory)"

did i get the rigth source? if yes the is there a way to build this dependencies some other way?

I really could use some help

tnks in advance,

yuri

---

### Post by thornomad on 2008-11-14
Did you try running:

```
$ sudo apt-get update
```

Before you did any of this?  That may resolve the conflict -- I don't think the issue has anything to do with the .deb package or the source package you downloaded ... something isn't right with apt.  That's my guess.

Damon

---

### Post by yurikoster1 on 2008-11-14
> **thornomad said:**
> Did you try running:

```
$ sudo apt-get update
```

Before you did any of this?  That may resolve the conflict -- I don't think the issue has anything to do with the .deb package or the source package you downloaded ... something isn't right with apt.  That's my guess.

Damon

 tnks 4 your reply

yes i did run that command. i even switched the download server from brazil( where i live) to the main server, then i ran apt-get update again but still no luck

---


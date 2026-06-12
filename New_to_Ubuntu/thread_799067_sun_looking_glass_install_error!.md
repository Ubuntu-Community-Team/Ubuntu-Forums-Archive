---
title: "sun looking glass install error!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-18
I've just tried to install sun microsystems "looking glass" desktop environment but i got this error:

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ sudo apt-get install lg3d-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libgtk1.2 libwxgtk2.8-0 libsnack2 abe-data libwxbase2.8-0 tcl8.5 python-wxversion libgtk1.2-common tk8.5 python-wxgtk2.8
  libjsw2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  lg3d-java3d lg3d-jdk
The following NEW packages will be installed
  lg3d-core lg3d-java3d lg3d-jdk
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 139MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  lg3d-jdk lg3d-java3d lg3d-core
Install these packages without verification [y/N]? y
Get: 1 http://javadesktop.org stable/contrib lg3d-jdk 1.6.0+b104 [73.9MB]
Get: 2 http://javadesktop.org stable/contrib lg3d-java3d 1.5.0 [1666kB]
Get: 3 http://javadesktop.org stable/contrib lg3d-core 1.0.0 [63.6MB]
Fetched 139MB in 7min32s (307kB/s)
Preconfiguring packages ...
Selecting previously deselected package lg3d-jdk.
(Reading database ... 143959 files and directories currently installed.)
Unpacking lg3d-jdk (from .../lg3d-jdk_1.6.0+b104_i386.deb) ...
Selecting previously deselected package lg3d-java3d.
Unpacking lg3d-java3d (from .../lg3d-java3d_1.5.0_i386.deb) ...
Selecting previously deselected package lg3d-core.
Unpacking lg3d-core (from .../lg3d-core_1.0.0_i386.deb) ...
Setting up lg3d-jdk (1.6.0+b104) ...

Setting up lg3d-java3d (1.5.0) ...

Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Vadi on 2008-05-18
This packages are broken then, let them know that. Nothing anyone can do here...

---

### Post by empthollow on 2008-05-18
try ```
sudo apt-get -f install
```
if that doesn't work then i agree with vadi

---

### Post by kk0sse54 on 2008-05-18
I just got the same message too like five minutes ago, strange....so if they are broken then I guess no one will be able to get them working?

---

### Post by kamitsukai on 2008-05-18
So how do I report the packages as broken? or importantly to whom?  as sun is a big company:lolflag:

---

### Post by SOULRiDER on 2008-05-18
The stuff will ahve to be repacked. I tried loooking glass a while back and it seemed it had potentias, but it still wasnt good enough. AFAIK theres a live Cd you can install. You could use it and not affect your existing system.

---

### Post by Vadi on 2008-05-18
As far as I know the project was pretty much dead. But, look about for contacts or something... but definitely reporting it here won't help.

---


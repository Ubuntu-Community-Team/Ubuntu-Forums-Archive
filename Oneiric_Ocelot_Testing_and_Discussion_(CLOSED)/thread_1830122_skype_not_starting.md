---
title: "skype not starting"
date: 2011-08-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TDK800 on 2011-08-21
latest updates broke Skype:

$ skype
skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

---

### Post by MadCow108 on 2011-08-21
you need to enable multiarch and install some extra libraries:
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/830440)

---

### Post by TDK800 on 2011-08-21
$ echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch

foreign-architecture i386

$ sudo apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxss1:i386
E: Unable to locate package libqtcore4:i386
E: Unable to locate package libqt4-dbus:i386

$ sudo apt-get install libqtgui4:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libqtgui4:i386

---

### Post by portis on 2011-08-21
sudo apt-get update

> **TDK800 said:**
> $ echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch

foreign-architecture i386

$ sudo apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libxss1:i386
E: Unable to locate package libqtcore4:i386
E: Unable to locate package libqt4-dbus:i386

$ sudo apt-get install libqtgui4:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libqtgui4:i386

---


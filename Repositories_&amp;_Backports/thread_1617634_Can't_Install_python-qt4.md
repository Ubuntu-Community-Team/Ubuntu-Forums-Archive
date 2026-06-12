---
title: "Can't Install python-qt4"
date: 2010-11-09
forum: Repositories &amp; Backports
---

### Post by igb on 2010-11-09
Running Maverick i386. I am having trouble installing qt4:

```
sudo apt-get install python-qt4  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.

 python-qt4 : Depends: libqt4-designer (>= 4:4.5.3) but it is not going to be installed
              Depends: libqt4-help (>= 4:4.6.1) but it is not going to be installed
              Depends: libqt4-script (>= 4:4.6.1) but it is not going to be installed
              Depends: libqt4-scripttools (>= 4:4.6.1) but it is not going to be installed
              Depends: libqt4-test (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

```

Is this a temporary problem with the mirror (I have tried several)? A couple of day ago I installed qt4 OK on an amd64 box.

Ian.

---

### Post by Fernando Serboncini on 2010-11-10
same problem here.

---

### Post by circuit_breaker on 2010-11-16
do you guys have maverick-proposed enabled?  I do and removing qt4 packages with version 4:4.7.0-0ubuntu4.1 worked for me.

See this bug for more info:
[https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/673706]("https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/673706")

---


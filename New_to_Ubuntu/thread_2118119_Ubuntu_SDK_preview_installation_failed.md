---
title: "Ubuntu SDK preview installation failed"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by anasik on 2013-02-20
After reading the article about Ubuntu coming to phones, i decided to download the Mobile SDK to my pc, as per the instructions on the website. Both the commands i.e.
> sudo add-apt-repository ppa:canonical-qt5-edgers/qt5-proper
and 
> sudo add-apt-repository ppa:ubuntu-sdk-team/ppa && sudo apt-get update && sudo apt-get install ubuntu-sdk notepad-qml

diplayed one error or another.

So i downloaded the qt libraries and creator from the QT website and installed it, but when i try installing the SDK ( using the terminal) it displays and error saying:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-sdk : Depends: qtbase5-dev but it is not going to be installed
              Depends: libqt5webkit5-dev but it is not going to be installed
              Depends: qtmultimedia5-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


P.S. Im using Ubuntu v12.10

---

### Post by ACubed10 on 2013-02-21
Im getting this same error.  I installed QT Creator from the software center and that doesn't open.  It created an icon, but doesn't ever open

---

### Post by Gart3nzw3rg on 2013-02-23
same here :( anyone knows what to do?

---

### Post by ACubed10 on 2013-02-23
I take it this is a problem with the repo's.  Seems to happen on every Ubuntu machine I've tried.  I guess we wait for answers?

---

### Post by octav hendra on 2013-02-24
Hi guys, i`m  using ubuntu 12.10 64 bit and i was having same problem.
And solution for me is to downgrade a few packages, such as libdrm2 libgl1-mesa-glx libglapi-mesa libglapi-mesa:i386 and other packages. All you have todo is follow the error ```
ubuntu-sdk : Depends: qtbase5-dev but it is not going to be installed
```
then try to install qtbase5-dev, until you found the package that have to downgrade like
```
libgl1-mesa-glx:
  Depends: libglapi-mesa (=9.0-0ubuntu1) but 9.1~git20121212.d225d076-ubuntu0ricotz~quantal is to be installed
```
the above error is libglapi-mesa need version  9.0-0ubuntu1 but current version is 9.1~git20121212.d225d076-ubuntu0ricotz~quantal.
open synaptic and search the packages and press ctrl+e and choose the downgrade version. I hope that solution is work for you.:D

---

### Post by Nr90 on 2013-02-24
Odd, I installed the PPA on a fresh install of ubuntu 12.10 64 bit and I did not have that problem.
I did have one missing package which stopped the modules in QT creator from running. Installing that package manually fixed everything.

---


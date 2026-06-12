---
title: "Catalyst Control Center not running"
date: 2015-10-28
forum: New to Ubuntu
---

### Post by coollmax on 2015-10-28
Hi all. Now i install 15.10 ubuntu. After install driver priopritarian Ati radeon. I have Ati radeon hd5650 and Intell card
I am need run Radeon card/ 
But Catalyst Control Center not running. Try with gksu amdcccle but not opened.
Wen i try open catalist have error:
Problems arise when the Linux version initialize Catalyst Control Center. It may be caused by the following reasons.

 AMD graphics driver is not installed, or AMD drivers are not working properly.
 Please install AMD drivers for AMD hardware, or use aticonfig configuration.

HELP PLEASE. WHERE PROBLEM? HOW RUN CATALIST???? =(

---

### Post by QIII on 2015-10-28
Hello!

You have two issues.

The first is that if this is a laptop then you have an Intel/ATI hybrid system.  This can take some special effort to use.

The second is that there is a bug in the installation package for the proprietary driver in Wily:  [https://bugs.launchpad.net/bugs/1493888](https://bugs.launchpad.net/bugs/1493888)

You are fortunate that you have a hybrid system right now.  Otherwise, attempting to install the proprietary driver would have rendered your machine completely inoperable.

Leave well enough alone for now.  Unless you are experienced enough to take on the installation of the proposed bug fix, you should not attempt it.

Subscribe to the bug and watch for the status to change to "Fix released".  Then ask for help with using a hybrid graphics set up.

---

### Post by coollmax on 2015-10-28
Thanks for answer. Now status fix released. I upload new package. Update fglrx. 
But still can't load catalyst . Center. And still worked Intel card:(

---

### Post by QIII on 2015-10-28
The status "Fix released" is for Xenial.  The status is still "Fix committed" for Wily, which is why it has to be installed from wily-proposed.

When the fix is released for Wily, this still may not work if your hybrid is muxed (multiplexed) through the Intel graphics adapter.  That is an entirely different matter.

I don't know the model of your machine, but I can say that since your AMD adapter is prior to the HD 6000 series, it is not likely that it is part of a muxless system.  The muxless systems pretty much started after the release of the HD 6000 series, and even then not all were muxless.

---


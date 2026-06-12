---
title: "*ERROR* too many full retries, give up"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by houmingc on 2015-05-15
While Booting up ubuntu 14.04, a message appear 
*ERROR* too many full retries, give up on the black screen before booting into Ubuntu.


I was using window 8.1, i reinstalled Ubuntu 14.04 onto it.[URL="http://askubuntu.com/questions/468466/why-this-occurs-error-diskfilter-writes-are-not-supported"]
[/URL]

---

### Post by bapoumba on 2015-05-15
May be related to this ?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1354046](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1354046)

---

### Post by houmingc on 2015-06-09
PC is initally windows8.
There is two drives(SSD and normal harddisk) in the notebook.
initially my intention is to create a dual boot, i reformat and accidentally window 8 is erased.
Now using ubuntu has this error.

How to resolve this problem???

---

### Post by seijirou on 2015-06-10
If it's related to the 3d acceleration error bug that was referenced earlier you might be able to fix it by not using the unity desktop environment?  I think that desktop uses 3d acceleration.

At the risk of sounding like a fanboy because I recommended it once already recently in another thread, try ubuntu-mate instead and see if the error goes away.

[https://ubuntu-mate.org/vivid/](https://ubuntu-mate.org/vivid/)

---

### Post by houmingc on 2015-06-15
using ubuntu-mate to replace unity desktop, is the only available solution?
I have tons of stuff already install in ubuntu 14.04

---

### Post by mörgæs on 2015-06-15
You can add Mate and other desktop environments to your existing setup. At boot you will have the option to choose among them.

---


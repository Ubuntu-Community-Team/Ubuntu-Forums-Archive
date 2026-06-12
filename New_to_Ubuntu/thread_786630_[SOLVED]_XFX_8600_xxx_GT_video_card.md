---
title: "[SOLVED] XFX 8600 xxx GT video card"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-08
I have one question and am looking for some help I am running ubuntu 8.04 the 64 bit ver.  I have a XFX 8600 xxx GT video card installed.  I did a fresh install of Ubuntu on a new machine 

I installed the restricted driver how ever I can not get a screen size any greater then 1024x768  I know the monitor I have will support it.  Is this a card issue or have I done some thing wrong?

---

### Post by Biggy on 2008-05-08
System > Administration > Nvidia X Server Setting chose X Server Display Configuration and see the resolution setting

---

### Post by Biggy on 2008-05-08
if Nvidia X Server Setting missing from your system,
go System >Administration >Synaptic Package Manager and search :
xserver-xorg-video-nv  and install it

---

### Post by hufferd on 2008-05-08
> **Biggy said:**
> if Nvidia X Server Setting missing from your system,
go System >Administration >Synaptic Package Manager and search :
xserver-xorg-video-nv  and install it

Ah thanks for the help - I'm a long time windows user I need all the help I can get LOL 

~D

---


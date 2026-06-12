---
title: "ubuntu helpppp"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by MysticConnection on 2011-12-18
whenever i boot up theres no taskbar or launcher and the screen is to big and when i start up the computer it says out of range  can someone help? running ubuntu 11.10

---

### Post by wildmanne39 on 2011-12-18
Hi, it sounds like three issues.

1. for the launcher look at this link.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

2. go into additional drivers and install the driver for your video card if there is one there for it.

3. For out of range.

How to fix out of range problem at boot
IF IT IS ONLY HAPPENING IN GRUB and you can boot into Ubuntu then please do this:
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=1024x768

Then save and exit the document.

Then do:
```
sudo update-grub
```
Thanks

---


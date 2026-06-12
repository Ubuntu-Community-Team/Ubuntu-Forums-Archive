---
title: "how to dual monitor in ati mobility"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-09
i have an ati mobility radeon and want to connect a second monitor...
i've never done this so i don't know where to start
also how to configure the options on the second monitor?

any help much appreciated

---

### Post by skrribble on 2008-06-09
i have configured dual monitors with my ati mobility x600 two different ways:

1. Currently I use the open source driver "ati".  then i get the second monitor to work using xrandr.  [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) .  that is a pretty useful link to use xrandr.

2. I have also used the proprietary driver "fglrx".  I havent used this in about six months, but i always had trouble getting it to work using aticonfig or their catalyst control center.  It may have gotten much better since then though.

Also, a word of advice, you may not be able to get dual monitors working with compiz.  A lot of ati mobilitys only support 2048 pixels wide.  That is the case with my x600.

---

### Post by lunaluna on 2008-06-09
> **skrribble said:**
> i have configured dual monitors with my ati mobility x600 two different ways:

1. Currently I use the open source driver "ati".  then i get the second monitor to work using xrandr.  [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) .  that is a pretty useful link to use xrandr.

2. I have also used the proprietary driver "fglrx".  I havent used this in about six months, but i always had trouble getting it to work using aticonfig or their catalyst control center.  It may have gotten much better since then though.

Also, a word of advice, you may not be able to get dual monitors working with compiz.  A lot of ati mobilitys only support 2048 pixels wide.  That is the case with my x600.

well i use proprietary drivers which have improved a lot...
so probably i must use aticonfig to get it working but i don't know how to do it... properly

---

### Post by skrribble on 2008-06-09
[http://wiki.cchtml.com/index.php/Configuring](http://wiki.cchtml.com/index.php/Configuring)

that was the wiki that i always used to configure the driver. 
By the way, what video card do you have, this might help with further questions.

---

### Post by argail1980 on 2008-06-09
You can try to edit /etc/X11/xorg.conf, that's how I got my x1400 to talk to a second monitor. but until now this is only a cloned output, not a second desktop. works perfect for presentations.
But how exactly to do it depends on your current configuration, I cannot just post my xorg.conf.

Maybe you post your's, we'll have a look then

---

### Post by skrribble on 2008-06-09
also, try installing the catalyst control center with```
sudo apt-get install fglrx-control
```and try configuring the driver from there. the control panel should be under applications> accesories or maybe applications>system tools.  I can't remember or the top of my head.

---


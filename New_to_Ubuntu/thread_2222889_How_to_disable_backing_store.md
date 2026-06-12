---
title: "How to disable backing store"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by ccdavis77 on 2014-05-08
Hello...having problems disabling backing store to try to eliminate tearing using nvidia drivers with xbmc. "A workaround for ubuntu 14.04 with nvidia driver is to disable backing store in xorg: Make sure you have the "-bs" option in lightdm config file".  I have gone in to the lightdm.conf and added this line: "Xserver-command=X -bs", saved it, and then typed the following at the command prompt: 

cat /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf


[SeatDefaults]
# Dump core
xserver-command=X -core 

shouldn't the last line read "xserver-command=X -bs -core"?

I'm confused, am I doing something wrong? Any help is greatly appreciated, still learning!!!

---

### Post by troysos on 2014-05-09
I have the same problem but I'm more lost than you. How to you even get to this point? How to you change conf? How do you get to it?

---


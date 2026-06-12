---
title: "Can not login GNOME after Citrix Install"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by sawibo on 2008-05-22
After installing Citrix, restart, i can not login to GNOME. I do not remember the error message. The message is something like installation not complete and can not start xsession (or xsomething ...) because can not overwrite .... file. After a few hours trying I just decided to re-install Ubuntu, more quicker. Anybody has same experience? thanks.

---

### Post by yochaigal on 2008-05-22
next time

from terminal:

sudo dpkg-reconfigure gdm

then

startx 
if it gives you an x error message, remove X0-lock with:
sudo rm /tmp/X0-lock

If that doesn't work---- you can always backup your xorg.conf file:

sudo cp /etc/X11/xorg.conf xorg.conf.backup

then

sudo dpkg-reconfigure xserver-xorg

follow the onscreen questions

you can also do

sudo displayconfig-gtk

see what happens...

---


---
title: "Unable to log in messed up graphics"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by corkscrew on 2008-04-26
I,m a newbie,
I had ubuntu running fine. I changed my graphics card to a Radeon 9800, again no probs i switched to the restricted driver again no problems. I have a second monitor which i plugged in i tried to set up without success after reboot it mucked up my primary display to a low graphics setting. I changed my display to a viewsonic driver when i reboot i just get a fuzzy screen. How can i restore my system using the boot option restore

---

### Post by alan34 on 2008-04-26
Boot up the recovery option ( or hit Ctl-Alt-F2 ) when you get to the fuzzy screen
then login and enter

sudo dpkg-reconfigure -phigh xserver-xorg

sudo shutdown -r now

Should give you back your desktop then switch on the restricted driver again.

---


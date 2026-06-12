---
title: "wooops"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Deckoh on 2008-06-03
i did something wrong... i connected my latop to a lcd t.v. and dorked the settings up some how. i changed the screen resolution during this and i cant get it back. i've tried to fix it, but to no avail. 

see attached.

---

### Post by ajmorris on 2008-06-03
hi there, you can backup your /etc/X11/xorg.conf to /etc/X11/xorg.conf.back
then run either ```
sudo xfix
```, or ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` from a terminal

AJ

---


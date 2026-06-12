---
title: "Nvidia GeoF 6200 Font size"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by strickja on 2013-02-22
I found a lot of posts with similar problems, but have not found a solution;

Fresh install of lubuntu 12.10, all updates and loaded Nvidia x config tool 
Geoforce 6200 Video card

works fine with VGA-0, can set resolution up to 1360x768 with xrandr 

on DVI-1 xrandr list resolutions up to 1920x1080 

DVI-1 brings display up, but fonts in apps/file manager/etc are huge, unusable

have gone into system settings and openbox config and reset all fonts to 6, which has helped, but not solved problem , as apps like xterm, fileman, etc. all are still using big fonts

tried forcing dpi 96 in /etc/x11 xorg.conf files , trashes driver and screen won't come up
 
Option "UseEdidDpi" "FALSE"
Option "DPI" "96 x 96"

  Pretty new to lubuntu and its window manager - would really appreciate someone clarifying what the problem is and a solution; my understanding is its a DPI setting prob, but I can't find how to solve 

thanks

---


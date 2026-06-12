---
title: "adjust screen resolution in Lubuntu"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by lwz0203shop on 2015-03-14
[SIZE=3]Hi all, I have a problem with adjusting the screen resolution in Lubuntu. Hope someone could share some thoughts.

I wanted to setup a lightweighted linux environment in my win7 64bits OS for small coding tasks. After some search online, I decided to install Lubuntu 14.10 in virtualbox 4.3.12. The installation process was fine, but I only have one choice of screen resolution at Preferences->Monitor settings, which is 640x480. I want to set a higher resolution. 

I tried to follow the method at the url below and modify 'xorg.conf', but could not stop LXDM and configure Xorg, said "service lxdm not found"
[https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens](https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens)

'xrandr' shows 
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0*
```
I tried to use 'xrandr --addmode', still not working.

I guess it is a problem with the drivers for the host video card, but couldn't figure out where to find the correct driver. My video card is NVIDIA NVS 5400M  

There is also a problem with sharing clipboard between the host win7 and guest Lubuntu. It's just not working no matter how I set it. 

BTW, if eventually I could not fix this problem, are there other recommended linux distributions fitting my need? Thanks.
[/SIZE]

---

### Post by sudodus on 2015-03-15
Welcome to the Ubuntu Forums :-)

1. Lubuntu uses lightdm (not lxdm)

2. But I think you should do something else (and easier) to that problem, because I think your problem is the same as described in these links
[URL="http://ubuntuforums.org/showthread.php?t=2260082"]
how to increase screen resolution on laptop[/URL][URL="http://ubuntuforums.org/showthread.php?t=2269309"]

Change display resolution[/URL]

---

### Post by lwz0203shop on 2015-03-15
it works great! thank you so much.

---

### Post by sudodus on 2015-03-15
You are welcome :-)

---


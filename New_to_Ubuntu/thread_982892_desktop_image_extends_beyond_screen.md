---
title: "desktop image extends beyond screen"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by SkepticUK on 2008-11-15
Hi 

I know others have posted on this topic but I still can't seem to fix it.
I installed 8.10 on my laptop but the desktop image extends beyond the screen. 

I have a intergrated graphics card (VIA UniChrome Pro *I think*)

xrandr produces

[PHP]Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0* 
   1400x1050       0.0  
   1280x1024       0.0  
   1280x800        0.0  
   1280x768        0.0  
   1024x768        0.0  
   800x600        61.0  
   640x480        60.0  [/PHP]

 cvt -v 1680 1050 60.0Hz shows

[PHP]# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync[/PHP]

I have tried putting this modeline into xorg.conf but that doesn't seem to help.  I am new to linux/ubuntu so go easy!

---

### Post by Peter09 on 2008-11-15
What is your screen resolution.

Can you set the correct resolution using

System->Preferences->Screen Resolution

---

### Post by SkepticUK on 2008-11-16
I hadn't tried all the options in

 System->Preferences->Screen Resolution 

but I have found one that works! Feeling a bit stupid now!

Thanks for the help

---


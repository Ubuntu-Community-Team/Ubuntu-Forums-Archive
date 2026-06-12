---
title: "Resolution problem, native resolution not showing in Display control panel"
date: 2016-01-16
forum: New to Ubuntu
---

### Post by wesley16 on 2016-01-16
Hello everyone. I'm actually quite new at linux. I installed it by installing a Ubuntu 15.10 iso onto a USB stick and then installing it on a separate hard drive on my computer. I've noticed when I switched to the Nvidia driver instead of the open-source driver for my card. The screen only goes up to 1360 x 768 instead of it's native 1920x1080 resolution. 

  My monitor is not displaying its native resolution on Ubuntu 15.10.  I'm using the proprietary nvidia driver (352.63) and I did try other  solutions to add the native resolution to my options (1920x1080) but  they wouldn't work. 


  I'm running Ubuntu 15.10 on a self built computer with these specs: 
  
[LIST]
[*]CPU: Intel Core i7-3770k 
[*]Motherboard: GIGABYTE GA-Z68X-UD3H-B3 
[*]RAM:24 GB of RAM 
[*]Graphics Card: GIGABYTE Windforce Geforce GTX 980 
[/LIST]
  My monitor is an ASUS VE228. And it's connected via HDMI.

  Here is what I'm doing:
  ```
   Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96*   59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
 cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    xrandr --addmode HDMI-0 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  45
  Current serial number in output stream:  46
     

```

I really would love some help with this so that the screen will be at it's actual resolution.

---

### Post by wesley16 on 2016-01-17
Never mind I apparently solved it by connecting a DVI to HDMI adapter to my monitor. plugging in my HDMI cable in and saving the x configuration while connected that way to it then plugging back in the HDMI cable to the HDMI port on the monitor and I now have the regular resolution. Yay!

---


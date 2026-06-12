---
title: "Fn key for adjusting brightness"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-03-10
Hi, I'm having problem with adjusting brightness in my netbook Asus X201E-KX006H with Xubuntu 12.10. I can only do that by typing in terminal:
```

xrandr --output LVDS1 --brightness [e.g.] 0.6

```
But when I try to control them via fn + F5/F6 keys.. It does not work. I've already tried copying these two files: [www.ubuntugeek.com/images/video_brightnessup.sh]("http://ubuntuforums.org/www.ubuntugeek.com/images/video_brightnessup.sh") and [http://www.ubuntugeek.com/images/video_brightnessdown.sh](http://www.ubuntugeek.com/images/video_brightnessdown.sh) into /etc/acpi/, but id did not worket as well. Also I've noticed, there are no brightness built-in controls (with some GUI).
Also, this is my output for xrandr command:
```

vilem@vilix-X201EP:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

```
Thank you, for every help. (If any)

---

### Post by Toz on 2013-03-10
Try the **acpi_osi=** kernel parameter. Have a look at the "Kernel Boot Paramters" link in my signature for information on how to test it and implement it permanently if it works.

---

### Post by ViliX64 on 2013-03-10
Thank you, I will try that. In the meantime, I have found a small ulity for adjustining brightness in the top bar..

---


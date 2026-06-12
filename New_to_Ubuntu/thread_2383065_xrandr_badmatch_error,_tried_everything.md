---
title: "xrandr badmatch error, tried everything"
date: 2018-01-20
forum: New to Ubuntu
---

### Post by Karsza_Levente on 2018-01-20
Hello!
I recently switched from Windows 10 to Xubuntu 17.10 Artful
When  I installed it, my resolution was 1024x768, I tought "Okay,  installing  drivers should fix this.", So I installed the nvidia-current  package and  rebooted
After rebooting I ran the nvidia-xconfig command and  rebooted again,  and my screen's max resolution was set to 640x480, so I  deleted the  xconf file

After all this hassle my max resolution was 1360x780, but I have a 1920x1080, so I tried to force my resolution with xrandr
Output: 
```
levente@levente:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
levente@levente:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
levente@levente:~$ 
levente@levente:~$ xrandr --addmode DVI-I-0 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38
levente@levente:~$ 

```

What should I do?
I have tried reinstalling xubuntu so far, I don't know what to do at this point

---


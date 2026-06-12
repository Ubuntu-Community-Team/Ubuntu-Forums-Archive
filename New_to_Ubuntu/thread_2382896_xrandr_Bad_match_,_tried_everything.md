---
title: "xrandr Bad match , tried everything"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by Karsza_Levente on 2018-01-18
Hello, I have a fresh install of xubuntu, I already have the nvidia-390 driver for my GTX 750 TI
I suspect it's because I have a converter from VGA to DVI, I'm not sure tough

Console:
```

levente@levente-H97-HD3:~$ cvt 1920 1080 60
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
levente@levente-H97-HD3:~$ xrandr --newmode "1080pp" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
levente@levente-H97-HD3:~$ xrandr --addmode DVI-I-0 "1080pp"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38
levente@levente-H97-HD3:~$ 

```

Note: I use a VGA to DVI-D converter, and I can't really buy a new monitor as of writing this post, so buying a new one isn't an option

---


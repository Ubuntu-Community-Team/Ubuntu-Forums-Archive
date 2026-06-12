---
title: "xranr not working"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by LewisKolb on 2011-11-30
hello all,
i recently just installed Xubuntu, first time ive even seen a linux OS so bear with me.
im trying to force a 1920x1080 resolution at 60hz and to no prevail.

this is what i punched into the terminal.

lewis@LewisUbuntu:~$ cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
lewis@LewisUbuntu:~$ xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
[SIZE=2]**xrandr: Failed to get size of gamma for output default**[/SIZE]

I followed a tutorial word for word and this is what happened, Am i doing something wrong?

thanks.

---

### Post by khelben1979 on 2011-11-30
Well.. for starters, does your hardware including the monitor support that screen resolution?

```
lspci
``` will show us some hardware specifications.

---

### Post by LewisKolb on 2011-12-01
yep, works perfectly on windows, cant show you any hard ware specifcs atm cause im at work.
 
but i can tell you i have
i5 750 quad (2.5 or 2.6ghz cant remember)
GTX 550ti
6gb 1300mhz

---

### Post by khelben1979 on 2011-12-01
I'm guessing the problem is that you have connected the cable using HDMI without any HDMI to DVI converter for the monitor, have you tried with an ordinary DVI cable?

A.f.a.i.k. the Linux nVidia driver would be responsible for this issue, I think..

---


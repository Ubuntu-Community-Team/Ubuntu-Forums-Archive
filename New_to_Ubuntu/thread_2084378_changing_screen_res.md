---
title: "changing screen res"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by Hex9 on 2012-11-15
Hi all, 
Im looking to change my screen res. It is locked at 1024 x 768

I've run xrandr and outputs as follows:

Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 


Im running a ThinkPad T420, its max res is 1366x768

---

### Post by cwsnyder on 2012-11-15
Check to make sure you have **x11-xserver-utils** package loaded.  If not, please load and retry.

If you do, do you have this message showing above the xrandr output:```
xrandr: failed to get size of gamma for output default
```If you do, subscribe to my bug [https://bugs.launchpad.net/bugs/1078695](https://bugs.launchpad.net/bugs/1078695) and hope they fix it.

Otherwise, do this: ```
$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
$ xrandr --newmode 1368x768 85.25 1368 1440 1576 1784 768 771 781 798 -hsync +vsync
$ xrandr --addmode default 1368x768
$ xrandr --output default --mode 1368x768
```If at any time you get the warning about failed to get size of gamma, the only suggestion I have is to follow the bug or change distributions until they get it fixed, possibly dropping back to 12.04.  If you don't get the warning, you may be able to fix your problem by writing or modifying an /etc/X11/xorg.conf file adding the modeline above.  Check back here with more questions.

---


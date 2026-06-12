---
title: "How do I calibrate the touchscreen?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by LifeTheHound on 2008-06-27
I put 8.04 on my Vaio UX280p, and the touchscreen responds to touch, but in the wrong place.  I want to calibrate it so it works right.  

Also, I want to disable the tap-to-click behavior of the mousepad, at least for when I try to move the mouse (right now, whenever I try to move the pointer with it, it clicks first so I always end up dragging things). By the way, the mousepad I speak of is the little knob-like finger-mouse, the same as that included with old IBM's.  

Thanks a bunch!

---

### Post by ajmorris on 2008-06-28
hi there,
the following might help:

Backup /etc/X11/xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig)
then add this to your touchscreen input section:
Option "Calibrate" "1"

then install the evtouch drivers if they are not already installed

```
sudo apt-get install xserver-xorg-input-evtouch
```

then run sudo /usr/lib/xf86-input-evtouch/calibrate.sh.

Restart X and see if it helps... if not, more xorg.conf tweaking may need to be done.


AJ

---

### Post by magicfab on 2008-11-19
You may want to try Intrepid as it comes with new supprot for many touchscreens and calibration utilities.

---


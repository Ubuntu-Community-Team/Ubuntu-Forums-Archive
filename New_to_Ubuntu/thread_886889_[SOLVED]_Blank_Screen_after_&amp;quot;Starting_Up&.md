---
title: "[SOLVED] Blank Screen after &amp;quot;Starting Up&amp;quot;"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by TJCIB on 2008-08-11
Ubuntu does not show the loading screen after "Starting up/Please Wait..."
No splash screen appears either after some minutes.
I can use crtl+alt+F1 to get to a command line and login.
I can boot into recovery mode,
I tried both kernels with the same problem
I ran ```
dpkg-reconfigure xserver-org
dpkg-reconfigure gdm
``` then rebooted with the same problem

When I press Crtl+alt+F7 to get back to the graphic interface, the monitor goes into standby mode (blinking light, instead of always on)

I did a search, but there are so many posts with similar symptoms it's hard to find the right one.  Any help or direction would be great!

Thanks.

---

### Post by Crafty Kisses on 2008-08-11
Try the following:
```
startx
```

---

### Post by cosine352 on 2008-08-11
I guess after reconfiguration you need to restart gdm

> sudo /etc/init.d/gdm stop

sudo /etc/init.d/gdm start

---

### Post by TJCIB on 2008-08-11
```
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
....
```
Along with some other errors
I tried removing the file, then rerunning startx.
It gave me a different output
a bunch of "Module already built-in"
The last three lines:
```
(EE)SAVAGE(0): [drm] DRIScreenInit failed. Disabling DRI.
(EE) SAVAGE(0): DRI isn't enabled
(EE) AIGLX: Screen 0 is not DRI capable
```

still same problem on the graphical interface

---

### Post by TJCIB on 2008-08-11
Well I feel a little sheepish...

I reconfigured xserver-xorg a few times trying different drivers and resolution combinations.  Nothing seemed to be working, and got some of the "system running in low graphics mode" warnings.

After trying one I thought should definitely work, i stopped and restarted gdm, and all works.

I guess something just got screwy...working now. thanks.

---

### Post by Crafty Kisses on 2008-08-11
> **TJCIB said:**
> Well I feel a little sheepish...

I reconfigured xserver-xorg a few times trying different drivers and resolution combinations.  Nothing seemed to be working, and got some of the "system running in low graphics mode" warnings.

After trying one I thought should definitely work, i stopped and restarted gdm, and all works.

I guess something just got screwy...working now. thanks.

Sounds like a driver issue possibly.

---

### Post by cosine352 on 2008-08-11
enjoy :guitar:

---


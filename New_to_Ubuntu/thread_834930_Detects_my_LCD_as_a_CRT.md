---
title: "Detects my LCD as a CRT"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by biehlbuddy on 2008-06-19
My monitor is a Hanns-G HW191D, and it detects it as a CRT and is stuck in 640x480 resolution.  Do I need to manually edit my xorg.conf file with my monitors information?  And if so, how?

I found this problem by trying to solve another problem, both these issues may be related.  My other thread is located here:

[http://ubuntuforums.org/showthread.php?t=834752]("http://ubuntuforums.org/showthread.php?t=834752")

---

### Post by alienexplorers on 2008-06-20
Heres the basic section of the monitor section of xorg.conf.  You can get to it by opening terminal and typing:
> sudo gedit /etc/X11/xorg.conf

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Delta"
    ModelName      "DE-570"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 120.0
    Option         "DPMS"
EndSection


---


---
title: "Screen Resolution"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by rgjones12 on 2008-05-10
I am using Wubi and Ubuntu 8.04. The default screen resolution at boot up is 800 x 600. I want to increase it to either 1024 x 768 or 1280 x 1024 at boot up. Where and how change I do it for all further boot ups? Then I can control resolution internal to Ubuntu after boot up. Thanks!

---

### Post by alienexplorers on 2008-05-13
Try adding a modeline and metamode to your xorg.conf file.  See my example below. The lines in red are the ones you need to add:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Delta"
    HorizSync       31.0 - 68.0
    VertRefresh     56.0 - 85.0
    [COLOR="Red"]ModeLine       "1280x768_70.00" 95.0 1280 1352 1488 1696 768 769 772 800 -hsync +vsync[/COLOR]
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    [COLOR="Red"]Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    [COLOR="Red"]Option         "metamodes" "1280x768_70 +0+0"[/COLOR]
EndSection

---


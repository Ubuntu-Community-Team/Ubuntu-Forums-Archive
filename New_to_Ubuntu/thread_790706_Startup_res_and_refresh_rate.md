---
title: "Startup res and refresh rate?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by kattman on 2008-05-11
When Unbuntu starts up and ask for the userid the screen Flickers like its set to 60HZ, Is there anyway to have it default to my desktop settings ?

---

### Post by alienexplorers on 2008-05-13
If you are running a nvidia video card then run:
> gksudo nvidia-settings
select your resolution and refresh rate.  If that does not work try adding to xorg.conf the following lines in red:
> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Delta"
    HorizSync       31.0 - 68.0
    VertRefresh     56.0 - 85.0
    [COLOR="Red"]ModeLine       "1280x768_70.00" 95.0 1280 1352 1488 1696 768 769 772 800 -hsync +vsync[/COLOR]
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


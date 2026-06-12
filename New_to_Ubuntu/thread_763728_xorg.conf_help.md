---
title: "xorg.conf help"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by kahrytan on 2008-04-23
I have no idea what I am doing and tools on a how to didn't work right.

I need modelines for a LCD monitor using Ubuntu 8.04

Viewsonic VA1916w
1440x900 (non-interlaced)
fh:24-82 kHz, fv:50-75 Hz

Recommended  and supported  Resolutions;

1440 x 900 @ 60, 75 Hz
1280 x 1024 @ 60, 75 Hz
1024 x 768 @ 60, 70, 72, 75 Hz
800 x 600 @ 56, 60, 72, 75 Hz
640 x 480 @ 60, 75 Hz
720 x 400 @ 70 Hz


i use the xorg tool for this xorg.cong setup but I would like some designed for this monitor.

```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1440x900"
    Horizsync    31.5-56.0
    Vertrefresh    56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Configured Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1440    900
        Modes        "800x600@60"    "1280x768@60"    "800x600@56"    "1280x720@60"    "1280x800@60"    "1440x900@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
    Load        "glx"
    Load        "v4l"
EndSection
Section "device" # 
    Identifier    "device1"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    1
EndSection
Section "screen" # 
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" # 
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection
```This is to fix a bug in Ubuntu 8.04

---

### Post by EXCiD3 on 2008-04-23
It looks like you are using the nvidia driver so why not try using the nvidia-settings or nvidia-xconfig? You can run these from terminal. Someone recently had trouble finding nvidia-settings, it may not be installed on your machine, im not sure.

---

### Post by kahrytan on 2008-04-23
> **EXCiD3 said:**
> It looks like you are using the nvidia driver so why not try using the nvidia-settings or nvidia-xconfig? You can run these from terminal. Someone recently had trouble finding nvidia-settings, it may not be installed on your machine, im not sure.



Dude, THANK YOU, THANK YOU, THANK YOU.  nvidia-config saved the day. It knew my monitor and knew how to set up xorg just right. 

I can't say the same for displayconfig-gtk. It didn even list my monitor.

---

### Post by EXCiD3 on 2008-04-23
Hey no problem! I havent ever used the new screen tools to configure my monitor because they can never seem to detect my monitors correctly. Was alot easier than you thought it was gonig to be wasnt it? ;)

---


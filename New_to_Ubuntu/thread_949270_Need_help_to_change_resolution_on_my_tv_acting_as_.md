---
title: "Need help to change resolution on my tv acting as a VGA monitor"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Eleventy3 on 2008-10-16
I am trying to set up dual screen with my AOC 210v lcd monitor connected with DVI and my Toshiba Regza 32" TV connected with VGA. I have the nvidia driver installed in nvidia-settings my tv is seen as CRT-1 and the max resolution it gets is 640x480. Ideally I want to set the resolution to 1360x768. I think I have had a bit of a look around the net and I think I have to change the xorg.conf but not too sure how. Any help appreciated.

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by trikster_x on 2008-10-16
Check this out:

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

It works perfect for my dual screen setup.

---


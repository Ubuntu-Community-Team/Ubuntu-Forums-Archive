---
title: "nvidia seprate x screen glitch(?)"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-07-02
I am running a Nvidia video card and got twinview to work. After playing around wiht it i wanted it to treat it as two seperate screens so i could open things with the maximize button and not have it span across two monitors.

so i switched the configuration to from TwinView to Separate X screen.

everything is fine except on the secondary monitor, where the panel should be at the top, it is garbled images of whatever it is i drag past it. 

And now i cant put it back to Twinview. it states that it is in twinview, but it is most definitly seperate screens.

what am i doing wrong?

---

### Post by deathvalleyjoker on 2008-07-02
here is what my xorg.conf looks like:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1280x1024 +1280+0"
EndSection

---


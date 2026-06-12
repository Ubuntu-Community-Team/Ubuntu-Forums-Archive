---
title: "[SOLVED] Using Dual Monitor as in windows."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by krojas on 2008-09-21
Hi all,

What im using at the moment is hardy 8.04 with twinview on my laptop(Dell m1330 with nvidia 8400gs). It works great I can see desktop on both of the screen.

The setup is using an external screen as primary and the laptop monitor as secondary.

The issue: With twinview all the application opens on the right side, so in my setup its the secondary monitor, plus whenever I do fullscreen eg firefox it gets to both of the screens, same thing with games and videos.

Now what I would like to do is to have twinview or perhaps some other mode work exactly as in Windows. Being able to drag application to another monitor and fullscreen it there without affecting the other monitor.

Is there any possible way to make it work as in Windows? I really like to use ubuntu for everyday use, but i really cant figure out or find any solution that fix the way I want it.

Just in case you need to check the /etc/X11/xorg.conf.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
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
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HIQ L90D+ D-SUB"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HIQ L90D+ D-SUB"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
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
    BoardName      "GeForce 8400M GS"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0; CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1280+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection


Thanks in advance. :)

---

### Post by krojas on 2008-09-21
Solved it by using seperate X windows and then using xinerama.

At last I can enjoy it as i want it to. :)

---


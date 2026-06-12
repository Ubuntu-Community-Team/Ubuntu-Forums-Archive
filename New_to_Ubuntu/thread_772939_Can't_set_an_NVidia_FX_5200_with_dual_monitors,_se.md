---
title: "Can't set an NVidia FX 5200 with dual monitors, separate X Screens"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Nax10 on 2008-04-28
Hello,

I installed 8.04 on an XP system using the wubi installer.

I have two LCD monitors (very similar specs) but only one is working, the other is blank.

I've enabled the restricted NVidia drivers in Ubuntu and have installed a program called nvidia-settings which I run and set both monitors to be active and set as separate X Screens.

When I hit the Apply button in the nvidia-settings program I always get an error saying it cannot apply the new settings because one of several settings has changed.

I save the new configuration file (run it with sudo to allow the program to do a backup), I reboot, all the settings in the nvidia-settings program look as they supposed to, all correct resolutions, enabled monitors as X Screens, etc, but the second monitor is blank.

Any suggestions on what to do now?

I've done 2 more installations of 8.04 on the same system and every time I try to follow several different instructions I found on the forums with my very limited knowledge of Linux, but I was never able to make the second monitor work, so I reinstall Ubuntu from the start and hope for the best.

At some point I was able to make TwinView work (one huge desktop at 2560x1024 resolution) but the task bar and status bar, etc, all extend over both monitors and this is very difficult to get used to. What I'd like to do is have the main monitor on the left with all the task bars, etc, and have the second monitor as extra space where I can move app windows to.

Thanks in advance for any help or suggestions.

If the xorg.conf file is of any help, here it is:

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
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
    ModelName      "Proview"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Daewoo 17 TFT-LCD"
    HorizSync       30.0 - 80.0
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
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
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
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
EndSection

```

---


---
title: "[SOLVED] Setting up TV-OUT with nVidia e-GeForce 6200"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by scott.todd on 2008-11-13
Recently I bought a new video card, with 2 monitor outputs plus an SVideo TV output.  I am trying to set up my Intrepid computer to use my TV as a second monitor, or at the very least send full-screen movies to the TV while being able to continue using my main monitor.

I am currently at work, will be able to troubleshoot more later (2-3 hours from now) when I am at home in front of the computer.

I have been able to install the nVidia drivers, tried both 177.x and 173.x, even enabled desktop effects which I couldn't before.  But when I go into the nVidia X Server Settings window, and try to set up the TV, no matter what I try, the TV out won't work yet.  Often, on reboot, it gives me errors (I'll have to be at home to provide verbose errors) forcing me to start over with a generic xorg.conf file.

I am pretty sure I am missing something obvious, is there something I am missing or an easy workaround for me to try?

I would appreciate any suggestions, and I will post back later, when I have had a chance to try them out.

TIA

---

### Post by NT4usB on 2008-11-13
(Install and) run```
sudo nvidia-settings
``` with the TV plugged in. See if it detects it.

---

### Post by scott.todd on 2008-11-13
When I run "sudo nvidia-settings" it detects my tv as TV-0 but it is disabled, I enable it and restart X, and run it again, it is still disabled.  I am now trying to figure out how to edit the xorg.conf file...  :(

---

### Post by scott.todd on 2008-11-13
This is what I came up with, but it just crashes the X server.  Error log says type1 is bad... but it was working with it before.

xorg.conf:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

    Option "Xinerama" "0"
# Removed Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "OEC"
    HorizSync       31.5 - 68.7
    VertRefresh     56.0 - 88.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:10:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:10:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I've tried many different combo's, even borrowed from:
[HTML]https://help.ubuntu.com/community/NvidiaTVOut[/HTML]

...and the best I can come up with, is to have the TV detected but disabled.  If I enable it and restart X, it is disabled again.  But still don't see anything on the TV.

Would I have been better off posting this in a different forum?

---

### Post by scott.todd on 2008-11-14
After trying everything else, I tried disabling the monitor and enabling the TV.  Clicking apply and presto!

I replugged the monitor in the other monitor plug and now I have the configuration I was trying to get all along.

So, after all that, I think it was a hardware issue.  My guess is that the TV out plug and one of the monitor plugs are using the same "channel"!

Very happy to see Ubuntu working like it usually does...  :)

---


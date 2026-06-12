---
title: "Screen shifted to the left (HDMI, Dual monitors)"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by younishusam on 2014-08-29
Hello,
I have an HP ENVY m6-1161ee laptop, and I want to connect my external Full HD monitor to it. Everything works except for one problem, the external monitor is shifted to the left by 2 pixels. It's connected using HDMI to DVI connector.

I'm running Ubuntu Gnome 14.04.1 with kernel version 3.16.1-031601-generic and the latest stable AMD driver (14.4).
 Graphics Card: AMD Radeon HD 7660/7670M Dual GPU

I have the same problem with Kubuntu running the same kernel and drivers.
When running the default driver I can see about 2 pixels from the screen on the left (laptop) on the screen on the right (external full hd)
I don't have such problems in Windows.

Here's my xrandr -q output
```

husam@husam-linux:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 16384 x 16384
LVDS connected primary 1366x768+0+153 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+   40.0  
   1360x768       60.0     40.0  
   1280x768       60.0     40.0  
   1280x720       60.0     40.0  
   1024x768       60.0     40.0  
   1024x600       60.0     40.0  
   800x600        60.0     40.0  
   800x480        60.0     40.0  
   640x480        60.0     40.0  
DFP1 connected 1920x1080+1366+0 (normal left inverted right x axis y axis) 527mm x 297mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   1024x600       75.0     60.0  
   800x600        75.0     60.3  
   800x480        75.0     60.3  
   640x480        75.0     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)

```

xorg.conf:

```

Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[1]-0" 3286 0
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 312"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1366 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:0:1:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-Default monitor" "1-Default monitor"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[0]-0"
    Device     "amdcccle-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```


Here's a photo showing how the mouse is 2px outside the screen boundary
[https://www.dropbox.com/s/84w5191c2zrs241/IMG_20140830_024807.jpg?dl=0](https://www.dropbox.com/s/84w5191c2zrs241/IMG_20140830_024807.jpg?dl=0)


Things I tried:
Using the proprietary drivers. Same issues
Using arandr to move screens and make a gap between the 2 screens: moves the screen on the left to the left, so it's useless.
Using AMD Xinerma: fixes the problem.. but seriously this thing's so outdated and disables desktop effects.
Disabling laptop display: works, but I need 2 monitors.
Switching displays location from settings: works but is inconvenient.

Thanks in advance

---


---
title: "Ubuntu 8.04 (Ultimate) Nvidia DEath (attention seeking there...nearly) HELP"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by hogwartsnigel on 2008-05-31
HI,
I am seeking help desperately, I have trawled the forums trying many things until I'm dizzy and sickly tired at 4am...so here is my cry for help.

MY SYSTEM
AMD 3600 64bit uni processor at 2400.Asus k8ne-Deluxe, 2gb Gskill ram ddr1,Lian-Li server case, Nvidia geforce 7300GT 512mb,Dual monitors Dell 1905fp and Mitsubishi Diamond Pro 2070SB, 1 Samsung 320GB IDE, 1 Maxtor 250GB IDE, 2 WD 120GB SATA (non raid)

Fresh install of Ultimate Ubuntu Hardy on the maxtor, single boot seperate usr/home/root/swap partitions.

I have been trying to resolve a single cloned display at extremely low res. since install. Other Hardy installs on other machines all fine..unique to this system for me.
I've tried installing proprietary drivers from NVIDIA..reportedlyly succesful at the time, the nvidia-xconfig in terminal offers no options.

I've installed ENVY and tried both potential drivers after uninstaling the others. NVIDIA SETTINGS tells me NVIDIA_Xserver is not running and to configure  see above no options just creates a new back up and existing xorg

here is mine
[COLOR="Navy"]Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1280 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1905fp"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Mitsubishi dp2075sb"
    HorizSync       30.0 - 83.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: 1280x1024 +0+0"
    Option         "RandRRotation" "On"
    Option         "Rotate" "CCW"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "On"
EndSection
[/COLOR]

I would be delighted if anyone can help me with this..I've managed to get my NVIDIA FX5700 to work fine but this is my main work pc at home.
Thanks in advance

Nigel

---

### Post by cprofitt on 2008-06-01
I had a similar problem with a different model of nvidia card...

I solved it with the following xorg.conf changes:

```

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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
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
    BoardName      "GeForce 8800 GTS"
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
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: [COLOR=Red]1280x1024_60[/COLOR] +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I removed all non-video configs.

I hope this helps - the problem appeared to be the refresh of my CRT monitor not being detected properly so I forced it to 60 as seen above in red.

---

### Post by hogwartsnigel on 2008-06-01
Hi Pirate,
I am very appreciative of your input, but I must confess tinkering with openSUSE at present on the box in question. The funny thing there is it is 11 beta and as such has a missing nvidia option for the graphics card until the official release of 11 later this month. Until then well...I have ubuntu on one of my other systems working flawlessly and the Suse Beta is enabling my res at an acceptable res.

Thanks anyway I'll keep it filed as a possible solution if i get bored with Suse on this box.

NIgel

---


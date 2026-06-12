---
title: "Ubuntu 11.04 nvidia, gnome, Compiz enhanced video no work"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by cwmoser on 2011-11-30
I cannot get Compiz to function using Ubuntu 11.04 and Gnome.

In addition, there is no Effects tab in System -> Preferences -> Appearance.

I also tried to install the latest nvidia driver.  My guess is that there is no way to enable the video enhancements like we could with Ubuntu 10.04.

I had Compiz working perfectly with 10.04 so I know my hardware is compatible.

Has anyone got Compiz to work with Ubuntu 11.04 Gnome and nVidia?

Thanks

Carl

---

### Post by farrinux on 2011-11-30
> **cwmoser said:**
> I cannot get Compiz to function using Ubuntu 11.04 and Gnome.

In addition, there is no Effects tab in System -> Preferences -> Appearance.

I also tried to install the latest nvidia driver.  My guess is that there is no way to enable the video enhancements like we could with Ubuntu 10.04.

I had Compiz working perfectly with 10.04 so I know my hardware is compatible.

Has anyone got Compiz to work with Ubuntu 11.04 Gnome and nVidia?

Thanks

Carl

carl:
 I know in 11.10 in order to use compiz (configure) you need to install the compiz configuration tool found in software center.

Hope it helps.

---

### Post by cwmoser on 2011-12-01
I have CCSM installed but it seems like the enhanced features are not enabled.  With Ubuntu 10.04, I went to Appearance and enabled the graphics - that tab is not there in 11.04.

In addition, the Monitor Preferences icon in the top status line shows "Rotation not supported" when I click on it.  Also the Resolution is 3360 x 1050.  Could there be an issue with dual monitors (twinview) - I'm using two monitors each 1680x1050.

I am attempting to migrate to 11.04 from 10.04 - both 64-bit versions.  I will say that 11.04 seems faster than 10.04.  Wonder how good 12.04 LTS will be?

Weird this version.  I wonder if the reason Compiz does not work with Gnome is because of the emphasis on Unity?

Carl

---

### Post by cwmoser on 2011-12-01
Here is my **/etc/X11/xorg.conf** file:

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SceptreX20WG-Naga"
    HorizSync       30.0 - 81.0
    VertRefresh     40.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Virtual     1400 1050
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050 +0+0, DFP: nvidia-auto-select +1680+0; CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1680+0"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---


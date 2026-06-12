---
title: "Video Card"
date: 2009-02-25
forum: Philippine Team
---

### Post by detorresrc on 2009-02-25
Pano ba malalaman kung tama yung naka install n driver nang video card? Gamit ko 512MB GeForce 7300 GT, Minsan kc nasisira yung graphics ko :D.

---

### Post by loell on 2009-02-26
si :lolflag: talaga nakaka sira ng screen. :biggrin:

what type of monitor have you got?

---

### Post by detorresrc on 2009-02-26
SyncMaster 920NW monitor ko.

---

### Post by loell on 2009-02-26
hmm, ok naman pala, 19 inch LCD,  baka nasobrahan lang ang Scanning Frequency settings sa xorg.conf.

---

### Post by detorresrc on 2009-02-26
Yup 19 Inch LCD, Pano po malaman ung Scanning Frequency settings sa xorg.conf. Tnx po.

---

### Post by detorresrc on 2009-02-26
eto po ung xorg.conf ko.



Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "Module"
        Load    "dbe"
EndSection

---

### Post by loell on 2009-02-26
base on [http://www.overstock.com/Electronics/Samsung-SyncMaster-920NW-Widescreen-LCD-Monitor/2637255/product.html](http://www.overstock.com/Electronics/Samsung-SyncMaster-920NW-Widescreen-LCD-Monitor/2637255/product.html)

at section "monitor", try adding

```

  HorizSync   30-81
  VertRefresh 56-75
EndSection

```

---

### Post by detorresrc on 2009-02-26
Sir loel ganon p din, na add ko na sa xorg.conf tapos na reboot ko nah. Tnx sir loel ha. :guitar:

---

### Post by loell on 2009-02-26
try to play the settings in nvidia-settings

```
sudo nvidia-settings
``` 

then in **X server Display configuration** then set the refresh rate to lower or higher instead of auto.

---

### Post by detorresrc on 2009-02-26
sir loel baket may error.


ERROR: Cannot open display 'rommel-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 22 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 23 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 24 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAniso specified on line 25 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAA specified on line 26 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 27 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadow specified on line 28 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 29 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 30 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 31 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 32 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 33 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 34 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 35 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 36 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedBrightness specified on line 37 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 38 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 39 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedContrast specified on line 40 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenContrast specified on line 41 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueContrast specified on line 42 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute RedGamma specified on line 43 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute GreenGamma specified on line 44 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute BlueGamma specified on line 45 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 46 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line 47 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line 48 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 49 of configuration file '/home/rommel/.nvidia-settings-rc' (no Display connection).

---

### Post by loell on 2009-02-26
oh :( , not sure what's happenning.. post the rc file

```
cat .nvidia-settings-rc 
```

---

### Post by detorresrc on 2009-02-26
Sir loel hre's my ~/.nvidia-settins-rc, pero nag run naman yung nvidia setting napalitan ko n yung resolution pati refresh rate OK n naman. :). Sir tnx for your time ha. Ano ba magandang suggested resolution moh?


#                                                             
# /home/rommel/.nvidia-settings-rc                            
#                                                             
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Thu Feb 26 15:10:22 2009                                        
#                                                                              

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes  
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = Yes                
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

rommel-desktop:0.0/DigitalVibrance[CRT-0]=0
rommel-desktop:0.0/ImageSharpening[CRT-0]=0
rommel-desktop:0.0/SyncToVBlank=0
rommel-desktop:0.0/AllowFlipping=1
rommel-desktop:0.0/LogAniso=0
rommel-desktop:0.0/FSAA=0
rommel-desktop:0.0/TextureSharpen=0
rommel-desktop:0.0/CursorShadow=0
rommel-desktop:0.0/CursorShadowXOffset=4
rommel-desktop:0.0/CursorShadowYOffset=2
rommel-desktop:0.0/CursorShadowAlpha=64
rommel-desktop:0.0/CursorShadowRed=0
rommel-desktop:0.0/CursorShadowGreen=0
rommel-desktop:0.0/CursorShadowBlue=0
rommel-desktop:0.0/FSAAAppControlled=1
rommel-desktop:0.0/LogAnisoAppControlled=1
rommel-desktop:0.0/RedBrightness=0.000000
rommel-desktop:0.0/GreenBrightness=0.000000
rommel-desktop:0.0/BlueBrightness=0.000000
rommel-desktop:0.0/RedContrast=0.000000
rommel-desktop:0.0/GreenContrast=0.000000
rommel-desktop:0.0/BlueContrast=0.000000
rommel-desktop:0.0/RedGamma=1.000000
rommel-desktop:0.0/GreenGamma=1.000000
rommel-desktop:0.0/BlueGamma=1.000000
rommel-desktop:0.0/OpenGLImageSettings=3
rommel-desktop:0.0/XVideoTextureSyncToVBlank=1
rommel-desktop:0.0/XVideoBlitterSyncToVBlank=0
rommel-desktop:0.0/XVideoSyncToDisplay=1

---

### Post by loell on 2009-02-26
> **detorresrc said:**
>  Ano ba magandang suggested resolution moh?


by all means maximize your resolution, sayang naman kung lower resolution lang gagagmitin mo. though it's always up to you. :)

---

### Post by detorresrc on 2009-02-26
Oks tnx tlga sir loell:guitar:

---

### Post by loell on 2009-02-26
no probs.. ;)

---


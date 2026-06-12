---
title: "Custom resolution not fitting within LCD Panel? Lubuntu 14.04"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by Smokin Whale on 2015-03-10
Hey guys,

Got an odd one today. I have an older Asus A6000 15.6" notebook (Z9200v) which does not want to play nice. It has an SIS graphics card in it which by default set the resolution to 640x480 and required modification of xorg.conf in order to set the correct resolution. Now I believe I have modified the resolution correctly, and it is set to 1280x800 (native resolution for this model), however it doesn't fit on the screen... what I mean by this is that whilst it fits horizontally, vertically it chops off about 30 pixels or so and stretches the image out a bit. By moving my mouse to the top or bottom, the entire display moves up or down. It's very odd.

Here is my xorg configuration:

```
Section "Device"  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
    Busid "PCI:1:0:0"
    Driver "vesa"
    Screen 0
        Option "UseFBDev" "true"
        Option "DPMS"
        Option "ShadowFB"
        Option "MaxXFBMem"
        VideoRam 262016
        Option "RenderAccel" "true"
        Option "AllowGLXWithComposite" "true"
        Option "backingstore" "true"
        Option "AddARGBGLXVisuals" "True"


EndSection


Section "Monitor"
    Identifier    "Configured Monitor"
    Vendorname    "Generic LCD Display"
    Modelname    "LCD Panel 1280x800"
    HorizSync 20-107
        VertRefresh 50-185
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 +hsync +vsync
    Gamma    1.0
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    800
        Modes        "1280x800@60"   "800x600@60"
    EndSubSection
EndSection


Section "Module"
    Load "dri"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "GLcore"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "int10"
    Load "vbe"
    Load "speedo"
    Load "record"
EndSection


Section "DRI"
        Mode 0666
EndSection
```

I'm sure I'm just specifying the resolution incorrectly, but I'm really not sure what values I should be using (I borrowed the code from a similar thread). Any help would be greatly appreciated.

---

### Post by Smokin Whale on 2015-03-11
Has anyone found that their resolution doesn't fit on their display? My display pans up and down even though it's set to 1280x800... made a thread: [http://ubuntuforums.org/showthread.php?t=2268709](http://ubuntuforums.org/showthread.php?t=2268709)

---

### Post by mörgæs on 2015-03-11
Threads merged. Please post only once.

Did you read all relevant links posted earlier in the thread?

---

### Post by Smokin Whale on 2015-03-12
> **mörgæs said:**
> Threads merged. Please post only once.

Did you read all relevant links posted earlier in the thread?

Yes I did, no success. Was hoping that maybe someone in this thread may be having a similar issue. I'm having a different problem, using a different SIS graphics chip, different laptop and a different distribution of Ubuntu, which is why I thought it was best to make my own thread. Could you please unmerge my posts? Thanks

---

### Post by mörgæs on 2015-03-12
Posts moved to a separate thread. 
Please don't cross-post.

In the thread from which you wanted to be moved there was a link relevant to your graphics card.

---

### Post by Smokin Whale on 2015-03-17
Still having no luck with this, I think it might have something to do with this line?

> [COLOR=#000000][FONT=Ubuntu Mono]modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 +hsync +vsync[/FONT][/COLOR]

---

### Post by Geoffrey_Arndt on 2015-03-17
From:  [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[LIST]
[*]
Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"
EndSection
Section "Device"
    Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    Driver          "ati"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"
EndSection
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]See man xorg.conf for full details on how to craft an xorg.conf file.[/FONT][/COLOR]

---

### Post by Smokin Whale on 2015-03-19
I had a read through that manpage and it looks like I'm doing things properly (as far as I can tell) as it is setting the right resolution. It just doesn't fit on the panel and pans the display instead. 1280x768 works fine though, but you can tell it's not the native resolution for the panel.

---


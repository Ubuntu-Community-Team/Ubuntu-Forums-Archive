---
title: "SIS 771/671 + Xubuntu 14.04 LTS"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by javier-ejsf on 2013-08-15
I've just fresh-installed Xubuntu 13.04 on a SIS 671/771 chip notebook. Can't get its normal display resolution 1200x800.
I've read before that there are hacked drivers for this hideous chip for Ubuntu 12.04 and older, but I can't find one for Xubuntu 13.04.
Can anyone point me where to look for? (Otherwise downgrade seems like the only option...)
(How is it that Mageia 3 runs ok on this notebook, but Xubuntu won't...? I prefer to stay in the Ubuntu family) :popcorn:

---

### Post by javier-ejsf on 2014-04-18
Now trying Xubuntu 14.04, in spite of Live DVD working pretty fine (1024x768 instead of expected 1200x800 resolution)  after installing resolution went down to 640x480, it won't admit any other  option. I guess there has to be an easy fix to this. Any ideas?
**-- Moderator may upgrade thread's title to 14.04**

---

### Post by javier-ejsf on 2014-04-18
Xubuntu 14.04 works in a near to proper resolution by adding
```
sudo cp xorg.conf /etc/X11/xorg.conf
```
where xorg.conf contains this esoteric things (remember I'm a plain user, willing to migrate from XP to any Buntu with no success yet)
```
Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
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
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
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

---

### Post by santiagofn on 2014-06-21
Javier,
Había estado buscando soluciones googleando; tu archivo me sirvió para hacer funcionar Xubuntu 14.04 en mi Olivetti del año del p..
¡Mil gracias!

Saludos,

---

### Post by sudodus on 2014-06-21
Congratulations and thanks for sharing your solution :KS

-o-

It is known that there are problems with SIS graphics and 14.04 LTS. There is even this recommendation to stay with 12.04 LTS

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#SIS_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#SIS_graphics)

'SIS graphics should be run with flavours or re-spins of Ubuntu 12.04 LTS, for example Bento, Bodhi, LXLE.' These re-spins promise support until April 2017.

Xubuntu 12.04 LTS is also an alternative, but the support will end in April 2015.

---

### Post by javier-ejsf on 2014-06-21
Genial que te haya servido. Aparentemente es la única forma para levantar los *buntu 14.04 LTS 

> **santiagofn said:**
> Javier,
Había estado buscando soluciones googleando; tu archivo me sirvió para hacer funcionar Xubuntu 14.04 en mi Olivetti del año del p..
¡Mil gracias!

Saludos,

---

### Post by mörgæs on 2014-06-21
Most SIS cards work in 14.04, some straight away and some after adding an xorg.conf as shown here. 

12.04 should be seen as last resort. 

[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

---

### Post by cristiano6 on 2014-11-11
> **javier-ejsf said:**
> Xubuntu 14.04 works in a near to proper resolution by adding
```
sudo cp xorg.conf /etc/X11/xorg.conf
```
where xorg.conf contains this esoteric things (remember I'm a plain user, willing to migrate from XP to any Buntu with no success yet)
```
Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
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
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
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


Thanks very much! It worked perfectly! :p

---

### Post by javier-ejsf on 2014-11-11
I'm glad it works! ):P

---

### Post by Alex Eagle on 2014-11-12
I haven't read this whole thread so no need to accuse me of being ignorant or owt, but I'm trying to post this on all SIS threads.

I have a (horrible) Fujitsu Siemens Esprimo Mobile V5535, and [this]("http://ubuntuforums.org/showthread.php?t=2252488") fixed it for me...

Hope it helps.

---

### Post by opdiebokke! on 2014-11-18
I got this on another forum...after combing hundreds of threads and trying a number of options...[http://askubuntu.com/a/450626/349776](http://askubuntu.com/a/450626/349776) "Firstly i went into xdiagnose and ticked all 3 debug options and restarted... this helped a little!?!? as the screen restarted at 1024x768 - go figure? (perhaps a detection path has been switched off if the debug messages aren't on?)

Next i i went to additional drivers and reticked the "using x86 virtualisation solution guest adition module" and applied the changes.

After another restart my screen seems fine and dandy again - including letting me resize the window on the fly."

Mine worked fine after only the xdiagnose bit. Hope it helps someone!

---

### Post by QNEPFmr on 2015-04-26
> **javier-ejsf said:**
> Xubuntu 14.04 works in a near to proper resolution by adding
```
sudo cp xorg.conf /etc/X11/xorg.conf
```
where xorg.conf contains this esoteric things (remember I'm a plain user, willing to migrate from XP to any Buntu with no success yet)
```
Section "Device"
  Identifier "Generic Video Card"
    VendorName  "Silicon Integrated Systems [SiS]"
        BoardName   "771/671 PCIE VGA Display Adapter"
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
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1280    768
        Modes        "1280x768@60"    "1280x720@60"    "800x600@60"    "1280x800@60"    "800x600@56"
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

Hi. 

I have done this fix in Elementary OS and it worked okay, I need a res. of 1280x800 and got 1280x768.
Only the tearing is horrible, Firefox is slow, even slower than when I'm running Windows 8.1 on this machine (Intel Celeron, 1 GB of ram).

Is this due to Elementary os?
Or is this xorg fix not as good as installing an appropriate driver? If there would be one of course.

---

### Post by javier-ejsf on 2015-04-27
That's all for now (or forever). I don't think they will ever fix this. And no, it's not Elementary OS specific. In any distro you're gonna find the same problems.
I got sick of this SIS card and I swear to all the gods (that ever existed) I will never ever buy a notebook like this again.

---

### Post by mörgæs on 2015-04-27
Maybe we have a last resort where the 12.04-based Bodhi Linux is worth trying.

---

### Post by dejw18 on 2015-06-01
Instructions that will allow you to get 1280x800 resolution using SIS iMedia driver (found by googling for "sisimedia amd64"):

The updated builds of SIS driver for *ubuntu/mint (both amd64 and i386) can be found on Mati75 launchpad site ([https://launchpad.net/~mati75/+archive/ubuntu/sis771](https://launchpad.net/~mati75/+archive/ubuntu/sis771)). You can add his PPA and install SIS driver by using the commands below:

```

sudo add-apt-repository ppa:mati75/sis771
sudo apt-get update
sudo apt-get install xserver-xorg-video-sisimedia

```

Next you need to rename/backup possibly existing xorg.conf file and delete a possibly existing monitors.xml file. The last step is to create new xorg.conf using nano command line editor (or gedit if you prefer GUI):

```

sudo mv /etc/X11/xorg.conf{,_old}
rm ~/.config/monitors.xml
sudo nano /etc/X11/xorg.conf
# alternatively using GUI editor like gedit or leafpad
gksudo gedit /etc/X11/xorg.conf

```

Insert/paste the below code into your new xorg.conf file:

```

Section "Device"
    Identifier    "sis671"
    Driver        "sisimedia"
    Screen        0
EndSection

Section "Files"
        ModulePath "/usr/lib/xorg/modules"
        ModulePath "/usr/lib64/xorg/modules"
EndSection

Section "Monitor"
    Identifier    "tft"
    Option        "PreferredMode"    "1280x800"
    Gamma        1
EndSection
 
Section "Screen"
    Identifier    "Default Screen"
    Device        "sis671"
    Monitor        "tft"
    DefaultDepth    24
    SubSection "Display"
        Virtual 1280    800
        Depth    24
        Modes    "1280x800@60"    "1024x768@60"
    EndSubSection
EndSection
 
Section "ServerFlags"
    Option        "IgnoreABI"    "True"
EndSection


```

Save the file, exit notepad and restart your machine. That's it.

PS. Above xorg.conf content has been taken (and corrected a little) from [http://axebase.net/blog/2014/08/23/sis-671-in-lubuntu-14-04xorg-1-15/](http://axebase.net/blog/2014/08/23/sis-671-in-lubuntu-14-04xorg-1-15/) (you may translate this site from German to English using Google Chrome build in translator).

---


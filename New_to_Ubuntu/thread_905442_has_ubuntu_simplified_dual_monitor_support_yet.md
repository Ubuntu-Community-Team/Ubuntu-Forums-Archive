---
title: "has ubuntu simplified dual monitor support yet?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by TechDragon on 2008-08-30
Hello,

I was using ubuntu 7.10 and dual monitors worked, in 8.04 they scrapped the whole system and tried to do something new.  Which absolutely did not work... for me at least.  

I have an IBM t61 laptop which sits on a docking station while I am at work and connects to two external monitors one through the DVI and the other through the VGA.  I also want it to be able to switch back to single built in lcd when not docked.

I had to switch to Fedora Core 9 or Suse 11 to get this to work.

Here is my XORG from Fedora Core 9
> 
# Xorg configuration created by livna-config-display

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules/extensions/nvidia"
	ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "Xinerama" "0"
EndSection

Section "InputDevice"

# keyboard added by rhpxl
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Unknown"
	ModelName    "DELL 1908FP"
	HorizSync    31.0 - 83.0
	VertRefresh  56.0 - 76.0
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Unknown"
	ModelName    "IBM"
	HorizSync    53.2 - 63.9
	VertRefresh  50.0 - 60.0
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Unknown"
	ModelName    "IBM"
	HorizSync    53.2 - 63.9
	VertRefresh  50.0 - 60.0
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "Quadro NVS 140M"
	Option	    "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
	Identifier  "Videocard1"
	Driver      "nvidia"
	VendorName  "NVIDIA Corporation"
	BoardName   "Quadro NVS 140M"
	Option	    "AddARGBGLXVisuals" "True"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "1280x1024 +0+0"
# Removed Option "TwinViewXineramaInfoOrder" "DFP-1"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option	    "TwinView" "1"
	Option	    "TwinViewXineramaInfoOrder" "CRT-0"
	Option	    "metamodes" "CRT: nvidia-auto-select +0+0, DFP-1: 1280x1024 +1280+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024 +0+0"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	Option	    "TwinViewXineramaInfoOrder" "CRT-1"
	Option	    "TwinView" "0"
	Option	    "metamodes" "DFP-0: 1440x900 +0+0"
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Videocard1"
	Monitor    "Monitor2"
	DefaultDepth     24
	Option	    "TwinView" "0"
	Option	    "metamodes" "DFP-0: 1440x900 +0+0"
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

I tried just throwing this into my ubuntu xorg but it doesn't work.

---

### Post by gmxgeek on 2008-08-30
Do you have your nvidia drivers installed and in use in ubuntu? dual monitors don't seem to work with the default 'nv' drivers

---

### Post by C.S.Cameron on 2008-08-30
Have you downloaded nvidia-settings from the repositories yet?
This seems to help a lot.

---

### Post by TechDragon on 2008-09-03
yes, and all works fine in kubuntu with kde 3.5.  

I haven't tried in the last month, but I tried everything before switching, even asking the bugzilla people.

oh well, I guess I will wait for the next version to come out and try it.  

Ubuntu for me is frustrating, almost everything works, but there is always a show stopper for me. I even special ordered this IBM t61 laptop with an Nvidia card because it was supposed to be more compatible.

Not complaining, just asking, Heck I have tried to use Ubuntu through many updates, 7.10 worked the best for me.

---

### Post by rossjman1 on 2008-09-03
I have a T60 with an ATI card, and duel monitors work great. The options are in catalyst control center. Doesn't Nvidia have a similar app?

---

### Post by bodhi.zazen on 2008-09-03
> **rossjman1 said:**
> I have a T60 with an ATI card, and duel monitors work great. The options are in catalyst control center. Doesn't Nvidia have a similar app?

look .... up ... @ C.S.Cameron's ... post ...

```
gksu nvidia-settings
```

---


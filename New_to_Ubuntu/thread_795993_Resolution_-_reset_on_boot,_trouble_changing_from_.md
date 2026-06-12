---
title: "Resolution - reset on boot, trouble changing from desktop"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by sbonner on 2008-05-16
Greetings!

A few days ago, this beastie started booting with the wrong resolution.  It should by 1024x768, but instead boots to 1280x768.

When I try to change it vis System>Preferences>ScreenResolution, I get an error message:  "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."  This has worked until recently.  Not sure what could have changed it.

So, I poked around and found I could enable the Screen and Graphics Preferences Program under Applications>Other>Screens and Graphics.  From there, I can change the resolution.

But, when I reboot, it is back to the wrong resolution again.

Combing the forums did not help.  I did find I am running kdm-kde4 as my X Display Manager.  This surprised me, as I am using ubuntu Hardy, not Kubuntu.  Does Ubuntu use kdm-kde4 by default?  Should I disable this?  Or will disabling it leave me with no display?

My vid driver is listed as "Intel - Experimental Modesetting Driver for Intel", which I think is the correct driver for the Intel 845GV.

I would appreciate any help in getting this resolution to stick, and in getting the Screen Resolution function to work again so I don't have to use the Screens and Graphics program to set my resolution.

Thanks to all!

---

### Post by hermes0710 on 2008-05-16
Hi,
 can you post your xorg.conf file (/etc/X11/xorg.conf)?

---

### Post by sbonner on 2008-05-16
Here it is.  Thanks.

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"hp vx74"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP VF17 Flat Panel Monitor"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"hp vx74"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1152x864@75"	"800x600@75"	"1280x1024@75"	"800x600@72"	"1280x960@60"	"800x600@56"	"1280x1024@60"	"640x480@75"	"1280x960@75"	"640x480@72"	"1400x1050@60"	"640x480@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by hermes0710 on 2008-05-16
Delete line "Virtual 1600 1200" and retry

---

### Post by sbonner on 2008-05-16
Thanks, but no change, unfortunately.  -- S

---


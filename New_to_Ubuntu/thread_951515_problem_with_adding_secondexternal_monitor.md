---
title: "problem with adding second/external monitor"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by ymp on 2008-10-18
Faced this problem a year ago, never could resolve it,

I plugged a second lcd monitor into my notebook for easier use on my desk.
When configuring a second monitor via the 'Screens and Graphics Preferences' all former resolution for my notebook disappears, and it is replaced with a barely useable 640 x 480 resolution, same case for the second lcd. Most desktop objects are off the screen and inaccessable. Items formerly on the panel have been squeezed out of existance.
Drop down box provides a single choice of this low resolution, no other resolutions are available for the notebook. Some higher res choices are available for the added monitor, but I need to log off to make it effective, whereupon when I log back in, everything is low res, I am offered the choice to increase the res, but must log off before it takes effect, and when I log back in everything is low res, etc. etc.

There must be some way to organize the right resolution for both screeens but I cannot find what it is.
I've gone through the posts, and it seems that this is a common problem, but there is no clear way out of it.
Any clear advice welcome.

Original xconf and current xconf below.

original xconf, gave good res on notebook, but not for extra screen:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

-----------
new xconf, shitty res all around:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
	Option		"MonitorLayout"	"CRT,LFP"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"Intel 85x"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
	Option		"MonitorLayout"	"CRT,LFP"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x960@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"NEC"
	Modelname	"NEC MultiSync LCD1560V"
	Horizsync	31.0-63.0
	Vertrefresh	55.0-75.0
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
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
	Option		"Xinerama"	"true"
EndSection

---


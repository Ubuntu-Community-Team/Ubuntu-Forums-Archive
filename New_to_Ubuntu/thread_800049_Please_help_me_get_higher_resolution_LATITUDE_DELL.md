---
title: "Please help me get higher resolution LATITUDE DELL Laptop 800x600"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by MozartlovesUbun2 on 2008-05-19
I just installed Hardy Heron on an old Dell Latitude laptop.
I only get two options 640x480 and 800x600

**I need "1024x768"**

Please help me, thank you.

Please tell me what other information you may need.

here is my:

/etc/X11/xorg.conf

================================================

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by sailor2001 on 2008-05-19
1st go to system/administration/hardware drivers    next go to /usr/share/applications/screen & graffics and search for your monitor model.set your resolution..... Also the trouble may be in your 'start up manager' If you don't have it, get it in synaptics.

---

### Post by MozartlovesUbun2 on 2008-05-19
sorry i still need help

please tell me what info you need?

thank you

its an old dell laptop, please how do i know about my hardware???

i dunno whats inside the old laptop

???

---


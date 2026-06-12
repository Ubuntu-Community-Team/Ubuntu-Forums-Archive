---
title: "Dell D600 Compiz Queries"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by HornedBeast on 2008-08-20
Hello,

This is my Xorg.conf for my Dell Latitude D600 with an ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000].

I know it works with Compiz-Fusion as I have had it running before, but it doesn't seem to work as of Hardy. I also know you have to change the display depth to 16bit, which I don't know how to do in this file.

Can anyone help me or amend my Xorg.conf file to make it work?

My resolution is 1400 X 1050 if that helps at all.

Thank-you kindly.

HB

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
```

---

### Post by oliviacond on 2008-08-22
have u install the xgl?

---


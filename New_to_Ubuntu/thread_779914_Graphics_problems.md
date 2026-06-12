---
title: "Graphics problems"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by jtclicker on 2008-05-03
Since upgrading to Hardy I've had a couple of graphics problems. I'm running a fully updated Hardy with an Nvidia Geforce4 8440.
The problems are
GDM logon screen off centre and wrong refresh rate.

I cannot use the nividia driver. When I load and reboot the driver the screen goes off. I've posted about this before but still can't get it to work. Xconf that fails is

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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Any ideas would be very very welcome!

---


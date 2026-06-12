---
title: "help with strange xorg.conf"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by anthrem on 2008-05-04
trying to figure out why my gdm text is so large, and KDE is unusable due to the resolution Ubuntu defaults to, I look at my xorg.conf, which looks like no one elses in the advice I have found here:  Please help me!  I can get 1024x768 in Gnome and three other resolutions, but no such luck in KDE. I have run 'sudo dpkg-reconfigure xserver-xorg' and I get the same file.  Please help me!

> Section "InputDevice"
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
EndSection

---

### Post by Vadi on 2008-05-06
That's strange, because as far as I remember, xorg is independent of the desktop enviroment you're using...

---


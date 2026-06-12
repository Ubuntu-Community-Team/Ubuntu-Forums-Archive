---
title: "How to change color-depth?"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-06-28
Hey everyone,
I'm running Ubuntu Server 8.04 with Fluxbox and I was wondering how I'd go about changing the color-depth. 'Cause right now it's like.. really low.

Here's a copy of my xorg.conf

```


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

```

---

### Post by markbuntu on 2008-06-29
In section "Screen" add the line

DefaultDepth  24

after the line

Device ....

Of course, with the scanty information you gave us about your video card and driver etc, it is difficult to say if your card will actually support 24bit video. If it does not try

DefaultDepth  16

---

### Post by mishathegoat on 2008-06-29
I picked this machine up at a thrift store for $4 and don't know too much about the specs yet.. But thanks anywho

---


---
title: "changing screen resolution"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by x88a on 2008-06-22
my max screen resolution is 1024 x 768
is there any way to make it bigger?
my screen resolution in windows can go bigger than that
tq

---

### Post by Biggy on 2008-06-22
you have nvidia graphic card ?
install x server settings

---

### Post by Pjotr123 on 2008-06-22
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by x88a on 2008-06-22
> **Biggy said:**
> you have nvidia graphic card ?
install x server settings

i aint sure if the driver for it is auto installed upon Ubuntu installation
is there anyway to check if i hv nvidia installed?

---

### Post by Biggy on 2008-06-22
system > administration >hardware drivers 

and check NVIDIA accelerated graphics driver

restart system

---

### Post by x88a on 2008-06-22
> **Biggy said:**
> system > administration >hardware drivers 

and check NVIDIA accelerated graphics driver

restart system

mine has ATI accelerated graphics driver
should i check it and restart my comp?
will ATI function like NVidia?

---

### Post by Biggy on 2008-06-22
yea check it and restart comp

---

### Post by x88a on 2008-06-22
> **Biggy said:**
> yea check it and restart comp

ok, done it
now i have access to more different resolutions.
However, the biggest resolution is still 1024 x 768, which is still small for me
any more ideas?
tq

---

### Post by Biggy on 2008-06-22
you try from system-->preferences-->screen resolution  ?

---

### Post by x88a on 2008-06-22
> **Biggy said:**
> you try from system-->preferences-->screen resolution  ?

yes

---

### Post by Biggy on 2008-06-22
can you post output of :
> sudo gedit /etc/X11/xorg.conf
We can change resolution there

---

### Post by x88a on 2008-06-22
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
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
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

here is the output
tq

---

### Post by Biggy on 2008-06-22
ok go to System > Administration >Synaptic package manager  and search for xorg-driver-fglrx and mark for installation

---

### Post by x88a on 2008-06-22
i already have it
here is a print screen
any more ideas?
tq

---


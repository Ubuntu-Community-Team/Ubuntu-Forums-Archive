---
title: "xorg.conf problems"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by WIlib on 2008-11-10
I set up Xubuntu on an old Toshiba Satellite 1800-S203 laptop. Due to a a problem with the video card, the normal set installation will not work and the screen will just go black.  > The problem appears to be that the Trident video chip driver tries to use VESA's Display Data Channel (DDC), a standard allows the monitor to tell the video card (or on some cases the computer directly) about itself; particularly the supported screen resolutions and refresh rates. However, this hardware configuration apparently does not support DDC and X simply freezes waiting for a DDC response that never comes.

So as a result I had to change the xorg.conf. Now the screen won't fill the monitor and whenever I try something else on the xorg.conf it all goes black. Here's my current xorg.conf set up. Any suggestions would be greatly appreciated

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Trident Microsystems CyberBlade/il"
	Driver		"trident"
	BusID		"PCI:1:0:0"
	Option		"NoDDC"	
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
EndSection 


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by w4ett on 2008-11-10
> Now the screen won't fill the monitor

I take it that you have black borders????  Try from the terminal:
```

xvidtune
```

and see if you can adjust the settings.

---

### Post by w4ett on 2008-11-10
Server error...Double Post

---

### Post by WIlib on 2008-11-11
Yeah, I have black borders. 

I tried xvidtune, but no matter what I adjusted, the screen remained the same.

---

### Post by sirgogo on 2008-11-11
Hey man,

You are going to definately want to try the Alternate Install CD, (does something like Safe-Graphics). If your xorg.conf file is looking like that, but it can't communicate with the card, either a weird driver is being used or your card is blown. Let us know how it goes.

---

### Post by WIlib on 2008-11-12
Well I had to install it originally with the alternative cd and that was how I was able to mod the xorg.conf in the first place. 

The system is working pretty good, I just can't tweak the screen image to fill the monitor. It's not a huge problem, the fact that I can't figure it out is just bugging me.

---

### Post by alienexplorers on 2008-11-12
have you tried modifying the xorg.conf files monitor section so it knows the verticle and horizontal refresh rates.  This may allow the video card to cause full screen operation.

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "ViewSonic"
    ModelName      "ViewSonic VA703 SERIES"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    ModeLine       "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    Option         "DPMS"
EndSection

You will need to change the monitor type and model to fit your monitor and to generate a modeline use:
> gtf 1024 768 60
or what ever you want the screen size to be.

---

### Post by WIlib on 2008-11-12
Thanks! Got it fixed.

---


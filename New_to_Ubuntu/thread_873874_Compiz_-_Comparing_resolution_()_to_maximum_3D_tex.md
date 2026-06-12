---
title: "Compiz - Comparing resolution () to maximum 3D texture size (): Failed"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by ace007 on 2008-07-29
I've just installed dual monitor displays with twinview and a **nVidia GeForce4 MX 440 AGP 8x**.  They're two 19 inch Monitors each set at 1280x1024 with a depth of 24.

I cannot enable desktop effects via the System>Preferences>Appearence GUI.  And starting Compiz via the command line with the command "compiz" results in the following:
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0181 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

```

I have tried many things to enable the desktop effects, not even because I need them, just because I'm curious.  I have also read that the Xgl not being present is something that some even experience when compiz is running.  Also, I have changed  the depth in my xorg.conf to 16 as was suggested elsewhere to no avail. 

Once and for all could someone tell me honestly that I cannot enable compiz because of the graphics card hardware, and **NOT** some kind of setting?

PS - For any one curious, here is the xorg.conf that got my nVidia twinview setup to work.

```


Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Option		"TwinView"	"True"
	Option		"TwinViewOrientation"	"Rightof"
	Option		"MetaModes"	"1280x1024, 1280x1024"
	Option		"SecondMonitorHorizSync"	"30.0-82.0"
	Option		"SecondMonitorVertRefresh"	"50.0-75.0"
	Option		"AddARGBGLXVisuals"	"True"
	#	Option	"CoolBits"	"1"
	SubSection "Display"
		Depth	24
		Modes		"2048x1024"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce4 MX 440 with AGP8X"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Screen0" 0 0
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Viewsonic"
	Modelname	"ViewSonic VA916 Series"
	Horizsync	30.0-82.0
	Vertrefresh	50.0-75.0
	Option		"dpms"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by ace007 on 2008-07-30
I'll just have to except that its the hardware, or else I'll fail out of college by wasting my time trying to fix it.

---


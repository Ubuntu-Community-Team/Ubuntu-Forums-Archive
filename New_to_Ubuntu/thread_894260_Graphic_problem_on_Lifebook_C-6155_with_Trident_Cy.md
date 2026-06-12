---
title: "Graphic problem on Lifebook C-6155 with Trident Cyber 9525"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Klei on 2008-08-19
I'm very happy! My Ubuntu 8.04 installation was successfully and works fine. The only problem: I can't set a
resolution above 800x600 pixel.

My xorg.con shows the following lines:

[COLOR="RoyalBlue"]Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/COLOR]

In other forums I found informations, that the following configuration works:

[COLOR="RoyalBlue"]Section "Device"
Identifier "Trident Microsystems Cyber 9525"
Driver "trident"
BusID "PCI:0:20:0"
VideoRam 4
EndSection

Section "Monitor"
Identifier "Standardbildschirm"
Option "DPMS"
HorizSync 28-60
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Trident Microsystems Cyber 9525"
Monitor "Standardbildschirm"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1200x800" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
EndSection[/COLOR]

Can you tell me if I can simply modify the xorg.conf without killing my running system?

Tanks!

---

### Post by Klei on 2008-08-22
After reading a lot of threads and trying a lot of configuration I have a configuration that works with a resolution of 1024x768. For all people, who have the same problem with Lifebook C-6155 :

[COLOR="RoyalBlue"]Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	16
	SubSection "Display"
		Depth	16
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection[/COLOR]

Bye
Klei

---

### Post by exsysadm on 2011-05-21
Hi 
Thanks very much, after some hours searching for a manual Xserver configuration tool I have just staged an old C-6155 using the provided configuration in a blank xorg.conf based on Ubuntu 11.04 and it worked quite immediate

---


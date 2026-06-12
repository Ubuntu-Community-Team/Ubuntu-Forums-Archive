---
title: "Getting second monitor to be Primary until undock."
date: 2008-11-21
forum: New to Ubuntu
---

### Post by chansen4 on 2008-11-21
I am running Ubuntu 8.10 on a laptop. I have an ATI card and have installed the needed drivers and configuration control for my card.

What I would like to have happen is...When I am just using the laptop, I would like the computer to only use the visible display on the laptop along with making it the primary display. When I dock my laptop I would like the computer to recognize the external monitor and switch the primary display to that monitor.

Currently I am able to assign primary display to the external monitor, but if I do so I can't see the login screen or the panels unless I am plugged into the dock. If I change to that the laptops monitor is the primary it not only doesn't change to the external monitor, but it also keeps the space allocated for that external monitor (I can move my mouse to the right and my mouse keeps going into the other screen even when it is not connected to another screen.

Does anyone know how to make this thing do what I would like? I am not afraid of command line scripts and things to get this to work.

P.S. following are the contents of xrandr -q and xorg.conf
xrandr -q
Screen 0: minimum 320 x 200, current 2880 x 900, maximum 2880 x 900
default connected 2880x900+0+0 0mm x 0mm
   2880x900       60.0* 
   1440x900       60.0  
   1280x768       60.0  
   1280x720       60.0  
   1152x864       85.0     60.0  
   1024x768       85.0     75.0     72.0     70.0     60.0  
   800x600        85.0     75.0     72.0     70.0     60.0     56.0  
   720x480        60.0  
   640x480        85.0     75.0     72.0     60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  


xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	SubSection "Display"
		Virtual   3360 1200
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---


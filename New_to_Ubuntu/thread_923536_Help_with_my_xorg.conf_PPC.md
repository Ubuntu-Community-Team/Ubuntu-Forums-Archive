---
title: "Help with my xorg.conf PPC"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Scribblah on 2008-09-18
I inherited an old Mac iBook and have taken the opportunity to try out Ubuntu. I've got it up and running but find some crashing likely related to my playing around with xorg.conf. I was very interested to see if I could get Beryl/Compiz working and followed a number of lengthy posts with various recommendations on how to make it work. At this point I just turned off using the desktop control panel applet but still get crashing.  Can one of you expert check out my xorg.conf to see if I've done something horribly wrong? Much appreciated.  I've got an ATI card.

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
	Identifier	"Configured Video Device"
	Driver		"radeon"
	BusID		"PCI:0:16:0"
	Option          "AGPMode" "2"
	Option          "AGPFastWrite" 	"true"
	Option          "XAANoOffscreenPixmaps"
        Option 		"DisableGLXRootClipping" "true"
        Option 		"AddARGBGLXVisuals" "true"
        Option 		"AllowGLXWithComposite" "true"
        Option 		"EnablePageFlip" "true"
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
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Module"
        Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
	Load		"dbe"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by jbrown96 on 2008-09-18
I don't think that you need to use aiglx with ati cards anymore. I used it a couple of years ago and it was horrible. I would restore the backup you made before you started messing with it (you did make a backup right??). If you didn't, then you need to restore your original xorg.conf. I believe this can be done with ```
sudo dpkg--reconfigure xserver-xorg
```
If that works ok, restart and you should be using the vesa driver. You can check xorg.conf to verify. you can either try to use envy to automatically install the driver, or what I would suggest, is grabbing the newest driver from ati's website. They have a great program to install the driver and setup xorg.conf (much better than nvidia's). Once you get the driver, extract it (maybe I can't remember whether it comes in a tarball), then simply run ```
sudo sh [driver]
``` where you replace [driver] with the path and file. I believe you will need to reset, but compiz should work afterwards.

---

### Post by Scribblah on 2008-09-19
Thank you for the assist. By removing the second dash I got the command to work and just accepted all the default the "reconfigure" utility picked up. Rebooted and all seems find on the display front. I don't think ATI has a driver for this old PPC with Radeon 7500 LW. But that's OK - the vesa driver looks find to me - I've just heard so many good things about Compiz I wanted to see it in action. Another day. By the by, I've got Hardy Heron on this.

Unfortunately this is my second shot at posting this reply because on the first go-around when I hit "reply to thread," bam... crash back out to the login. Since the only thing I've played with at all was xorg.conf I thought I had caused that problem. Seems to be something else. Will have to consider what I can do before introducing this to the wife for the even older laptop I've got her on with Fedora 6.

---


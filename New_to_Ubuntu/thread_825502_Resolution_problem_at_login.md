---
title: "Resolution problem at login"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by mentallaxative on 2008-06-11
Hi everyone,

I am using Ubuntu 7.10 and I recently installed xfce to see if my performance was any better. I tinkered with the resolution settings in it to try and get something closer to what I had in GNOME, but after I logged out I couldn't get back to the login screen. It flashes
> 
starting anac(h)ronistic cron anacron
Starting deferred execution scheduler atd
Starting periodic command scheduler crond
Enabling additional executable binary formats (binfmt-support
Checking battery state...
Running local boot scripts (/etc/rc.local)

about three times and then goes black. I tried sudo dpkg-reconfigure xserver-xorg in recovery mode but it's made it even worse, now the screen doesn't go black but stays with that text.

I am unfortunately very new at this--I vaguely remember my original working resolution used to be 1200x1048, or something in that range of numbers.

Please help me. I'm very worried. :(

---

### Post by Xiong Chiamiov on 2008-06-11
Probably 1280x1024, as that's what I have.

Can you post your xorg.conf please? (/etc/X11/xorg.conf)

---

### Post by mentallaxative on 2008-06-11
> **Xiong Chiamiov said:**
> Probably 1280x1024, as that's what I have.

Can you post your xorg.conf please? (/etc/X11/xorg.conf)

Sorry.... how would I go about copying it and pasting it here?

---

### Post by mentallaxative on 2008-06-11
Thank god for the live cd.... I didn't realize it could access ubuntu files on the hard drive. I tried startx in recovery mode too, and it came up with a fatal IO error 404, no screens found.

Here is the original:

```
Section "Monitor"
	Identifier	"HP vs17"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"HP vs17"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
```

---


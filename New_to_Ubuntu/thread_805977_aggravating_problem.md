---
title: "aggravating problem"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by sir_napsalot on 2008-05-24
Ok, recently I was trying to play Starcraft over a direct cable connection with my brother. But the game froze and I had to force quit. after i force quit the resolution was stuck in 640x480 so i adjusted the settings and rebooted. now everytime i boot my monitor will give me a screen that says the refresh rate is out of range. but everytime i login it brings up the UI with no problems. i can play games but when i exit the game i still get the refresh rate problem. what is going wrong and how can i fix it?

Update -- I tried running the game in a window and I could exit the game just fine with no problems. And just to clarify the refresh problem looks like this:
"Out of range"
"79.4k  74Hz"

---

### Post by RealPSL on 2008-05-24
Each monitor does have an approved range in which it operates. Did you check to see if these settings are within the approved range?

---

### Post by sir_napsalot on 2008-05-24
the max for my monitor is supposedly 75Hz although it says 74Hz is out of range. and i don't know of any way to force all the games to run at a set refresh rate. plus im only trying to get it to run at 60hz which it has never had a problem with.

---

### Post by RealPSL on 2008-05-25
Can you tell if there have been any recent modifications to your /etc/X11/xorg.conf file?

---

### Post by sir_napsalot on 2008-05-25
there seem to have definitely been changes made since i last looked at /etc/X11/xorg.conf. the section involving the monitor looks like this ```
Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1280x1024"
	Horizsync	31.5-81.0
	Vertrefresh	50-75
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
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

```
am i the only one who thinks something might be wrong here?

---

### Post by sayakb on 2008-05-25
Ok, this might sound stupid, but what if you just remove the lines having 75Hz (like in 800x600@75). That might prevent X to even initialize modes having 75Hz frequency..

---

### Post by Sinkingships7 on 2008-05-25
> **LinuxIsInnovation said:**
> Ok, this might sound stupid, but what if you just remove the lines having 75Hz (like in 800x600@75). That might prevent X to even initialize modes having 75Hz frequency..

be sure to back it up first

---

### Post by RealPSL on 2008-05-25
Before you change anything is there an older version of the file present that you can reference instead of just going off the last time you looked at it? if not backup the current file and remove the resolutions you do not want to be available. Please let us know the results.

---


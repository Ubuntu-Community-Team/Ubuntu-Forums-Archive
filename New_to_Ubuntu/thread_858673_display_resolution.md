---
title: "display resolution"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ccl4 on 2008-07-13
hello,
how can i change the display resolution to 1280*800? because that is not available. (i have nvidia geforce go 7600)
thanks

---

### Post by Rocket2DMn on 2008-07-13
Hi, have you installed the restricted drivers for you nvidia card?  Try System->Administration->Hardware Drivers.  If it is not listed, try EnvyNG (assuming you are in Hardy Heron) - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
Then you can use nvidia-settings to change options.

---

### Post by cosine352 on 2008-07-13
system --> preferences  --> screen resolution

---

### Post by ccl4 on 2008-07-13
> **cosine352 said:**
> system --> preferences  --> screen resolution
i said: **that is not available**

---

### Post by dodle on 2008-07-13
If all your drivers are installed and you are still having the problem, you can try this:```
gksu gedit /etc/X11/xorg.conf
```Make sure to make a backup file of xorg.conf first.

In the section called "Screen" add (1280x800@75) to the line titled "Mode".  The "@75" stands for 75hz, so you can put whatever refresh rate you want there.  

Here's what mine looks like:> Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Virtual 1024 768
		Modes	"1024x768@75" "1024x768@70" "1024x768@60" "800x600@75" "800x600@70" "800x600@60" "640x480@75" "640x480@70" "640x480@60"
	EndSubSectionAlso you might need to add a modeline to the section "Monitor".> Section "monitor" # 
	Identifier	"monitor1"
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
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

---

### Post by dodle on 2008-07-13
Actually, thinking about it, it sounds like the same exact problem I was having.  My xorg.conf file was all messed up, so I input the command:```
gksu displayconfig-gtk
```
I then had to change to default screen model to "Monitor 1024x1280".  Under graphics card I found my driver.  Then I hit the button on the upper right called "save current configurations as location".  When it asked me where I wanted to save, I typed in "/etc/X11/xorg", this will overwrite your xorg.conf file, so again, back it up first.  The resolution I wanted still wasn't available, so I added these lines (in [COLOR="Red"]red[/COLOR]) to my new xorg.conf:> Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
[COLOR="Red"]	SubSection "Display"
		Depth	24
		Virtual 1024 768
		Modes	"1024x768@75" "1024x768@70" "1024x768@60" "800x600@75" "800x600@70" "800x600@60" "640x480@75" "640x480@70" "640x480@60"[/COLOR]
	EndSubSection

---


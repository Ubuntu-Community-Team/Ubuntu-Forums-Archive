---
title: "issues..."
date: 2008-07-31
forum: New to Ubuntu
---

### Post by marine63 on 2008-07-31
1. a common problem for me is most of the time i boot into ubuntu or any other linux distro my monitor says out of ranges.... 
2. another common problem is my wireless adapter cannot connect properly. im using somethingwrapper which works but when i reboot into ubuntu it can't connect to the internet and i have to type in modprobe or something in terminal to get it working again...
3.also i have slax linux how can i install it on my hard drive using a usb drive?

---

### Post by saj0577 on 2008-07-31
The second problem can be fixed with a bash script that runs on boot. 

3. There are many guides about installing from USB drive including   [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


Saj

---

### Post by daimaru on 2008-07-31
concerning question 1. Edit your /etc/X11/xorg.conf file and manually add your display resolutions under the "Section monitor": mine reads :

```
Section "Monitor"
    Identifier    "Samsung SyncMaster 214T"
    Vendorname    "Samsung"
    Modelname    "Samsung SyncMaster 215TW(Digital)"
    Horizsync    30-81
    Vertrefresh    56-75
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
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Gamma    1.0
EndSection
```Don't mind all the low res stuff, just add a line with the maximum resolution you want e.g. 1600x1200@60 should read YourMaximumResolution@MaxHertzYourMonitorCanSupport. You can neglect the crap behind the @60 .... and make sure you enter the right vertical and horizontal Sync ranges that are documented in your monitors manual. If you don't have a manual just google your monitors name +"sync range" and fill in the right stuff. After you edited your xorg.conf file you have to restart the xserver for it to take effect. You can do that by hitting ctrl+alt+backspace, or by rebooting.

---

### Post by marine63 on 2008-07-31
how would u do this bash script

---

### Post by daimaru on 2008-07-31
> **marine63 said:**
> how would u do this bash script
you could create a file in /etc/init.d called anything you want, just leave out spaces. 
inside the file do this for an example, just replace the modprobe stuff with the commands you normally issue to get wireless to work:
#!/bin/bash
modprobe -r capability
modprobe dazuko
modprobe capability


this code gets antivir to work. just replace it with your modprobe line and save it thats it..

---

### Post by eightmillion on 2008-07-31
marine63 you should just be able to enter this line into a terminal and have your system load the driver on boot.

> echo ndiswrapper | sudo tee -a /etc/modules


---

### Post by marine63 on 2008-08-01
ty so much for yall help i hope that in future updates ubuntu will be more friendly to my hardware... 
also i have managed to enter ubuntu without out of range. however i cant go to higher resolution than 1024x768

> Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 8 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0	-	65.0
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
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by eightmillion on 2008-08-01
marine63, Try changing some lines in your xorg.conf and you should be able to change to a higher resolution.

Change this:
```

modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync

```
To this:
```

modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1440x900@60"

```
And this:
```

Modes "1024x768@60" "800x600@60" "800x600@56" "640x480@60"

```
To this:
```

Modes "1440x900@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"

```

---


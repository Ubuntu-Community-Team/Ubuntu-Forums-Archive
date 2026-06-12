---
title: "Cannot log in properly"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by sjmacewan on 2008-07-20
Hello,
I've been using Ubuntu 8.04 since it came out and all of a sudden I'm having issues logging in properly.
I can get in if I load a Failure GDM session, but if I try to just login to a normal session the screen goes black for a moment (as it always did), but then it just goes back to the login screen.

I've tried reconfiguring xserver, and it actually works correctly then. The problem is that I need to edit my xorg.conf file in order to get things to display properly. To be specific, I'm using an Everex gBook will Via Chrome9 HC IGP video, and things start not working when I tell xorg.conf to use the via drivers.

I'm confident that my additions to the file are correct because it was working perfectly for months with them.

Any ideas?

---

### Post by JagDragon on 2008-07-20
Have you tried using alternate drivers to the via?
Can we see your /etc/X11/xorg.conf please?

---

### Post by sjmacewan on 2008-07-20
When I first got the laptop I tried using the different drivers, I think they were called OpenChrome, and they didn't really work overly well.

Here's two xorg.conf files, the first is what's running now and won't start in a normal session and the second is what I was using before this all happened. I've added in the "via" bits and the PanelID is required for display on this laptop using those drivers.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
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
	Driver		"via"
	VendorName	"VIA Tech"
	BoardName	"via"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
	Option		"HWCursor"		"off"
	Option		"PanelID"		"19"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes "1440x900"
		Virtual 1440 900
		Depth 24
	EndSubSection
	SubSection "Display"
		Depth 24
		Virtual 1440 900
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

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
	Driver "via"
	VendorName  "VIA Tech"
	BoardName   "via"
	Identifier	"Configured Video Device"
	Option		"HWCursor"		"off"
	Option		"PanelID"		"19"
EndSection

Section "Monitor"
	Identifier "Monitor"
	ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
	ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
	ModeLine "800x480" 29.58 800 816 896 992 480 481 484 497
	ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
	ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
	ModeLine "960x600" 45.98 960 1000 1096 1232  600 601 604 622 -HSync +Vsync
	ModeLine "1000x600" 48.07 1000 1040 1144 1288 600 601 604 622 -HSync +Vsync
	ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
	ModeLine "1088x612" 52.95 1088 1128 1240 1392 612 613 616 634 -HSync +Vsync
	ModeLine "1152x720" 67.32 1152 1208 1328 1504 720 721 724 746 -HSync +Vsync
	ModeLine "1200x720" 70.18 1200 1256 1384 1568 720 721 724 746 -HSync +Vsync
	ModeLine "1280x600" 61.50 1280 1336 1464 1648 600 601 604 622 -HSync +Vsync
	ModeLine "1280x720" 74.6 1280 1341 1474 1688 720 721 724 746
	ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
	ModeLine "1360x768" 85.50 1360 1392 1712 1744 768 783 791 807 +HSync +Vsync
	ModeLine "1366x768" 85.86 1366 1440 1584 1800 768 769 772 795 -HSync +Vsync
	ModeLine "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
	ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
	ModeLine "1600x900" 119.00 1600 1696 1864 2128 900 901 904 932 -HSync +Vsync
	ModeLine "1600x1024" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -HSync +Vsync
	ModeLine "1792x1344" 202.97 1792 1920 2112 2432 1344 1345 1348 1391 -HSync +Vsync
	ModeLine "1856x1392" 218.57 1856 1992 2192 2528 1392 1393 1396 1441 -HSync +Vsync
	ModeLine "1920x1080" 172.9 1920 2043 2249 2578 1080 1081 1084 1118
	ModeLine "2048x1536" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -HSync +Vsync
	ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
	ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
	ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
	ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
	ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
	ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
	ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
	ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
	ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
	ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
EndSection

Section "Screen"
	Monitor  "Monitor"
	SubSection "Display"
		Modes  "1440x900" 
		Virtual 1440 900
		Depth  24
	EndSubSection
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Virtual 1440 900
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
	Load  "extmod"
EndSection

Section "DRI"
	Group 0
	Mode 0666
EndSection
```

---

### Post by sjmacewan on 2008-07-20
UPDATE
Ok...if I don't use the via drivers for this (by not adding in those lines to the xorg file) then it starts up in a normal session, but video doesn't work as well...the mouse flashes a bunch when anything java/flashy is running.
It's better than nothing, but it WAS working perfectly with those lines in it before.
Could it be something to do with the monitor lines there? I noticed that when I had the via lines in there that when I loaded up a failsafe session it said that nautilus couldn't start because it didn't support the monitor (or something like that)

---

### Post by JagDragon on 2008-07-20
Another helpful debugger is the X log file. It can be found at /var/log/xorg.0.log

---

### Post by mbarak on 2008-07-20
There is a graphical program to configure the Xserver
When logging in click at the bottom left (I think its "Actions" or "Options") choose session and choose "Failsafe Gnome" or "Failsafe Terminal"

If you chose Gnome press Alt+F2 and type in "gksudo displayconfig-gtk"
If you chose the terminal type "sudo displayconfig-gtk"

In when the program comes up you can choose your graphics driver on the "Graphics Card" tab

---

### Post by sjmacewan on 2008-07-20
that log file isn't there, and using the displayconfig thing seemed to make things worse when I tried to choose the drivers...it had some issues with static-y bars running down the screen

---

### Post by mbarak on 2008-07-20
run gnome-system-log
you should see the Xserver log file in that program
System > Administration > System Log

and using the displayconfig program should make your server return to automatic configuration except for the few options you choose in there

if one graphics driver doesn't work, try another

I remember trying to help someone else with a VIA graphics driver (not the same as yours) and there just wasn't a driver in ubuntu that would work 100% with his card (even tried the official via drivers)

perhaps you should search the forums for your specific graphics card and maybe there's a driver for you out there

---

### Post by sjmacewan on 2008-07-20
OK, i found that log file by doing that log command, it's huge and I understand none of it. :(

I know that VIA cards don't yet work flawlessly with Ubuntu yet, it's just frustrating because it WAS working better than it is now...

Should I post that xorg log file? Like I said, it's huge

---

### Post by mbarak on 2008-07-20
> **sjmacewan said:**
> OK, i found that log file by doing that log command, it's huge and I understand none of it. :(

I know that VIA cards don't yet work flawlessly with Ubuntu yet, it's just frustrating because it WAS working better than it is now...

Should I post that xorg log file? Like I said, it's huge
A lot of the log file is just informational
in front of every line theres a code which indicates what type of message is being sent

look for:
(WW) - warning
(!!) - notice
(EE) - error
(??) - unknown

This information is at the beginning of the log file

---


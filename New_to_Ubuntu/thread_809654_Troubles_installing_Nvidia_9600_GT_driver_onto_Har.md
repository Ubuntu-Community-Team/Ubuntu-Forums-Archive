---
title: "Troubles installing Nvidia 9600 GT driver onto Hardy"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Denkogami on 2008-05-27
So I was following [these]("https://help.ubuntu.com/community/NvidiaManual") instructions on how to install the driver, when a couple of things didn't work out right. I downloaded the latest driver from the NVidia site figuring it would be the one that should work.

First, in my xorg, there is no ```
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
#       Load    "dri"   <------ this is 'commented'
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection
```

Next, when I get to the point of actually installing the driver, it says it can't find it. Not knowing what to do, I rebooted and now am in safe graphics mode.

This is what xorg has for the driver:
```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true" 
	Driver		"nvidia"
EndSection
```

I'm very new to Ubuntu, so sorry if I'm not providing enough info.

-------------------------
Update.

I rebooted and tried configuring things. It found my monitor, but I couldn't choose the right model of graphics card. 

Resolution is the exact same but now xorg looks like: ```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 226BW (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Lord Xeb on 2008-05-27
Your update, all it is tell me are the resolutions supported by the card. What is the maximum resolution your monitor suports?

---

### Post by Denkogami on 2008-05-27
1680x1050 is the usual one.
Though apparently it's 1900 x 1200

---

### Post by Denkogami on 2008-06-07
SO.

Finally got it all working lovelily. Now Ubuntu only loads 1/2 the time (usually after rebooting once). I get to the nVidia Splash and it's got pixels mixing from the logo located randomly about the screen and it won't load from there.

---

### Post by ad_267 on 2008-06-07
You did read this part right?
> This is not the recommended way to install the NVIDIA drivers - please see BinaryDriverHowto/Nvidia for the supported method.

The normal method works fine for most people and if you're using Hardy Heron (8.04) I'm pretty sure the driver is the latest version. Why try the hard way?

---

### Post by Denkogami on 2008-06-07
The card never showed up in Restricted Drivers, and straight up installing the nVidia drivers from Add/Remove Programs didn't work either, so I did this. It solved most problems, but created this one.

---

### Post by SteveNorman on 2008-06-07
Its to new to be in the repos

use this technique:

```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```

from this post:

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by trivix on 2008-09-23
worked like a charm for NVIDIA 8800GTS :)

---


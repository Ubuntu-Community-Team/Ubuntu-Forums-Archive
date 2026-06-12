---
title: "[SOLVED] Ubuntu not recognizing GeForce 7300LE video card"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2008-10-26
I've tried uninstalling and reinstalling and check-boxing to enable the driver(s), to no avail.

Below is a copy and paste of my xorg.conf file. Below that should be (first time trying it) a print-screen of the other *.conf files in my etc/x11 directory. I don't understand why there are so many.

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
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
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by Riffer on 2008-10-26
Assuming you're using Hardy, install "envy", its in the repos.  After you have it installed open up "envy" and use the option to remove nVidia drivers, this is important.  After that is done do a reboot.  After you log back in open "envy" again and re-install your driver.  I think you will have to reboot again.

Also I noticed in your xorg.conf file that your moniter isn't specified.  If you have problems with resolution after re-installing your driver you have to manually change that setting in the nVidia server found in the Administration drop down menu.

Good luck

---

### Post by ibuclaw on 2008-10-26
How many graphics cards do you have? 2?

The way I would go about it would be to let nvidia create it's own xorg.conf file, then set the rest up nvidia-settings.

```
sudo apt-get install nvidia-settings
```
If you can't set it up right with the nvidia-settings tool.

```
sudo nvidia-xconfig
```
But be warned, although I've never had a problem with nvidia-xconfig, that is not to say it won't go wrong with you.

Regards
Iain

---

### Post by AlanInVancouverBC on 2008-10-26
I installed Envy, but I can't find where it resides to open it!

---

### Post by AlanInVancouverBC on 2008-10-26
Well, I installed the nvidia-settings tool. But I get screenshot #1: I'm not using an nvidia-x driver. But I am, if you look at screenshot #2.
I'm stuck.

---

### Post by AlanInVancouverBC on 2008-10-26
What would happen if I deleted all the xorg.conf files that I have--all the various iterations and backups (I have 13!), and then rebooted?

---

### Post by cdtech on 2008-10-26
I would keep the most current xorg file if you delete any. Go into recovery mode and type:
sudo dpkg-reconfigure xserver-xorg

This will reconfigure your xserver with known hardware.

---

### Post by AlanInVancouverBC on 2008-10-26
Go into recovery mode and type:  sudo dpkg-reconfigure xserver-xorg

I went into Recovery and your suggestion worked. It also (although I guess you knew this would happen) "wanted" to change keyboard settings. I don't care about that; the resolution is good. Even though the Nvidia driver is "not in use". (?)

---

### Post by Riffer on 2008-10-26
> **AlanInVancouverBC said:**
> Go into recovery mode and type:  sudo dpkg-reconfigure xserver-xorg

I went into Recovery and your suggestion worked. It also (although I guess you knew this would happen) "wanted" to change keyboard settings. I don't care about that; the resolution is good. Even though the Nvidia driver is "not in use". (?)

Good to hear.  What's happening now is that your system is using the open source or "vesa" driver.  Its only giving you 2D.  It would be safe now to delete your old config files.  Such as xorg.conf1, xorg.backup etc., leave your present one xorg.conf.

If you want to try envy type in your terminal 

> sudo envyng -g

I think.  If a it comes up delete the old driver and install new one as I described before.

---

### Post by AlanInVancouverBC on 2008-10-26
When both envyNG files are downloaded, I get the shortcut (sorry for the XP lexicon) to the EnvyNG program that works for me. The need for the envy core AND gtk for the program to work wasn't there to see, nor did I get the note of the dependency when I went to download it. That seems like a fault. I used Terminal to do it all. The pkg mgr and add/remove are not the best methods: Terminal appears to be.

---

### Post by Riffer on 2008-10-26
I use synaptic found in administration, works better for me.

---


---
title: "The correct drivers for Geforce 7800"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by pcostanza on 2008-04-27
I had this working well in Gutsy but am not sure what happened when I upgraded (maybe that itself is the problem).  Compiz doesn't want to enable and now I can't even figure out how to get the restricted drivers back. Envy NG works ok but doesn't allow Compiz to enable either.
I'm hoping to get one of the 8 series cards soon but am not even sure that will make any difference.

---

### Post by artir on 2008-04-27
DONT USE Envy..
sudo apt-get install nvidia-glx-new nvidia-settings

---

### Post by pcostanza on 2008-04-27
I uninstalled Envy's drivers, rebooted and followed your post but see no difference at all.  Still no luck with compiz.  Does Hardy not like these drivers?
Also, should this be happening?

---

### Post by pcostanza on 2008-05-01
I took out my 7800 and put in a 8500 and though the screen res looks better, I'm still not able to enable desktop effects and use Compiz.  This worked fine in Gutsy without any problems at all and why it won't work now, I don't know.
Envy still makes no difference so I uninstalled that and am not experienced enough to know what else to try.
Any more ideas?

---

### Post by Tatty on 2008-05-01
use System->Administration->Hardware Drivers

use glxgears to check if you are getting a decent FPS  (over 1000)

---

### Post by pcostanza on 2008-05-01
> **Tatty said:**
> use System->Administration->Hardware Drivers

use glxgears to check if you are getting a decent FPS  (over 1000)

When I go to hardware drivers, nothing is there.  Not only with the 8500 but even with the 7800 card.  I'm pretty sure in Gutsy, I used hardware drivers.
How do I get them back?
Thanks for helping.

---

### Post by bsharp on 2008-05-01
For 32-bit:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)
64-bit:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)

Push Ctrl+alt+F1 and:
```
sudo apt-get install build-essential
sudo /etc/init.d/gdm stop
cd /wherever/you/downloaded/it/to
sudo chmod +x NVIDIA*
sudo ./NVIDIA*
sudo reboot
```

---

### Post by pcostanza on 2008-05-01
> **bsharp said:**
> For 32-bit:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run)
64-bit:
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)

Push Ctrl+alt+F1 and:
```
sudo apt-get install build-essential
sudo /etc/init.d/gdm stop
cd /wherever/you/downloaded/it/to
sudo chmod +x NVIDIA*
sudo ./NVIDIA*
sudo reboot
```

Thanks much for your info....very easy and helpful.  It did complete successfully but still I can't get Compiz to enable nor is there anything listed in my hardware drivers. Just the 'no proprietary drivers are in use on this system' at the top of the drivers screen.
I must be missing something. I'll keep trying other things.

---

### Post by alienexplorers on 2008-05-01
Please list your xorg.conf file.
> cat /etc/X11/xorg.conf
Post results here.

---

### Post by pcostanza on 2008-05-03
> **alienexplorers said:**
> Please list your xorg.conf file.

Post results here.
First, let me say that I now have a Gigabyte 8500 card. It's very nice and I'm running at recommended res, 1920x1200 60 Hz. Same problems as with the 7800 so it's certainly something I'm doing wrong.
My  xorg.conf file:

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
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
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
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

---

### Post by Antdemo on 2008-05-03
no reason for post just need to click my name to view my post lol sorry

---


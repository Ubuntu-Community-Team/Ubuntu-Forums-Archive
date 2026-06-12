---
title: "xorg.conf for dual monitors in 12.04LTS"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by AustenG on 2012-08-04
Hi, 

I'm trying to set up dual Dell Ultrasharp u2311h (23 inch, 1920x1080) monitors with my ubuntu 12.04 partition. I'm running a Radeon 7970HD graphics card with the fglrx drivers (from the ati website), and for some reason my xorg.conf file keeps messing up. Every time I back up xorg.conf, delete it and reboot it seems to works fine. The only problem is that every time I reboot after that, it tends to hang on a black screen with a blinking cursor, forcing me to manually reboot into safemode, delete the file and reboot again. 

Does anyone have any idea how to properly set up the xorg.conf file for the system that I have - and more importantly keeping the file from changing every time I reboot?

Thanks for any help!

---

### Post by QIII on 2012-08-04
When you installed the driver from the AMD site, did you just use the .run file, or did you follow instructions for creating a .deb?

Do you have a single graphics card, hybrid Intel/ATI or dual ATI/ATI graphics?

Did you run 

```
sudo aticonfig --initial
```for a single card or

```
sudo aticonfig --adapter=all --initial
```if ATI/ATI dual graphics?

---

### Post by AustenG on 2012-08-05
I have a single graphics card, and no I don't think I configured it after I ran it. Wouldn't I have had issues if I didn't? My single monitor setup was working just fine without having to do all of this.

---

### Post by AustenG on 2012-08-05
I tried the command but it's a no-go. It always gets goes to a black screen with various checks on it (ssh, battery, etc..). It always gets stuck on:
"stopping system v runlevel compatability."

Any idea what's going on? I can post my xorg.conf if that helps.

---

### Post by d4m1r on 2012-08-05
Yes, post up the one you modified but screws up after reboot.

---

### Post by AustenG on 2012-08-05
This is located in /etc/x11   :

```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" RightOf "amdcccle-Screen[1]-0"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP10"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP10" "0-DFP10"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3960 1080
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by AustenG on 2012-08-05
I've also tried:
```

dpkg --configure -a
apt-get update
apt-get dist-upgrade
apt-get install lightdm-gtk-greeter
apt-get clean
reboot


```
Problem persists.

---

### Post by AustenG on 2012-08-07
Interesting thing I found for Radeon 7970HD chip:
[http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")
^^    Basically says to use Catalyst 12.1 to be officially supported.

Anyway, I'm having a hard time uninstalling my previous drivers:

```
  
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove &#8211;purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

```

Neither of these commands work, they return errors like "no file or directory", or "could find package...". But what is confusing is that my ```
 fglrxinfo 
``` tells me that it is installed... 

I really need to get this working, can anybody make any sense of this?

---

### Post by raja.genupula on 2012-08-11
>  Interesting thing I found for Radeon 7970HD chip:
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)
^^    Basically says to use Catalyst 12.1 to be officially supported.

  

  


+1 , thanks for the info .

---


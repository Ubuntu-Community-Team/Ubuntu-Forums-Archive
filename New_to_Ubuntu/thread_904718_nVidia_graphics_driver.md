---
title: "nVidia graphics driver"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bob74 on 2008-08-29
I've used Ubuntu for some while now without problems but after upgrading to the latest version I am stuck with the choice of three resolutions and with 800x600 some windows are lost at the bottom edge. I have tried many suggestions and one I have downloaded the latest driver from nVidia which has a self installer. When I try to run in terminal I get a message- nvidia-installer must be run as root. How do I do that?
Any suggestions would be gratefully received. My card is 6100
Thanking you in anticpation of your help.
bob74

---

### Post by _Atreides_ on 2008-08-29
If you want a graphical way of doing it, open up your terminal and type
```
gksudo nautilus
```
You will now have a explorer window open that has root permission, just double click the installer.

---

### Post by Crafty Kisses on 2008-08-29
If you're just trying to run that command, try this:
```
sudo nvidia-installer
```

---

### Post by mocha on 2008-08-29
Or you can run sudo ./name-of-installer-file

You might need to run sudo nvidia-xconfig after you install the driver to fix your xorg.conf file.  It sounds like your xorg.conf file is screwed up.

Why are you installing the driver from Nvidia's site?  Just use the envy nvidia new driver from the repositories, use Synaptic to find it.  It's the same version as the latest stable on nvidia's site.

---

### Post by Crafty Kisses on 2008-08-29
You know also if you're just installing the drivers try the **Restricted Drivers Manager**, it should be in there.

---

### Post by bob74 on 2008-08-30
Many thanks for your replies and latest nvidia is installed. I now have a further problem in that when I now start up I get the message
Ubuntu is running in low-graphics mode
Your screen and graphics card could not be detected correctly. To use higher resolution visual effects or multiple screens you have to configure the display yourself.There is an option to always run in lower mode and three buttons
1. Configure
2.Shut down
3.Continue
When I go to configure and enter the graphics card and monitor and then click OK nothing happens and I have to do a contro/alt/backspace to restart.
When I get back to the same screen and click continue Ubuntu loads OK but I am stuck with low resolution.
Is there a command line which will force card and monitor detection?
When typing this I've discovered that I now have US keyboard layout for some reason. This change might be connected?
Any ideas please.
bob74

---

### Post by gmxgeek on 2008-08-30
type in terminal
```

sudo nvidia-settings

```

that is a gui for onfiguring video settings

---

### Post by swoll1980 on 2008-08-30
post your /etc/X11/xorg.conf let me take a look at it

---

### Post by t0p on 2008-08-30
> **bob74 said:**
> Many thanks for your replies and latest nvidia is installed. I now have a further problem in that when I now start up I get the message
Ubuntu is running in low-graphics mode
Your screen and graphics card could not be detected correctly. To use higher resolution visual effects or multiple screens you have to configure the display yourself.There is an option to always run in lower mode and three buttons
1. Configure
2.Shut down
3.Continue
When I go to configure and enter the graphics card and monitor and then click OK nothing happens and I have to do a contro/alt/backspace to restart.
When I get back to the same screen and click continue Ubuntu loads OK but I am stuck with low resolution.
Is there a command line which will force card and monitor detection?
When typing this I've discovered that I now have US keyboard layout for some reason. This change might be connected?
Any ideas please.
bob74

I had this very problem - even the keyboard change - after an update gave me a new kernel, 2.6.24-19 instead of 2.6.24-16.  I describe what I did to fix it in this thread - [http://ubuntuforums.org/showthread.php?t=904304]("http://ubuntuforums.org/showthread.php?t=904304").  Because the good news is, it is fixable, I'm all better now (except for the keyboard - I haven't got round to that yet).   But I went through some complicated steps.

---

### Post by swoll1980 on 2008-08-30
One of the easier ways to fix these update problems is to rename one of your xorg.conf.backup to xorg.conf that should fix it right there

---

### Post by t0p on 2008-08-30
> **swoll1980 said:**
> One of the easier ways to fix these update problems is to rename one of your xorg.conf.backup to xorg.conf that should fix it right there

```
t0p@ubunty:~$ locate xorg.conf
/etc/X11/xorg.conf
/etc/X11/xorg.conf.1
/etc/X11/xorg.conf.2
/etc/X11/xorg.conf.20080827190918
/etc/X11/xorg.conf.20080827231256
/etc/X11/xorg.conf.20080828204338
/etc/X11/xorg.conf.3
/etc/X11/xorg.conf.failsafe
/etc/X11/xorg.conf.failsafe.bak
/etc/X11/xorg.conf_backup_200808282037
/usr/share/displayconfig-gtk/xorg.conf.fallback
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster

```

Which xorg.conf backup should I use?  Any of them?  Or just one in particular.  Coz as you can see, I've got a whole bunch!

Not that I need to do anything - as I said in my previous post, I've fixed it.  But it'll happen again next time the kernel changes, so I'd sure like to know which xorg.conf is the magic one! :p

---

### Post by swoll1980 on 2008-08-30
> **t0p said:**
> ```
t0p@ubunty:~$ locate xorg.conf
/etc/X11/xorg.conf
/etc/X11/xorg.conf.1
/etc/X11/xorg.conf.2
/etc/X11/xorg.conf.20080827190918
/etc/X11/xorg.conf.20080827231256
/etc/X11/xorg.conf.20080828204338
/etc/X11/xorg.conf.3
/etc/X11/xorg.conf.failsafe
/etc/X11/xorg.conf.failsafe.bak
/etc/X11/xorg.conf_backup_200808282037
/usr/share/displayconfig-gtk/xorg.conf.fallback
/usr/share/man/man5/xorg.conf.5.gz
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster

```

Which xorg.conf backup should I use?  Any of them?  Or just one in particular.  Coz as you can see, I've got a whole bunch!

Not that I need to do anything - as I said in my previous post, I've fixed it.  But it'll happen again next time the kernel changes, so I'd sure like to know which xorg.conf is the magic one! :p

anyone from before the update right click, properties check date created

---

### Post by gmxgeek on 2008-08-30
> **swoll1980 said:**
> anyone from before the update

don't use failsafe!

---

### Post by swoll1980 on 2008-08-30
> **gmxgeek said:**
> don't use failsafe!

anyone except failsafe. sorry I left that out

---

### Post by bob74 on 2008-08-30
swoll
herewith file
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by bob74 on 2008-08-30
swoll
I forgot Monitor Acer P203W Graphics Nvidia 6100

---

### Post by D.Rose613 on 2008-08-30
hey whatsup people . Sorry off topic . but how do you Create a New Forum on this site?

---

### Post by bob74 on 2008-08-30
swoll
file details
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
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
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

Hope this helps, thanks for taking the time
bob74

---

### Post by birkopf on 2008-08-30
> **bob74 said:**
> I've used Ubuntu for some while now without problems but after upgrading to the latest version I am stuck with the choice of three resolutions and with 800x600 some windows are lost at the bottom edge. I have tried many suggestions and one I have downloaded the latest driver from nVidia which has a self installer. When I try to run in terminal I get a message- nvidia-installer must be run as root. How do I do that?
Any suggestions would be gratefully received. My card is 6100
bob74

Your problem seems to be very similar to mine... and I've done it, and it works ;-) I might be able to help.

Question - did you install drivers in graphic mode or before xserver started ?

---

### Post by swoll1980 on 2008-08-30
> **bob74 said:**
> 

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection



driver should be "nvidia" the "nv" is the safe driver I believe.

---

### Post by gmxgeek on 2008-08-30
nv is the generic ubuntu drover for nvidia, and nvidia is the uber driver of graphic amazingness

---

### Post by swoll1980 on 2008-08-30
> **gmxgeek said:**
> nv is the generic ubuntu drover for nvidia, and nvidia is the uber driver of graphic amazingness

Yeah that's what I thought it should defiantly be set to use the nvidia driver of graphic amazingness

---

### Post by gmxgeek on 2008-08-30
> **swoll1980 said:**
> Yeah that's what I thought it should defiantly be set to use the nvidia driver of graphic amazingness

After messing with X for about a week during various crashes in ibex i am now quite familiar with xorg nvidia combos

---

### Post by bob74 on 2008-08-31
Thanks for all your suggestions. Am still trying between times and when successful will leave a post.
Thankyou again
bob74

---


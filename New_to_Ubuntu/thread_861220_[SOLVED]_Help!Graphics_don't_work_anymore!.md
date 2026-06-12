---
title: "[SOLVED] Help!Graphics don't work anymore!"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-07-16
Hy all!
I did a kernel update (2.6.24-19) last night and it completely screw up my graphics.The previous kernel (2.6.24-18) worked, but I tried to install the graphics driver in 2.6.24-19.So I installed envyng and that really f... up the system.Now 2.6.24-18 is screwed up as well.I uninstalled envy and the graphic that came with it and installed the old drivers (from synaptic) but it still doesn't work.Now the highest resolution in 800X600 (my native one is 1280x800).In hardware drivers I can see may adapter but it says "Not in use".I tried checking the box and restart, but no use.
Also in nvidia settings I get this error:
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```.
I enclose 2 pictures of my screen, hope this will help.

---

### Post by Jose Catre-Vandis on 2008-07-16
Hi follow this thread, 

[http://ubuntuforums.org/showthread.php?t=860993](http://ubuntuforums.org/showthread.php?t=860993)

I am having the same problem, but was able to fix X by going into recovery mode. Still lost my desktop effects, and no drivers showing up in "Hardware Drivers" though.

---

### Post by tuxxy on 2008-07-16
You could try configure x again, from terminal

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Troll_the_Great on 2008-07-16
Tried "sudo dpkg-reconfigure xserver-xorg" and it didn't work...:(
How can I make my card "be in use"?

---

### Post by Troll_the_Great on 2008-07-16
Anyone? I'm pretty desperate, I don't want to make a clean install.I've just set up my system the way I want it...:(

---

### Post by philinux on 2008-07-16
Boot up press esc and choose recovery mode.

There is now a little menu there.

Choose xfix. See if that helps.

---

### Post by Troll_the_Great on 2008-07-16
Philinux, I did what you suggested and I can get my normal resolution, but still my graphic card is not in use.If I check the box, it promts me to restart, and after restart I'm back where I started (the low resolution phase).I don't know what to do....:(:(:(

---

### Post by Canis familiaris on 2008-07-16
> **Troll_the_Great said:**
> 
```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```.

Did you try what the error message said?
Try if if you didn't.

If that didn't help. This link may help.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Also try running nvidia-glx in the terminal.

Ages ago, I installed nVidia drivers in my friend PC and it worked.
```
sudo apt-get install nvidia-glx
```

But that was ages ago. I use ATi now, so I dont really know further. Sorry not be able to help much.

---

### Post by dannyboy79 on 2008-07-16
are you going to stick with the latest kernel? if so, change your xorg.conf to use vesa for the time being and restart your x-server. then go into synaptic and uninstall and completely remove anythign with nvidia in the title. then download the latest envy and run it, it should install what you need, then run 
gksudo nvidia-settings from the terminal and set up your xorg.conf file using that GUI. good luck.

---

### Post by Troll_the_Great on 2008-07-16
How can I restart the X server?

---

### Post by Troll_the_Great on 2008-07-16
> **dannyboy79 said:**
> are you going to stick with the latest kernel? if so, change your xorg.conf to use vesa for the time being and restart your x-server. then go into synaptic and uninstall and completely remove anythign with nvidia in the title. then download the latest envy and run it, it should install what you need, then run 
gksudo nvidia-settings from the terminal and set up your xorg.conf file using that GUI. good luck.

I have no idea how to do what you told me.I made a little progress though.Now, in Hardware Drivers my card is "in use" but when I try to open the nvidia-settings I get the same message.How can I restart the x server?What's the command?

EDIT: I used envy, it was the one who screw up the system.

---

### Post by Barnetto on 2008-07-16
i tihnk you need to update all you programs with the new kernel, im having the same problem as you on this one this one. but for now when ubuntu is booting press esc and select and older kernel, should be the 3rd one down (generic mode)


Barnetto

---

### Post by Troll_the_Great on 2008-07-16
> **Barnetto said:**
> i tihnk you need to update all you programs with the new kernel, im having the same problem as you on this one this one. but for now when ubuntu is booting press esc and select and older kernel, should be the 3rd one down (generic mode)


Barnetto

I did that, but both of my kernels are screwed up now (2.6.24-18 and 2.6.24-19).
I don't know what to do....Somebody told me to restart the x server, but I don't know how...

---

### Post by Barnetto on 2008-07-16
run this:

```
sudo aptitude install envyng-gtk
```


Run with System Tools > EnvyNG

Click Nvidia

then Install the NVIDIA driver (Automatic Hardware Detection)

and then Apply :)

Hope this helps, let me no.

Barnetto

---

### Post by Troll_the_Great on 2008-07-16
> **Barnetto said:**
> run this:

```
sudo aptitude install envyng-gtk
```


Run with System Tools > EnvyNG

Click Nvidia

then Install the NVIDIA driver (Automatic Hardware Detection)

and then Apply :)

Hope this helps, let me no.

Barnetto

Thank, it worked...bot no so good.Compiz is working now, but I can get only 1024x768 max resolution.My native resolution is 1280x800...:(
Any ideas how to fix that?

---

### Post by Troll_the_Great on 2008-07-16
Another thing that I find weird is the fact that in System-Hardware Drivers my card is not in use...How can compiz run then?:confused:

---

### Post by Barnetto on 2008-07-16
thats abit weird...

any how open:

Add/Remove..

search nvidia and install NVIDIA Sever X Settings and install it (and you might want to reboot)

when you login go to system > administration > NVIDIA Sever X Settings

click on display configuration and tweak in there :)


Hope this helps again :)


Barnetto

---

### Post by Barnetto on 2008-07-16
Think of what was in Hardware Drivers is cheapy ubuntu nvidia drivers, what you got now is the really thing ;)

Barnetto

---

### Post by Troll_the_Great on 2008-07-16
> **Barnetto said:**
> thats abit weird...

any how open:

Add/Remove..

search nvidia and install NVIDIA Sever X Settings and install it (and you might want to reboot)

when you login go to system > administration > NVIDIA Sever X Settings

click on display configuration and tweak in there :)


Hope this helps again :)


Barnetto

I did that, but it won't let me choose a resolution higher then 1024x768...I want to get back to my original resolution of 1280x800.How do I do that?

---

### Post by Troll_the_Great on 2008-07-16
I am going to bed now, it's 2:30 in the morning here.Please post any replies and I will look at them in the morning and tell you if they work.
Thanks in advance!
Cheers!

---

### Post by t0p on 2008-07-16
> **Barnetto said:**
> Think of what was in Hardware Drivers is cheapy ubuntu nvidia drivers, what you got now is the really thing ;)


Where do you get that idea from?  It seems pretty clear to me that the drivers supplied through **Hardware Drivers** are proprietary drivers, not "Ubuntu" drivers.

When I open **System > Administration > Hardware Drivers**, I see this blurb:

> Proprietary drivers do not have public source code that Ubuntu developers are free to modify.  They represent a risk to you because they are only available on the types of computer chosen by the manufacturer, and security updates to them depend solely on the responsiveness of the manufacturer.  Ubuntu cannot fix or improve these drivers.

This text makes it clear that Ubuntu developers did not create these NVIDIA drivers. ("*Proprietary drivers do not have public source code that Ubuntu developers are free to modify ... Ubuntu cannot fix or improve these drivers*") Also, if you read subsequent boot messages, you'll see one that says **the proprietary drivers have tainted the kernel**.

Using **Hardware Drivers** introduces proprietary code to your installation of Ubuntu.

---

### Post by Barnetto on 2008-07-16
WOW chill out i simply meant that the i said was more official and proper than the other ones.

---

### Post by Troll_the_Great on 2008-07-17
OK, but anybody knows how can I get my resolution back?

---

### Post by philinux on 2008-07-17
Post the contents of your xorg.conf.

---

### Post by Troll_the_Great on 2008-07-17
> **philinux said:**
> Post the contents of your xorg.conf.

Please give me the exact command because if I paste xorg.conf in a terminal I get "command not found".

---

### Post by Canis familiaris on 2008-07-17
> **Troll_the_Great said:**
> Please give me the exact command because if I paste xorg.conf in a terminal I get "command not found".

```
gedit /etc/X11/xorg.conf
```

---

### Post by Troll_the_Great on 2008-07-17
Thanks Anurag_Panda.This is my xorg-conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```
Does it help?

---

### Post by Canis familiaris on 2008-07-17
Could you post the output of this command:
```
ls /etc/X11/xorg.con* -l
```
This will list all the older xorg.conf files

---

### Post by Troll_the_Great on 2008-07-17
Sure, here it is:
```
ls /etc/X11/xorg.con* -l
-rw-r--r-- 1 root root 2321 2008-07-17 01:48 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1574 2008-07-16 16:17 /etc/X11/xorg.conf.1
-rw-r--r-- 1 root root 2297 2008-07-16 18:02 /etc/X11/xorg.conf.2
-rw-r--r-- 1 root root 1574 2008-05-30 14:23 /etc/X11/xorg.conf.20080530142348
-rw-r--r-- 1 root root 2653 2008-07-16 18:56 /etc/X11/xorg.conf.20080716185633
-rw-r--r-- 1 root root 1574 2008-07-16 20:27 /etc/X11/xorg.conf.20080716202710
-rw-r--r-- 1 root root 2167 2008-07-16 21:02 /etc/X11/xorg.conf.20080716210243
-rw-r--r-- 1 root root 1574 2008-07-16 21:14 /etc/X11/xorg.conf.20080716211458
-rw-r--r-- 1 root root 1574 2008-07-16 21:22 /etc/X11/xorg.conf.20080716212210
-rw-r--r-- 1 root root 2167 2008-07-17 00:37 /etc/X11/xorg.conf.20080717003748
-rw-r--r-- 1 root root 2301 2008-07-16 18:09 /etc/X11/xorg.conf.3
-rw-r--r-- 1 root root 2167 2008-07-17 00:43 /etc/X11/xorg.conf.4
-rw-r--r-- 1 root root 1574 2008-07-17 00:40 /etc/X11/xorg.conf.backup
-rw-r--r-- 1 root root 2618 2008-07-16 17:38 /etc/X11/xorg.conf_backup_200807161738
-rw-r--r-- 1 root root 2205 2008-07-17 01:12 /etc/X11/xorg.conf_backup_200807170112
-rw-r--r-- 1 root root 2211 2008-07-17 01:48 /etc/X11/xorg.conf_backup_200807170148
-rw-r--r-- 1 root root 1238 2008-07-17 01:39 /etc/X11/xorg.conf.failsafe
-rw-r--r-- 1 root root 1238 2008-07-17 01:33 /etc/X11/xorg.conf.failsafe.b
```

---

### Post by Canis familiaris on 2008-07-17
Could you open and post the output of:
```
gedit /etc/X11/xorg.conf.1
```

Basically what I am trying to do is to view that xorg.conf file which existed before your graphics got kaput. You could replace this xorg.conf with that older xorg.conf to get it working.

---

### Post by Troll_the_Great on 2008-07-17
Ok,I got it.Thank you for your time.Here is what you asked:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
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
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by Canis familiaris on 2008-07-17
Things are not going the way I thought. Your older xorg.conf was configured very differently to your current xorg.conf. Baically I thought there would have corresponding entries for your native resolution in that xorg.conf.1 but I was wrong.
In my understanding you need the corresponding lines for your reqd. resolution where I have marked as red.

Your original xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	[color=red]1024	768[/color]
		Modes	[color=red]**"???"**[/color]	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:4:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0	-	65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
[color=red]**CORRESPONDING ENTRY FOR 1280x800**[/color]
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```]

I can guess "???" to be "1280x800@60" (replace 1280x800 with your resolution and 60 by your frequency) but I cannot really guess about the second line I've marked.

BTW did you try the nVidia tool for setting up screen resolution?

---

### Post by Troll_the_Great on 2008-07-17
If by nvidia tool you mean "Nvidia X Server Settings" yes I did, but the highest resolution is 1024x768.I figured out about those lines, the first one is pretty easy "1280x800@60" but the second...I don't know what those figures represent...(65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync).What can I do?:(

---

### Post by Canis familiaris on 2008-07-17
> **Troll_the_Great said:**
> If by nvidia tool you mean "Nvidia X Server Settings" yes I did, but the highest resolution is 1024x768.I figured out about those lines, the first one is pretty easy "1280x800@60" but the second...I don't know what those figures represent...(65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync).What can I do?:(
Yes I dont understand them too.
You may just try to change the first line you understand and try without changing the second line though.

Just backup your current xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Just restart X: by Ctrl+Alt+Backspace and then try changing the resolution.

If it worsens up things you could revert back by:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.failed
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

But I seriously doubt whether it will work! :???:

---

### Post by Troll_the_Great on 2008-07-17
You were right, I was back to 800x600 resolution and the system saying it is not able to find my video adapter :(
I don't know what can I do anymore...

---

### Post by Troll_the_Great on 2008-07-17
I also don't understand why in Hardware Drivers my graphic card is not in use...If I enable it, it overrides drivers from EnvyNG and when I reboot I get only 800x600 resolution, no effects and Nvidia X Server Settings complains that "it appears that I don't use the X Server"...What's with that?Should I look for drivers and install them manually?

---

### Post by Canis familiaris on 2008-07-17
Perhaps, This may help:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by philinux on 2008-07-17
You could run the screens and graphics tool.

gksu displayconfig-gtk

This is the old tool that the devs say we dont need now with the bullet proof x.

But in your case x is anything but.

---

### Post by Troll_the_Great on 2008-07-17
Now I'm really confused...I've installed again the driver using EnvyNG and now everything work.Copiz is ok and my resolution is back to normal...Weird, no?I'm just happy that the problem is fixed.Thanks again to all for your time.
Cheers!

---

### Post by Troll_the_Great on 2008-07-17
Before I mark the thread  as solved, I rebooted to see if everything is OK after reboot (and it is).In Hardware Drivers my card is still not in use but the effects work and my resolution is back to normal so...thread solved.I don't know why, but I'm glad is ok.Thanks again to all for your time.

---

### Post by Canis familiaris on 2008-07-17
All well that ends well ;)

---

### Post by philinux on 2008-07-17
Yep don't worry about it not showing in there. It only shows in there if you use the default ubuntu driver from synaptic.

---


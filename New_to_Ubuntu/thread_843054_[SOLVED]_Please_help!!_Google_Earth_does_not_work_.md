---
title: "[SOLVED] Please help!! Google Earth does not work in 8.04"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Liakath on 2008-06-27
Dear All

I have been running HH on my Toshiba Satellite A200 laptop dual boot with Windows Vista without any problems excepting this one.

I installed Google Earth 4.3 from Medibuntu Repos. But when I try to run it, it tries to login to the server and then throws me error message **"Unidentified Graphics card"**.See the attached screen shot1.


When I try to start using the terminal the error message is **"Xlib:   extension "GLX" missing on display 0:0 "**. See the attached screen shot2.


I have an integrated Mobile Intel 965 Chipset Video card. No restricted drivers are in use. I am not able to use Compiz or desktop effects.


I have no problem in running Google Earth under Vista in the same machine.


Am I missing anything? Please help

---

### Post by RomeReactor on 2008-06-27
Hi. Looks like your card doesn't have hardware acceleration enabled; please post the output of this:
```
glxinfo | grep rendering
```
I think you need the **intel** driver, as opposed to the **i810**. Try setting it in 'Applications->Other->Screens and Graphics'.

---

### Post by Liakath on 2008-06-27
Dear RomeReactor,

> **RomeReactor said:**
> Hi. Looks like your card doesn't have hardware acceleration enabled; please post the output of this:
```
glxinfo | grep rendering
```
I think you need the **intel** driver, as opposed to the **i810**. Try setting it in 'Applications->Other->Screens and Graphics'.

glxinfo: grep rendering It gives me the same error **"Xlib: extension "GLX" missing on display" 0.0**
I have this driver installed **"xserver-xorg-video-intel version 2:2.2.1 from Hardy Updates"**. I do not have Screens and Graphics installed. How to enable it?

---

### Post by RomeReactor on 2008-06-27
The 'Other' section of the Applications menu is probably unchecked, so it doesn't show up. Right-click on the menu in the top panel, select 'Edit menus' and check the entry for 'Other'. Or, to open the application from the terminal:
```
gksudo displayconfig-gtk
```
Also, please post the output of this, so we know the exact model of your card:
```
lspci -nn | grep VGA
```
and which driver it's currently using:
```
cat /etc/X11/xorg.conf | grep Driver
```

EDIT: If the Screens and Graphics application isn't installed:
```
sudo aptitude install displayconfig-gtk
```

---

### Post by Liakath on 2008-06-28
Dear RomeReactor,

> **RomeReactor said:**
> The 'Other' section of the Applications menu is probably unchecked, so it doesn't show up. Right-click on the menu in the top panel, select 'Edit menus' and check the entry for 'Other'. Or, to open the application from the terminal:
```
gksudo displayconfig-gtk
```
Also, please post the output of this, so we know the exact model of your card:
```
lspci -nn | grep VGA
```
and which driver it's currently using:
```
cat /etc/X11/xorg.conf | grep Driver
```

EDIT: If the Screens and Graphics application isn't installed:
```
sudo aptitude install displayconfig-gtk
```

I could get "displayconfig-gtk" installed through synaptic and Other entry enabled with "Screen and Graphics" added as a new item.
Enabling any other driver like Intel drivers under "gksudo displayconfig-gtk" or from "Screen and Graphics" crashes X and I have to enter recovery mode after restart and fix it with XFIX to get X back with VESA compliant generic driver only.

My video Card from lspci | grep VGA output is
00:02.0 VGA Compatible Controller Intel Corporation Mobile GM965/GL 960 Integrated Graphics Controller (rev 03)

In xorg.conf he entries under driver is only for KBD, MOUSE and SYNAPTIC Pad.

Hope I am able to give all required information for the solution of my problem. I appreciate your help very much.

---

### Post by RomeReactor on 2008-06-28
You might want to try reconfiguring your display: Press CTRL+ALT+F1 to switch to a console; then stop GDM (the display manager):
```
sudo /etc/init.d/gdm stop
```
Then, to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
Usually you should accept the defaults unless you're certain an option needs to be changed; when asked which video driver to use, select **intel**. When the process ends, the display should start automatically and you'll be at your desktop. If the **intel** driver doesn't work, you can reconfigure again, this time choosing the **i810** driver.

---

### Post by Liakath on 2008-06-28
Dear RomeReactor,

Thank you for your continued interest. You wanted me to try

> **RomeReactor said:**
> You might want to try reconfiguring your display: Press CTRL+ALT+F1 to switch to a console; then stop GDM (the display manager):
```
sudo /etc/init.d/gdm stop
```
Then, to reconfigure the display:
```
sudo dpkg-reconfigure xserver-xorg
```
Usually you should accept the defaults unless you're certain an option needs to be changed; when asked which video driver to use, select **intel**. When the process ends, the display should start automatically and you'll be at your desktop. If the **intel** driver doesn't work, you can reconfigure again, this time choosing the **i810** driver.

I have tried the steps given. There is only option for configuring KEYBOARD with the second command. Then it drops me back to the shell after rewriting the xorg.conf file backing up the earlier file. No options for configuring GRAPHICS Card.

Even running these commands after rebooting in to recovery mode also gives the same result.

Thanks once again

The relevant portion of the xorg.conf file

[B]
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc102"
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
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
[/B]

I am using **2.16.24.19-rt kernel** if it could be useful

---

### Post by RomeReactor on 2008-06-28
Try running the reconfigure command like this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Liakath on 2008-06-28
Dear RomeReactor,

Thank you for your continued interest in my problem.

> **RomeReactor said:**
> Try running the reconfigure command like this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Your suggestion I have tried both in X and also after getting in to terminal using CTRL-ALT-F1 stopping GDM using sudo /etc/init.d/gdm stop

Both give almost the same results. See the Screenshot attached. I have tried even using LIVECD the result is always the same. **"No option for GRAPHICS Reconfiguration"**

I have also tried it with LIVECD of LinuxMint5-RC1 with the same results.

---

### Post by RomeReactor on 2008-06-28
Did you try selecting the i810 driver in 'Screens and graphics'? Also, if you have previous generic kernels, try booting into an earlier one and try to run Google Earth. The rt kernel *might* have something to do with this.

I'm out of suggestions at the moment.

---

### Post by Liakath on 2008-06-28
Dear RomeReactor,

Thanks once again for your help.

> **RomeReactor said:**
> Did you try selecting the i810 driver in 'Screens and graphics'? Also, if you have previous generic kernels, try booting into an earlier one and try to run Google Earth. The rt kernel *might* have something to do with this.

I'm out of suggestions at the moment.

I have tried to go back to 2.6.24-19-Generic Kernel which I am presently in. But in this also I have same situation. Configuration of both i810 & intel drivers fail and I am back to vesa driver only.

May be I will wait for the next kernel update to resolve the problem. Hope some one else will be able to add information about how to bring it to their knowlegde.

Thanks once again for all the help and patience to be with me which I appreciate very much

---

### Post by RomeReactor on 2008-06-28
I'm not sure why you have two entries for the video card. Are you using an external monitor? In any case, the the first video card entry shows no driver in use. Have you tried setting the intel or i810 driver there?

Google Earth won't run on your video card using the vesa driver. If using a previous generic kernel hasn't helped, then I doubt it's a problem with it; more likely it's a problem with the video configuration.

---

### Post by Liakath on 2008-06-28
Dear all,

Kindly help me in resolving the above problem. As can be seen in the previous posts several measures have not been able to achieve resolution. May be others in this wonderful community may be able to suggest any other work around. Even after reverting back to 2.6.24-18-generic kernel also the problem remains the same.

Liakath

---

### Post by Liakath on 2008-06-28
Dear RomeReactor,

> **RomeReactor said:**
> I'm not sure why you have two entries for the video card. Are you using an external monitor? In any case, the the first video card entry shows no driver in use. Have you tried setting the intel or i810 driver there?

Google Earth won't run on your video card using the vesa driver. If using a previous generic kernel hasn't helped, then I doubt it's a problem with it; more likely it's a problem with the video configuration.

I was also wondering about why there are two entries there!! I am unable to set any thing in the first entry; any attempts there leads to entry in second one only and it fails. May be reinstalling Hardy Heron could be an option.

May be I should give it a try. I will try with backing up all my updates and home.

Excellent support from you is appreciated. I will post on new development after reinstall.

---

### Post by Liakath on 2008-06-30
Dear RomeReactor,

Thank you for being with me all through this.

> **RomeReactor said:**
> I'm not sure why you have two entries for the video card. Are you using an external monitor? In any case, the the first video card entry shows no driver in use. Have you tried setting the intel or i810 driver there?

Google Earth won't run on your video card using the vesa driver. If using a previous generic kernel hasn't helped, then I doubt it's a problem with it; more likely it's a problem with the video configuration.

Two entries for video card is possibly because I have an option to connect an external monitor or projector on my laptop though I have not used it.

Like I had wondered I had a fresh install of Ubuntu 8.04 and applied all updates. Surprisingly I am able to enable desktop effects and after installing Google Earth from Medibuntu it started working.

However the Graphics Card options remain the same as earlier on running "displayconfig-gtk" as well as the entries in "xorg.conf" are also the same as before reinstall. I have not attempted enabling "i810" or "intel" drivers since I do not want to break the setup. I have not attempted using "Compiz" also.

I am tempted to mark this thread but for not knowing what had fixed it I am still leaving it unmarked. I can post additional information after I return to my Linux Laptop.

---

### Post by RomeReactor on 2008-06-30
Since you are now able to use desktop effects and Google Earth, I suggest that you leave the video configuration as it is. The system seems to have properly configured the video card now.

The video configuration relies more on autodetection now, so some changes made to xorg.conf have little to no effect on how the system manages the display. In many cases, reinstalling the system is the best way to make sure Ubuntu gets the video configuration right.

Glad you solved the problem!

---

### Post by Liakath on 2008-06-30
Dear RomeReactor,

> **RomeReactor said:**
> Since you are now able to use desktop effects and Google Earth, I suggest that you leave the video configuration as it is. The system seems to have properly configured the video card now.

The video configuration relies more on autodetection now, so some changes made to xorg.conf have little to no effect on how the system manages the display. In many cases, reinstalling the system is the best way to make sure Ubuntu gets the video configuration right.

Glad you solved the problem!

I think you are right. Reinstall must have helped with auto-configuration during installation. I will stick to it without any further changes. I will try to use advanced desktop effects with CCSM to see whether it gives me cube and other like options.

I have already marked this thread as solved.

---


---
title: "loads of games give me glx visual error"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-09-27
some games check through loads of different resolutions 1st.

```


Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Desired video mode fail, trying fallbacks...
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 1024x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x768x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x768: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x32x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x480: Couldn't find matching GLX visual
Initializing Video Mode: fullscreen 640x480x16x60hz
Linked against SDL version 1.2.12
Using SDL library version 1.2.12
Failed to set video mode to 640x480: Couldn't find matching GLX visual
 Video modes failed


```

the output of lspci is

```

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
03:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


```

my screen resolution is:  

1280 X 1024 60 HZ

no other resolutions work. They just either go black or funny.


thanks in advance for any help

---

### Post by pluckypigeon on 2008-09-28
anyone?:( I can post more information.

---

### Post by Nepherte on 2008-09-28
The only thing I can think of is that the 3d acceleration driver isn't working somehow. I see you have a intel vga, but the driver should support it rightaway. Does this work?
```
glxgears
```

---

### Post by pluckypigeon on 2008-09-28
> **Nepherte said:**
> The only thing I can think of is that the 3d acceleration driver isn't working somehow. I see you have a intel vga, but the driver should support it rightaway. Does this work?
```
glxgears
```

Thank you for your help. I get this

```


Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual


```

---

### Post by Nepherte on 2008-09-28
That only confirms my thoughts. Can you post your xorg.conf file?
```
cat /etc/X11/xorg.conf
```

---

### Post by DrMega on 2008-09-28
What does the following command return:

```

glxinfo | grep rendering

```

---

### Post by nowshining on 2008-09-28
you will more than likely have to install the Drivers for ATI/Nvidia direct from the manufacturers site...

---

### Post by DrMega on 2008-09-28
> **nowshining said:**
> you will more than likely have to install the Drivers for ATI/Nvidia direct from the manufacturers site...

This shouldn't be necessary. They are in the repositories.

@OP - You haven't by any chance activate GL Desktop have you? I'm not sure of its purpose but I once switched it on in error and it disabled all my hardware acceleration.

---

### Post by lavinog on 2008-09-28
> **nowshining said:**
> you will more than likely have to install the Drivers for ATI/Nvidia direct from the manufacturers site...

why?
> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

I don't know much about the intel video cards, but I don't see why the op would need ATI/Nvidia drivers.

---

### Post by nowshining on 2008-09-28
> **lavinog said:**
> why?

I don't know much about the intel video cards, but I don't see why the op would need ATI/Nvidia drivers.

srry i didn't notice it was an intel card - my bad...

---

### Post by pluckypigeon on 2008-09-29
> **Nepherte said:**
> That only confirms my thoughts. Can you post your xorg.conf file?
```
cat /etc/X11/xorg.conf
```

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
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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
EndSection






```

---

### Post by pluckypigeon on 2008-09-29
> **DrMega said:**
> What does the following command return:

```

glxinfo | grep rendering

```

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



```

---

### Post by pluckypigeon on 2008-09-29
anyone have an ideas?

---

### Post by Nepherte on 2008-09-29
Let's backup your current xorg file first, just in case things go wrong:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Now open up your xorg file:
```
gksudo gedit /etc/X11/xorg.conf
```

Add the following section:
```
Section "Module"
        Load  "glx"
EndSection
```
and save the file. Now restart the x-server by pressing ctrl+alt+backspace.

When you don't get any graphics, you can simply restore your old settings with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by pluckypigeon on 2008-09-29
> **Nepherte said:**
> Let's backup your current xorg file first, just in case things go wrong:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Now open up your xorg file:
```
gksudo gedit /etc/X11/xorg.conf
```

Add the following section:
```
Section "Module"
        Load  "glx"
EndSection
```
and save the file. Now restart the x-server by pressing ctrl+alt+backspace.

When you don't get any graphics, you can simply restore your old settings with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Thanks for your reply but that didn't work!!

:(:(:(:(:(:(

---

### Post by DrMega on 2008-09-29
> **pluckypigeon said:**
> Thanks for your reply but that didn't work!!

:(:(:(:(:(:(

Now that you've backed up your xorg.conf, you could try reconfiguring xserver with the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

It has worked in the past for me (I had a slightly different problem though).

---

### Post by pluckypigeon on 2008-09-30
> **DrMega said:**
> Now that you've backed up your xorg.conf, you could try reconfiguring xserver with the following command:

```
sudo dpkg-reconfigure xserver-xorg
```

It has worked in the past for me (I had a slightly different problem though).

thanks but no joy:(:(

---

### Post by nowshining on 2008-09-30
go thru synaptic and install mesagl stuff, or whatever it's called...

---

### Post by pluckypigeon on 2008-09-30
> **nowshining said:**
> go thru synaptic and install mesagl stuff, or whatever it's called...

Everything is installed apart from the stuff that wants to remove ubuntu-desktop

---

### Post by pluckypigeon on 2008-09-30
I don't want to have to keep bumping this but it's really starting to frustrate me. :confused::confused:

---

### Post by Nepherte on 2008-09-30
Try adding, in addition to the glx earlier:
```
Section "Module"
    Load           "glx"
    #Load          "dri" 
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
You could also try uncommenting the load "dri" as well.

---

### Post by pluckypigeon on 2008-10-01
> **Nepherte said:**
> Try adding, in addition to the glx earlier:
```
Section "Module"
    Load           "glx"
    #Load          "dri" 
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
You could also try uncommenting the load "dri" as well.

thanks but no luck.

---

### Post by pluckypigeon on 2008-10-01
I never knew I had this problem before because I've never tried to play games really before.

---

### Post by Roanoke on 2009-04-01
I have the same problem.

---

### Post by sloggerkhan on 2009-05-10
I have the same problem. Trying to use nvidia proprietary driver.
```

$ glxinfo 
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

```

---

### Post by waltons_pacman on 2009-05-26
i have the same problem on mine.

---

### Post by A Future Pilot on 2009-08-14
(First of all I don't know how old this post is, I have close to the same problem and was googling it and found this...)

I don't have quite the same problem but...

When I try to run d1x-rebirth it tells me:

```
Error: Could not set 640x480x32 opengl video mode: Couldn't find matching GLX visual

Error: Could not set 640x480x32 opengl video mode: Couldn't find matching GLX visual
```

The difference in my problem, and the original poster is that when I run glxgears, it morks fine. I have Load "glx" Load "dri" and Load "dri2" all in my xorg.conf. Can anyone help me?

---

### Post by lavinog on 2009-08-14
I would suggest starting a new thread. Even though the problem looks similar, you may have different hardware, different drivers/versions that make this problem different.

When you start a new thread, please mention what video card you have and if you enabled any restricted drivers.

---


---
title: "HOWTO: ATI drivers"
date: 2005-03-28
forum: Outdated Tutorials &amp; Tips
---

### Post by teumima on 2005-03-28
Ok, there have been many many posts about this, many users breaking their heads over this.

I've been trying to get it to work for months. Finally last night I stayed up chatting with guys at #ati on irc.freenode.org and finally here's the solution. I simply have to share this with everyone as there were certain things I need to change in order for the graphics to work that I have not seen mentioned anywhere else (doesn't mean that they don't exist).

First of all: BACKUP BACKUP BACKUP!

Second, but not least: Don't just copy and past all the commands, make sure I don't have any typos and that you have those dir, ideally type it in and use the tab key to complete.

There is no need to make your life more miserable by reinstalling your Ubuntu everytime you screw things up (That's why I left Windows, at least one of the 10 billions of reasons)

Do:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Now:

Download this file:

[http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.10.19-1.i386.rpm](http://www2.ati.com/drivers/linux/fglrx_6_8_0-8.10.19-1.i386.rpm)

Once downloaded go to the dir you downloaded it to. Always a good idea to create a downloads file in your home dir. Do: (only for ubuntu & debian users)

sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm 

Now you should have the following .deb package:

fglrx-6-8-0_8.10.19-2_i386.deb

Type:

sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb

You have to force overwrite otherwise it wont install. Mesa wont let you.

Now we need to edit you xorg.conf

Now it's time to configure:

type fglrxconfig

also type in another terminal:

sudo gedit /etc/X11/xorg.conf

you will need to find your monitor frequencies, in order to punch them in to your fglrxconfig when it asks you for them. Before writing your fglrxconfig to file make sure to close your xorg.conf.

In fglrxconfig the defaults should work fine, when it comes where it asks you to use external AGP choose "YES" note the default is "no" for those trigger happy users who just press the enter key without thinking much.

when you come to the the hsync (horizontal sync) and vsync (vertical sync) part choose the option which allows you to enter a custom range (the last option). Copy what is in your xorg.conf "monitor" section and paste it.

Save the file. Restart X, reboot, whatever u want.

type:

sudo gedit /etc/X11/xorg.conf

Make sure your Device section looks like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
            Option          "backingstore"          "true"
	Option          "UseInternalAGPGART"    "no"  
EndSection

Obviously if you don't have a radeon 9200 the identifier will be different. The important ones are Driver should be the same, Option 1 and Option 2

Now go to the Modules section:

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Note the Load "dri" if it's not there add it.

Now go to the "extensions" section, it should look like this:

Section "Extensions"
	Option 	"Composite" "Disable"
EndSection


NOTE: It's either 3D accl graphics or composite effects such as fading and shadowns, not both. Make your choice. To me the choice is obvious. If it's important to you, then an NVIDIA card should be your next choice.

Ok, almost there!

type:

cd /lib/modules/fglrx/build_mod/

sudo sh make.sh

For the next command you need to be out of X. I press ctrl +alt+ F2

cd /lib/modules/fglrx

sh make_install.sh

startx

If sh make.sh give  you errors then you'll  need to apt-cache

Unfortunately it was late at  night so I don't remember the command, I will try and find it and then edit thei HOWTO, if anyone else know what it is, please post it.

I deffinetaly needed it, so I'm sure others do too.

Hope this helped.

feel free to ask me.

---

### Post by Shaggy on 2005-03-28
It should be noted that you should try this method if using the normal packages does not work, which it does for some people(me included).

Normal method being download and install the xorg-driver-fglrx, fglrx-control, and most importantly linux-restricted-modules-<kernel type> using apt/synaptic.

And then changing the line in your xorg.conf file from reading 

Driver        "ati" 

to reading 

Driver        "fglrx"

---

### Post by PinGzor on 2005-03-28
Thanks, it's working here now.

But i only get ~115 fps in glxgears. I got ~880 in slackware
Are you familiar to this problem?

---

### Post by ChaperonNoir on 2005-03-28
In glxgears, with MESA GL, i get like 350-400 fps.


With FGLRX i get 4000 FPS :)

---

### Post by budge on 2005-03-28
[QUOTE=Shaggy]It should be noted that you should try this method if using the normal packages does not work, which it does for some people(me included).

Normal method being download and install the xorg-driver-fglrx, fglrx-control, and most importantly linux-restricted-modules-<kernel type> using apt/synaptic.

And then changing the line in your xorg.conf file from reading 

Driver        "ati" 

to reading 

Driver        "fglrx"[/QUOTE]

Hi Did the above but now get this error message when I try to change screen resolution.
Any help appreiciated.

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

---

### Post by bobmitch on 2005-03-28
[QUOTE=budge]Hi Did the above but now get this error message when I try to change screen resolution.
Any help appreiciated.

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."[/QUOTE]

When using the fglrx driver, you must configure your resolution in the xorg.conf file - resolution changes cannot be made on-the-fly.

Look for the Subsection "Display" in the "Screen" section - specifically the "Modes" line.  The order of these modes is the order X will try them until it gets one that works - make sure you have your desired mode first.

---

### Post by teumima on 2005-03-28
The best indication for if your driver works is not the glgears test, but running an app.

After all if ur apps are running smooth, what do u care?

Try an app and see if it works slow. If you are still using mesa as your gl, that is a msitake and needs to be fixed. If you followed the steps exactly as I mentioned mesa should have been replaced with ati.

Sometimes I get 2000 sometimes 500 and yet I play half-life 2 and its always smooth.

---

### Post by teumima on 2005-03-28
[QUOTE=PinGzor]Thanks, it's working here now.

But i only get ~115 fps in glxgears. I got ~880 in slackware
Are you familiar to this problem?[/QUOTE]

Seems to me that mesa is still in charge. Did you check?

type fglrxinfo

---

### Post by PinGzor on 2005-03-28
It's using Mesa and i have checked my xorg.conf and it looks fine

---

### Post by Slavakion on 2005-03-28
Tried this in Warty, and of course X didn't like it. Had to fix it from command line. (sorry, just proud of myself for fixing a linux problem)

---

### Post by teumima on 2005-03-28
[QUOTE=PinGzor]It's using Mesa and i have checked my xorg.conf and it looks fine[/QUOTE]
 Man, its working fine with mesa??? obviously not if ur only getting 150 FPS, Did you follow the instructions?

---

### Post by Randabis on 2005-03-28
[QUOTE=PinGzor]It's using Mesa and i have checked my xorg.conf and it looks fine[/QUOTE]
What ATI chipset are you using?

---

### Post by PinGzor on 2005-03-28
[QUOTE=Randabis]What ATI chipset are you using?[/QUOTE]

Im using Ati Radeon 9600 M10 (Laptop)

---

### Post by ChaperonNoir on 2005-03-28
Look if in your xorg.conf.


You see driver : fglrx instead of ati.

When i did this, everything worked.

---

### Post by PinGzor on 2005-03-28
This is my xorg.conf, can you guys se anything wrong?

fglrx is probed, but X aint loading it

```
# **********************************************************************
# DRI Section
# **********************************************************************

Section "dri"
    Mode 0666
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************

Section "Module"

# This loads the DBE extension module.

#    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
#    SubSection  "extmod"
#      Option    "omit xfree86-dga"   # don't initialise the DGA extension
#    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"
    Load	"bitmap"
    Load	"dbe"
    Load	"dbc"
    Load	"dri"
    Load	"glx"
    Load	"extmod"
    Load	"int10"
    Load	"record"
    Load	"vbe"
    Load	"fglrx"
# This loads the GLX module
    Load        "glx"  # libglx.a
    Load        "dri"  # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

#    Option "NoTrapSignals"

#    Option "DontZap"

#    Option "Dont Zoom"

#    Option "DisableVidModeExtension"

#    Option "AllowNonLocalXvidtune"

#    Option "DisableModInDev"

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"se"

EndSection

# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/psaux"

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"
#    Option "ChordMiddle"

EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 48.4
    VertRefresh 20 - 60
    Option "DPMS"

EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "ATI Graphics Adapter"
    VendorName  "ATI"
    BoardName   "Radeon 9600"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "fglrx"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

    BusID       "PCI:1:0:0"
    Option "backingstore" "true"
    Option "UseInternalAGPGART" "no"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection



# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    Option "backingstore" "true"

    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

Section "ServerLayout"

    Identifier  "Server Layout"
    Screen "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection
```

---

### Post by Jesus Franco on 2005-03-28
Try putting the DRI section at the bottom of the file. Also the Internal AGP GART should only be removed if you are using a NFORCE2 chipset mobo, if your not then delete that line so that it can be functional.

This is what I think yours should look like :D


# **************************************************  ********************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **************************************************  ********************

Section "Module"

# This loads the DBE extension module.

#    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
#    SubSection  "extmod"
#      Option    "omit xfree86-dga"   # don't initialise the DGA extension
#    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"
    Load	"bitmap"
    Load	"dbe"
    Load	"dbc"
    Load	"dri"
    Load	"glx"
    Load	"extmod"
    Load	"int10"
    Load	"record"
    Load	"vbe"
    Load	"fglrx"
# This loads the GLX module
    Load        "glx"  # libglx.a
    Load        "dri"  # libdri.a

EndSection

# **************************************************  ********************
# Files section.  This allows default font and rgb paths to be set
# **************************************************  ********************

Section "Files"

    RgbPath	"/usr/X11R6/lib/X11/rgb"

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **************************************************  ********************
# Server flags section.
# **************************************************  ********************

Section "ServerFlags"

#    Option "NoTrapSignals"

#    Option "DontZap"

#    Option "Dont Zoom"

#    Option "DisableVidModeExtension"

#    Option "AllowNonLocalXvidtune"

#    Option "DisableModInDev"

#    Option "AllowNonLocalModInDev"

EndSection

# **************************************************  ********************
# Core keyboard's InputDevice section
# **************************************************  ********************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"se"

EndSection

# **************************************************  ********************
# Core Pointer's InputDevice section
# **************************************************  ********************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/psaux"

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"
#    Option "ChordMiddle"

EndSection

# **************************************************  ********************
# Monitor section
# **************************************************  ********************

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 48.4
    VertRefresh 20 - 60
    Option "DPMS"

EndSection

# **************************************************  ********************
# Graphics device section
# **************************************************  ********************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "ATI Graphics Adapter"
    VendorName  "ATI"
    BoardName   "Radeon 9600"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "fglrx"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

    BusID       "PCI:1:0:0"
    Option "backingstore" "true"
    Option "UseInternalAGPGART" "no"
# Comment out the line above with a # if your motherboard isnt a nforce 2 chipset.
#    VideoRam    256

#    Clocks      25.2 28.3

EndSection



# **************************************************  ********************
# Screen sections
# **************************************************  ********************

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    Option "backingstore" "true"

    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection
EndSection

# **************************************************  ********************
# ServerLayout sections.
# **************************************************  ********************

Section "ServerLayout"

    Identifier  "Server Layout"
    Screen "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

# **************************************************  ********************
# DRI Section
# **************************************************  ********************

Section "dri"
    Mode 0666
EndSection

---

### Post by Liau on 2005-03-28
Hi

Everything went well up till the part where I had to do

sudo sh make.sh

I got an error message that said:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h


and so sh make_install.sh wouldn't work either :(

Any idea how I might solve this problem?

thanks!

---

### Post by nehalem on 2005-03-29
I guess I'm lucky in that the hoary ones work for me (and much better than the warty ones ever did since I have yet to experience a crash).

Just curious why ATI doesn't support composite stuff.  It's surprising fun to mess with that stuff.

---

### Post by budge on 2005-03-29
[QUOTE=bobmitch]When using the fglrx driver, you must configure your resolution in the xorg.conf file - resolution changes cannot be made on-the-fly.

Look for the Subsection "Display" in the "Screen" section - specifically the "Modes" line.  The order of these modes is the order X will try them until it gets one that works - make sure you have your desired mode first.[/QUOTE]

Thanks...all looking good again. :-)

---

### Post by bobmitch on 2005-03-29
[QUOTE=Liau]Hi

Everything went well up till the part where I had to do

sudo sh make.sh

I got an error message that said:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h


and so sh make_install.sh wouldn't work either :(

Any idea how I might solve this problem?

thanks![/QUOTE]

Looks like you need to install the linux headers for your kernel version from synaptic.

---

### Post by teumima on 2005-03-29
[QUOTE=Liau]Hi

Everything went well up till the part where I had to do

sudo sh make.sh

I got an error message that said:

ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h


and so sh make_install.sh wouldn't work either :(

Any idea how I might solve this problem?

thanks![/QUOTE]
 yeah man that is the part that i dont remember how to do. I ahd the exact problem. Go to irc.freenode.org and join #ati ask them there. You have to apt-cache certain headers and then it will work.

---

### Post by Dracontopes on 2005-03-29
You have to install the linux-headers for your kernel version.

Do: ```
sudo apt-get install linux-headers
```
(or something similar, you should be able to select/find the correct name of the package by searching for it in synaptic)

---

### Post by bradword on 2005-03-30
I have followed the instructions and I'm still having problems.  I'm using an ATI 9700 Pro on a dell system.  When I do fglrxinfo I am still getting Mesa as the main 3d component. 

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
        Load    "fglrx"
EndSection

Section "Extensions"
	Option	"Composite" "Disable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"backingstore"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option 		"UseInternalAGPGART"	"no"
EndSection

Section "Monitor"
	Identifier	"DELL 1800FP"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9700 Pro (R300 ND)"
	Monitor		"DELL 1800FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#Option "composite" "Disable"
#EndSection
``` 

Any ideas please?

---

### Post by bradword on 2005-03-30
I have also tried this code 

```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
    Load 	"flgrx"

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30-70
    VertRefresh 56-85
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    Option "backingstore"		"true"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e44
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "800x600" "1024x768" "1280x1024"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "Extensions"

    Option  "Composite"  	"Disable"

EndSection

### EOF ###
```

---

### Post by Liau on 2005-03-30
Hi again

I managed to fix the problem of make.sh not working by following the instructions at this link

[http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module](http://www.ubuntulinux.org/support/documentation/faq/compile-kernel-module)

It turns out I was indeed missing the kernel headers :)

Unfortunately, even after successfully running make.sh and make_install.sh, fglrxinfo still tells me that Mesa is running : /



I think make.sh didn't run perfectly though, here's the output when i type in "sudo sh make.sh"

ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.



Does anyone have any ideas what that warning message means, if anything?

Thanks for the quick replies btw everybody, I appreciate it!

---

### Post by bobmitch on 2005-03-31
Well, it does say it has succeeded, so I would go ahead and try continuing with the installation.  You`ll know if it hasn`t worked properly when you come to attempt the modprobe.

If you have your old xorg.conf backed up you have nothing to lose. :)

Good luck.

---

### Post by teumima on 2005-03-31
Ok guys this is what you have to download if your sh make.sh doesn't work.

type:

 sudo apt-cache search linux-headers

find your platform. Most people have a 386 kernel, so download the one with the 386 which is:

linux-headers-2.6.10-5-386 - Linux kernel headers 2.6.10 on 386

or 

linux-headers-386 - Linux kernel headers on 386

type:

sudo apt-get install linux-headers-386

now you probably noticed the linux-headers-2.6.11-1-386. Do not dowload that, as your kernel is only 2.6.10-5. Don't go looking for the 2.6.11-1 kernel either, as it's not supported yet, and if like me u want to be at the edge of things and end up downloading it your linux will freeze after login in X.

---

### Post by gasley on 2005-04-01
Hi, i'm still having trouble getting this to work. I did everything described in the first post and fglrxinfo still says I'm using Mesa :|

Here are the contents of my xorg.conf

```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
    
    Load "bitmap"
    Load "ddc"
    Load "extmod"
    Load "int10"
    Load "record"
    Load "vbe"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection



# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************


Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"fi"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 91.1
    VertRefresh 60 - 100
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

#Section "Device"
#    Identifier  "Standard VGA"
#    VendorName  "Unknown"
#    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

#    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

#EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"

    Option "backingstore" "true"

    BusID "PCI:2:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###
``` 

Any help would be appreciated, thanks.

---

### Post by Jujimufu on 2005-04-01
[QUOTE=gasley]Hi, i'm still having trouble getting this to work. I did everything described in the first post and fglrxinfo still says I'm using Mesa :|[/QUOTE]

I'm having this problem too.  I followed the first post pretty closely (Closely is an understatement considering the reason I'm using Ubuntu now is because I actually ruined my Fedora 3 *trying* to get this crap to work: [color=gray]*Fedora wasn't as good as Ubuntu anyway, too much bloat.*[/color])

I'm having the same troubles as Gasley.  Fglrxinfo still says I'm using Mesa - and the xorg.conf file just doesn't seem to be what it should.  I've followed fglrxconfig, it was rewritten differently - but it seems sketchy.  For example: Under devices it says

> 
# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"


Yeah?  Why?  I wasn't recieving errors or anything all the way through - no harm done thus far.  But my xorg.conf file just doesn't seem right anyway.

---

### Post by Dracontopes on 2005-04-01
That section about the Standard VGA is just an example that fglrxconfig put there.

Okay, I can see you have set UseInternalAGPGART "no". Setting this to yes would crash the X server right? (it does here) 

Might be helpful if you post your Xorg.log.0 (or something like that) here, this greatly increases the help we can give you.

Edit: Oh and Liau, that error message is quite 'normal', it appeared on my rig too, but fglrx is working, so you can ignore the error.

```
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
```

---

### Post by Jujimufu on 2005-04-01
[QUOTE=Shaggy]It should be noted that you should try this method if using the normal packages does not work, which it does for some people(me included).

Normal method being download and install the xorg-driver-fglrx, fglrx-control, and most importantly linux-restricted-modules-<kernel type> using apt/synaptic.

And then changing the line in your xorg.conf file from reading 

Driver        "ati" 

to reading 

Driver        "fglrx"[/QUOTE]

Holy crap it worked!  I uninstalled the fglrx-6-8-0 file from synaptic.  Then I installed the fglrx-control and the xorg-driver-fglrx files from synaptic.  Restarted X, and VOILA! Direct rendering: Yes //  And glxgears gave off FPS above 10,000.  I'm an idiot who lucked out after ruining one OS and spending a couple weeks on this.  WOO!!

---

### Post by allans on 2005-04-01
[QUOTE=Jujimufu]Holy crap it worked!  I uninstalled the fglrx-6-8-0 file from synaptic.  Then I installed the fglrx-control and the xorg-driver-fglrx files from synaptic.  Restarted X, and VOILA! Direct rendering: Yes //  And glxgears gave off FPS above 10,000.  I'm an idiot who lucked out after ruining one OS and spending a couple weeks on this.  WOO!![/QUOTE]

I've just done the same thing, using fglrx-6-8-0 from the ati website worked for all the kernels bar 2.6.10-5, but the "official" hoary drivers now work.  People should also realise that forcing fglrx-6-8-0 to install will cause problems with mesa packages later on, did with me anyway.

Is there anyway of getting a gtk based ati-control?  I wanted to install it but didn't want to install the qt library.

Allan

---

### Post by gasley on 2005-04-02
[QUOTE=Dracontopes]
Might be helpful if you post your Xorg.log.0 (or something like that) here, this greatly increases the help we can give you.[/QUOTE]

I was supposed to post that logfile too, but I seem to have forgotten that.

Had to upload it to my homepages, since it was too big to post inside code-tags or as an attachment: [Xorg.0.log](http://wesley.laatikko.org/Xorg.0.log.txt)

---

### Post by seven on 2005-04-02
it works perfect, but unreal 2004 works slower than windows :(
glxgears gets 3034.600 fps (radeon 9600PRO with 128MB).
is this score normal for this video card?

*sorry if i had any english grammer \ spelling mistake.
english isn't my native

---

### Post by teumima on 2005-04-02
[QUOTE=gasley]Hi, i'm still having trouble getting this to work. I did everything described in the first post and fglrxinfo still says I'm using Mesa :|

Here are the contents of my xorg.conf

```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
    
    Load "bitmap"
    Load "ddc"
    Load "extmod"
    Load "int10"
    Load "record"
    Load "vbe"
EndSection

Section "Extensions"
    Option "Composite" "Disable"
EndSection



# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************


Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"fi"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 91.1
    VertRefresh 60 - 100
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

#Section "Device"
#    Identifier  "Standard VGA"
#    VendorName  "Unknown"
#    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

#    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

#EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"

    Option "backingstore" "true"

    BusID "PCI:2:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###
``` 

Any help would be appreciated, thanks.[/QUOTE]
 Hey man

add this option to your device section

Option          "UseInternalAGPGART"    "no"

---

### Post by gasley on 2005-04-02
[QUOTE=teumima]Hey man

add this option to your device section

Option          "UseInternalAGPGART"    "no"[/QUOTE]

I guess you missed it, it is already there :)

---

### Post by laggerzero on 2005-04-02
I'm using the latest hoary releace (RC) and have installed the drivers through synaptic aswell as the kenrel headers and am still having problems. Here is the part of my xorg log where it started giving me probs.

```

(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8de0000
(II) fglrx(0): [drm] mapped SAREA 0xf8de0000 to 0xb7dab000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xd0020000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8de0000 at 0xb7dab000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,960) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 960)
(II) fglrx(0): Largest offscreen area available: 1280 x 7227
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

```

Here is my xorg.conf:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Sony G500"
	Option		"DPMS"
	HorizSync	30-121
	VertRefresh	48-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x960" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by bobmitch on 2005-04-02
[QUOTE=laggerzero]I'm using the latest hoary releace (RC) and have installed the drivers through synaptic aswell as the kenrel headers and am still having problems. Here is the part of my xorg log where it started giving me probs.

<snip>

[/QUOTE]

If you are going to use these drivers, please use the **fglrxconfig** application supplied to generate an X config file.

---

### Post by ola on 2005-04-02
I did actually get the fglrx drivers to work with the apt-getted ones. But 2D seems to SUCK with those drivers..  The mesa ones is MUCH better, not good, but better..

Is there any reason for me to try these or will it be the same?

I dont need any super acceleration, but to get the windows move smooth would be a big plus!

Thanks

.o

---

### Post by bobmitch on 2005-04-02
[QUOTE=ola]I did actually get the fglrx drivers to work with the apt-getted ones. But 2D seems to SUCK with those drivers..  The mesa ones is MUCH better, not good, but better..

Is there any reason for me to try these or will it be the same?

I dont need any super acceleration, but to get the windows move smooth would be a big plus!

Thanks

.o[/QUOTE]

If you are not using 3d applications/games, it would probably be better to stick with the open source drivers.

---

### Post by laggerzero on 2005-04-02
When i run the fglrxconfig that comes with hoary it says it is designed fro xf86config; hoary uses xorg. when i try to use it, X won't start; even if i rename it xorg.conf

---

### Post by dafrabbit on 2005-04-02
Can you give us your xorg log? It is at /var/log/Xorg.0.log

---

### Post by bradword on 2005-04-03
I also did the uninstall and install through synaptec as described a few posts back.  It also worked for me!  I would suggest anyone with ati to do as described there first as it is simple and quick.  I am now getting 3000+ fps in glxgears and I can now play World of Warcraft in cedega!  It all runs very smooth.  Thank you very much for everyone's effort and help in this issue.

I have tried MANY linux distros and always get frustrated at the lack of community and help.  If I would ask a question they would give me a few steps that only a linux guru would know.  Here you help with step by step directions that I can follow and learn from.   Kudos to the Ubuntu community, the best one around!

---

### Post by ola on 2005-04-03
[QUOTE=bobmitch]If you are not using 3d applications/games, it would probably be better to stick with the open source drivers.[/QUOTE]

OK. Thanks. If I'm to annoied Ill switch to my GF3 card instead..

---

### Post by laggerzero on 2005-04-04
Sorry for my delayed response. I might just format since there is probably conflicts between the two drivers since i have tried them both. Which method is guaranteed to give me 3D support? anyways, here is my xorg log:

NOTE: I had to trim some of the fat off since it was too large to paste in.

```

(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(--) Chipset RADEON 9800 PRO (R350 4E48) found
(II) fglrx(0): pEnt->device->identifier=0x820e6c0
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(==) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9800 PRO (R350 4E48)" (Chipset = 0x4e48)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: original ATI grafics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
(--) fglrx(0): MMIO registers at 0xd0020000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x01
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 0
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 0
(II) fglrx(0): Primary head:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Overlay disabled
(==) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Generic Monitor: Using hsync range of 30.00-121.00 kHz
(II) fglrx(0): Generic Monitor: Using vrefresh range of 48.00-160.00 Hz
(II) fglrx(0): Clock range:  20.00 to 400.00 MHz
(II) fglrx(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) fglrx(0): Not using default mode "1920x1440" (hsync out of range)
(II) fglrx(0): Not using default mode "960x720" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (hsync out of range)
(II) fglrx(0): Not using default mode "1024x768" (hsync out of range)
(II) fglrx(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) fglrx(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) fglrx(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) fglrx(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) fglrx(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) fglrx(0): Not using default mode "1440x900" (width too large for virtual size)
(--) fglrx(0): Virtual size is 1280x960 (pitch 1280)
(**) fglrx(0): *Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
(**) fglrx(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) fglrx(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) fglrx(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) fglrx(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) fglrx(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) fglrx(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) fglrx(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) fglrx(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) fglrx(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 170.2 MHz, 120.2 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "1024x768"  170.24  1024 1108 1220 1416  768 768 770 801 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "1024x768"  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) fglrx(0):  Default mode "960x720": 148.5 MHz, 112.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "960x720"  148.50  960 1032 1144 1320  720 720 722 750 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "960x720"  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "928x696": 144.0 MHz, 112.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "928x696"  144.00  928 992 1104 1280  696 696 698 750 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "928x696"  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "896x672": 130.5 MHz, 106.3 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "896x672"  130.50  896 944 1052 1228  672 672 674 708 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "896x672"  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync
(**) fglrx(0):  Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(II) fglrx(0): Modeline "960x600"  115.00  960 968 1048 1264  600 600 602 625 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "960x600"   96.58  960 1024 1128 1296  600 600 602 621 doublescan
(**) fglrx(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) fglrx(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) fglrx(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) fglrx(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 114.8 MHz, 106.2 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "800x600"  114.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "800x600"  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) fglrx(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) fglrx(0):  Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(II) fglrx(0): Modeline "700x525"   92.00  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) fglrx(0): Modeline "700x525"   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   78.75  640 672 752 864  512 512 514 536 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) fglrx(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(II) fglrx(0): Modeline "640x480"   74.25  640 672 752 864  480 480 482 505 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) fglrx(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) fglrx(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) fglrx(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) fglrx(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) fglrx(0):  Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) fglrx(0): Modeline "576x432"   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync
(**) fglrx(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) fglrx(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) fglrx(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) fglrx(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) fglrx(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) fglrx(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) fglrx(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) fglrx(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) fglrx(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) fglrx(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) fglrx(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(==) fglrx(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x00000729
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) fglrx(0): UMM area:     0xc06b1000 (size=0x0794f000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
(WW) fglrx(0): could not detect XFree86 version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8d83000
(II) fglrx(0): [drm] mapped SAREA 0xf8d83000 to 0xb7dab000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xd0020000
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d83000 at 0xb7dab000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xc0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,960) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 960)
(II) fglrx(0): Largest offscreen area available: 1280 x 7227
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!


```

---

### Post by dafrabbit on 2005-04-04
Hrmm....well if there is nothing critical, a reinstall of hoary is probably the easiest. As for drivers, I'm using the one in hoary, it was just recently updated the 8.8.25 so unless I've misunderstood something there doesn't appear to be any advantage to compiling your own. Especially because the hoary one just worked for me (just sudo apt-get install xorg-driver-fglrx)

Sorry to say that I can't help you....just newbie at the whole linux thing myself.  ;-)

---

### Post by laggerzero on 2005-04-04
Ok, did a fresh install of hoary and am using the fglrx drivers that you get through apt.

After examining the Xorg log more closely i noticed this:

```

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EBUSY"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8da9000 at 0xb7db6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Is that my problem? If so, how do I fix this.

---

### Post by teumima on 2005-04-05
Hi

did you do make.sh?

---

### Post by teumima on 2005-04-05
[QUOTE=allans]I've just done the same thing, using fglrx-6-8-0 from the ati website worked for all the kernels bar 2.6.10-5, but the "official" hoary drivers now work.  People should also realise that forcing fglrx-6-8-0 to install will cause problems with mesa packages later on, did with me anyway.

Is there anyway of getting a gtk based ati-control?  I wanted to install it but didn't want to install the qt library.

Allan[/QUOTE]
 Hey man

All you'll need to do is shutdown x: sudo /etc/init.d/gdm stop
remove fglrx: sudo apt-get remove fglrx-6-8-0
update xlibmesa: sudo apt-get install xlibmesa-gl
reinstall the fglrx: sudo apt-get dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb
startx: startx

Then you'll have your mesa-gl updated, your fglrx graphics 100% and no  headache ;)

P.S. Taken from Dracontopes post, when he helped me with this.

---

### Post by allans on 2005-04-05
[QUOTE=teumima]Hey man

All you'll need to do is shutdown x: sudo /etc/init.d/gdm stop
remove fglrx: sudo apt-get remove fglrx-6-8-0
update xlibmesa: sudo apt-get install xlibmesa-gl
reinstall the fglrx: sudo apt-get dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb
startx: startx

Then you'll have your mesa-gl updated, your fglrx graphics 100% and no  headache ;)

P.S. Taken from Dracontopes post, when he helped me with this.[/QUOTE]

Hey thanks for the reply, I'll remember that for breezy development!  I'm happy enough with the hoary drivers for now, but ati do need to get em sorted, I can't restart X with these drivers and stuff like that.  Beginning to wish I'd gone nvidia...

Allan

---

### Post by allans on 2005-04-05
[QUOTE=seven]it works perfect, but unreal 2004 works slower than windows :(
glxgears gets 3034.600 fps (radeon 9600PRO with 128MB).
is this score normal for this video card?

*sorry if i had any english grammer \ spelling mistake.
english isn't my native[/QUOTE]

I think that UT2004 uses direct x rendering on windows, I could be wrong here but I'm pretty sure that was the way they went.  Obviously on linux opengl is the only option, so performance is likely to be better on the windows platform.  If ut2004 does use opengl on windows and I'm wrong then I'd put it down to the drivers, ati is fairly infamous for its opengl drivers!

Allan

---

### Post by bobmitch on 2005-04-06
[QUOTE=allans]I think that UT2004 uses direct x rendering on windows, I could be wrong here but I'm pretty sure that was the way they went.  Obviously on linux opengl is the only option, so performance is likely to be better on the windows platform.  If ut2004 does use opengl on windows and I'm wrong then I'd put it down to the drivers, ati is fairly infamous for its opengl drivers!

Allan[/QUOTE]

UT2004 on windows uses Direct3d - but also has an opengl rendering path - classed as 'experimental'.  So it is likely to be slower using opengl on windows as well as linux.

---

### Post by teumima on 2005-04-06
[QUOTE=allans]Hey thanks for the reply, I'll remember that for breezy development!  I'm happy enough with the hoary drivers for now, but ati do need to get em sorted, I can't restart X with these drivers and stuff like that.  Beginning to wish I'd gone nvidia...

Allan[/QUOTE]
 NVIDIA will be my next option. But what do you mean you can't restart X?

---

### Post by allans on 2005-04-06
[QUOTE=teumima]NVIDIA will be my next option. But what do you mean you can't restart X?[/QUOTE]

Well whenever I try ctrl + alt + backspace, my monitor tells me that there is no video input and I'm forced to restart the computer, I can't even get to a terminal by ctrl + alt + f1.  I'm putting this down to the drivers because when I used the latest drivers from ati's website (which caused the problems with the mes library), I didn't have this problem.

Allan

---

### Post by teumima on 2005-04-07
[QUOTE=allans]Well whenever I try ctrl + alt + backspace, my monitor tells me that there is no video input and I'm forced to restart the computer, I can't even get to a terminal by ctrl + alt + f1.  I'm putting this down to the drivers because when I used the latest drivers from ati's website (which caused the problems with the mes library), I didn't have this problem.

Allan[/QUOTE]
 that is weird.Did you apt-get your drivers?

I downloaded the xorg driver from ati. It's an rpm, used alien to make deb. and that was it?
Did you read my howto?

---

### Post by Dennis Snuggs on 2005-04-09
Right.  I done the instuctions that teumima wrote, and this came up on the screen.

root@denniss:/ # dpkg -i -force fglrx64-6-8-0_8.10.19-2_amd64.deb
dpkg: conflicting actions --field and --install

Type dpkg --help for help about installing and deinstalling packages [*];
Use dselect for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@denniss:/ #

Any ideas what the conflicting actions are?
I have not seen or written the --field or --install, so I take it that is a part of the install procedures of dpkg?  :-? 

It could have occured due to trying to install the i386 version. I have an AMD 64. So do I have to uninstall the i386 version first. Which did not install any way, in the first place. And how do I do that?

Thanks for any help. ](*,)

---

### Post by bobmitch on 2005-04-09
> **Dennis Snuggs]Right.  I done the instuctions that teumima wrote, and this came up on the screen.

root@denniss:/ # dpkg -i -force fglrx64-6-8-0_8.10.19-2_amd64.deb
dpkg: conflicting actions --field and --install

Type dpkg --help for help about installing and deinstalling packages [*] said:**
> .

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@denniss:/ #

Any ideas what the conflicting actions are?
I have not seen or written the --field or --install, so I take it that is a part of the install procedures of dpkg?  :-? 

It could have occured due to trying to install the i386 version. I have an AMD 64. So do I have to uninstall the i386 version first. Which did not install any way, in the first place. And how do I do that?

Thanks for any help. ](*,)

Should be:

root@denniss:/ # dpkg -i --force-overwrite fglrx64-6-8-0_8.10.19-2_amd64.deb

---

### Post by Dennis Snuggs on 2005-04-09
Silly me.   :roll: 

I did put the -overwrite in first time I tried it, but not the --force. As you can see, only one -.    :o 

Then I took out the -overwrite to try, but did not work either.

As Bob pointed out, I only put one - in front of force.

Thank you bobmitch. It has gone in this time, using:-
 dpkg -i --force-overwrite fglrx64-6-8-0_8.10.19-2_amd64.deb.

 I'm just about to reboot now.

I'll let you know if it works.

Thanks Bob.

---

### Post by Dennis Snuggs on 2005-04-09
I have done the bits and pieces.

Ran the make.sh as shown below. Then the bit below that came up.

Does this mean that I do not have the 'gcc' installed?



root@denniss:/lib/modules/fglrx/build_mod # sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
root@denniss:/lib/modules/fglrx/build_mod #

---

### Post by bobmitch on 2005-04-10
[QUOTE=Dennis Snuggs]I have done the bits and pieces.

Ran the make.sh as shown below. Then the bit below that came up.

Does this mean that I do not have the 'gcc' installed?



root@denniss:/lib/modules/fglrx/build_mod # sudo sh make.sh
make.sh: line 46: gcc: command not found
make.sh: line 52: [: !=: unary operator expected
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
root@denniss:/lib/modules/fglrx/build_mod #[/QUOTE]

Yup.  Just do a search for 'gcc' in synaptic and install the relevant package.  I`m on my xp box at the moment, so I can`t check exactly what it should be.  If you don`t get it going, let us know.

---

### Post by teumima on 2005-04-10
You need to get the headers probably too:

sudo apt-cache search linux-headers


and find the appropraite one for your kernel.

uname -r

will tell you what kernel u have.

---

### Post by heuler on 2005-04-13
plz help-me.

im brazilian and speak a poor english.

when i execute install of the ATI driver (.deb) i receive this mesage. Anywere can help-me.

===================================================

heuler@joselito:~/downloads$  sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb
(Reading database ... 60034 files and directories currently installed.)
Preparing to replace fglrx-6-8-0 8.10.19-2 (using fglrx-6-8-0_8.10.19-2_i386.deb) ...
Unpacking replacement fglrx-6-8-0 ...
Setting up fglrx-6-8-0 (8.10.19-2) ...
ldconfig: Cannot lstat /usr/lib/libncursesw.so.5: Permission denied
ldconfig: Can't link /usr/lib/libncursesw.so.5 to libncursesw.so.5.4

heuler@joselito:~/downloads$

===================================================

tks.

---

### Post by teumima on 2005-04-14
[QUOTE=heuler]plz help-me.

im brazilian and speak a poor english.

when i execute install of the ATI driver (.deb) i receive this mesage. Anywere can help-me.

===================================================

heuler@joselito:~/downloads$  sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb
(Reading database ... 60034 files and directories currently installed.)
Preparing to replace fglrx-6-8-0 8.10.19-2 (using fglrx-6-8-0_8.10.19-2_i386.deb) ...
Unpacking replacement fglrx-6-8-0 ...
Setting up fglrx-6-8-0 (8.10.19-2) ...
ldconfig: Cannot lstat /usr/lib/libncursesw.so.5: Permission denied
ldconfig: Can't link /usr/lib/libncursesw.so.5 to libncursesw.so.5.4

heuler@joselito:~/downloads$

===================================================

tks.[/QUOTE]
 Hey man

Are you doing this on Hoary?

---

### Post by copilot on 2005-04-14
I think you should add "This guide is by no means complete or even correct." to your guide, I followed it step by step and ended up with 640x480 after six or seven times trying to get X to load at all. Don't use this guide people, wait for a more defined/easier one.

---

### Post by teumima on 2005-04-14
[QUOTE=copilot]I think you should add "This guide is by no means complete or even correct." to your guide, I followed it step by step and ended up with 640x480 after six or seven times trying to get X to load at all. Don't use this guide people, wait for a more defined/easier one.[/QUOTE]
 That is obviously a personal issue. 

Most users don't have that problem. If you want a guide on individual tweaking, then write one.

If you want different resolutions go to you xorg.conf tot he section that looks like this:

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
    Monitor        "AOC FT7x0"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

If you run the fglrxconfig properly and choose the resolutions the way you should, then it should work, in the case you didn't do that, or it really didn't work (which happens). Then add the resolutions you want in the above section. Note they must be added in all modes. The farthest left one is the default.

Or just run fglrxconfig again, and focus carefully on the resolutions sections. If this doesn't work, then it's an individual issue and I recommend going to irc.freenode.org #ati which is more productive then blaming my guide.

---

### Post by copilot on 2005-04-14
How would one go about removing all the changes made to the system using this guide? I reverted back to the original xorg.conf, but if I try to follow other guides I end up with errors when I try to install a newer driver than the one we converted earlier.

I don't want a personalized guide, I want one that works.

---

### Post by teumima on 2005-04-14
[QUOTE=copilot]How would one go about removing all the changes made to the system using this guide? I reverted back to the original xorg.conf, but if I try to follow other guides I end up with errors when I try to install a newer driver than the one we converted earlier.

I don't want a personalized guide, I want one that works.[/QUOTE]
 I hope you made a backup of you xorg.conf 

I made a note the users should do that. Many users don't and then it's very hard to sort it out.

You have to remove you fglrx like this: 
sudo apt-get remove fglrx-6-8-0

The assuming you did a xorg backup:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by copilot on 2005-04-14
Thanks!

---

### Post by heuler on 2005-04-14
[QUOTE=teumima]Hey man

Are you doing this on Hoary?[/QUOTE]


yes....

---

### Post by teumima on 2005-04-14
[QUOTE=heuler]yes....[/QUOTE]
 type:

sudo nautilus and go to the folder /usr/lib/libncursesw.so.5

and make sure than you have the right permissions

---

### Post by Dennis Snuggs on 2005-04-21
Hi Bobmitch.

I installed the gcc and the source files. This worked ok, but still have no direct rendering.

This is now my xorg.conf  Any ideas?

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module
    Load	"bitmap"
    Load        "dbe"  	# Double buffer extension
    Load        "ddc"

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
    Load        "extmod"

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
    Load        "init10"
    Load        "record"
    Load        "vbe"
EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"gb"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30-65
    VertRefresh 50-75
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "backingstore" "true"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e44
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# _+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+
# Missing Section
# _+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+_+

# Added by me DBS
Section "Extensions"
    Option "Composite" "Disable"
EndSection


# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

---

### Post by bobmitch on 2005-04-22
It looks ok to me.

Try looking in /var/log/Xorg.0.log for any obvious errors?

---

### Post by Dennis Snuggs on 2005-04-22
Well, what can I say.
There are a couple of warnings about fglxr, but it seems to be loading!
Here are the warnings, and some fglxr bits. Some bits are taken out, due to length:

(**) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/75dpi/:unscaled,/usr/X11R6/lib/X11/fonts/100dpi/:unscaled,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(**) Extension "Composite" is disabled
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3188 card 1043,80a3 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01

(II) PCI: 01:00:1: chip 1002,4e64 card 1002,0005 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfd100000 - 0xfd6fffff (0x600000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcff00000 - 0xefefffff (0x20000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:0), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro] rev 0, Mem @ 0xe0000000/27, 0xfd600000/16, I/O @ 0xa000/8, BIOS @ 0xfd500000/17
(--) PCI: (1:0:1) ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary) rev 0, Mem @ 0xd8000000/27, 0xfd400000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdf00000 - 0xfdf000ff (0x100) MX[B]
	[1] -1	0	0xfdb00000 - 0xfdb03fff (0x4000) MX[B]
	[2] -1	0	0xfd700000 - 0xfd7007ff (0x800) MX[B]
	[3] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O


	[27] -1	0	0x0000e800 - 0x0000e807 (0x8 ) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "extmod"
(II) Reloading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "init10"
(WW) Warning, couldn't open module init10
(II) UnloadModule: "init10"
(EE) Failed to load module "init10" (module does not exist, 0)
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	FireGL - (RV250 4964), FireGL - (RV250 4965),
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY FireGL - (M9 4C65),
	MOBILITY RADEON 9000 (M9 4C66), RADEON 9000 PRO (D9 4C67),
	RADEON 9250 (RV280 5960), RADEON 9200 (RV280 5961),
	RADEON 9200 SE (RV280 5964), MOBILITY RADEON 9200 (M9+ 5C61),
	MOBILITY RADEON 9200 (M9+ 5C63), FireGL 8800 (R200 5148 ),
	RADEON 8500 (R200 514C), RADEON 9100 (R200 514D),
	RADEON - (R200 5154), RADEON - (R200 5155),
	RADEON 8500 AIW (R200 4242), RADEON 9600 (RV350 4150),
	RADEON 9600 SE (RV350 4151), RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50), RADEON 9500 (R300 4144),
	RADEON - (R300 4145), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148 ),
	FireGL - (R350 414B), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), FireGL - (RV350 4155), FireGL - (RV350 4156),
	FireGL - (RV350 4157), RADEON 9800 PRO (R350 4E48 ),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON - (RV370 5B61), RADEON X600 (RV380 5B62),
	RADEON - (RV370 5B63), FireGL V3100 (RV370 5B64),
	FireGL - (RV370 5B66), FireGL - (RV370 5B67),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON - (M22 5461),
	MOBILITY RADEON - (M22 5462), MOBILITY RADEON - (M22 5463),
	MOBILITY FireGL V3100 (M22 5464), MOBILITY FireGL - (M22 5465),
	MOBILITY FireGL - (M22 5466), MOBILITY FireGL - (M22 5467),
	RADEON X600 (RV380 3E50), RADEON - (RV380 3E51),
	RADEON - (RV380 3E52), RADEON - (RV380 3E53),
	FireGL V3200* (RV380 3E54), FireGL -* (RV380 3E55),
	FireGL -* (RV380 3E56), FireGL -* (RV380 3E57),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON - (M24 3151),
	MOBILITY RADEON X300 (M22 3152), MOBILITY RADEON - (M24 3153),
	MOBILITY FireGL V3200 (M24 3154), MOBILITY FireGL - (M24 3155),
	MOBILITY FireGL - (M24 3156), MOBILITY FireGL - (M24 3157),
	RADEON X800 (R420 4A48 ), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548 ),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	FireGL -* (R423 5552), MOBILITY RADEON X800 XT (M28 5D48 ),
	MOBILITY FireGL V5100* (M28 5D49), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700 (RV410 5E4F),
	RADEON - (RV410 5E52), RADEON - (RV410 5E53), RADEON - (RV410 5E55),
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835)
[COLOR=Red](II) Primary Device is: PCI 01:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found[/COLOR]
(--) Chipset RADEON 9700 PRO (R300 4E44) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]

	[29] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x71ac30
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "0x00000000"
(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "IgnoreEDID" "off"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(**) fglrx(0): Option "Stereo" "off"
(**) fglrx(0): Option "StereoSyncEnable" "1"
(**) fglrx(0): Option "UseFastTLS" "0"
(**) fglrx(0): Option "BlockSignalsOnLock" "on"
(**) fglrx(0): Option "ForceGenericCPU" "no"
(**) fglrx(0): Option "CenterMode" "off"
(**) fglrx(0): Option "FSAAScale" "1"
(**) fglrx(0): Option "FSAAEnable" "no"
(**) fglrx(0): Option "FSAADisableGamma" "no"
(**) fglrx(0): Option "FSAACustomizeMSPos" "no"
(**) fglrx(0): Option "FSAAMSPosX0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY0" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY1" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY2" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY3" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY4" "0.000000"
(**) fglrx(0): Option "FSAAMSPosX5" "0.000000"
(**) fglrx(0): Option "FSAAMSPosY5" "0.000000"
(**) fglrx(0): Option "NoTV" "yes"
(**) fglrx(0): Option "TVStandard" "NTSC-M"
(**) fglrx(0): Option "TVHSizeAdj" "0"
(**) fglrx(0): Option "TVVSizeAdj" "0"
(**) fglrx(0): Option "TVHPosAdj" "0"
(**) fglrx(0): Option "TVVPosAdj" "0"
(**) fglrx(0): Option "TVHStartAdj" "0"
(**) fglrx(0): Option "TVColorAdj" "0"
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(**) fglrx(0): Qbs disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): initializing int10
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON 9700 PRO (R300 4E44)" (Chipset = 0x4e44)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0004)
(--) fglrx(0): board vendor info: original ATI grafics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfd600000
(--) fglrx(0): ROM-BIOS at 0xfd500000
(--) fglrx(0): ChipExtRevID = 0x00
(--) fglrx(0): ChipIntRevID = 0x02
(--) fglrx(0): VideoRAM: 131072 kByte (64-bit SDR SDRAM)
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 0
(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 3 with Monitor Type 1
(II) fglrx(0): Primary head:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) fglrx(0): Secondary head:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) fglrx(0): EDID data from the display on Secondary head ---------------------------
(II) fglrx(0): Manufacturer: ACR  Model: 6b0  Serial#: 5606
(II) fglrx(0): Year: 2004  Week: 38
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space

(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.651 redY: 0.320   greenX: 0.300 greenY: 0.600
(II) fglrx(0): blueX: 0.153 blueY: 0.109   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: AL1715
(II) fglrx(0):  ACER
(II) fglrx(0): 
(II) fglrx(0): DesktopSetup 0x0000
(**) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): Overlay disabled
(**) fglrx(0): Overlay disabled
(II) fglrx(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total 4 valid mode(s) found.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) fglrx(0): *Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) fglrx(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) fglrx(0): *Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(--) fglrx(0): Display dimensions: (340, 270) mm
(--) fglrx(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): cpuFlags: 0x4000001f
(**) fglrx(0): cpuSpeedMHz: 0x000007d2
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfd600000 - 0xfd60ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)

	[35] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): UMM area:     0xe0701000 (size=0x078ff000)
(II) fglrx(0): driver needs XFree86 version: 4.3.x
[COLOR=Red](WW) fglrx(0): could not detect XFree86 version (query_status=-3)
[/COLOR](II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed

(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xffffff00001ef000
(II) fglrx(0): [drm] mapped SAREA 0xffffff00001ef000 to 0x2a9557e000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-amd64-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xfd600000
(II) fglrx(0): [agp] Mode=0x1f000a1a bridge: 0x1106/0x3188
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b1a
(II) fglrx(0): [agp] AGP protocoll is enabled for grafics board. (cmd=0x1f000312)
(II) fglrx(0): [agp] grafics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xffffff0008381000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00701000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(**) fglrx(0): Option "BackingStore" "true"
(**) fglrx(0): Backing store enabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 402
(**) Option "dpms"
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		30 128x128 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE

[COLOR=Red]Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0[/COLOR]

---

### Post by Crimson Tide on 2005-04-22
Hello All-

Tried these steps and my system locks on boot, I am guessing when it startx command is run.  I have base 5.04 installed original 2.6.10-5-386 kernel running.

I have laptop HP nc6230 with ATI X300 chip. 

I can copy back in my xorg.conf.backup file and get into my system. 

When I say my system locks, it begins to load X and halts.  Caps and Num locks do not appear to even work, I have to hard power off the system.

Please help.

Thanks!

Here is xorg.conf

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
#    HorizSync   31.5 - 48.4
#    VertRefresh 20 - 60
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000100" 
    Option "MonitorLayout"              "AUTO, NONE"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=5460
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

---

### Post by Dennis Snuggs on 2005-04-23
Hi Bobmitch.

Well, I don't know what's happened here, but, it wasn't working on rendering. BUT now it is.

Thank you very much for all your help. And anyone else who has helped.

I CAN GET RID OF WINDOWS NOW.  :razz: 

Yeeee Haaaa  to you BG.   \\:D/

---

### Post by bobmitch on 2005-04-23
[QUOTE=Dennis Snuggs]Hi Bobmitch.

Well, I don't know what's happened here, but, it wasn't working on rendering. BUT now it is.

Thank you very much for all your help. And anyone else who has helped.

I CAN GET RID OF WINDOWS NOW.  :razz: 

Yeeee Haaaa  to you BG.   \\:D/[/QUOTE]

Congrats!

---

### Post by Dennis Snuggs on 2005-04-24
Thanks Bob.

There is one problem that has occured.* (Sorry to be a pain).*

I installed Americas Army, the Linux version, and when I ran it, it came up with:

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

And then came out of it. So it didn't run.

Any ideas what or where it is going wrong?

I thought the display was "PCI:1:0:0" or whatever. I.e. 3 digit entries.

---

### Post by gege71.hu on 2005-04-25
[QUOTE=bobmitch]When using the fglrx driver, you must configure your resolution in the xorg.conf file - resolution changes cannot be made on-the-fly.

Look for the Subsection "Display" in the "Screen" section - specifically the "Modes" line.  The order of these modes is the order X will try them until it gets one that works - make sure you have your desired mode first.[/QUOTE]

Is there any way to have the availability of "on-the-fly" resolution-change after installin fglrx for radeon? It is a bit "lame" situation that You have to "dig in" xorg.conf to make resolution change...bahhh.. :(

---

### Post by Dennis Snuggs on 2005-04-25
You can change "on-the-fly" by using Ctrl Alt + or -.

Mine works like that. But you must have more than one resolution choosen.

I have three I can select.

This is set when you run fglrxconfig.

---

### Post by abstractism on 2005-04-25
okay, so I still haven't been able to get fglrx running. I'm tired of running around this problem, can anyone help me? I can post my xorg.conf and xorg log files..well maybe not the whole xorg log yet but here's the xorg.conf one. 
this is what I'm getting when I do fglrxinfo:
abstractism@chiana:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
thanks in advance for any help

---

### Post by gege71.hu on 2005-04-26
[QUOTE=Dennis Snuggs]You can change "on-the-fly" by using Ctrl Alt + or -.

Mine works like that. But you must have more than one resolution choosen.

I have three I can select.

This is set when you run fglrxconfig.[/QUOTE]

Thanx mate!
I'll give it a try tonight at home \\:D/

---

### Post by abstractism on 2005-04-27
wow, nobody's posted here yet

here's more of my problem. my xorg log says that my fglrx driver doesn't match with my kernel version, so openGL will not work. I can post more when I'm at my computer, but thats all I got.
someone please help.
abstractism

---

### Post by Dennis Snuggs on 2005-04-27
Right abstractism.

It looks like you haven't installed the fglrx config.

Here are the top lines of my xorg.conf

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#

Note line two in mine, then look at line three in yours.

Yours says:
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.


"#This file was generated by dexconf"

It should be

"# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config."

So it looks like you haven't installed it yet.

If you go to the beginning of this HOWTO, and follow what 'teumima' and 'bobmitch' has been saying. It should work.

The only other problem may be is that if you ARE installing the 9800. I'm not sure if the driver works for that yet.

I have only just got my 9700Pro going after 8 months!!!!

Anyway. Give the fglrx install a go, again.

What version is your Linux kernal?
Which processor are you using? (This can make a lot of difference also.)

ALSO

Quote bobmitch:
----------------------------------------------------------------------------------------------------------------------------------
Yup. Just do a search for 'gcc' in synaptic and install the relevant package..... 
----------------------------------------------------------------------------------------------------------------------------------
From 04-10-2005 01:33 AM

{As the gcc may not be installed.  If it is, ignore this bit.}


Quote teumima
----------------------------------------------------------------------------------------------------------------------------------
You need to get the headers probably too:
sudo apt-cache search linux-headers and find the appropraite one for your kernel.

uname -r

will tell you what kernel u have.
----------------------------------------------------------------------------------------------------------------------------------

{Make sure you got the right kernal.}

See if it works after that.

---

### Post by Dennis Snuggs on 2005-04-27
[QUOTE=gege71.hu]Thanx mate!
I'll give it a try tonight at home \\:D/[/QUOTE]

You're welcome.  I hope it works for you.  :)

---

### Post by Dennis Snuggs on 2005-04-27
[QUOTE=Dennis Snuggs]Thanks Bob.

There is one problem that has occured.* (Sorry to be a pain).*

I installed Americas Army, the Linux version, and when I ran it, it came up with:

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

And then came out of it. So it didn't run.

Any ideas what or where it is going wrong?

I thought the display was "PCI:1:0:0" or whatever. I.e. 3 digit entries.[/QUOTE]

It's ok peeps.  I have found out why this doesn't work. It's to do with the sound card!

All I gotta do is try and make it load.  Hmmmmm!

  ](*,)   again!

---

### Post by bobmitch on 2005-04-28
> 
Xlib: extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".


Dennis, for what it's worth (not much, as you`ve solved most of your issues... ;)  ), the digits there are not referring to the pci slot/address, but rather to the X method of addressing displays.  (ie.  hostname:xserver.displaynumber )

---

### Post by magaltavor on 2005-05-06
i got an ATI RadeOn 9200 on An hp NX 7000 my ubiintu is detecting it as 9000 how can i fix that is this important ?

---

### Post by brutus on 2005-06-08
hi
I tried to install drivers using alien. I installed headers, and after commands I had  no errors. In xorg.conf I didn't have to change to driver:fglrx, it was there already. But after type "fglrxinfo I see mesa working. 
Can anyone help me?
I have Radeon 9550.

This is my xorg.conf

```


# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "pl"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"pl"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 80.5
    VertRefresh 60 - 85
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
#    BusID "PCI:1:0:0"    # no device found at config time
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###



```

---

### Post by FizDev on 2005-06-14
I suppose this method won't work with the ATI Radeon Mobility X600? As it seems that fglrx works only with 
         - ATI Radeon 8500 / 9100
         - ATI FireGL 8700 / 8800 / E1
         - ATI FireGL T2
         - ATI Radeon 9000
         - ATI Radeon 9200
         - ATI Radeon 9500
         - ATI Radeon 9600
         - ATI Radeon 9700
         - ATI Radeon 9800
         - ATI FireGL Z1 / X1 / X2
         - ATI Mobility M9
         - ATI Mobility FireGL 9000
         - ATI Mobility M9PLUS
Or has anyone been able to use one of these for their Radeon Mobility X600 / X800?

---

### Post by edgarallan on 2005-07-13
hi i've barton 2500 on nforce2 mobo and radeon 2600 pro (agpgart and nvidia_agp loaded into kernel)

i've done all the possible... followed all the stiky messages. (2 days of frustration maybe i will return winzozz)

fglrxinfo say i'm in MESA
Xorg.0.log say loaded kernel module for "fglrx" driver
Kernel Module version matches driver.
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
DRI initialization successfull!
glrxinfo say direct rendering: No
client glx vendor string: ATI
OpenGL vendor string: Mesa

don't know what i can do
please helpme
tanks and bye,
francesco. this is my xorg.conf:

ection "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "dri"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "glx"
# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
Load "freetype"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
Load "GLcore"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Driver "fglrx"
Option "UseInternalAGPGART" "no"
BusID "PCI:2:0:0"
Option "backingstore" "true"
# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "yes"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.

EndSection

Section "Monitor"
Identifier "CM715"
Option "DPMS"
EndSection



Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Monitor "CM715"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by Kaso_Da_Zmok on 2005-09-04
I was playing around my company (AT&T) Dell Latitude D600 ](*,)  with Gentoo and Ubuntu. (had 1 week holiday cause of small injury). Finally i managed to get the fekin FGLRX to work on the onboard ATI 9000 mobile. Using this howto. I did install the Ubuntu 3 times on this laptop and 2 times Gentoo  (once from stage 1 that one was horrible due slow compiling speed, 3 days of pure compiling). Whatever... wanna say that no problem to setu up using great

---

### Post by userguy on 2005-09-05
I've successfully used it with a Radeon X300. It does work with the X series.

[QUOTE=FizDev]I suppose this method won't work with the ATI Radeon Mobility X600? As it seems that fglrx works only with 
         - ATI Radeon 8500 / 9100
         - ATI FireGL 8700 / 8800 / E1
         - ATI FireGL T2
         - ATI Radeon 9000
         - ATI Radeon 9200
         - ATI Radeon 9500
         - ATI Radeon 9600
         - ATI Radeon 9700
         - ATI Radeon 9800
         - ATI FireGL Z1 / X1 / X2
         - ATI Mobility M9
         - ATI Mobility FireGL 9000
         - ATI Mobility M9PLUS
Or has anyone been able to use one of these for their Radeon Mobility X600 / X800?[/QUOTE]

---

### Post by luckSpray on 2006-01-01
I don't know if this problem has been posted somewhere but there are definitely too much problems with Ati drivers... At least IMHO

I've read a dozen of those Ati driver installation guides but I still can't get it functional. I have a triple monitor setup 2 are connected to my Radeon 9800 pro AGP and 1 is connected to a Radeon 7000 PCI. But for first I must get fglrx to a working state.

As soon as I'm using the fglrx, X won't start. And I've read many Tutorials, Troubleshootings etc... on several sites. Well here's my xorg.conf

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	SubSection "extmod"
	        Option "omit xfree86-dga"
	EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	
    # If X refuses to use the screen resolution you asked for,
    # uncomment this; see "Bugs and Workarounds" for details.
	#Option "NoDDC"
	  
    # === Video Overlay for the Xv extension ===
	Option "VideoOverlay" "on"
	# === OpenGL Overlay ===
    # Note: When OpenGL Overlay is enabled, Video Overlay
    #       will be disabled automatically
	Option "OpenGLOverlay" "off"
    # === Use internal AGP GART support? ===
    # If OpenGL acceleration doesn't work, try using "yes" here
    # and disable the kernel agpgart driver.
	Option "UseInternalAGPGART" "no"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-110
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480" "640x400"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I hope I've got the crucial parts of the xorg log file:
```

...
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.0, module version = 8.16.20
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
...
(II) Primary Device is: PCI 03:02:0
(II) ATI Proprietary Linux Driver Version Identifier:8.16.20
(II) ATI Proprietary Linux Driver Release Identifier: @@UNRELEASED_AND_UNSUPPORTED_DRIVER@@
(II) ATI Proprietary Linux Driver Build Date: Aug 16 2005 00:15:14
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.16.1-driver-lnx-206829
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:3:2:0) found
(--) Chipset RADEON 9800 PRO (R350 4E48) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
...
	[39] -1	0	0x00008800 - 0x000088ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x82127b0
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
...
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(EE) fglrx(0): Cannot read V_BIOS
(EE) fglrx(0): PreInitInt10 failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) UnloadModule: "fglrx"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

I hope someone can tell me what to do... I'm very desperate because I'm trying to get this work the whole time. :cry:

---

### Post by cran on 2006-03-20
I'm having exactly the same problem (breezy, radeon 9800 pro):

```

(==) fglrx(0): Buffer Tiling is ON
(EE) fglrx(0): Cannot read V_BIOS
(EE) fglrx(0): PreInitInt10 failed
SetVBEMode failed
(EE) fglrx(0): R200PreInit failed
(II) fglrx(0): === [R200PreInit] === end
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(EE) Screen(s) found, but none have a usable configuration.

```

I also have a second card (pci) in my computer. If somebody knows a solution, or just a hint, please post!

---

### Post by codemode on 2006-05-10
I had the same problem.
i got 2 monitors working by switching monitors, i.e. connecting a different monitor to my ATI graphics card and selecting it as the primary graphics card in my BIOS. Since this is my AGP card I selected "AGP" in the BIOS settings.
Then I did a "Xorg -configure" on my system. It now works with the "ati" driver and also with the "fglrx" driver.

---

### Post by Gummi on 2007-02-18
Somehow I don't get the .deb file it only extracts it self into an folder. Can anyone tell me why?

---

### Post by mikegpc on 2007-03-29
I have a Mobility Radeon X1400 in my Dell Inspiron 6400. Although i have been fighting with the drivers for a while, and trying the "alien" command, i can't get the debian file because the "alien" command isn't being recognized. Can you help me out here??

---

### Post by Captain M on 2007-11-24
> **mikegpc said:**
> I have a Mobility Radeon X1400 in my Dell Inspiron 6400. Although i have been fighting with the drivers for a while, and trying the "alien" command, i can't get the debian file because the "alien" command isn't being recognized. Can you help me out here??

It's because you have to install it from synaptic package manager. Alien isn't included by default.

---

### Post by zarroc33 on 2009-08-07
Hello,

I was so relieved to find this but I ran into some trouble...

When I typed in ```
sudo alien fglrx_6_8_0-8.10.19-1.i386.rpm 
```
It said "file not found" I changed the file name and typed that in but still nothing. If anyone has any suggestions, please help. Thanks.

---

### Post by szirakitamas on 2009-08-08
hi,
do you want to convert this file into deb?
the correct form is

alien -i fglrx_6_8_0-8.10.19-1.i386.rpm

or

alien --to-deb fglrx_6_8_0-8.10.19-1.i386.rpm

man alien

:)

bests, 
t

---

### Post by zarroc33 on 2009-08-08
Hello again,

So the code you put was correct but is their a certain place I need to download the file to? Because right now it's on the desktop and it still says file fglrx_6_8_0-8.10.19-1.i386.rpm not found. Thanks

---

### Post by ssri on 2009-08-08
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

After checking out the latest git version of the radeon drivers, I was pleased with its improvement over the ones released with jaunty.  However, I experienced some tearing and fill problems with my ATI Mobility Radeon x2300.  So, I used the above link to downgrade my xserver, installed the necessary packages for the appropriate build environment, installed Catalyst 9.3 packages I built for jaunty (sh ./ati-blahblah-9.3.run --buildpkg Ubuntu/jaunty) and pinned all of the relevant packages in /etc/apt/preferences.  Running jaunty and kde 4.3.0 right now.  In Jaunty, Catalyst 9.3 experiences a touch more tearing when cycling through menus and windows than in intrepid, but nothing like what was seen with the radeon drivers.  However, I experienced no tearing when using googleearth or playing any videos.

---

### Post by linuxnewb1 on 2009-08-09
Hey, first time user of linux. im trying to install the radeon 9200 card and when I am in the terminal typing in commands i go to enter them and then it prompts me to enter a password, it says " [sudo] password for gareth: " at which point i cant type anything in. its like the keyboard cuts out.

---

### Post by sliv on 2009-08-09
> **linuxnewb1 said:**
> Hey, first time user of linux. im trying to install the radeon 9200 card and when I am in the terminal typing in commands i go to enter them and then it prompts me to enter a password, it says " [sudo] password for gareth: " at which point i cant type anything in. its like the keyboard cuts out.

Your keyboard works just fine, you just can't see the output of it on your screen as you're typing the password. If you type in your password and press enter the command you typed in above (the one with sudo in front of it) will be executed.

---

### Post by ziadnahas on 2009-08-13
I have tried exactly what was advised, after rebooting the system, i get what appears to be a graphics card crash. This also crashes the computer and am forced to restart. I dont understand what i'm doing wrong. Can anyone assist.

---

### Post by Mark Phelps on 2009-08-14
> **ziadnahas said:**
> I have tried exactly what was advised, after rebooting the system, i get what appears to be a graphics card crash. This also crashes the computer and am forced to restart. I dont understand what i'm doing wrong. Can anyone assist.

What you did wrong is force the installation of probably what is an incompatible driver.  The person who told you to do that should have first asked if you were running an Ubuntu newer than 8.10, because in 9.04 and newer, the Xserver running is incompatible with the  restricted drivers that you get from ATI.

If you're running 9.04, you will need to remove the restricted drivers and install the open source drivers in their place. See the link below and scroll down to the part about removing the fglrx driver:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Yellow Pasque on 2009-08-15
This ia a really old tutorial.

---

### Post by i_surf_the_turf on 2009-12-05
I have an ASUS AH3650 -> radeon hd3600 and although the UI works preety smoothly (not perfectly...) the fullscreen video really sucks. What should I do?

---

### Post by xdaedalus on 2010-01-28
> **Mark Phelps said:**
> What you did wrong is force the installation of probably what is an incompatible driver.  The person who told you to do that should have first asked if you were running an Ubuntu newer than 8.10, because in 9.04 and newer, the Xserver running is incompatible with the  restricted drivers that you get from ATI.

If you're running 9.04, you will need to remove the restricted drivers and install the open source drivers in their place. See the link below and scroll down to the part about removing the fglrx driver:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Hmm, I've been having the same problem as everyone else here-- radeon x300 that works for everyday stuff, but not for full 3-D acceleration. I found an old Linux driver on the ATI site. Does anyone know if it's possible to install this on Ubuntu 9.10? 

It just seems to me that there should be some kind of workaround. If I'm understanding everyone correctly, the radeon x300 used to work correctly, but now doesn't because ATI dropped support and Ubuntu no longer supports the legacy driver. But is it possible just to revert to using the relevant Ubuntu stuff from an earlier version (i.e. the version of Xserver that was used in 7.10 or whatever)?

I'm a complete newbie to this, but it would be nice to get my graphics working fully.

---

### Post by bwanaaa on 2010-02-20
I  upgraded to Ubuntu 9.1 and like it. But I want to use the ATI drivers for my video card, X1900 radeon. The recommene linux driver for this card is:
ati-driver-installer-9-3-x86.x86_64

So I downloaed it and read the install instructions and issued this command in terminal:
sudo sh ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/karmic
Well, this is what ubuntu did:

Created directory fglrx-install.JLlQi2
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/karmic
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Error: Distro Version entered incorrectly or not supported, use --listpkg to identify valid distro versions
Removing temporary directory: fglrx-install.JLlQi2


So, I googled and read and googled and read... and cannot seem to find a good solution. There's this page that says I have to downgrade my kernel
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
but do i really want to do this?

Can anyone one point me to the right thread?

Tnx.

---

### Post by Laysan_A on 2010-03-01
Hi bwanaaa,

I'm afraid I won't be of any direct help to you. Hopefully you've already found a solution elsewhere, on this, or a different forum.

I haven't had a working fglrx since intrepid (8.10). I was having so many other problems with jaunty that I just gave up on trying to get ati's driver to work. Since I upgraded to karmic yesterday, I gave it another shot, and no joy. I haven't had time yet to venture through the various ati threads (this is my first in months), but I'm sure you'll find one more recent than this one if you use the forum's search function.

Good luck!

Oh, check the driver section at ati's site for a wiki or something. It occurs to me that there used to be a helpful installation guide. The one I saw is likely not current, but they may have updated it.

---


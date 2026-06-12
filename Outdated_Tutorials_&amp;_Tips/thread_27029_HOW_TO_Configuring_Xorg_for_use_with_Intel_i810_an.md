---
title: "HOW TO: Configuring Xorg for use with Intel i810 and higher video cards"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by shakin on 2005-04-14
I've seen a lot of people having issues with integrated Intel video chipsets. I though I'd share my success story (well, mostly success. There is one minor problem addressed at the bottom of this how-to). I successfully ran Xorg on an integrated i915 chipset, but I believe this will work for any i810 or higher video chipset since I'm using the i810 driver.

In my case, the specific problem I was dealing with is that the Hoary installer gave me the vesa driver, which is servicable, but not great. After running dpkg-reconfigure xserver-xorg and manually selecting the i810 driver, my LCD monitor would fail to accept the requested video mode unless I commented out the horiz and vert refresh lines in my xorg monitor config, then it would force me to use 640x480. This is apparently because a faulty video bios that doesn't report valid video modes. Thus, I needed to use a program called 855resolution to force a better video mode. This how-to walks you through the process of installing and configuring 855resolution, then changing your xorg.conf file to start with the i810 driver.

Let's go...

- run 'wget http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb'
- run 'dpkg -i 855resolution_0.3-4_i386.deb'
- run 'sudo gedit /etc/default/855resolution'
- add config from modes list

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1400x1050, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1400x1050, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1400x1050, 32 bits/pixel

eg. (you need 3 lines in the file)

MODE=58
XRESO=1280
YRESO=1024

(look in /usr/share/doc/855resolution/README.Debian for more configuration information if you want)

- run 'sudo /etc/init.d/855resolution start' (should provide feedback that the patch is complete)
- run 'sudo gedit /etc/X11/xorg.conf'
- In gedit, change your video driver to i810 (Driver	"i810") in your device section. It is probably set to vesa by default.
- Restart X by pressing ctrl-alt-backspace or rebooting your computer.
- If X won't start after doing this you can go into command prompt mode from the Grub menu (recovery mode) and edit /etc/X11/xorg.conf to change your driver back to what it was (probably vesa)

- Note: on my system there is a problem where X initially starts in an invalid mode and my LCD won't display it. I switch to another terminal (ctrl-alt-F1) and then switch back to X (alt-F7) and then it works. I believe this is a refresh rate problem. I will update this how-to with a solution when I find it.

---

### Post by wxm505 on 2005-04-20
Hi mate. I did everything as u recommanded.
But it still does not work well.
I post some threads about this issue a couple weeks ago.
Would u like to have a look to find where the problem is of my 
box.Thank u very much indeed :)

[http://ubuntuforums.org/showthread.php?t=24328&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=24328&page=1&pp=10)
[http://ubuntuforums.org/showthread.php?t=24798&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=24798&page=1&pp=10)

---

### Post by jr_G-man on 2005-05-02
FYI,

A BIOS update resolved this problem for me.

I have a Dell Optiplex GX260.  It HAD the A06 BIOS.  I upgraded it to A09...and I get normal resolutions.

If this is an option, I highly recommend giving it a shot.

---

### Post by Gandalf on 2005-05-02
well i installed this and i still have the same problem which is low FPS
glxgears reports
```

1588 frames in 5.0 seconds = 317.600 FPS
1684 frames in 5.0 seconds = 336.800 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1688 frames in 5.0 seconds = 337.600 FPS
1685 frames in 5.0 seconds = 337.000 FPS
1683 frames in 5.0 seconds = 336.600 FPS

```
can we get more FPS???

---

### Post by Sav on 2005-05-08
[QUOTE=Gandalf]well i installed this and i still have the same problem which is low FPS
glxgears reports
```

1588 frames in 5.0 seconds = 317.600 FPS
1684 frames in 5.0 seconds = 336.800 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1688 frames in 5.0 seconds = 337.600 FPS
1685 frames in 5.0 seconds = 337.000 FPS
1683 frames in 5.0 seconds = 336.600 FPS

```
can we get more FPS???[/QUOTE]

Did you enable the DRI acceleration?

---

### Post by Gandalf on 2005-05-08
[QUOTE=Sav]Did you enable the DRI acceleration?[/QUOTE]
 how to do it???

---

### Post by wxm505 on 2005-05-08
[QUOTE=Gandalf]well i installed this and i still have the same problem which is low FPS
glxgears reports
```

1588 frames in 5.0 seconds = 317.600 FPS
1684 frames in 5.0 seconds = 336.800 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1688 frames in 5.0 seconds = 337.600 FPS
1685 frames in 5.0 seconds = 337.000 FPS
1683 frames in 5.0 seconds = 336.600 FPS

```
can we get more FPS???[/QUOTE]
THe same thing happened to me.

---

### Post by domo on 2005-05-14
[QUOTE=Gandalf]well i installed this and i still have the same problem which is low FPS
glxgears reports
```

1588 frames in 5.0 seconds = 317.600 FPS
1684 frames in 5.0 seconds = 336.800 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1690 frames in 5.0 seconds = 338.000 FPS
1688 frames in 5.0 seconds = 337.600 FPS
1685 frames in 5.0 seconds = 337.000 FPS
1683 frames in 5.0 seconds = 336.600 FPS

```
can we get more FPS???[/QUOTE]

If that can help:
Be sure that the module are load:
```
domo@xmas:~/data/nwn $ lsmod | grep drm
drm                    59540  2 i915
agpgart                32040  3 drm,intel_agp
``` 

And check if you have this lines on your /etc/X11/xorg.conf:
On the Section "Module"
```
        Load  "glx"
        Load  "dri"
``` 
Plus:
```
Section "DRI"
        Mode 0666
EndSection
```

---

### Post by dmatubu on 2005-05-20
I have an Intel 855GM in my laptop. I just CAN'T get it to go over 800x600 after trying many things, including 855resolution, even though the chipset supports 1024x768. In fact, the default Ubuntu xorg.conf did not even work - had to run xorgconfig to even get it to work at 800x600. I downloaded the driver from Intel, but I can't even run that, as it asks for the "latest kernel", which I already have. In the System->Preference->Screen Resolution panel it never displays anything greater than 800x600 at 70Hz. 

I would REALLY like to get away from Windoze and start using Ubuntu full-time, especially since learning that Microsoft was (is) one of the Korporations that wanted to profit from the "war" (correct word: invasion) in the middle east. I would greatly appreciate any knowledge on getting this funky video chip's chip off its block. I wouldn't even mind 800x600 except for the fact that some programs I will need to run have default screens larger than this res.

---

### Post by brokenladder on 2005-05-22
[FONT=Arial]
I went through a night or two of hell with this issue until finally I got it working..and I'm not entirely sure how.  I started off doing what was advised in the first message, adding the modes, whatever that did.  It didn't seem to immediately fix anything, but as far as I know it might have been part of what fixed the problem later.

I also did xorgconfig, or whatever it's called, and even tried manually editing /etc/X11/xorg.conf.  Nothing.  I was stuck in a low terrible resolution.

I later was advised to do: sudo dpkg-reconfigure xserver-org, which I did several times to no avail.

At some point, after doing various combinations of these procedures many many times, I went into xorg.conf, and found that my horizontal and vertical rates were not defined.  I defined them, and instantly it all worked.  Here is my xorg.conf if this helps anyone:

> 
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
	Load	"GLcore"
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
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dvorak"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Acer AL1715"
	Option		"DPMS"
        HorizSync    31.5-80
        VertRefresh  36.5-75	
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Device"
	Monitor		"Acer AL1715"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

[/FONT]

---

### Post by dmatubu on 2005-05-23
](*,) 

I just tried dkpg-reconfigure xserver-org, and dpkg told me that package "xserver-org" is not installed. 

I also checked the horiz and vert rates in the monitor section, and yep they're there. 

I have the video chipset from hell. 

Does anyone have any other advice I could try? At this point I'll try anything short of trying to fly this laptop like a kite. 

Here is my xorg.conf as written by xorgconfig, and which gives me a working X at 800x600:

# File generated by xorgconfig.

#
# Copyright 2004 The X.Org Foundation
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
# The X.Org Foundation BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of The X.Org Foundation shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from
# The X.Org Foundation.
#

# **********************************************************************
# Refer to the xorg.conf(5x) man page for details about the format of 
# this file.
# **********************************************************************

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

# This loads the font modules
    Load        "type1"
#    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
#    Load       "glx"
# This loads the DRI module
#    Load       "dri"

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
# 

    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TTF/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/CID/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/TrueType/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/freefont/"

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

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

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

#    Option     "Protocol"      "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option	"Xleds"      "1 2 3"

#    Option "LeftAlt"     "Meta"
#    Option "RightAlt"    "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"    "pc105"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"    "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"   "de"
# or:
#    Option "XkbLayout"   "de"
#    Option "XkbVariant"  "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions"  "ctrl:swapcaps"

# These are the default XKB settings for Xorg
#    Option "XkbRules"    "xorg"
#    Option "XkbModel"    "pc105"
#    Option "XkbLayout"   "us"
#    Option "XkbVariant"  ""
#    Option "XkbOptions"  ""

#    Option "XkbDisable"

    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"us"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/input/mouse0"

# Mouse-speed setting for PS/2 mouse.

#    Option "Resolution"	"256"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"	"Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"	"9600"
#    Option "SampleRate"	"150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the xorg.conf man page for a description of the options.
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
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"        "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "1412"
#    Option     "MaxX"          "15184"
#    Option     "MinY"          "15372"
#    Option     "MaxY"          "1230"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"        "/dev/ttyS0"
#    Option     "MinX"          "231"
#    Option     "MaxX"          "3868"
#    Option     "MinY"          "3858"
#    Option     "MaxY"          "272"
#    Option     "ScreenNumber"  "0"
#    Option     "ReportingMode" "Scaled"
#    Option     "ButtonThreshold"       "17"
#    Option     "ButtonNumber"  "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier  "My Monitor"

# HorizSync is in kHz unless units are specified.
# HorizSync may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    #HorizSync   31.5 - 48.5
HorizSync 31.5-80

#    HorizSync	30-64         # multisync
#    HorizSync	31.5, 35.2    # multiple fixed sync frequencies
#    HorizSync	15-25, 30-50  # multiple ranges of sync frequencies

# VertRefresh is in Hz unless units are specified.
# VertRefresh may be a comma separated list of discrete values, or a
# comma separated list of ranges of values.
# NOTE: THE VALUES HERE ARE EXAMPLES ONLY.  REFER TO YOUR MONITOR'S
# USER MANUAL FOR THE CORRECT NUMBERS.

    #VertRefresh 40-150
VertRefresh 36.5-75

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier	"Standard VGA"
    VendorName	"Unknown"
    BoardName	"Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset	"generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver     "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# intalled.

#    BusID      "PCI:0:10:0"

#    VideoRam	256

#    Clocks	25.2 28.3

EndSection

# Device configured by xorgconfig:

Section "Device"
    Identifier  "** Intel i810 (generic)               [i810]"
    Driver      "i810"
    VideoRam    8192
    # Insert Clocks lines here if appropriate
EndSection


# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen 1"
    Device      "** Intel i810 (generic)               [i810]"
    Monitor     "My Monitor"
    DefaultDepth 16

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
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
    Identifier  "Simple Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.  In this example, screen 2 is located to the
# right of screen 1.

    Screen "Screen 1"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

# Section "DRI"
#    Mode 0666
# EndSection

---

### Post by geearf on 2005-05-24
isn't it dpkg-reconfigure xserver-xorg ?and not xserver-org ?

---

### Post by TheChad on 2005-06-01
[QUOTE=brokenladder][FONT=Arial]
Section "Monitor"
Identifier "Acer AL1715"
Option "DPMS"
HorizSync 31.5-80
VertRefresh 36.5-75
EndSection

[/FONT][/QUOTE]
This worked like a charm, except of course I have a different monitor.  Thanks dude.  Everything except the refresh rate is spot on, but it still works fine.  My xorg.conf looks like this:

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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL E171FP"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL E171FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
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
 :grin: (that's not part of xorg.conf, but i was just too happy)

---

### Post by X3N on 2005-06-12
I noticed some people were having problems with the fps. I've just fixed this on my laptop (Samsung X05) which has an Intel Corp. 82852/855GM. The main problem was that it was using software rendering for everything. 

I noticed when looking in lsmod that the video modules were vesafb related. after modprobe -r (remove) the vesa modules and then modprobe'ing the agpgart,drm,intel_agp and intelfb . After restarting X i found that glxinfo reported "direct rendering: Yes" and my glxgears now runs at

michael@Pegasus:~$ glxgears
2999 frames in 5.0 seconds = 599.800 FPS
3000 frames in 5.0 seconds = 600.000 FPS
3001 frames in 5.0 seconds = 600.200 FPS
3002 frames in 5.0 seconds = 600.400 FPS
3001 frames in 5.0 seconds = 600.200 FPS

[ not amazing but good enough ] 

michael@Pegasus:~$ glxgears
11291 frames in 5.0 seconds = 2258.200 FPS
10538 frames in 5.0 seconds = 2107.600 FPS
10354 frames in 5.0 seconds = 2070.800 FPS
11212 frames in 5.0 seconds = 2242.400 FPS
12044 frames in 5.0 seconds = 2408.800 FPS
10618 frames in 5.0 seconds = 2123.600 FPS
11115 frames in 5.0 seconds = 2223.000 FPS

^^ when glxgears is not in the foreground [ don't understand why it decides to use more cpu when it is not in the foreground.  when it is ontop it uses less cpu than when it is behind another window. ] 

here are the relivant modules you need

root@Pegasus:~ # lsmod
Module                  Size  Used by
i915                   18304  1
intel_agp              20636  1
intelfb                28676  0
cfbcopyarea             3968  1 intelfb
cfbimgblt               3072  1 intelfb
cfbfillrect             3584  1 intelfb
drm                    59412  2 i915
agpgart                31784  4 intel_agp,intelfb,drm

Here is my device section from /etc/X11/xorg.conf

Section "Device"
        Identifier      "Intel"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "NoAccel"               "0"
        Option          "DRI"                   "1"
        VideoRam 64000
EndSection

---

### Post by kubuntuuser on 2005-06-28
I originally installed mandrake on my insprion 1100 without any modification to the bios and had to use something called something called i845patch (cant remember the name exactly) which assigned more memory to the video controller, otherwise i was stuck with an unusable desktop that was about 5 inches in diameter in the center of the screen. 

When I swapped to kubuntu, I thought I may have the same problem so updated the bios to A32, which fixes the amount of memory that the video controller is assigned but still gave me a resolution problem. 

This is however a very simple edit to the xorg.conf file. I added added the refresh rates and none of the steps highlighted above were tried, only an edit to the conf file. On  a reboot gave me my full resolution of 1024x768 and 24bit colour.


I dont know whether this allows 3D graphics however as I do not use my machine for gaming.

---

### Post by ccj@griskroppen on 2005-07-01
Another thing to be aware of is the amount of RAM reserved for the integrated
graphics card.

Gnome refused to let me set anything better than 640*480, even though 
dpkg-reconfigure xserver-xorg would happily suggest much higher resolutions.

The solution was to enter the BIOS and, under advanced chipset features,
up the amount of RAM to 8MB.  It was set to 1MB (doh!).  I blame the clowns
in our IT-department, ;)

I now live happily ever after with 1600*1200.

---

### Post by majikstreet on 2005-07-26
I can not get this solution to work.

I have a dell dimension 2350 with a dell E151FPb lcd monitor. 

When I boot my computer, toward the end of the boot, the screen flashes and then there is a blue screen that says X isn't configured properly. (Hmm.. I though people say there is no BSOD in Linux, but there is if you have a POS Dell!)

Anywho, I have a thread here about this problem: [http://ubuntuforums.org/showthread.php?t=51954](http://ubuntuforums.org/showthread.php?t=51954)

Thanks,
majikstreet

---

### Post by DeathOnJuice on 2005-08-09
[QUOTE=domo]If that can help:
Be sure that the module are load:
```
domo@xmas:~/data/nwn $ lsmod | grep drm
drm                    59540  2 i915
agpgart                32040  3 drm,intel_agp
``` 

And check if you have this lines on your /etc/X11/xorg.conf:
On the Section "Module"
```
        Load  "glx"
        Load  "dri"
``` 
Plus:
```
Section "DRI"
        Mode 0666
EndSection
```[/QUOTE]
My resolution and everything else that involves display is fine, except for one thing: my FPS.

I have all of those lines on my xorg.conf, but when I run lsmod | grep drm, it doesn't say anything. Here is what glxgears says: 

```
512 frames in 5.0 seconds = 102.400 FPS
565 frames in 5.0 seconds = 113.000 FPS
565 frames in 5.0 seconds = 113.000 FPS
452 frames in 5.0 seconds = 90.400 FPS
565 frames in 5.0 seconds = 113.000 FPS
```

My video card is an Intel 82815 CGC [Chipset Graphics Card]. Could someone help?

---

### Post by DeathOnJuice on 2005-08-10
Come on... anyone? Can't someone help?

---

### Post by DeathOnJuice on 2005-08-11
[QUOTE=DeathOnJuice]Come on... anyone? Can't someone help?[/QUOTE]
 Bump.

---

### Post by verrice on 2005-08-11
[QUOTE=DeathOnJuice]My resolution and everything else that involves display is fine, except for one thing: my FPS.

I have all of those lines on my xorg.conf, but when I run lsmod | grep drm, it doesn't say anything. Here is what glxgears says: 

```
512 frames in 5.0 seconds = 102.400 FPS
565 frames in 5.0 seconds = 113.000 FPS
565 frames in 5.0 seconds = 113.000 FPS
452 frames in 5.0 seconds = 90.400 FPS
565 frames in 5.0 seconds = 113.000 FPS
```

My video card is an Intel 82815 CGC [Chipset Graphics Card]. Could someone help?[/QUOTE]

I have the 82865G CGC and was getting similar results as you. After upgrading my BIOS (was 11 versions behind) as done by someone else earlier in this thread; I now get over 1000fps. If you haven't tried updating your bios yet, do so.

---

### Post by lgiraud on 2005-08-18
I try all the tricks given here with bad results... So I succed by my own  :razz: :
I got a Knoppix-debian version that works with my I810 ( :-x ) video card. So I edited the XF86Config file and just copy in the right section the "modelines" and other VideoRam, HorizSync and VertRefresh.
This is a little bit ugly but it works.

If its help, this is a part of my now working xorg.conf:


Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam   64000
EndSection

Section "Monitor"
	Identifier	"COMPAQ 7500"
	Option		"DPMS"
	Option "NoDCC"
	HorizSync 30 - 70 # DDC-probed
        VertRefresh 50 - 140 # DDC-probed
       ModeLine "1024x768"      94.50 1024 1072 1168 1376 768  769  772  808 +hsync +vsync
        # 1024x768, 75.0Hz; hfreq=60.02, vfreq=75.03
        ModeLine "1024x768"      78.75 1024 1040 1136 1312 768  769  772  800 +hsync +vsync
        # 800x600, 85.0Hz; hfreq=53.67, vfreq=85.06
        ModeLine "800x600"       56.25  800  832  896 1048 600  601  604  631 +hsync +vsync
        # 800x600, 75.0Hz; hfreq=46.88, vfreq=75.00
        ModeLine "800x600"       49.50  800  816  896 1056 600  601  604  625 +hsync +vsync
        # 800x600, 60.0Hz; hfreq=37.88, vfreq=60.32
        ModeLine "800x600"       40.00  800  840  968 1056  600  601  605  628 +hsync +vsync
        # 640x480, 85.0Hz; hfreq=43.27, vfreq=85.01
        ModeLine "640x480"       36.00  640  696  752  832  480  481  484  509 -hsync -vsync
        # 640x480, 75.0Hz; hfreq=37.50, vfreq=75.00
        ModeLine "640x480"       31.50  640  656  720  840  480  481  484  500 -hsync -vsync
        # 640x480, 60.0Hz; hfreq=31.47, vfreq=59.94
        ModeLine "640x480"       25.17  640  648  744  784  480  482  484  509 -hsync -vsync
        # Extended modelines with GTF timings
        
        ModeLine "640x480"  43.16  640 680 744 848  480 481 484 509  -HSync +Vsync
        
        ModeLine "768x576"  34.96  768 792 872 976  576 577 580 597  -HSync +Vsync
        
        ModeLine "768x576"  42.93  768 800 880 992  576 577 580 601  -HSync +Vsync
        
        ModeLine "768x576"  45.51  768 808 888 1008  576 577 580 602  -HSync +Vsync
        
        ModeLine "768x576"  51.84  768 808 888 1008  576 577 580 605  -HSync +Vsync
        
        ModeLine "768x576"  62.57  768 816 896 1024  576 577 580 611  -HSync +Vsync
        
        ModeLine "800x600"  68.18  800 848 936 1072  600 601 604 636  -HSync +Vsync
        
        ModeLine "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814 -HSync +Vsync
        
        ModeLine "1152x864"  81.62  1152 1216 1336 1520  864 865 868 895  -HSync +Vsync
        
        ModeLine "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 -HSync +Vsync
        
        ModeLine "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915 -HSync +Vsync
        
        ModeLine "1280x960"  124.54  1280 1368 1504 1728  960 961 964 1001 -HSync +Vsync
        
        ModeLine "1280x960"  129.86  1280 1368 1504 1728  960 961 964 1002 -HSync +Vsync
        
        ModeLine "1280x960"  178.99  1280 1376 1520 1760  960 961 964 1017 -HSync +Vsync
        
        ModeLine "1280x1024"  190.96  1280 1376 1520 1760  1024 1025 1028 1085 -HSync +Vsync
        
        ModeLine "1400x1050"  122.61  1400 1488 1640 1880  1050 1051 1054 1087 -HSync +Vsync
       
        ModeLine "1400x1050"  149.34  1400 1496 1648 1896  1050 1051 1054 1094 -HSync +Vsync
       
        ModeLine "1400x1050"  155.85  1400 1496 1648 1896  1050 1051 1054 1096 -HSync +Vsync
        
        ModeLine "1400x1050"  179.26  1400 1504 1656 1912  1050 1051 1054 1103 -HSync +Vsync
        
        ModeLine "1400x1050"  214.39  1400 1512 1664 1928  1050 1051 1054 1112 -HSync +Vsync
        
        ModeLine "1600x1200"  280.64  1600 1728 1904 2208  1200 1201 1204 1271 -HSync +Vsync
       
        Modeline "1920x1200" 193.16  1920 2048 2256 2592  1200 1201 1204 1242 -HSync +HSync
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"COMPAQ 7500"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

---

### Post by Triton on 2005-08-18
This didn't work for you?

[Link](http://www.ubuntuforums.org/showthread.php?t=48154&highlight=trito)

---

### Post by ekravche on 2005-09-03
[QUOTE=shakin]I've seen a lot of people having issues with integrated Intel video chipsets. I though I'd share my success story (well, mostly success. There is one minor problem addressed at the bottom of this how-to). I successfully ran Xorg on an integrated i915 chipset, but I believe this will work for any i810 or higher video chipset since I'm using the i810 driver.

In my case, the specific problem I was dealing with is that the Hoary installer gave me the vesa driver, which is servicable, but not great. After running dpkg-reconfigure xserver-xorg and manually selecting the i810 driver, my LCD monitor would fail to accept the requested video mode unless I commented out the horiz and vert refresh lines in my xorg monitor config, then it would force me to use 640x480. This is apparently because a faulty video bios that doesn't report valid video modes. Thus, I needed to use a program called 855resolution to force a better video mode. This how-to walks you through the process of installing and configuring 855resolution, then changing your xorg.conf file to start with the i810 driver.

Let's go...

- run 'wget http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb'
- run 'dpkg -i 855resolution_0.3-4_i386.deb'
- run 'sudo gedit /etc/default/855resolution'
- add config from modes list

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1400x1050, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1400x1050, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1400x1050, 32 bits/pixel

eg. (you need 3 lines in the file)

MODE=58
XRESO=1280
YRESO=1024

(look in /usr/share/doc/855resolution/README.Debian for more configuration information if you want)

- run 'sudo /etc/init.d/855resolution start' (should provide feedback that the patch is complete)
- run 'sudo gedit /etc/X11/xorg.conf'
- In gedit, change your video driver to i810 (Driver	"i810") in your device section. It is probably set to vesa by default.
- Restart X by pressing ctrl-alt-backspace or rebooting your computer.
- If X won't start after doing this you can go into command prompt mode from the Grub menu (recovery mode) and edit /etc/X11/xorg.conf to change your driver back to what it was (probably vesa)

- Note: on my system there is a problem where X initially starts in an invalid mode and my LCD won't display it. I switch to another terminal (ctrl-alt-F1) and then switch back to X (alt-F7) and then it works. I believe this is a refresh rate problem. I will update this how-to with a solution when I find it.[/QUOTE]

Got this to work. Also check out this thread regarding the fix to 640X480 problem:  [http://www.ubuntuforums.org/showthread.php?t=55614](http://www.ubuntuforums.org/showthread.php?t=55614)

---

### Post by majikstreet on 2005-09-03
HI,
I just wanted to post my xorg.conf as a reference, this is how I got mine to work...

[http://www.majikstreet.org/xorg.conf](http://www.majikstreet.org/xorg.conf)

---

### Post by TestDummy! on 2005-09-08
I helped somebody with an i810 chipset.

I tried to follow this but in the end, this soulution did it..

All I did was add in the Hoirzontal Sync, Vertical Refresh and the Video RAM into xorg.conf, like so

[i]Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        **VideoRam 65536** 
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
        [b]HorizSync 30-70
        VertRefresh 50-160[/b]
EndSection[/i] 

(Generic Disclaimer: Settings used for example, yours will vary depending on what monitor you have and what you have your BIOS set to allocate system RAM for video. Not responsible for blowing up your monitor or something :) ) 

 From what I gather on here, the i810 chipsets sometimes get a bad count of memory from the BIOS and get X to think there is only 1MB to use for video, or something.

---

### Post by Pancetilla on 2005-09-29
Hi everybody, new to the forums, been using Ubuntu since July or so and now have bought a laptop:

I had the already known problem with the i810 but I could not work it out with the monitor frequency workaround. So I inserted the new Ubuntu 5.10 live preview, copied **i810_drv.o** from /etc/X11R6/.... to Ubuntu 5.04 and now it  works alright, without changing anything in xorg.conf. The i810_drv.o file from 5.04 must be broken or something.

You can also get working i810_drv.o in the web, I think.

Bye and hope it helps.

---

### Post by yrjo on 2005-10-01
So is direct rendering now enabled? What does glxinfo tell about direct rendering?

---

### Post by tregetour on 2005-10-09
I managed to get it to give me 1280x1024.

But: It's drawing everything twice in weird places. The refresh rate according to the screen resolution dialouge is 75 -- acording to my moniter it's 60. Could this be the problem? And if so ... how do I fix it? Thank you!

When I change the driver in xorg.conf to 'vesa' everything works peachy and the moniter says 75.

[the moniter is a BenQ FP731 -- the computer is an HP pavillion a600y]

thank you in advance.

---

### Post by assan on 2005-10-15
I have very low fps on my acer notebook Intel 855GM
About 250 fps, after installation of DRI drivers.
There is no direct rendering how to switch it on?

glxinfo
name of display: :0.0
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method,
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control,
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_visual_select_group
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_imaging, GL_ARB_multitexture,
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_shadow,
    GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_window_pos,
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate,
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_clip_volume_hint, GL_EXT_copy_texture, GL_EXT_draw_range_elements,
    GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels,
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_rescale_normal,
    GL_EXT_secondary_color, GL_EXT_separate_specular_color,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle,
    GL_EXT_vertex_array, GL_APPLE_packed_pixels, GL_ATI_texture_env_combine3,
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,
    GL_HP_occlusion_test, GL_IBM_texture_mirrored_repeat,
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_point_sprite, GL_NV_texgen_reflection,
    GL_NV_texture_rectangle, GL_SGIS_generate_mipmap,
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp,
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SGIX_shadow,
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

---

### Post by assan on 2005-10-16
I have similar problem 855gm and installed DRI following   instruction (for intel i915) HOWTO: Enable DRI (3D support) on SAVAGE cards.
Fps is about 300, and lsgrep is showing:

lsmod | grep drm
drm                    74168  2 i915
agpgart                34792  3 drm,intel_agp

but: glxinfo is showing no 3D rendering
$ glxinfo |grep rendering
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No

Any idea how to fix it?

---

### Post by rakhil on 2006-03-18
hey i too am having this problem with Intel 82845G graphics controller and my xorg.conf file shows it is using i810 driver.My motherboard is of mercury and monitor is of LG 500E.Now the problem is that i can't get resolution more than 640x480.also my gdm is not starting using the command 
 /etc/init.d/gdm start
actually it says it failed to do so.
i tried various solutions of 855 resolutin but they didn't work out.........
and this might be due to the fact that i don't know my monitor's vert refresh and horz sync rate plus videoram.How can i know that??
Plz give any idea vat to do ???
will driver or biosupdate help solving the problem?
my bios version is american megatrends inc.  version 07.00T

---

### Post by jaywatkins on 2006-07-19
> **jr_G-man said:**
> FYI,

A BIOS update resolved this problem for me.

I have a Dell Optiplex GX260.  It HAD the A06 BIOS.  I upgraded it to A09...and I get normal resolutions.

If this is an option, I highly recommend giving it a shot.

The same fix worked for me after trying the 855resolution route...

/J

---

### Post by intel352 on 2007-04-19
just as an fyi, the tip on upping the onboard video ram to 8mb (from 1mb) solved the problem for me.

i810 chipset, PCBSD :-)

---

### Post by etola on 2007-04-27
Hi, 

I have feisty with kdm and I wasn't able to change  my graphics driver from **system settings**.  The 1st message in the thread solved my problem. Here is my** xorg.conf **for  interested souls

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
#	Device		"Generic Video Card"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

edit: By the way I have this on a Dell D410 laptop

---

### Post by Prachii on 2009-03-28
I've been having a similar problem with my laptop screen resolution. Somehow I managed to reset it to 1024 x 768 from 800 x 600 but since I have a 1440 x 900 Widescreen LCD screen, this resolution still looks very primitive. I am able to change the configuration using a GUI program and it allows me to change the screen model to Generic, LCD Panel 1024 x 768 (widescreen) and resolution to 1024 x 768 but I am unable to do the same for Generic, LCD Panel 1440 x 900 (widescreen) and resolution to 1440 x 900. Please help!

---


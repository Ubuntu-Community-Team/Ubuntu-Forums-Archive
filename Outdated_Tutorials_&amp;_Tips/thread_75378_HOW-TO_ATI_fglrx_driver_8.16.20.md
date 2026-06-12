---
title: "HOW-TO: ATI fglrx driver 8.16.20"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by mlomker on 2005-10-13
The fglrx driver supports Radeon 8500+ and the X-series cards.  *Note that the 9100 IGP cards and the Mobility 9000 M7 LW (laptop chipset) are not supported for 3D.*

When running the dpkg-reconfigure commands you can accept the defaults whenever you aren't sure.

_**Remove the 8.16.20 driver if it is already installed (not working)**_

```

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #*Select the ATI driver*

```

Reboot--*necessary to get the restricted modules out of memory*.


_**(Re)Installing the driver**_

**All Platforms:**
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #*Okay if it is already installed*
sudo dpkg-reconfigure xserver-xorg #*Select the fglrx driver*

```

**64-bit users:** 

You have to downgrade to an older version of libdri.a due to an incompatilbity with the ATI drivers.  [Download it here]("http://mail3.mpr.org/mlomker/libdri.a.gz").

Change to download directory:
```

gunzip libdri.a.gz
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
sudo cp libdri.a /usr/X11R6/lib/modules/extensions/

```

If you wish to revert to any non-fglrx driver you will need to copy the libdri.a.old file back over the fglrx version.

Reboot.


_**Confirm that it works**_
```

mlomker@mlomkernote:/$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

_**Troubleshooting**_
[B]
Resolution Problem:[/B]
The driver is installed but you are at 1024x768.  The installer may have defaulted to that setting--I know that it didn't prompt me during my install.  Either manually edit the xorg.conf file (if you know how) using **nano /etc/X11/xorg.conf** or run **sudo dpkg-reconfigure xserver-xorg**.

If you have updated the xorg.conf but your widescreen display is still stuck at 1024x768 then it is probably the bug in the 8.16.20 driver that was fixed in 8.18.6.  That driver is harder to install but [I have a how-to]("http://ubuntuforums.org/showthread.php?p=423589").  

**General Troubleshooting:**
You can look through the /var/log/Xorg.0.log and kern.log file for troubleshooting most problems.

[xf86_EINVAL and MTRR errors]("http://ubuntuforums.org/showthread.php?t=115104")


**64-bit users:**

You may get this error message when you go to restart:

```

Duplicate symbol rol_long in /usr/X11R6/lib/modules/drivers/fglrx_drv.o
Also defined in /usr/X11R6/lib/modules/linux/libint10.a

```

You can fix this by editing your xorg.conf file and commenting out the libint10.a line:

```

sudo nano /etc/X11/xorg.conf

```

```

Section "Module"
#       Load    "int10"
EndSection

```

Ctrl-W, Y, Enter to save.

---

### Post by Olav on 2005-10-13
[QUOTE=mlomker]The fglrx driver supports Radeon 8500+ and the X-series cards.

Installing the driver that comes with Breezy:

```

sudo apt-get install fglrx-control
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-2.6.12
sudo fglrxconfig

```
[/QUOTE]
Okay, using that at least I get functional TV output [EDIT to be clear: I mean watching TV from my TV-card in a program called TVTime]. This was my second biggest problem. The biggest-biggest problem was all the terrible random crashes and hangups I got with both "ati" and "radeon" standard drivers. That seems to be fixed now, too.

But 3D is terribly slow. I tried glxgears of course, it's beyond bad. Just to see how a game would perform I installed Planet Penguin (was: Tux Racer). Where normally our brave and sleek Linux mascot goes whoooosh down the hill, it looks now like you have to kick the fat lazy bird forward, just half a meter at a time ;)

I guess this is the only alternative. I had the same thing going on in Hoary, and I never lost sleep over it. I was just hoping it would get better. Have to keep on doing that, or so it seems.

I blame this situation entirely on ATI, by the way.

---

### Post by jecos on 2005-10-13
[QUOTE=Olav]Okay, using that at least I get functional TV output [EDIT to be clear: I mean watching TV from my TV-card in a program called TVTime]. This was my second biggest problem. The biggest-biggest problem was all the terrible random crashes and hangups I got with both "ati" and "radeon" standard drivers. That seems to be fixed now, too.

But 3D is terribly slow. I tried glxgears of course, it's beyond bad. Just to see how a game would perform I installed Planet Penguin (was: Tux Racer). Where normally our brave and sleek Linux mascot goes whoooosh down the hill, it looks now like you have to kick the fat lazy bird forward, just half a meter at a time ;)

I guess this is the only alternative. I had the same thing going on in Hoary, and I never lost sleep over it. I was just hoping it would get better. Have to keep on doing that, or so it seems.
I blame this situation entirely on ATI, by the way.[/QUOTE]  
It would help if you would actually state what card you are using and what your xorg.conf looks like.. 'ati' and 'radeon' drivers are open source, 'fglrx' is ati's proprietary driver for radeon 8500 and up..  Its a work in progress..

---

### Post by mlomker on 2005-10-13
> I guess this is the only alternative. I had the same thing going on in Hoary, and I never lost sleep over it.

What is the output of **glxgears -iacknowledgethatthistoolisnotabenchmark** and **fglrxinfo** for you?  If it says ATI and you're over 1k fps then you've got what you got.

---

### Post by Olav on 2005-10-13
[QUOTE=mlomker]What is the output of **glxgears -iacknowledgethatthistoolisnotabenchmark** and **fglrxinfo** for you?  If it says ATI and you're over 1k fps then you've got what you got.[/QUOTE]
Here it is:
```
olav@dinges:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
olav@dinges:~$
olav@dinges:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
How do I get output from that crazy glxgears command? It doesn't say a thing.

---

### Post by SilverTab on 2005-10-13
[QUOTE=Olav]Here it is:
```
olav@dinges:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
olav@dinges:~$
olav@dinges:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```
How do I get output from that crazy glxgears command? It doesn't say a thing.[/QUOTE]


Mesa = no good....

same problem for me...I installed via synaptic, I ran fglrxconfig....

restarted....nothing will work...

---

### Post by mlomker on 2005-10-13
> 
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)


That crazy command is what you need for glxgears to give you fps output in Breezy.  How else did you test your machine?  The fgl_glxgears test is ATI-specific and gives lower numbers.

If you see 'Mesa' from fglrxinfo it meant that the drivers were not installed properly and your performance is a 1/10th of what it should be.  Try rerunning the apt-get commands and put a --reinstall after the 'install' keyword.

---

### Post by Olav on 2005-10-13
[QUOTE=jecos]It would help if you would actually state what card you are using and what your xorg.conf looks like.. 'ati' and 'radeon' drivers are open source, 'fglrx' is ati's proprietary driver for radeon 8500 and up..  Its a work in progress..[/QUOTE]
I am fully aware that it is a work in progress, but unless ATI is going to really open up their chip specs and drivers I' m still going to blame them :p 

Anyway, the card is (according to device Management) a Radeon R200 QL [Radeon 8500 LE], OEM Vendor: Hercules.

And this is the xorg.conf, as created by fglrxconfig, I admit I don't understand a lot of what' s in there:

```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

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
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

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
    Option "XkbLayout"	"en_US"

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
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
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
    BusID "PCI:1:0:0"    # vendor=1002, device=514c
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
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
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

### Post by SilverTab on 2005-10-13
Here's my result for glrxgears:
973 frames in 5.2 seconds = 186.916 FPS
960 frames in 5.5 seconds = 176.115 FPS


display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1


:(

---

### Post by Olav on 2005-10-13
[QUOTE=mlomker]That crazy command is what you need for glxgears to give you fps output in Breezy.  How else did you test your machine?[/QUOTE]
By just running glxgears of course, without the crazy command. 

> The fgl_glxgears test is ATI-specific and gives lower numbers.

If you see 'Mesa' from fglrxinfo it meant that the drivers were not installed properly and your performance is a 1/10th of what it should be.  Try rerunning the apt-get commands and put a --reinstall after the 'install' keyword.
Will do in a minute ;)

---

### Post by mlomker on 2005-10-13
> By just running glxgears of course, without the crazy command. 


Then you don't have the Breezy version of the file, unless they changed it today.  I haven't been able to run an update since the formal release...the servers just time out.

---

### Post by SilverTab on 2005-10-13
Ok I just did a clean install of Ubuntu Breezy...

What would be your suggestion mlomker???
what would be the safest way to install the driver on a fresh install?

That way I know nothing I did before will cause a conflict!

---

### Post by SilverTab on 2005-10-13
Note: The EASIEST way....i.e.  8.16.20....no need for the latest version...any working version will do!

---

### Post by mlomker on 2005-10-13
[QUOTE=SilverTab]Note: The EASIEST way....i.e.  8.16.20....no need for the latest version...any working version will do![/QUOTE]

That's what the first post of this thread was for.

---

### Post by Olav on 2005-10-13
[QUOTE=mlomker]Then you don't have the Breezy version of the file, unless they changed it today.  I haven't been able to run an update since the formal release...the servers just time out.[/QUOTE]
Okay, I' m back. Back to VESA, that is :(

First, there is nothing wrong with the glxgears utility. Turned out I never let it run long enough to actually come up with an FPS rate. Yes, it was that slow.

Second, I did exactly what you told me, reinstalled the packages you named. Must warn you however, there is actually no package called **linux-restricted-modules-2.6.12**, look:

```
olav@dinges:~$ apt-cache search linux-restricted-modules-2.6.12
linux-restricted-modules-2.6.12-9-386 - Non-free Linux 2.6.12 modules on 386
linux-restricted-modules-2.6.12-9-386-nvidia-legacy - Non-free Linux 2.6.12 NVIDIA legacy module on 386
linux-restricted-modules-2.6.12-9-686 - Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIVlinux-restricted-modules-2.6.12-9-686-nvidia-legacy - Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV
linux-restricted-modules-2.6.12-9-686-smp - Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules-2.6.12-9-686-smp-nvidia-legacy - Non-free Linux 2.6.12 modules on PPro/Celeron/PII/PIII/PIV SMP
linux-restricted-modules-2.6.12-9-k7 - Non-free Linux 2.6.12 modules on AMD K7
linux-restricted-modules-2.6.12-9-k7-nvidia-legacy - Non-free Linux 2.6.12 modules on AMD K7
linux-restricted-modules-2.6.12-9-k7-smp - Non-free Linux 2.6.12 modules on AMD K7 SMP
linux-restricted-modules-2.6.12-9-k7-smp-nvidia-legacy - Non-free Linux 2.6.12 modules on AMD K7 SMP

```

Of those, I took **linux-restricted-modules-2.6.12-9-k7** which also matches the kernel I' m running.

I did the fglrxconfig and shut down X with Ctrl+Alt+BS, but no joy. Then I rebooted, and it was almost like Eureka! Perfect FPS on glxgears, and the info in fglrxinfo showed ATI as vendor...

Then I was almost finished typing a message, telling you what a great guru you really are :) (I still do not doubt that)

But **old** problems started again, causing the screen to freeze completely except for the mouse cursor.

I have tried several things, while being logged in from another machine with ssh to keep an eye on top. And it puzzles me completely. The screen does not necessarily freeze when I'm running "heavy" stuff like glxgears. Even after a fresh reboot, after logging in and using only gedit and Firefox it goes STOP.

In fact, when that happens, X takes almost 100% CPU usage and only because I have the ssh login I can kill -9 the sucker and return more or less to normal. Took me a couple of reboots though, to test it through.

So. the only driver that seems capable of giving me video overlay for TVTime **and** good 3D performance, is actually preventing me from doing anything for longer than a few minutes...

I need to go to bed now. In fact, I needed to go to bed 3-4 hours ago. I appreciate all the cooperation here and I do hope that this thing gets sorted out during the weekend. This is going to be quite the learning experience :D

---

### Post by SilverTab on 2005-10-13
[QUOTE=mlomker]That's what the first post of this thread was for.[/QUOTE]


ok ill follow the instructions closely (again)...and make sure I didnt miss anything....

i'll report back!... *fingers crossed*

---

### Post by Olav on 2005-10-13
[QUOTE=mlomker]
[quote=SilverTab]
Note: The EASIEST way....i.e. 8.16.20....no need for the latest version...any working version will do![/quote]
That's what the first post of this thread was for.[/QUOTE]
Yes, and while I agree that it should work, it is not working for everybody - alas!

---

### Post by souled on 2005-10-13
How do I find out which kernel I'm running?

---

### Post by Téragone on 2005-10-13
type **uname -a**

---

### Post by SilverTab on 2005-10-13
nah.,..nothing will do...

I followed your exact instructions on a clean install and it wont work (and It was working in hoary :( )

Do you think the online xorg.conf tools you posted in your original thread might help?

---

### Post by mlomker on 2005-10-13
> Yes, and while I agree that it should work, it is not working for everybody - alas!

Nothing works for everyone and it took weeks to refine the last how-to.  The problem is that they were making major changes in Breezy up until the last minute and I wouldn't be surprised to see big updates for a bit yet.  I wasn't even using Ubuntu when Hoary was released, so I'm not sure if it was the same story then.

---

### Post by Jujimufu on 2005-10-13
After going through the nightmare which was Hoary ATI drivers, this was just breezy (no pun intended, okay maybe).

Worked fine for me.  Thanks!

---

### Post by mlomker on 2005-10-13
> Do you think the online xorg.conf tools you posted in your original thread might help?

Sort of.  The problem is that they moved the font directory in Breezy under /usr/share and I also had a problem with the int10a module loading.  Every release of Ubuntu becomes less like Debian...for better or for worse.

I've heard reports that people have had luck with **sudo dpkg-reconfigure xserver-xorg**.   

It's hard to write an ATI how-to because everybody gives me feedback about what worked and didn't and the next guy says the opposite...I get to the point where all I can do is list things to try.  I only have one PC, myself, and it's a laptop with a 9700 and that's old news by desktop standards even though it's a new laptop...

---

### Post by mlomker on 2005-10-13
> there is actually no package called **linux-restricted-modules-2.6.12**, look:


That's right.  My Hoary how-to probably has gone through 50 edits.  If you write a good one I'll put it in the sticky for you. ;)

> But **old** problems started again, causing the screen to freeze completely except for the mouse cursor.

Well, I do my best helping people with the drivers but hardware problems and poorly written software...that's a taller order.

> This is going to be quite the learning experience :D

For all of us!  As soon as we get up to speed the six months have passed and Draper will be here.

I'll be working on the 8.18.6 drivers, myself...it fixes my misdetected resolution problem but no 3D so far.  :(

---

### Post by SilverTab on 2005-10-13
[QUOTE=mlomker]I get to the point where all I can do is list things to try.  I only have one PC, myself, and it's a laptop with a 9700 and that's old news by desktop standards even though it's a new laptop...[/QUOTE]


hey no worries, I appreciate your help A LOT, I'm sure you're doing the best you can and every reply is greatly appreciated! ;)

I just don't understand why the sudden problem with this driver since it always worked in the past...and seeing people who got it to work without any problems (like it did for me in hoary) is kinda frustrating :P  especially with a clear and easy to follow how-to like this one...

I know I did nothing wrong....if it can help though... when I did the last 2 apt-get
(linux-restricted and xconf-driver) I was told that the latest version of the two is already installed...

---

### Post by mlomker on 2005-10-13
> especially with a clear and easy to follow how-to like this one...


You haven't detailed what you're getting.  You getting a desktop but ending up with Mesa or a more dramatic error message?

The usual diagnostics:

```

lsmod | grep fglrx
dmesg | grep fglrx
gksudo gedit /var/log/Xorg.0.log

```

I've also run across people that swear there's something wrong with Breezy's built-in drivers.  You might end up trying to remove all of the previously installed packages and then download the driver from ATI like we did with Hoary.  The very latest driver, 8.18.6 seems to not work at the moment, but that doesn't mean that 8.16.20 wouldn't.

You have a clean system right now, so no loss if you bork it while trying things.

---

### Post by SilverTab on 2005-10-13
[QUOTE=mlomker]You haven't detailed what you're getting.  You getting a desktop but ending up with Mesa or a more dramatic error message?

The usual diagnostics:

```

lsmod | grep fglrx
dmesg | grep fglrx
gksudo gedit /var/log/Xorg.0.log

```

I've also run across people that swear there's something wrong with Breezy's built-in drivers.  You might end up trying to remove all of the previously installed packages and then download the driver from ATI like we did with Hoary.  The very latest driver, 8.18.6 seems to not work at the moment, but that doesn't mean that 8.16.20 wouldn't.

You have a clean system right now, so no loss if you bork it while trying things.[/QUOTE]


lsmod | grep fglrx gave the following result:
```
fglrx                 245412  0
agpgart                32328  2 fglrx,intel_agp

```

dmesg | grep fglrx  gave the following result:
```
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4295579.350000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4295579.350000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4295579.364000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4295579.365000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4295579.365000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4295579.365000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4295579.365000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[4295579.366000] [fglrx:firegl_unlock] *ERROR* Process 9683 using kernel context 0

```

The result of Xorg.0.log is more than 2000lines long, not sure if I should post it here?

---

### Post by mlomker on 2005-10-14
> [4295579.364000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[4295579.366000] [fglrx:firegl_unlock] *ERROR* Process 9683 using kernel context 0

The result of Xorg.0.log is more than 2000lines long, not sure if I should post it here?

You can attach text files to posts here, no problem.  There's no need, though...these are 'good' errors.

Take a look at [this thread]("http://www.rage3d.com/board/showthread.php?threadid=33736241"), though it is a little old.  ATI's forums aren't Ubuntu-specific, but obviously a great resource for ATI driver problems.  You could do some searches on these errors and see what comes up.

---

### Post by SilverTab on 2005-10-14
[QUOTE=mlomker]You can attach text files to posts here, no problem.  There's no need, though...these are 'good' errors.

Take a look at [this thread]("http://www.rage3d.com/board/showthread.php?threadid=33736241"), though it is a little old.  ATI's forums aren't Ubuntu-specific, but obviously a great resource for ATI driver problems.  You could do some searches on these errors and see what comes up.[/QUOTE]


mmm I followed the guide...however I only get 1 of the 2 errors mentioned....I still decided to read on...it says to open menu.lst (from /boot/grub)
and look for the kernel line....now here is the suggested modification:
There you should find something like:

kernel /boot/vmlinuz root=/dev/hda1 video=vesafb:ywrap,mtrr,vga=0x31X <---- here you need to add the code found below.


however, this is what my entry looks like....there's no "video" entry in my grub config... :(
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash

---

### Post by SilverTab on 2005-10-14
mlomker: just out of curiosity, what do you get when you do
cat /proc/mtrr 

??

---

### Post by SilverTab on 2005-10-14
oh well I tried posting on the rage3d forum...hopefully someone there will be able to help me out! :(

mlomker: I would like to thank you for all your help and your patience! again, its really appreciated! :)

one last thing... when I do cat /proc/mtrr, the only thing showing up is:

reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=1

which is my ram....I see no entry for video memory...

---

### Post by Cloud[01] on 2005-10-14
Allright everything is working great, except from the Resolution.
I'm on a widescreen, so my best resolution would be:
1280x800
But all I can get is 1024x768 which is pretty bad because it stretches everything
my xorg.conf:
```

...
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection
...

```
So I don't know why it doesn't use this resolution. Any hint?

By the way, the real test to get fps with the drivers installed correctly is:
```

fgl_glxgears

```
(I got a:
```

2808 frames in 5.0 seconds = 561.600 FPS
3767 frames in 5.0 seconds = 753.400 FPS
4079 frames in 5.0 seconds = 815.800 FPS
4058 frames in 5.0 seconds = 811.600 FPS

```)
For the control panel
```

fireglcontrol

```

ciop ciop

---

### Post by zupermanz on 2005-10-14
I've just made a clean kubuntu install and did what the how to said...exept the part linux-restricted-modules-$(uname -r) but no 3d acceleration . I still have mesa. Any ideas? I have AMD64 3200,via chipset and ati 9600 pro


I did --reinstall linux-restricted-modules-$(uname -r) from the sepositories and non the cd... Rebooting and......

---

### Post by mlomker on 2005-10-14
> But all I can get is 1024x768 which is pretty bad because it stretches everything

That's a known bug with the 8.16.20 driver and certain displays.  My own laptop is one of them, unfortunately.

I'm going to try getting the new 8.18.6 driver installed and write a how-to for it.  It solves that detection problem, but I had no luck getting it installed yesterday.

---

### Post by mlomker on 2005-10-14
> I've just made a clean kubuntu install and did what the how to said...exept the part linux-restricted-modules-$(uname -r) but no 3d acceleration..

You need the restricted modules for the fglrx.ko file (the kernel driver).  I just did a clean 32-bit install and updated the how-to again.  It looks like it's best to **sudo dpkg-reconfigure xserver-xorg** rather than using ATI's fglrxconfig.

---

### Post by zupermanz on 2005-10-14
[QUOTE=mlomker]sudo dpkg-reconfigure xserver-xorg[/b] rather than using ATI's fglrxconfig.[/QUOTE]
I did that and x couldnt start... it froze on checking battery status.....
i copied the old xconf to restart x again.
i apt-get the modules..reseting.. brb.

---

### Post by zupermanz on 2005-10-14
Nope that didnt do it eather!
I stall have mesa!

---

### Post by mlomker on 2005-10-14
[QUOTE=zupermanz]I did that and x couldnt start[/QUOTE]

Attach a copy of the xorg.conf and your /var/log/Xorg.0.log (from the failed startup) and we'll take a look.

---

### Post by hackyou on 2005-10-14
[QUOTE=mlomker]That's a known bug with the 8.16.20 driver and certain displays.  My own laptop is one of them, unfortunately.

I'm going to try getting the new 8.18.6 driver installed and write a how-to for it.  It solves that detection problem, but I had no luck getting it installed yesterday.[/QUOTE]

That's my problems tooooooooo!
I hope you'll make it works, if you need any help just ask.

---

### Post by TheRay1987 on 2005-10-14
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

$ fgl_glxgears
1528 frames in 5.0 seconds = 305.600 FPS
1639 frames in 5.0 seconds = 327.800 FPS
2145 frames in 5.0 seconds = 429.000 FPS
2144 frames in 5.0 seconds = 428.800 FPS
1771 frames in 5.0 seconds = 354.200 FPS
1838 frames in 5.0 seconds = 367.600 FPS
1579 frames in 5.0 seconds = 315.800 FPS
1641 frames in 5.0 seconds = 328.200 FPS
1604 frames in 5.0 seconds = 320.800 FPS

I had installed my driver using a howto guide on these forums before breezy came out. It included chaging a bunch of stuff in my xorg.conf file. And just a reminder, ALWAYS MAKE A BACKUP BEFORE CHANGING YOUR xorg.conf. Here is my xorg.conf file (/etc/X11/xorg.conf):
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
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load    "GLcore"
	Load	"glx"
	Load	"dri"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"freetype"
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
  	Identifier 	"ATI"
  	Driver     	"fglrx" # this is the important bi
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
	Identifier	"SONY HMD-A20"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	48-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"SONY HMD-A20"
	DefaultDepth	24
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

---

### Post by zupermanz on 2005-10-14
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
#	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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


This is mine .... i cant understand why i still have mesa!

---

### Post by zupermanz on 2005-10-14
when i do sudo apt-get install linux-restricted-modules-$(uname -r
i get 
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.12-9-amd64-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Is this ok?

---

### Post by Téragone on 2005-10-14
This package is installed by default, so if you don't have removed it it's normal.

---

### Post by ilans on 2005-10-14
After a lot of experiments (includ  the "how-to" manual) I realized that 
my ATI Radeon 9550 card is not recognize in my Ubuntu kernel

lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

This is the reason of my non 3D acceleretaion.
BUT HOW I CAUSE MY KERNEL TO RECOGNIZE MY CARD ???

---

### Post by SilverTab on 2005-10-14
[QUOTE=ilans]After a lot of experiments (includ  the "how-to" manual) I realized that 
my ATI Radeon 9550 card is not recognize in my Ubuntu kernel

lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

This is the reason of my non 3D acceleretaion.
BUT HOW I CAUSE MY KERNEL TO RECOGNIZE MY CARD ???[/QUOTE]


im right there with you!...

weird thing is that, it was working in hoary...with an older kernel! :(

---

### Post by zupermanz on 2005-10-14
fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)



is the libGL the problem?

---

### Post by remmelt on 2005-10-14
```
lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
```

```
 $ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

For me. Used to work under Hoary, after the dist-upgrade X didn't come back up and when I followed this guide it did. Not the right driver though, and the GUI seems sluggish, especially when using Firefox.

---

### Post by GaryG on 2005-10-14
Would this work on my laptop (ATI Radeon Mobility)?

---

### Post by zupermanz on 2005-10-14
I think that it must be a 64bit problem because with 32 bits i didnt had a problem...

---

### Post by remmelt on 2005-10-14
Following the other thread:

change your xorg.conf so that the driver isn't "ati" but "fglrx", restart X and presto:

```
fgl_glxgears 
1648 frames in 5.0 seconds = 329.600 FPS
2016 frames in 5.0 seconds = 403.200 FPS
1978 frames in 5.0 seconds = 395.600 FPS
2017 frames in 5.0 seconds = 403.400 FPS
2010 frames in 5.0 seconds = 402.000 FPS

```

---

### Post by zupermanz on 2005-10-14
nope i had already tried that but nothing Here is my xorg.conf
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
#	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by GameManK on 2005-10-14
[QUOTE=remmelt]Following the other thread:

change your xorg.conf so that the driver isn't "ati" but "fglrx", restart X and presto:

```
fgl_glxgears 
1648 frames in 5.0 seconds = 329.600 FPS
2016 frames in 5.0 seconds = 403.200 FPS
1978 frames in 5.0 seconds = 395.600 FPS
2017 frames in 5.0 seconds = 403.400 FPS
2010 frames in 5.0 seconds = 402.000 FPS

```[/QUOTE]

THANK YOU

this worked, ... i thought "ati" sounded more like the generic driver..

---

### Post by zupermanz on 2005-10-14
do you have 64 or 32 bit?

---

### Post by mlomker on 2005-10-14
[QUOTE=GaryG]Would this work on my laptop (ATI Radeon Mobility)?[/QUOTE]

Yes, that's what I have.  The drivers support the 8500+.

---

### Post by GaryG on 2005-10-15
Thanl you mlomker

---

### Post by eightysix on 2005-10-15
Well, after failing to the 8.18.6 driver to work, I tried modifying 8.16.20 instead. For the most part, I got my video card to use the "fglrx" driver by commenting out folders that didn't exist in the filesystem in the first place!

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	# FontPath"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	# FontPath"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	# FontPath"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	# FontPath"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection
```

But, fglrxinfo is **still** broken. :mad: 

```
eightysix@hikaru:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I'm assuming that this is an AMD64 related problem since the people who are having trouble getting to work are using it (including myself).

Edit: Scratch that. I had to change back to using the "ati" driver since the "fglrx" driver would crash my xorg configuration.

---

### Post by toujours on 2005-10-15
Allow me to join this thread as I too am experiencing the similar problems : AMD64, 
ATI drivers installed with restricted modules as suggested, you get the picture...

```

fglrxinfo
libGL error: drmMap of framebuffer failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

---

### Post by jamesford on 2005-10-15
hmm, i got 3D working just fine, but whats wrong with the 2D performance? like moving a window sideways or playing a fullscreen movie uses almost all of my cpu, while it used next to nothing before i installed the fglrx stuff...

---

### Post by mlomker on 2005-10-15
I just got a post to another thread from a developer.  There is a patch for ATI's 8.18.6 installer that is supposed to fix all of the problems with installing that package.

[Look here.]("http://ati.cchtml.com/show_bug.cgi?id=198")

I can't test it, myself, without doing a clean reload.  Someone please let me know if it works.  If so then I hope we can find someone to put the .deb files on a web server.

---

### Post by toujours on 2005-10-15
[QUOTE=mlomker]I just got a post to another thread from a developer.  There is a patch for ATI's 8.18.6 installer that is supposed to fix all of the problems with installing that package.

[Look here.]("http://ati.cchtml.com/show_bug.cgi?id=198")

I can't test it, myself, without doing a clean reload.  Someone please let me know if it works.  If so then I hope we can find someone to put the .deb files on a web server.[/QUOTE]

Ewwww..... :confused: :( 

If that's what it takes I'll just wait until I can use Synaptic to download it...

---

### Post by Anchovie on 2005-10-15
[QUOTE=mlomker]I just got a post to another thread from a developer.  There is a patch for ATI's 8.18.6 installer that is supposed to fix all of the problems with installing that package.

[Look here.]("http://ati.cchtml.com/show_bug.cgi?id=198")

I can't test it, myself, without doing a clean reload.  Someone please let me know if it works.  If so then I hope we can find someone to put the .deb files on a web server.[/QUOTE]

How do you do a clean reload? If you can give me the instructions on a clean reload I can test it out, since I'm still struggling with mine.

---

### Post by mlomker on 2005-10-15
> How do you do a clean reload?

I was referring to reinstalling Ubuntu from CD and starting over.  Once you install a package manually it is almost impossible to get back to a clean system, which you really need in order to write a workable how-to for others.  A freshly loaded system and then creating a .deb file with the patch is the only clean way to test things.  I'm thinking about buying another PC that I'll use just for that, but right now I only have one PC.

---

### Post by Anchovie on 2005-10-15
[QUOTE=mlomker]I was referring to reinstalling Ubuntu from CD and starting over.  Once you install a package manually it is almost impossible to get back to a clean system, which you really need in order to write a workable how-to for others.  A freshly loaded system and then creating a .deb file with the patch is the only clean way to test things.  I'm thinking about buying another PC that I'll use just for that, but right now I only have one PC.[/QUOTE]

Okay that's fine, I wouldn't mind doing that, I'll post back here as soon as I get the result and whatever the troubleshooting steps I have to go through in order to get it to work.

---

### Post by remmelt on 2005-10-15
[QUOTE=mlomker]I was referring to reinstalling Ubuntu from CD and starting over.  Once you install a package manually it is almost impossible to get back to a clean system, which you really need in order to write a workable how-to for others.  A freshly loaded system and then creating a .deb file with the patch is the only clean way to test things.  I'm thinking about buying another PC that I'll use just for that, but right now I only have one PC.[/QUOTE]
Ha! But you wouldn't shoot yourself in the foot and buy ATI again, would you? ;)


To add something on-topic to this thread: I have an AMD64 processor, but I'm running 32 bit Ubuntu.

---

### Post by mlomker on 2005-10-15
> Ha! But you wouldn't shoot yourself in the foot and buy ATI again, would you? 

Yeah, I just ordered a box with an X300 minute ago.  Somebody has to help people with ATI cards on here. ;)

> To add something on-topic to this thread: I have an AMD64 processor, but I'm running 32 bit Ubuntu.

So do I and haven't had any trouble, personally, with 32-bit.  My new desktop will be Pentium-D.

---

### Post by TLE on 2005-10-15
First of all my specs are:
AMD 64 3200+
ATI Radeon X800XL
(If you need anything else)

I've been following this thread, and did as the howto said. When I get to the "restricted modelus" part i'm told that it is already installed, but I understand that is not a problem. When i've done the configuration I get the same result as a lot of the other people here, I cant start up i X, and it's working fine except for the 3D acc. which is still running under Mesa. 

I was sort of expecting trouble and since I have plenty of harddrive space I used a rescueCD with partimage to make a image of my Ubuntu partition, with an absolutely clean install. (Which also for me, means that it won't start X).

So this means that I can "reload" an absolutly clean install in about 25 min. So i'm ready to try anything you(mlorker) can think of. But i'm an intermediate Linux so i'm might going to need a little guidance.

I'm thinking if you are interesseted maybe we should do it off forum, not to clogg this thread up. So, I have a few questions to the patch, but i'll postpone posting them until I know if anynody will assist me.

Regards TLE

---

### Post by TLE on 2005-10-15
Sorry. 
"I cant start up i X"
It is of course supposed to read 
"I CAN start up in X"

---

### Post by mlomker on 2005-10-15
> I cant start up i X, and it's working fine except for the 3D acc. which is still running under Mesa. 


I'm going to assume that you are running 32-bit Ubuntu (k7 kernel).  The 64-bit version is a lost cause right now.  I spent an entire day and couldn't get it to work and so have a number of other advanced but non-developer users.  Something's broke there.

Boot up with the built-in fglrx drivers (I assume you've already created an xorg.conf using the dpkg reconfigure).  Find your fglrxinfo and do an ldd against it.

```

sudo updatedb
locate libGL.so.1

whereis fglrxinfo
ldd /somepath/fglrxinfo
cat /etc/ld.so.conf

```

---

### Post by TLE on 2005-10-15
Sorry about the misunderstanding, but I'm actually using the 64 bit version. I wasn't aware that It was a "lost cause". I thought a read posts from other 64-bit users. My bad.

I'll try the 32 bit version, as soon as I can get It downloaded. But anyway the offer still stands. I have a lot of harddrive space for partition images, (and fall vacation for the next week) so I can can do "fresh installs" by the snap of my fingers, almost. So I wouldn't mind helping out if I can, also with the 64 bit version later, I can just install both a 64 bit version and a 32, just let me know.

I'll post a soon as i've tried the how to on the 32 bit version

---

### Post by mlomker on 2005-10-15
[QUOTE=TLE]Sorry about the misunderstanding, but I'm actually using the 64 bit version.[/QUOTE]

A few days before Breezy's release they repackaged Xorg into many smaller packages, many of them for video drivers.  At the moment there is no known way of getting rid of Mesa on 64-bit.  I had the built-in 8.16.20 drivers working in 3D but my box was seriously modded that it wasn't a good example...I'm the only one that I know of who has gotten the Breezy drivers to work on 64-bit.

Since I was going to do a clean reload anyway, I decided to go 32-bit so that I can use multimedia and my winmodem and all that jazz.

---

### Post by ilans on 2005-10-15
MLOMKER I need your help:
I generated the 5 new patched debs files (using the patch):
fglrx-control_8.18.6-1_i386.deb
fglrx-kernel-source_8.18.6-1_i386.deb
fglrx-sources_8.18.6-1_i386.deb
xorg-driver-fglrx_8.18.6-1_i386.deb
xorg-driver-fglrx-dev_8.18.6-1_i386.deb
(I CAN ZIP AND SEND THEM VIA YOUSENDIT)

And I did (successfully) these steps:

1. sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
Than I rebooted (before change correctly xorg.conf in order to launce to gnome)

2. I install the 5 new patched debs files :
fglrx-control_8.18.6-1_i386.deb
fglrx-kernel-source_8.18.6-1_i386.deb
fglrx-sources_8.18.6-1_i386.deb
xorg-driver-fglrx_8.18.6-1_i386.deb
xorg-driver-fglrx-dev_8.18.6-1_i386.deb

3. I untar /usr/src/fglrx.tar.bz2

4. I have a problem in the folowing step:
"generate the kernel module for your current kernel"

I tried both:

1. sudo module-assistant a-i fglrx
(I installed module-assistant and linux-header)

I get this message:
/usr/bin/make -C /usr/src/linux-headers-2.6.12-9-386
SUBDIRS=/usr/src/modules/fglrx modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11:
gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12:
gcc-3.4: command not found
make[1]: gcc-3.4: Command not found

2. sudo sh make.sh

I get this message:
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make.sh: line 843: cd: 2.6.x: No such file or directory
/bin/sh: gcc-3.4: command not found
/bin/sh: gcc-3.4: command not found


I DONT UNDERSTAND WHY I HAVE GOT AN ERROR ON GCC 3.4 WHILE I HAVE BEEN USING GCC 4.0 !!!

---

### Post by arjun on 2005-10-15
Hi.  My problem is very similar to most of the ones described here, however, I think I can add another significant problem to the list.  As well as fglrx using mesa as the driver as opposed to openGL, the transfer type is PCI.  My card is plugged into an AGP slot and with the 8.13.14 drivers in hoary, AGP was recognized and the driver worked without a hitch (4000 rpm in glxgears).  I've tried the driver in the repo (with fglrx module) and ATI's giant sh installer- both yield the same terrible results.  I'm using Power Colour Radeon 9600 SE and the 686-SMP kernel.  Kernel Headers are also installed...

---

### Post by nbx909 on 2005-10-15
okay i have a radeon 9600 pro on an amd xp 2000+ machine... i get this when i run fglrxinfo```

michael@mikeubuntu:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

michael@mikeubuntu:~$

```
So i tried doing sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
but i get
```
michael@mikeubuntu:~$ sudo echo "/usr/X11R6/lib" >> /etc/ld.so.conf
bash: /etc/ld.so.conf: Permission denied

```
any ideas?

---

### Post by mlomker on 2005-10-15
> 
bash: /etc/ld.so.conf: Permission denied
any ideas?

That means that you already have a file there.  I've done two clean installs today and that file doesn't exist on either box.  Is yours an upgrade from Hoary or the 64-bit version?

Try editing it with nano.

```

sudo nano /etc/ld.so.conf

```
 
Ctrl-W, Y, Enter to save.

---

### Post by eudemon on 2005-10-15
Hello,
Just another person who cannot seem to get 3d acceleration working.  I just followed the instructions to install on a clean installation of breezy.  I have a similar system to you, mlomker:  64 bit amd cpu laptop, running 32 bit breezy, with a radeon 9700 mobile card.

I've tried xorg.conf files generated by fglrx-control, dpkg-reconfigure xserver-xorg, and simply modifying the original to replace the string "ati" with "fglrx".  So far nothing has worked.  

I was able to get acceleration consistently working under hoary by using this hack:  [http://ubuntuforums.org/showpost.php?p=77060&postcount=54](http://ubuntuforums.org/showpost.php?p=77060&postcount=54).  Otherwise, no dice.

Thanks for your help.

---

### Post by Anchovie on 2005-10-16
Hm... I tried to follow the steps located at [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198), but I got stuck on step 4, I got an error "bash: ./ati-installer: No such file or directory" when trying to run "./ati-installer 8.18.6 --buildpkg Ubuntu/breezy", anybody have any ideas? No error occured from the previous steps.t

---

### Post by ilans on 2005-10-16
[QUOTE=Anchovie]Hm... I tried to follow the steps located at [http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198), but I got stuck on step 4, I got an error "bash: ./ati-installer: No such file or directory" when trying to run "./ati-installer 8.18.6 --buildpkg Ubuntu/breezy", anybody have any ideas? No error occured from the previous steps.t[/QUOTE]

Dont work so hard.
Here is the 5 pached deb files (I managed to create them) but I'm stuck
in updating the kernel with the new module
     [http://s46.yousendit.com/d.aspx?id=29UM2H2HFBNF02HU7CROE0919E](http://s46.yousendit.com/d.aspx?id=29UM2H2HFBNF02HU7CROE0919E)

---

### Post by deepspring on 2005-10-16
Edit: See this post instead:

[http://www.ubuntuforums.org/showpost.php?p=575778&postcount=224](http://www.ubuntuforums.org/showpost.php?p=575778&postcount=224)

---

### Post by Anchovie on 2005-10-16
[QUOTE=ilans]Dont work so hard.
Here is the 5 pached deb files (I managed to create them) but I'm stuck
in updating the kernel with the new module
     [http://s46.yousendit.com/d.aspx?id=29UM2H2HFBNF02HU7CROE0919E](http://s46.yousendit.com/d.aspx?id=29UM2H2HFBNF02HU7CROE0919E)[/QUOTE]

I thought that's the purpose of step 4, to create the five deb packages... How did you created them? When you said using the "patch to generate 5 new deb files" in post 74, do you mean using the "update the Ubuntu packages scripts in the ati installer patch"? Or was it something else.

---

### Post by arjun on 2005-10-16
Hi.  Further elaborating on the 8.16.20 drivers; it looks as if my libraries are not linked correctly and I can't change them.  When typing "ldd /usr/bin/glxinfo", one of the entries is: libGL.so.1 => /usr/lib/libGL.so.1.  From what I understand, that library in particular out of all the other ones displayed is crucial for OpenGL and has to be linked to a lib in /usr/X11R6/lib.  Now that the problem is identified, I cannot fix it.  When I type: "sudo echo /usr/X11R6/lib >> /etc/ld.so.conf" I get a permission denied error.  When I wanted to check out ld.so.conf, it does not exist.  Do I have to create it?

---

### Post by Anchovie on 2005-10-16
[QUOTE=arjun]Hi.  Further elaborating on the 8.16.20 patch; it looks as if my libraries are not linked correctly and I can't change them.  When typing "ldd /usr/bin/glxinfo", one of the entries is: libGL.so.1 => /usr/lib/libGL.so.1.  From what I understand, that library in particular out of all the other ones displayed is crucial for OpenGL and has to be linked to a lib in /usr/X11R6/lib.  Now that the problem is identified, I cannot fix it.  When I type: "sudo echo /usr/X11R6/lib >> /etc/ld.so.conf" I get a permission denied error.  When I wanted to check out ld.so.conf, it does not exist.  Do I have to create it?[/QUOTE]

Yes, ld.so.conf is the file you'll have to create.

---

### Post by comradevik on 2005-10-16
sory for the n00b type question.. but how do i find out what videocard i get.. cuz the info says mesa.. which by now i know is bad.. i followe all the instructions but nothing worked... i suspect its an ATI but i got no idea ... i have an HP pavilion 753n and it doesnt say what graphics card i have anywhere except it says 64 mb DDR SDRAM inegrated intel extreme graphics with up to 64 mb shared video memory

---

### Post by mlomker on 2005-10-16
> 
     Option "UseInternalAGPGART" "no"         # <= Disables internal AGPgart driver


That won't do anything.  If you look at the output of **dmesg | grep fglrx** after booting you'll see this:

```

 Internal AGP support requested, but kernel AGP support active.
 Have to use kernel AGP support to avoid conflicts.

```

In other words, the driver ignores that line if the internal AGP Gart is built into the kernel, which it is on a Ubuntu kernel.  Perhaps there was a conflict with your card, but it doesn't make sense.  Have you tried adding it back and starting up?  If it's consistent then that's interesting.

---

### Post by mlomker on 2005-10-16
> i suspect its an ATI but i got no idea 

```

lspci | grep VGA

```

---

### Post by comradevik on 2005-10-16
```
victor@ubuntu:~$ lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
victor@ubuntu:~$
```


what's that mean.. should i go and buy a video-card?

---

### Post by mlomker on 2005-10-16
> what's that mean.. should i go and buy a video-card?

LOL.  If you play games you should!

You're using the integrated Intel video card and it's going to be very slow.  I'd recommend an Nvidia if you're buying a new card.  People say that they are less trouble under linux...then again, I don't read those threads.  ;)

---

### Post by comradevik on 2005-10-16
i dont play games .... they run slow :-D 

i work in blender.... and that depends on ram i think.. at least i haven't had problems with it 

under windows it run just as slow with some games... and some games worked fine (cs was perfect while american army was slow) but i dont play as much so i gave it up anyways.

---

### Post by eudemon on 2005-10-16
I just followed the instructions for removing and reinstalling, and at the reboot step X failed to start.  Simply went back and did an apt-get install for everything that I removed, changed xorg.conf to have "fglrx" again, and X could start up again.  But still no hardware acceleration.

Checked my linked libs using ldd, and the correct libraries from the X11R6 directory are being used.

I'm starting to get really frustrated.  I know that it is not the Ubuntu devs fault, but I'm going to have to go back to windows (blech) if I can't get this working soon.  What really gets me is that it worked under Hoary, albeit in a hacked fashion.

---

### Post by arjun on 2005-10-16
I've created ld.so.conf but I can't do anything to it.  I get permission denied even if I try to chmod it.  Is a fresh install justified?

---

### Post by mlomker on 2005-10-16
[QUOTE=arjun]I've created ld.so.conf but I can't do anything to it.  I get permission denied even if I try to chmod it.  Is a fresh install justified?[/QUOTE]

You have to use **sudo** to do anything with that file, but further experimentation this morning leads me to believe that the problem isn't in there anyway.

---

### Post by mlomker on 2005-10-16
> "fglrx" again, and X could start up again.  But still no hardware acceleration.

It's too late now for me to speculate on that.  It's possible that you've made enough library changes that you won't be able to use the ATI driver anymore.

>  What really gets me is that it worked under Hoary, albeit in a hacked fashion.

Did you do an upgrade from Hoary or a clean install?  I'd definitely try a clean install first.  That being said, you can always reinstall Hoary...it's not like there was anything wrong with Hoary.

---

### Post by eudemon on 2005-10-16
[QUOTE=mlomker]It's too late now for me to speculate on that.  It's possible that you've made enough library changes that you won't be able to use the ATI driver anymore.

Did you do an upgrade from Hoary or a clean install?  I'd definitely try a clean install first.  That being said, you can always reinstall Hoary...it's not like there was anything wrong with Hoary.[/QUOTE]

When Breezy became available, I did a clean install as soon as I had it downloaded, then followed the instructions in the first post.  Then, when that failed to work, I went back and did the removal and reinstallation bit.  That's where I hit this snag described in the previous post.  It wouldn't be a big deal to do another clean install at this point, as I haven't done much in the way of setting up stuff under my new system.

I've found that in the past, if I install xorg-driver-fglrx, then remove it, X will fail to start properly until I put it back, even though it wasn't there to begin with.  :confused: 

I could go back to Hoary, and I may do that.  I'd really like to get this working though; it seems like everyone but me can accomplish it.  

Are there still issues with the fglrx driver and the k7 kernel?  I seem to recall that being a problem in the past.

---

### Post by souled on 2005-10-16
Ok, after removing the restricted kernel thing and rebooting, I installed the fglrx-control and I just put in sudo apt-get install linux-restricted-modules-$(uname -r). It's asking me to insert the Breezy Badger CD. Is this supposed to happen?

---

### Post by mlomker on 2005-10-16
> I've found that in the past, if I install xorg-driver-fglrx, then remove it, X will fail to start properly until I put it back, even though it wasn't there to begin with.  :confused: 

In working with a few other people today I discovered that installation of that file renames the Mesa library and moves it to a backup directory.  I should think that the removal would copy it back, but maybe that doesn't always go so well.  I'm going to buy a 2nd PC so that I have one to test things on...probably with an X300 card since they are cheap.

>  I'd really like to get this working though; it seems like everyone but me can accomplish it. 

I wish that were true.  I'm trying to help a lot of people.  It seems like anyone with a 9550-series card can't get them working right now.  I've only talked to one person that has.

> Are there still issues with the fglrx driver and the k7 kernel?  I seem to recall that being a problem in the past.

Naw, that's what I'm running.  32-bit Kubuntu with a Mobility 9700 card and the 8.18.6 driver.  The newer driver took some work to get going but the included one was easy.

I think it really depends on your system board/card combination as to whether or not things are easy.  If you're going to reload then you could give the [newer driver]("http://ubuntuforums.org/showthread.php?p=411503") a shot.  I don't recommend it unless people are having trouble, but you're having trouble.  :)

---

### Post by eudemon on 2005-10-16
[QUOTE=mlomker]
Naw, that's what I'm running.  32-bit Kubuntu with a Mobility 9700 card and the 8.18.6 driver.  The newer driver took some work to get going but the included one was easy.[/QUOTE]

I've got the same video card, and an amd64 cpu running 32-bit Ubuntu on my laptop.  I've never had an easy time getting DRI working, with any version of the driver or of Ubuntu.  I might try the newer driver, just to see what happens, but I doubt it'll be any better than previous versions.  Experience has made me a pessimist unfortunately :???: .

I don't know enough about the hardware involved, but editing the driver source so that it thinks the kernel has no mtrr capabilities has gotten DRI working for me before.  That didn't work under Breezy before, but I might try it again, with both 8.16.20 and 8.18.6.

Btw, thanks for the thread, and all the work you've put into getting the fglrx driver working for people.  I'm sure everyone really appreciates how much of your own time you've put into getting other people's systems working.

---

### Post by mlomker on 2005-10-16
[QUOTE=]I don't know enough about the hardware involved, but editing the driver source so that it thinks the kernel has no mtrr capabilities has gotten DRI working for me before.  [/QUOTE]

There are some commands related to mtrr that you can pass to the kernel in grub's /boot/grub/menu.lst file.  There's a [thread here]("http://www.rage3d.com/board/showthread.php?threadid=33736241") discussing that.

It sounds like we have very similar hardware.  I'm running an amd64 3400+ with 32-bit Kubuntu and the k7 kernel.

You're welcome!  I hope we can come up with a solid how-to soon.

---

### Post by eudemon on 2005-10-16
[QUOTE=mlomker]There are some commands related to mtrr that you can pass to the kernel in grub's /boot/grub/menu.lst file.  There's a [thread here]("http://www.rage3d.com/board/showthread.php?threadid=33736241") discussing that.

It sounds like we have very similar hardware.  I'm running an amd64 3400+ with 32-bit Kubuntu and the k7 kernel.

You're welcome!  I hope we can come up with a solid how-to soon.[/QUOTE]
Thanks, I saw that thread before, but I'll take a closer look.  This looks like it might be able to help me.

EDIT:

Okay, on a hunch, I opened up my laptop and removed one of my two 512 mb ram chips.  I rebooted, and 3D acceleration worked like a charm.  Put it back in, rebooted again, and no 3D acceleration.  I'm gonna try removing te other ram chip to see what happens.  Can't believe this was my problem for the past 8 months.

---

### Post by eudemon on 2005-10-16
So, as long as I only have one of my two 512mb ram chips installed, hardware acceleration works beautifully.  Put them both in though, and there's an error that causes DRI to fail.  Something with mtrrs I guess.  Like I said, I don't know enough about the hardware to provide any useful info, but maybe someone else can make something of my situtation.  Maybe having both chips causes all my mtrrs to be used up, leaving none for my vram? :confused:

---

### Post by souled on 2005-10-17
Ok, I've tried this HOWTO and the 8.18.6 HOWTO, and no dice. I have a Radeon 9200, AMD Athlon XP 2500+. I got the drivers working on Hoary, but can't get them working on Breezy. I'm reinstalling Breezy right now, any ideas?

---

### Post by mlomker on 2005-10-17
> Maybe having both chips causes all my mtrrs to be used up, leaving none for my vram? 

That's really weird because that mtrr business refers to the video ram, which is totally separate memory on a 9700 from your system memory.  I have 1 Gig in my machine and the memory is different brands and different speeds.

Your box is fairly new so the BIOS should be up-to-date.  Have you made many changes in there?  I'd start poking around the BIOS looking for settings if I were you.

---

### Post by eudemon on 2005-10-17
I'll take a look.  It's been a while since I looked at my BIOS on this machine, but I remember that it was exremely limited.

---

### Post by eudemon on 2005-10-17
Yeah, my BIOS offers no options on ram, just says how much there is.  Once I get home tonight I can open up my box again, and see what the BIOS does when I have both chips in, but for now at least, halving my ram isn't a bad trade-off to have 3D acceleration.  :smile:

EDIT:

So looking at my ram a little closer, its the same brand, same speed, with slightly different model numbers.  Strange that it would cause problems to use both chips.

---

### Post by gelse on 2005-10-22
any solution yet about the resolution bug in 8.16.20 ?

reason: cant use the 8.18 driver, because it just doesnt work in some applications (ok, in games. ok in ONE game. wow - but as its the ONLY reason i need 3D-acceleration, and its the only game i play anyway, its critical...)

what would help me too, is a way to get the 8.14.13 to compile with GCC4.

---

### Post by clp on 2005-10-24
What about mtrr errors?

This is my error's log in dmesg...

[fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)

This thread...

([http://www.rage3d.com/board/showthread.php?threadid=33736241](http://www.rage3d.com/board/showthread.php?threadid=33736241))
Don't resolve anything (April 2004)

I have test 8.18  driver but I get the same error.

My "cat /proc/mtrr"
reg00: base=0x00000000 (   0MB), size=983552MB: write-back, count=1
reg01: base=0x20000000 ( 512MB), size=983296MB: write-back, count=1
reg02: base=0xd8000000 (3456MB), size=983104MB: write-combining, count=1

Any suggestion?

Sorry for my poor english...

---

### Post by mlomker on 2005-10-24
> What about mtrr errors?


The mtrr and firegl_unlock errors are a problem for some people but it's a bug and not an installation issue, so I can't help you.  There is a link for bugzilla at the top of every page and that's the only way to communicate with the developers about those sort of problems.

---

### Post by hounddog32 on 2005-10-26
I have followed the howto (upgraded to breezy, 32-bit kernel, Radeon 9100 integrated graphics) and have a problem not mentioned in this thread. I've looked elsewhere on the forum but most of it is hoary stuff that is mixing me up a bit. 

When I run fglrxinfo it tells me that the vendor is ATI, as it should be. xorg.conf has fglrx as the driver to use, all good.

When I run glxgears or fg_glxgears, the window opens, black background and the computer locks - i have to do a hard reset. I've not tried a game, but I can guess what it'll be.

---

### Post by mlomker on 2005-10-26
> i have to do a hard reset. I've not tried a game, but I can guess what it'll be.

I've seen a few other threads with similar results.  I gather that it is the 9200 and older that most often see the problem.

---

### Post by cyberkode on 2005-10-26
Hey I was wondering how I would go about getting 3d acceleration for my video card in my laptop. It is a ATI Rage Mobility 32.

Thanks,

Mike

---

### Post by Baf on 2005-10-26
I followed the guide by mlomker and it didn't work. Then I tried remmelt's suggestion which was replacing 'ati' with 'fglrx' in the xorg.conf driver. That worked. I rebooted and ran fglrxinfo and got what I wanted. 

However, I'm still having problems. I cant open up Totem to play an mp3 or a video clip. It says: > The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.

No, I don't have any other video apps open. I took a look at the Multimedia Systems Selector in System>Preferences and I just don't know which option to choose. 

I haven't installed any codecs which I was thinking was the problem, but before I installed the ati drivers I could listen to mp3's with Totem. Also, when I run glxgears the window pops up with the gears and it appears they are moving at the speed they should be. But it doesn't display the fps and time in the terminal and my computer becomes really slow.

EDIT: I just ran fgl_glxgears and I actually got results. My computer didn't become as slow and it outputted the fps, which was mostly in the eight hundreds. Like I said above, glxgears is really choppy and doesn't display output. I left it on for ten minutes, came back and it still didn't print anything.

---

### Post by mlomker on 2005-10-26
> I followed the guide by mlomker and it didn't work. Then I tried remmelt's suggestion which was replacing 'ati' with 'fglrx' in the xorg.conf driver. That worked. I rebooted and ran fglrxinfo and got what I wanted. 

That's what the **dpkg-reconfigure** does, so I have to assume that you skipped it.

> display output. I left it on for ten minutes, came back and it still didn't print anything.
[URL="http://ubuntuforums.org/showpost.php?p=412040&postcount=2"]
Look here.[/URL]

---

### Post by Baf on 2005-10-26
I didn't skip it, I don't think. I could have by mistake, but I have been trying to get the  video drivers to work for some time now so I was careful. Does it matter anyway, I got the ATI output after running fglrxinfo? I really hope not. 

I did just add that alias to the bash.bashrc file and now I got it to over a thousand. But my computer is still slow when running it. Is that normal? I wouldn't think so, but I don't know. 

Any suggestions on the other things? mlomker, thanks for the help and the guide. It must be very time consuming and I thank you for your efforts.

---

### Post by mlomker on 2005-10-26
> Does it matter anyway, I got the ATI output after running fglrxinfo? I really hope not. 

mlomker, thanks for the help and the guide. It must be very time consuming and I thank you for your efforts


It might not matter with your install but I want a how-to that always works (if that's possible).   

> I did just add that alias to the bash.bashrc file and now I got it to over a thousand. But my computer is still slow when running it. Is that normal? I wouldn't think so, but I don't know. 

I don't know, either.  You could try running **top** in a terminal to see what is taking up memory and processor time.

---

### Post by Septor on 2005-10-26
Just a heads up to all:  A new fglrx **8.18.8 has been released**.  This should include the native Ubuntu package scripts, so no more patches should be necessary to build the Ubuntu .debs.

Cheers.

---

### Post by Leopard on 2005-10-27
[QUOTE=mlomker]That's what the **dpkg-reconfigure** does, so I have to assume that you skipped it.[/URL][/QUOTE]
Is that all it does?  I went through I don't know how many reconfiguration questions and all I needed to do was change a single entry in xorg.conf?  :confused:  Do'h!
[QUOTE=Septor]Just a heads up to all:  A new fglrx **8.18.8 has been released**.  This should include the native Ubuntu package scripts, so no more patches should be necessary to build the Ubuntu .debs.

Cheers.[/QUOTE]
I hope this means a simplfied install of ATI drivers for AMD64 users is in the pipeline! Please!

Thanks for all your help guys :D

---

### Post by Septor on 2005-10-27
[QUOTE=Leopard]Is that all it does?  I went through I don't know how many reconfiguration questions and all I needed to do was change a single entry in xorg.conf?  :confused:  Do'h!

I hope this means a simplfied install of ATI drivers for AMD64 users is in the pipeline! Please!

Thanks for all your help guys :D[/QUOTE]

Unfortunately no.  the ATI drivers are built against the latest DRI, however Ubuntu includes a patch which breaks compatability.  So you will be stuck copying a different libdrm.a until the Ubuntu changes make it into DRI cvs.  I guess it is possible ATI will build a separate module against the patches DRI, but I doubt it.

*Edit:  I take that back.  The change is in DRI CVS, so 64bit should be okay on Xorg 6.9/70... whenever X7.0 makes it into Ubuntu though I don't know.*

---

### Post by wakeboarder on 2005-10-28
mlomker: great HowTo!
After installing Breezy I too got the vendor=Mesa from fglrxinfo
so I decided to switch to fglrx.
Everything seems to work nice and fast. However when I use suspend my laptop it freezes in resume, which never happend before.
Any suggestions?

---

### Post by mlomker on 2005-10-28
> Everything seems to work nice and fast. However when I use suspend my laptop it freezes in resume, which never happend before.


Yup.  fglrx does not support power management.  ATI states that in their FAQ's.  You'll have to choose.

---

### Post by jd_ on 2005-10-31
Just a note about the Mesa bug :
as suggested in the first page, I did a sudo apt-get install --reinstall needed_packages (note the **--reinstall**) and it worked fine : no more Mesa but
```
jd@Bibi:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```
which is actually better ;)

Thanks.

---

### Post by Baf on 2005-11-01
I have the ATI drivers installed properly... atleast thats what running fglrxinfo tells me. I can run Unreal Tournament fine, actually probably smoother than in Windows. 
However, when I am doing normal things on the desktop it still seems choppy. Like, minimizing a screen I can see the trails. It makes it slower, or makes it seem that way.
Let me know if any of you have any suggestions.

---

### Post by Septor on 2005-11-01
[QUOTE=Baf]I have the ATI drivers installed properly... atleast thats what running fglrxinfo tells me. I can run Unreal Tournament fine, actually probably smoother than in Windows. 
However, when I am doing normal things on the desktop it still seems choppy. Like, minimizing a screen I can see the trails. It makes it slower, or makes it seem that way.
Let me know if any of you have any suggestions.[/QUOTE]

This is a common/known problem with fglrx.  The 2D part of the driver seems to be slower in some cases when compared with the open source Radeon driver.  As always, it has improved over time, but still seems to be slower in a few cases.  I noticed on my laptop that the screen-fade when logging out is smooth with the radeon driver but only has 3-5 chunky "steps" with the fglrx driver... right now I don't care... I rather have 3D and slow 2D than fast 2D and no 3D at all :)

---

### Post by Baf on 2005-11-01
[QUOTE=Septor]This is a common/known problem with fglrx.  The 2D part of the driver seems to be slower in some cases when compared with the open source Radeon driver.  As always, it has improved over time, but still seems to be slower in a few cases.  I noticed on my laptop that the screen-fade when logging out is smooth with the radeon driver but only has 3-5 chunky "steps" with the fglrx driver... right now I don't care... I rather have 3D and slow 2D than fast 2D and no 3D at all :)[/QUOTE]

Geesh, that blows. But yeah, I'd rather 3d.

---

### Post by sciurus on 2005-11-01
This partially worked for me. I have a Radeon 9800 AIW Pro on a 19" Dell P991  Epox ERDA3+ with a Athlon XP 2600 and 2x512mb RAM. glxgears reports more than 4000 fps, but my resolution and refresh rate won't go past 1024x768 and 60Hz.

If I decide high resolution is more important than 3d acceleration, can I safely go back to my old xorg.conf without making any other changes?

My current /etc/X11/xorg.conf is

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "type1"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9800 AIW"
        Driver          "fglrx"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL P991"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon 9800 AIW"
        Monitor         "DELL P991"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

The part of x's log that looks relevant
```

(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): No EDID information available.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 9 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 +hsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525 -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  600 601 605 742 -hsync
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  480 491 493 525 -hsync
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync -vsync
(==) fglrx(0): DPI set to (75, 75)

```

---

### Post by Septor on 2005-11-01
[QUOTE=sciurus]This partially worked for me. I have a Radeon 9800 AIW Pro on a 19" Dell P991  Epox ERDA3+ with a Athlon XP 2600 and 2x512mb RAM. glxgears reports more than 4000 fps, but my resolution and refresh rate won't go past 1024x768 and 60Hz.

If I decide high resolution is more important than 3d acceleration, can I safely go back to my old xorg.conf without making any other changes?

My current /etc/X11/xorg.conf is

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "type1"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Radeon 9800 AIW"
        Driver          "fglrx"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "DELL P991"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Radeon 9800 AIW"
        Monitor         "DELL P991"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

The part of x's log that looks relevant
```

(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): No EDID information available.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 9 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 +hsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525 -hsync -vsync
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  600 601 605 742 -hsync
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  480 491 493 525 -hsync
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  400 457 459 524 -hsync -vsync
(==) fglrx(0): DPI set to (75, 75)

```[/QUOTE]


It appears that the driver can't find EDID information for your monitor.  Either this is because you hit the monitor bug in 8.16 or you have a really old monitor.  Try upgrading to 8.18 if you feel brave, or simple set the horizontal and vertical refresh values in your monitor section (man xorg.conf).  Make sure you use the actual values for your monitor though (check the manual or the manufacturer's homepage)!

---

### Post by mlomker on 2005-11-02
> my resolution and refresh rate won't go past 1024x768 and 60Hz.

You should [install 8.18.8.]("http://ubuntuforums.org/showthread.php?t=78466")  Certain newer LCD's don't 'talk' to the driver properly.

> 
If I decide high resolution is more important than 3d acceleration, can I safely go back to my old xorg.conf without making any other changes?


Yes.

---

### Post by sciurus on 2005-11-02
[QUOTE=Septor]It appears that the driver can't find EDID information for your monitor.  Either this is because you hit the monitor bug in 8.16 or you have a really old monitor.  Try upgrading to 8.18 if you feel brave, or simple set the horizontal and vertical refresh values in your monitor section (man xorg.conf).  Make sure you use the actual values for your monitor though (check the manual or the manufacturer's homepage)![/QUOTE]

Thanks, that was the problem! I thought I had specified those setting when I reconfigured X, and somehow I didn't notice that they weren't in the configuation file. Running fine at 1600x1200 now.

---

### Post by Cufishing on 2005-11-04
Wow! This was pretty strenous for a Newb. But, hey I was able to follow along and make it happen. Went FPS went through the roof.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

glxgears -iacknowledgethatthistoolisnotabenchmark
15804 frames in 5.0 seconds = 3160.638 FPS
15774 frames in 5.0 seconds = 3154.685 FPS

fgl_glxgears
2737 frames in 5.0 seconds = 547.400 FPS

Thank you.

---

### Post by mlomker on 2005-11-04
[QUOTE=Cufishing]Wow! This was pretty strenous for a Newb. But, hey I was able to follow along and make it happen. Went FPS went through the roof.[/QUOTE]

:cool:   Linux takes a little more determination but it is also rewarding to learn new things.

---

### Post by lukeweb on 2005-11-06
Thank you for this very simple but so far effective guide. It's gone better than the pre-Breezy days...
However, this has caused a number of  oddities that I would appreciate some help with. 
My overall system performance has become extremely erratic. There will be a massive delay when trying to perform a task - opening a terminal, executing a command, changing focus, etc. then a quick burst where lots will happen. I'm having a lot of programs sitting in the taskbar indicating they're loading ('Starting Terminal...'), but taking quite a long time. This wasn't happening before. In it's current state it's fairly unusable, but I certainly count this as progress.
AFAIK I'm  using the right driver now...
```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```

glxgears is all over the place. In another test, it was ranging from <100 to 3000+.
```
glxgears -iacknowledgethatthistoolisnotabenchmark
1302 frames in 6.3 seconds = 207.895 FPS
503 frames in 10.7 seconds = 46.975 FPS
514 frames in 7.2 seconds = 70.900 FPS
3548 frames in 8.0 seconds = 443.211 FPS
1014 frames in 9.1 seconds = 111.780 FPS
483 frames in 10.9 seconds = 44.492 FPS
```

I've noticed with both glxgears and fgl_glxgears there is a burst of regular fast FPS which lasts a very short time before bursts of fairly slow, static, fairly slow, static etc. I should also point out that actually running those programs takes about 15s when previously that was near-instant.
Any ideas what's up? I should be able to provide more information on request - I haven't edited the conf file that was output, but could this all be down to one wrong setting in the reconfigure wizard?
Really appreciating the help though - getting acceleration for this card sorted would certainly dilute my Windows use even more :)

**EDIT**
Ok, ok - someone slap me PLEASE.
I be very stupid, but I should probably preserve this gem of stupidity in case someone falls in the same trap as me (not likely)
I had only restarted X when I hit those problems, but restarting my whole PC made it go **SWIMMINGLY**

```

glxgears -iacknowledgethatthistoolisnotabenchmark
20776 frames in 5.0 seconds = 4155.054 FPS
22579 frames in 5.0 seconds = 4515.663 FPS
22586 frames in 5.0 seconds = 4517.159 FPS

```

```

fgl_glxgears
3048 frames in 5.0 seconds = 609.600 FPS
4210 frames in 5.0 seconds = 842.000 FPS
4211 frames in 5.0 seconds = 842.200 FPS

```

Beautiful, isn't it? :)
Thanks SOOOO much to the OP for making me a mega-happy bunny :D

---

### Post by mlomker on 2005-11-06
> Thanks SOOOO much to the OP for making me a mega-happy bunny :D

Around the IT department we call that *Dr. Reboot.*  He makes housecalls and fixes all kinds of weird problems.  :cool:

---

### Post by foxy123 on 2005-11-06
Does fglrx driver still not support composite and dri together? If I put
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection

```
option in my xorg.conf, dri disappear and fglrxinfo gives me:
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

---

### Post by mlomker on 2005-11-06
[QUOTE=foxy123]Does fglrx driver still not support composite and dri together?[/QUOTE]

I've read in other threads that it doesn't, but that'd be a question better asked on [ATI's forum.]("www.rage3d.com/board/forumdisplay.php?f=88")

---

### Post by Cufishing on 2005-11-06
Mlomker, I totally destroyed my Ubuntu attempting to install an chipset driver.
I rebuilt with Ubuntu, and could NOT get your guide to work the second time. I also decided to try Kbuntu, again could not get it to work. 
However, reading through this forum, I followed your link to the 8.18.8 driver. It worked perfectly for me, on this clean install of Kubuntu. I do have a newer LCD 19" panel, if that helps. And it locked right into 1280x1024 @60 'native'. 

drew@OSS:~$ fglrxinfo 
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc. 
OpenGL renderer string: RADEON 9600 XT Generic OpenGL version string: 1.3.5395 (X4.3.0-8.18.8)        

drew@OSS:~$ glxgears -iacknowledgethatthistoolisnotabenchmark 
16084 frames in 5.0 seconds = 3216.704 FPS
16038 frames in 5.0 seconds = 3207.506 FPS
20331 frames in 5.0 seconds = 4066.150 FPS

drew@OSS:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
2423 frames in 5.0 seconds = 484.600 FPS
2995 frames in 5.0 seconds = 599.000 FPS
2976 frames in 5.0 seconds = 595.200 FPS
3002 frames in 5.0 seconds = 600.400 FPS
Did not realize how much effect moving the mouse had on this test.
Again, Thank You. :D 

Now, could you build a how to on installing nvidia nforce 2 chipset update install? :razz:

---

### Post by mlomker on 2005-11-06
>  Now, could you build a how to on installing nvidia nforce 2 chipset update install? :razz:

I've thought about buying a desktop with an Nvidia card but I'm saving up for a Caribbean cruise this Winter.  :p

---

### Post by zachtib on 2005-11-06
thanks, boosted my glxgears score by almost 300

---

### Post by Cuppa-Chino on 2005-11-07
[QUOTE=Olav]
But **old** problems started again, causing the screen to freeze completely except for the mouse cursor.
[/QUOTE]

[QUOTE=mlomker]Yup.  fglrx does not support power management.  ATI states that in their FAQ's.  You'll have to choose.[/QUOTE]

Those two in any way related? I also have freezes. Furthermore I sometimes seem to have power management problems with P4 2.4GHz C 800MHz FSB, Asus P4P800 & Ati Radeon 9500 (sometimes @9700 - but that does not matter to freezes)

Any idea how to turn power management off to fix the ATI issue....

---

### Post by mlomker on 2005-11-07
> Any idea how to turn power management off to fix the ATI issue....

I was referring to hibernation on laptops.  I doubt that is the problem that you are having.  You can disable power management in your system's BIOS (usually F10 or DEL at boot-up).

---

### Post by Grimlock on 2005-11-08
I have installed the new drivers, but when I do fglrxinfo I get this?

richienation@richie:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

This is my xorg.conf


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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        256000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "L1715S"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Monitor         "L1715S"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"


Anyone got any ideas??

---

### Post by Septor on 2005-11-08
[QUOTE=Grimlock]I have installed the new drivers, but when I do fglrxinfo I get this?

richienation@richie:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

This is my xorg.conf


Section "Module"
        Load    "dbe"
EndSection

Anyone got any ideas??[/QUOTE]


You need to load modules "glx" and "dri" in your xorg.conf Modules section.

---

### Post by Grimlock on 2005-11-08
Thank you, that's sorted the problem.

---

### Post by sciurus on 2005-11-08
When I first installed Breezy, xorg.conf included the following:

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

When I reconfigured after installing fglrx, I wasn't sure what modules to include. I went with the ones listed below based on their inclusion in the ouput of an online tool for generating xorg configurations using fglrx:

Section "Module"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "type1"
EndSection

My problem is that xvimagesink no longer works. Could this be caused by my current module configuration? I can't find enough documentation online to tell what each module does, so I don't know what to add or remove. For now I changed my video output in the multimedia systems selector to XWindows(no xv), but it's unusably slow.

---

### Post by mlomker on 2005-11-08
Mine is this, but I'm not familiar with your application.  You might wish to start another thread for your question.

```

Section "Module"
        Load  "GLcore"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

```

---

### Post by fonkypij on 2005-11-12
Hi guys... Nice tutorial but... I still got a weird problem with this fglrx stuff. How come Planet Penguins runs ssloooooww (so slow that I just couldn't click on the quite button) although I got both fglrx and direct rendering? : 

fonkypij@delpij:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 1.3.5395 (X4.3.0-8.18.8)

fonkypij@delpij:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
[...]

Any idea? This is kinda special... I also tryed Atunnel GL screensaver from Xscreensaver... And it runs at about 0.8 fps! WoOow :???: Is there a fix for this?

---

### Post by mlomker on 2005-11-12
> Any idea? This is kinda special... I also tryed Atunnel GL screensaver from Xscreensaver... And it runs at about 0.8 fps! WoOow :???: Is there a fix for this?

**glxgears** is the only tool that I've used for benchmarking.  You should make a post to one of the gaming forums where more people will see it.

---

### Post by jsteidl on 2005-11-12
Hello There!

I was running my r300-card with mesa and had defntl NO fun with tuxracer .. erm sorry ... planet-penguin-racer (what sick name is that btw? ;))

anyway, it works now good with fglrx and i can play that sick-named game with good framerates.

only problem is: i tried to open totem after setting up fglrx and it gave me an error. so i went to the gnome-configuration-dialog for the multimedia system and picked another sink. okay. totem started. only problem is: movies that worked fine before are now out of sync and jerky... the problem with the non-starting totem was mentioned [here]("http://ubuntuforums.org/showpost.php?p=445582&postcount=109")
 but i didnt saw anybody reply to that problem... so is there a way to please totem with a working sink, because i am using ximagesink at the moment.. but that does not please me.

another problem with mplayer.. the program says that it was unable to find /dev/3dfx

any ideay?

thanks for the manual btw!! :)

---

### Post by BoneyOne on 2005-11-12
Ok, I'm at a loss here.

I'm running on an AMD64 system with the X800XL using PCI-E.

Obviously it is not detected normally so I'm using the vesa driver to startx.
I've loaded the 8.19.10_amd64 drivers and used the above process (page1).

After several attempts I finally got all the way through the process without any errors....or so I though. When I restarted X...no card/monitor found.

Had to go back to the vesa drivers...

Any ideas?

Oh, guess I should tell everyone I'm a linux newb as well.

---

### Post by fonkypij on 2005-11-12
Hello,
 
Try the latest drivers install @ [http://ubuntuforums.org/showthread.php?t=78466]("http://ubuntuforums.org/showthread.php?t=78466")

Then pay attention to the monitor configuration. Sometimes it is all about frequency.

Could you show us the bottom of your error's output?

---

### Post by andars on 2005-11-13
Thanks for the great guide, I just changed Driver from "ati" to "fglrx" and it works great.


anders@server-llama:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


anders@server-llama:~$ glxgears
53889 frames in 5.0 seconds = 10777.697 FPS
53822 frames in 5.0 seconds = 10764.339 FPS
51874 frames in 5.0 seconds = 10374.663 FPS

---

### Post by mlomker on 2005-11-13
> any errors....or so I though. When I restarted X...no card/monitor found.

Then your xorg.conf file is wrong.  Try the **dpkg-reconfigure** thing again.

---

### Post by mlomker on 2005-11-13
[QUOTE=jsteidl]another problem with mplayer.. the program says that it was unable to find /dev/3dfx
[/QUOTE]

I only use amaroK...I'm a KDE guy.  You should start another thread after searching to see if there is an existing one.  It's probably a problem with the driver and not the installation...I can't do anything about that.

---

### Post by BLTicklemonster on 2005-11-15
mloker: thanks. Now I have to reinstall Ubuntu again. yet again, I was stuck at the black screen of white letters de la morte. sudo nano dpkg-reconfigure did no good again.

I think I'll just get everybody in the house nvidia cards for christmas and take a pair of needle nose pliers to the ati cards.


No wait, didn't ati cards work in hoary? If so, I wonder where I can download it?

---

### Post by yarbys on 2005-11-16
Hi.  I have a Radeon X850XT PE, and I can't get the fglrx module to load.  lsmod doesn't list it.

dmesg:
```
$ dmesg | grep fglrx
[4295426.667000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4295426.669000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
**[4295426.669000] [fglrx:firegl_init] *ERROR* Device not found!**
```

lspci:
```
$ lspci | grep -i ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4b4c
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4b6c

```

---

### Post by BLTicklemonster on 2005-11-16
[QUOTE=BLTicklemonster]mloker: thanks. Now I have to reinstall Ubuntu again. yet again, I was stuck at the black screen of white letters de la morte. sudo nano dpkg-reconfigure did no good again.

I think I'll just get everybody in the house nvidia cards for christmas and take a pair of needle nose pliers to the ati cards.


No wait, didn't ati cards work in hoary? If so, I wonder where I can download it?[/QUOTE]


Finally got it working. I followed the how to (again) but this time from a fresh install and paid attention to detail and found out some things that weren't right. Once I corrected them (see my post in the discussion thread) it installed nicely. Finally!

Thanks in the above post wasn't meant like "thanks, you made me blah blah blah" it was meant like thanks for not screaming at me lol.

---

### Post by souled on 2005-11-16
[QUOTE=BLTicklemonster] Once I corrected them (see my post in the discussion thread) it installed nicely. Finally!
[/QUOTE]

Where is this discussion thread might I ask?

---

### Post by jecos on 2005-11-16
[QUOTE=BLTicklemonster]mloker: thanks. Now I have to reinstall Ubuntu again. yet again, I was stuck at the black screen of white letters de la morte. sudo nano dpkg-reconfigure did no good again.

I think I'll just get everybody in the house nvidia cards for christmas and take a pair of needle nose pliers to the ati cards.


No wait, didn't ati cards work in hoary? If so, I wonder where I can download it?[/QUOTE]
because you can't modify xorg.conf in a command line..your gonna reinstall *sigh*   You should never have to re-install unless you mess up your grub conf. then you can just boot a live cd and fix it.
"sudo nano -w /etc/X11/xorg.conf"  change driver to "ati" for safe mode then "fglrx" when you have fglrx installed.

---

### Post by BLTicklemonster on 2005-11-16
[QUOTE=jecos]because you can't modify xorg.conf in a command line..your gonna reinstall *sigh*   You should never have to re-install unless you mess up your grub conf. then you can just boot a live cd and fix it.
"sudo nano -w /etc/X11/xorg.conf"  change driver to "ati" for safe mode then "fglrx" when you have fglrx installed.[/QUOTE]
Easy for you to *yawn* say.

"have to" and "rather just do that than beat my head against the wall for 5 minutes longer looking for information on how to save 5 minutes"....

---

### Post by BLTicklemonster on 2005-11-16
[QUOTE=souled]Where is this discussion thread might I ask?[/QUOTE]

How to:
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)

Discussion:
[http://ubuntuforums.org/showthread.php?t=76116](http://ubuntuforums.org/showthread.php?t=76116)

---

### Post by jecos on 2005-11-16
[QUOTE=yarbys]Hi.  I have a Radeon X850XT PE, and I can't get the fglrx module to load.  lsmod doesn't list it.

dmesg:
```
$ dmesg | grep fglrx
[4295426.667000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4295426.669000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
**[4295426.669000] [fglrx:firegl_init] *ERROR* Device not found!**
```

lspci:
```
$ lspci | grep -i ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4b4c
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4b6c

```[/QUOTE]

check out rage3d.com linux forums theres a fix you add a line to your xorg.conf

---

### Post by jecos on 2005-11-16
[QUOTE=BLTicklemonster]Easy for you to *yawn* say.

"have to" and "rather just do that than beat my head against the wall for 5 minutes longer looking for information on how to save 5 minutes"....[/QUOTE]

That time taken to properly learn a simple command line will save you in the long run...unless you want to never learn anything. Linux is about learning.  Its free but sometimes at the cost of usability(works but isn't point and click)

---

### Post by BLTicklemonster on 2005-11-16
[QUOTE=jecos]That time taken to properly learn a simple command line will save you in the long run...unless you want to never learn anything. Linux is about learning.  Its free but sometimes at the cost of usability(works but isn't point and click)[/QUOTE]


I'm feelling very enlightened now, thank you. So is this what all newcomers to linux are to be told? If it doesn't work, learn how to make it work? Then why did arnieboy make Automatix? Why is there ubuntu? But yes, in the meantime, commands are to be learned, and I have a gazillion of them in my pm box back at the legion so I can reference them whenever I need to.

I just tried this again here at work with a machine we had sitting around, and it totally failed. Guess what? I'm going to reinstall again!!! And do you want to know why? Because of the same reason I did it last night; I don't have time to sit and nit pick. While UB is installing, I can be doing other things, but if I hunt and peck and search through tons of cryptic gobbledygook, I will totally waste time. Same here, I can sit here and spam a- er post in the forum and look for other stuff I'm working on besides UB while the machine is back there getting itself back into it's pristine state. I spent 9 HOURS last night getting the other machine working. And don't go off on me about learning, look at my post, and tell me I would have figured any of that out if I weren't learning. 

Thank you.

---

### Post by jc87 on 2005-11-16
Noob question :

```
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver
```

How do i write this code exactly:???: .

For example i tryed :

sudo dpkg-reconfigure xserver-xorg #fglrx-8.16.20

sudo dpkg-reconfigure xserver-xorg fglrx-8.16.20 

is any of theese correct? if not what is the correct one ?  

And still no 3d acelaration , before i check the xorg.conf file i would like to see if the command im doing is right:eek:

---

### Post by BLTicklemonster on 2005-11-16
Just type

sudo dpkg-reconfigure xserver-xorg

and follow the instructions, don't let it choose the graphic card, choose it yourself.

---

### Post by mlomker on 2005-11-16
[QUOTE=jc87]And still no 3d acelaration , before i check the xorg.conf file i would like to see if the command im doing is right:eek:[/QUOTE]

The # and everything after it is just a comment.  If you typed it in that way then the system would ignore the comment and execute the command normally.  All of the commands are entered at a terminal prompt.

---

### Post by souled on 2005-11-17
WOW, I just tried this Howto again and it worked... I've tried it before and it didn't work. This time, I did sudo apt-get clean before I download the files... Don't know if that really made a difference though. About that color problem I had before... I think it was fixed when I enabled this ```
Option		"UseFBDev" "true"
``` Can't remember what option it was in the dpkg reconfigure thing but that's the entry in my xorg.conf. Yay, I'm all back to normal now. Thanks for all the work you do mlomker!

---

### Post by Robocoastie on 2005-11-18
System: Dell Dimension 5100
CPU: Pentium4 HT EM64T 2.8GHz
Ram: 1.6 GB Video Card: ATI Radeon X300 with 128MB memory
Ubuntu 5.10 64bit

Problem: after install X won't start
References to solve: this thread, ATI instructions and ATI driver:
ati-driver-installer-8.19.10-x86_64.run and Ubuntu FAQ 4.3 "How do I Install 3D ATI video card driver?"

I've walked through all these steps with limited success. The instructions at Ubuntur FAQ 4.3 resulted in the same x server crash.

A combination of the original post and ATI's instructions however gets me into Gnome at least but fglrxinfo reveals the same mesa driver that others in this thread keep getting:

> rob@dell5100:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
rob@dell5100:~$

also the kernel is seeing the card:

> rob@dell5100:~$ lspci | grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
rob@dell5100:~$

I installed the .deb's that sudo sh ./ati-* creates:
> fglrx-control_8.19.10-1_amd64.deb, fglrx-kernel-source_8.19.10-1_amd64.deb
fglrx-sources_8.19.10-1_amd64.deb
xorg-driver-fglrx_8.19.10-1_amd64.deb
xorg-driver-fglrx-dev_8.19.10-1_amd64.deb

(of course the fglrx-control one has to be last to be installed)

I then ran fglrxconfig and accepted all the defaults ---could the problem be with the options such as DRI ?? I know when an nvidia card is installed that needs to be commented out but what about with this?

grrr I want to include the xorg.0.log file and my xorg.conf but I keep getting "too big" errors when I try to attach.

****edit/Update***
ok it gets weirder... I tried the "Easy multimedia installer" I learned about from: [http://ubuntuforums.org/showthread.php?t=84742](http://ubuntuforums.org/showthread.php?t=84742)
and I noticed that DRI wasn't selected, - as instructed I left it alone and used all defaults. A reboot resulted in x server crash.
I then figured the problem was the Load "init10" line so I commented that out and rebooted again. That fixed the x crash and low and behold my desktop was actually at 1280x1024! But relax... still stuck at mesa3d see:

> rob@dell5100:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

rob@dell5100:~$


---

### Post by mlomker on 2005-11-18
[QUOTE=Robocoastie]System: Dell Dimension 5100
[/quote]

Did you replace the libdri.a file, as in my how-to?  If not, then none of the drivers are going to work on 64-bit.

It's more useful to look at /var/log/kern.log and Xorg.0.log than the others.

---

### Post by Robocoastie on 2005-11-18
aye I replaced the libdri.a

all my steps were done from command line, I had jotted down the web addy from your link and used wget.

I was just reading the conversation thread regarding this and some other people mentioned needing to install headers (why aren't these installed in the first place?) and one person said on the steps during the fglrxconfig process that they said Y to "do you want to initialize xfree86-dga (i had used default n) and said yes to "do you want to use the external AGP GART module (i had used default n).

Since my rig is PCIExpress video though wasn't the "n" for AGP GART the correct answer?

thanks,
Rob

edit/add: oh I wanted to attach the log but I keep getting the message that its too big to attach. I'm not sure what parts can be excluded, I'll post it to my web site in a minute and just link to it...

---

### Post by BLTicklemonster on 2005-11-18
Question, herr mmloker, oh wise one:

if I go changing video cards, xserver will fail, and I just reconfigure, right? then install the correct drivers?

---

### Post by Robocoastie on 2005-11-18
ok I'm now working from a clean install. Same thing happens with x server crash so I'm working from command line strictly here.

when i attempt to remove old fglrx driver it fails saying there is no fglrx installed. (hence the x server crash after install I imagine). So I move right along and am able to remove linux-restricted-modules-$(uname -r). performing sudo dpkg-reconfigure xserver-xorg and selecting ATI I didn't bother with because I still got a x server crash the last time so skipped that.


I then apt-get install fakeroot debhelper build-essential make gcc-3.4 libstdc++5
which seemed to work, but just as last time I got an error message when I tried to apt-get install build-essential saying "Package module-assistant is not available But is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source." (same message later when I tried to sudo module-assistant prepare) Also I did apt-get install linux-headers-2.6.12-9 and apt-get install linux-headers-2.6.12-9-amd64-generic.

I then followed the steps you gave for libdri.a and ran fglrxconfig all defaults but said y to initialize xfree86-dga and external AGP GART module (again, I don't know if this is right or what to select for these parts really).

Rebooted - which got me into gnome but at 1024x768 and fglrxinfo said mesa graphics again (no surprise).

Been at this so many times now my brains fried heh.

Oh, while I'm at it which kernel header files for sure should I be d/loading? Does the *amd64-generic one have smp compiled in?

thanks,

---

### Post by BLTicklemonster on 2005-11-18
I caved in and put my son's windows hd back in. I'll get him an nvidia card for christmas, this isn't worth keeping him from having fun on his machine. I'm sure it will all be fixed later on.


(again I ask, wasn't hoary better with ati than breezy?)

---

### Post by mlomker on 2005-11-19
[QUOTE=Robocoastie]other people mentioned needing to install headers (why aren't these installed in the first 
[/quote]

Not for Breezy's 8.16.20.  You need them to compile the newer ones.  moduel-assistant in my how-to for the latest driver will do that for you.

> Since my rig is PCIExpress video though wasn't the "n" for AGP GART the correct answer?

It doesn't matter what you select for that.  Ubuntu has the built-in gart and the driver will use it.  I assume it doesn't matter at all with PCI-E, as you said.  I have an older card, so I'm speculating there.

---

### Post by mlomker on 2005-11-19
[QUOTE=BLTicklemonster]if I go changing video cards, xserver will fail, and I just reconfigure, right? then install the correct drivers?[/QUOTE]

Sure.  You could make the change before you power down to swap the card.  I'd probably just pick 'vesa' because it works with almost all cards (it isn't 3D but gets you a desktop).  You can switch to another driver after you install the other card.

---

### Post by mlomker on 2005-11-19
[QUOTE=Robocoastie]Oh, while I'm at it which kernel header files for sure should I be d/loading? Does the *amd64-generic one have smp compiled in?
[/QUOTE]

I'm not sure why we're discussing the latest drivers in the thread for Breezy's included drivers.  You need to apt-get install module-assistant.  That will download the proper headers when you do the prepare step.

This is the [how-to]("http://ubuntuforums.org/showthread.php?t=78466") and the other discussion thread is linked at the top of it.

---

### Post by Robocoastie on 2005-11-19
Hi mloker,

> 
I'm not sure why we're discussing the latest drivers in the thread for Breezy's included drivers. You need to apt-get install module-assistant. That will download the proper headers when you do the prepare step.

the reason was that I couldn't I got an error when I tried to apt-get module-assistant so it wasn't included for me for some reason. So I thought I was going to have to build it the mepis way which involves mucking with the linux kernel.

At any rate I have this partially working now. Here's what I did different from previously described:

1. clean installed 32bit version instead of 64
2. switched to 686-smp kernel and d/loaded headers for that
3. again I was able to get to the desktop at least but stuck with mesa drivers still but that let me enable the universe repositories and then was able to apt-get module-assistant.
4. I was then able to follow your kernel driver steps with success. ran aticonfig --initial
5. ran fglrxconfig BUT I'm not sure what to choose for: 
Do you want to initialize xfree86-dga (y/n)? [n]
Do you want to use the external AGP GART module (y/n)? [n]
(my card is PCIExpress further confusing me on this)
Do you want to enable "AGP Locked User Pages" (y/n)? [y]
Which storage method do you want to use? [0]

In any case I chose the defaults for these.

glxgears however is running turtle slow though which sets an alarm off in my head. Painfully slow one can count the revolutions by hand its that slow. But I am running at 1280x1024 at least, so it all seems to be working other than that. Next I'll try it with 64bit on my other partition.


enable AGP GART?,

---

### Post by mlomker on 2005-11-19
The defaults should work fine.  Are you using **glxgears -printfps**?  What is the result?  **fglrxinfo** will also tell you if it is working.  If it's not then you'll need to look at /var/log/kern.log and Xorg.0.log for errors.

---

### Post by BLTicklemonster on 2005-11-19
[QUOTE=mlomker]Sure.  You could make the change before you power down to swap the card.  I'd probably just pick 'vesa' because it works with almost all cards (it isn't 3D but gets you a desktop).  You can switch to another driver after you install the other card.[/QUOTE]

Great, because I'm going to try the ati on my machine, it's a better motherboard, so it may handle the card better, and put the nvidia on his machine. Thanks tons, dude.

---

### Post by Robocoastie on 2005-11-19
[QUOTE=mlomker]The defaults should work fine.  Are you using **glxgears -printfps**?  What is the result?  **fglrxinfo** will also tell you if it is working.  If it's not then you'll need to look at /var/log/kern.log and Xorg.0.log for errors.[/QUOTE]

well I'll be a bat in a bellry! talk about appearances can be deceiving! I didn't know about the -printfps I'd always just killed it after a few seconds and then saw what it printed. Here's my -printfps result (minus many lines that averaged the same)

```
rob@dell5100:~$ glxgears -printfps
6468 frames in 5.0 seconds = 1292.478 FPS
7052 frames in 5.0 seconds = 1410.223 FPS
7043 frames in 5.0 seconds = 1408.574 FPS
7043 frames in 5.0 seconds = 1408.549 FPS
7044 frames in 5.0 seconds = 1408.726 FPS
7043 frames in 5.0 seconds = 1408.533 FPS
7044 frames in 5.0 seconds = 1408.651 FPS
7043 frames in 5.0 seconds = 1408.512 FPS
7044 frames in 5.0 seconds = 1408.615 FPS
7043 frames in 5.0 seconds = 1408.588 FPS
7043 frames in 5.0 seconds = 1408.458 FPS
7043 frames in 5.0 seconds = 1408.495 FPS

```

And my fglrxinfo:

```

rob@dell5100:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 1.3.5461 (X4.3.0-8.19.10)

rob@dell5100:~$

```

So it appears its all working afterall! Hurray! 3 cheers for mlomker! hip hip hurray!
This also proves that walking away and sleeping on a problem helps - it was only after I did that finally (2am'ish) that I saw on linuxquestions that others had the same problem finding module-assistant which led me to deduce (sp?) that the other repositories needed to be enabled. And walla! it became apt-get'able

---

### Post by mlomker on 2005-11-20
[QUOTE=Robocoastie] that the other repositories needed to be enabled. And walla! it became apt-get'able[/QUOTE]

That's a good point.  I could add something about that to the how-to.

---

### Post by windowsguy on 2005-11-24
I get this error when I try to remove xorg-driver-fglrx.

I have everything working and my card was detected until I upgraded my kernel to k7 version. Now I cant even use the fglrxinfo command.

Thanks for the help,
Robert


windowsguy@windowsguy:~$ sudo apt-get remove xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 19.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125506 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
windowsguy@windowsguy:~$

---

### Post by mlomker on 2005-11-24
[QUOTE=windowsguy]
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
[/QUOTE]

AFAIK Breezy's driver doesn't have a diversion.  Did you have 8.16.20 or a newer version installed?  You could always **sudo apt-get --force-yes remove** but that's the sledgehammer approach.

---

### Post by masingerz on 2005-12-05
I have a radeon x300se and when I tried to use fglrx I found myself with no gui, (luckyly fglrx made a backup), and an error message that gdm was not configured appropriatly, so i had to "sudo killall gdm" and "sudo mv xorg.conf.bak xorg.conf" and then "sudo gdm" and it worked: I have a gui now, I still want to have good display, but i do not want to suffer so much.

(the actual backup was called xorg.conf.2005101021213, but i put xorg.conf.bak for illustration purpose)

---

### Post by Hellaxe on 2005-12-05
I Couldn't find the answer to my problem.
I've followed the how-to but x server doesn't start.
I attach the xorg.0.log to see if anyone can tell me what am i doing wrong.
My video card is a Mobility M7 LW from the IBM Thinkpad R51. The laptop says it's a 9000.

---

### Post by mlomker on 2005-12-05
[QUOTE=Hellaxe]I attach the xorg.0.log to see if anyone can tell me what am i doing wrong.
My video card is a Mobility M7 LW from the IBM Thinkpad R51. The laptop says it's a 9000.[/QUOTE]

I didn't see anything in there but that wasn't the complete log.  You'll also want to look in /var/log/kern.log for messages relating to the fglrx module loading.

Are any error messags printed to the screen when it fails?  You should be able to Ctrl-Alt-F2 and run **startx** from the prompt.  At least when it crashes you should see some errors on the screen.

---

### Post by Hellaxe on 2005-12-05
This is the second part of the log. Sorry but i'm still a noob and can't undertand the ati stuff.The other log íll see it tomorrow. bed time now. thanks

```
II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)".
(--) Chipset ATI Radeon Mobility M7 LW (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xc0214000 - 0xc0214fff (0x1000) MX[B]
	[6] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[7] -1	0	0xc0220000 - 0xc023ffff (0x20000) MX[B]
	[8] -1	0	0xc0210000 - 0xc0213fff (0x4000) MX[B]
	[9] -1	0	0xc0215000 - 0xc02157ff (0x800) MX[B]
	[10] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[11] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[12] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[13] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[14] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[15] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[21] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[23] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[24] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[25] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[26] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[27] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[28] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[29] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xc0214000 - 0xc0214fff (0x1000) MX[B]
	[6] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[7] -1	0	0xc0220000 - 0xc023ffff (0x20000) MX[B]
	[8] -1	0	0xc0210000 - 0xc0213fff (0x4000) MX[B]
	[9] -1	0	0xc0215000 - 0xc02157ff (0x800) MX[B]
	[10] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[11] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[12] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[13] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[14] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[15] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[23] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[24] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[25] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[27] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[28] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xc0100000
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility M7 LW (AGP)" (ChipID = 0x4c57)
(--) RADEON(0): Linear framebuffer at 0xe0000000
(--) RADEON(0): VideoRAM: 32768 kByte (64 bit DDR SDRAM)
(II) RADEON(0): AGP card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/X11R6/lib/modules/libi2c.a
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- LVDS
 Connector -- DVI-D
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=12000 max=35000; xclk=18300
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Panel ID string: Samsung LTN150P1-L02    
(II) RADEON(0): Panel Size from BIOS: 1400x1050
(II) RADEON(0): BIOS provided dividers will be used.
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): Valid mode using on-chip RMX: 1400x1050
(II) RADEON(0): Total number of valid FP mode(s) found: 1
(--) RADEON(0): Virtual size is 1400x1050 (pitch 1408)
(**) RADEON(0): *Mode "1400x1050": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1400x1050"  108.00  1400 34208 34320 1688  1050 1052 1055 1063
(**) RADEON(0):  Default mode "640x350": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "640x350"  108.00  640 34208 34320 1688  350 1052 1055 1063
(**) RADEON(0):  Default mode "640x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "640x400"  108.00  640 34208 34320 1688  400 1052 1055 1063
(**) RADEON(0):  Default mode "720x400": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "720x400"  108.00  720 34208 34320 1688  400 1052 1055 1063
(**) RADEON(0):  Default mode "640x480": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "640x480"  108.00  640 34208 34320 1688  480 1052 1055 1063
(**) RADEON(0):  Default mode "800x600": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "800x600"  108.00  800 34208 34320 1688  600 1052 1055 1063
(**) RADEON(0):  Default mode "1024x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1024x768"  108.00  1024 34208 34320 1688  768 1052 1055 1063
(**) RADEON(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1152x864"  108.00  1152 34208 34320 1688  864 1052 1055 1063
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 34208 34320 1688  960 1052 1055 1063
(**) RADEON(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 34208 34320 1688  1024 1052 1055 1063
(**) RADEON(0):  Default mode "832x624": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "832x624"  108.00  832 34208 34320 1688  624 1052 1055 1063
(**) RADEON(0):  Default mode "1280x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1280x768"  108.00  1280 34208 34320 1688  768 1052 1055 1063
(**) RADEON(0):  Default mode "1280x800": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1280x800"  108.00  1280 34208 34320 1688  800 1052 1055 1063
(**) RADEON(0):  Default mode "1152x768": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.2 Hz
(II) RADEON(0): Modeline "1152x768"  108.00  1152 34208 34320 1688  768 1052 1055 1063
(++) RADEON(0): DPI set to (100, 100)
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
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): AGP Fast Write disabled by default
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xc0100000 - 0xc010ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xc0214000 - 0xc0214fff (0x1000) MX[B]
	[8] -1	0	0xc0200000 - 0xc020ffff (0x10000) MX[B]
	[9] -1	0	0xc0220000 - 0xc023ffff (0x20000) MX[B]
	[10] -1	0	0xc0210000 - 0xc0213fff (0x4000) MX[B]
	[11] -1	0	0xc0215000 - 0xc02157ff (0x800) MX[B]
	[12] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[13] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[14] -1	0	0x20000000 - 0x200003ff (0x400) MX[B]
	[15] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[16] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[17] -1	0	0xc0100000 - 0xc010ffff (0x10000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[26] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[27] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[28] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[29] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[30] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[31] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[35] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xe0000000,0x2000000)
(II) RADEON(0): Dynamic Clock Scaling Disabled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xe0d63000
(II) RADEON(0): [drm] mapped SAREA 0xe0d63000 to 0xb5c71000
(II) RADEON(0): [drm] framebuffer handle = 0xe0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f000201 [AGP 0x8086/0x3340; Card 0x1002/0x4c57]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xd0000000
(II) RADEON(0): [agp] Ring mapped at 0xb5b70000
(II) RADEON(0): [agp] ring read ptr handle = 0xd0101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb5b6f000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xd0102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xb596f000
(II) RADEON(0): [agp] GART texture map handle = 0xd0302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xb548f000
(II) RADEON(0): [drm] register handle = 0xc0100000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1408,5957)
(II) RADEON(0): Reserved area from (0,1050) to (1408,1052)
(II) RADEON(0): Largest offscreen area available: 1408 x 4905
(II) RADEON(0): Will use back buffer at offset 0xb70000
(II) RADEON(0): Will use depth buffer at offset 0x1114000
(II) RADEON(0): Will use 9472 kb for textures at offset 0x16c0000
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		15 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): Backing store disabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1052)
(II) RADEON(0): Largest offscreen area available: 1408 x 4902
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(II) RADEON(0): X context handle = 0x00000001
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 11
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(==) RandR enabled
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "pt"
(**) Generic Keyboard: XkbLayout: "pt"
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
(II) Synaptics touchpad driver version 0.13.6
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad synaptics touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad synaptics touchpad found
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
```

---

### Post by joshuapurcell on 2005-12-05
I've looked through the log file, and everything looks great except for these things:

The EDID portion of **/var/log/Xorg.0.log**, where it eventually says "desktop setup not supported":```
(II) fglrx(0): Connected Display1: DFP on internal TMDS
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SAM  Model: bb  Serial#: 1312960825
(II) fglrx(0): Year: 2003  Week: 38
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.60
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.635 redY: 0.345   greenX: 0.295 greenY: 0.600
(II) fglrx(0): blueX: 0.140 blueY: 0.080   whiteX: 0.310 whiteY: 0.330
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) fglrx(0): Monitor name: SyncMaster
(II) fglrx(0): Serial No: HCHW906010
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - DFP on internal TMDS
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled
(==) fglrx(0): TMDS coherent mode is enabled
(II) fglrx(0): Total of 21 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
```

Also this warning in the same file:```
(WW) Ignoring request to load module GLcore
```

Here are the FPS printouts from glxgears and fgl_glxgears. From these numbers it seems everything is fine, but when I run these commands my processor goes to 97-99% useage every time:```
jeremy@breezy:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
26450 frames in 5.0 seconds = 5289.871 FPS
jeremy@breezy:~$ fgl_glxgears
5163 frames in 5.0 seconds = 1032.600 FPS
```

Here's some more info from the kernel log:```
jeremy@breezy:~$ more /var/log/kern.log | grep fglrx
Dec  5 22:24:20 localhost kernel: [ 2092.420660] [fglrx] Internal AGP support requested, but kernel AGP support active.
Dec  5 22:24:20 localhost kernel: [ 2092.420667] [fglrx] Have to use kernel AGP support to avoid conflicts.
Dec  5 22:24:20 localhost kernel: [ 2092.420673] [fglrx] AGP detected, AgpState   = 0x1f000a1a (hardware caps of chipset)
Dec  5 22:24:20 localhost kernel: [ 2092.421288] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
Dec  5 22:24:21 localhost kernel: [ 2092.500979] [fglrx] free  AGP = 54800384
Dec  5 22:24:21 localhost kernel: [ 2092.500984] [fglrx] max   AGP = 54800384
Dec  5 22:24:21 localhost kernel: [ 2092.500987] [fglrx] free  LFB = 116387840
Dec  5 22:24:21 localhost kernel: [ 2092.500989] [fglrx] max   LFB = 116387840
Dec  5 22:24:21 localhost kernel: [ 2092.500992] [fglrx] free  Inv = 134217728
Dec  5 22:24:21 localhost kernel: [ 2092.500994] [fglrx] max   Inv = 134217728
Dec  5 22:24:21 localhost kernel: [ 2092.500996] [fglrx] total Inv = 134217728
Dec  5 22:24:21 localhost kernel: [ 2092.500998] [fglrx] total TIM = 0
Dec  5 22:24:21 localhost kernel: [ 2092.501000] [fglrx] total FB  = 0
Dec  5 22:24:21 localhost kernel: [ 2092.501002] [fglrx] total AGP = 16384
```

I have an Athlon64 3400+, 1GB RAM, and an ASUS Radeon 9800 XT. Could my processor alone give me these numbers? Is there anything I need to do about the unsupported desktop setup error? Why do I get the "Ingoring request to load module GLcore" warning?

Thanks for the helpful guide.

EDIT: While I'm posting, I thought I'd ask about this (since the kernel log above reminded me of it). Would adding this option to the device section of my xorg.conf file help?```
 Option "UseInternalAGPGART" "no"
```
The above line isn't there now, but I'm not sure if it is useful to me or not... guess I'll try and find out.

---

### Post by mlomker on 2005-12-06
[QUOTE=joshuapurcell]Could my processor alone give me these numbers?[/quote]

No, MESA tops out at 500 fps on my box.  If you're getting over 1k then the drivers are doing their thing.

> Why do I get the "Ingoring request to load module GLcore" warning?

Some of the error messages in those logs are normal.

> The above line isn't there now, but I'm not sure if it is useful to me or not... guess I'll try and find out.

It won't do anything on Ubuntu due to the way that the kernel is built.

The rest of your questions you'll have to ask on the Rage3D board.  I'm not a programmer, I just try to keep the installation how-to's up to date.

---

### Post by Hellaxe on 2005-12-07
Hello people. A little help is welcome :)

---

### Post by DarthFrog on 2005-12-07
I'm Canadian and bought an ATI Radeon 9800 Pro because ATI is Canadian.  Bad mistake!  I *cannot* get it to do direct rendering in Breezy Kubuntu.

 I'm running kernel 2.6.12-10-k7 (Athlon Mobile 2800+ CPU) and an Acer AL1914 LCD monitor.

In /var/log/Xorg.0.log, I get:
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP

and from dmesg, I see:
[4294724.498000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294724.504000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294724.504000] [fglrx] module loaded - fglrx 8.19.10 [Nov  9 2005] on minor 0
[4294724.539000] [fglrx] ACPI power management is initialized.
[4294771.877000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294771.877000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294771.877000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294771.877000] [fglrx] AGP detected, AgpState   = 0x1f004e0b (hardware caps of chipset)
[4294771.878000] [fglrx:firegl_unlock] *ERROR* Process 7373 using kernel context 0
[4322061.643000] [fglrx:firegl_unlock] *ERROR* Process 16011 using kernel context 0
[4400624.678000] [fglrx:firegl_unlock] *ERROR* Process 11669 using kernel context 0
[4415135.119000] [fglrx:firegl_unlock] *ERROR* Process 17447 using kernel context 0

 Kernel modules fglrx, agpgart and sis_agp are loaded.

  According to ATI, the error "xf86_ENODEV" is not an issue with their fglrx driver, rather a problem with agpgart.  

  I'm a competent enough sysadmin but I'm damned if I can figure out what to do to get 3D hardware acceleration going with this ATI card.  I've read the entire 19 pages :) of this thread with no joy.

  I'm definitely missing something, I think.  Can anyone offer guidance?

--
Cheers,
Rob

---

### Post by mlomker on 2005-12-07
[QUOTE=DarthFrog]According to ATI, the error "xf86_ENODEV" is not an issue with their fglrx driver, rather a problem with agpgart.[/QUOTE]

That's what I found in my searches as well...the fglrx driver uses a motherboard-specific AGP driver as its interface.  Basically Ubuntu isn't playing quite right with your motherboard.  Other than reading through the posts regarding that error on the Rage3D board, I'd also search for your motherboard model here and on there to see if there are known issues.

My laptop uses the sis_agp module:

```

mlomker@mlomkernote:/$ lsmod | grep agp
sis_agp                 8644  0
amd64_agp              12296  1
agpgart                34888  3 fglrx,sis_agp,amd64_agp

```

---

### Post by mlomker on 2005-12-07
[QUOTE=Hellaxe]Hello people. A little help is welcome :)[/QUOTE]

You posted a log that is using the Radeon driver, which doesn't help us.  You'll need to get the log from the failed bootup.  Did you see post 182?  Once you've gone over to another prompt you'll need to either examine the log file or copy it somewhere so you can post it later.

If you haven't figured out the command-line then I'd recommend you just put the video-driver thing on hold for a day or two and learn your way around linux first.  Here's a [command-line tutorial]("http://linuxcommand.org/learning_the_shell.php") that I like.

---

### Post by croken254 on 2005-12-07
here is a sample of the results, Awesome job guy's thanks...


10678 frames in 5.0 seconds = 2135.503 FPS
9546 frames in 5.0 seconds = 1909.029 FPS
10677 frames in 5.0 seconds = 2135.251 FPS
10600 frames in 5.0 seconds = 2119.991 FPS
kendall@ubuntu1:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

---

### Post by tedddee on 2005-12-11
I'm having the same problems as HellAxe, laptop with the Mobility M7

[http://s87055070.onlinehome.us/ted/Xorg.0.log](http://s87055070.onlinehome.us/ted/Xorg.0.log)

---

### Post by soc on 2005-12-12
it seems that i already tried thousands of different methods to install the newest fglrx, but since 8.20.8 the problem appeared that the screen turns black immediately after i click on log off/shutdown/reboot/...
i searched in different forums which proposed everytime different things.
i would be glad if somebody could answer me these questions:
1. in xorg.conf:
UseInternalAGPGART 
YES or NO???
2. when configuring my kernel (2.6.15_rc4_ck1)
Device Drivers -> Charakter Devices -> /dev/agpgart (AGP Support)
i got told that i should set it to NO, but i can only build it into the kernel or as a module! what should i do?
3. Device Drivers -> Charakter Devices -> Direct Rendering Manager
should i choose MODULE or NO???
i would prefer a small and fast kernel with working 3d acceleration, so what should i do??
on linux-militia it is said
*"In order to use the fglrx internal AGP support, you have to make sure that the kernel agpgart support is not active, i.e. it is not compiled into the kernel and the kernel modules are not loaded. If the fglrx kernel module detects that the kernel agpgart support is active, it will automatically use that even if its internal AGP support is requested in order to avoid conflicts that can cause problems under some circumstances."*
so what?? is it important? which agp support should it use by the way? some say UseInternalAGPGART yes, other no!!
thanks in advance for all your help!
soc

---

### Post by mlomker on 2005-12-12
[QUOTE=soc]it seems that i already tried thousands of different methods to install [/QUOTE]

You should really be talking to the guys on [Rage3D]("www.rage3d.com/board/forumdisplay.php?f=88") if you are going to build a custom kernel.

It doesn't matter what you pick for the gart config on a Ubuntu kernel because it's built in and will use it regardless of setting.

---

### Post by mlomker on 2005-12-12
[QUOTE=tedddee]I'm having the same problems as HellAxe, laptop with the Mobility M7
[/QUOTE]

Well, your Xorg.0.log file contains this line:

```

(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] rev 0, Mem @ 0xf0000000/27, 0xef000000/16, I/O @ 0xd800/8, BIOS @ 0xeffe0000/17

```

The fglrx driver supports 8500+.  Your laptop may be fairly new but IBM is famous for being conservative and therefore they use ancient video cards.

---

### Post by tedddee on 2005-12-12
ok, thanks for the reply :)

are there any other drivers i could use? or just stick with the default ati/mesa thingy?

---

### Post by mlomker on 2005-12-12
[QUOTE=tedddee]are there any other drivers i could use? or just stick with the default ati/mesa thingy?[/QUOTE]

I think that's the best that you can do.  You're going to be very unhappy if you are a game player but you really don't need a fancy video card for everyday things (email, surfing, etc).

---

### Post by tedddee on 2005-12-12
was thinking of toying with quake2 on the laptop, but dont really need to i guess :)

leave that for the desktop

---

### Post by Toontwnca on 2005-12-12
[QUOTE=mlomker]I've seen a few other threads with similar results.  I gather that it is the 9200 and older that most often see the problem.[/QUOTE]

Right. I have 9000 on a Toshiba notebook.
Locks up tighter than a drum. ](*,)

---

### Post by mlomker on 2005-12-12
[QUOTE=Toontwnca]Right. I have 9000 on a Toshiba notebook.
Locks up tighter than a drum.[/QUOTE]

Lock-ups are usually a hardware problem (Ctrl-Alt-F2 doesn't work).  I think most cards from that era use shared memory and that could be a part of it.

Have you tried the [latest driver]("http://ubuntuforums.org/showthread.php?t=78466") yet?  If that doesn't work then you could file a bug report.

---

### Post by Toontwnca on 2005-12-12
[QUOTE=mlomker]Lock-ups are usually a hardware problem (Ctrl-Alt-F2 doesn't work).  I think most cards from that era use shared memory and that could be a part of it.

Have you tried the [latest driver]("http://ubuntuforums.org/showthread.php?t=78466") yet?  If that doesn't work then you could file a bug report.[/QUOTE]

Yes I tried the new drivers as per your howto.
The install went smoothly; but no difference
on restart.

I did notice something odd in /etc/X11/xorg.conf:
that being two sections for drivers, one said 'ati'
the other said 'fglrx'.

On a side note; it is shared memory.
Computer only a year and a half old.
Similar to your IBM reference; new
computer, old card. 
Will know better next time.:rolleyes:

---

### Post by flabdablet on 2005-12-13
[This post on the Rage3D forum]("http://www.rage3d.com/board/showpost.php?p=1333981360&postcount=18") nailed it for me.

If you've worked through the OP Howto, you still have the mesa driver active, and the result of

cat /proc/mtrr

looks like

reg00: base=0x00000000 ( 0MB), size=984064MB: write-back, count=1

with a similarly outrageously large size= value, it will probably nail it for you too (no size under /proc/mtrr should ever be larger than the amount of mainboard RAM you have).

mlomker, perhaps you could link to this in your troubleshooting section.

Razzafrazzin crabblfranchin garbage BIOS.  I'm off to look for a flash upgrade...

---

### Post by flabdablet on 2005-12-13
For those who might be curious about what this particular failure looks like, here is the relevant part of my /var/log/Xorg.0.log:

```

(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8c5c000
(II) fglrx(0): [drm] mapped SAREA 0xf8c5c000 to 0xb7b5d000
(II) fglrx(0): [drm] framebuffer handle = 0xd0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.16.20
(II) fglrx(0):     Date: Aug 16 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xf9000000
[B](EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
[/B](II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8c5c000 at 0xb7b5d000
[B](WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
[/B](II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
[B](WW) fglrx(0): Failed to set up write-combining range (0xd0000000,0x8000000)
[/B](II) fglrx(0): FBMM initialized for area (0,0)-(1152,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1152,864) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(II) fglrx(0): Using hardware cursor (scanline 864)
(II) fglrx(0): Largest offscreen area available: 1152 x 7323
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

```


and my dmesg:

```

[4294731.756000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294731.761000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294731.761000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294731.761000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[B][4294731.776000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
[4294731.776000] [fglrx:firegl_addmap] *ERROR* mtrr allocation failed (-22)
[/B][4294731.777000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294731.777000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294731.777000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294731.777000] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[B][4294731.777000] mtrr: type mismatch for f0000000,8000000 old: write-back new: write-combining
[4294731.777000] [fglrx:firegl_unlock] *ERROR* Process 8342 using kernel context 0
[4294731.844000] mtrr: type mismatch for d0000000,8000000 old: write-back new: write-combining
[/B]
```

Here's the entire output of "cat /proc/mtrr":

```

reg00: base=0x00000000 (   0MB), size=984064MB: write-back, count=1

```

It looks like the fglrx driver is trying to set up a couple of memory type range register entries that specify how to deal with the video memory, and can't do it because there's already an entry there that covers that address range.  That entry is bogus (984064MB is just stupidly huge), and according to the  the [posting linked above]("http://www.rage3d.com/board/showpost.php?p=1333981360&postcount=18") is caused by the system BIOS telling lies.  It's in no way ATI's fault, all you nVidia boosters :) - what the driver is trying to do is quite reasonable.

That posting shows you how to set up a much more useful mtrr entry for your system RAM, covering only the RAM you actually have installed.  This allows fglrx to set up its own entries without conflicts, and on my box at least gives me fully working 3D without needing to do anything terribly clever with drivers and without needing to hand-edit xorg.conf.

It's still a bit beyond Aunt Tillie though.  Perhaps somebody with more Debian-fu than me (i.e. almost anybody) can make this problem go away with an automatic update.

---

### Post by executer on 2005-12-13
when i type "fglrxinfo" i get an error:

extension "XFree86-DRI" missing on display ":0.0".

What does it mean?

My hole output looks like this:

executer@executer:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I am just trying to get 3ddesktop to work :)

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]when i type "fglrxinfo" i get an error:

extension "XFree86-DRI" missing on display ":0.0".

What does it mean?

My hole output looks like this:

executer@executer:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I am just trying to get 3ddesktop to work :)[/QUOTE]
means that you do not have ati drivers installed...

---

### Post by executer on 2005-12-13
I followed the how-to step-by-step.. Any idea why they are not installed?

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]I followed the how-to step-by-step.. Any idea why they are not installed?[/QUOTE]
could you post your xorg.conf?

---

### Post by executer on 2005-12-13
Here it is:

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
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
	Identifier	"ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

### Post by executer on 2005-12-13
Another problem im having is that ubuntu start, and i get to the login screen. My
monitor goes black and says: Video mode not supported. So I have to do ctrl+alt+num+up to get another screen rezolution, which looks like crap. 
Then I login, and everything is ok, running 1280x1024 resolution.

Is there a way to put the standard screen resolution on startup? Is that in the xorg.conf file, or?

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]Here it is:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9500 Pro (R300 AD)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```[/QUOTE]

The driver here should be fglrx... You can try to change it manually if you know how to to change it back from the command line it it does not work....

---

### Post by executer on 2005-12-13
[QUOTE=foxy123]The driver here should be fglrx... You can try to change it manually if you know how to to change it back from the command line it it does not work....[/QUOTE]

So I set the "ati" to "fglrx". And no, how do I change it back from the command line if it does not work?

---

### Post by executer on 2005-12-13
I edited the xorg.conf to driver "fglrx" and then run:
sudo dpkg-reconfigure -phigh xserver-xorg
to update file.

But my fglrxinfo still looks like this: 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]So I set the "ati" to "fglrx". And no, how do I change it back from the command line if it does not work?[/QUOTE]
There is another tool which can help you to configure your xorg.conf, but I have never used it. Look through this and other ATI topics to find out how to do it.

If you decide to try to do it manually, then first make a backup of you current xorg.conf:
```
cd /etc/X11
sudo cp xorg.conf xorg.backup
```
then do the change.
If it does not work and you can't boot in graphic mode than login in text mode and do the reverse to what you have already done:
```
cd /etc/X11
sudo cp xorg.backup xorg.conf
```

you can either to reboot or run startx, I guess...

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]I edited the xorg.conf to driver "fglrx" and then run:
sudo dpkg-reconfigure -phigh xserver-xorg
to update file.

But my fglrxinfo still looks like this: 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/QUOTE]
take a look at your xorg.conf if "fglrx2 is still there... I am not sure I know what dpkg-reconfigure does (never used it)...

---

### Post by executer on 2005-12-13
No, now its set back to "ati".

So this line error: Xlib:  extension "XFree86-DRI" missing on display ":0.0".
means my ATI drivers are not installed u said?

---

### Post by mlomker on 2005-12-13
[QUOTE=flabdablet]mlomker, perhaps you could link to this in your troubleshooting section.
[/QUOTE]

Will do.

---

### Post by foxy123 on 2005-12-13
[QUOTE=executer]No, now its set back to "ati".

So this line error: Xlib:  extension "XFree86-DRI" missing on display ":0.0".
means my ATI drivers are not installed u said?[/QUOTE]
Try the howto from the beginning... I do not use this dpkg-reconfigure tool, frankly speaking so I do not know why you need it. I guess if you have the driver installed you just need to change ati to fglrx in your xorg.conf. However, if it's not then you'd better repeat the whole routine again starting with removing a possible driver....

---

### Post by mlomker on 2005-12-13
[QUOTE=foxy123]means that you do not have ati drivers installed...[/QUOTE]

You didn't provide enough details:

> 
**General Troubleshooting:**
You can look through the /var/log/Xorg.0.log and kern.log file for troubleshooting most problems.


---

### Post by foxy123 on 2005-12-13
[QUOTE=mlomker]You didn't provide enough details:[/QUOTE]
you're right...

---

### Post by mlomker on 2005-12-13
[QUOTE=executer]Is there a way to put the standard screen resolution on startup? Is that in the xorg.conf file, or?[/QUOTE]

Yes.  You posted your xorg.conf in an earlier post and you had every possible resolution in it, by the looks of things.  I only have one resolution in mine because I never change it.

```

        SubSection "Display"
                Depth     24
                Modes    "1280x800"
        EndSubSection

```

---

### Post by nelposto on 2005-12-13
Hmm...

So I just compiled my own kernel based on 2.6.14, and tried to follow this guide to install the drivers.

fglrxinfo reports correctly my ATI card, glxgears performs wonderfully, but when I try to test with ppracer, it says it can't find a matching GLX visual.

Given that fglrxinfo gives the correct details and glxgears is fine, I'm not sure whether the problem is with my driver setup or ppracer....

I tried uninstalling the driver and then re-installing it under 2.6.12-10, successfully, but prracer gave the same error.

Any ideas?

---

### Post by flabdablet on 2005-12-14
Blarg.  Nothing is ever easy :)

**mlomker**: when you post that link to the workaround, you'll need to tell people to name the symlink /etc/rcS.d/S03fix_mtrr instead of /etc/rcS.d/S02fix_mtrr.  This is because /etc/rcS.d/S02mountvirtfs is already there, and if fix_mtrr also has an S02 prefix they race; mountvirtfs only wins some of the time, so fix_mtrr sometimes tries to write to regular file /proc/mtrr in the root filesystem (which is still mounted readonly) and generates errors instead of fixing problems (whew).

[Bug 18506]("https://bugzilla.ubuntu.com/show_bug.cgi?id=18506") covers the bogus mtrr issue that affected me, and [Bug 17644]("https://bugzilla.ubuntu.com/show_bug.cgi?id=17644") covers a related one.

---

### Post by flabdablet on 2005-12-14
**executer**: For more clues, have a look in /var/log/Xorg.0.log and see if there are any lines in there that start with (EE) or (WW).  Also, try looking in /var/log/messages for lines containing [fglrx] and any nearby lines that look like error messages.

---

### Post by mlomker on 2005-12-14
[QUOTE=nelposto]I tried uninstalling the driver and then re-installing it under 2.6.12-10, successfully, but prracer gave the same error.
[/QUOTE]

I'd recommend asking the question in the gaming forum.  glxgears is as far as I go with the drivers...I don't play games.

---

### Post by deepspring on 2005-12-15
This is how I get my PCIE Radeon X600 Pro to behave itself and run properly, without lockups, usind the fglrx agpgart kernel driver, not the mainboard "intel_agp" agpgart kernel driver.

Firstly I backed up my files (important!)... 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo cp /etc/modules /etc/modules.backup
sudo cp /etc/hotplug/blacklist /etc/hotplug/blacklist.backup
```

Then I did this...

```
sudo apt-get update
sudo apt-get install msttcorefonts
sudo fc-cache -f -v
sudo apt-get install xorg-driver-fglrx fglrx-control
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo cat "fglrx" >> /etc/modules
sudo cat "intel_agp" >> /etc/hotplug/blacklist
```

Then I used the "sudo fglrxconfig" wizard to create a new xorg.conf file. I selected "No" for the option that reads something like "Use External AGP Driver", and selected "Yes" for the option that reads something like "Enable User Locked IO Pages".

When the wizard finished, it created a rather "raw" xorg.conf file, which lacked important things like font paths (bad!). So I opened both the backup xorg.conf file and the new xorg.conf file in gedit ("sudo gedit /etc/X11/xorg.conf /etc/X11/xorg.conf.backup").

I deleted the entire "Files" section from the new xorg.conf and copied the entire "Files" section from the backup copy of xorg.conf to the new one. I also added this entry to the section...

```
FontPath		"/usr/share/fonts/truetype/msttcorefonts"
```

I also tweaked my display and monitor settings. Anyway... here is a copy of my new xorg.conf file (minus some of the rubbish):

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

	FontPath		"/usr/share/X11/fonts/misc"
	FontPath		"/usr/share/X11/fonts/cyrillic"
	FontPath		"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath		"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath		"/usr/share/X11/fonts/Type1"
	FontPath		"/usr/share/X11/fonts/CID"
	FontPath		"/usr/share/X11/fonts/100dpi"
	FontPath		"/usr/share/X11/fonts/75dpi"
    # paths to defoma fonts
	FontPath		"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath		"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
	FontPath		"/usr/share/fonts/truetype/msttcorefonts"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

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

EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30-96
    VertRefresh 50-160
    Option "DPMS"
	DisplaySize		423 317  # 1600x1200
	
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
	VideoRam 262144
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
    Option "DesktopSetup"               "(null)" 
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
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
    BusID "PCI:1:0:0"    # vendor=1002, device=5b62
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
        Modes       "1600x1200"
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

After rebooting my computer, my system was flying along without any problems...

See the attached text file if you need proof.

---

### Post by mlomker on 2005-12-15
[QUOTE=deepspring]This is how I get my PCIE Radeon X600 Pro to behave itself and run properly, without lockups, usind the fglrx agpgart kernel driver, not the mainboard "intel_agp" agpgart kernel driver.
[/quote]

The fonts aren't needed by the driver and you don't need **fglrx** in /etc/modules because it gets called out of the xorg.conf.  You might want to specify /truetype instead of /truetype/msttcorefonts, since there are probably other fonts in that directory as well.

I do find it interesting that blacklisting the gart worked for you.  I had tried it before by renaming the modules themselves and 3D fails to function without them.  Perhaps it just works on your particular motherboard (or just Intel).  I have an AMD64 and it uses two in its interface:

```

mlomker@mlomkernote:/etc/X11$ lsmod | grep fglrx
fglrx                 438496  7
agpgart                34888  3 fglrx,sis_agp,amd64_agp

```

Following your instructions:

```

mlomker@mlomkernote:/etc/init.d$ dmesg | grep fglrx
[4294735.782000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294735.782000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
[4294735.814000] [fglrx] ACPI power management is initialized.
[4294736.361000] [fglrx] Failed to load fglrx_agp module
[4294736.361000] [fglrx] Error code  256
[4294736.361000] [fglrx] Failed to load ATI module agpgart
[4294736.361000] [fglrx] Fallback to internal agpgart module
[4294736.361000] [fglrx] Initialization of built-in AGP-support failed (ret=-19).
[4294736.362000] [fglrx:firegl_unlock] *ERROR* Process 7599 using kernel context 0
mlomker@mlomkernote:/etc/init.d$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I believe your results, but I won't add something to a how-to unless it works fairly universally...starting with my own laptop!  :)

Thanks.

---

### Post by deepspring on 2005-12-15
[QUOTE=mlomker]The fonts aren't needed by the driver and you don't need **fglrx** in /etc/modules because it gets called out of the xorg.conf.  You might want to specify /truetype instead of /truetype/msttcorefonts, since there are probably other fonts in that directory as well.[/QUOTE]

Actually, I found that some older applications became a little more responsive and the fonts appeared to be a lot smoother (especially websites and wine apps that required Arial or Tahoma) after adding the FontPaths from the original xorg.conf to the fglrxconfig generated xorg.conf.

But thats probably just me.

[QUOTE=mlomker]I do find it interesting that blacklisting the gart worked for you.  I had tried it before by renaming the modules themselves and 3D fails to function without them.  Perhaps it just works on your particular motherboard (or just Intel).  I have an AMD64 and it uses two in its interface:

```

mlomker@mlomkernote:/etc/X11$ lsmod | grep fglrx
fglrx                 438496  7
agpgart                34888  3 fglrx,sis_agp,amd64_agp

```

Following your instructions:

```

mlomker@mlomkernote:/etc/init.d$ dmesg | grep fglrx
[4294735.782000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294735.782000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
[4294735.814000] [fglrx] ACPI power management is initialized.
[4294736.361000] [fglrx] Failed to load fglrx_agp module
[4294736.361000] [fglrx] Error code  256
[4294736.361000] [fglrx] Failed to load ATI module agpgart
[4294736.361000] [fglrx] Fallback to internal agpgart module
[4294736.361000] [fglrx] Initialization of built-in AGP-support failed (ret=-19).
[4294736.362000] [fglrx:firegl_unlock] *ERROR* Process 7599 using kernel context 0
mlomker@mlomkernote:/etc/init.d$  fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

I believe your results, but I won't add something to a how-to unless it works fairly universally...starting with my own laptop!  :)

Thanks.[/QUOTE]

Sadly, I don't own an AMD64 system or a laptop for that matter to test it on, and I don't have a system with an onboard ATI IGP chipset either. We probably wont know if I'm the only one it works for unless others on different setups give it a shot. 

However, in your case I'm willing to accept that it is going to be tricky to get it to work perfectly. I noticed that you didn't blacklist any of the other AGPgart drivers (??). You should be able try various configurations without harming your setup (*crossing fingers*).

Anyways, I have tried other config variations, such as...

I was greeted with terrible 3D performance for this configuration:  No blacklisting of "intel_agp", no loading "fglrx" in "/etc/modules", disabled the "fglrx" builtin AGPgart in the xorg.conf file (option "UseInternalAGPGART" "no").

I was greeted with random lockups, as well as poor 3D performance with this configuration: blacklisting "intel_agp", no loading "fglrx" in "/etc/modules", enabled the "fglrx" builtin AGPgart in the xorg.conf file (option "UseInternalAGPGART" "yes").

I was greeted with lockups as soon as Gnome loaded with this configuration: no blacklisting "intel_agp", no loading "fglrx" in "/etc/modules", enabled the "fglrx" builtin AGPgart in the xorg.conf file (option "UseInternalAGPGART" "yes").

I was greeted with lockups as soon as Gnome loaded with this configuration: no blacklisting "intel_agp", loading "fglrx" in "/etc/modules", enabled the "fglrx" builtin AGPgart in the xorg.conf file (option "UseInternalAGPGART" "yes").

Others might have differing results.

I also found that 3D performance went up a notch or two when I specified how much memory my video card has in the xorg.conf file (VideoRam 262144).

That said my next video card is going to be an nVidia. :D

---

### Post by mlomker on 2005-12-15
[QUOTE=deepspring]I noticed that you didn't blacklist any of the other AGPgart drivers (??). You should be able try various configurations without harming your setup (*crossing fingers*).[/quote]

Sure I did.  The lsmod output was the 'before' picture.  I tried disabling them individually and then both.  sis_agp doesn't seem to affect anything when it is missing but the amd64 one will cause the driver to not work at all (as the output showed).

> That said my next video card is going to be an nVidia. :D

They definitely have the upper-hand in performance right now, but I've talked to my counterparts that maintain the Nvidia how-to's and they tell me that it's just as bad.  The video card wasn't the deciding factor for me--I'm an AMD fan and AMD laptops with Nvidia cards don't seem that common.

---

### Post by deepspring on 2005-12-15
[QUOTE=mlomker]Sure I did.  The lsmod output was the 'before' picture.  I tried disabling them individually and then both.  sis_agp doesn't seem to affect anything when it is missing but the amd64 one will cause the driver to not work at all (as the output showed).[/QUOTE]

Well, I said it would be tricky. 

The amd64_agp is probably some form of 64bit emulation driver or an instructional interface for other 32bit agpgart drivers.

You could try leaving the sis_agp driver blacklisted (not renamed), keep the amd64_agp driver loaded, add fglrx to "/etc/modules", modify your xorg.conf to use fglrx's internal agpgart.

If you get lockups or poor 3D performance, then you can just change things back...

[QUOTE=mlomker]They definitely have the upper-hand in performance right now, but I've talked to my counterparts that maintain the Nvidia how-to's and they tell me that it's just as bad.  The video card wasn't the deciding factor for me--I'm an AMD fan and AMD laptops with Nvidia cards don't seem that common.[/QUOTE]

I have seen a few notebooks around with AMD processors and GeForce Go graphics chipsets. But these have always been really crap notebooks.

---

### Post by eXSBass on 2005-12-16
Does this guide work for the latest 8.19.10 drivers? If so do I need to change anything?

Thanks

---

### Post by mlomker on 2005-12-16
[QUOTE=eXSBass]Does this guide work for the latest 8.19.10 drivers? If so do I need to change anything?
[/QUOTE]

Nope.  8.20.8 is the latest.  [Use this.]("http://ubuntuforums.org/showthread.php?t=78466")

---

### Post by deepspring on 2005-12-16
Didn't realise you had a howto for the latest drivers. I just installed and tested them using my config [above](http://ubuntuforums.org/showpost.php?p=575778&postcount=224) , and so far they are working brilliantly...

```
scott@lazerus:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 PRO Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

scott@lazerus:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
2004 frames in 5.0 seconds = 400.800 FPS
2423 frames in 5.0 seconds = 484.600 FPS
2404 frames in 5.0 seconds = 480.800 FPS
2429 frames in 5.0 seconds = 485.800 FPS
2421 frames in 5.0 seconds = 484.200 FPS
2415 frames in 5.0 seconds = 483.000 FPS
2366 frames in 5.0 seconds = 473.200 FPS

scott@lazerus:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
12504 frames in 5.0 seconds = 2500.649 FPS
12470 frames in 5.0 seconds = 2493.964 FPS
12471 frames in 5.0 seconds = 2494.178 FPS
12470 frames in 5.0 seconds = 2493.830 FPS
12472 frames in 5.0 seconds = 2494.313 FPS
12470 frames in 5.0 seconds = 2493.890 FPS
12471 frames in 5.0 seconds = 2494.136 FPS

scott@lazerus:~$ lsmod | grep agp
agpgart                34792  1 fglrx

scott@lazerus:~$ dmesg | grep fglrx
[4294683.464000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294683.466000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294683.466000] [fglrx] module loaded - fglrx 8.20.8 [Dec  6 2005] on minor 0
[4294683.488000] [fglrx] ACPI power management is initialized.
[4294707.608000] [fglrx] free  PCIe = 54804480
[4294707.608000] [fglrx] max   PCIe = 54804480
[4294707.608000] [fglrx] free  LFB = 108908544
[4294707.608000] [fglrx] max   LFB = 108908544
[4294707.608000] [fglrx] free  Inv = 134217728
[4294707.608000] [fglrx] max   Inv = 134217728
[4294707.608000] [fglrx] total Inv = 134217728
[4294707.608000] [fglrx] total TIM = 0
[4294707.608000] [fglrx] total FB  = 0
[4294707.608000] [fglrx] total PCIe = 16384

scott@lazerus:~$ dmesg | grep agp
[4294683.389000] Linux agpgart interface v0.101 (c) Dave Jones

scott@lazerus:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=1024MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=1

scott@lazerus:~$ cat /var/log/Xorg.0.log | grep fglrx
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) fglrx(0): pEnt->device->identifier=0x82128f0
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "NoAccel" "no"
(**) fglrx(0): Option "NoDRI" "no"
(**) fglrx(0): Option "Capabilities" "0x00000000"
(**) fglrx(0): Option "CapabilitiesEx" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionI" "0x00000000"
(**) fglrx(0): Option "GammaCorrectionII" "0x00000000"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DesktopSetup" "(null)"
(**) fglrx(0): Option "HSync2" "unspecified"
(**) fglrx(0): Option "VRefresh2" "unspecified"
(**) fglrx(0): Option "ScreenOverlap" "0"
(**) fglrx(0): Option "UseInternalAGPGART" "yes"
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
(**) fglrx(0): Option "PseudoColorVisuals" "off"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x00000000
(**) fglrx(0): Gamma Correction for II is 0x00000000
(==) fglrx(0): Buffer Tiling is ON
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(**) fglrx(0): Option "mtrr" "off"
(--) fglrx(0): Chipset: "RADEON X600 (RV380 5B62)" (Chipset = 0x5b62)
(--) fglrx(0): (PciSubVendor = 0x147b, PciSubDevice = 0x0002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI RV380
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V380
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): Video RAM override, using 262144 kB instead of 262144 kB
(**) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 4a5b  Serial#: 4671
(II) fglrx(0): Year: 2002  Week: 11
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Signal levels configurable
(II) fglrx(0): Sync:  Separate  Composite
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) fglrx(0): Gamma: 2.76
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.638 redY: 0.326   greenX: 0.279 greenY: 0.602
(II) fglrx(0): blueX: 0.142 blueY: 0.063   whiteX: 0.282 whiteY: 0.298
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 720x400@88Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@87Hz (interlaced)
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) fglrx(0): #5: hsize: 2048  vsize 1536  refresh: 60  vid: 16609
(II) fglrx(0): #6: hsize: 1600  vsize 1200  refresh: 70  vid: 19113
(II) fglrx(0): #7: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 157.5 MHz   Image Size:  350 x 262 mm
(II) fglrx(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 98 kHz, PixClock max 270 MHz
(II) fglrx(0): Monitor name: 900B
(II) fglrx(0): Monitor name: 
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  4 power states available:
(II) fglrx(0):   1. 405/257MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   2. 304/257MHz @ 50Hz [enable load balancing, overdrive]
(II) fglrx(0):   3. 419/257MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(II) fglrx(0):   4. 432/257MHz @ 50Hz [overclocked, enable load balancing, overdrive]
(**) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(**) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(**) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 49 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"  202.50  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0):  Default mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"  119.65  1152 1224 1352 1552  864 865 868 907 +hsync
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.77  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.68  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.29  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"  143.47  1152 1232 1360 1568  864 865 868 915 +hsync
(**) fglrx(0):  Default mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814 +hsync
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"  100.19  1024 1088 1200 1376  768 769 772 809 +hsync
(**) fglrx(0):  Default mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 84.0 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"   83.95  800 856 944 1088  600 601 604 643 +hsync
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"   60.06  800 840 928 1056  600 601 604 632 +hsync
(**) fglrx(0):  Default mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"   72.85  640 680 752 864  480 481 484 527 +hsync
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"   52.41  640 680 744 848  480 481 484 515 +hsync
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"   43.16  640 680 744 848  480 481 484 509 +hsync
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"   37.89  640 672 736 832  480 481 484 506 +hsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(**) fglrx(0): Display dimensions: (423, 317) mm
(WW) fglrx(0): Probed monitor is 360x270 mm, using Displaysize 423x317 mm
(**) fglrx(0): DPI set to (96, 96)
(**) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(**) fglrx(0): FSAA Gamma enabled
(**) fglrx(0): FSAA Multisample Position is fix
(**) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/X11R6/lib/modules/linux/libfglrxdrm.a
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
(II) fglrx(0): Depth moves disabled by default
(**) fglrx(0): Capabilities: 0x00000000
(**) fglrx(0): CapabilitiesEx: 0x00000000
(**) fglrx(0): cpuFlags: 0x8000001d
(**) fglrx(0): cpuSpeedMHz: 0x00000ae9
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): UseFastTLS=0
(**) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xe0954000 (size=0x0769c000)
(II) fglrx(0): UMM area:     0xe0954000 (size=0x0769c000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 6.8.2.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8d32000
(II) fglrx(0): [drm] mapped SAREA 0xf8d32000 to 0xb7a7f000
(II) fglrx(0): [drm] framebuffer handle = 0xe0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.20.8
(II) fglrx(0):     Date: Dec  6 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.12-10-686
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0xf1000000
(II) fglrx(0): [pcie] 65536 kB allocated with handle 0xdeadbeef
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 28672
(II) fglrx(0): [drm] texture shared area handle = 0xf8ea4000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x00954000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,1528)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1200)
(II) fglrx(0): Largest offscreen area available: 1600 x 320
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x00000001
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
```


**Update:**

After running stable for several days without incident, my video card finally started playing up. Basicly, Xorg would display nothing but a white screen whenever I went to shutdown, this was happening at random and I couldn't even switch to a text terminal.

I am yet to find out what is causing this issue (nothing is showing up in the logs) and why it just started happening all of a sudden. So, as a precaution I have changed back to using mlomkers recommendations of...

- Leaving "fglrx" out of "/etc/modules"
- Leaving "intel_agp" out of "/etc/hotplug/blacklist"
- Disabling "fglrx" built-in AGPGart controller in "/etc/X11/xorg.conf"

If anyone else starts having these problems after trying my earlier posts configuration recommendations, I would recommend doing the same...

---

### Post by amohanty on 2005-12-18
Just a note, the Ctrl-Alt-Backspace thingy did not reload X for me, Had to do a reboot to get it to work.

But aside from that it has worked beautifully.

AM

---

### Post by Masteroc on 2005-12-23
Will this driver work for a  ATI Rage 128 card??

---

### Post by mlomker on 2005-12-23
[QUOTE=Masteroc]Will this driver work for a  ATI Rage 128 card??[/QUOTE]

No.

---

### Post by Masteroc on 2005-12-23
then what can i use if i want to install an ati rage 128?

---

### Post by veloct on 2005-12-23
[QUOTE=mlomker]Nope.  8.20.8 is the latest.  [Use this.]("http://ubuntuforums.org/showthread.php?t=78466")[/QUOTE]

That worked for me.

```
eddie@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)
```

Thanks.

---

### Post by Masteroc on 2005-12-23
Is there a driver for the Rage 128 pro, or can i just use the driver with ubuntu?

---

### Post by littlered on 2005-12-24
Well, I just tried to install xorg-driver-fglrx for my AIW Radeon 8500DV and I thought it was working, but as it turns out it would freeze on me after logging in within a few minutes, usually just a couple... I've poked around a bit to no avail, and I'm not sure where to go from here... If anyone else has had a similar problem solved, I'd love to hear about it, though. :)

Edit: After following the directions from this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Uninstalling the default driver and making the packages for the current ATI driver and such, it's working. Woohoo!

Except, the "sudo aticonfig --initial" at the end part didn't edit the file properly and created a new section in xorg.conf the computer wasn't reading. So then I just did dpkg-reconfigure xserver-xorg and there it went.

Thanks,

x

---

### Post by mlomker on 2005-12-24
[QUOTE=Masteroc]Is there a driver for the Rage 128 pro, or can i just use the driver with ubuntu?[/QUOTE]

AFAIK the only option is to use the ATI driver that comes with Ubuntu.  It's open-source and provides software 3D using MESA.  The Rage cards are so slow that you wouldn't get any performance improvement from an ATI-written driver anyway (that's probably why ATI doesn't write one).

---

### Post by whitesox on 2005-12-24
Hi, I have an old-ish toshiba laptop, with an old graphics card, the radeon m6 9000.  But when I installed the ati drivers without a hitch, xserver will not start.  When the driver is set to "ati" it works fine, although 3d does not work, but when I set it to "fglrx", i get this error:
```

"(II) ATI Radeon/FireGL: The following chipsets are supported:
        RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
        MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
        RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
        RADEON 9200 (RV280 5961), RADEON 9200 SE (RV280 5964),
        MOBILITY RADEON 9200 (M9+ 5C61), etc...
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.20.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.20g1
(II) ATI Proprietary Linux Driver Build Date: Dec  6 2005 20:05:53
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.20.1-driver-lnx-232334
(EE) No devices detected.

```:

Mine is not listed! why is it not listed? It should work, unless somehow the 9000 is before the 8500.  And also, this is the ONLY error I get.

---

### Post by mlomker on 2005-12-24
[QUOTE=whitesox]the radeon m6 9000.  [/QUOTE]

That's a case of misleading labeling.  It's actually a [7500 chip]("http://ubuntuforums.org/showthread.php?t=26148").

---

### Post by whitesox on 2005-12-24
Yup thats it.  Oh well.

---

### Post by Masteroc on 2005-12-25
sry for the double or triple post, but i really need to get my ATI Rage 128 pro card working with ubuntu. I am not sure wheather to just replace the current card (Trident 3D image) with it, or do i need to first install a driver or change some text in my x11\...\xconfig file?

Any help at all would be appreciated

---

### Post by mlomker on 2005-12-26
[QUOTE=Masteroc]sry for the double or triple post, but i really need to get my ATI Rage 128 pro card working with ubuntu.[/QUOTE]

Start a new thread in the Video & Sound forum.

---

### Post by Masteroc on 2005-12-26
k, thanks, ill do that

---

### Post by thava on 2006-01-10
I follow the ATI fglrx driver 8.16.20 installation guide. After the succesfully instalation of my ATI driver, i can't open my emacs in normal view. :(

The warning msg i got:

> 
thava@local ~
$ emacs
Warning: Cannot convert string "-*-courier-medium-r-*-*-*-120-*-*-*-*-iso8859-*" to type FontStruct
Warning: Cannot convert string "-*-helvetica-medium-r-*--*-120-*-*-*-*-iso8859-1" to type FontStruct


And my tvout is also not working.
Sse my xorg.conf is attach here:

Thanks
/ Thava

---

### Post by Randomskk on 2006-01-11
I'm running and AMD64 3200+ system, with 2gig of ram and an ATI Radeon X800XT PE.
First install of Ubuntu, this guide went fine, and I tried the darwinia demo, ran perfect.
However, I had to wipe that install and start over, and having done so, while the install went OK, Darwinia has 1FPS.

Not sure what's causing this...

```
adam@random:~$ fgl_glxgears
7791 frames in 5.0 seconds = 1558.200 FPS
7769 frames in 5.0 seconds = 1553.800 FPS
7702 frames in 5.0 seconds = 1540.400 FPS
7789 frames in 5.0 seconds = 1557.800 FPS
7710 frames in 5.0 seconds = 1542.000 FPS
7895 frames in 5.0 seconds = 1579.000 FPS
7875 frames in 5.0 seconds = 1575.000 FPS
7757 frames in 5.0 seconds = 1551.400 FPS
7718 frames in 5.0 seconds = 1543.600 FPS
7804 frames in 5.0 seconds = 1560.800 FPS
7987 frames in 5.0 seconds = 1597.400 FPS
7992 frames in 5.0 seconds = 1598.400 FPS

```

```
adam@random:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
29745 frames in 5.0 seconds = 5930.314 FPS
25402 frames in 5.1 seconds = 5028.870 FPS
26425 frames in 5.1 seconds = 5201.108 FPS
26458 frames in 5.0 seconds = 5247.279 FPS

```

```
adam@random:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)



display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

```
adam@random:~$ lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4a5                        0
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4a70

```

```
adam@random:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0xe0000000 (3584MB), size= 128MB: write-combining, count=2
reg02: base=0xe8000000 (3712MB), size= 128MB: write-combining, count=14

```

```
adam@random:~$ lsmod | grep fglrx
fglrx                 277304  14

```

```
# File: xorg.conf
# File generated by fglrxconfig (C) ATI Technologies, a substitute for xf86config.

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
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

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
    Option "XkbLayout"	"gb"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ExplorerPS/2"
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

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

# this is from the old file, it's for scroll wheel to work
    Option "ZAxisMapping"	"4 5"

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


Section "Monitor"
    Identifier  "Monitor1"
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
    Identifier                          "ATI Graphics Adapter connector 0"
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
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
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
    BusID "PCI:1:0:0"    # vendor=1002, device=4a50
    Screen 0
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 1"
    Driver                              "fglrx"
    BusID "PCI:1:0:0"    # vendor=1002, device=4a50
    Screen 1
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
    Device      "ATI Graphics Adapter connector 0"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter connector 1"
    Monitor     "Monitor1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
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
    Screen "Screen1" RightOf "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

```

Thanks for any help, I'd really like to get 3d games working nicely here.


edit: I just noticed that I think I installed the latest driver instead of this one last time, I'll try following the latest driver install tomorrow and see if it helps :)

---

### Post by deepspring on 2006-01-11
```

    Option "UseFastTLS"                 "0"
    Option "UseInternalAGPGART"         "yes"

```

Try changing the above to...

```

    Option "UseFastTLS"                 "2"
    Option "UseInternalAGPGART"         "no"

```

And then restart...

---

### Post by onesojourner on 2006-01-13
I have a 7500 radeon. will this driver screw things up?

---

### Post by animated on 2006-01-14
Thanks mlomker for the great unofficial guide to setting up Ubunto for ATI at:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

It took a lot of reading to figure out that the official guide doesn't
work.


I have an HP-a1250n and it has the following

   Athlon64 x2 processor
  Motherboard: MSI MS-7184, Socket 939, Northbridge ATI RS482,
	Southbridge ATI SB400, HP name: AmethystM or 
             AmethystM-GL6E
             250GB SATA drive
	ATI Radeon Xpress 200 Series integrated video
 
I was getting the DRIScreenInit Failed and Disabling DRI messages from the
ATI card.  I also got the "libGL error: drmMap of sarea failed".  But the
libdri.a fix worked for this.

I am a Linux newbie, and documented the problems I had setting up the HP-a1250n here [http://www.geocities.com/dcblaha/articles/hp-a1250nLinux.htm]("http://www.geocities.com/dcblaha/articles/hp-a1250nLinux.htm").

---

### Post by Glass Casket on 2006-01-14
I have the ATI X300 PCIE, so i'm assuming it'll work.

But when I tried to do what the little tutorial asked, it still told me my card was a mesa something...

---

### Post by flight_master on 2006-01-14
Can you please post the output of 

```

sudo lsmod 

```

and 
```

sudo lspci -v
``` 

and finally,
```
fglrxinfo
```


-Christian

---

### Post by mlomker on 2006-01-15
[QUOTE=animated]Thanks mlomker for the great unofficial guide to setting up Ubunto for ATI at:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

It took a lot of reading to figure out that the official guide doesn't
work.
[/QUOTE]

That's true.  If someone wants to update the 'official' documentation then they are welcome to do so.  I don't care to participate there.

I worked with Septor (the Ubuntu driver packager), who solved the problem.  I then documented the installation procedure.  It's been a known issue since Breezy was deployed, so I'm not sure why Ubuntu hasn't fixed their version of the driver.  I can only assume that they disagree with ATI's methods for whatever reason.

---

### Post by mlomker on 2006-01-15
[QUOTE=Glass Casket]I have the ATI X300 PCIE, so i'm assuming it'll work.

But when I tried to do what the little tutorial asked, it still told me my card was a mesa something...[/QUOTE]

The logs to review are listed under General Troubleshooting.

---

### Post by langerouge on 2006-01-15
i have an ATI 9600 and my OS is Linux Ubuntu.
My problem is:

(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xd0c0a000 at 0xb7b04000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

Can anybody help me?
tks!

---

### Post by flight_master on 2006-01-15
Welcome to the world of late nights, and lots of coffee (A.K.A Ubuntu)! :D

This will help: 
[HowTo: ATI fglrx Hardware Acceleration](http://ubuntuforums.org/showthread.php?t=115104)

-Christian

---

### Post by Mellon on 2006-01-16
Hola!!!

I try this "how to" with no luck, used to have the mesa thing when i type  fglrxinfo but now im getting something diferent....



```
edwin@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 Prototype DDR Athlon (3DNow!) (FireGL) (GNU_ ICD)
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

edwin@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
4619 frames in 5.0 seconds = 923.798 FPS
3720 frames in 5.0 seconds = 743.948 FPS
3649 frames in 5.0 seconds = 729.763 FPS
3649 frames in 5.0 seconds = 729.766 FPS

edwin@ubuntu:~$ fgl_glxgears
550 frames in 5.0 seconds = 110.000 FPS
563 frames in 5.0 seconds = 112.600 FPS
567 frames in 5.0 seconds = 113.400 FPS
444 frames in 5.0 seconds = 88.800 FPS

edwin@ubuntu:~$ lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)

edwin@ubuntu:~$ lsmod | grep fglrx
fglrx                 245412  7
agpgart                32328  2 fglrx,amd64_agp

```

im running an Ati Radeon 9250 on an AMD 64 

Gracias.

---

### Post by mlomker on 2006-01-16
[QUOTE=Mellon]I try this "how to" with no luck, used to have the mesa thing when i type  fglrxinfo but now im getting something diferent....
[/QUOTE]

I don't understand your comment, because that output means that it worked.

---

### Post by mlomker on 2006-01-16
[QUOTE=flight_master]Welcome to the world of late nights, and lots of coffee (A.K.A Ubuntu)! :D

This will help: 
[HowTo: ATI fglrx Hardware Acceleration](http://ubuntuforums.org/showthread.php?t=115104)[/QUOTE]

Nice, I'll refer people to that.

---

### Post by Roookie on 2006-01-16
Could someone give me working repo for ppc and xorg-driver-fglrx?

---

### Post by Mellon on 2006-01-16
[QUOTE=mlomker]I don't understand your comment, because that output means that it worked.[/QUOTE]

i think is very slow, and when i try "fgl_glxgears" i cant see anything...

---

### Post by BLTicklemonster on 2006-01-16
Thank you, I'm stuck in Vesa again. And when I can manage to get ati to appear to work, I get that glx mess up message again. I'm not posting any info, because it's all been said before, but I can tell you right now, if I were an average Joe, and didn't know Nvidia was out there, I'd walk away from linux altogether. 4 hours I've been trying to get this card to work, and I have nothing to show for it.

Rant rant rant.


I'll keep trying, dammit.

---

### Post by flight_master on 2006-01-17
TickleMonster,

Just curious... but what do you mean "that glx messup message again"? I'm guessing, that something is going wrong with the hardware acceleration? Can you post your xorg.log? I'm pretty sure we can work this out for you ;)

-Christian

---

### Post by jrei on 2006-01-17
Hi,

i have a new Thinkpad z60m which has a ATI x600 and got it working.
Since I realy like suspend and DRI which is only supported by the fglrx 8.20.xx I had no other choice than trying that driver.

First I got the rpm from ATI.com and converted it with alien. I had to mess arround to get it working. And the result was - "Direct rendering = No".

I new that I risked my system, but since I just installed it I did what kids shouldn't do at home.

I opend my '/etc/apt/sources.list' and replaced breezy with dapper.

I did a

```

apt-get update
apt-get install xorg-driver-fglrx

```

and tried to restartet my X.  Which led to a "No input devices found".
I remembered something simmilar from the xfree to xorg upgrade.
So I did a 
```

apt-get install xserver-xorg-input*

```
beeing ready for a totaly broken system.

I tried to start X and it started.
```

glxinfo

```
told me, "Direct rendering = Yes" *cheers*

And it also survives suspend and hibernation.

It worked on a new installed breezy. I don't know what it will do to an older system. 

As I mentioned above "don't try this at home" or better don't try it on a system you debend on. Dapper is unstable and if you install some packages you will need more because of version conflicts. 
For me it's ok because I can't live without suspend. ^^ If for you it's something simmilar, give it a shot.

Greetings, Jörn

---

### Post by WhiteZ on 2006-01-17
Hi,

Any idea about how to get xrandr rotation working with this ?

In the X logs I get the
(==) RandR enabled

but when trying to rotate I'm getting the following error:
% xrandr -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  157 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12


Othervise the driver seems to be working fine:
% fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300 SE Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)


The monitor is Samsung 214T which supports the pivoting

Regards

Jyri

---

### Post by BLTicklemonster on 2006-01-17
> **flight_master]TickleMonster,

Just curious... but what do you mean "that glx messup message again"? I'm guessing, that something is going wrong with the hardware acceleration? Can you post your xorg.log? I'm pretty sure we can work this out for you  said:**
> 

I'm in VESA now, and actually don't relish going back and changing things again. It is tiresome to do so. I had hoped that I could just change the card, bring up the machine using sudo dpkg-reconfigure xserver-xorg and set it to vesa and then install. I did that with the original how to for ati and then came here trying. None did the trick. 

This, however:

[quote]ati-driver-installer-8.18.6-i386.run

1. apt-get install build-essential
2. apt-get install linux-headers-2.6.12-9
3. apt-get install linux-headers-2.6.12-9-386
4. apt-get install gcc-3.4
5. apt-get install libstdc++5

6. rm -rf /lib/linux-restricted-modules/2.6.12-9-386/fglrx/
7. rm -f /lib/modules/2.6.12-9-386/volatile/fglrx.ko

8. sh ati-driver-installer-8.18.6-i386.run

9. /usr/X11R6/bin/fglrxconfig
Do you want to initialize xfree86-dga (y/n)? [n] y
Do you want to use the external AGP GART module (y/n)? [n] y

10. reboot 
accounting for driver version being newer worked to the extent that I actually got to the desktop in an ati driver. But I still got that good old glx error. Bah, when I'll run that again while I finish up this other computer (dude's going on windows xp for sure, I know he can't do more that point and click) and see if I can get to the desktop in ati, and run fglrxinfo again and see if I can post it. It's the one with the 0.0 at the end, if that helps, lol.


*edit:

```
bill@ubuntu:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

bill@ubuntu:~$

```

Bingo, looked in the log, and my NVIDIA-Linux-x86-1.0-8174-pkg1 drivers are still there. Oops. And I bet this has something to do with it:
```
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
```

Now how do I remedy this here situation?

*edit:

Oh, sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run --uninstall. Done, now to reconfigure again...

---

### Post by BLTicklemonster on 2006-01-17
lmao:

```
bill@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

bill@ubuntu:~$

```

well, I'm getting there...


*edit:

No I'm not... I just followed the instructions from the first page, and could not get back to the desktop. I had to reconfigure to vesa once again. 

The hilarity ensues...

---

### Post by flight_master on 2006-01-18
You need to unload those nvidia drivers ;) Also, do me a favour, and post the entire xorg.log! I think that you are having an issue with MTRR allocations...

-Christian

---

### Post by mlomker on 2006-01-18
[QUOTE=BLTicklemonster]The hilarity ensues...[/QUOTE]

In another post you also reference trying to use the latest drivers and then reinstalling the old ones from the Ubuntu CD (which this thread discusses).  

The way that you installed 8.18.x is not one that I would have used because you're deleting files rather than removing packages.  I have no doubt that by this point you have a crazy mix of Nvidia, 8.16.20, and and 8.18.x drivers on your hard disk and it'll probably be difficult to figure it out.

The GLX file is in /usr/X11R6/lib/modules/extensions/ along with other video drivers that are loaded during startup.

---

### Post by BLTicklemonster on 2006-01-19
You asked for it! I think this is what is the problem?


```
(**) fglrx(0): Option "mtrr" "off"

or maybe this

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
```

Here's the what looks to be causing the problem, I got a bad kernel (call stalag 13!!!), I can't post the whole thing... (and mlomker, yeah, probably, but what now? I'm willing to suffer through this if you dudes are willing to help me)
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 18 23:51:50 2006
(==) Using config file: "/etc/X11/xorg.conf"

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d87000 at 0xb7b19000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
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

```

---

### Post by BLTicklemonster on 2006-01-19
LMAO, you guys are gonna crucify me, but I removed the fglrx kernel using synaptic, then used terminal, and installed (sudo sh atidriver.run) the driver, and looky:
```
bill@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1030 (X4.3.0-8.20.8)

bill@ubuntu:~$

```

I guess that worked?


(huh, just looked, and mtrr is still off, but Unreal Tournament played like a champ, except for the one thing that I always see in it when I use ati, and that is the mouse is spongy, like it's lagging behind me or something)

---

### Post by mlomker on 2006-01-19
[QUOTE=BLTicklemonster]LMAO, you guys are gonna crucify me

I guess that worked?
[/QUOTE]

Looks happy to me.  :cool:

---

### Post by flight_master on 2006-01-19
[QUOTE=BLTicklemonster]You asked for it! I think this is what is the problem?


```
(**) fglrx(0): Option "mtrr" "off"

or maybe this

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
```

Here's the what looks to be causing the problem, I got a bad kernel (call stalag 13!!!), I can't post the whole thing... (and mlomker, yeah, probably, but what now? I'm willing to suffer through this if you dudes are willing to help me)
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Thu Dec 22 11:37:10 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 18 23:51:50 2006
(==) Using config file: "/etc/X11/xorg.conf"

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.19.10
(II) fglrx(0):     Date: Nov  9 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8d87000 at 0xb7b19000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd8000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor (scanline 1024)
(II) fglrx(0): Largest offscreen area available: 1280 x 7163
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

```[/QUOTE]


Could you please post your ```
uname -r
```? Are you using an SMP kernel? Or a 386? There's a mismatch somewhere.

-Christian

---

### Post by BLTicklemonster on 2006-01-19
```
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Thu Dec 22 11:37:10 UTC 2005 i686
```

See, this is what gets me, there's an i686 on the end of that.

I'll be home shortly, you name it, I'll uname -r it.

---

### Post by BLTicklemonster on 2006-01-19
OMG, I just noticed this:

```
Build Operating System: Linux 2.6.10 i686 [ELF] 
```


It's like I can't get away from Helios or something.


Anyway, it's what it shows up there.

---

### Post by spoilerhead on 2006-01-20
new drivers 8.21.7 availaible at ati.com

---

### Post by Atomac on 2006-01-21
Hi,

I have just installed AMD64 Ubuntu on an AMD 64 machine. I have a PowerColor ATI X800GTO 16 graphic card.

I had the problem of X not working when I installed. After reading on here I got the vesa (?) drive to work. I then had a look at the guide above for install the fglrx drive.

1. The line in the first bit about removing Linux-Restricted with the -$ (uname -r) at then end. No matter how I type that it doesn't like it.

2. I used apt-get to get the latest driver and I can select it in the xconfig but when I do x won't start.

3. How am I meant to be able to download the older file for the AMD64 version from the command line?

I am a total n00b and completed flumoxed. Thanks.

---

### Post by BLTicklemonster on 2006-01-21
[QUOTE=Atomac]Hi,

I have just installed AMD64 Ubuntu on an AMD 64 machine. I have a PowerColor ATI X800GTO 16 graphic card.

I had the problem of X not working when I installed. After reading on here I got the vesa (?) drive to work. I then had a look at the guide above for install the fglrx drive.

1. The line in the first bit about removing Linux-Restricted with the -$ (uname -r) at then end. No matter how I type that it doesn't like it.

2. I used apt-get to get the latest driver and I can select it in the xconfig but when I do x won't start.

3. How am I meant to be able to download the older file for the AMD64 version from the command line?

I am a total n00b and completed flumoxed. Thanks.[/QUOTE]

Maybe I did it wrong, too, but I assumed he meant that you put the info from typing uname -r there instead of putting -$ (uname -r)... like just before you do that particular command, just type uname -r and whatever it says, put that there in place of the -$ (uname -r). Try that.

---

### Post by BLTicklemonster on 2006-01-22
Okay, so yeah, I'm stupid. I saw the mention of a new ati driver, loaded it up and the system tanked yet again. After giving it a go, I gave up and traded my killer 128 meg ati for a 32 meg nvidia and loaded up the drivers first try. Sorry, but I'm not about to attempt ati on linux ever again. Thanks for all your help and understanding guys, you are a class act. Thanks again.

---

### Post by ilbahr on 2006-01-23
any one have problems with gdmflexiserver (new login prgoram) and the fglrx driver. I get a scrambled screen when i use it.

Card ATI 9600.

Ps running glxgears give me some crazy results.

1767 FPs while the actual animation is buggy

---

### Post by mlomker on 2006-01-23
[QUOTE=BLTicklemonster]-$(uname -r)[/QUOTE]

No, that actually works but you can't have a space between the $ and the rest.

---

### Post by mlomker on 2006-01-23
[QUOTE=spoilerhead]new drivers 8.21.7 availaible at ati.com[/QUOTE]

Here we go again.  :)

---

### Post by mlomker on 2006-01-23
[QUOTE=Atomac]1. The line in the first bit about removing Linux-Restricted with the -$ (uname -r) at then end. No matter how I type that it doesn't like it.[/quote]

You can't have a space after the $.  What Tickle said would also work.

> 2. I used apt-get to get the latest driver and I can select it in the xconfig but when I do x won't start.

You can't apt-get the latest driver unless something has changed.  8.16.20 is what comes with Breezy.

> 3. How am I meant to be able to download the older file for the AMD64 version from the command line?

You could use **wget** from the command-line but I don't know why you would.  Download the file from Firefox while using the basic VGA driver.  The how-to assumes a fresh load and on a fresh load you should be running on the ATI driver with slow 3D.

---

### Post by Howcomes on 2006-01-29
This ATI driver has , by far , been the bane of my linux existance :P I'm gonna try following this thread to the letter and see if i can get it to work - When i can get a definitive solution ill post any additional info i come across that may be of use. CPU: Intel Celeron 2.00GHz RAM: 512MB Graphics: ATi Radeon 9200 SE 128mb Boot loader: GRUB Other OS's installed: XP Pro Harddrive: 80GB - 9.5GB partition broken off for linux. remaining is NTFS, 150mb swap partition. (got leftover/lost in translation so made it swap for lack of anything better to do with it) ```
 Disk /dev/hda: 81.9 GB, 81964302336 bytes 255 heads, 63 sectors/track, 9964 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Device Boot Start End Blocks Id System /dev/hda1 * 1 1150 9237343+ 83 Linux /dev/hda2 1151 9951 70694001 7 HPFS/NTFS /dev/hda3 9952 9964 104422+ 5 Extended /dev/hda5 9952 9964 104359+ 82 Linux swap / Solaris 
``` I'm currently booted into XP atm, but im gonna boot into Kubuntu now and try some stuff out. will update. Update: Ok , first command listed gives errors, here is the output: ```
 howcomes@kubuntu:~$ sudo apt-get remove xorg-driver-fglrx Password: Reading package lists... Done Building dependency tree... Done The following packages will be REMOVED: fglrx-control xorg-driver-fglrx 0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded. Need to get 0B of archives. After unpacking 25.8MB disk space will be freed. Do you want to continue [Y/n]? y (Reading database ... 64400 files and directories currently installed.) Removing fglrx-control ... Removing xorg-driver-fglrx ... dpkg-divert: mismatch on divert-to when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/share/fglrx/diversions/libGL.so.1.2 by xorg-driver-fglrx' found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx' dpkg: error processing xorg-driver-fglrx (--remove): subprocess post-removal script returned error exit status 2 Errors were encountered while processing: xorg-driver-fglrx E: Sub-process /usr/bin/dpkg returned an error code (1) howcomes@kubuntu:~$ 
``` Any and all help would be much appreciated. I'm also on Freenode IRC as Howcomes.

UPDATE:

It Finally works!
```

howcomes@x1-6-00-0a-e6-b7-13-c6:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

```

I had to do format and do a clean install unfortunately, but it was a fairly new install anyway so i wasnt losing much.

---

### Post by mlomker on 2006-01-29
[QUOTE=Howcomes]Any and all help would be much appreciated. I'm also on Freenode IRC as Howcomes.[/QUOTE]

That indicates that you do not have a clean install of Breezy and I'd guess that you've previously installed drivers newer than 8.16.20.  My how-to's are written from a clean/patched install.

If the driver is already installed then you may just want to start looking at error logs instead of removing it.

---

### Post by ulgor on 2006-01-30
OK,

first I had problems, but finally it worked.

1 - I followed the instructions in the first post

   --> I still had the Mesa drivers appearing in fglrxinfo

2 - I reinstalled by using the "apt-get install" lines in the HOWTO with "--reinstall", then I also did the xorg-reconfigure

 --> Still Mesa drivers appearing in fglrxinfo!

3 - I manually changed the xorg.conf, I just replaced "ati" with "fglrx"

4 - reboot: tataa!

Now everything is fine, thanks a lot for this thread!

---

### Post by rtgh4 on 2006-02-02
:-k ok,...so where is the driver?

---

### Post by mlomker on 2006-02-02
[QUOTE=rtgh4]:-k ok,...so where is the driver?[/QUOTE]

I'm not sure what you're referring to.

---

### Post by donar73 on 2006-02-03
[QUOTE=rtgh4]:-k ok,...so where is the driver?[/QUOTE]

[www.ati.com](www.ati.com) ;)

---

### Post by Maniak on 2006-02-03
[QUOTE=ulgor]OK,

first I had problems, but finally it worked.

1 - I followed the instructions in the first post

   --> I still had the Mesa drivers appearing in fglrxinfo

2 - I reinstalled by using the "apt-get install" lines in the HOWTO with "--reinstall", then I also did the xorg-reconfigure

 --> Still Mesa drivers appearing in fglrxinfo!

3 - I manually changed the xorg.conf, I just replaced "ati" with "fglrx"

4 - reboot: tataa!

Now everything is fine, thanks a lot for this thread![/QUOTE]


Same here!!! Except in step 3 I also added the xorg.conf options from the first post to be sure it would work.

Not half as difficult as I imagined (and I went from a Nvidia card to an ATI card). 

Thanks mlomker!

---

### Post by vfxdude2 on 2006-02-06
Hey everybody -

This probably isn't in the thread of the conversation, but I just wanted to pass on some useful info...

After a solid day of hacking away at getting the fglrx driver to work, I found a "magic setting" in some obscure spot on the Internet.

Here's my situation:  I have a dual-core Intel EMT64-based machine with only one core running (haven't tried using the SMP kernel yet :-) )  I have an ATI X300.  I'm using the 2.6.12-10-amd64-generic kernel.

I was having problems getting the fglrx driver to work -- wasn't loading.  Checking the Xorg log, I saw that it was giving the error "Failed to allocate shared Z/stencil buffer!" That stopped the ATI driver from loading.


Found the magic setting to fix this (for me anyway...)

Put this in your xorg.conf under:

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"

**    Option      "EnablePrivateBackZ" "yes"**

Good luck!  Hope this helps! :-)

-vfxdude

---

### Post by x__dark on 2006-02-07
I'm having problems installing the ATI Driver, when I follow any of the HowTos I find online I get this back from "fglrxinfo":

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


I know that means I didn't do it right, but I can't figure out what's going wrong, I've done this over and over. Any suggestions?

I have an ATI Radeon 9600pro

---

### Post by mlomker on 2006-02-07
[QUOTE=x__dark]I know that means I didn't do it right, but I can't figure out what's going wrong, I've done this over and over. Any suggestions?
[/QUOTE]

You'll need to look in /var/log/Xorg.0.log and kern.log for the reason...that is a generic error that 3D isn't working.

---

### Post by Micro Rotors on 2006-02-07
OK I installed this driver and it works on the computer at work (were I installed it) but upon taking it home, after 5 seconds at the usplash login screen, it goes blank then I get a message that says: > Input signal out of range
Then the screen goes blank. How do I correct this?

Also what the heck is this driver so darn interested in my mouse and keyboard? the questions on those two topics were 5:1 about the graphics.

---

### Post by encompass on 2006-02-07
I have an ATI radeon 9100 IGP has anyone one has success with this card?
I have the driver installed... it is useing it... It says I have DRI.  But when I try to use the accelleration, like with glx-gears.  I get a lock wiht the mouse able to move but nothing else happens.  I have to hard reboot it.
I used to have accel with ati if I am not mistaken... but I can't get that back anymore.  Is there a way I can get that back?  or Better yet, get this driver working?

> jason@tabby:~$
jason@tabby:~$ lsmod | grep fglrx
fglrx                 257028  7
agpgart                35436  2 fglrx,ati_agp
jason@tabby:~$ dmesg | grep fglrx
[4294718.191000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294718.195000] [fglrx] Maximum main memory to use for locked dma buffers: 402 MBytes.
[4294718.195000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294718.215000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294718.215000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294718.215000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294718.215000] [fglrx] AGP detected, AgpState   = 0x1f00021b (hardware caps of chipset)
[4294718.216000] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[4294718.547000] [fglrx] free  AGP = 54800384
[4294718.547000] [fglrx] max   AGP = 54800384
[4294718.547000] [fglrx] free  LFB = 15724544
[4294718.547000] [fglrx] max   LFB = 15724544
[4294718.547000] [fglrx] free  Inv = 0
[4294718.547000] [fglrx] max   Inv = 0
[4294718.547000] [fglrx] total Inv = 0
[4294718.547000] [fglrx] total TIM = 0
[4294718.547000] [fglrx] total FB  = 0
[4294718.547000] [fglrx] total AGP = 16384


---

### Post by x__dark on 2006-02-07
[QUOTE=mlomker]You'll need to look in /var/log/Xorg.0.log and kern.log for the reason...that is a generic error that 3D isn't working.[/QUOTE]

> Feb  7 15:50:31 localhost kernel: [4294708.361000] [fglrx] Have to use kernel AGP support to avoid conflicts.

Could that be it? It switches back to Kernel AGP support?

---

### Post by hounddog32 on 2006-02-08
I have a 9100 IGP also, and after a lot of research, I found on the ATI site that there is no 3D accel for 9100 IGP in the fglrx driver. If you once had 3d accel, I'm surprised and impressed - I'd love to know how too!

---

### Post by encompass on 2006-02-08
[QUOTE=hounddog32]I have a 9100 IGP also, and after a lot of research, I found on the ATI site that there is no 3D accel for 9100 IGP in the fglrx driver. If you once had 3d accel, I'm surprised and impressed - I'd love to know how too![/QUOTE]
Thanks for the info on this driver... but YES I KNOW I HAD 3d support... it was not the greatest but it worked for all my games, and a few screensavers... it crashed once in a while but work while play games... just crashed after too many changes in the screensaver.  But if this driver doesn't work... then I will drop this one and try getting the old way to work... I amy jsut do a reinstall just to see the settings.:neutral: :-|

---

### Post by encompass on 2006-02-08
Alrighty!  Well, I am right about a fresh install; the dri works.  But I don't know how to get that back into my current system... I will create a howto and information on this what I have more time.\\:D/

In addition... I have also found out that if I copy the xorg.conf from one install to another... it doesn't change anything... I figure it amy have something to do with the kernel or something to that effect.

---

### Post by mlomker on 2006-02-08
[QUOTE=Micro Rotors]Then the screen goes blank. How do I correct this?
[/QUOTE]

Look in the Xorg.0.log file.  Ctrl-Alt-F2 should bring you to a login prompt.  It's misdetecting your monitor's capabilities, I suppose.

---

### Post by mlomker on 2006-02-08
[QUOTE=x__dark]Could that be it? It switches back to Kernel AGP support?[/QUOTE]

No, that's normal.  You might want to start a new thread in the Video & Sound forum and attach your logs.  Send me a PM with a link if you like.

---

### Post by Micro Rotors on 2006-02-09
Ok I installed the driver  but when I check that my ATI Radeon X300 to see if its working I get the following:

[PHP]bill@Linux:/$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)[/PHP]

I can run Slune but I would like my X300 working.


Here is my /etc/X11/xorg.conf

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
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
	Option		"XkbModel"	"pc105"
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
	Identifier	"ATI Technologies, Inc. Radeon X300 SE (RV370)"
	Driver		"ati"
	BusID		"PCI:5:0:0"
	VideoRam	256262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Emprex LM 1702"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X300 SE (RV370)"
	Monitor		"Emprex LM 1702"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

### Post by forbmj on 2006-02-10
something is wrong with mplayer after installing this new ATI driver:

It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5582 (8.21.7)


any idea?

---

### Post by Micro Rotors on 2006-02-10
forbmj

I am not sure if your post was a reply to me but I ran > xvinfo and I belive it shows that I do have xv support, here is the output. ```
sh-3.00$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 61
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 15
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SWITCHCRT" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GAMMA" (range 100 to 10000)
              client settable attribute
              client gettable attribute (current value is 1000)
      "XV_COLORSPACE" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
sh-3.00$


```

---

### Post by mlomker on 2006-02-10
[QUOTE=Micro Rotors]Ok I installed the driver  but when I check that my ATI Radeon X300 to see if its working I get the following:
[/QUOTE]

The xorg.conf is not the place to look for problems.  Look in the error logs like it says in the how-to.  I'm really starting to feel like a broken record with this.

/var/log/Xorg.0.log and kern.log

---

### Post by Cysman on 2006-02-10
Please help:

This is what I got after following your instructions.  Something seems amiss here.....

Newborn Newbie

kenoutten@ubuntubedroom:~$ sudo apt-get install xorg-driver-fglrx
Password:
Reading package lists... Done
Building dependency tree... Done
Recommended packages:
  fglrx-kernel
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 96736 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
Setting up xorg-driver-fglrx (6.8.0-8.16.20-0ubuntu16.1) ...
kenoutten@ubuntubedroom:~$ sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  nvidia-glx avm-fritz-firmware-2.6.12-10
The following NEW packages will be installed:
  linux-restricted-modules-2.6.12-10-386
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5178kB of archives.
After unpacking 13.8MB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package linux-restricted-modules-2.6.12-10-386.
(Reading database ... 96762 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.12-10-386 (from .../linux-restricted-modules-2.6.12-10-386_2.6.12.4-11.1_i386.deb) ...
Setting up linux-restricted-modules-2.6.12-10-386 (2.6.12.4-11.1) ...

kenoutten@ubuntubedroom:~$ sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200602101748
kenoutten@ubuntubedroom:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

kenoutten@ubuntubedroom:~$

---

### Post by Micro Rotors on 2006-02-11
[QUOTE=mlomker]The xorg.conf is not the place to look for problems.  Look in the error logs like it says in the how-to.  I'm really starting to feel like a broken record with this.

/var/log/Xorg.0.log and kern.log[/QUOTE]

mlomker

Sorry for making it sound like you are a broken record. I am pretty new at this and don't know much about the files that are being talked about. I am learning and I am getting there, but still I do not know what I am looking for in these files. I DID look at the how to I DID look at this file before but a lot of us don't even know what we are looking for. I DO see were there are (EE) errors and (WW) warnings but were do you fix these, how do you fix these?

We learn by asking questions WE hope others that see the problem and recognize that they had the same problem jump in and try to help ( \\:D/  ) and I thank them!!!!!

If someone tells me to look somewhere I will I am hoping and trusting that they know what could be the problem.

Well here is what this file shows, Like I said I don't know what to change, if it is in this file or not. If ANYONE knows, Please let me know. ;) 

Thanks
Bill

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux Linux 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Jan 16 17:18:08 UTC 2006 F
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 11 08:05:52 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Emprex LM 1702"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X300 SE (RV370)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
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
(II) PCI: 00:00:0: chip 10de,005e card 1019,1b51 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1019,1b51 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1019,1b51 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1019,1b51 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1019,1b51 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1019,1b51 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1019,1b51 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1019,1b51 rev a3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1019,1b51 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:07:0: chip 1102,0008 card 1102,1001 rev 00 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 4444,0016 card 0070,8003 rev 01 class 04,00,00 hdr 00
(II) PCI: 05:00:0: chip 1002,5b60 card 1092,0470 rev 00 class 03,00,00 hdr 80
(II) PCI: 05:00:1: chip 1002,5b70 card 1092,0471 rev 00 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0204 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:1), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:2), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:24:3), (-1,-1,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI: (1:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf8000000/26
(--) PCI:*(5:0:0) ATI Technologies Inc unknown chipset (0x5b60) rev 0, Mem @ 0xd8000000/27, 0xfd8f0000/16, I/O @ 0x6c00/8
(--) PCI: (5:0:1) ATI Technologies Inc unknown chipset (0x5b70) rev 0, Mem @ 0xfd8e0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[3] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[4] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[5] -1	0	0xfd8f0000 - 0xfd8fffff (0x10000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
	[9] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[24] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xfd8e0000 - 0xfd8effff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[1] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[2] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[3] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[4] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[5] -1	0	0xfd8f0000 - 0xfd8fffff (0x10000) MX[B](B)
	[6] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[7] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[8] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
	[9] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[11] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[12] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[13] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[14] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[16] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[17] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[18] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[19] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[21] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[24] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xfd8e0000 - 0xfd8effff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfd8f0000 - 0xfd8fffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfd8e0000 - 0xfd8effff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[19] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[20] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[21] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[22] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[29] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[32] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
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
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 6.5.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4

```

---

### Post by Micro Rotors on 2006-02-11
the file was so long I had to split it up. Here is the second half.

```
(II) ATI: ATI driver (version 6.5.6) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9200PRO 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9700 NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI RADEON 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireGL D1100 (RV370) 5B65 (PCIE),
	ATI Radeon Mobility M300 (M22) 5460 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI RADEON XPRESS 200 Series,
	ATI RADEON XPRESS 200M Series, ATI FireGL V5000,
	ATI MOBILITY FireGL V5000, ATI MOBILITY FireGL V5000,
	ATI MOBILITY RADEON X700, ATI MOBILITY RADEON X700,
	ATI RADEON X700 PRO, ATI RADEON X700 XT, ATI RADEON X700,
	ATI RADEON X700 SE, ATI RADEON X700 SE,
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI RADEON X800 SE,
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V7200 (R423) UQ (PCIE), ATI FireGL V5100 (R423) UR (PCIE),
	ATI FireGL V7100 (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100,
	ATI MOBILITY FireGL V5100, ATI MOBILITY RADEON X800,
	ATI MOBILITY RADEON X800 XT, ATI RADEON X800, ATI RADEON X800 XL,
	ATI RADEON R430 SE, ATI RADEON R430 XTP, ATI RADEON R480 4P,
	ATI RADEON R480 GL 16P, ATI RADEON R480 SE, ATI RADEON X850 PRO,
	ATI RADEON X850 XT, ATI RADEON X850 XT Platinum Edition,
	ATI RADEON X850 PRO, ATI RADEON X850 SE, ATI RADEON X850 XT,
	ATI RADEON X850 XT Platinum Edition
(II) Primary Device is: PCI 05:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X300 SE (RV370)".
(WW) ATI:  PCI Mach64 in slot 5:0:1 could not be detected!
(WW) RADEON: No matching Device section for instance (BusID PCI:5:0:1) found
(--) Chipset ATI Radeon X300 (RV370) 5B60 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfd8f0000 - 0xfd8fffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfd8e0000 - 0xfd8effff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[19] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[20] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[21] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[22] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[25] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[26] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[27] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[29] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[30] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[32] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/X11R6/lib/modules/drivers/radeon_drv.o
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 4.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02afff (0x1000) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02e000 - 0xfe02e0ff (0x100) MX[B]
	[9] -1	0	0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
	[10] -1	0	0xfd8f0000 - 0xfd8fffff (0x10000) MX[B](B)
	[11] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[12] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[13] -1	0	0xfd8e0000 - 0xfd8effff (0x10000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac3f (0x40) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[32] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[33] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[34] -1	0	0x0000fc00 - 0x0000fc1f (0x20) IX[B]
	[35] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xfd8f0000
(II) RADEON(0): PCI bus 5 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "UseFBDev" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.7
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon X300 (RV370) 5B60 (PCIE)" (ChipID = 0x5b60)
(--) RADEON(0): Linear framebuffer at 0xd8000000
(II) RADEON(0): Video RAM override, using 256262144 kB instead of 131072 kB
(**) RADEON(0): VideoRAM: 256262144 kByte (64 bit DDR SDRAM)
(II) RADEON(0): PCI card detected
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: DEL  Model: 515b  Serial#: 810701914
(II) RADEON(0): Year: 1999  Week: 10
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 29
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) RADEON(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) RADEON(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) RADEON(0): #5: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 28.3 MHz   Image Size:  388 x 291 mm
(II) RADEON(0): h_active: 720  h_sync: 738  h_sync_end 846 h_blank_end 900 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 388  v_sync_end 390 v_blanking: 449 v_border: 0
(II) RADEON(0): Serial No: 55347B0RTZ39
(II) RADEON(0): Monitor name: DELL D1626HT
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 107 kHz,
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=25000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): Emprex LM 1702: Using hsync range of 30.00-65.00 kHz
(II) RADEON(0): Emprex LM 1702: Using vrefresh range of 50.00-75.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(WW) (640x480,Emprex LM 1702) mode clock 25.2MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(WW) (640x480,Emprex LM 1702) mode clock 31.5MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(WW) (640x480,Emprex LM 1702) mode clock 31.5MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(WW) (800x600,Emprex LM 1702) mode clock 36MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(WW) (800x600,Emprex LM 1702) mode clock 40MHz exceeds DDC maximum 0MHz
(WW) (400x300,Emprex LM 1702) mode clock 20MHz exceeds DDC maximum 0MHz
(WW) (800x600,Emprex LM 1702) mode clock 50MHz exceeds DDC maximum 0MHz
(WW) (400x300,Emprex LM 1702) mode clock 25MHz exceeds DDC maximum 0MHz
(WW) (800x600,Emprex LM 1702) mode clock 49.5MHz exceeds DDC maximum 0MHz
(WW) (400x300,Emprex LM 1702) mode clock 24.75MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "400x300" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "512x384" (vrefresh out of range)
(WW) (1024x768,Emprex LM 1702) mode clock 65MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(WW) (1024x768,Emprex LM 1702) mode clock 75MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(WW) (1024x768,Emprex LM 1702) mode clock 78.8MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(WW) (1280x960,Emprex LM 1702) mode clock 108MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(WW) (1280x1024,Emprex LM 1702) mode clock 108MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(WW) (832x624,Emprex LM 1702) mode clock 57.284MHz exceeds DDC maximum 0MHz
(WW) (416x312,Emprex LM 1702) mode clock 28.642MHz exceeds DDC maximum 0MHz
(WW) (1280x768,Emprex LM 1702) mode clock 80.14MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(WW) (1280x800,Emprex LM 1702) mode clock 83.46MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(WW) (1152x768,Emprex LM 1702) mode clock 64.995MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(WW) (1400x1050,Emprex LM 1702) mode clock 122MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(WW) (1440x900,Emprex LM 1702) mode clock 108.84MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(WW) (1600x1024,Emprex LM 1702) mode clock 106.91MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(WW) (1680x1050,Emprex LM 1702) mode clock 147.14MHz exceeds DDC maximum 0MHz
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (width too large for virtual size)
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) RADEON(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) RADEON(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) RADEON(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) RADEON(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) RADEON(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) RADEON(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) RADEON(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) RADEON(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) RADEON(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) RADEON(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) RADEON(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) RADEON(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) RADEON(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) RADEON(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) RADEON(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) RADEON(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(--) RADEON(0): Display dimensions: (380, 290) mm
(--) RADEON(0): DPI set to (85, 89)
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
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) RADEON(0): Depth moves disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/X11R6/lib/modules/libshadowfb.a
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) RADEON(0): Page flipping disabled
(!!) RADEON(0): For information on using the multimedia capabilities
```

---

### Post by SWAT on 2006-02-12
Hmm, this topic is about the ATI drivers in the repository, right? I'm pretty much a hardass and [have written a HowTo](http://www.zwhlug.nl/content/ati_ati_driver_8_18_6_installation_on_ubuntu_breezy_5_10) for those of you, who wish to install the ATI drivers from the ATI site. 
Note: These drivers *might* break, but you'll always be able to use the latest drivers :D

---

### Post by mlomker on 2006-02-12
[QUOTE=SWAT]Hmm, this topic is about the ATI drivers in the repository, right? I'm pretty much a hardass and [have written a HowTo](http://www.zwhlug.nl/content/ati_ati_driver_8_18_6_installation_on_ubuntu_breezy_5_10) for those of you, who wish to install the ATI drivers from the ATI site. 
Note: These drivers *might* break, but you'll always be able to use the latest drivers :D[/QUOTE]

I also have a how-to for the latest drivers.  It is on the ATIwiki link in my sig and also on [this thread]("http://www.ubuntuforums.org/showthread.php?t=76116").

If the Breezy driver works it's a lot less complicated to stick with it, imo.

---

### Post by mlomker on 2006-02-12
[QUOTE=Cysman]
kenoutten@ubuntubedroom:~$ sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200602101748

kenoutten@ubuntubedroom:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
[/QUOTE]

Can I assume that rebooted between those two commands?  If so then you'll need to look in /var/log/Xorg.0.log and kern.log for error messages.

---

### Post by mlomker on 2006-02-12
[QUOTE=Micro Rotors]the file was so long I had to split it up. Here is the second half.[/QUOTE]

The only error that I wonder about it the one about buffers.  The rest of it looked okay.  What are you getting in kern.log when the driver loads?

I'm also wondering if you're actually using Breezy's 8.16.20 driver or a new one?  I'm not sure that I'd even try using the older driver because it predates the X-series cards by quite a while, I believe.  You could give the [latest driver]("http://www.ubuntuforums.org/showthread.php?t=76116") a try.

---

### Post by Micro Rotors on 2006-02-13
[QUOTE=mlomker]The only error that I wonder about it the one about buffers.  The rest of it looked okay.  What are you getting in kern.log when the driver loads?[/QUOTE]

The /var/log/kern.log file is completly blank, not a letter on it.



> I'm also wondering if you're actually using Breezy's 8.16.20 driver or a new one?  I'm not sure that I'd even try using the older driver because it predates the X-series cards by quite a while, I believe.  You could give the [latest driver]("http://www.ubuntuforums.org/showthread.php?t=76116") a try.

The latest driver from ATI is Version: 8.22.5 I guess I could give it a try after I hear from you about my /var/log/kern.log file being blank.

Thanks mlomker ;)

---

### Post by Micro Rotors on 2006-02-15
Ok I went ahead and updated to the latest driver and it works just fine, 

Thanks to all!
Bill

---

### Post by ilbahr on 2006-02-17
Hi 

First thanks for a great howto. Running it with the latest fglrx driver now here is the o/p of fglrx info

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5642 (8.22.5)

running though fgl_glxgears 
I get a crappy ouput and this error message

FGLTexMgr: open of shared memory object failed (Read-only file system)
__FGLTexMgrCreateObject: __FGLTexMgrSHMmalloc failed!!!
fglX11AllocateManagedSurface: __FGLTexMgrCreateObject failed!!

:evil: 

anyone knows what might cause that or how to fix it. Is it an option i need to enable in xorg.conf?

Running ati 9600 64 MB on a notebook here

Thanx again for your help :D

---

### Post by mlomker on 2006-02-17
[QUOTE=ilbahr]FGLTexMgr: open of shared memory object failed (Read-only file system)[/QUOTE]

I searched Google and found quite a few references.  [Look at this]("http://ubuntuforums.org/showthread.php?p=102546#post102546").

---

### Post by ilbahr on 2006-02-18
[QUOTE=mlomker]I searched Google and found quite a few references.  [Look at this]("http://ubuntuforums.org/showthread.php?p=102546#post102546").[/QUOTE]

Oh my I am really lazy or do not know how to efficienly use google yet. Thank you for putting me on the right path I found a

tmpfs     /dev/shm     tmpfs     defaults,ro     0 0

:-k 

line in my fstab file put there by the ati installer.

Just changed the defaults from defaults,ro to defaults. It was set to read only (do not know why though :-k ) so the new line is

tmpfs     /dev/shm     tmpfs     defaults     0 0



Now the installer also created the /dev/shm device which is owned by whoever installed the file so I had to change the ownership so it belongs to root and such that all user who can use video acceleration can use it.

sudo chown -R root:video /dev/shm

ps /dev/shm is a directory and the R options to change ownership of all files under this directory

Now it is crazy getting 450 frms/sec with the fgl_glxgears

:D

ps: perhaps a note in the howto can help other users like me who had this problem. :D


Now to look for a solution to the crapy output i get if i use the gdmflexiserver (new login) on my laptop. [-( 

ps gdmflexiserver -nl thought works (so works if using xnest but not if a new session is initiated)

---

### Post by Micro Rotors on 2006-02-18
Hmmm, I noticed that after installing the new driver 8.22.5 my mythtv got messed up.

---

### Post by bluevoodoo1 on 2006-02-19
[QUOTE=Olav]Okay, I' m back. Back to VESA, that is :(

But **old** problems started again, causing the screen to freeze completely except for the mouse cursor.

[/QUOTE]

This is happening to me as well. Xorg config file looked fine, fglrxinfo stated it was the ATI 9100 and dmesg |grep fglr gave no errors. But as soon as I run glxgears or throw in a DVD everything freezes but the mouse. I have the 2.6.12-10-386 kernel and ATI 9100 on board video. (Is it because it's on board video the problem?)

---

### Post by hounddog32 on 2006-02-20
As I found, if you look on the ATI website, you'll see that the 9100 and 9100IGP are not supported for 3D by the FGLRX driver. Unfortunately, that means that the PC will just lock when you try to run GLX gears or anything else that relys on 3D rendering. To get a workable system you'll need to uninstall the driver and use the default ATI driver - which works, just not in 3D.

---

### Post by cronholio on 2006-02-20
> As I found, if you look on the ATI website, you'll see that the 9100 and 9100IGP are not supported for 3D by the FGLRX driver.

And I've been trying forever to get it to work. Unfortunately, I own an ASUS Pundit (like bluevoodoo1) with an onboard Radeon 9100 and that thing does not even have a free AGP slot. I'm not a heavy gamer but being stuck with 2D sucks.

I found this project, they create open source ATI drivers: [http://dri.freedesktop.org](http://dri.freedesktop.org)

They say that: 

> There is support for 2D and 3D acceleration for the IGP chipsets in DRI and Mesa CVS.

And also that:

> Open source 3D acceleration is available on all Radeons up to and including the 9250 (rv280). (...) the 8500 through 9250 are supported by the r200 DRI driver.

Anyone knows anything about that driver? I'm a little reluctant to install it for fear of f**king up my system.

---

### Post by mlomker on 2006-02-21
[QUOTE=ilbahr]Oh my I am really lazy or do not know how to efficienly use google yet.[/QUOTE]

Learning to use search engines well is a learned skill--I do IT for a living, so I've had a lot of practice...out of necessity.

---

### Post by mlomker on 2006-02-21
[QUOTE=cronholio]Anyone knows anything about that driver? I'm a little reluctant to install it for fear of f**king up my system.[/QUOTE]

The ATI driver that Ubuntu provides uses MESA for software 3D.  It's basically the same thing as that project.

As an aside, 9100's are so slow that it wouldn't be much faster than MESA even if you had hardware accelleration...it's simply an old card.

---

### Post by flummoxed on 2006-02-21
OK... so what exactly ARE the linux-restricted-modules? I'm running the 2.6.15 vanilla kernel, installed over the 2.6.12-10-k7 kernel. I installed the 8.22.5 drivers, in hopes that they would work better than the 8.16.20 drivers. Neverwinter nights won't even boot any more, saying "Failed to initialize graphics." Counterstrike 1.6 only works with software rendering. 

When I try to use apt-get to install the 2.6.15 restricted modules, I get an error saying it can't find them. What do they do? Where can I find them? Will it make my video card work?

---

### Post by mlomker on 2006-02-22
[QUOTE=flummoxed]When I try to use apt-get to install the 2.6.15 restricted modules, I get an error saying it can't find them. What do they do? Where can I find them? Will it make my video card work?[/QUOTE]

It is a set of 3rd party drivers that Ubuntu packages for each kernel version.  Your kernel is not Ubuntu so they won't have a package for you.  Not only will they not make this how-to work but, as I stated, they cannot be installed.

I'm not interested in supporting non-Ubuntu kernels.  Supporting plain jane installs can be challenging enough.  There are plenty of posts about getting the newer kernels to work on the Rage3D board.  I know when .15 was first released it wouldn't work out of the box and required some hacks.  I'm not sure if that is still the case.

---

### Post by Hellaxe on 2006-02-27
Well... Here i am again.
I' justs can't instal the drivers for the Mobility 9000 M7 LW that cames with my IBM R51 laptop.
I tried this how-to and the other one about the latest drivers.
The same problem occurs: the **_fglrx.ko module_** isn´t loaded to the kernel.
I looked in the ATI website and that stupid card is suported by the drivers, at least all the 9000 and i assume that goes for mine too.

What should i do?

Thanks again.

---

### Post by mlomker on 2006-02-27
[QUOTE=Hellaxe]I looked in the ATI website and that stupid card is suported by the drivers, at least all the 9000 and i assume that goes for mine too.
[/QUOTE]

It isn't supported.  The M7 is actually a 7500 chipset.

---

### Post by Hellaxe on 2006-02-27
Thank´s mlomker.
I've figure it out 2 or 3 hours after i posted the doubt.
Sorry for the late answer.

---

### Post by cronholio on 2006-02-28
> As an aside, 9100's are so slow that it wouldn't be much faster than MESA even if you had hardware accelleration...it's simply an old card.

Well, HW accelleration works in Windows and I can run Glest smoothly. It's unplayable in Linux w/o accelleration. :-(

---

### Post by h4ck3r on 2006-03-01
Ok, I got 3d accel working on my M22 ATI Graphics card, but know I have this totaly wierd problem, whenever I try to start totem player to play an mp3 (because I like the eye candy it has for music) it gives me this error.

The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.

There are no other music or movie players open or anything of the type. I have gone to the menu and messed with Multimedia Systems Selector but it didn't help any :(. It would be awsome if I could figure this problem out.

I used this page to install it, I know there are later drivers but I am not sure if they will work with my graphics card if anyone knows if they will please tell me.

[http://ubuntuforums.org/showthread.php?p=408111](http://ubuntuforums.org/showthread.php?p=408111)

Thanks for any help, :-k 
H4ck3r

---

### Post by cronholio on 2006-03-01
@h4ck3r: That has nothing at all to do with the ATI driver. The error message is a bit confusing. It's a common and widely discussed problem. Have a look here:

[http://ubuntuforums.org/showthread.php?t=120591](http://ubuntuforums.org/showthread.php?t=120591)

---

### Post by h4ck3r on 2006-03-01
Well, it was working before hand and after installing it it stopped working...

Thanks alot

---

### Post by goraperas on 2006-03-09
Hi,

I am following this guide [http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g/]("http://www.martinhenze.de/2006/01/03/ubuntu-linux-on-fujitsu-siemens-amilo-m1437g/") to install Ubuntu on my Fujitsu-Siemens Amilo M1437G.

My problem now is that I cannot load the X. I tried to follow the how-to of the first post in this thread but either when I run "apt-get remove xorg-driver-fglrx" or "apt-get remove xorg-driver-fglrx" I get an error:

"The packet has not been found"

I suppose that may be because I don't have Internet connection yet??

Thanks,

goraperas

---

### Post by cronholio on 2006-03-10
No, that's because you don't have it installed. Just disregard the message and continue as described in the guide.

---

### Post by goraperas on 2006-03-10
[QUOTE=cronholio]No, that's because you don't have it installed. Just disregard the message and continue as described in the guide.[/QUOTE]

Hi,

I already did that. I wanted to say that the command:

apt-get install xorg-driver-fglrx

also get the same result:

The packet has not been found

Any ideas?

Thanks,

goraperas

---

### Post by goraperas on 2006-03-10
Hi again,

This is exactly what I get:

```
mymachine:~# apt-get install xorg-driver-fglrx
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package xorg-driver-fglrx
```

Thanks for any help,

goraperas

---

### Post by simulant on 2006-03-10
First of all I'd just like to say thanks to mlomker! I got the driver (kinda) working today, after a couple of weeks of pain with installs and reinstalls...

weird thing:

fglrxinfo is ok. fgl_glxgears gives ~400 FPS, but it also give me somekind of distorted horizontal line on the screen. i also tried scorched3d and it looked crazy! it ran smooth but it didn't look like scorched3d... just fragments of polygons scattered around the screen!

i havn't read about this behaviour, so maybe i'm unique after all :neutral: .
maybe it has to do with the xorg.conf-file?

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
	Load	"extmod"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event2"   #USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event2"   #USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event2"   #USB ONLY
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "Device"
	Identifier	"ATI RADEON 9600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
 	VideoRam 	256262144
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9600"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    #For non-LCD tablets only
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by cronholio on 2006-03-11
@goraperas: Well, you do need internet for installing it. I don't think the driver is on the Ubuntu CD.

---

### Post by Robgould on 2006-03-11
ok, I guess I need help.  I have tried severl how to's now and no luck.  Here is what I get from the console.  I will add my xorg.conf too.  Any help at all would be appreciated.  I am using a Toshiba Satellite Laptop.

When I ran the fglrxinfo, my procesor scaled to 100% and was over 60% loaded.  I have a dual core p4 rated at 3.46 GHZ.  That kind of load is crazy.  Everytime my screensaver kicks on my computer will get hot and shut down within 10 minutes.  I really need to get this resolved.

Thanks in advance.

```

rgould@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

rgould@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
1733 frames in 5.4 seconds = 318.696 FPS
1680 frames in 5.4 seconds = 312.063 FPS
1680 frames in 5.4 seconds = 312.866 FPS
1680 frames in 5.4 seconds = 311.962 FPS
1680 frames in 5.4 seconds = 312.438 FPS
1680 frames in 5.4 seconds = 312.595 FPS
1680 frames in 5.4 seconds = 312.670 FPS
1680 frames in 5.4 seconds = 312.213 FPS
1627 frames in 5.3 seconds = 304.168 FPS
1590 frames in 5.2 seconds = 307.198 FPS
1590 frames in 5.2 seconds = 307.219 FPS
1628 frames in 5.4 seconds = 298.982 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

``` 

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
    Driver        "fglrx"
    BusID        "PCI:1:5:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-51
    VertRefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by wzzrd on 2006-03-13
I hope I'm putting this in the right place.

I followed the howto on page 1 in installing the fglrx driver on my breezy system a couple of days ago. All went fine, but apparently, there is a discrepancy between my newly built driver and my kernel. I can only load it, if I modprobe it as follows:

```
modprobe --force-vermagic fglrx
```

Part of the cause is the fact that the module is built with gcc-4.0.2 and the kernel is not. The version of the compiler is added to the vermagic and those numbers are obviously not the same. Therefore I have to force the module into my kernel with the above command.

Anyway, to make a long story short: I need a command to load that module automagically at boot. I need a way to load the module *with* that --force-vermagic bit added to it. And now my question: how? I don't think Ubuntu has a /etc/conf.d/local.start file like Gentoo, so I am at a loss here.

:)

---

### Post by mlomker on 2006-03-15
[QUOTE=goraperas]
E: Couldn't find package xorg-driver-fglrx[/CODE]
[/QUOTE]

Make sure that you've updated your sources.list and then do a **sudo apt-get update** first.  You need to be connected to the Internet.  There are some ways around that by downloading a file from another connected machine, but this how-to assumes an Internet connection.

---

### Post by mlomker on 2006-03-15
[QUOTE=simulant]i also tried scorched3d and it looked crazy! it ran smooth but it didn't look like scorched3d... just fragments of polygons scattered around the screen![/QUOTE]

I don't want to support applications in this thread, just the driver install.  You might want to search and/or make a post on an appropriate thread (gaming boards).  The ATI forum is also a good bet.

---

### Post by mlomker on 2006-03-15
[QUOTE=wzzrd]Part of the cause is the fact that the module is built with gcc-4.0.2 and the kernel is not.[/QUOTE]

I assume you are using a newer driver than the one included with Ubuntu because it is compiled with the correct compiler.  You could try putting that command in /etc/modules, but I'd recommend that you recompile it with the proper compiler instead.

Put this in your /etc/bash.bashrc (and make sure you have that compiler installed, of course):

export CC=/usr/bin/gcc-3.4

---

### Post by Zarteg on 2006-03-19
35 Pages of complaints, doesn't works, can't finds. - still no answers from what I could find.
 
Makes a good arguement for Windows users, well not that bad maybe but damned close. Video in Windows just works - unfortunately security and very little else does.

As a Fedora User for a long time, I have really come to hate Ubuntu. The OS itself is kind of cool, but I have yet to see "Support"
 
I noticed in Fedora Posts the answers are usually exceptionally well thought out, and if someone misses something in an answer... someone else will always jump in to point out the missed piece.
 
Ubuntu on the other hand, pages and pages of whining, with some half baked answers that sometimes may or may not work. I feel like I am in a forum of 14 year olds with the odd post from someone who actually gets it.
 
Alright, rant released... (sorry about this but I am fed up and pis$ed off)
 
I tried to follow this install your ATI driver how to ....
[http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
 
All kinds of @##@ gone wrong.... course no answers to why, and from what I gather in my reading I am likely the only user on the planet with these problems .... 
 
Ok well what the heck I might as well post too.

Machine is a Compaq Evo N600C
2.6.12-10-686 (Kernel - Breezy)

LSPPCI
0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Texas Instruments PCI1420
0000:02:03.1 CardBus bridge: Texas Instruments PCI1420
0000:02:04.0 Communication controller: Lucent Microelectronics LT WinModem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
0000:02:09.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)

Following along the tutorial - everything goes well until I get here:

$ sudo dpkg -i xorg-driver-fglrx_8.23.7-1_i386.deb
(Reading database ... 118741 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 6.8.0-8.16.20-0ubuntu16.1 (using xorg-driver-fglrx_8.23.7-1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx ...
dpkg: error processing xorg-driver-fglrx_8.23.7-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libGL.so.1.2', which is also in package libgl1-mesa
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 xorg-driver-fglrx_8.23.7-1_i386.deb

Then it just continues to error as I move on to other steps

$ sudo dpkg -i fglrx-control_8.23.7-1_i386.deb
(Reading database ... 118741 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.23.7-1_i386.deb) ...
dpkg: error processing fglrx-control_8.23.7-1_i386.deb (--install):
 trying to overwrite `/usr/share/applnk/fireglcontrol.kdelnk', which is also in package fglrx-4-3-0
Errors were encountered while processing:
 fglrx-control_8.23.7-1_i386.deb

YES I AM IN THE DIRECTORY WHERE THESE PACKAGES ARE LOCATED.

~$ sudo dpkg -i fglrx-kernel-source_8.23.7-1_i386.deb
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 118741 files and directories currently installed.)
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.23.7-1_i386.deb) ...
Setting up fglrx-kernel-source (8.23.7-1) ...

This part seems to go well - ah well maybe like windows 33% is a good number?

$ sudo dpkg -i fglrx-kernel-source_8.23.7-1_i386.deb
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 118741 files and directories currently installed.)
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.23.7-1_i386.deb) ...
Setting up fglrx-kernel-source (8.23.7-1) ...
dsmith@evo:~$ sudo m-a prepare
Kernel headers available in /usr/src/linux
 
OK two in a row worked WOO HA

$ sudo m-a update

Updated infos about 68 packages

Wow another one worked!

$ sudo m-a update

Updated infos about 68 packages

Wow another worked? kewl - well maybe - cuz lets face it stuff failed earlier, and I have not a clue if that may make the whole house of cards cave in.

sudo aticonfig --initial
aticonfig: error while loading shared libraries: libfglrx_pp.so.1: cannot open shared object file: No such file or directory

Big surprise - maybe its to remind me of how much better this is than Windows

sudo fglrxconfig
sudo: fglrxconfig: command not found

I guess I don't really need this anyway right? 

$ sudo fglrxinfo

sizeof(RADEONDRIRec) == 100, devPrivSize 100
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20050528 AGP 1x NO-TCL
OpenGL version string: 1.2 Mesa 6.3.2

Note the sudo command in this first since it doesn't do anything when logged in as plain old me.
 
If I sound pissed off and frustrated, its because I have been playing with this crap for days.... and after hours and hours of reading, I still don't understand squat about whats going on.

Not very Tech friendly much less user friendly is it?

Now I can reboot, but if I do, X will probably fail, and I will probably have to reconfigure xorg.conf to even get to a desktop.
 
All being said - maybe its because of this:
with the exception of the 9100 IGP, M6 Mobility, and possibly others 
 
Who knows, because of course while the problem with these cards is pointed out, there is no alternative answer - at least from what I can see, and I am not seeing straight after days of reading about this problem.

---

### Post by Zarteg on 2006-03-19
Part 2 of 2

Here is the output from my Xorg.0.log

Course that won't fit here, so I guess I am not including it

I am a knob ... I used Windows for years, and while there is no security or reliability at least Video and Sound drivers were always a piece of cake.

Perhaps the brain damage I experienced with all those years of Windows has made me to stupid to understand this.
 
Anyone know a good lawyer willing to sue MS for this medical condition that they have inflicted?

If you can help with this COOL! I (and I am sure many others) appreciate your time and intelligent comments.
 
Going to call a Neuro Surgeon now and make an appointment. I will check for a response later.
 
Drooling continues.
 
PS: When I do finally get back in to Ubuntu desktop (after regenerating the xorg.conf on an init 3 prompt) it seems as though my frame rate is way higher.
 
I am getting over 400 FPS versus about 120 prior to half baked install, which is a LOT better so maybe I should just shut up and be thankful I have a gui??

---

### Post by Pettman on 2006-03-20
Followed this how-to and still no 3d, I've been looking around pretty much and this is the info I think will be needed to sort it out.
```
pettman@ubuntu:~$ lsmod | grep fglrx fglrx                 245412  0
agpgart                32328  2 fglrx,via_agp
pettman@ubuntu:~$ dmesg | grep fglrx [4294717.411000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294717.418000] [fglrx] Maximum main memory to use for locked dma buffers: 930 MBytes.
[4294717.418000] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[4294717.431000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294717.431000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294717.431000] [fglrx] Kernel AGP support doesn't provide agplock functionality.
[4294717.431000] [fglrx] AGP detected, AgpState   = 0x1f000a0f (hardware caps of chipset)
[4294717.432000] [fglrx:firegl_unlock] *ERROR* Process 7854 using kernel context 0
```From /var/log/Xorg.0.log ```
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENOMEM"
(EE) fglrx(0): cannot init AGP
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8b6f000 at 0xb7b6f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Addition:
I fixed it :). By adding these 2 lines in /etc/modules ```
agpgart
via_agp
```
But now the comp hangs when I try to run anything that uses OpenGL :(

---

### Post by japs_it88 on 2006-03-24
Problably someone has already said this:

I was one of those who installed the drivers followind the instructions and i was still getting something similar to this:
```
olav@dinges:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
```

I casually found out that in order to configure the xorg.conf file for ATI you first have to run sudo fglrxconfig

I know have this output:
```
jacopo@studio:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200SE DDR Generic
OpenGL version string: 1.3.1010 (X4.3.0-8.16.20)

```

Looks better, doesn't it?

---

### Post by sistemico on 2006-03-28
Thank you mlomker,

We installed properly an ATI X200 Radeon on a compaq presario v2415 la (Latinamerica) laptop following your How-to guide.
1024x768 resolution is working fine (Ubuntu Breezy).

sistemico.

---

### Post by HighTemplar on 2006-03-29
Sistemico:

how did you install that driver? it's the same i've downloaded from ATi website? (ati-driver-installer-8.23.7-i386)
I have the same laptop and however the GUI resolution is correct (1280x800), 3D is quite slow.

---

### Post by octothorpe on 2006-04-18
will this driver set work with my x800 in my laptop?

---

### Post by salocinbake on 2006-04-19
If you own a Emachine M6810 with an ATI 9600, or the equivalent on Gateway, save yourself 6 hours of search, just back up your etc/x11/xorg.conf and use the one below.

I wanted 1280X800 res, I finally copied the result of xvidtune in the xorg.conf file. Using Ubuntu 5.10

fglrx driver will be active. I assume you installed it before use

So you will have 1280X800 1024X768 800X600 640X480 res, with 60hz and 3D accel.  Good luck!

fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

N.B. If you upgrade to Dapper, make sure you return to your back up version before upgrading. The x window crash after install.


Salo

                                                                     
                                                                     
                                                                     
                                             
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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/X11/fonts/misc"
    FontPath    "/usr/share/X11/fonts/cyrillic"
    FontPath    "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/X11/fonts/Type1"
    FontPath    "/usr/share/X11/fonts/CID"
    FontPath    "/usr/share/X11/fonts/100dpi"
    FontPath    "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load    "GLcore"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"    
      SubSection "extmod"
                Option "omit xfree86-dga"
      EndSubSection
        Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Modeline    "1280x800"     71.00   1280 1328 1360 1440    800  802  808  823 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1280x800"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1280x800"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection

---

### Post by lzfy on 2006-04-20
Hi, I have a laptop with an ATI Mobility Radeon x700 card and I'm running Kubuntu dapper drake flight 6 with the latest updates. Should I just follow your tutorial and install the drivers? I really need help because I'm new to Linux.

---

### Post by GsmCyber on 2006-04-28
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

Can someone help me to solve this problem?!

I can't run 3ddesk with this problem :(

I have a ATI X700 on an amd64

---

### Post by mirak63 on 2006-05-01
anyone know how to make work nforce2 chipset along 9600pro ?
I can't enable dri.

---

### Post by EdThaSlayer on 2006-05-28
1827 frames in 5.1 seconds = 359.687 FPS
1200 frames in 5.4 seconds = 223.225 FPS
956 frames in 5.3 seconds = 180.617 FPS
1200 frames in 5.1 seconds = 233.807 FPS
1440 frames in 5.2 seconds = 275.512 FPS
1800 frames in 5.1 seconds = 352.165 FPS
1680 frames in 5.3 seconds = 318.433 FPS
1080 frames in 5.2 seconds = 206.118 FPS
840 frames in 7.4 seconds = 113.792 FPS
1080 frames in 5.3 seconds = 204.035 FPS
1080 frames in 7.9 seconds = 136.609 FPS
720 frames in 5.2 seconds = 138.448 FPS
1080 frames in 5.0 seconds = 213.869 FPS
1080 frames in 5.1 seconds = 211.256 FPS


i get such low scores using that glrxgears -iacknowledgethathisisnotabenchmark

while i have a ATI radeon 9600 128 mb of RAM running at 400 mhz!!

---

### Post by spliterz on 2006-05-28
I run this:

> sudo apt-get install xorg-driver-fglrx 

and I get:

> Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 122501 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/lib/modules/dri/fglrx_dri.so', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


if I try:

> sudo apt-get remove xorg-driver-fglrx

I get:

> Reading package lists... Done
Building dependency tree... Done
Package xorg-driver-fglrx is not installed, so not removed
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  fglrx-control: Depends: xorg-driver-fglrx but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).


and if I try:

> sudo apt-get -f install

I get:

> Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/8325kB of archives.
After unpacking 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 122501 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/lib/modules/dri/fglrx_dri.so', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xorg-driver-fglrx_6.8.0-8.16.20-0ubuntu16.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone please help me sort this out.  Package manager is throwing upthe same 'trying to overwrite' error.

---

### Post by SShadow on 2006-05-28
Well, I am happy to say after spending a couple hours at this, I finally managed to get my ATi card working.  Even on installation, X wasn't working - it wasn't until I booted back into Windows and found out that I could put VESA in my xorg.conf in order to get X up and running that I started making a little headway.
For some reason, following the very first post in this thread (three times!) just wouldn't get things rolling for me.  Then I saw in a later post a link to this page (which pretty much says the same darned stuff, as far as I can tell) 
[http://http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide]("http://http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide")

I followed method one, and this time it worked.  The only difference I noticed that I did this time around was I deselected the **int10a** right from the **sudo dpkg-reconfigure xserver-xorg** instead of editing the xorg.conf file after the fact.

Now when I do the **fglrxinfo** command I am greeted with:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X850 PRO Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

And the [B]glxgears -iacknowledgethatthistoolisnotabenchmark
[/B] get me the following:
> 40642 frames in 5.0 seconds = 8128.330 FPS
39457 frames in 5.0 seconds = 7891.340 FPS
40829 frames in 5.0 seconds = 8165.658 FPS
40830 frames in 5.0 seconds = 8165.839 FPS

All I can say is Thank you guys for all your hard work helping us n00bies out.  I've been running Ubuntu at work, but it is on an older P3 machine, and I had no issues with the moldy oldy hardware...  My home machine is just a bit newer -
AMD64 3000+ with a Saphire Radeon GTO2 flashed to 16pipelines.

Anyways, keep up the good work - I know I am benefitting from it!

---

### Post by fantysun on 2006-07-11
Thank you very much!
I'll have a try .

---

### Post by Onyros on 2006-07-29
I installed ATi's drivers following Method #2 on this site ---> [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

And now, glxgears gives me a very bad result, just around 135 fps (when I had around 4000 fps with the previous version of the drivers, installed with the exact same method)... but the strange things is that fgl_glxears gives me the same type of result I had with the previous version of the ATi drivers (720 fps with both drivers), confirmed by trying Enemy Territory out with good performance.

Can anyone try guessing what's up with this, why is glxgears giving me such low results? It's a Mobile X700 with 128MB.

---

### Post by zzhnet on 2006-10-19
[QUOTE]
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux phoenix-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 18 19:28:56 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "A71f"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X550 (RV370)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1458,a102 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1458,5004 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1458,5004 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1458,5004 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1458,5004 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1458,5006 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1458,5001 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c0 card 1458,b002 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1458,5001 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5b63 card 0000,0000 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5b73 card 0000,0001 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,169d card 1458,e000 rev 11 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:2), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xea000000 - 0xea0fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV370 [ATI Sapphire X550 Silent] rev 0, Mem @ 0xe0000000/27, 0xe9000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent] rev 0, Mem @ 0xe9010000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xea000000 - 0xea00ffff (0x10000) MX[B]
	[1] -1	0	0xea104000 - 0xea1043ff (0x400) MX[B]
	[2] -1	0	0xea100000 - 0xea103fff (0x4000) MX[B]
	[3] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[6] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[9] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[10] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xea000000 - 0xea00ffff (0x10000) MX[B]
	[1] -1	0	0xea104000 - 0xea1043ff (0x400) MX[B]
	[2] -1	0	0xea100000 - 0xea103fff (0x4000) MX[B]
	[3] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[5] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[6] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[8] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[9] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[10] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xea000000 - 0xea00ffff (0x10000) MX[B]
	[5] -1	0	0xea104000 - 0xea1043ff (0x400) MX[B]
	[6] -1	0	0xea100000 - 0xea103fff (0x4000) MX[B]
	[7] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[13] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 6.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?),
	ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?),
	ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?),
	ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?),
	ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?),
	ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?),
	ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?),
	ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
	ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
	ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
	ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X550 (RV370)".
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon X550 (RV370) 5B63 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xea000000 - 0xea00ffff (0x10000) MX[B]
	[5] -1	0	0xea104000 - 0xea1043ff (0x400) MX[B]
	[6] -1	0	0xea100000 - 0xea103fff (0x4000) MX[B]
	[7] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[13] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[15] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[18] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xea000000 - 0xea00ffff (0x10000) MX[B]
	[5] -1	0	0xea104000 - 0xea1043ff (0x400) MX[B]
	[6] -1	0	0xea100000 - 0xea103fff (0x4000) MX[B]
	[7] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe9010000 - 0xe901ffff (0x10000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[18] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[19] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xe9000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "UseFBDev" "true"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(==) RADEON(0): X server will not keep DPI constant for all screen sizes
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.0.2
	ABI class: X.Org Video Driver, version 1.0
(WW) open /dev/fb0: No such device
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) RADEON(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(WW) RADEON(0): fbdevHWInit failed, not using framebuffer device
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon X550 (RV370) 5B63 (PCIE)" (ChipID = 0x5b63)
(--) RADEON(0): Linear framebuffer at 0xe0000000
(II) RADEON(0): PCIE card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.25.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=131072K (PCI BAR=131072K)
(II) RADEON(0): Video RAM override, using 128 kB instead of 131072 kB
(**) RADEON(0): Mapped VideoRAM: 128 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Type: 1
(II) RADEON(0): EDID data from the display on port 2-----------------------
(II) RADEON(0): Manufacturer: VSC  Model: 371c  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) RADEON(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 720x400@88Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@87Hz (interlaced)
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) RADEON(0): #4: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) RADEON(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) RADEON(0): Serial No: PTW054557762
(II) RADEON(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) RADEON(0): Monitor name: A71f
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- CRT
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): A71f: Using hsync range of 30.00-70.00 kHz
(II) RADEON(0): A71f: Using vrefresh range of 50.00-160.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "640x350" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x175" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x400" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "720x400" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "360x200" (insufficient memory for mode)

---

### Post by zzhnet on 2006-10-19
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x240" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x240" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x240" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "320x240" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "400x300" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "400x300" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "400x300" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "400x300" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "400x300" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "512x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "512x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "512x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "512x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "512x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "576x432" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x960" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x480" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x512" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x512" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x1024" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x512" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "896x672" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1792x1344" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "896x672" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "928x696" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1856x1392" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "928x696" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "960x720" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "960x720" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "832x624" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "416x312" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1280x800" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "640x400" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1152x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "576x384" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1152x864" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "576x432" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "700x525" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "700x525" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "700x525" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1400x1050" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "700x525" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1440x900" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "720x450" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1600x1024" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "800x512" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1680x1050" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "840x525" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "960x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1920x1200" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "960x600" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1920x1440" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "960x720" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) RADEON(0): Not using default mode "1024x768" (insufficient memory for mode)
(WW) RADEON(0): Mode pool is empty
(EE) RADEON(0): No valid modes found
(**) RADEON(0): RADEONFreeScreen
(II) UnloadModule: "ati"
(II) UnloadModule: "i2c"
(II) Unloading /usr/lib/xorg/modules/libi2c.so
(II) UnloadModule: "ddc"
(II) UnloadModule: "shadowfb"
(II) Unloading /usr/lib/xorg/modules/libshadowfb.so
(II) UnloadModule: "int10"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "radeon"
(II) Unloading /usr/lib/xorg/modules/drivers/radeon_drv.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by zzhnet on 2006-10-19
help me!

---

### Post by Darganot on 2006-10-23
> **SilverTab said:**
> Mesa = no good....

same problem for me...I installed via synaptic, I ran fglrxconfig....

restarted....nothing will work...

I had the same problems, after doing some searching it turns out I was missing a few commands:
> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

I hope I did that right...this is my first post on these forums  :D  I have  been using these since I installed Dapper about four months ago, but only now do I finally feel I know enough to contribute to them.  Thanks for everyone's help, hope this helps others having same problems.  Here's the wiki I got the code from:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

After running those commands restart and run fglrxinfo again.  You should notice a considerable difference if it worked  :mrgreen:

I didn't have any problems like this with a NVIDIA card and driver I installed through automatix.  I switched boxes and this box has a ATI Radeon 9250.

---

### Post by boom1992 on 2006-12-24
Hello, theres a problem with DRI on my fglrx-driver:
I have a x1600pro
fglrxinfo:
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
There`s my xorg.conf:
[http://www.ubuntuusers.de/paste/6144/](http://www.ubuntuusers.de/paste/6144/)

And there my Xorg.0.log:
[http://www.ubuntuusers.de/paste/6146/](http://www.ubuntuusers.de/paste/6146/)

This here is the error:
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_EINVAL"
1010 (EE) fglrx(0): cannot init AGP
1011 (II) fglrx(0): [drm] removed 1 reserved context for kernel
1012 (II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7129000
1013 (WW) fglrx(0): ***********************************************
1014 (WW) fglrx(0): * DRI initialization failed! *
1015 (WW) fglrx(0): * (maybe driver kernel module missing or bad) *
1016 (WW) fglrx(0): * 2D acceleraton available (MMIO) *
1017 (WW) fglrx(0): * no 3D acceleration available *
1018 (WW) fglrx(0): ********************************************* *
Can you help me???

---

### Post by MotoX on 2007-02-12
I need to download the  older version of libdri.a but the link doesn't work for me.
Can I download it from anywhere else?
thanks

---

### Post by MotoX on 2007-02-16
found a place for those who need it

[http://ati.cchtml.com/show_bug.cgi?id=198](http://ati.cchtml.com/show_bug.cgi?id=198)

---

### Post by airdoo0 on 2007-03-11
I realise this is sort of a gravebump, but:
The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be in stalled
                     Depends: libfreetype6 (>= 2.2) but 2.1.10-1ubuntu2.2 is tobe installed
                     Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to  be installed

they are all installed, updated and i did fix packages too.
help.

---

### Post by srk on 2007-03-20
Hi, thanks for the how-to, i followed it, my X starts with the fglrx driver, but when i try to run glxgears or whatever uses the 3D i get these errors:

```
srk@Obor:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT

```
Anybody help ?

---

### Post by syroncoda on 2007-03-23
Hi, I too am having issues with my ATI X1600. I installed fglrx drivers correctly and my refresh rate sure did get fixed but now i seem to have HORRIBLE RENDERING PROBLEMS OF DOOM!!$! (I'm not sure if anyone else has had an issue like this but check it out. whenever i open a window, usually any window, and move it, it loses definition and i can't read anything on it. just writing this message was difficult.

I've hunted for a straight answer to this problem for about a month and not finding one that works I'm turning to posting like a whiny noob.

I'll try to post all the info i can find. I can't even see if there's an option for the reply to be emailed to me so i can read up on a working machine.

anyhooz heres info

#####@#####:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)
02:07.0 USB Controller: NEC Corporation USB (rev 41)
02:07.1 USB Controller: NEC Corporation USB (rev 41)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)

####@####:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)





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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "ULTRASCANP99"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "ULTRASCANP99"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection



Hope this all helps... and if anyone could take the time to email it to me (syroncoda@gmail.com) i'd really appreciate it... i can't figure it out and im stuck

---

### Post by Petar Marjanovic on 2007-03-24
Does this driver also support "sapphire radeon x1600 pro pci express"? **Yes it does.**

---


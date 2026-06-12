---
title: "HOWTO: Turn your Ubuntu Box into a Media Center Computer"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by matthewstory on 2005-11-29
This How-To will cover how to set-up your computer to rip DVDs down from the disc to your computer, and then set-up your computer to play these files on a TV.  If set-up properly you'll be able to use your computer to with the primary monitor while playing movies in Full Screen on your TV.
(my first how-to so bear with me here)

Before we begin I should note what I'm running this on: 
My System is a Dell Inspiron 8200 (laptop) with a NVidia GeForce2 Go.

This how-to will assume that you have the following:
1. A computer running Ubuntu Breezy Badger 5.10
2. An S-Video or Composite out port on your computer
3. A NVidia card capable of dual-screen set-up and TV-out (i'm sure this will work on lots of other cards, but i only have experience setting this up with a NVidia card)
4. A TV with some kind of Input port (S-Video or Composite, but if you only have RCA on your TV and S-Video on your computer you can get an adaptor: [http://www.cablestogo.com/product.asp?cat%5Fid=2012&sku=27963](http://www.cablestogo.com/product.asp?cat%5Fid=2012&sku=27963))
5. Media Player Software of some kind.  I use Totem/XINE (not GStreamer) but MPlayer will work just as well if not better, and there are several others.

This How-To is broken down into four sections:
A. Updating your NVidia Driver
B. Installing HandBrake 
C. Setting up Dual-Screen with TV-Out
D. Other Tips/Recommendations

A. Updating your NVidia Driver:

The first thing we need to do is update the Free nv driver to the non-Free nvidia driver:
To get this use Synaptic and search for 'nvidia-glx' to download and install the nvidia driver.  Then you'll need to manually edit the xorg.conf file:
```

sudo gedit /etc/X11/xorg.conf

```
Save a backup copy of this file as xorg.conf.back before you do any editing and then edit the following sections:
In the "Module" section comment out these two lines:
```

#Load "GLcore"
#Load "dri"

```
and also make sure that the following line is in the "Module" section
```

Load "glx"

```
Then Go to the "Device" section and change the following line:
```

Driver "nv"

```
to:
```

Driver "nvidia"

```
And voila, you've successfully updated the driver to the nvidia driver.  In order for this to take effect you'll need to restart the x-server, and if you've changed it properly a pretty NVidia screen should pop up before your login.  If you want this screen to go away add the following line to the "Device" section:
```

Option "NoLogo" "1"

```
If this doesn't work, you should be loaded automatically into the command line, but if you're just staring at a blank screen hit CTRL+ALT+F1 to exit into the command line and type the following command:
```

$ cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf

```
and then restart the x server.

B. Installing HandBrake

Next we need a tool to encode DVDs and rip them down to your hard drive.  For this we're going to use HandBrake 0.7.0 (handbrake.m0k.org).  Before we install HandBrake we're going to need a few tools.  Handbrake on Ubuntu needs to be installed from the source code, there is a Deb package for it, but as of right now it has unresolvable dependencies.  Use Synaptic to get the following tools:

1. make
2. jam
3. gcc
4. g++
5. dpkg-dev

Once you've installed all of these packages, you need to get the HandBrake source, you can download the tarball for this at:
[http://handbrake.m0k.org/download.php](http://handbrake.m0k.org/download.php).
Unpack the TarBall using the command:
```

$ tar zxvf home/matt/Desktop/HandBrake-0.7.0.tar.gz

```
Of course you'll have to change this for whatever location you saved the tarball to.    Once you unpack the file open the folder and then open the file BUILD in a text editor: this will explain how to build handbrake, but we'll go over it in more detail here for those who are unfamiliar with building applications from source.

First you'll need to cd to the handbrake folder:
```

$ cd /home/matt/Desktop/HandBrake-0.7.0/

```
Then run jam
```

$ jam

```
This command might take a while to execute but when it's done HandBrake should be installed, if you have any errors with this please feel free to reply to this How-To with the error and i'll try to help you debug it as best as possible.  (Usually this is just that you forgot to install a necessary package).  HandBrake for Linux has no GUI, so you'll have to run it with CLI (command line interface) the CLI program is HBTest, so to run HandBrake enter the following command:
```

$ ./HBTest *options*

```
For those more familiar with CLI you can just run:
```

$ ./HBTest --help

```
for a complete list of options.  When running HandBrake make sure you're always in the handbrake directory before running the ./HBTest command, or else you'll get an error and handbrake won't run.  For a complete guide on how to use the various options accessible through the CLI visit the HandBrake CLI reference page:
[http://homepage.mac.com/johnmm/HandBrake.CLI.Guide/](http://homepage.mac.com/johnmm/HandBrake.CLI.Guide/)

A simple handbrake rip will look like this:
```

$ mount /dev/hdb
$ cd /home/matt/Desktop/HandBrake-0.7.0
$ ./HBTest -i /media/cdrom0/video_ts -o /home/matt/Desktop/Movies/Bloodsport.mp4

```

C. Setting up Dual-Screen with TV-Out

Now that we can rip our favorite DVDs - like bloodsport - down to our harddrive, all we need to do is set up our computer to play our videos on our TV and we'll be set.  There are alot of different ways to do this, but only one of them worked for me and that's the way that i'll be explaining.  We're going to be setting up the TV and the digital flat panel as two seperate monitors running two seperat X Windows (as opposed to TwinView set-up).  If you want to try to set-up TwinView please see these various How-Tos:
[http://www.ublug.org/ubuntu/twinview...to-breezy.html](http://www.ublug.org/ubuntu/twinview...to-breezy.html) --HowTo by a Breezy Badger user
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors) --Gentoo Wiki Dual Monitors HowTo

Credit for my solution goes to ubuntu forums user rbtprkr and his xorg.conf file posted at: [http://ubuntuforums.org/showthread.p...ghlight=tv-out](http://ubuntuforums.org/showthread.p...ghlight=tv-out) and the NVidia readme document: [ftp://download.nvidia.com/XFree86/Linux-x86/1.0-5336/README](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-5336/README)

Anyway, now that all proper credit has been given, on with the solution!  You'll need to open your xorg.conf file as we're going to edit it manually:
```

$ sudo gedit /etc/X11/xorg.conf

```
Once again you should save a copy of this as xorg.conf.back should anything go terribly wrong in the process of altering it.  First we need to alter the "Device" section by altering the Identifier and adding a screen line:
```

Identifier "nvidia0"
Screen 0

```
Then we need to create a second "Device" section:
```

Section "Device"
Identifier "nvidia1"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 1
Option "TVOutFormat" "SVIDEO"
Option "TVStandard" "NTSC-M"
Option "ConnectedMonitor" "TV"
EndSection

```
IMPORTANT: make sure that the value of BusID is the same as the value of BusID in the first device section.  

For the TVOutFormat and TVStandard values please substitute in the appropriate values (e.g. if you are using composite out then substitute "COMPOSITE" for "SVIDEO" or if you're standard is PAL-B substitute "PAL-B" for "NTSC-M"), for more on this see the nvidia readme appendix J.

What we've done here is divided our nvidia card into two seperate devices that are going to provide picture out to two seperate monitors each running its own screen.  

Next we need to change the existing "Monitor" section's identifier to:
```

Identifier "Monitor0"

```
and then create a second monitor section for our TV:
```

Section "Monitor"
Identifier "Monitor1" #TV
Option "HorizSync" "30-50"
Option "VertRefresh" "60"
EndSection

```

Now that we've set up both of our monitors we need to set up the screens that will be displayed on each.  In the existing screen section you'll need to change the identifier, device and monitor lines to match the following:
```

Identifier "Screen0"
Device "nvidia0"
Monitor "Monitor0"

```
and then you'll need to add a second screen section for your TV:
```

Section "Screen"
Identifier "Screen1"
Device "nvidia1"
Monitor "Monitor1"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "800x600"
EndSubSection
EndSection

```

Make sure that default depth for the TV is the same as the default depth for your other monitor.  You may also have to screw around with the modes, 800x600 works for my tv and will probably work for most TVs, but if you have a better TV you may want to try 1024x768 or other resolutions.  
The last thing we need to do is set up the "ServerLayout" section so that X knows how to set up your new configuration (Note: keep your own InputDevice settings for this):
```

Section "ServerLayout"
Identifier "SimpleLayout"
Screen 0 "Screen0"
Screen 1 "Screen1" leftOf "Screen0"

```
If your TV is to the right of your primary monitor change the leftOf to rightOf.  Once you've finished this save your xorg.conf file, make sure your TV is hooked up to your computer and restart.  You'll notice that if you watch a movie in full-screen on the TV it doesn't effect your primary monitor at all and you can use your computer to still do whatever you want.

D. Other Tips/Recommendations

Encoding a DVD takes a very long time, and during this time you might want to be using your combo drive to do something else.  In this case I recommend picking up a nice little program called vobcopy.  You can get this through synaptic, it allows you to copy DVDs to your harddrive, a process that takes much less time than encoding DVDs.  Once you've downloaded it you'll want to run it with the -m option, which will make an exact copy of the DVD on your local drive, and then HandBrake can treat this directory the same way it would treat a DVD.
Well I hope this works for everyone,

cheers,
matt

---

### Post by pbb on 2006-02-02
[QUOTE=matthewstory][http://www.ublug.org/ubuntu/twinview...to-breezy.html](http://www.ublug.org/ubuntu/twinview...to-breezy.html) --HowTo by a Breezy Badger user[/QUOTE]

That should have been [http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

[QUOTE=matthewstory]Credit for my solution goes to ubuntu forums user rbtprkr and his xorg.conf file posted at: [http://ubuntuforums.org/showthread.p...ghlight=tv-out](http://ubuntuforums.org/showthread.p...ghlight=tv-out)[/QUOTE]

Don't know what that URL should have been. The forum software seems to cripple some URLs.

---

### Post by benplaut on 2006-02-02
read up a bit on MythTV ;)

---

### Post by Iandefor on 2006-02-02
I've had a bad time with Handbrake; primarily, the fact that the video output is usually sub-par and the audio and video are a few seconds out of sync. I prefer using vobcopy and ffmpeg, since the video output is usually of high quality and is extremely configurable.

---

### Post by dudus on 2006-02-03
You relly should try mythtv. It has a better looking interface in TV's and can play and encode cds and dvds. Besides mythtv can handle tv channels like a tivo. It also has an snes emulator [:)]

---

### Post by pnodine92074 on 2006-07-17
Thanks, I really appreciated your how-to article, not so much for hooking up two monitors/tv but for the handbrake and ripping dvd to hard drive.  Greatly appreciated. 
Thanks!!

---

### Post by ixus_123 on 2006-10-14
currently using acidrip but thought I'd give this HandBrake a try.

You have to run
```
./configure
```
before you run jam - but the it will tell you this in the terminal :)

---

### Post by tastygroove on 2007-06-13
hey, thanks for the great how-to.  quick question though.  i have a computer that i sometimes use to watch dvds and other videos on my TV, but not always.  i followed your guide and got the svideo out to the tv working, but i don't want the dual monitors active all the time.  do you know of a quick way to disable the TV output without having to edit scripts?

thanks

---

### Post by zuzuzzzip on 2007-08-13
I get an error :S

I've been trying to get an output on my TV now for 2 hours, still nothing... tried twinview first though...

my /var/log/Xorg.0.log
```
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.38.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GT at PCI:5:0:0:
(--) NVIDIA(0):     ACI ASUS PM17TU (DFP-0)
(--) NVIDIA(0): ACI ASUS PM17TU (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI ASUS PM17TU (DFP-0): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(1): RGB weight 565
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Option "HorizSync" "30-50"
(**) NVIDIA(1): Option "VertRefresh" "60"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "PAL-B"
(II) NVIDIA(1): NVIDIA GPU GeForce 6800 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.40.02.38.07
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6800 GT at PCI:5:0:0:
(--) NVIDIA(1):     ACI ASUS PM17TU (DFP-0)
(--) NVIDIA(1): ACI ASUS PM17TU (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): ACI ASUS PM17TU (DFP-0): External Single Link TMDS
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

my xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier "SimpleLayout"
    Screen 0 "Screen0"
    Screen 1 "Screen1" leftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option       "Name" "Logitech USB-PS/2 Optical Mouse"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

# TFT section
Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia0"
    Screen 0
    Driver         "nvidia"
    BusID       "PCI:5:0:0"
    Option        "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "nvidia0"
    Monitor        "Monitor0"
    Option       "NoLogo"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
# end of TFT section

# TV section
Section "Device"
    Identifier "nvidia1"
    Driver "nvidia"
    BusID "PCI:5:0:0"
    Screen 1
    Option "TVOutFormat" "SVIDEO"
    Option "TVStandard" "PAL-B"
    Option "ConnectedMonitor" "TV"
EndSection

Section "Monitor"
    Identifier "Monitor1" #TV
    Option "HorizSync" "30-50"
    Option "VertRefresh" "60"
EndSection

Section "Screen"
   Identifier "Screen1"
   Device "nvidia1"
   Monitor "Monitor1"
   DefaultDepth 16
   SubSection "Display"
    Depth 16
    Modes "800x600"
   EndSubSection
EndSection
# end of TV section
```

---

### Post by loudestnoise on 2007-08-13
I'm having trouble getting Video output to my TV, and here is my xorg.conf file.  Perhaps someone can tell me what I have wrong. The TV will show the Ubuntu splash screen and then I get an error saying X server can't start.

**EDIT: I solved my problems by following the [NvidiaTVOut]("https://help.ubuntu.com/community/NvidiaTVOut") documentation page**
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia0"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Screen		0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Device"
	Identifier	"nvidia1"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Screen		1
	Option		"TVOutFormat"	"SVIDEO"
	Option		"TVStandard"	"NTSC-M"
	Option		"ConnectedMonitor"	"TV"
EndSection	

Section "Monitor0"
	Identifier	"Monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier "Monitor1" #TV
	Option "HorizSync" "30-50"
	Option "VertRefresh" "60"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Device		"nvidia0"
	Monitor		"Monitor0"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	
EndSubSection

Section "Screen"
	Identifier 	"Screen1"
	Device		"Monitor1"
	Montior		"TV"
	Defaultdepth	24
	Modes		"800x600"
EndSubSection
EndSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	Option         "TwinView"
    	Option         "MetaModes" "1280x1024,1152x864;1024x768,NULL; 800x600,NULL; 640x480,NULL"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 0  	"Screen0"
	Screen 1	"Screen1" rightOf "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by zuzuzzzip on 2007-08-14
> **loudestnoise said:**
> [B]EDIT: I solved my problems by following the [NvidiaTVOut]("https://help.ubuntu.com/community/NvidiaTVOut") 
documentation page[/B]

your xorg.conf(adjusted to my settings ofc) made my X-server not recognise any screen :P

---

### Post by loudestnoise on 2007-08-14
That's why I posted having a problem. The pasted xorg.conf was not working. The NvidiaTVOut documentation gives you instructions on howto get it running. Assuming you have an nvidia card.

---

### Post by zuzuzzzip on 2007-08-14
Well, I've tried some other stuff now, but now he will not recognise my TV-Encoder no more :s yesterday it did!

here is my config and log...
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier        "Basic Layout"
    Screen 0        "Screen0"
    Screen 1        "Screen1" rightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

    # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "be"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "CorePointer"
    Option       "Name" "Logitech USB-PS/2 Optical Mouse"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

# TFT section
Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nvidia0"
    Driver         "nvidia"
    BusID       "PCI:5:0:0"
    Screen        0
    Option       "AddARGBGLXVisuals"    "True"
    Option       "NoLogo"    "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "nvidia0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth      24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
# end of TFT section

# TV section
Section "Device"
    Identifier        "nvidia1"
    Driver        "nvidia"
    BusID        "PCI:5:0:0"
    Screen        1
    Option       "ConnectedMonitor" "TV"
EndSection

Section "Monitor"
    Identifier        "Monitor1" #TV
    Option        "HorizSync" "30-50"
    Option        "VertRefresh" "60"
EndSection

Section "Screen"
   Identifier        "Screen1"
   Device        "nvidia1"
   Monitor        "Monitor1"
   DefaultDepth    24
   Option          "TVOutFormat" "SVIDEO"
   Option          "TVStandard" "PAL-B"
   Option          "ConnectedMonitor" "TV"
   SubSection "Display"
    Depth       24
    Modes       "640x480"
   EndSubSection
EndSection
# end of TV section
```

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ZuzuPC-ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
Build Date: 04 April 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 14 15:46:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Basic Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "nvidia0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "nvidia1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1462,7100 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1462,7100 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1462,7100 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1462,7100 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1462,7100 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1462,7100 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1462,7100 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1462,7100 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1462,7100 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:08:0: chip 1814,0201 card 1462,6834 rev 01 class 02,80,00 hdr 00
(II) PCI: 01:0c:0: chip 1106,3044 card 0574,086c rev 46 class 0c,00,10 hdr 00
(II) PCI: 01:0d:0: chip 1102,0007 card 1462,1009 rev 00 class 04,01,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4362 card 1462,058c rev 15 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 1095,3132 card 1462,710a rev 01 class 01,80,00 hdr 00
(II) PCI: 05:00:0: chip 10de,00f9 card 1554,1185 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
    [0] -1    0    0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
    [0] -1    0    0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
    [0] -1    0    0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfdb00000 - 0xfdbfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
    [0] -1    0    0xfda00000 - 0xfdafffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xfd900000 - 0xfd9fffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
    [0] -1    0    0xfd800000 - 0xfd8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 I/O range:
    [0] -1    0    0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
    [0] -1    0    0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
    [0] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
(--) PCI:*(5:0:0) nVidia Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT] rev 162, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x100000000) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [1] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [2] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [3] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [4] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [5] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [6] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [7] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [10] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [12] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [13] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [14] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [15] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [16] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [17] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [18] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [19] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [20] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [21] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [22] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [23] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [24] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [25] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [26] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [27] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [28] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [29] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [30] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [31] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [1] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [2] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [3] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [4] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [5] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [6] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [7] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [8] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [9] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [10] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [11] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [12] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [13] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [14] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [15] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [16] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [17] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [18] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [19] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [20] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [21] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [22] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [23] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [24] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [25] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [26] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [27] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [28] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [29] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [30] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [31] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [5] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [6] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [7] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [8] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [9] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [10] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [11] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [12] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [13] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [14] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [15] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [16] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [20] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [21] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [22] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [23] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [24] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [25] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [26] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [27] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [28] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [29] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [30] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [31] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [32] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [33] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [34] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [35] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [36] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [37] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9631
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.9631
    Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:37:27 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [5] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [6] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [7] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [8] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [9] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [10] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [11] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [12] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [13] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [14] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [15] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [16] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [17] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [18] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [19] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [20] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [21] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [22] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [23] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [24] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [25] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [26] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [27] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [28] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [29] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [30] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [31] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [32] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [33] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [34] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [35] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [36] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [37] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [5] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [6] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [7] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [8] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [9] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [10] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [11] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [12] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [13] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [14] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [15] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [16] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [17] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [18] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [19] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [22] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [23] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [24] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [25] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [26] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [27] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [28] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [29] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [30] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [31] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [32] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [33] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [34] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [35] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [36] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [37] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [38] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [39] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [40] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
    [41] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [42] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.40.02.38.07
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GT at PCI:5:0:0:
(--) NVIDIA(0):     ACI ASUS PM17TU (DFP-0)
(--) NVIDIA(0): ACI ASUS PM17TU (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): ACI ASUS PM17TU (DFP-0): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "ConnectedMonitor" "TV"
(**) NVIDIA(1): Option "TVStandard" "PAL-B"
(**) NVIDIA(1): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(1): Option "HorizSync" "30-50"
(**) NVIDIA(1): Option "VertRefresh" "60"
(**) NVIDIA(1): Enabling RENDER acceleration
(**) NVIDIA(1): Forcing SVIDEO output
(**) NVIDIA(1): TV Standard string: "PAL-B"
(II) NVIDIA(1): NVIDIA GPU GeForce 6800 GT at PCI:5:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 262144 kBytes
(--) NVIDIA(1): VideoBIOS: 05.40.02.38.07
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 6800 GT at PCI:5:0:0:
(--) NVIDIA(1):     ACI ASUS PM17TU (DFP-0)
(--) NVIDIA(1): ACI ASUS PM17TU (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(1): ACI ASUS PM17TU (DFP-0): External Single Link TMDS
(EE) NVIDIA(1): Unable to find available Display Devices for screen 1.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B]
    [1] 0    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B]
    [2] 0    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [7] -1    0    0xfdbf8000 - 0xfdbfbfff (0x4000) MX[B]
    [8] -1    0    0xfdbff000 - 0xfdbff07f (0x80) MX[B]
    [9] -1    0    0xfddfc000 - 0xfddfffff (0x4000) MX[B]
    [10] -1    0    0xfdeff000 - 0xfdeff7ff (0x800) MX[B]
    [11] -1    0    0xfdefc000 - 0xfdefdfff (0x2000) MX[B]
    [12] -1    0    0xfe029000 - 0xfe029fff (0x1000) MX[B]
    [13] -1    0    0xfe02a000 - 0xfe02afff (0x1000) MX[B]
    [14] -1    0    0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
    [15] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[B]
    [16] -1    0    0xfe02f000 - 0xfe02ffff (0x1000) MX[B]
    [17] -1    0    0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
    [18] -1    0    0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
    [19] -1    0    0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [21] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [22] -1    0    0x0000bf00 - 0x0000bf7f (0x80) IX[B]
    [23] -1    0    0x0000ce00 - 0x0000ceff (0x100) IX[B]
    [24] -1    0    0x0000de00 - 0x0000de1f (0x20) IX[B]
    [25] -1    0    0x0000df00 - 0x0000df7f (0x80) IX[B]
    [26] -1    0    0x0000f000 - 0x0000f007 (0x8) IX[B]
    [27] -1    0    0x0000f100 - 0x0000f10f (0x10) IX[B]
    [28] -1    0    0x00000b60 - 0x00000b63 (0x4) IX[B]
    [29] -1    0    0x00000960 - 0x00000967 (0x8) IX[B]
    [30] -1    0    0x00000be0 - 0x00000be3 (0x4) IX[B]
    [31] -1    0    0x000009e0 - 0x000009e7 (0x8) IX[B]
    [32] -1    0    0x0000f600 - 0x0000f60f (0x10) IX[B]
    [33] -1    0    0x00000b70 - 0x00000b73 (0x4) IX[B]
    [34] -1    0    0x00000970 - 0x00000977 (0x8) IX[B]
    [35] -1    0    0x00000bf0 - 0x00000bf3 (0x4) IX[B]
    [36] -1    0    0x000009f0 - 0x000009f7 (0x8) IX[B]
    [37] -1    0    0x0000fb00 - 0x0000fb0f (0x10) IX[B]
    [38] -1    0    0x00004c40 - 0x00004c7f (0x40) IX[B]
    [39] -1    0    0x00004c00 - 0x00004c3f (0x40) IX[B]
    [40] -1    0    0x0000ff00 - 0x0000ff1f (0x20) IX[B]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "be"
(**) Generic Keyboard: XkbLayout: "be"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evdev brain: Rescanning devices (1).
(**) Option "CorePointer"
(**) Configured Mouse-usb-0000:00:02.0-8/input0: Core Pointer
(II) Configured Mouse-usb-0000:00:02.0-8/input0: Found 4 relative axes.
(II) Configured Mouse-usb-0000:00:02.0-8/input0: Configuring as pointer.
(**) Configured Mouse-usb-0000:00:02.0-8/input0: HWHEELRelativeAxisButtons: 6 7.
(**) Configured Mouse-usb-0000:00:02.0-8/input0: WHEELRelativeAxisButtons: 4 5.
(II) Configured Mouse-usb-0000:00:02.0-8/input0: Found 8 mouse buttons
(**) Configured Mouse-usb-0000:00:02.0-8/input0: Configuring 4 relative axes.
(II) Configured Mouse-usb-0000:00:02.0-8/input0: Configured 12 mouse buttons
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse-usb-0000:00:02.0-8/input0" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Configured Mouse-usb-0000:00:02.0-8/input0: 4 valuators.
(**) ../../src/evdev_btn.c (166): Registering 12 buttons.
(II) Configured Mouse-usb-0000:00:02.0-8/input0: Init
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
    No such file or directory.
Error opening /dev/input/wacom : Success
(II) evdev brain: Rescanning devices (2).
(II) Configured Mouse-usb-0000:00:02.0-8/input0: On
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?
AUDIT: Tue Aug 14 15:46:43 2007: 4898 X: client 6 rejected from local host (uid 1000)
AUDIT: Tue Aug 14 15:46:43 2007: 4898 X: client 7 rejected from local host (uid 1000)
```

---

### Post by mikeize on 2007-10-08
I get an error when compiling handbrake:

```
mike@u-desktop:~/HandBrake-source$ jam
...found 318 target(s)...
...updating 1 target(s)...
Link HandBrakeCLI 
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status

g++  -o HandBrakeCLI  test/test.o test/parsecsv.o libhb/libhb.a contrib/lib/liba52.a contrib/lib/libavformat.a contrib/lib/libavcodec.a contrib/lib/libavutil.a contrib/lib/libdca.a contrib/lib/libdvdread.a contrib/lib/libmp4v2.a contrib/lib/libfaac.a contrib/lib/libmp3lame.a contrib/lib/libmpeg2.a contrib/lib/libvorbis.a contrib/lib/libvorbisenc.a contrib/lib/libogg.a contrib/lib/libsamplerate.a contrib/lib/libx264.a contrib/lib/libxvidcore.a contrib/lib/libmkv.a contrib/lib/libswscale.a contrib/lib/libdvdcss.a -lz -lpthread 

...failed Link HandBrakeCLI ...
...failed updating 1 target(s)...
mike@u-desktop:~/HandBrake-source$ make
( cd .. ; ./configure ; cd contrib ; cp -f ../config.jam . ; jam )
System: Linux
Endian: little

To build HandBrake, run:
 './jam' on a Mac (or 'make' to try the UB build method),
 'jam' on Linux or Windows.
...found 56 target(s)...
Link HandBrakeCLI
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
Compile line for ../HandBrakeCLI was:
g++ -I../libhb -o ../HandBrakeCLI test.o parsecsv.o ../libhb/libhb.a ../contrib/lib/liba52.a ../contrib/lib/libmkv.a ../contrib/lib/libavformat.a ../contrib/lib/libavcodec.a ../contrib/lib/libavutil.a ../contrib/lib/libdca.a ../contrib/lib/libdvdread.a ../contrib/lib/libdvdcss.a ../contrib/lib/libfaac.a ../contrib/lib/libmp3lame.a ../contrib/lib/libmpeg2.a ../contrib/lib/libvorbis.a ../contrib/lib/libvorbisenc.a ../contrib/lib/libogg.a ../contrib/lib/libsamplerate.a ../contrib/lib/libx264.a ../contrib/lib/libxvidcore.a ../contrib/lib/libmp4v2.a ../contrib/lib/libswscale.a -lz -lpthread
make[1]: *** [../HandBrakeCLI] Error 1
make: *** [HandBrakeCLI] Error 2
```

any thoughts?

-mike

---

### Post by cchi on 2008-04-27
Mike, it looks like you dont have any compliers installed.  There are a lot of other packages that you need other than jam.

Run this (remove jam, and whatever else you already have):
sudo apt-get install jam build-essential nasm zlib1g-dev libdvdcss2

You also should check if you have these if you still have problems after you have installed the above.  Some may be needed on your system.

ii autoconf 2.61-4
ii automake 1.10+nogfdl-1
ii devscripts 2.9.26
ii g++ 4.1.1-15
ii g++-4.1 4.1.1-21
ii gcc 4.1.1-15
ii gcc-4.1 4.1.1-21
ii gcc-4.1-base 4.1.1-21
ii jam 2.5rel-1
ii libgcc1 4.1.1-21
ii libtool 1.5.22-4
ii make 3.81-2
ii makedev 2.3.1-83
ii yasm 0.5.0-2
ii zlib1g-dev 1.2.3-13

---


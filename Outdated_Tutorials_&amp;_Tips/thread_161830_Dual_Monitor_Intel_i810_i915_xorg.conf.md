---
title: "Dual Monitor Intel i810 i915 xorg.conf"
date: 2006-04-17
forum: Outdated Tutorials &amp; Tips
---

### Post by thebasard on 2006-04-17
Hi all,
I've seen some posts about getting dual monitors to work where you have one large desktop that spans two monitors and I wanted to post my xorg.conf file in case anyone wants to use it.  It ain't pretty and the hardware acceleration does not work but on my Dell Latitude D610 with the Intel 915GM video card, the dual monitor setup is at least workable.

I get a large desktop that spans both screens and I can have windows on each monitor, pretty much like you would see in Windows.

One problem that I know of is that when my laptop isn't connected to the external LCD monitor, windows that I had previously opened and had placed on the LCD start up to the left of my onboard laptop display.  For example if I opened Text Editor and placed it on the external LCD and did my work there, the next time I use my laptop without the external LCD and start Text Editor it opens up to the left of my laptop display where it is not visible.

Again, this xorg.conf file isn't perfect but it does work, well mostly.

**Backup your existing xorg.conf file!**
If you intend to use this file to replace your existing xorg.conf I suggest that you do 
# cd /etc/X11
# sudo cp xorg.conf xorg.conf-original

to keep your original version in case you want to revert back.

#---------- My File -----------#
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

# Section "Extensions"
# 	Option 	"Composite" "Enable"
# EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"intel0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option          "MonitorLayout" 	"CRT,LFP"
        VideoRam        131072
	Screen          0
        Option "DevicePresence" "true"
#        Option          "ForceBIOS" "800x600=1400x1050"
#	Option		"FlipPrimary"		"true"
EndSection

Section "Device"
        Identifier      "intel1"
#       Option "Rotate" "CCW"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
#Option "DisplayInfo" "false"
        Option "DevicePresence" "true"
#       Option          "ForceBIOS" "1920x1440=1920x1200"
#	Option		"FlipPrimary"		"true"
EndSection

Section "Monitor"
	Identifier	"Internal"
	Option		"DPMS"
EndSection

Section "Monitor"
        Identifier      "dell1905"
	Option		"DPMS"
#        Modeline "1280x1024" 114.98 1280 1312 1744 1776 1024 1045 1055 1076

#	DisplaySize	519 324
#	HorizSync	30-81
#	VertRefresh	60-60
#	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Screen"
	Identifier	"builtinlcd"
	Device		"intel0"
	Monitor		"Internal"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "externallcd"
        Device          "intel1"
        Monitor         "dell1905"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Xinerama"
        Screen          0 "builtinlcd" 0 0
        Screen          1 "externallcd" LeftOf "builtinlcd"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option          "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by russelld on 2006-08-26
To avoid issues when changing from dual to single monitors, I change xorg.conf back to single momitor to force the aps onto one monitor by using [multimonitor script]("http://www.ubuntuforums.org/showpost.php?p=1182999&postcount=25").  Change it to suit your needs.

One thing that I had to change the screen resolution to 1024x768 to make it work as this laptop uses XGA rather than SXGA+ which uses 1400x1050.

> **thebasard said:**
> 
Section "Screen"
	Identifier	"builtinlcd"
	Device		"intel0"
	Monitor		"Internal"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		[COLOR="Red"]Modes		"1400x1050"[/COLOR]
	EndSubSection
EndSection


so I set it to this:

```

Section "Screen"
	Identifier	"builtinlcd"
	Device		"intel0"
	Monitor		"Internal"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		[COLOR="Red"]Modes   "1024x768"[/COLOR]
	EndSubSection
EndSection

```

After changing the resolution of the external monitor to suit the LCD, it worked a treat! :D

---

### Post by wammin on 2006-11-26
I have a HP Pavilion dv1000t widescreen laptop that I'm trying to set up with  an additional 19" LCD that I have positioned on a stand directly above the laptop screen. This particular laptop has the Intel 810i built-in video card. I tried using the configuration posted in this thread, and it sort-of works. 

Both displays are working fine and I can move the mouse between the displays, up and down as you would expect. But the problem is that I can't drag and application windows more than halfway down into the lower screen. It's like the windows get stuck halfway down the screen, and won't go any lower.

Anybody have any ideas?

I'm using Ubuntu Edgy, here's my xorg.conf:

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
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Option		"Protocol"		"ExplorerPS/2"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"intel0"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"MonitorLayout" "CRT,LFP"
	VideoRam 	131072
	Screen		0
	Option		"DevicePresence" "true"
EndSection

Section "Device"
	Identifier	"intel1"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
	Option		"DevicePresence" "true"
EndSection

Section "Monitor"
	Identifier	"builtin"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"external"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"builtinlcd"
	Device		"intel0"
	Monitor		"builtin"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"externallcd"
	Device		"intel1"
	Monitor		"external"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes 		"1280x1024"
	EndSubSection
EndSection



Section "ServerLayout"
	Identifier	"Xinerama"
	Screen 0	"builtinlcd" 0 0
	Screen 1	"externallcd" Above "builtinlcd"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by wammin on 2006-12-02
I found the answer!
```
rm -r ~/.gconf/desktop/gnome/screen
```

It works!

---

### Post by tmecklem on 2006-12-07
I have the same problem, although my setup is left/right dual display.  I am a recent convert from gentoo and I had the window dragging problem in gentoo as well.  When I first installed ubuntu, I was thrilled to see that it did not have the dragging problem.  After this morning's updates, however, it began to occur in my ubuntu install.  It pretty much makes having dual display support worthless since no windows get placed on my right screen and I can't drag anything over there either.  It's like the windows hit an invisible brick wall. ](*,) 

I tried removing the screen gconf like the previous poster suggested, but that did not help my situation.  Does anyone have any other ideas or an explanation of what's going on here?  It seems like this isn't an isolated problem, so I'm hoping that there's somebody out there who understands the problem.  I can post my x config if needed, but it's a pretty stock xinerama-enabled config.

---

### Post by tmecklem on 2006-12-07
My problem is fixed, most likely due to the removal of one of the other folders in my gconf config.  I blew away font_rendering and background along with several others and my next X restart was like waking up from a nightmare where everything's back to normal.

I wish I had taken a more scientific approach to solving the problem, but frustration and dismay settled in to the part of my brain that takes a rational approach in most circumstances.  Thanks for the help, it solved my problem in an indirect way.  :-D

---

### Post by Blaise Faugeras on 2007-01-26
Dear all,
I have exactly the same problem with my dual screen configuration. My mouse can go 
everywhere but windows get stuck against "invisible walls". I tried to remove the screen folder in my .gconf and also other folders but restarting the Xserver doesn't change anything. 
Does anybody have another brillant idea to solve this?
thanks

---

### Post by funkjunkie on 2007-10-30
Even though i had used the upgrade tool for past upgrades without much trouble, I recommend anyone who is moving up from other versions to do a clean install rather than upgrade.

having /home and /opt mounted as partitions is esp helpfull and kept me from losing my data. 

I found that new 'screens and graphics'  GUI very frustrating 

I was finally able to get my dual-head working by going to ATI website and downloading my driver installer from them.   It basically disables the randr GUI or whatever its called..  good riddance that thing didnt give me anything but grief.

---


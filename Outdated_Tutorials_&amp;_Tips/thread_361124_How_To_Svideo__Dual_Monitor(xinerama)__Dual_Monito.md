---
title: "How To: Svideo / Dual Monitor(xinerama) / Dual Monitor(cloned desktop) on i945"
date: 2007-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by featherking on 2007-02-14
[SIZE="3"]How To: Svideo(cloned) / Dual Monitor(xinerama) / Dual Monitor(cloned desktop) on i945 (i810 driver)[/SIZE]

*[COLOR="Green"]*The basic purpose of this is to enable your Svideo-out and also your VGA-out ports on your computer*[/COLOR]*
I have used this successfully on 32bit Feisty using my i945(i810 driver)
We know it works on the i945, and the i915 for sure; however, i suspect it will work with all i810 driver-using chipsets
Others have successfully used it in Kubuntu,Dapper Drake, Edgy Eft, and even Archlinux :)

I have a little script that i use to switch inbetween the different xorgs that we will set up.

[SIZE="2"][COLOR="red"]STEP ONE[/COLOR][/SIZE]
run this to create the script:
```
sudo gedit /usr/bin/switchmon
```

[COLOR="Green"]credit goes to groggyboy for his modification of my original script, it is now very automated and very nice!![/COLOR]
then paste the following code into the open gedit window:
*note* [COLOR="Green"]This script, by default, assumes you are running beryl in gnome. If you are running beryl in KDE, comment out the gnome line and uncomment the KDE line. If you dont run beryl at all, comment out both lines. The reason is - beryl does not work properly with the Xorg file and will crash everytime if it isnt disabled. I have bolded the a few of the lines as an example of where to look. These will have to be edited for every xorg if you do run KDE or no beryl at all.[/COLOR]*/note*
```
#!/bin/sh
#
cmd=${0##*/}                              # Command's basename
msg="\n\tUsage: $cmd [1|2|3|4|5]\n\t\t1 = Single Monitor\n\t\t2 = SVideo Dual Monitor\n\t\t3 = Svideo Clone\n\t\t4 = VGA Dual Monitor\n\t\t5 = VGA Clone Desktop"

if [ $# -lt 1 ]; then
	echo $msg
	exit 0
fi 
if [ $1 = "4" ]; then
	echo -e "\nChanging to VGA Dual Monitor mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # **<-GNOME**
	**#**mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # **<-KDE**
	sudo cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "5" ]; then
	echo -e "\nChanging to VGA Cloned Desktop mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.clone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "3" ]; then
	echo -e "\nChanging to S-Video(Clone) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.sclone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "2" ]; then
	echo -e "\nChanging to S-Video(Dual) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.svideo /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
elif [ $1 = "1" ]; then
	echo -e "\nChanging to Single Monitor mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment out both if you don't use Beryl.
	mv ~/.config/beryl-manager.off ~/.config/autostart/beryl-manager.desktop # <-GNOME
	#mv ~/.kde/beryl-manager.off ~/.kde/Autostart/beryl-manager.desktop # <-KDE
	sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 1
else
	echo "Invalid Number" $msg
	exit 0
fi

```

then save and exit. we need to make that file executable so it can do its job:
```
sudo chmod +x /usr/bin/switchmon
```

Now we need to create the different xorg.conf files that we will switch between
[COLOR="Red"]*note*[/COLOR] You will probably have to edit the resolution values in these files to match whatever you are
trying to get, i just use my laptop so im limited to 1280x800 but some people might have bigger monitors or whatever[COLOR="Red"]*/note*[/COLOR]

[SIZE="2"][COLOR="red"]STEP TWO[/COLOR][/SIZE]

We will copy the xorg.conf to a different named file so we can switch back to it when not using svideo:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
```

Now we create the svideo dual monitor version of the xorg:
```
sudo gedit /etc/X11/xorg.conf.svideo
```

Paste the following into that window:
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO" # "COMPOSITE"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		0 "LCD"
	Screen		1 "TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

```
Now save and close the file.

This creates the svideo xorg that will clone your two screens:
```
sudo gedit /etc/X11/xorg.conf.sclone
```

paste the following into that window:
[COLOR="Red"]*note*[/COLOR] You may want to copy only from the "Section 'Device'" line and below depending on your hardware, if you have a different mouse or something just make a copy of your current xorg.conf and save it as xorg.conf.svideo and then replace from the Device line below in your file with what ive posted here [COLOR="Red"]*/note*[/COLOR]
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
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
	Identifier "SVIDEO"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "FlipPrimary" "True"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Option "Clone" "True"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

```
then save and close the file

Now we create another xorg file for using a cloned desktop (useful for connecting to a projector):
```
sudo gedit /etc/X11/xorg.conf.clone
```

Again, paste the following (and again from the device line and below if you want):
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
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load    "dbe"
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
	Identifier	"Intel"
	Driver		"i810"
	Option    "MonitorLayout" "CRT,LFP"
	Option    "Clone" "true"
	Option    "DevicePresence" "true"
	Option		"UseFBDev"		"true"
	BusID		"PCI:0:2:0"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Option 		"AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite" "Enable"
EndSection

```
then save and close the file

Now we create an xorg for using dual monitors as one desktop(using xinerama):
```
sudo gedit /etc/X11/xorg.conf.dual
```

Again, paste the following:
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```
save the file and close

[SIZE="2"][COLOR="red"]STEP THREE[/COLOR][/SIZE]
Now we should have 5 different xorg.conf files:
xorg.conf.single
xorg.conf.dual
xorg.conf.clone
xorg.conf.svideo
xorg.conf.sclone

The script we created at the beginning will switch between these, the xorg.conf.single is the file that you were currently using when you started. To switch between them its very simple:
from the terminal run
```
switchmon
```

And it displays the script usage parameters, for example running:
```
switchmon 2
```
will close beryl and swap out your current xorg.conf with the svideo xorg.conf and then restart X

[COLOR="Red"]*note1*[/COLOR]Also, sometimes after switching between two many xorg right in a row (i.e. running switchmon 1, then restart x, then switchmon 2, then restart x, then switchmon 4, then restart x, etc) for me sometimes X would just give an error about not being able to start, in these cases i could only get back into X by rebooting, just FYI [COLOR="Red"]*/note1*[/COLOR]

[COLOR="Red"]*note2*[/COLOR] If something goes horribly wrong and you cant boot into X at all, just run 'switchmon 1' this will restore your original single monitor xorg.conf and you can try ctrl+alt+backspace or just reboot after that and you should be back in business (this has helped me many times) [COLOR="Red"]*/note2*[/COLOR]

[COLOR="Red"]*note3*[/COLOR] if you have an issue about not being able to drag images to certain parts of your dual screen, try running ([COLOR="Green"]credit goes to Veloce for the fix):[/COLOR]
```
sudo rm -r ./.gconf/desktop/gnome/screen
```
 [COLOR="Red"]*/note3*[/COLOR]

[COLOR="Red"]EXTRA - Create Gnome Launcher[/COLOR]
[COLOR="Green"]Rather than open the terminal to run the 'switchmon' script everytime you need to change you xorg, it is much easier to create a launcher. You could create a launcher to run any switchmon you want. For example 'switchmon 1' or 'switchmon 4'. The launcher I created basically gives all the 'switchmon' configurations in one window. However you could substitute my command with any 'switchmon' like I said.

To start, right-click on the desktop and hit 'Create Launcher'. This brings up a window with a few options. The 'Name' and 'Comment' boxes are what show up when you hover the mouse over the new launcher. I would suggest typing```
SwitchMon
```
in the 'Name' box and

```
Switch between Svideo and VGA output
```
In the 'Comment' box.

Next, in the 'Command' box paste the following, or if you know you will always want to run 'switchmon 2' then replace the 'Command' box with whatever you will be running. The following is the command I use:
```
xterm -e /bin/bash -c "switchmon; sudo -s"
```
[COLOR="Red"]*note*[/COLOR] This merely shows you what switchmon can do and leaves you at a terminal prompt. You will still have to type 'switchmon 2', for example, to run the script [COLOR="Red"]*/note*[/COLOR]

For the icon you can click the button that says 'no icon' and choose one that you like the one I use is found here:
```
/usr/share/icons/gnome/48x48/apps/gdm.png
```[/COLOR]
[COLOR="Blue"]
ISSUES WITH BLUE VIDEO ON OUTPUT IN CLONE MODE[/COLOR]

Here are the fixes for MPlayer, KMPlayer, totem-gstreamer, and totem-xine. (have not figured out a fix for VLC yet)
some of this was taken from a gandalfn tutorial that I used ages ago:

-> if you are using MPlayer or KMPlayer :
launch Mplayer and go to 'Preferences' > 'Video' and from the available drivers select 'X11 (XImage/SHM)'

-> if you have totem-gstreamer :
launch gstreamer-properties and select on default video playback &#8220;XWindow (NoXv)&#8221; in video tab.

-> if you have totem-xine :
edit ~/.gnome2/totem_config and find this line:
```
#video.driver:auto
```
and replace it with
```
video.driver:xshm
```

Hopefully this helps someone, im no Xorg expert so i will try to answer any problems that will probably arise but this works for me after many days of hunting obscure settings from the forums.. Please let me know if it works/doesnt and maybe i have a typo somewhere.

Good luck

-The King

---

### Post by SonicTheHedgehog on 2007-02-20
Does this work with the VGA-out port?

---

### Post by dmcdante on 2007-02-20
thanks so much, very good work. 
it's people like you that make linux what it actually is. 
biggest thanks.

greets, dante

---

### Post by featherking on 2007-02-20
@SonicTheHedgehog
yes simply attach another monitor and if you have followed the tutorial run 'switchmon #' replace number with whatever xorg you are trying to run, then restart x (ctrl+alt+backspace)

@dmcdante
thanks im glad it works for you

---

### Post by TecnoVM64 on 2007-02-20
Thanks dude! Finally a howto that actually worked on my laptop with an Intel 915 :)
I tried s-video and dual and both worked with almost no modification at all (and I'm using arch linux, not ubuntu) :)

---

### Post by featherking on 2007-02-20
@TecnoVM64
Thats great to hear! Most TVs wont go higher than 800 x 600 on an svideo connection so you really shouldnt need to modify that file much, but as i said, if you have a seperate monitor/projector with a huge native resolution you could easily modify that in its appropriate xorg, again, congratulations!

---

### Post by groggyboy on 2007-02-21
this is exciting.  being unable to use my laptop's s-video in ubuntu was one of the final things preventing me from wiping windows from my box.  if what TecnoVM64 says is true, and this *does* work with the i915...  \\:D/   too bad its so hackish.  but whatever, restarting my X session and killing beryl is a hell of a lot easier than rebooting into windows just to watch a movie!

that said, it's really late in my part of the world right now.  i'll have to test this in the morning.  i'll get back with an update then!

now if only i could get all my favourite games to play nicely with linux...

---

### Post by featherking on 2007-02-21
@groggyboy
I know exactly what you mean, i wanted to put youtube videos up on the screen for the whole family to enjoy, and i could never get it to work. So one day i actually got kind of close to making it work so i kept digging and finally did get it to work! Then i wanted also to use a projector, etc etc.. But i agree i wish there were an easier way.. I suspect though that this will work with any intel board using the i810 driver (and alot of them do)

---

### Post by groggyboy on 2007-02-21
update: s-video is a success (i915 on Ubuntu) - i haven't tried either of the dual monitor setups because I don't have another monitor to test them on.

thanks a bunch!

to other people wanting to try this out: it is rather hackish, and not for the faint of heart.  even the tiniest typo or missing line in your xorg.conf file can (and will) prevent X from loading.  i forgot to add an "endSection" line to the s-video xorg file, and it caused an error (easily fixed from the command line though).

now if only these xorg.conf setups were hotswappable...

---

### Post by featherking on 2007-02-21
@groggyboy
good to hear! i had thought about trying to create a script better than my 'switchmon' terminal script. My thought was to just click a shortcut and have it - switch to metacity from beryl, switch to the proper xorg file, and then restart x. All by double clicking a link. But that may be a project for another day..

---

### Post by gardara on 2007-02-21
I just tried your tip and it seems to work pretty good... However I can't figure one thing.... I have a widescreen laptop but a FS LCD monitor, now what I would like to do is to keep the WS resolution on the laptop but have FS resolution on the LCD monitor but I don't seem to get it working.... neither with Dual Monitor or Clone Desktop... Does this maby have something to do with that I had to have 915 resolution installed to get proper WS resolution on my laptop.... ?

Edit: Hmm, I noticed another thing, videos always appear black on my second monitor. I have to choose x11 video output and it has terrible quality :(
And another thing. Does anyone know how to let OpenOffice presentation apper in full screen  on the second monitor when I have dual monitor selected?

---

### Post by featherking on 2007-02-22
@gardara
I dont think you can play video on the second monitor, this is an excerpt from the i810 man page:
> NOTE: Video overlay functions will not work on the second head in this mode.

If you must have your video play on your other monitor you can try adding this in your "Device" section:
```
Option "FlipPrimary" "True"
```
That may or may not work, but it also says that it can sometimes cause the text to appear odd.

As for your other monitor, i have not played with different resolutions a great deal, i would try adding your FS monitor resolution into the "Screen" section for your FS monitor. In my example look at the file xorg.conf.dual and go to the "Screen" section with the "CRT" identifier. On the line that begins with "Modes" add the resolution of your FS monitor. For example if my monitor resolution is 1600x1200 then my line now looks like this:
```
Modes   "1600x1200" "1024x768" "800x600" "640x480"
```

---

### Post by featherking on 2007-02-23
@ALL
I have edited the original how to in the svideo configuration. When running in Svideo mode it will now clone your display to the tv. The behavior before was to have the TV act as a second desktop, but i think (for me) this new configuration will be a more desirable configuration. I tested playing a youtube video on my laptop and it correctly was displayed via svideo on the tv.

To those who used the how to before: You can just make the changes listed in the new svideo configuration to your current xorg.conf.svideo or just repeat that entire step of creating the new xorg.conf.svideo

---

### Post by Ripfox on 2007-02-23
You ARE the king bro! Thanks alot, works perfecto!

---

### Post by Ripfox on 2007-02-24
Oh, wow it's a bad trade off...I like the dual monitor, but video is blued out on the tv now. Can you please repost the original svideo file please? It worked with dvds and other video files on the tv.

---

### Post by featherking on 2007-02-24
@ripfox
ive posted the original back and added an option for a cloned mode. So now you have svideo where the tv acts as a seperate desktop and one where it clones your laptop monitor and tv monitor. However, you should not have any problems playing video in either setup, i tested both on my laptop fine. Could you please post your xorg that you are having video problems with?

---

### Post by Ripfox on 2007-02-24
It was the second xorg.svideo file you posted, Switchmon 1. Worked before with dvds, but the second config decided not to play video, just a blue screen in VLC or Gxine.




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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
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
	Identifier "SVIDEO"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "FlipPrimary" "True"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Option "Clone" "True"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768 800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

---

### Post by dgermann on 2007-02-25
featherking--

Followed all your instructions, and then did switchmon 2, and I got "unexpected end of file".

Any idea what would be the fix?

Thanks for doing this fantastic work, featherking!

---

### Post by featherking on 2007-02-25
@ripfox
Thats really strange that it doesnt play the video, as i said i have no problems at all.. Perhaps i will try testing some more things on it.. The only difference between the xorg you posted and the one i use for that is in the "Display" section yours looks like this
```
SubSection "Display"
Depth 24
Modes "1024x768 800x600" "640x480"
EndSubSection
EndSection

```
And mine looks like this:
```
SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
```
The only difference(besides the resolution) is the quotation marks around each individual resolution, in your xorg your were missing some inbetween 1024x768 and 800x600, but i dont see how that would affect the video.. You could try and see, but i did put that original xorg back up if you want to switch back

@dgerman
I found the typo, follow the howto just at the beginning when it creates the 'switchmon' script. I was missing something and it is now fixed..!

---

### Post by Ripfox on 2007-02-26
Yea, the original one works again...weird. Oh well if it works, it doesn't need fixin'! BTW, anyone here know why Regnum wont launch with the Intel embedded graphics? I was playing it forever on my box with an Nvidia card, no problems, but now that I got this lappy, no go. I have tried everything it seems, and I DO have Beryl running and all, so my video is ok...
*note* I don't try to run it while running Beryl

Any help is appreciated!

---

### Post by dgermann on 2007-02-26
featherking--

OK, will do.

Thanks!

---

### Post by featherking on 2007-02-27
@ripfox
not sure what the issue was with the other xorg, it does work fine on my machine..? oh well, glad the original works

@dgermann
let me know if that script works for you, i was missing 'fi' and thats all it took to mess things up!

---

### Post by groggyboy on 2007-02-28
hey folks:

i took the liberty of modifying featherking's switchmon script to automate things even further.  my version disables/enables beryl and restarts the X-session as well as switching xorg files.  so when you run the script, all you have to do is log back in.

note: i included commands for disabling beryl in both KDE and GNOME - you have to uncomment the appropriate lines for your DE (or comment out both if you don't use beryl).  if you take a look at the script, it should be pretty self-explanatory.

here it is:```
#!/bin/sh
#
cmd=${0##*/}                              # Command's basename
msg="\n\tUsage: $cmd [1|2|3|4]\n\t\t1 = single monitor\n\t\t2 = SVideo 
Dual Monitor\n\t\t3 = Svideo Clone\n\t\t4 = Dual Monitor\n\t\t5 = Clone 
Desktop"

if [ $# -lt 1 ]; then
	echo $msg
	exit 0
fi 
if [ $1 = "4" ]; then
	echo -e "\nChanging to Dual Monitor mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "5" ]; then
	echo -e "\nChanging to Cloned Desktop mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.clone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "3" ]; then
	echo -e "\nChanging to S-Video(Clone) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.sclone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "2" ]; then
	echo -e "\nChanging to S-Video(Dual) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.svideo /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
elif [ $1 = "1" ]; then
	echo -e "\nChanging to single monitor mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment out both if you don't use Beryl.
	mv ~/.config/beryl-manager.off ~/.config/autostart/beryl-manager.desktop # <-GNOME
	#mv ~/.kde/beryl-manager.off ~/.kde/Autostart/beryl-manager.desktop # <-KDE
	sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 1
else
	echo "Invalid Number" $msg
	exit 0
fi
```
if, like me, you have a roommate who hates the command line, you can create buttons in your gnome-panel to make things even easier.  to make them: right click the panel and choose "Add to Panel...".  choose "Custom Application Launcher" and set the type to "Application in Terminal".  Give it a name, icon, and comment.  For command, it should say "switchmon 1" - repeat this for every xorg configuration you use, replacing "switchmon 1" with the appropriate switchmon command.

now if only i could get gnome to automatically log back in...

cheers, groggyboy

---

### Post by featherking on 2007-02-28
@groggyboy
You script works great here. I am going to replace mine in the original 'how to' with this script. I hope you are okay with that, if not post and i will take it down!

Also, I just added in groggyboys new script, and added a section at the bottom on how to 'Create a Gnome Launcher'. I never thought of posting my launcher so I posted the command that I use in my own launcher. The command of course can be changed to any certain script you want to run. (i.e. 'switchmon 2' all the time instead of my command)

---

### Post by featherking on 2007-03-01
@ALL with blue video issues
Ive been playing around with the svideo clone configuration some (the one i usually use) and as i said when i first created it, i never had any video playback issues. I have discovered a fix for xine and mplayer but not for VLC. I have added it to the main howto near the bottom. The blue video on the tv that appears is not an xorg bug or an xorg error, it is how these programs use xorg to overlay the video on the TV.

@ripfox
i believe these fixes would get that clone svideo mode working for your video playback. I am now running all 5 xorg.confs with no problems

---

### Post by groggyboy on 2007-03-01
> **featherking said:**
> You script works great here. I am going to replace mine in the original 'how to' with this script. I hope you are okay with that, if not post and i will take it down!

glad you like it!;) 

cheers, groggyboy

---

### Post by Bitmastro on 2007-03-06
Hi all!
Regarding the blue video issue, following the directions on [http://intellinuxgraphics.org/man.html](http://intellinuxgraphics.org/man.html), (on the monitorlayout and clone option) you cannot have video overlay on both pipes. so using Option "MonitorLayout" "LFP+TV,NONE"  should work :-? 
i can't test this right now, but maybe this could be useful for someone.
bye!

---

### Post by featherking on 2007-03-06
@bitmastro
Ive read the man page before and have actually tried quite a few different configurations of this (LFP+TV,NONE or TV+LFP,NONE or NONE,TV+LFP or NONE,LFP+TV etc. etc) and was never able to get it to do anything regardless of what the man page says. On my laptop, either X would not start or it would turn off my laptop screen and nothing would appear on the TV.

Using the fixes for blue video I have posted in the 'How To' I run the 'Svideo Clone' mode with no problems. Having said that, if you do find a way to get this to work let me know because some programs still have the blue video issue despite the fixes (VLC for example)

---

### Post by zachstruck on 2007-03-06
I just tried out this excellent tutorial, and everything works fine except one thing.  The TV screen is black and white (and slightly wavy too).  I know that it's not the s-video cable since it works fine with my DVD player.  Any reasons why this may be?

---

### Post by featherking on 2007-03-07
@zachstruck
Odd, I havent heard of any problems, and i havent had any problems with B&W screen myself... What conf are you trying to use? and please post your xorg.conf that is giving you the B&W screen

---

### Post by zachstruck on 2007-03-07
Well, I have i915.  And my xorg is just a copy-and-paste of the examples.  Both s-video clone and the s-video dual screen both give a black and white screens.  Additionally, the screen on the TV doesn't fill the height of the TV.
I am using Fiesty, which has xorg 7.2.  Perhaps that's causing the problem.

---

### Post by featherking on 2007-03-08
@zachstruck
Well i searched through the forums and most of the people having black and white svideo issues are A. using a PAL tv or B. using an nvidia card.. Not alot of help in either case. I am inclined to agree with you that perhaps it is xorg 7.2... But that doesnt make a whole lot of sense because you are still using the i810 driver which i dont believe has changed..

One piece of advice i did see was some people were helped by changing this line:
```
Option "TVOutFormat"    "SVIDEO"
```

to this:
```
Option "TVOutFormat"    "COMPOSITE"
```

That shouldnt fix anything but some people did report that it gave them color on their svideo. I am trying to hunt down xorg 7.2 so i can play with it myself but until then perhaps you could try changing that line...?

EDIT: Well hunting down Xorg 7.2 is proving to be a challenge for edgy. Find this source, compile these install that. Im afraid if it is a problem with xorg 7.2 then you may have to wait it out. As a side note, i didnt think feisty had 7.2 installed by default..? you can check what you are running by typing 'Xorg -version' at the terminal. I am running 7.1.1

---

### Post by zachstruck on 2007-03-08
I tried the "COMPOSITE", but it didn't change anything.  I also tried just commenting it out, but that didn't do anything either.
I searched around the Internet, and it does seem that people with PAL TVs have this black and white problem, but I live in the States and use NTSC.
And my Xorg is 7.2.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2

```

I think that I am going to downgrade and reinstall Edgy sometime next week.  I'll let you know if there's any difference.

---

### Post by featherking on 2007-03-08
I tried looking some more but i continue to only find PAL issues.. If you do downgrade to edgy please let me know. I even downloaded the newer i810 driver to look at it but i didnt notice anything that looked different concerning svideo.. As i plan on upgrading to feisty (maybe RC1 or RC2) i hope that the svideo function isnt broken....?

---

### Post by Biochem on 2007-03-10
Thanks Featherking your scrip work perfectly well with the clone to VGA monitor.

However, I need some help with the dual monitor. I cannot put application on the second monitor. There is always part of them on the laptop screen Even if there is room on the VGA.  :confused: 

This is my xorg.conf for the dual monitor. Maybe a generous soul can tell me what is wrong with it.

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
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ca"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"multix"
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
	Option		"MaxTapTime"		"0"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```

---

### Post by geoffree on 2007-03-13
This may not happen as I intend it as this is my first time in this forum so please excuse any mistakes.  The script by FeatherKing is a well thought out piece of work but a little beyond my dealing with.  I bought my first notebook, a Sony Viao, with a 15" screen and an Intel GeForce card.  I want to run it through a Sony 17" E200 monitor which can do with XP but I sent that OS to the trash and am running Ubuntu ver. Dapper Drake.  When I connect the exterior monitor to the notebook port, nothing happens; a blank screen.  In addition, the F keys do not function.  Is there either a simple script to help. I dont need to go back and forth if that would make a difference.  Or is there a How To that would address this issue in somewhat simpler terms than FT. 

Many thanks,  Geoffree

---

### Post by veloce on 2007-03-13
> **Biochem said:**
> Thanks Featherking your scrip work perfectly well with the clone to VGA monitor.

However, I need some help with the dual monitor. I cannot put application on the second monitor. There is always part of them on the laptop screen Even if there is room on the VGA.  :confused: 

This is my xorg.conf for the dual monitor. Maybe a generous soul can tell me what is wrong with it.



i can't see anything wrong with your xorg, however your symptoms sound similar to some I had - couldn't drag windows to certain parts of the screen.  I found the solution in an obscure part of this forum. From my notes:

Gnome remembers some settings that kills things!  Delete the ~/.gconf/desktop/gnome/screen folder. i.e. from home folder:

 sudo rm -r ./.gconf/desktop/gnome/screen 

might work for you.

---

### Post by spankymasterc on 2007-03-13
is there any way to undo what i just did cuz now i cant start ubuntu! lol i dont know what i did wrong but i give me a long error ...... good thing i have my windows dualbooting.... anywayz anyway to get into ubuntu and undo what i did thnx in advance plz i need hlep....

---

### Post by featherking on 2007-03-13
@Biochem
Veloce's advice is the only thing i can think of. I have not tested many of the vga settings as i do not use that configuration that much. Let me know if it works and i will add it to the first post in the 'how to'

@spankymasterc
if you followed the 'how to' steps exactly, then you need to restart your computer and select recovery mode. Once you get to a terminal simply type:
```
switchmon 1
```

and restart. If you followed steps exactly you have just restored your original file.

---

### Post by spankymasterc on 2007-03-14
nvm i got it all i did was sudo dpkg-reconfig xserver-xorg and i got it running dont know what i did wrong but im good now XD

---

### Post by zachstruck on 2007-03-14
featherking,
On my issue of the black and white output, I reinstalled Edgy today.  Unfortunately, I had no more luck with it either.  The output on Edgy is the exact same as with Feisty.
The output is still black and white.

---

### Post by Biochem on 2007-03-14
THANK YOU Veloce,
deleting the ~/.gconf/desktop/gnome/screen folder effectively did the trick. :guitar:

@ Featherking: Once I deleted the folder I restarted X but it didn't change anything. However once I rebooted it was fixed.

---

### Post by featherking on 2007-03-15
@zachstruck
i hate to say it but i have absolutely no idea what would cause that.. Like i said before, everything i pull up is about nvidia cards or scart adapters.. sorry :(

@biochem
i will add that to the bottom of the 'how to'. congrats

---

### Post by ahmad1986 on 2007-03-16
Many thanks for ur effort featherking,

Could u plz explain each of the 5 modes more clearly, cuz i got confused on reading them!

All What i want to do is to have the tv and/or laptop screen works displaying the same content.

I have an output SVideo and TV input is composite so i use a converter.

My graphics card is :

```

#lspci | grep 915
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

i have copied ur svideo file and modified it a little to my settings and here it is now :

```

Section "Module"

    Load        "dbe"  	# Double buffer extension
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

    Load        "freetype"
    Load       "glx"
    Load       "dri"

EndSection

Section "Files"

    FontPath   "/usr/share/fonts/misc/"
    FontPath   "/usr/share/fonts/Type1/"
    FontPath   "/usr/share/fonts/100dpi/"
    FontPath   "/usr/share/fonts/75dpi/"

EndSection

Section "ServerFlags"

EndSection

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"

    Option "AutoRepeat" "500 30"

    Option "XkbRules"	"xorg"
    Option "XkbModel"	"pc104"
    Option "XkbLayout"	"gb"

EndSection

Section "InputDevice"

    Identifier	"Mouse1"
    Driver	"mouse"
    Option "Protocol"     "Auto"	# Auto detect
    Option "Device"       "/dev/input/mice"
    Option "ZAxisMapping" "4 5"

    Option "ZAxisMapping"   "4 5 6 7"

    Option "Emulate3Buttons"

EndSection

Section "InputDevice"
   Driver  	"synaptics"
   Identifier  	"TouchPad"
   Option	"Device"  	"/dev/input/mouse0"
   Option	"Protocol"	"auto-dev"
   Option	"LeftEdge"      "1700"
   Option	"RightEdge"     "5300"
   Option	"TopEdge"       "1700"
   Option	"BottomEdge"    "4200"
   Option	"FingerLow"	"25"
   Option	"FingerHigh"	"30"
   Option	"MaxTapTime"	"180"
   Option	"MaxTapMove"	"220"
   Option	"VertScrollDelta" "100"
   Option	"MinSpeed"	"0.09"
   Option	"MaxSpeed"	"0.18"
   Option	"AccelFactor"	"0.0015"
   Option	"SHMConfig"	"on"
 EndSection

Section "Device"
	Identifier "SVIDEO"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "FlipPrimary" "True"
	Option "TVStandard"	"PAL"
	Option "TVOutFormat"	"COMPOSITE"
	Option "ConnectedMonitor"	"TV"
	Option "Clone" "True"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Laptop"
	Option		"DPMS"
#	HorizSync	30 - 81
#	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
#	HorizSync	30-50
#	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

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

Section "ServerLayout"
	Identifier	"LaptopandTV"
	Screen		"TV"
	InputDevice "Mouse1" "CorePointer"
    	InputDevice "TouchPad" "AlwaysCore"
    	InputDevice "Keyboard1" "CoreKeyboard"
	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LaptopandTV"
EndSection


```

Now I have the picture displayed on both monitors but the TV is black-white image!!!

Any help will be much appreciated. 

Best Regards

---

### Post by hanretty on 2007-03-16
I am new to Linux and love ubuntu because it is so friendly to linux dummies.  I have a widescreen laptop (1280x800) and wish to do dual screens with a 1280x1024 LCD.  I tried the code but haven't gotten it to work.  A lot of my errors when I try anything other than xorg.conf.single come from 	
        FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc
These directories do not exist, but the /misc, /Type1, /100dpi, /75dpi do exist in /etc/X11/fonts/X11R7/.  The others (/cyrillic, /100dpi/:unscaled, /75dpi/:unscaled, /usr/share/fonts/X11/misc) do not.  Do these not exist just because i may have my computer not set up just like yours?  Any ideas how i can make this work?  Also, why does the xorg.conf.single work fine if these directories and files do not exist, but the others simply crash?  These scripts are well written and seem like they should work perfectly once you change the resol to what you want.  Any help would be great. 
(I am also getting errors from the "Device" part of the code but the only thing I have plugged into my laptop is a 3 button Kensington optical mouse which should cause a problem, I hoping this will magically disappear onece i fix the other problems)

---

### Post by featherking on 2007-03-16
@amahd1986
Im not sure if there is a fix for people using adapters and having a black and white screen. Ive heard of the issue but as i cant see it myself im not really sure how to fix it. The only thing i can suggest is try changing the line where you have 'Option "TVOutFormat" "Composite"' to read "Option "TVOutFormat" "SVIDEO"'    See if that changes anything

@hanretty
the font errors dont matter, ive had them since i first installed linux, never had a problem. Post the xorg.conf.dual so i can see if you have edited everything right. Also run 'lspci' and post the output and do you use beryl? Post these and we will start to figure out whats wrong. Start with the lspci output if you will...

---

### Post by brettr on 2007-03-18
So this is pretty wicked, they all seem to work for me, except i seem to have issues with using the resolutions specified in xorg.conf. GDM/GNOME seem to mess with it all. It just uses whatever resolution it wants, then if i set it in the system --> preferences --> Screen resolution, it will remember it. Also, why does the keyboard shortcut ctrl + alt + + or ctrl + alt + -  not switch the resolution.


Second Question: 

When i use the X11 (XImage/SHM) Driver the video does not get stretched to full screen. Just wondering if this is normal?

---

### Post by T8y8 on 2007-03-19
This was exactly what I've been looking for. Great Job

However, it doesn't seem to be Fiesty Friendly yet. When it restarts the GDM, it hangs at running local boot scripts.

---

### Post by hanretty on 2007-03-19
```
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x1024" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	32

	SubSection "Display"
		Depth	32
		Modes	"1280x1024" "1280x800" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection


```

I am assuming that the LCD is my 1280x800 laptop screen and the CRT is the 1280x1024 Dell monitor. My lspci output is:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

``` 

I do not run beryl.

---

### Post by hanretty on 2007-03-19
In addition, am i using the correct xorg.conf file (the dual one) for what I am trying to do?

---

### Post by hanretty on 2007-03-19
Nevermind, i got it working now :) Very nice!!!!
One more question though:  Is there a way that I can have a whole desktop background image on each monitor?  Right now it took my background and stretched it to fit both screens as if they were a whole.  This isn't really a problem, just a matter of looks.

---

### Post by headphase on 2007-03-19
I have a e1405 with a gm945 chipset and I just bought a 1440 x 900 widescreen monitor and I can't get it into widescreen mode like my other mointor(1280x800).
Here's my Xorg:
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load 	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
	Option  "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```
And here's the dual Xorg:
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```

---

### Post by hanretty on 2007-03-19
No worries about the background.  Everything work beautifully now.  It wasn't working because I must have for some karmatic reason, I for got to save the file after I set the CTV default depth back to 24.  At the end of the day, all I had to do was comment out the beryl line, change the resolutions to what I wanted, and add the 1280 x 1024 (for the 2nd monitor) to my list of resolutions.  Many thanks for the code (and clear instructions, and help) !!

---

### Post by featherking on 2007-03-19
@hanretty
glad you got it working, i tried to make the directions as simple as possible (its pretty complicated anyways though) so its understandable to miss one or two steps

@headphase
both of the xorg.conf's you posted were the same.. your original xorg will be named xorg.conf.single if you want to post that. But before you do that try looking [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1471810&postcount=4") for tips on configuring a 1440 resolution.

My suggestion would be to add "1440x900" to your "CRT" "Display" section if you have used your widescreen monitor successfully before in ubuntu. But if this is the first time you have set it up, try following the directions in that post and see if you can get it going. All the lines that affect your external monitor are under "CRT" in your xorg.conf (or xorg.conf.dual)

---

### Post by headphase on 2007-03-19
featherking: here's my new dual Xorg:
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "AL1917W"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "False"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"AL1917W"
	Option		"DPMS"
	HorizSync	30 - 83
	#VertRefresh	56 - 76
        #1440x900 @ 60hz
         modeline "1440x900" 108.000 1440 1520 1672 1904 900 903 909 934 +hsync +vsync
        #1280x1024 @ 60hz
         modeline "1280x1024" 108.000 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier  "AL1917W"
   	Device      "AL1917W"
    	Monitor     "AL1917W"
    	DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1440x900" "1280x1024" "1024x768" "800x600"
        #ViewPort    0 0
	Virtual     1440 900
    EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "AL1917W" LeftOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```
I am still having problems with adjusting it to ws resolution

---

### Post by featherking on 2007-03-20
@headphase
That xorg looks okay to me.. The only other thing I can think of to try is playing around with 915resolution. It should be available in the repo's. I had to use it in order to get my laptop to display 1280x800, perhaps you have to use it to enable 1440x900 since both resolutions are widescreen.

Try running '915resolution' from the terminal and see if you have it on your system. If you do, I believe there is a tutorial somewhere on the forums that describes how to use. Perhaps then you can add '1440x900' using it?

---

### Post by headphase on 2007-03-20
That worked! I just needed to reinstall my 915resolution!

---

### Post by featherking on 2007-03-21
@headphase
Awesome! glad you got it going

---

### Post by groggyboy on 2007-03-21
> **T8y8 said:**
> This was exactly what I've been looking for. Great Job

However, it doesn't seem to be Fiesty Friendly yet. When it restarts the GDM, it hangs at running local boot scripts.

I just installed feisty on my machine last week, but i haven't gotten around to trying out featherking's svideo tweak on it.  just a thought - i know from my own experience and from reading the forums (like [here]("http://www.ubuntuforums.org/showthread.php?t=384862"), [here]("http://www.ubuntuforums.org/showthread.php?t=386013") and [here]("http://www.ubuntuforums.org/showthread.php?t=383753")) that feisty is still rather glitchy when it comes to killing the X Session (ie, using ctrl+alt+backspace doesn't work for me).

i suspect that the line in the switchmon script that reads "sudo pkill Xorg" may be causing T8y8's problem.  if my hunch is right, feisty users should probably comment out that line and manually restart Xorg using one of the suggestions in the forums i linked to.

it's late over here, but i'm gonna test out this theory tomorrow.

---

### Post by groggyboy on 2007-03-21
okay, so i tested out the svideo-dual and svideo-clone xorg files on my feisty box.  as long as they are set up correctly with no typos, they'll work.

the problem lies with the switchmon script.  more specifically, as i suspected, the command "sudo pkill Xorg" doesn't work.  it's a known bug - i guess that's why feisty is still only an alpha release ;-) .

the simplest solution is to replace every instance of "sudo pkill Xorg" in the switchmon script with "sudo reboot".  obviously, this makes your computer restart, which may not be desirable for everybody.

if you don't want to do that, your other option is to comment out "sudo pkill Xorg".  then, every time you run the script, you'll have to switch to a terminal by hitting "ctrl+alt+F1".  login, and from there you can run "sudo /etc/init.d/gdm restart".

until a fix is released, feisty users are stuck with both of these less-than-desirable solutions.  :(

---

### Post by featherking on 2007-03-21
@groggyboy
good to know and im glad that the svideo still works in feisty! Hopefully they will sort out that ctrl+alt+backspace issue..

---

### Post by Xvani on 2007-03-22
there has to be an easier way to do dual screen. Is there a graphical way? I am on a laptop and I switch between different screens every day (3 in total) - no way in hell I'm replacing my xorg.conf file every time I wanna boot. That is NOT user-friendly.

other OS's do this so well, what keeps (k)ubuntu from doing it?

---

### Post by featherking on 2007-03-22
@Xvani
It takes a little work to setup but its nothing to swap xorgs.. especially if you create a shortcut to the script then you merely double-click and log back in.. Sure theres a lot going on in the background when you double click but hey it works

---

### Post by veloce on 2007-03-23
> **Xvani said:**
> there has to be an easier way to do dual screen. Is there a graphical way? I am on a laptop and I switch between different screens every day (3 in total) - no way in hell I'm replacing my xorg.conf file every time I wanna boot. That is NOT user-friendly.

other OS's do this so well, what keeps (k)ubuntu from doing it?

There are a number of solutions to this.  Personally, I just un/comment out two lines of my xorg.conf and restart X with ctl+alt+bksp.  

Best thing I've seen is: 
[http://www.fmi.uni-passau.de/~zimmerma/xlayout_chooser/](http://www.fmi.uni-passau.de/~zimmerma/xlayout_chooser/) 
but I haven't bothered installing it so far.

---

### Post by Xvani on 2007-03-30
How do I know which one to use for my LCD screens though? How do I know I wont **** them up? v-sync and so might screw everything up?

And although I don't know what it does, it says "CRT" or "Generic monitor" on the clonescreen. I have an LCD. Will that matter?

---

### Post by Xvani on 2007-03-30
i get: 
/usr/bin/switchmon: 10: Syntax error: "(" unexpected (expecting "then")

when trying to run: "switchmon 3"

what to do? :)

---

### Post by rlopezpe on 2007-03-30
featherking,

I have modified my xorg over 50 times already using what other people claim it worked on their computers with No Luck!  I think is time to try some help.  I use your solution also and I do see my two screens with a green light meaning they're gettin some signal but they're just pitch black and my X server wont start.

I need to get this working, this is my computer at work and I finally got permission to install Linux on it so I need to get it working propperly since Everyone here has a dual monitor setup.

Here is my hardware info:
- 945G Intel Chipset
- Dual monitor one regular and one Digital. They are both flat panels Acer the regular one is a AL1706 and the digital is AL1716. Both 17"
-Just in case I have a Dell Optiplex GX620.

Any Ideas why this would happen?

What's supposed to be my Option "MonitorLayout" values, DFP, LFP? I think I have tried all combinations anyways.

Please throw some Ideas here, thanks.

---

### Post by nedkelly on 2007-04-01
Has any one found a solution for the black and white issue, for Pal standard tv's??

It is really annoying since everything else works perfectly!!! 

Thanks to featherking for making this how to

---

### Post by jondska on 2007-04-01
Hi,
I am very new to this and I am just trying to output to my TV but I am following your dual monitor guide. I have an e-GEForce mx4000 dual video card and trying to run the svideo to my TV. In step 2, when entering the code for the svideo dual monitor version of the xorg, I get "command not found". How do I fix? Thanks.

---

### Post by featherking on 2007-04-01
@xvani
you have a typo somewhere in your switchmon script. Try comparing the one on your machine to the one in the howto

@rlopezpe
all i know is i have never been able to get anything to work with a dual monitor setup unless i was using CRT,LFP. however, i am using it on a laptop so the LFP always has to be last. try posting your original working xorg here and then post a copy of your xorg.dual that isnt working. Also, when does your xorg crash, is it after you login or before?

@jondska
this how to only works if you are using an intel graphics card. your e-GEForce is probably an nVidia, so you will have to find another how to sorry

---

### Post by chronniff on 2007-04-02
This works perfectly on my cpu and much thanks to you guys, however has anyone tried getting something likethis working on the new linuxmce?  I'm too much of a newb to figure it out on my own..thanks

---

### Post by roystonvasey on 2007-04-02
> **featherking said:**
> @jondska
this how to only works if you are using an intel graphics card. your e-GEForce is probably an nVidia, so you will have to find another how to sorry

oh, foo. all this time I thought I was doing somethin' wrong when, really, I've got an nvidia card. you might want to put a note at the top of this how-to for newbs like me to explain this :\

---

### Post by jjordan on 2007-04-03
It should be possible to do this with a single xorg.conf with multiple serverlayout sections.  Then call xstart with the name (indentifier) of the appropriate serverlayout section.

Someone smarter than me could probably figure out how to test for the presence of the monitor or television connection and automatically choose the correct layout.  



- j

---

### Post by motin on 2007-04-06
> **Xvani said:**
> there has to be an easier way to do dual screen. Is there a graphical way? I am on a laptop and I switch between different screens every day (3 in total) - no way in hell I'm replacing my xorg.conf file every time I wanna boot. That is NOT user-friendly.

other OS's do this so well, what keeps (k)ubuntu from doing it?

You are certainly right. A blueprint describing this issue is available here: [https://blueprints.launchpad.net/ubuntu/+spec/xorg-config-ui/](https://blueprints.launchpad.net/ubuntu/+spec/xorg-config-ui/) with the full specification at: [https://wiki.ubuntu.com/GraphicalXConfiguration](https://wiki.ubuntu.com/GraphicalXConfiguration)

Reading it, you will find some good news - like that there already exists this kind of programs and that the next version of Xserver 7.3 should be able to switch configuration without needing a restart. The for the time being bad news are that the tools are not integrated with Ubuntu yet (but please do try them out anyway - they might just as well work as you wish), and that Xserver 7.3 is not released before May and will earliest be incorporated in the version after Feisty - so maybe this fall we have what we wish for!

> **nedkelly said:**
> Has any one found a solution for the black and white issue, for Pal standard tv's??

It is really annoying since everything else works perfectly!!! 

Thanks to featherking for making this how to

I couldn't have said it better myself. Experiencing the same B&W issues, everything else works great including playing movies on the cloned/dual Svideo TV screens. After looking for a way to do this for ages (rounding up a lot of threads on the issue: [http://ubuntuforums.org/showthread.php?t=259816](http://ubuntuforums.org/showthread.php?t=259816)), I can only say: Big thanks for sharing your great solution to making this relatively simple!

> **jjordan said:**
> It should be possible to do this with a single xorg.conf with multiple serverlayout sections.  Then call xstart with the name (identifier) of the appropriate serverlayout section.

Someone smarter than me could probably figure out how to test for the presence of the monitor or television connection and automatically choose the correct layout.  
- j

True. I hope we'll see an update in this fashion later!

> **T8y8 said:**
> This was exactly what I've been looking for. Great Job

However, it doesn't seem to be Fiesty Friendly yet. When it restarts the GDM, it hangs at running local boot scripts.

I guess this is an outdated post, as everything I mentioned above is after following this guide on Feisty Beta. 

> **groggyboy said:**
> okay, so i tested out the svideo-dual and svideo-clone xorg files on my feisty box.  as long as they are set up correctly with no typos, they'll work.

the problem lies with the switchmon script.  more specifically, as i suspected, the command "sudo pkill Xorg" doesn't work.  it's a known bug - i guess that's why feisty is still only an alpha release ;-) .

the simplest solution is to replace every instance of "sudo pkill Xorg" in the switchmon script with "sudo reboot".  obviously, this makes your computer restart, which may not be desirable for everybody.

if you don't want to do that, your other option is to comment out "sudo pkill Xorg".  then, every time you run the script, you'll have to switch to a terminal by hitting "ctrl+alt+F1".  login, and from there you can run "sudo /etc/init.d/gdm restart".

until a fix is released, feisty users are stuck with both of these less-than-desirable solutions.  :(

A note to Feisty users: This guide works for Feisty Beta!

---

### Post by kevinlyfellow on 2007-04-10
Thanks feathery regent, I really wanted to do this, and now I have :-)

BTW here's a quick zenity oriented script if anyone is interested

```

#!/bin/sh

whichmode=`zenity --list --radiolist \
 --title "Change Display Mode" \
 --text "Choose where you want to display your desktop." \
 --column="" --column="" --column="Options" \
 "" "1" "Just the Laptop's LCD" \
 "" "2" "Dual Monitor with SVideo" \
 "" "3" "SVideo Cloned Desktop" \
 "" "4" "VGA Dual Monitor" \
 "" "5" "VGA Cloned (projector mode)"`

if [ $whichmode -gt 0 ]
then
        gksudo switchmon $whichmode
fi

```

---

### Post by featherking on 2007-04-11
@kevinlyfellow
Your King enjoys your praise! glad you got it working and that zenity script is neat

---

### Post by gejr on 2007-04-17
I've had the problem of having blue video in VLC when connected to my TV for a long time. I just found a solution that worked for me, so maybe it can help someone else as well. 

First, the X11 output worked for me. In VLC: Settings -> Preferences -> Check the "Advanced Options" checkbox in the lower right corner -> Video -> Output modules -> Change "Video output module" to X11. -> Save -> Play movie.

BUT, this X11-module shows the video in worse quality than it should. So, I wasn't really satisfied with this. However, when I changed Option "TVStandard" to "PAL-G" in xorg.conf my laptop monitor video screen becomes blue, but the tv-image becomes perfect. So it's the other way around. It's most perfect in my eyes.

So many europeans probably want to change this to PAL-G and see if that helps you:9

---

### Post by motin on 2007-04-17
> **kevinlyfellow said:**
> Thanks feathery regent, I really wanted to do this, and now I have :-)

BTW here's a quick zenity oriented script if anyone is interested
...

Hey thanks! I added it to System -> Settings -> Switch Monitormode with a monitoricon and it's like it's a part of base install.

---

### Post by chronniff on 2007-04-18
that zenity script is dope.......I just wanted to voice my praise to kevinlyfellow......as well as to you featherking......much thanks

---

### Post by StreLochKi on 2007-04-23
Hello,

I can't get it to work :confused: 

I have a HP compaq dc7600 with on board i810
and the last ubuntu
In my pci ex slot is a digi expantion of the onboard grafix crard
in Windows it works fine
in ubuntu he loads only 1 driver and clones the screen but i want to extend

greetz

edit: the error i get is "No screens detected", in the log @ the end he says screens detected but no correct driver conf

---

### Post by veloce on 2007-04-23
> **StreLochKi said:**
> Hello,

I can't get it to work :confused: 

I have a HP compaq dc7600 with on board i810
and the last ubuntu
In my pci ex slot is a digi expantion of the onboard grafix crard
in Windows it works fine
in ubuntu he loads only 1 driver and clones the screen but i want to extend

greetz

edit: the error i get is "No screens detected", in the log @ the end he says screens detected but no correct driver conf

post your xorg.conf and let's have a look.  By latest Ubuntu, do you mean 7.04?

---

### Post by motin on 2007-04-25
> **featherking said:**
> @zachstruck
Well i searched through the forums and most of the people having black and white svideo issues are A. using a PAL tv or B. using an nvidia card.. Not alot of help in either case. I am inclined to agree with you that perhaps it is xorg 7.2... But that doesnt make a whole lot of sense because you are still using the i810 driver which i dont believe has changed..

One piece of advice i did see was some people were helped by changing this line:
```
Option "TVOutFormat"    "SVIDEO"
```

to this:
```
Option "TVOutFormat"    "COMPOSITE"
```

That shouldnt fix anything but some people did report that it gave them color on their svideo. I am trying to hunt down xorg 7.2 so i can play with it myself but until then perhaps you could try changing that line...?

EDIT: Well hunting down Xorg 7.2 is proving to be a challenge for edgy. Find this source, compile these install that. Im afraid if it is a problem with xorg 7.2 then you may have to wait it out. As a side note, i didnt think feisty had 7.2 installed by default..? you can check what you are running by typing 'Xorg -version' at the terminal. I am running 7.1.1

> **zachstruck said:**
> I just tried out this excellent tutorial, and everything works fine except one thing.  The TV screen is black and white (and slightly wavy too).  I know that it's not the s-video cable since it works fine with my DVD player.  Any reasons why this may be?

> **zachstruck said:**
> Well, I have i915.  And my xorg is just a copy-and-paste of the examples.  Both s-video clone and the s-video dual screen both give a black and white screens.  Additionally, the screen on the TV doesn't fill the height of the TV.
I am using Fiesty, which has xorg 7.2.  Perhaps that's causing the problem.

> **zachstruck said:**
> featherking,
On my issue of the black and white output, I reinstalled Edgy today.  Unfortunately, I had no more luck with it either.  The output on Edgy is the exact same as with Feisty.
The output is still black and white.

> **featherking said:**
> @amahd1986
Im not sure if there is a fix for people using adapters and having a black and white screen. Ive heard of the issue but as i cant see it myself im not really sure how to fix it. The only thing i can suggest is try changing the line where you have 'Option "TVOutFormat" "Composite"' to read "Option "TVOutFormat" "SVIDEO"'    See if that changes anything

@hanretty
the font errors dont matter, ive had them since i first installed linux, never had a problem. Post the xorg.conf.dual so i can see if you have edited everything right. Also run 'lspci' and post the output and do you use beryl? Post these and we will start to figure out whats wrong. Start with the lspci output if you will...

> **nedkelly said:**
> Has any one found a solution for the black and white issue, for Pal standard tv's??

It is really annoying since everything else works perfectly!!! 

Thanks to featherking for making this how to

> **gejr said:**
> I've had the problem of having blue video in VLC when connected to my TV for a long time. I just found a solution that worked for me, so maybe it can help someone else as well. 

First, the X11 output worked for me. In VLC: Settings -> Preferences -> Check the "Advanced Options" checkbox in the lower right corner -> Video -> Output modules -> Change "Video output module" to X11. -> Save -> Play movie.

BUT, this X11-module shows the video in worse quality than it should. So, I wasn't really satisfied with this. However, when I changed Option "TVStandard" to "PAL-G" in xorg.conf my laptop monitor video screen becomes blue, but the tv-image becomes perfect. So it's the other way around. It's most perfect in my eyes.

So many europeans probably want to change this to PAL-G and see if that helps you:9

> **ahmad1986 said:**
> Many thanks for ur effort featherking,

Could u plz explain each of the 5 modes more clearly, cuz i got confused on reading them!

All What i want to do is to have the tv and/or laptop screen works displaying the same content.

I have an output SVideo and TV input is composite so i use a converter.

My graphics card is :

```

#lspci | grep 915
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

i have copied ur svideo file and modified it a little to my settings and here it is now :

...

Now I have the picture displayed on both monitors but the TV is black-white image!!!

Any help will be much appreciated. 

Best Regards

> **featherking said:**
> I tried looking some more but i continue to only find PAL issues.. If you do downgrade to edgy please let me know. I even downloaded the newer i810 driver to look at it but i didnt notice anything that looked different concerning svideo.. As i plan on upgrading to feisty (maybe RC1 or RC2) i hope that the svideo function isnt broken....?

> **zachstruck said:**
> I tried the "COMPOSITE", but it didn't change anything.  I also tried just commenting it out, but that didn't do anything either.
I searched around the Internet, and it does seem that people with PAL TVs have this black and white problem, but I live in the States and use NTSC.
And my Xorg is 7.2.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2

```

I think that I am going to downgrade and reinstall Edgy sometime next week.  I'll let you know if there's any difference.

Summarized the Black and white issue with PAL TVs and i810 driver here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/109934](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/109934)

All who are having the same problem should visit this bugreport and mark it as confirmed!

---

### Post by adt41287 on 2007-04-25
awesome!! i have been looking for something like this.. i cant wait to get home and try it!!! i will let you know how it goes.

---

### Post by featherking on 2007-04-25
@motin
Wow that is alot of posts about black and white issues! they really start to add up, good idea opening up a bug report

@adt41287
Hopefully it works well for you, if not post back!

---

### Post by adt41287 on 2007-04-26
i can not for the life of me get this working.. 
i am using feisty fawn, but not using beryl. the chip is an Mobile Intel 915GM Express
i had it hooked up to my Tv the whole time and saw some flickers and a couple of the times i would get an image but black and white and split into 3 sections not very clear... i tried starting all sections but no luck

---

### Post by extremecarver on 2007-04-26
edited:
Hi Featherking - this was about the tenth howto I tried to setup dualview and the first one that worked - though I get frequent crashes 

1. However how do I can use a 6. th format (or I am fine if it is either number 2 or 3 as I never ever use tv-out) which only shows CRT! (it's possible for me to do that by rebooting and during boot having the external monitor enabled) - Found out how to do it. I have to leave X - then FN-F8 (or whatever is configured for your notebook to switch the screen) and then restart X and it works. - For 2-4 I haven't yet found out how to achieve.

2. Is it possible to have in dualview CRT as prime monitor and Laptop as second? Under windows this works (allso there too it crashes sometimes).
If I switch outside x to the CRT with FN-F8 and then try to login I get thrown back and says crash so I have to change with FN-F8 to laptop lcd before restarting in a switchmon mode.

3. How is it possible in Clonemode to use the bigger CRT in lets say 1280x1024 and use the laptop screen in 1280x800 with scrolled overscan?
4. Is it possible to use different refresh rates in clone mode, as 50 or 60hz on CRT looks really bad and hurts my eyes?

Thank you very much - you made my day.

---

### Post by extremecarver on 2007-04-26
One more question: do you know why I have many many problems to log in as normal user but as root it works nearly allways?

---

### Post by motin on 2007-04-28
> **extremecarver said:**
> One more question: do you know why I have many many problems to log in as normal user but as root it works nearly allways?

Since you followed this guide? Check the permissions of the X configuration files as well as do a:

```
 sudo chown YOURUSERNAME /home/YOURUSERNAME -Rc
 sudo chmod u+r /home/YOURUSERNAME -Rc 
```

... to make sure you can access all files in your home directory. 

If it is not a problem related to this guide, I beg you to start a new thread on the issue. It is not very polite to even innocently hijack another thread.

---

### Post by hanretty on 2007-05-02
First of all, thanks to Featherking for this code.  I've been using it for awhile now and it works great and makes my colleagues jealous :)  The problem is that since I have upgraded to feisty and installed beryl (i didn't forget to uncomment the line in the switchmon script) I cannot use dual screen.  The problem comes from the restarting X.  When i restart X, i am met with the hated blue screen.  This happens even when using the single.dat file, forcing me to do a sudo reboot to get my computer back up (but then it works fine, i.e. no blue screen->a normal boot).  Has anyone else had this issue?  Anyone, have a solution?  I miss my dual screen............

---

### Post by featherking on 2007-05-02
@hanretty
what happens if you manually disable beryl before you run the script to go dual screen? (at least switch the window manager to metacity) Does X still crash?

---

### Post by hanretty on 2007-05-04
Good idea.  I switched to Metacity and then went to dual screen and it worked.  However, when I am in dual screen, i can't switch back to Beryl.  I can open the beryl manager (the emerald icon, or from a terminal) and click on Beryl, but nothing happens.  Did this several times but it did not switch to Beryl.    Beryl is real cool and all, but I may just have to settle with Metacity for dual screen (at work) and save Beryl for single screen (at home).Any ideas as to why I can't switch to Beryl while in dual screen? (switchmon 4)

---

### Post by featherking on 2007-05-06
@hanretty
I have never been able to get beryl on a dual screen at my setup. I have always done just as you described metacity for dual screen, beryl for single screen. If you do figure out how to get beryl on both, please let me know. As for not being able to switch to beryl via the script, that part was actually contributed by someone else. i used to always manually switch to metacity. I will play around with the script and let you know

---

### Post by henryhynd on 2007-05-08
thanks so much for this article. I'm new to linux and this was the one final thing stopping me from deleting my windows partition! DOWN WITH WINDOWS!!!

I do however, have one problem:

I managed to get my DVICO FusionHDTV DVB-T usb working not too long ago, and then only by disabling the desktop effects that i had running. Now I face the same black window in kaffeine that i was getting before i turn off the effects.

I'm running a Dell Inspiron 6000 with a 17" LCD (Acer AL1714) attached. I upped the ram to 1GB and apart from that it is your stock standard inspiron 6000. I was wondering if anybody had the same problem after implementing this method, or knows whats happening?

THanks very much.
Henry

---

### Post by Hasen_A on 2007-05-08
> Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection
As far as I have experienced, using 2 Screens will not let you drag windows between them. I am using an ATI card, but I think this issue is only X-Server relevant.

I am using 1 Screen with an Option for a second monitor and windows dragging works. Heres my device section. Try finding an equavalent to "DesktopSetup" for your grafik card.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
########### DualScreen with 2 LCDs ##########################
	Option "DesktopSetup"  "horizontal,reverse" #Enable Big Desktop
	Option "Mode2"         "1024x768" #Resolution for second monitor
	Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
	Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 31-61
	Option "VRefresh2" "60" #This sets the refresh rate of the secondary display. 56-75
	#Option	  	"ForceMonitors" "crt1,tmds1,notv"	#Doesn't really work, use "EnableMonitor" instead
	Option	    "EnableMonitor" "notv,tmds1,crt1"
	Option	    "PairModes" "1280x1024+1024x768"
#############################################################
EndSection

```

---

### Post by Hasen_A on 2007-05-08
Great Job ob explaining featherking. Ive got my configuration with an ATI working :).

I still have a problem with the resolution changing between two of my xorg.confs. My clone mode needs a resolution of 1024x768 on my LCD monitor so that my old Television will be able to clone it.
When in dual mode, I use **1280x1024+1024x768**=(DVI LCD)+(Analog LCD).

When I change between the two with your script, I have to set the resolution accordingly with gnome-display-properties. Is there a way to pybass this with a command in the script?
```
gnome-display-properties --help
``` didn't reveal anything useful.

---

### Post by featherking on 2007-05-09
@Hasen_A
I would think that you could just change the resolutions available in your xorg.conf.clone. What i mean is make 1024 x 768 the only available resolution. Then whenever you load that conf file it will switch to the available resolution automatically when X is restarted. Look in your xorg for Section "Screen" then SubSection "Display" then Modes and the resolution that is the furthest left of all the resolutions listed is the default. So if you have ```
SubSection "Display"
                Depth           24
                Modes           "1280x800" "1024x768" "800x600"
        EndSubSection
```

then try changing it to this
```
SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
```

Always make a backup of your working file before you begin messing around. However, this should automatically load 1024x768 whenever this conf file is used. When you use the xorg.conf.dual those resoIutions are stored in a seperate file so you dont need to change anything else. I hope i understood your question. Let me know..

---

### Post by Hasen_A on 2007-05-10
Thanks, I solved the first problem myself and you are right about Gnome remembering the dual screen resolution correctly. The problem was that without 
```
SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
```I switched the resolution by hand and when going back to dual mode via script, it would keep that first resolution.

Thanks a bunch, happy with my TV right now.

---

### Post by featherking on 2007-05-10
@Hasen_A
So what ended up working to fix it? did you edit your xorg like my suggestion or did you just find a command to add to the xorg rotater script. You say you switch the resolution by hand? are you just manually changing the resolution and then running the script? Sorry for all the questions i just want to understand what the problem and solution are, thanks

---

### Post by Hasen_A on 2007-05-12
@Featherking:
I've got everything working the way I want. I changed the xorg.conf to 
```
SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
``` and Gnome does remember the resolution settings when switching xorg.confs with you're script and the resolution is kept the same. All I do now is run the script, no follow-ups.

---

### Post by lummer on 2007-05-12
hi, can someone please help me?

in step 2, after i type 

sudo /etc/X11/xorg.conf.svideo


I keep getting the error ...

sudo: /etc/X11/xorg.conf.svideo: command not found

Please help!

Thanks in advance.

Leon

---

### Post by veloce on 2007-05-12
> **lummer said:**
> hi, can someone please help me?

in step 2, after i type 

sudo /etc/X11/xorg.conf.svideo


I keep getting the error ...

sudo: /etc/X11/xorg.conf.svideo: command not found

Please help!

Thanks in advance.

Leon

I suspect that's because that line should be:

sudo gedit /etc/X11/xorg.conf.svideo

---

### Post by Hasen_A on 2007-05-13
The command is ```
sudo gedit /etc/X11/xorg.conf.svideo
```

**gedit** is the text program, which is opened with super user rights using the **sudo** command. /etc/... is the path you are opening to edit. You'll get used to using bash commands. I hated them at first, but now it's kind of nice.

---

### Post by aromboli on 2007-05-13
Hi, I followed all the steps, and unfortunatelly I can no manage to have my Acer Travelmate 2410 (Intel 915GM/GMS, 910 GML Express Chipset Familiy) with my external screen (Acer AL1917) working as dual screen. When I switch it to dual, I get a blank screen in my computer and a bleu one in the external screen. Any ideas? This is the file content:

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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

---

### Post by veloce on 2007-05-13
> **aromboli said:**
> 
Any ideas?


Yes, but just ideas.  YMMV.

> **aromboli said:**
> 

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection


Are you sure that you have the HorizSync and VertRefresh correct for the different monitors?

> **aromboli said:**
> 

Section "Screen"
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"

	SubSection "Display"
		Depth	24
		Modes	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection



xorg may have the two screens around the wrong way, try starting with the same resolution for both.

Lastly, if you are using Feisty, try getting the two screens working without Xinerama first.  (You get separate sessions on each monitor rather than one across the two).

---

### Post by lummer on 2007-05-14
@veloce
@Hasen_A

Thanks guys, that did it. Now the next problem...

I do get an output, but not the correct one, the 2nd screen goes white with a black border(kinda like in the days of ZX Spectrum). The main screen goes black.

If I ctrl-del-backspace then it allows me to logon on but then goes to the situation described above.

To remedy I have to boot into safe mode and switchmon 1.

any suggestions?

Thanks in advance!

---

### Post by veloce on 2007-05-14
Another thing that goes wrong is that the card cannot cope with the screen depth of 24 bit when running dual screen.  This is probably a memory issue.  Make sure you allow for it to drop to 16bit (or lower with older equipment).  

This means having these options included in the screens sections of the xorg.conf.

For those who have asked here's my xorg.conf:

```
##########################################################################################
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This version by: Kerry Mayes, February 2007.
# For Dell Latitude D520 with external Viewsonic VE710b Monitor connected via docking station.
# 
# As an edited file, it will not be automatically updated on xserver-xorg package upgrades. 
#
# I have not run the following command to allow it to be automatically updated:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#
# Updated by: Kerry Mayes, May 2007 for Feisty changes
# Xinerama no longer used as xorg now runs a session for each monitor.
##########################################################################################
#
# These sections have not been altered except to update for Feisty
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
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
#
##########################################################################################
#
# First device section, will control the Laptop LCD screen
Section "Device"
       Identifier      "D520 945GM 0"
       Driver "i810"
       BusID "PCI:0:2:0"
       # This next line is required for xinerama.
       Screen 0
       # It was stated somewhere that the LFP is always the second pipe. Make sure never 
       # to have a space after the "," it's interpreted as "None". 
       Option "MonitorLayout" "CRT,LFP"
       # I don't think these next lines are actually required.
		Option          "BackingStore" "true"
      Option          "DevicePresence" "on"
      Option          "DisplayInfo" "FALSE"
      Option          "DRI" "true"
       Option			  "CacheLines" "1024"
EndSection
#
##########################################################################################
#
# Second device section, will control the external screen 
Section "Device"
       Identifier "D520 945GM 1"
       Driver "i810"
		 # Even though there is a second pci address for the card, only this one is used for 
		 # the external monitor.  The other may be for the svideo out but that has not been
		 # confirmed.
       BusID "PCI:0:2:0"
       # This next line is required for xinerama.
       Screen 1
       # It was stated somewhere that the LFP is always the second pipe. Make sure never 
       # to have a space after the "," it's interpreted as "None". 
       Option "MonitorLayout" "CRT,LFP"
       # I don't think these next lines are actually required.
		 Option          "BackingStore" "true"
       Option          "DevicePresence" "on"
       Option          "DisplayInfo" "FALSE"
       Option          "DRI" "true"
       Option			  "CacheLines" "1024"
EndSection
#
##########################################################################################
#
# First Monitor section, for the Laptop LCD screen.
Section "Monitor"
   Identifier      "D520 Monitor"
   # I can't find a definitive source for these values, but these are the ones Fiesty came up with.
	HorizSync	28-70
	VertRefresh	43-60
   DisplaySize     304 228     # From manual
   Option          "DPMS"
EndSection
#
##########################################################################################
#
# Second Monitor section, for the Viewsonic monitor connected to the docking station.
Section "Monitor"
       Identifier "Viewsonic VE710b Monitor"
       # These values are from the monitor's manual.
       HorizSync       30-82
       VertRefresh     50-75
       DisplaySize	338 270
       Option "DPMS"
EndSection
#
##########################################################################################
#
# First screen section, connects the first device to the Laptop LCD screen.
# Note that the resolution "1400x1050" wasn't available until I had installed 915resolution
Section "Screen"
       Identifier      "D520 Screen"
       Device          "D520 945GM 0"
       Monitor         "D520 Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           24
               Modes           "1400x1050" "1280x1024" "1024x768" 
               viewport 0 0
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1400x1050" "1280x1024" "1024x768" 
               viewport 0 0
       EndSubSection
EndSection
#
##########################################################################################
#
# Second screen section, connects the second device to the Viewsonic monitor connected to 
# the docking station.
Section "Screen"
       Identifier "Viewsonic VE710b Screen"
       Device "D520 945GM 1"
       Monitor "Viewsonic VE710b Monitor"
       DefaultDepth 24
       SubSection "Display"
               Depth 24
               Modes "1280x1024" "1024x768"
               # This next line has been found useful when xinerama automatically makes 
               # the two screens the same virtual size - this command can be used on the 
               # lower resolution screen to limit it to the resolution it can display 
               # without scrolling.
               # virtual 1280 1024
               viewport 0 0
       EndSubSection
       SubSection "Display"
               Depth 16
               Modes "1280x1024" "1024x768"
               # This next line has been found useful when xinerama automatically makes 
               # the two screens the same virtual size - this command can be used on the 
               # lower resolution screen to limit it to the resolution it can display 
               # without scrolling.
               # virtual 1280 1024
               viewport 0 0
       EndSubSection
EndSection
#
##########################################################################################
#
# The serverlayout section to put it all together.  
# Currently I use this file for both Laptop only and Dual screens so have to comment things 
# out or put them back in each time I switch.
#
Section "ServerLayout"
       Identifier      "Default Layout"
       # For the Intel, having a screen number in these lines seems to get it confused.
       Screen       "D520 Screen" 0 0
       # Comment out the next two lines to use just the laptop screen.        
       Screen       "Viewsonic VE710b Screen" LeftOf "D520 Screen"
#       Option "Xinerama" "on"
       Option "Clone" "off"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"
       InputDevice     "Synaptics Touchpad"
EndSection
#
# Sometimes gnome remembers layout stuff that screws up the screen - you can't drag windows
# into certain parts of the screen and so forth.  The solution I found on the forums was to
# delete the following directory: [home directory]/.gconf/desktop/gnome/screen
#
#
##########################################################################################
#
# These sections not altered.
Section "ServerFlags"
EndSection

Section "DRI"
       Mode    0666
EndSection
#
##########################################################################################
```

---

### Post by lummer on 2007-05-15
@veloce, thanks again. I got it working. Simply by choosing clone output instead of extended desktop.

Still not working properly though I still have a big black border around the 2nd screen output.

any suggestions ?

thanks!

---

### Post by veloce on 2007-05-15
> **lummer said:**
> @veloce, thanks again. I got it working. Simply by choosing clone output instead of extended desktop.

Still not working properly though I still have a big black border around the 2nd screen output.

any suggestions ?

thanks!

That sounds like a resolution issue.  xorg is not driving the screen at a high enough resolution.  

A couple of possibilities:
1. with clone mode it may be driving both screens at the same resolution 
2. xorg hasn't got the refresh and sync ranges for the monitor

Sorry you may have answered these before:
Are you running Fiesty?  If so, try turning of clone mode (as well as leaving xinerama off).
Do you have an Intel graphics card?  If so, try setting modes for the screens in the 915reolution config file.

---

### Post by Atrio05 on 2007-05-16
hey i was just wondering if this howto would help me in getting my s-video out on my ATI Radeon 7000/ve to work on my tv properly?

---

### Post by lummer on 2007-05-17
@veloce

Yes, I am using Feisty, the border are only on the TV screen. When I swtich off clone mode the res goes back to 1024x786 on the laptop from I think 800x600.

Yes, I have an Intel integrated graphics card. How do I set modes for the screens in the 915reolution config file?

---

### Post by extremecarver on 2007-05-17
Has anyone gotten this setup to work with the video-intel driver instead of video-i810 ????
Some patches have been applied to video-intel to save more power in the newest source.

---

### Post by veloce on 2007-05-17
> **lummer said:**
> @veloce

Yes, I am using Feisty, the border are only on the TV screen. When I swtich off clone mode the res goes back to 1024x786 on the laptop from I think 800x600.

Yes, I have an Intel integrated graphics card. How do I set modes for the screens in the 915reolution config file?

First check whether 915resolution is picking up the resolutions.  On a command line run:

```
sudo /etc/sbin/915resolution -l
```

If this lists all the graphics modes that you want to use, then you are okay.

If you need to edit the config file the command is:

```
gksudo gedit /etc/default/915resolution
```

set the xres and yres for the resolution you are not getting.

When you switch off clone mode it sounds like you get your laptop work correctly, yes?  If so, then have a look at the settings for the other monitor in your xorg.  Does your mouse move from one screen to the other correctly?  If so, you at least know that xorg has the screens around the right way. You can tweak the xorg.conf settings for your second monitor without killing your primary monitor.

So try changing the default depth of the second screen to something quite low and working with the resolutions at that level.

---

### Post by lummer on 2007-05-19
when I run..



sudo /etc/sbin/915resolution -l 


I get told command not found

---

### Post by Hasen_A on 2007-05-19
Try the following xorg.conf. I've got it working with my ATI X800. 
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configu
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
	FontPath     "/usr/share/X11/fonts/misc"	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/home/andy/fonts/MathFonts_TrueType"
EndSection

Section "Module"
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

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Buttons" "7"
	Option		"Emulate3Buttons" "true"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Resolution" "100"
#	Option		"VertScrollDelta" 	"250"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to
						# /dev/input/event
						# for USB
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to
						# /dev/input/event
						# for USB
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to 
						# /dev/input/event
						# for USB
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "P19-1A"
	HorizSync    31.0 - 64.0
	VertRefresh  56.0 - 60 #75.0 nur bis 60 da sonst da bei login falsche frequenz
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "TV"
	HorizSync    31.0 - 61.0
	VertRefresh  60.0 - 60.0
EndSection

Section "Monitor"
	Identifier	"Belinea"
	Option		"DPMS" "true"
	HorizSync	31-61
	VertRefresh	56-75
EndSection

Section "Device"
	Identifier  "DVI"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
	#Option	    	"VideoOverlay" "on"
	Option          "XAANoOffscreenPixmaps"
	Option	    	"OpenGLOverlay" "off"
	Option		"NoTV"	"yes"

#########################################################
	Option	  	"ForceMonitors" "tv,tmds1,nocrt1"
#	Option	    "EnableMonitor" "tmds1,nocrt1,notv"
#	Option		"MonitorLayout" "TMDS1,TV"
########### TV kann bis max Auflösung 1024x768 ##########
	#Option	    "DesktopSetup" "clone"
	Option	    "TVOverscan" "off" #mit off funktionieren die maße TVV.. und TVH..
	Option	    "TVHPosAdj" "0"
	Option	    "TVVPosAdj" "0"
	Option	    "TVHSizeAdj" "80"
	Option	    "TVVSizeAdj" "80"
	Option	    "TVColorAdj" "0"
	Option	    "TVStandard" "VIDEO" # folgende Option ist falsch: "TVOutFormat" "S-VIDEO"
	Option	    "TVFormat" "NTSC-M"
#### TV ### fglrx needed #############
	Option 		"DesktopSetup"	"clone" #Enable Big Desktop
	Option 		"Mode2"         "1024x768" 	#Resolution for second monitor
	Option	    	"OverlayOnCRTC2" "1"
	Option 		"DesktopSetup" 	"LVDS,AUTO" 	#the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option 		"EnablePrivateBackZ" "yes" 	#Enable 3d support <= May Not Work
	Option 	"HSync2" "65" 				#This sets the horizontal sync for the secondary display. 31-61
	Option 	"VRefresh2" "60" 			#This sets the refresh rate of the secondary display. 56-75

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "DVI"
	Monitor    "P19-1A"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480" #"1280x1024" not used cuz "out of range"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "DVI"
	Monitor    "Belinea"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
#	Screen         "TV" LeftOf "Default Screen"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSectionration tool, using
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
	FontPath     "/usr/share/X11/fonts/misc"	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/home/andy/fonts/MathFonts_TrueType"
EndSection

Section "Module"
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

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Buttons" "7"
	Option		"Emulate3Buttons" "true"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Resolution" "100"
#	Option		"VertScrollDelta" 	"250"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to
						# /dev/input/event
						# for USB
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to
						# /dev/input/event
						# for USB
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"	# Change to 
						# /dev/input/event
						# for USB
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"	# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "P19-1A"
	HorizSync    31.0 - 64.0
	VertRefresh  56.0 - 60 #75.0 nur bis 60 da sonst da bei login falsche frequenz
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "TV"
	HorizSync    31.0 - 61.0
	VertRefresh  60.0 - 60.0
EndSection

Section "Monitor"
	Identifier	"Belinea"
	Option		"DPMS" "true"
	HorizSync	31-61
	VertRefresh	56-75
EndSection

Section "Device"
	Identifier  "DVI"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
	#Option	    	"VideoOverlay" "on"
	Option          "XAANoOffscreenPixmaps"
	Option	    	"OpenGLOverlay" "off"
	Option		"NoTV"	"yes"

#########################################################
	Option	  	"ForceMonitors" "tv,tmds1,nocrt1"
#	Option	    "EnableMonitor" "tmds1,nocrt1,notv"
#	Option		"MonitorLayout" "TMDS1,TV"
########### TV kann bis max Auflösung 1024x768 ##########
	#Option	    "DesktopSetup" "clone"
	Option	    "TVOverscan" "off" #mit off funktionieren die maße TVV.. und TVH..
	Option	    "TVHPosAdj" "0"
	Option	    "TVVPosAdj" "0"
	Option	    "TVHSizeAdj" "80"
	Option	    "TVVSizeAdj" "80"
	Option	    "TVColorAdj" "0"
	Option	    "TVStandard" "VIDEO" # folgende Option ist falsch: "TVOutFormat" "S-VIDEO"
	Option	    "TVFormat" "NTSC-M"
#### TV ### fglrx needed #############
	Option 		"DesktopSetup"	"clone" #Enable Big Desktop
	Option 		"Mode2"         "1024x768" 	#Resolution for second monitor
	Option	    	"OverlayOnCRTC2" "1"
	Option 		"DesktopSetup" 	"LVDS,AUTO" 	#the types of monitors that is connected LVDS = LCD, CRT, AUTO
	Option 		"EnablePrivateBackZ" "yes" 	#Enable 3d support <= May Not Work
	Option 	"HSync2" "65" 				#This sets the horizontal sync for the secondary display. 31-61
	Option 	"VRefresh2" "60" 			#This sets the refresh rate of the secondary display. 56-75

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "DVI"
	Monitor    "P19-1A"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480" #"1280x1024" not used cuz "out of range"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Second Screen"
	Device     "DVI"
	Monitor    "Belinea"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "ServerLayout"
#	Screen         "TV" LeftOf "Default Screen"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```

---

### Post by veloce on 2007-05-19
> **lummer said:**
> when I run..



sudo /etc/sbin/915resolution -l 


I get told command not found

Then I suspect that 915resolution is not installed? I believe that it's in the universe repo, installable from Synaptic or apt directly.

---

### Post by featherking on 2007-05-21
@all
Went out of town for a week (cruise to the carribbean) sorry i havent been responding, generally i like to check this thread at least once a day. Just wanted to post to say im still here

-The King

---

### Post by ebob on 2007-05-25
I have an HP laptop with i945 graphics.  I have tried this method to get the s-video out working, but my success has been limited.  The best I have gotten so far is getting the desktop to appear on the television, but nothing else appears on it (opening a browser, playing a video, etc.).  Is there a way that I can just have the video appear on the television without appearing on the laptop screen?  I really don't care about dual monitors, only switching between the built-in LCD and the television.

UPDATE:  I have managed to get video on only the television without appearing on the built-in LCD by switching the "Monitor Layout" to "LFP,TV" in the xorg.conf.svideo file, but now whenever I play a video the computer crashes and needs a hard shutdown.

---

### Post by featherking on 2007-05-27
@ebob
Probably the only way to do it would be to create a custom xorg file that the TV as your only output device. You could try copying the xorg that outputs to TV and try editing the LFP,TV section to read TV only. I am quite sure what you are trying to do can be done, because when i was first writing the how to i remember outputting to TV only at one point. If i get some time later today i will experiment with a few things

---

### Post by isagani on 2007-05-30
This guide seriously rocks! Thanks man!

A few notes:
[LIST]
[*]Worked perfectly on my laptop
[*]Except for switching from dual to single monitor (Hangs the system)
[*]Solved by manually restarting x (alt-backspace)
[/LIST]

Thank you so much. I've spent 3 days trying to find a solution and here it is. More power to you "scripting gods".

---

### Post by Morientes on 2007-06-01
I have a laptop (lenovo 3000 c100) that has an Intel GMA 900. The laptop display has a resolution of 1024x768. Now I also have a TV that I would like to plug into the external monitor plug (not the s-video) because this way I get a very good resolution on the TV. But I would like to know if it is possible to output a widescreen resolution to the TV when the laptop itself is not widescreen?

---

### Post by suoko on 2007-06-02
Unfortunately this howto doesn't work on my feisty as far as  the tv-out question is concerned.
I got no tv output at all.

By the way, with my original single screen xorg.conf TV-out is enabled as default but in B/W.
I guess the problem is either NTSC (my tv is PAL) or, more probably the SVIDEO option (mine is COMPOSITE)
I tried adding the PAL and COMPOSITE option to the xorg single conf file but I still have B/W tv-out.
Any hints?

I still have to try connecting an external VGA monitor ant test it.

My original xorg:

Section "Device"
        Identifier      "945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "XAANoOffscreenPixmaps"
        Option          "AllowGLXWithComposite" "true"
        Option          "EnablePageFlip" "true"
        Option "TVStandard"     "PAL"
        Option "TVOutFormat"    "COMPOSITE"
        Option "ConnectedMonitor"       "TV"


EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "945GM"
        Monitor         "Generic Monitor"
        Option          "AddARGBGLXVisuals" "true"
        Option          "DisableGLXRootClipping" "true"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
....

---

### Post by Ripfox on 2007-06-05
By the way, with the new intel driver, all you have to do is plug in the s-video cable and ctrl/alt/backspace (restart the x server) as far as I can tell this works out of the box. If I am mistaken let me know...

---

### Post by voi on 2007-06-05
just used your fix to get svideo out on an acer aspire 3680... many thanks .

---

### Post by suoko on 2007-06-05
> **ripfox said:**
> By the way, with the new intel driver, all you have to do is plug in the s-video cable and ctrl/alt/backspace (restart the x server) as far as I can tell this works out of the box. If I am mistaken let me know...

That's right but it is in B/W here in Europe (where we use PAL)...
I guess they chose NTSC as default since DELL sells notebooks with this intel GPU and ubuntu preinstalled in U.S. only....

---

### Post by groggyboy on 2007-06-10
> **ripfox said:**
> By the way, with the new intel driver, all you have to do is plug in the s-video cable and ctrl/alt/backspace (restart the x server) as far as I can tell this works out of the box. If I am mistaken let me know...

this new intel driver - is it the one installed by default in feisty, or do i have to install it myself?

---

### Post by TutoWRM on 2007-06-10
It worked fine for me, i have a 950 gma and feisty installed.
Also to work with vlc:

- Options>Preferences>Video>Output Module or Out Module (I have it in spanish:D )

- Check the advanced options

- Select X11

- Save and enjoy :D

At least this is how it worked for me, i hope the same for you. :D

PD: Featherking i send you a pm with this so you can update the original post :D

---

### Post by lummer on 2007-06-12
> **groggyboy said:**
> this new intel driver - is it the one installed by default in feisty, or do i have to install it myself?

I am still having problems, so I'd like to know this too.

---

### Post by oddin85 on 2007-06-12
awesome! thanks man! i now have s-video! ^_^

---

### Post by extremecarver on 2007-06-12
> **lummer said:**
> I am still having problems, so I'd like to know this too.

Nope not installed by default:

Code: 
Sudo Apt-get video-intel

And your done. If on restart X doesn't work put in sudo dpkg-reconfigure xserver-xorg and choose video intel instead of i810 or before restarting x exchange all occurences of video-i810 by video-intel in etc/x11/xorg.conf
For Gutsy Tribe 1  it is installed by default, however video-i810 is chosen by default (since around 2 weeks gutsy allows to have both installed but X.org defaults it i810.)

---

### Post by standardissue on 2007-06-16
Method in original post works great on my  Acer Aspire 3680-2633 laptop. Thanks to the community. :0)

---

### Post by groggyboy on 2007-06-16
as ripfox and extremecarver mention, the 'intel' driver *just works*.  hitting ctl-alt-backspace with the s-video cable attached is enough to make it work, no switching of xorg files nescessary.  hell, i didn't even have to edit the xorg file for s-video to work!

it's glitchy though.  the screen resolution on the TV was the same as my laptop (1280x800), and about a quarter of the display was offscreen.  switching resolutions to 800x600 solved this.

the other problem came up when i tried to switch back to single display.  maybe i removed the s-video cable too soon, but X crashed after i tried to restart it.  a reboot didn't even fix it, as gdm wouldn't let me log in any more.

i solved things by reinstalling gdm and by switching back to the 'i810' driver.  glitches aside, the new intel driver is promising.  maybe, when i'm feeling braver, i'll try it again.  it could be i just removed the s-video cable too soon.  for now, i'll just keep using featherking's script.

---

### Post by pratik5705 on 2007-06-18
> **motin said:**
> Summarized the Black and white issue with PAL TVs and i810 driver here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/109934](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/109934)

All who are having the same problem should visit this bugreport and mark it as confirmed!

Maybe I can shed some light on this issue.

I was having the same problem when using the original xorg.conf.svideo file as posted here.  Then I experimented around a bit and got it to work in color.  Here is my modified xorg.conf file (only the sections that were changed):  

Section "Device"
         Identifier "Intel Corporation XXXXXXXXXXXX"
        Driver "i810"
        BusID "PCI:0:2:0"
EndSection
##IMP READ THIS
##The above section should be preserved from the original xorg.conf file (the one with .single extension)
## The identifier should be as it is in your original xorg.conf file.  I have put XXXXXX there so that you can replace it with your original text

Section "Device"
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"COMPOSITE"  # "SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

# NOTICE THE COMPOSITE in the TV out format.  The SVIDEO is hashed (commented out)

---

### Post by z94 on 2007-06-18
quick question...i TRIED looking through the rest of the reply's...lookng for my problem, but i didnt see it...i may have missed it, and if i did, let me know, for i dont want to waste anyones time...but when i start up dual monitors, (i dont use the S-port whatever, just the VGA and the dual "cloned" desktop works fine...) but when i have the extended one...my Laptop goes white. after about econds, but on my second monitor, i have the extended screen...i can still see the mouse on my laptop, and i just 'guessed' clicked and draged the task bar thingy to the other monitor, where i could see what i was doing, so i coul set it back to single screen...but if anyone has a solution, or needs specs on my laptop/monitor, please let me know. feel free to email me, Instand Message (aim) me, or reply on here...ill be sure to check back. I appreciate anyone who takes the time to read this. Thanks

-aL

AIM-Thisispathetic20
Email- [email]Thisispathetic20@yahoo.com[/email]

thanks again

---

### Post by subliminal727 on 2007-06-22
THANK YOU!  this worked perfectly.  thats pretty much the last thing i needed to replace from windows...i think my ubuntu partition on this laptop might be getting a whole lot bigger soon.

---

### Post by harty83 on 2007-06-25
For anyone interested, I found a thread [here]("http://ubuntuforums.org/showthread.php?t=255608")  that gave a xorg file that uses mergedfb instead of xinerama for dual monitor setup so that beryl/compiz will work.  It places the external "above" the laptop so that the screen height and width will play nice with compiz/beryl.  

Here is the xorg.conf file (which I named xorg.conf.dual-mergedfb) 

```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "i2c"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection
Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"

        VideoRam        131072

        Option  "DRI"                           "true"
        Option  "MergedFB"                      "true"
        Option  "MonitorLayout"                 "CRT,LFP"
        #Option "DDC"                           "false"
        Option  "VBERestore"                    "true"

        Option  "SecondPosition"                "Above"
        Option  "MetaModes"                     "1280x800-1280x1024"
        Option  "SecondMonitorHorizSync"        "31-81"
        Option  "SecondMonitorVertRefresh"      "56-76"

        Option  "XAANoOffscreenPixmaps"         "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync 30-81
        VertRefresh 56-76
        DisplaySize 350 700
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x800" "1280x1024"
                Virtual         1280 1824
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

And I edited the switchmon script to include it (note, I use compiz fusion so I commented out the beryl lines)
```

#!/bin/sh
#
cmd=${0##*/}                              # Command's basename
msg="\n\tUsage: $cmd [1|2|3|4|5|6]\n\t\t1 = Single Monitor\n\t\t2 = SVideo Dual Monitor\n\t\t3 = Svideo Clone\n\t\t4 = VGA Dual Monitor (Xinerama)\n\t\t5 = VGA Dual Monitor (Mergedfb)\n\t\t6 = VGA Clone Desktop"

if [ $# -lt 1 ]; then
	echo $msg
	exit 0
fi 
if [ $1 = "4" ]; then
	echo -e "\nChanging to VGA Dual Monitor (Xinerama) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	#mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "5" ]; then
	echo -e "\nChanging to VGA Dual Monitor (MergedFB) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	#mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.dual-mergedfb /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "6" ]; then
	echo -e "\nChanging to VGA Cloned Desktop mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	#mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.clone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "3" ]; then
	echo -e "\nChanging to S-Video(Clone) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	#mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.sclone /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
fi
if [ $1 = "2" ]; then
	echo -e "\nChanging to S-Video(Dual) mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment both out if you don't use Beryl.
	#mv ~/.config/autostart/beryl-manager.desktop ~/.config/beryl-manager.off # <-GNOME
	#mv ~/.kde/Autostart/beryl-manager.desktop ~/.kde/beryl-manager.off # <-KDE
	sudo cp /etc/X11/xorg.conf.svideo /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 2
elif [ $1 = "1" ]; then
	echo -e "\nChanging to Single Monitor mode"
	# The following two lines are important only if you use Beryl.
	# Uncomment the appropriate line for your DE.  Comment out both if you don't use Beryl.
	#mv ~/.config/beryl-manager.off ~/.config/autostart/beryl-manager.desktop # <-GNOME
	#mv ~/.kde/beryl-manager.off ~/.kde/Autostart/beryl-manager.desktop # <-KDE
	sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
	sudo pkill Xorg
	echo
	exit 1
else
	echo "Invalid Number" $msg
	exit 0
fi
```

---

### Post by Sirchristopher on 2007-07-17
This is exactly what I have been looking for.  The only problem is I am very new and I don't know how to edit the script to fit my needs.  When I type 'sudo /etc/X11/xorg.conf.svideo'  I am given an error ' sudo: /etc/X11/xorg.conf.svideo: command not found'  Can you help me proceed from here?

---

### Post by lagartoflojo on 2007-07-17
Okay, I'll clear it up for ya.

"sudo" is a command that says "I want to do something as root" (root being the administrator, ie super-user).
So when you want to edit a file that can only be edited by root, you need to tell sudo what program you want to use to edit the file:```
sudo someprogram thefile
```What you are typing is simply "sudo thefile"; you are not telling sudo what program to run. What you need to do then is to tell sudo that you want to edit the xorg.conf.svideo file with, say, nano:```
sudo **nano** /etc/X11/xorg.conf.svideo
```
But maybe those command-line text editors are too ugly and hard to use for you. That's okay, you can use a graphical text editor like "gedit". To do this though, you don't become the super-user with "sudo" but with "gksudo". The difference is subtle; you can read more about it here: [http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo").
Assuming that you are using Ubuntu and not Kubuntu, hit ALT+F2 on your keyboard. This will open the "Run" dialog. Type```
gksudo gedit /etc/X11/xorg.conf.svideo
``` and hit ENTER. Now enter your password, and you'll be editing your xorg conf files in a graphical editor. Nice!

---

### Post by motin on 2007-07-18
> **Sirchristopher said:**
> This is exactly what I have been looking for.  The only problem is I am very new and I don't know how to edit the script to fit my needs.  When I type 'sudo /etc/X11/xorg.conf.svideo'  I am given an error ' sudo: /etc/X11/xorg.conf.svideo: command not found'  Can you help me proceed from here?

Be sure to read up on how to restore the original xorg.conf from the recovery console before proceeding. Or you'll have a hard time getting up the graphical interface if something goes wrong.

---

### Post by Sirchristopher on 2007-07-18
I'm in business!!!  Now I can use my s-video.  I have one more question....My display on my TV is in black and white.  How do I change it?  (Also my laptop's resolution is now 800x600 but I think it is from displaying both it and my s-video at the same time)

---

### Post by lagartoflojo on 2007-07-18
Yeah, mine's in B&W also, and unfortunately I have not been able to solve this.

---

### Post by Sirchristopher on 2007-07-19
Thanks!  You helped me understand what I was typing qnd why.  I thnk I am going to get along well with Ubuntu!

---

### Post by groggyboy on 2007-07-19
to all the people who are having problems with the television displaying in black&white:

i've noticed that simply restarting X (which is what the script on the first page will do) doesn't work right.  in order to get my TV in colour, i need to reboot the whole computer after switching Xorg files.  my tv is NTSC (i was reading how some people were having trouble with PAL tv's).  you can make the change in the script by changing every instance of "sudo pkill xorg" to "sudo reboot".

hope that helps some people having the B&W issue.

---

### Post by Sirchristopher on 2007-07-20
That fixed it.  Thank you for your help!

---

### Post by chronniff on 2007-08-07
that new driver going by the name intel does show a lot of hope for the future.......it automatically detects and launches the second monitor nicely configured to whatever the attached monitor is (I am using this on a Del inspiron laptop).......however has anybody had the trouble of not being able to switch back to the proper resolution afterword......as well has having touble booting into  single monitor mode?     also is there away to control the kind of output you want, because all I seem to get is a cloned desktop.......If you guys maybe even know a place to point me to with some info that would be great, I can't seem to find any

---

### Post by badrigate on 2007-08-11
hi,

i see two different packages in ubuntu ( feisty fawn ) -

xserver-xorg-video-i810
================
X.Org X server -- Intel i8xx, i9xx display driver
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.

&&

xserver-xorg-video-intel
================
X.Org X server -- Intel i8xx, i9xx display driver 
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.

which one should i install for a dell laptop ( inspiron 6400 ) with i945GM graphics card for a s-video output ?

thanks in advance,
cheerio,
badri.

---

### Post by badrigate on 2007-08-11
removing the post already posted.. !

---

### Post by lagartoflojo on 2007-08-11
xserver-xorg-video-i810 is the "old" driver (ie it comes with Feisty).
xserver-xorg-video-intel is the "new" driver (ie, eventually it should replace the old one).
I can tell you that I have not had a good experience with the new driver (I couldn't even log on to Gnome), but your luck might be different (my card is a 915, not a 945). I think you could try both and see which one works for you best.

---

### Post by tseliot on 2007-08-12
> **badrigate said:**
> hi,

i see two different packages in ubuntu ( feisty fawn ) -

xserver-xorg-video-i810
================
X.Org X server -- Intel i8xx, i9xx display driver
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.

&&

xserver-xorg-video-intel
================
X.Org X server -- Intel i8xx, i9xx display driver 
This package provides the driver for the Intel i8xx and i9xx family
of chipsets, including i810, i815, i830, i845, i855, i865, i915, and
i945 series chips.

which one should i install for a dell laptop ( inspiron 6400 ) with i945GM graphics card for a s-video output ?
use the xserver-xorg-video-i810

the other one is not stable (i.e. that's a snapshot of an unstable release of driver 2.0).

---

### Post by aeqvitas1 on 2007-08-12
I tried it, but after step two I got this:
daniel@daniel-laptop:~$ sudo gedit /usr/bin/switchmon
Password:
daniel@daniel-laptop:~$ sudo chmod +x /usr/bin/switchmon
daniel@daniel-laptop:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
daniel@daniel-laptop:~$ sudo /etc/X11/xorg.conf.svideo
sudo: /etc/X11/xorg.conf.svideo: command not found


I'm not too up on programming lingo and such...so any help is appreciated.

---

### Post by lagartoflojo on 2007-08-12
See post #137 in this thread, by me ( [http://ubuntuforums.org/showpost.php?p=3037354&postcount=137](http://ubuntuforums.org/showpost.php?p=3037354&postcount=137) )

---

### Post by mustali on 2007-08-14
Hi,

I need some help with xorg.conf. I am using a Dell Inspiron laptop with an external monitor. Everything was running fine. I had 1280X800 on my laptop LCD and 1280x1024 on the external Dell CRT. 

Yesterday, I got a 19" Dell LCD (E197FP) at work to replace the CRT. Unfortunately, the xorg.conf didn't like it and I can't seem to get the 1280x1024 resolution no matter what I tweak. the resolution always resets to 1024x768. The LCD's optimum resolution is 1280x1024 @60 Hz.

This is my xorg.conf
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
	Load	"bitmap"
	#Load 	"GLcore"
	Load	"ddc"
	Load	"dbe"
	#Load	"dri"
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
	Identifier "LCD"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 0
	BusID "PCI:0:2:0"
EndSection

Section "Device"
	Identifier "CRT"
	Driver "i810"
	Option "MonitorLayout"	"CRT,LFP"
	Option "DDCMode" "True"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	31 - 80
	VertRefresh	56 - 75
EndSection

Section "Monitor"
	Identifier	"CRT"
	Option		"DPMS"
	HorizSync	31 - 80
	VertRefresh	56 - 75
EndSection

Section "Screen"
	Identifier	"LCD"
	Device		"LCD"
	Monitor		"LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"CRT"
	Device		"CRT"
	Monitor		"CRT"
	DefaultDepth	24

	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes	"1280x1024" 
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes	"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandCRT"
	Screen		0 "LCD"
	Screen		1 "CRT" LeftOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandCRT"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection

```

The Xorg log file seems to identify the modes available but just can't set the resolution.
This is the Xorg log file
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux mustali-laptop 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 14 09:10:56 2007
(==) Using config file: "/etc/X11/xorg.conf"
(**) Option "defaultserverlayout" "LCDandCRT"
(**) ServerLayout "LCDandCRT"
(**) |-->Screen "LCD" (0)
(**) |   |-->Monitor "LCD"
(**) |   |-->Device "LCD"
(**) |-->Screen "CRT" (1)
(**) |   |-->Monitor "CRT"
(**) |   |-->Device "CRT"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
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
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
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
(II) PCI: 00:00:0: chip 8086,2590 card 1028,01b5 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2592 card 1028,01b5 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2792 card 1028,01b5 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,2668 card 1028,01b5 rev 03 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2662 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,01b5 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,01b5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,01b5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,01b5 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,01b5 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev d3 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2641 card 1028,01b5 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2653 card 1028,01b5 rev 03 class 01,01,80 hdr 00
(II) PCI: 02:00:0: chip 14e4,170c card 1028,01b5 rev 02 class 02,00,00 hdr 00
(II) PCI: 02:01:0: chip 1180,0832 card 1028,01b5 rev 00 class 0c,00,10 hdr 80
(II) PCI: 02:01:1: chip 1180,0822 card 1028,01b5 rev 19 class 08,05,01 hdr 80
(II) PCI: 02:01:2: chip 1180,0843 card 1028,01b5 rev 01 class 08,80,00 hdr 80
(II) PCI: 02:01:3: chip 1180,0592 card 1028,01b5 rev 0a class 08,80,00 hdr 80
(II) PCI: 02:01:4: chip 1180,0852 card 1028,01b5 rev 05 class 08,80,00 hdr 80
(II) PCI: 02:03:0: chip 8086,4223 card 8086,1020 rev 05 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,12), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,13), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xdfc00000 - 0xdfdfffff (0x200000) MX[B]
(II) Bus 12 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdfb00000 - 0xdfbfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff00000/19, 0xc0000000/28, 0xdfec0000/18, I/O @ 0xeff8/3
(--) PCI: (0:2:1) Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller rev 3, Mem @ 0xdff80000/19
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
	[0] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[1] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[2] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[3] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[4] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[5] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[6] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[9] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[1] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[2] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[3] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[4] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[5] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[6] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[7] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[8] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[9] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[10] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
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
	[4] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[5] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[6] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[7] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[8] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[9] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[10] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[13] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[14] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.7.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 915GM found
(--) Chipset 915GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[5] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[6] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[7] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[8] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[9] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[10] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[13] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[14] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[5] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[6] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[7] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[8] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[9] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[10] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[11] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[12] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[13] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[14] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(**) I810(0): Option "MonitorLayout" "CRT,LFP"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(0): Chipset: "915GM"
(--) I810(0): Linear framebuffer at 0xC0000000
(--) I810(0): IO registers at addr 0xDFF00000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 489216 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 1956860 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 98304 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1219
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1280,800)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(0): Size of device LFP (local flat panel) is 1280 x 800
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1280 x 800
(==) I810(0): Primary head is using Pipe B
(--) I810(0): Maximum frambuffer space: 98136 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1280x800
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: DEL  Model: a024  Serial#: 860108109
(II) I810(0): Year: 2007  Week: 4
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): Default color space is primary color space
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.340   greenX: 0.279 greenY: 0.619
(II) I810(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 108.0 MHz   Image Size:  380 x 305 mm
(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) I810(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) I810(0): Serial No: WH31971N3D5M
(II) I810(0): Monitor name: DELL E197FP
(II) I810(0): EDID (in hex):
(II) I810(0): 	00ffffffffffff0010ac24a04d354433
(II) I810(0): 	0411010368261e78eecaf6a357479e23
(II) I810(0): 	114f54a54b00714f8180010101010101
(II) I810(0): 	010101010101302a009851002a403070
(II) I810(0): 	13007c311100001e000000fd00384b1f
(II) I810(0): 	500e000a202020202020000000ff0057
(II) I810(0): 	4833313937314e3344354d0a000000fc
(II) I810(0): 	0044454c4c204531393746500a200055
(II) I810(0): Using hsync ranges from config file
(II) I810(0): Using vrefresh ranges from config file
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) I810(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) I810(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) I810(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) I810(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) I810(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) I810(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) I810(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) I810(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 31-80
(II) I810(0): 	VertRefresh 56-75
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 37
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 37
	LinNumberOfImagePages: 37
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 15
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 15
	LinNumberOfImagePages: 15
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 3c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 4d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*(II) I810(0): Not using mode "640x480" (vrefresh out of range)
Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "800x600" (vrefresh out of range)
Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(0): Not using mode "1024x768" (vrefresh out of range)
Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 58 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 5a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 5c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 60 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 61 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 62 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 63 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 64 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 65 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 66 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 67 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 68 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 69 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 70 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 71 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) I810(0): LCD: Using hsync range of 31.00-80.00 kHz
(II) I810(0): LCD: Using vrefresh range of 56.00-75.00 Hz
(--) I810(0): Virtual size is 1280x800 (pitch 1280)
(**) I810(0): *Built-in mode "1280x800"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(**) I810(0): Display dimensions: (380, 300) mm
(**) I810(0): DPI set to (85, 67)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(**) I810(1): Depth 24, (--) framebuffer bpp 32
(==) I810(1): RGB weight 888
(==) I810(1): Default visual is TrueColor
(**) I810(1): Option "MonitorLayout" "CRT,LFP"
(II) I810(1): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(1): Chipset: "915GM"
(--) I810(1): Linear framebuffer at 0xC0000000
(--) I810(1): IO registers at addr 0xDFF00000
(II) I810(1): 2 display pipes available.
(II) I810(1): detected 7932 kB stolen memory.
(WW) I810(1): Detected stolen memory (7872 kB) doesn't match what the BIOS reports (12288 kB)
(II) I810(1): Will try to reserve 32768 kiB of AGP aperture space
	for the DRM memory manager.
(II) I810(1): Monitoring connected displays enabled
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(==) I810(1): VideoRAM: 12288 kByte
(==) I810(1): video overlay key set to 0x101fe
(**) I810(1): page flipping disabled
(==) I810(1): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(1): BIOS Build: 1219
(==) I810(1): Device Presence: disabled.
(==) I810(1): Display Info: enabled.
(II) I810(1): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(1): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(1): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(1): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1280,800)
(II) I810(1): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Size of device LFP (local flat panel) is 1280 x 800
(II) I810(1): Currently active displays on Pipe A:
(II) I810(1): 	CRT
(II) I810(1): Currently active displays on Pipe B:
(II) I810(1): 	LFP (local flat panel)
(II) I810(1): Lowest common panel size for pipe B is 1280 x 800
(==) I810(1): Secondary head is using Pipe A
(--) I810(1): Using HW Cursor because it's enabled on primary head.
(--) I810(1): Maximum frambuffer space: 12120 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC read failed
(II) I810(1): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(1): Maximum space available for video modes: 12120 kByte
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*(II) I810(1): Not using mode "640x480" (vrefresh out of range)
Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(1): Not using mode "800x600" (vrefresh out of range)
Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(1): Not using mode "1024x768" (vrefresh out of range)
Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 58 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(1): Not using mode "1600x1200" (hsync out of range)
(II) I810(1): Not using mode "1600x1200" (hsync out of range)
(II) I810(1): Not using mode "1600x1200" (hsync out of range)
(II) I810(1): Not using mode "1600x1200" (hsync out of range)
Mode: 5a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
(II) I810(1): Not using mode "1920x1440" (hsync out of range)
Mode: 5c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000723f
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 60 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 61 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 62 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 63 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 64 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 65 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 66 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 67 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 68 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 69 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 6f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 70 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 71 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) I810(1): CRT: Using hsync range of 31.00-80.00 kHz
(II) I810(1): CRT: Using vrefresh range of 56.00-75.00 Hz
(II) I810(1): Not using mode "1280x1024" (no mode of this name)
(--) I810(1): Virtual size is 1024x768 (pitch 1024)
(**) I810(1): *Built-in mode "1024x768"
(**) I810(1): *Built-in mode "800x600"
(**) I810(1): *Built-in mode "640x480"
(II) I810(1): Attempting to use 75.03Hz refresh for mode "1024x768" (854)
(II) I810(1): Attempting to use 75.00Hz refresh for mode "800x600" (852)
(II) I810(1): Attempting to use 75.00Hz refresh for mode "640x480" (850)
(==) I810(1): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Reloading /usr/lib/xorg/modules//libramdac.so
(==) I810(1): VBE Restore workaround: enabled.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[2] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[3] 0	0	0xdfec0000 - 0xdfefffff (0x40000) MS[B]
	[4] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MS[B]
	[5] 0	0	0xdff00000 - 0xdff7ffff (0x80000) MS[B]
	[6] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[7] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[8] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[9] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[10] -1	0	0xdfbfd000 - 0xdfbfdfff (0x1000) MX[B]
	[11] -1	0	0xdfbfc700 - 0xdfbfc7ff (0x100) MX[B]
	[12] -1	0	0xdfbfc600 - 0xdfbfc6ff (0x100) MX[B]
	[13] -1	0	0xdfbfc500 - 0xdfbfc5ff (0x100) MX[B]
	[14] -1	0	0xdfbfc400 - 0xdfbfc4ff (0x100) MX[B]
	[15] -1	0	0xdfbfc800 - 0xdfbfcfff (0x800) MX[B]
	[16] -1	0	0xdfbfe000 - 0xdfbfffff (0x2000) MX[B]
	[17] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[18] -1	0	0xdfebc000 - 0xdfebffff (0x4000) MX[B]
	[19] -1	0	0xdff80000 - 0xdfffffff (0x80000) MX[B](B)
	[20] -1	0	0xdfec0000 - 0xdfefffff (0x40000) MX[B](B)
	[21] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xdff00000 - 0xdff7ffff (0x80000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[26] 0	0	0x0000eff8 - 0x0000efff (0x8) IS[B]
	[27] 0	0	0x0000eff8 - 0x0000efff (0x8) IS[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[30] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[31] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[32] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[33] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[36] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[37] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[38] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[39] -1	0	0x0000eff8 - 0x0000efff (0x8) IX[B](B)
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)915GM/910ML/915MS Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Secondary framebuffer allocation size: 6144 kByte
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 7680 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x31d99000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x3149c000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x2da78000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
(II) I810(0): Allocated 64 kB for the second scratch buffer at 0xffda000
(II) I810(0): 0x81fc088: Memory at offset 0x00020000, size 6144 kBytes
(II) I810(0): 0x81fc068: Memory at offset 0x00620000, size 7680 kBytes
(II) I810(0): 0x81fd228: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x81fd250: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x81fcf84: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81fc0a8: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81fc0c8: Memory at offset 0x0ffda000, size 64 kBytes
(II) I810(0): 0x81fd380: Memory at offset 0x0fffa000, size 4 kBytes
(==) I810(0): Write-combining range (0xc0000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffda000 (pgoffset 65498)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(WW) I810(0): Correcting plane B stride (160 -> 1024)
(II) I810(0): Mode bandwidth is 61 Mpixel/s
(II) I810(0): maxBandwidth is 1216 Mbyte/s, pipe bandwidths are 420 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		20 128x128 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): direct rendering: Disabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(WW) I810(0): Option "DDCMode" is not used
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
(==) I810(1): Write-combining range (0xc0000000,0x10000000)
(II) I810(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(1): Setting refresh with VBE 3 method.
(II) I810(1): Display plane A is enabled and connected to Pipe A.
(II) I810(1): Display plane B is enabled and connected to Pipe B.
(II) I810(1): Enabling plane A.
(II) I810(1): Enabling plane B.
(II) I810(1): Display plane A is now enabled and connected to Pipe A.
(II) I810(1): Display plane B is now enabled and connected to Pipe B.
(II) I810(1): PIPEACONF is 0x80000000
(II) I810(1): PIPEBCONF is 0x80000000
(II) I810(1): Mode bandwidth is 47 Mpixel/s
(II) I810(1): maxBandwidth is 1216 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(1): Backing store disabled
(==) I810(1): Silken mouse enabled
(II) I810(1): Initializing HW Cursor
(**) Option "dpms"
(**) I810(1): DPMS enabled
(II) I810(1): Set up overlay video
(II) I810(1): Set up textured video
(II) I810(1): direct rendering: Disabled
(II) I810(1): RandR enabled, ignore the following RandR disabled message.
(WW) I810(1): Option "DDCMode" is not used
(II) I810(1): Rotating to 0 degrees
(--) RandR disabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(EE) AIGLX: DRI module not loaded
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(EE) AIGLX: DRI module not loaded
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
(**) Option "CoreKeyboard"
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
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event5
(**) Option "Device" "/dev/input/event5"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
ProcXCloseDevice to close or not ?

```


I am also using the 915resolution patch for the Intel driver. Could this be interfering with the setup? This did not cause any problems with the CRT.

Any help would be appreciated. I got this nice LCD but I can't use it right. Not fair for the LCD :)

Thanks.

---

### Post by Samodelkin on 2007-08-22
Thank you for this guide. The part about allowing the VGA output worked for me. Unfortunately, the part about allowing the s-video output did not work, and the reason I came across this post in the first place was searching for a way to enable s-video output.

First let me say that I am a newbie at Linux. I first installed Linux this summer because Vista was being really creepy. (I mean really REALLY creepy, and I don't regret permanently replacing it.) This has been a happy-crash-course for me; so far I know how to open the console, and the basic commands for it.

Back to the subject, I followed the howto, but the television shows no reaction when I use "switchmon 3" to switch to svideo-clone mode. KDE restarts under a lower resolution, but the television remains the same - same blank screen as before I even plugged in the cable, no flashes or anything.

I am certain that the settings of the television are not the cause of the problem; I tried it on two different televisions with the right input setting. The link between the laptop and the television is not the problem, since an identical setup works with my desktop. (Windows XP) I know of no way to determine whether the s-video port on my laptop is functioning, nor what's directly connected to it. However, I would think it's unlikely that this is a hardware failure. My guess is that the contents of xorg.conf.sclone are incorrect, though I can be wrong on that. I am in the United States, so NTSC must be correct.

Known specifications of computer:
HP Compaq Presario c502us (apparently also known as c500)
No hardware-related modifications since time of purchase.
CPU: 1.86 GHz Intel Celeron M 440
System: 32-bit
OS: Kubuntu, Feisty Fawn
Environment: KDE 3.5.6

Original contents of xorg.conf:
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

These are the contents of xorg.conf.sclone I created by following the howto; I think the problem should be here somewhere:
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier "SVIDEO"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "FlipPrimary" "True"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Option "Clone" "True"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
	HorizSync	30 - 81
	VertRefresh	56 - 76
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection

```
Here are the results of lspci, just in case they may prove useful:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```
If anyone can see the mistake(s) I made trying to get s-video output, please tell me how to fix them. Help on this would be very much appreciated.

Also, I noticed that when I am in VGA Clone Desktop mode, the picture on the connected CRT monitor disappears when I close the laptop lid. That would be unfavorable, as what I am trying to do requires the laptop to remain closed. I would appreciate any pointers on how to make the s-video output (if I can get it to work) work even when the laptop's screen is closed down.

---

### Post by Hyperion_1984 on 2007-09-18
> **z94 said:**
> [...] when i have the extended one...my Laptop goes white. after about econds, but on my second monitor, i have the extended screen...i can still see the mouse on my laptop, and i just 'guessed' clicked and draged the task bar thingy to the other monitor, where i could see what i was doing, so i coul set it back to single screen...but if anyone has a solution, or needs specs on my laptop/monitor, please let me know. 

I have the same problem as z94. After restarting the x server to dual mode, I have a perfect extended desktop for the login widow. However, after I log in,  the primary monitor gets blank.

---

### Post by Hyperion_1984 on 2007-09-19
> **Hyperion_1984 said:**
> I have the same problem as z94. After restarting the x server to dual mode, I have a perfect extended desktop for the login widow. However, after I log in,  the primary monitor gets blank.

Ok, I'm replying to myself. It seems the problem is with Beryl and/or Compiz and/or the 3D desktop include with Feasty Fawn. After disabling everything which as to do with some 3D desktop features, the procedure worked.

Thanks

---

### Post by esala on 2007-09-22
I think i found a solution for the black & white issue. I wasn't getting any colors when i connected the svideo connector to my tv. When i was about to give up, i switched my windows xp and i noticed that i the screen was also black and white. I switched to my tv standard (mine was ntsc_m) from the intel graphics options (in windows). Then i went back to kubuntu and tried one more time. You can't imagine my face when i found out that the colors appeared. I review all my previous steps to check if i changed anything in the xorg configuration file, but it was the same. So the good news is that i managed to get the colors in my linux installation, the bad news is that i needed windows to get them work :P. Let me know if this worked for all of you as well.

---

### Post by punzada on 2007-09-26
> **esala said:**
> I think i found a solution for the black & white issue. I wasn't getting any colors when i connected the svideo connector to my tv. When i was about to give up, i switched my windows xp and i noticed that i the screen was also black and white. I switched to my tv standard (mine was ntsc_m) from the intel graphics options (in windows). Then i went back to kubuntu and tried one more time. You can't imagine my face when i found out that the colors appeared. I review all my previous steps to check if i changed anything in the xorg configuration file, but it was the same. So the good news is that i managed to get the colors in my linux installation, the bad news is that i needed windows to get them work :P. Let me know if this worked for all of you as well.

This worked for me also, leads me to believe that X defaults to another NTSC setting (in windows xp if I changed it to something like NTSC_441 instead of NTSC_M it was black and white just like ubuntu originally.)

Very good tip, odd problem though I wonder if there is anyway to handle it just through ubuntu or if the card really just needed to be told what to do by the correct drivers in windows xp? Good food for thought on the issue, I'm more then pleased for the moment. :)

---

### Post by hieadenna on 2007-09-27
Complete newbie here. I had Feisty Fawn for a few months, but when I found out my gaming was fairly important, I reinstalled windows. It's only been the past day or so since I want to dual boot my system. I managed to do so.

However, I need SVideo to work my laptop. My laptop monitor is almost completely dead. (I have to hulk grip it to see anything. My hand is killing me from doing so for the past two hours). I was elated when I found this article. I did everything correctly, copiped from the first post. I tried SOut and ended up getting pure white screens on my laptop and on my television. I tried SVideo clone and the system got mad at me. I'm currently working on trying to get it back to just the laptop monitor >:

I'm on an NTSC television and my graphics card is an Intel. Laptop is an Acer  Aspire 3690

---

### Post by peabody on 2007-09-28
To the OP I want to say this thread is really great, fixed me up well.  But I have two questions.

Edit: scratch number 1, Aspect ratio is only wrong in clone mode, which is to be expected since the resolution on the external will match the resolution of the laptop LCD.

1)  does anyone here use this with a widescreen laptop?  I noticed that in dual setups with a wide screen laptop, the aspect ratio seems wrong on the external monitor.  I was wondering if there was a work-around for that, or if that's simply a limitation of the current Xorg.

2) has anyone had any luck getting this to work with the xserver-xorg-video-intel driver?  I hear that's the latest intel driver for xorg and if I use that I don't need to use the 915resolution package to get my widescreen resolutions.  However, all of these setups don't seem to work with that driver.  The X server will segfault upon startup.

Edit: 

[3rd Edit: Nvm, harty's setup seems to make it so that the display adapter refuses to try any other setups.  While it works, the xserver crashes constantly after using it].

3) [2nd Edit: harty83's merged fb works nice for this] Anyone get dri working with Xinerama?  If I could get that working I wouldn't bother with a single setup, I would probably leave it on dual all the time.

4) I've heard about hotpluggable external vga support via xrandr.  Is that going to be available in feisty or will we have to wait for gutsy to get this feature?

5)  I've noticed that when I open new windows they have a tendency to default to the external display.  Is there a way to get them to default to the primary display?

---

### Post by Voullie on 2007-09-30
Hey,

I've followed this thread from the beginning and tried all the different solutions and some additional ones but still haven't got it to work. My main objective is to get a clone desktop on my TV via my s-video output.

The closest I've come  is getting the gnome login window in color with too small resolution at the same time as I get a pale, black&white picture on my TV. After loging in the screen on my laptop goes black and only the inferior quality picture on the TV remains. I tried turning off desktop effects (compiz) but this doesn't help.

In other words my problem is in two parts:
1. The picture on my laptop disappears
2. The picture on my TV is bad

I'm running feisty on a Intel GM965 chipset and the new Intel driver. Now most of the people in this thread is running the i810 driver but as far as I know this shouldn't matter. The relevant parts of my xorg.conf is attached below. 

cheers /V  


Section "Device"
	Identifier	"Allmänt grafikkort"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option 		"CacheLines" "32768"
	Option 		"DRI" "true"
	Option 		"PageFlip" "true"
	Option 		"TripleBuffer" "true"

	Option		"MonitorLayout"	"TV,LFP"
	Option		"Clone"	"true"
	Option		"TVOutFormat"	"SVIDEO"
EndSection

Section "Monitor"
	Identifier	"Allmän skärm"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60	
EndSection

Section "Monitor"
	Identifier	"TV"
EndSection

#Section "Extensions"
#	Option		"Composite" "Enable"
#EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Allmänt grafikkort"
	Monitor		"TV"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by peabody on 2007-10-12
> **Voullie said:**
> Hey,
I'm running feisty on a Intel GM965 chipset and the new Intel driver. Now most of the people in this thread is running the i810 driver but as far as I know this shouldn't matter. 

Actually, it matters a ton.  The latest intel driver doesn't support Xinerama, it's using the xrandr extension to do its work.  This is more promising for the future as it will support hotpluggable configuration.  Try this thread to get it up and running, the currently feisty doesn't have the proper version of xrandr support for this yet (v. 1.2), but the repository mentioned in the thread will hook you up.  I'm running it now:

[http://ubuntuforums.org/showthread.php?t=561865&highlight=xrandr+1.2+intel](http://ubuntuforums.org/showthread.php?t=561865&highlight=xrandr+1.2+intel)

---

### Post by jwlam on 2007-10-20
@hanretty
> 
Nevermind, i got it working now  Very nice!!!!
One more question though: Is there a way that I can have a whole desktop background image on each monitor? Right now it took my background and stretched it to fit both screens as if they were a whole. This isn't really a problem, just a matter of looks.

Mind to share what u did to achieve that?
I am also trying to get 1280x800 on my laptop and 1024x768 on external monitor.
I follow the great guide and get dual monitor working on my Dell Inspiron 6400 running Fedora 7. But both screen appear to be 1024x768.

Also, I got this error:
> [jwlam@localhost USBDISKPRO]$ system-config-display
Traceback (most recent call last):
  File "/usr/share/system-config-display/xconf.py", line 381, in <module>
    dialog = xConfigDialog.XConfigDialog(hardware_state, xconfig, rhpxl.videocard.VideoCardInfo())
  File "/usr/share/system-config-display/xConfigDialog.py", line 646, in __init__
    self.xml.get_widget("secondMonitorLabel").set_text(monitor_list[1].modelname)
TypeError: GtkLabel.set_text() argument 1 must be string, not None

and X-server will run into problems... (wallpaper missing from one of the monitors, menu bar missing, etc). Simply cant access my display settings.

Please advise. Thx.

---

### Post by jwlam on 2007-10-20
I juz switched to XFCE. running 'system-config-display' basically has no effect on desktop or the menu bar. The only problem is the same error msg. I still cannot access those settings.

---

### Post by dysphasi on 2007-10-20
Ok, I've just installed Ubuntu 7.10 and it's a bit of a mixed bag.

If I log out and back in after connecting my s-video cable I CAN get a picture on my TV. HOWEVER, it's a cloned picture. 

As such it's a bit awkward, if I fullscreen a video, it first tries to fit the screensize of the laptop, then if I go out and back in, hey presto, it fits the tv screen BUT I lose the display on the laptop entirely and have to log out and back in to get it back.

I can get around this somewhat by downing the resolution on my laptop. But it's far too hard to navigate menus etc.. like this.

Ideally I'd like a dual screen setup, with the tv screen as an extension of my desktop, letting me drag a video onto the tv and play it fullscreen there whilst I work on my laptop.

If I go to graphics options, even though I have a cloned picture on the tv, I can't select Screen 2 as a secondary screen, it's disabled (?!...even though I can see the cloned display there).


Soooo... the long and short, I thought I'd try the method listed here. Unforutnately it doesn't work, option 1 just logs me out and once I log in I'm back to normal (as I'd expect). The other options log me out, and actually disable any picture on the tv. Does this method just not work with 9.10?

Any help would be well received! .... I'm trying to ditch windows, but this isn't helping! :(


...ps I've got a VAIO VGN-C2S with a mobile intel 945GM

---

### Post by dysphasi on 2007-10-23
Ok, just to follow up on my previous posting, I've sorted out my problems.

If anyone else is interested in setting up a tv as an extension of the laptop screen please have a little ganders at my [[color=blue]**other post**[/color]](http://ubuntuforums.org/showthread.php?t=583566) :)

---

### Post by LORDs_diakonos on 2007-10-29
OK 
I am using the recommenced config from the beginning of the post.  I am using Gutsy.  The problem is that when I have the second monitor plugged in the resolution on my lcd goes down even though in the xorg.conf it is only set to use "1920x1200".  i noticed this is a problem even when running in single if the external monitor is plugged in. 

Is there a trick here?

---

### Post by Depressed Man on 2007-11-04
A question for Svideo users.. where did you find your 5 pin Svideo cable to component/composite? I'm looking for one and know that stores like Radioshack carry them. But I'm wondering if anyone has a good one they'd like to recommend.

---

### Post by extremecarver on 2007-11-05
Go for a 9 pin instead. Don't take a standard s-video cable, it won't fit (dell 630m but suppose it's like this for most s-video out with intel chip).

---

### Post by Depressed Man on 2007-11-05
How would a 9 pin fit in a 5 pin?

---

### Post by nsilva on 2007-11-15
Hey Featherking, congratulation for the hardwork and all the support you have given the community. :guitar:

Hey guys, Im trying to play some movies by S-video in my TV, I have a widescreen 29'' HDTV. 
[http://www.insignia-products.com/p-99-insignia-26-widescreen-hd-ready-flat-panel-lcd-tv-with-dvi-component-video-inputs-silver.aspx](http://www.insignia-products.com/p-99-insignia-26-widescreen-hd-ready-flat-panel-lcd-tv-with-dvi-component-video-inputs-silver.aspx)

The manufactured says** "WXGA (1366 x 768 pixels) resolution for stunning image clarity"**. When I use 800x600 I have some big black margins in the TV. Then I try adding higher value resoltuions (e.g 1270X780, etc..). I used the SwitchMon command Option 3, after logging in, I try changing the resolution through Ubuntu->Preferences->Screen Resolution, but does not give me the option of changing to the higher values I entered in the file, it only gives me the orginal options.

I tried a more desperate measure, and modify the file (by the way I'm using the s-video clone file) to look
```

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"1280 x 760"
	EndSubSection
EndSection


```

This way I thought it would be the only option possible, after logging in, I could only see a color rectangle (logging screen was fine!), couldnt see anything else - no toolbar, anything!

How can I change the file to look the best on that TV? 

Thanks

---

### Post by dysphasi on 2007-11-15
Can I just ask if anyone using Gutsy has a xinerama setup fully working using an intel 945gm?

If so, would you mind posting your xorg? Further, what driver are you using for the card? The default intel modesetting driver, or the i810? And is the 915resolution dooda needed?

I've tried a thorough search, but can't seem to find a definitive answer anywhere.

---

### Post by olavjunior on 2007-11-15
I've been playing around with the script, and I really  like this. But I can't figure out how to disable compiz and use metacity instead. It's not in the autostart in Gutsy. I tried something like ```
sleep 15s
metacity --replace
```
without success. Any ideas on how I can automate this? (The reason is that I don't like the video playback in compiz, it flikkers)

---

### Post by veloce on 2007-11-15
I got it going with xrandr, but couldn't get it the way I liked it (two seperate desktops is no longer supported) and 3dfx don't work with a virtual desktop greater than 2048 in either direction with this card.

Xinerama, while it is supposed to still work, has been replaced by xrandr.

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Also, there is a nice script to setup monitors based on what xrandr detects here:
[http://ubuntuforums.org/showthread.php?t=583566](http://ubuntuforums.org/showthread.php?t=583566)

---

### Post by dgray_from_dc on 2007-12-17
Hello all,  I have a "mini-PC" (based on the mini-ITX form factor) that uses the Intel 945 chipset.  However, this machine not only has a S-Video out, but also composite and component video.

  I've gotten this machine working in Windows where I have a cloned display where one will display in 1024x720 on the VGA out and 1920x1080p on the component out.  I'd like to get this working in Linux and dump the Windows partition.

  So far, I've been able to get maximum performance in Linux from the VGA port but nothing from the TV out.  Linux has identified the hardware, even that there is a second video out.  But when I try to set the second output to active, the X-server won't start.  I've been able to fix it by reverting to my old xorg.conf file, but can't get this working even in the most basic capacity.

This thread was all that I could find that related to my issue.  I tried the how-to and that was worse than simply turning the second output on.  (Probably because of the additional video outs).  I think that this is an exotic off-shoot of this chipset.  However, any help would be greatly appreciated.

---

### Post by motin on 2008-01-26
I just wrote a new bash+zenity script that allows choosing an appropriate xorg.conf-file without ever touching a terminal - check it out (with screenshots): [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

Someone mentioned that xinerama has been replaces by xrandr - is there any chance that someone has a xorg.conf.dual that is based on xrandr instead? Hopefully that would add DRI to the dual setup I assume?

---

### Post by lagartoflojo on 2008-01-26
> **motin said:**
> I just wrote a new bash+zenity script that allows choosing an appropriate xorg.conf-file without ever touching a terminal - check it out (with screenshots): [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)

Someone mentioned that xinerama has been replaces by xrandr - is there any chance that someone has a xorg.conf.dual that is based on xrandr instead? Hopefully that would add DRI to the dual setup I assume?

Here is my xorg.conf for dual screens. It allows me to have my 1680x1050 laptop  screen on one side and a 1280x1024 monitor on the other.
I then activate it doing:
xrandr --output LVDS --auto --right-of VGA

Got it from here:
[http://ubuntuforums.org/showthread.php?t=617934](http://ubuntuforums.org/showthread.php?t=617934)

I'm also attaching a script that automatically generates the xrandr command and allows you to set the resolution of the external screen.
Source:
[http://blog.cpinto.net/2007/10/extended-display-with-ubuntu-xrandr-12.html](http://blog.cpinto.net/2007/10/extended-display-with-ubuntu-xrandr-12.html)

I haven't tried your script yet, I will when I get a chance... it looks nice!

---

### Post by piercleo on 2008-02-01
Could someone tell me if this guide is the proper one for me ?

I run Gutsy Gibbon AMD64 on a dell Latitude D520. The screen pilot is intel i495

TY

---

### Post by darkmdbeener on 2008-02-29
im not sure what went wrong but i end up restarting in the terminal. said something like no images found i fixed that problem by change to  # 1 from # 3. ill see if it was something i did.

o should this "$ sudo /etc/X11/xorg.conf.svideo" be "$sudo kate /etc/X11/xorg.conf.svideo"?

---

### Post by lagartoflojo on 2008-02-29
Regarding the second part of your message. please see this post by me:

[http://ubuntuforums.org/showpost.php?p=3037354&postcount=137](http://ubuntuforums.org/showpost.php?p=3037354&postcount=137)

(in short, yes, you should include "kate" in the command)

---

### Post by darkmdbeener on 2008-03-02
thanks

---

### Post by E_K on 2008-03-11
any solution for the PAL tv's out there.... please??! ive tried everything i have read about... has anyone with PAL got colour?

---

### Post by dysphasi on 2008-03-11
> **E_K said:**
> any solution for the PAL tv's out there.... please??! ive tried everything i have read about... has anyone with PAL got colour?

You can do as follows:

Edit the /etc/X11/xorg.conf to enable pal by default at boot.

Just open it up, and add the following section:
```

Section "Monitor"
	Identifier	"TV"
	Option		"TV Format" "PAL"
EndSection

```

And hey-presto should work :D ... does for me anyhow, let me know if there are any probs!

---

### Post by E_K on 2008-03-11
i wish i saw your post 2 hours earlier this is turning into a big headache

you gave me alot of faith but it didnt work

im using fiesty...with the switchmon method on mainpage

let me know..... im dying here im usingthis:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

dont know what else to say? this one has me stupped and if some people have done this in gutsy why cant i do it in fiesty, thing is a had a LOOOONG fight to get the headphone sound working which is essential to watching movies on the TV and i dont want to loose it.

---

### Post by dysphasi on 2008-03-12
> **E_K said:**
> i wish i saw your post 2 hours earlier this is turning into a big headache

you gave me alot of faith but it didnt work

im using fiesty...with the switchmon method on mainpage

let me know..... im dying here im usingthis:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

dont know what else to say? this one has me stupped and if some people have done this in gutsy why cant i do it in fiesty, thing is a had a LOOOONG fight to get the headphone sound working which is essential to watching movies on the TV and i dont want to loose it.

Hmmm, it worked for me, I'm using gutsy though, soz didn't think it would be any dif in fiesty.

I also use the [xrandr approach](http://ubuntuforums.org/showthread.php?t=583566), is this still usable in feisty, if so may be worth a shot.

Otherwise....try gutsy? I'm a fine one to talk though, I ended up switching back to windows primarily, I just prefer the way dual monitors are set up, with more control over overscan etc.. the linux drivers just aren't up to speed.

---

### Post by RamR on 2008-03-29
Ok, I've been using Ubuntu for less than a week and a lot of the time so far has been spent trying to connect to my TV using s-video.  

Today I stumbled upon this guide and it looks as if it might be the answer.  In fact I have been able to get the "s-video clone" working with a bit of minor tinkering.  Unfortunately the one I want is the "s-video dual screen" and I haven't had the same success with it.

I will copy the 3 xorg that I have (single and s-video clone which both work and s-video dual which does not work).  Hopefully someone can spot why the first two work and the third does not.

Here is my "single" xorg

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

My successful "s-video clone" xorg (just from the Section "Device" section as the rest is the same).

```
Section "Device"
	Identifier "SVIDEO"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "FlipPrimary" "True"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO"
	Option "ConnectedMonitor"	"TV"
	Option "Clone" "True"
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
EndSection

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"SVIDEO"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		"TV"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection
```

And my unsuccessful "s-video dual screen" xorg (again just from Section "Device").

```
Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Device"
	Identifier "TV"
	Driver "i810"
	Option "MonitorLayout"	"TV,LFP"
	Option "TVStandard"	"NTSC"
	Option "TVOutFormat"	"SVIDEO" # "COMPOSITE"
	Option "ConnectedMonitor"	"TV"
	Screen 1
	BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0

Section "Monitor"
	Identifier	"TV"
	HorizSync	30-50
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Failsafe Monitor"
	Device		"Failsafe Monitor"
	Monitor		"Failsafe Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"TV"
	Device		"TV"
	Monitor		"TV"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
		Modes	"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"LCDandTV"
	Screen		0 "Failsafe Monitor"
	Screen		1 "TV" RightOf "LCD"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
#	Option 		"AIGLX" "true"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout" "LCDandTV"
EndSection
```

---

### Post by ajeffreys on 2008-03-29
I was wondering how I would go about doing this, if I run compiz instead of beryl (on Gusty), with an i915 chipset, and a 1024x768 laptop screen with a 1280x1024 monitor. Any help would be greatly appreciated, as I've been having trouble with this for a while.

---

### Post by RamR on 2008-04-18
I have finally made some progress on this issue of connecting my TV to my laptop using s-video.  In fact it is actually working.  I've upgraded to 8.04 but I doubt this is key to the issue.  I am running the intel 810 driver.

There are, however, three small but irritating problems remaining.

1. The TV becomes the main screen when the dual screens are enabled.  As a result the laptop screen is to the right of the TV rather than the other way around as it should be.

2. The laptop screen resolution is lower than it should be.

3. Can't drag windows from one screen to the other.

Can anyone help with these three issues which, regardless how minor, I really want to fix?

---

### Post by ASULutzy on 2008-05-18
I can't for the live of me get Hardy to make my TV through S-video so much as flicker. I've been trying for several days with absolutely no luck. I'll include some info here and maybe someone here could help me, because I'm about to give up.

I'm using an HP Pavillion dv6000 (BIOS identifies it as a 6700 specifically)

lspci | grep VGA```
ryan@lappy:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

xorg.conf```
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
	Driver		"vmmouse"
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
```

xrandr --verbose```
ryan@lappy:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
	Identifier: 0x4b
	Timestamp:  24854
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
LVDS connected 1280x800+0+0 (0x4e) normal (normal left inverted right x axis y axis) 331mm x 207mm
	Identifier: 0x4c
	Timestamp:  24854
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	EDID_DATA:
		00ffffffffffff0006af748100000000
		01100103802115780a1cf59758508e27
		27505400000001010101010101010101
		010101010101c71b00a0502017303020
		36004bcf100000180000000f00000000
		00000000000000000020000000fe0041
		554f0a202020202020202020000000fe
		004231353445573038205631200a0043
	BACKLIGHT_CONTROL: kernel
		supported: native       legacy       combination  kernel      
	BACKLIGHT: 10 (0x0000000a) range:  (0,10)
  1280x800 (0x4e)   71.1MHz -HSync -VSync
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.4KHz
        v: height  800 start  803 end  809 total  823           clock   60.0Hz
  1280x800 (0x4f)   83.5MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  801 end  804 total  828           clock   60.0Hz
  1280x768 (0x50)   80.1MHz
        h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   47.7KHz
        v: height  768 start  769 end  772 total  795           clock   60.0Hz
  1024x768 (0x51)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x52)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x53)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
TV connected (normal left inverted right x axis y axis)
	Identifier: 0x4d
	Timestamp:  24854
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	BOTTOM: 37 (0x00000025) range:  (0,100)
	RIGHT: 46 (0x0000002e) range:  (0,100)
	TOP: 36 (0x00000024) range:  (0,100)
	LEFT: 54 (0x00000036) range:  (0,100)
	TV_FORMAT: NTSC-M
		supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
		           PAL-N        PAL         
  1024x768 (0x8f)   26.9MHz
        h: width  1024 start 1025 end 1088 total 1120 skew    0 clock   24.0KHz
        v: height  768 start  769 end  800 total  801           clock   30.0Hz
  800x600 (0x90)   17.0MHz
        h: width   800 start  801 end  864 total  896 skew    0 clock   19.0KHz
        v: height  600 start  601 end  632 total  633           clock   30.0Hz
  848x480 (0x91)   14.5MHz
        h: width   848 start  849 end  912 total  944 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
  640x480 (0x92)   11.3MHz
        h: width   640 start  641 end  704 total  736 skew    0 clock   15.4KHz
        v: height  480 start  481 end  512 total  513           clock   30.0Hz
```

The S-video works in Windows, and dual-head with VGA works in Ubuntu; it's just the S-video that doesn't seem to be able to output anything to the TV. I'm thinking about filing a bug report since no matter what I tell xrandr or mess around with grandr or use the built in system->preferences->screen resolution, I can't get the TV to do so much as flicker.

Anyone got any ideas?

---

### Post by upallnight on 2008-06-15
I just followed the steps on the first page of this thread and now my monitor is always in low-graphics mode :(

I restored the backup of /etc/X11/xorg.conf from /etc/X11/xorg.conf and restarted X11 and even restarted ubuntu and it still didn't fix it.

I am using a Compaq Presario R3000 with the NVIDIA Gforce4 graphics card.

I reinstalled the NVIDIA restricted drivers and it still didn't change anything!

:( its as if my xorg.conf file is being ignored!!!


Nevermind... turns out I ran out of disk space.

---

### Post by stldirty on 2008-07-13
> **upallnight said:**
> I just followed the steps on the first page of this thread and now my monitor is always in low-graphics mode :(

I restored the backup of /etc/X11/xorg.conf from /etc/X11/xorg.conf and restarted X11 and even restarted ubuntu and it still didn't fix it.

I am using a Compaq Presario R3000 with the NVIDIA Gforce4 graphics card.

I reinstalled the NVIDIA restricted drivers and it still didn't change anything!

:( its as if my xorg.conf file is being ignored!!!


Nevermind... turns out I ran out of disk space.
lmfaooooooo

---

### Post by stldirty on 2008-07-13
> **ASULutzy said:**
> I can't for the live of me get Hardy to make my TV through S-video so much as flicker. I've been trying for several days with absolutely no luck. I'll include some info here and maybe someone here could help me, because I'm about to give up.

I'm using an HP Pavillion dv6000 (BIOS identifies it as a 6700 specifically)


exact same problem here bro. hp dv6000.  i tried to tutorial and it broke my xorg and still didn't work...

---

### Post by bukharin on 2008-08-09
Hello, i wanted to know if this guide would help with the new "intel" driver, on kubuntu hardy, and if not, what parts of it should be modified (asuming that this is possible).

Any help would be apreciated. thanks!

---

### Post by seanature on 2008-08-12
Anyone out there who would know how to replicate this on an nvidia card? I'm using [fx5200]("http://www.nvidia.com/page/fx_5200.html")

oh and im using kubuntu 8.04 Hardy

And im a fresh 1 week old linux user.

---

### Post by seuzy13 on 2008-12-13
This looks like an excellent how-to that I would like to follow, but I want t o make sure I have the right graphics card first. I can't tell what driver I'm using, but my card  is an Intel 82852/855GM Integrated Graphics Device. My xorg.conf doesn't explain here. It only says "Configured Monitor."

---

### Post by seuzy13 on 2008-12-13
Well, the long and short is that it didn't work for me. I'm trying to clone to a TV through S-video, so I used switchmon 3. This caused my computer monitor to become staticy and my television showed absolutely no change. What could I be doing wrong?

---

### Post by Sonja on 2009-02-13
Is it possible to adapt this guide to my situation with Ibex and Radeon HD 2400 PRO?

[http://ubuntuforums.org/showthread.php?p=6727810](http://ubuntuforums.org/showthread.php?p=6727810)

I'm a n00b.

---

### Post by wcasper4 on 2009-11-29
Thanks for the excellent tutorial. The only reason I was still using windows is because I couldn't get my tv hooked up properly. However, I still can't get it to work. I get this error. I am new to linux, so this could be a simple fix? Any suggestions?



walter@walter:~$ switchmon
bash: /usr/bin/switchmon: Permission denied

---

### Post by stjuuv on 2010-09-06
My /etc/X11/ directory does not have the xorg.conf file. Any idea on where I should look for it?

---


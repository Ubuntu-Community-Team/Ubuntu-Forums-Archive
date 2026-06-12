---
title: "Triple Head Setup (special instructions for dual core processor)"
date: 2007-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by jgordon510 on 2007-02-04
Okay, there aren't a lot of these posted in the forums, so I thought I would post mine.  It's a triple-head setup that has xinerama and works.

my xorg.conf:

```

# xorg.conf-4800x1200_triplehead-3x1-xinerama-dualview+monoview

Section "ServerLayout"
  Identifier   "Layout0"
  InputDevice	"Generic Keyboard"
  InputDevice	"Configured Mouse"
  Option	"Clone"     "off"
  Option       "Xinerama"  "on"
  Screen       0           "Screen0"
  Screen       1           "Screen1" RightOf "Screen0"
  Screen       2           "Screen2" RightOf "Screen1"
EndSection

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
	Load  "dbe"
	Load  "extmod"
	Load  "fbdevhw"
	Load  "glx"
	Load  "record"
	Load  "freetype"
	Load  "type1"
EndSection

Section "Module"
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "Monitor"
	Identifier   "Monitor0"
    VendorName     "Samsung"
    ModelName      "SyncMaster 913N"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
    VendorName     "Samsung"
    ModelName      "SyncMaster 913N"
    HorizSync       30.0 - 81.0
    VertRefresh     60.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
        Identifier   "Monitor2"
        VendorName   "Monitor Vendor"
        ModelName    "LCD Panel 1600x1200"
        HorizSync    31.5 - 90.0
        VertRefresh  60.0 - 60.0
        Option      "dpms"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	Option         "Metamodes" "1280x1024,1280x1024,1280x1024"
    	SubSection     "Display"
        	Depth       24
        	Modes      "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Videocard1"
	Monitor    "Monitor1"
	DefaultDepth     24
	Option         "Metamodes" "1280x1024,1280x1024,1280x1024"
    	SubSection     "Display"
        	Depth       24
        	Modes      "1280x1024"
	EndSubSection
EndSection

Section "Screen"
        Identifier "Screen2"
        Device     "Videocard2"
        Monitor    "Monitor2"
	DefaultDepth     24
	Option         "Metamodes" "1280x1024,1280x1024,1280x1024"
    	SubSection     "Display"
        	Depth       24
        	Modes      "1280x1024"
	EndSubSection
EndSection


Section "Device"
        Identifier  "Videocard0"
        Driver      "nvidia"
	BusID       "PCI:1:0:0"
        Option      "CursorShadow" "1"
        Option      "NoLogo" "1"
     Option         "RenderAccel"      "True"
Screen		0        

EndSection

Section "Device"
        Identifier  "Videocard1"
        Driver      "nvidia"
	BusID       "PCI:1:0:0"
        Option      "CursorShadow" "1"
        Option      "NoLogo" "1"
     Option         "RenderAccel"      "True"      
Screen      1
EndSection

Section "Device"
	Identifier  "Videocard2"
	Driver      "nvidia"
	Option "ConnectedMonitor" "CRT"
	VendorName  "Videocard vendor"
	BusID       "PCI:2:2:0"
        Option      "CursorShadow" "1"
        Option      "NoLogo" "1"
Screen 0
EndSection

Section "DRI"
	Mode	0666
EndSection

```

[COLOR="Red"]This is important.[/COLOR]
Although this worked, the first time I did anything remotely intensive, my whole system locked up.  It took me a few hours of googling to find [this post at nvnews.]("http://www.nvnews.net/vbulletin/showthread.php?t=58498")

> If you are seeing severe stability problems and you are using a Linux 2.6 SMP kernel on a system with multiple processors (or processor cores) in combination with more than one GPU, please search the output of `dmesg` for the presence of the message below after the system has just been started:

    PCI: Using MMCONFIG


If this message is present, please boot the system with the pci=nommconf kernel parameter and check if the stability problems continue to reproduce.

So if you've got a dual core processor make sure you use the pci=nommconf boot option.  Everything is running beautifully now.

---


---
title: "Dual video cards in Intrepid"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by mongi3 on 2008-11-24
Hi all... I know this is a bit lengthy, but I'm trying to provide the info you all are going to ask for.

I'm trying to put ubuntu on my last remaining XP box, but I've got one issue I haven't been able to overcome, Dual monitors.

For now I'm booting off the Live CD (until I can determine if dual monitors is possible.)  I've got a system with an onboard S3 Unichrome P4M800 video card.  Additionally I've got an ATI Radeon 9200 Pro in a PCI expansion slot.

The problem is I can't get dual monitors to work in ubuntu.  More specifically,  Only the monitor hooked to the ATI card gets a signal.

I've tried many things from forum posts though they seem a bit dated with the new Xorg found in Intrepid.

Here's where I'm at.  Straight boot off the live CD doesn't work.  I check out the /etc/X11/xorg.conf and find that it's a very vanilla file (I believe due to the improved autodetection present in Xorg.)  Here it is:
```

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
```

So I checkout lspci -v and see that the card is attached (pertient sections below):

```
00:08.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: ATI Technologies Inc Device 2002
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at b000 [size=256]
	Memory at f6030000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Kernel modules: radeonfb

00:08.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: ATI Technologies Inc Device 2003
	Flags: medium devsel
	Memory at e8000000 (32-bit, prefetchable) [disabled] [size=128M]
	Memory at f6020000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)
	Subsystem: Biostar Microtech Int'l Corp Device 1202
	Flags: 66MHz, medium devsel, IRQ 10
	Memory at f0000000 (32-bit, prefetchable) [disabled] [size=64M]
	Memory at f4000000 (32-bit, non-prefetchable) [disabled] [size=16M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
	Capabilities: [70] AGP version 3.0

```

NOTE: There are 3 present because the ATI card also has a TV out on it.  In the end I'd like to have that working as well, but right now I'm mainly interested in just the dual screen.

I've validated that if I take the ATI card out, the onboard video works with the "openchrome" driver.

I've made my first goal to get video displayed on the onboard card alone while the ATI card is plugged in (thinking that if I can get video on that one, I can work out the virtual desktop and combining displays later).

I've also gone as far as running "sudo X -configure" with just the onboard as well as with the ATI card.  I've created a consolidated xorg.conf shown below, but it I try and switch the config to use just screen1, I get no signal anywhere when I ctrl-alt-backspace or do a "sudo /etc/init.d/gdm restart"

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0 # When I switch this to line below I get no display
#	Screen      1  "Screen1" 0 0 
#	Screen      1  "Screen1" RightOf "Screen0"  #Commented for now, just want single display with onboard
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  410   260	# mm
	Identifier   "Monitor0"
	VendorName   "ACR"
	ModelName    "Acer AL1916W"
	HorizSync    30.0 - 82.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "DynamicClocks"      	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV280 [Radeon 9200 PRO]"
	BusID       "PCI:0:8:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "PrintVGARegs"       	# [<bool>]
        #Option     "PrintTVRegs"        	# [<bool>]
        #Option     "I2CScan"            	# [<bool>]
        #Option     "VBEModes"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "ExaNoComposite"     	# [<bool>]
        #Option     "ExaScratchSize"     	# <i>
        #Option     "SWCursor"           	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoRAM"           	# <i>
        #Option     "ActiveDevice"       	# [<str>]
        #Option     "BusWidth"           	# [<str>]
        #Option     "Center"             	# [<bool>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForcePanel"         	# [<bool>]
        #Option     "TVDotCrawl"         	# [<bool>]
        #Option     "TVDeflicker"        	# <i>
        #Option     "TVType"             	# [<str>]
        #Option     "TVOutput"           	# [<str>]
        #Option     "DisableVQ"          	# [<bool>]
        #Option     "DisableIRQ"         	# [<bool>]
        #Option     "EnableAGPDMA"       	# [<bool>]
        #Option     "NoAGPFor2D"         	# [<bool>]
        #Option     "NoXVDMA"            	# [<bool>]
        #Option     "VbeSaveRestore"     	# [<bool>]
        #Option     "DisableXvBWCheck"   	# [<bool>]
        #Option     "MaxDRIMem"          	# <i>
        #Option     "AGPMem"             	# <i>
	Identifier  "Card1"
	Driver      "openchrome"
	VendorName  "VIA Technologies, Inc."
	BoardName   "CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Any ideas?  It works in XP with no problems and lspci shows the card.  What am I missing?

---

### Post by ggaaron on 2008-11-24
Please post what xrandr command (run it in a terminal under running X) says. It is now default configuration utility for multiple monitors, I don't know about several cards though as I've never had one... If you can, reset you xorg.conf to Ubuntu default first, many parts of it are now handled by dynamic tools (like hal) and changed xorg.conf may cause them not to run properly.

---

### Post by mongi3 on 2008-11-24
xrandr output: (with original unaltered xorg.conf)

```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1600 x 1200
VGA-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   59.9*    60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0     60.0     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)

```

Again it shows only input from the ATI PCI card.  The monitor is my widescreen LCD, and the S-video I'm guessing would be the tv-out on the ati card.

No mention of the monitor hooked up to the onboard video card.

---

### Post by ggaaron on 2008-11-25
I'm afraid that I won't be able to help then... Maybe someone else will answer you, I'd like to know how to do this as well=)

---

### Post by mongi3 on 2008-12-05
Bump!

---

### Post by thomph on 2009-02-05
Hey mongi3,

I'm not sure if you're still trying to get this working but I've got the same setup as you (though my radeon 9200 PRO has a DVI port). It works in XP so somehow it should work in ubuntu.

I am having the same issues as you are (which makes sense), that the onboard unichrome is being ignored by xrandr even though it shows up in lspci.

Have you had any success since you last posted?

Cheers,
thomph

---

### Post by mongi3 on 2009-02-05
sorry, no updates.  I gave up long ago and just use a single monitor.

Please post back if you are able to dig something up.

---


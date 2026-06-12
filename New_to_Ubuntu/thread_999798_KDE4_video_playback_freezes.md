---
title: "KDE4 video playback freezes"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by netimen on 2008-12-02
I have recently upgraded to 8.10 from 8.04 KDE3. Now when I watch films they stop for several seconds every 10-15min. I have tried using mplayer and vlc - both have same effect.

---

### Post by sztomi on 2009-01-30
I have the exact same issue with Kde4.2 on Arch :/
(I tried VLC and Dragon player)

---

### Post by binbash on 2009-01-31
What output modes are you using guys?Also post your xorg.conf please

---

### Post by sztomi on 2009-01-31
()

---

### Post by sztomi on 2009-01-31
This is my xorg.conf:

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "SynapticsTouchpad" "SendCoreEvents"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"
	Load  "xtrap"
	Load  "glx"
	Load  "extmod"
	Load  "freetype"
	Load  "synaptics"
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

Section "InputDevice"
	Identifier  "SynapticsTouchpad"
	Driver	    "synaptics"
	Option	    "AlwaysCore"	"true"
	Option	    "Device"		"/dev/psaux"
	Option	    "Protocol"		"auto-dev"
	Option	    "SHMConfig"		"true"
	Option	    "LeftEdge"		"1700"
	Option	    "RightEdge"		"5300"
	Option	    "TopEdge"		"1700"
	Option	    "BottomEdge"	"4200"
	Option	    "FingerLow"		"25"
	Option	    "FingerHigh"	"30"
	Option	    "MaxTapTime"	"180"
	Option 	    "VertEdgeScroll"	"true"
	Option	    "HorizEdgeScroll"	"false"
	Option	    "CornerCoasting"	"true"
	Option	    "CoastingSpeed"	"0.30"
	Option	    "VertScrollDelta"	"100"
	Option	    "HorizScrollDelta"	"100"
	Option 	    "MinSpeed"		"0.25"
	Option	    "MaxSpeed"		"0.60"
	Option	    "AccelFactor"	"0.0020"
	Option	    "VertTwoFingerScroll" "true"
	Option	    "HorizTwoFingerScroll" "true"
	Option	    "CircularScrolling"	"off"
        Option	    "CircularScrollTrigger" "2"
	Option      "TapButton1"	"1"
	Option	    "TabButton2"	"2"
	Option	    "TabButton3"	"3"
EndSection

Section "Monitor"
	#DisplaySize	  330   210	# mm
	Identifier   "Monitor0"
	VendorName   "LPL"
	ModelName    "LP154WX4-TLAB"
	HorizSync    30.0 - 130.0
	VertRefresh  50.0 - 100.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24
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

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

On VLC, I used the "default" output mode, which is most probably X11 output mode.
And to clarify: I'm on Arch linux, with Kdemod4.2, but it happened so with kdemod4.1, too.

---


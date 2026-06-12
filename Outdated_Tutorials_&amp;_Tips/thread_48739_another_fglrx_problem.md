---
title: "another fglrx problem"
date: 2005-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by edgarallan on 2005-07-13
hi i've barton 2500 on nforce2 mobo and radeon 2600 pro (agpgart and nvidia_agp loaded into kernel)

i've done all the possible... followed all the stiky messages. (2 days of frustration maybe i will return winzozz)

fglrxinfo say                i'm in MESA
Xorg.0.log say         loaded kernel module for "fglrx" driver
                                       Kernel Module version matches driver.
                                 (II) fglrx(0): [drm] DRM interface version 1.0
                                  (II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
                                  DRI initialization successfull!
glrxinfo say               direct rendering: No
                                     client glx vendor string: ATI
                                     OpenGL vendor string: Mesa

don't know what i can do:(
please helpme
tanks and bye,
francesco. this is my xorg.conf:

ection "Files"
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
	Load	"dri"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"glx"
	# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
  	SubSection "extmod"
    	    Option "omit xfree86-dga"
  	EndSubSection
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
	Load    "GLcore"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option  "UseInternalAGPGART" "no"
 	BusID "PCI:2:0:0"
 	Option "backingstore" "true"
# === Video Overlay for the Xv extension ===
  	Option 		"VideoOverlay" 		"yes"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  	Option 		"OpenGLOverlay" 	"off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.

EndSection

Section "Monitor"
	Identifier	"CM715"
	Option		"DPMS"
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"CM715"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


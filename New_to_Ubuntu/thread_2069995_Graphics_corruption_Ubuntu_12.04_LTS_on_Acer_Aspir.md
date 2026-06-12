---
title: "Graphics corruption Ubuntu 12.04 LTS on Acer Aspire 1360"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by guypracy on 2012-10-11
I currently run 10.04 LTS Lucid Lynx on my Acer Aspire 1360 with no problems. I have tried both 11.04 and 12.04 LTS and they BOTH exhibit chronic video corruption making the screen virtually unreadable. I get 3/4 of the screen corrupt with the rest of the screen black.

It is not a video card problem as I can run Windows XP, Windows 7, Haiku Alpha 3 and Ubuntu 10.04 LTS with no issues. Interestingly I also have the same graphic corruption with Linux Mint 13 Maya, Fedora 17 and (predictably) Kubuntu 11.04.

I have search the internet but still cannot find a solution to this problem - does any body here have the solution?

I would really like to get this sorted before the support for Lucid runs out in April 2013.

Thanks

---

### Post by ajgreeny on 2012-10-11
In spite of your comment, it probably **is** the graphic card that is the problem.

What card does the machine have?  Let's see the output of ```
lspci
``` and ```
sudo lshw -C display
```

---

### Post by mardybear on 2012-10-11
The Acer Aspire 1360 uses an NVIDIA GeForce graphic chip...many linux users have had challenges running Nvidia graphics. It's probably just a proprietary graphic driver issue.

Not sure about 12.04 (i use 10.04), but check synaptic or gnome-control-center (hardware drivers section) to see if this helps you find a solution.

Good luck,

mardybear

---

### Post by mardybear on 2012-10-11
Just re-read your post...hopefully you'll get it sorted out before 2013 - funny ! (you must be incredibly patient to wait that long for a solution). mardybear

---

### Post by AngelArnal on 2013-01-02
After some struggling, I've managed to set up Ubuntu Studio 12.04 on my Aspire 1363WLMi with UniChrome Pro. Here is my xorg.conf, in case you want to try it. Works perfectly at 1280x800. Maybe (surely) there are extra, non-essential lines, but I don't dare to touch anything after four days trying. I'm not any kind of guru, so I'll leave refinements to them gurus.

[https://dl.dropbox.com/u/31474726/xorg.conf](https://dl.dropbox.com/u/31474726/xorg.conf)

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
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
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync    30.0-70.0
	VertRefresh  50.0-150.0
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
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
        #Option     "RotationType"       	# [<str>]
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
        #Option     "TVPort"             	# [<str>]
        #Option     "DisableVQ"          	# [<bool>]
        #Option     "DisableIRQ"         	# [<bool>]
        #Option     "EnableAGPDMA"       	# [<bool>]
        #Option     "NoAGPFor2D"         	# [<bool>]
        #Option     "NoXVDMA"            	# [<bool>]
        #Option     "VbeSaveRestore"     	# [<bool>]
        #Option     "DisableXvBWCheck"   	# [<bool>]
        #Option     "ModeSwitchMethod"   	# [<str>]
        #Option     "MaxDRIMem"          	# <i>
        #Option     "AGPMem"             	# <i>
        #Option     "I2CDevices"         	# [<str>]
	Identifier  "Card1"
	Driver      "openchrome"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card2"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 1280 800
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

---

### Post by guypracy on 2013-01-17
Hi

Finally got round to this PC again (Acer Aspire 1360)

Here are the outputs asked for.....
lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.1 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
00:0b.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)

and 
sudo lshw -C display

*-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:f0000000-f3ffffff(prefetchable) memory:d1000000-d1ffffff


Hope this means something to you "ajgreeny".


Thanks

---

### Post by rattencomics on 2013-05-03
sry for my bad english

I've got the same problems, AngelArnals Posting of his xorg.conf showed me the way out of the acer aspire 1360 graphic disaster.

The successful entries in this file are: 

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
HorizSync 30.0-70.0
VertRefresh 50.0-150.0
EndSection


 	Section "Device"
Identifier "Card0"
Driver "vesa"
BusID "PCI:1:0:0"
EndSection

 	
Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 24
Virtual 1280 800
EndSubSection
EndSection

I have tested this and found, that the three section-entries above are relevant for the graphic display of the Aspire 1360.

Section Device = Card0 gives you a pic,but a poor one.
Section Screen gives you a spliced Pic, 
Section Monitor gives you a perfect Pic.

Sorry for my bad english again, but i want to thank the forum community because i have brought my loved acer aspire 1360 to life again! And i wanted to give feedback, that this thread was helpful. 

THANK YOU ALL!

---


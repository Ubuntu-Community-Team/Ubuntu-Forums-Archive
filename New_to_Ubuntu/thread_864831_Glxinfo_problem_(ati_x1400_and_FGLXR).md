---
title: "Glxinfo problem (ati x1400 and FGLXR)"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Mobidoy on 2008-07-20
Hello all,

once again, i need your help on this. I have reinstalled the Fglrx drivers after failing to have direct rendering with the open source drivers.

I have an ATI radeon mobility X1400 chip and, i have notice a big lost of fps from previous installation of fglrx drivers. From what i see, it is not the Ati/Amd drivers that are providing the direct rendering but, some SGI.

Could someone tell me haw i can get Ati tech. alone ?

Also, is there anything i can change to my xorg.conf to get better fps ?

Fglinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_OML_sync_control, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

```

xorg.conf
```

# xorg.conf 16 Juillet 2008 pour Ati Mobility Radeon X1400
#
# Video Driver
# Driver:		Ati Fglrx 8.6
# Date:		18 Juin 2008
#
# X.org X Server
# Version:		1.4.0.90
# Date:		5 Sept 2007
# X Protocol:	Ver.11 Rev.0
#
# Operating System
# Build: 		Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
# Current:		Linux Notebook 2.6.24-19-generic #1 SMP 18 Juin 2008 i686
# Build Date:	13 June 2008  01:08:21AM
#
# Components
# Keyboard:	Notebook Gateway MX-6750 1KBZZUTAE5 86 Keys
# Mouse:		Logitech G5 laser (Not fully working yet)
# Touchpad:	Synaptics Touchpad (need improvement)
# Video Card:	Ati Mobility Radeon X1400
#
# This is the configuration file for a notebook gateway MX-6750.
# If you want to be sure that your modification have been applied, 
# type "sudo aticonfig --input=/etc/X11/xorg.conf" in a terminal window
# to write the changes in the actual ATI configuration file.
# Use "lspci -nn" to look at your PCI devices
#	Option	"PowerState"			"integer"
#	Option	"EnablePrivateBackZ"		"on"
#	Option	    "DRI" "true"
#	Option	"PseudoColorVisuals"		"off"

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Synaptics Touchpad"
	Option	    "Clone" "off"
	Option	    "Xinerama" "off"
	Option	    "AIGLX" "on"
EndSection

Section "Files"
	RgbPath      "/usr/share/X11/rgb.txt"
	ModulePath   "/usr/lib/xorg/modules"
EndSection

Section "Module"
	Load  "dri"
	Load  "dbe"		#Already loaded by default
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
#	Option		"Protocol"		"evdev"
#	Option		"Dev Name"		"Logitech USB Gaming Mouse"
#	Option		"Buttons"		"12"
#	Option		"ZAxisMapping"	"4 5 7 6"
#	Option		"Resolution"		"2000"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
	Option	    "SHMConfig" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
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
	Group        "video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection
```

Xorg.0.log
```
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 20 02:27:55 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "Xinerama" "off"
(**) Option "AIGLX" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) RgbPath set to "/usr/share/X11/rgb.txt"
(**) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "RENDER" is enabled
(**) Extension "DAMAGE" is enabled
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 107b,0461 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 107b,0461 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 107b,0461 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 107b,0461 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 107b,0461 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 107b,0461 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 107b,0461 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 107b,0461 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 107b,0461 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c5 card 107b,0461 rev 02 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 107b,0461 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7145 card 107b,0461 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 8086,109a card 107b,0461 rev 00 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 04:09:0: chip 104c,8039 card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 04:09:1: chip 104c,803a card 107b,0461 rev 00 class 0c,00,10 hdr 80
(II) PCI: 04:09:2: chip 104c,803b card 107b,0461 rev 00 class 01,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0018 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00002000 - 0x00002fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd80fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,8), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xd8100000 - 0xd81fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (4:9:0), (4,5,8), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xc8000000/27, 0xd8000000/16, I/O @ 0x2000/8
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
	[0] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[1] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[2] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[3] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[4] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[5] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[6] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[7] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[8] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[1] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[2] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[3] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[4] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[5] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[6] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[7] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[8] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[9] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[10] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[11] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[12] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[13] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[14] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[15] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[16] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[17] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
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
	[4] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[5] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[6] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[7] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[8] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[9] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[10] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[11] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[12] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[18] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[19] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[20] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[21] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[22] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[23] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded by default.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	Module class: X.Org Video Driver
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471                    
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x7145) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[5] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[6] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[7] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[8] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[9] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[10] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[11] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[12] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[17] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[18] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[19] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[20] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[21] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[22] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[23] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[29] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[30] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[31] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[32] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x820c750
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[5] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[6] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[7] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[8] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[9] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[10] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[11] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[12] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[13] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[20] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[21] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[22] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[23] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[24] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[25] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[26] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[32] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[33] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[34] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[35] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x107b, PciSubDevice = 0x0461)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xc8000000
(--) fglrx(0): MMIO registers at 0xd8000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.47.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR3
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: SEC  Model: 3445  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) fglrx(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) fglrx(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) fglrx(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(II) fglrx(0):  SAMSUNG
(II) fglrx(0):  LTN154X3-L03
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff004ca3453400000000
(II) fglrx(0): 	000f0103802115780a87f594574f8c27
(II) fglrx(0): 	27505400000001010101010101010101
(II) fglrx(0): 	010101010101ee1a0080502010301030
(II) fglrx(0): 	13004bcf100000190000000f00000000
(II) fglrx(0): 	00000000002387026400000000fe0053
(II) fglrx(0): 	414d53554e470a2020202020000000fe
(II) fglrx(0): 	004c544e31353458332d4c30330a0065
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 439/450MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 128/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 209/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   4. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(**) fglrx(0): OpenGL Overlay enabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 10 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x800 (pitch 0)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.94  1280 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync (49.0 kHz)
(--) fglrx(0): Display dimensions: (330, 210) mm
(--) fglrx(0): DPI set to (98, 96)
(--) fglrx(0): Virtual size is 1280x800 (pitch 1280)
(**) fglrx(0): *Mode "1280x800": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1280x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   68.94  1280 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "1024x768": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   68.94  1024 1296 1344 1408  768 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "800x600": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   68.94  800 1296 1344 1408  600 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0): *Mode "640x480": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   68.94  640 1296 1344 1408  480 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "640x400": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   68.94  640 1296 1344 1408  400 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "512x384": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   68.94  512 1296 1344 1408  384 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "400x300": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"x60.0   68.94  400 1296 1344 1408  300 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x240": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"x60.0   68.94  320 1296 1344 1408  240 801 804 816 +hsync +vsync (49.0 kHz)
(**) fglrx(0):  Default mode "320x200": 68.9 MHz (scaled from 0.0 MHz), 49.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"x60.0   68.94  320 1296 1344 1408  200 801 804 816 +hsync +vsync (49.0 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(**) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xd8104000 - 0xd8104fff (0x1000) MX[B]
	[7] -1	0	0xd8100000 - 0xd8103fff (0x4000) MX[B]
	[8] -1	0	0xd8105000 - 0xd81057ff (0x800) MX[B]
	[9] -1	0	0xd6000000 - 0xd6000fff (0x1000) MX[B]
	[10] -1	0	0xd4000000 - 0xd401ffff (0x20000) MX[B]
	[11] -1	0	0xd8404400 - 0xd84047ff (0x400) MX[B]
	[12] -1	0	0xd8404000 - 0xd84043ff (0x400) MX[B]
	[13] -1	0	0xd8400000 - 0xd8403fff (0x4000) MX[B]
	[14] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00003000 - 0x0000301f (0x20) IX[B]
	[23] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[24] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[25] -1	0	0x000018a8 - 0x000018ab (0x4) IX[B]
	[26] -1	0	0x000018c0 - 0x000018c7 (0x8) IX[B]
	[27] -1	0	0x000018ac - 0x000018af (0x4) IX[B]
	[28] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[29] -1	0	0x00001880 - 0x0000188f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[35] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[36] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[37] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[38] -1	0	0x00002000 - 0x000020ff (0x100) IX[B](B)
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(WW) fglrx(0): could not detect X server version (query_status=-3)
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [drm] installed DRM signal handler
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.47.3
(II) fglrx(0):     Date: Feb 25 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.24-19-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01004000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3280)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,800) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2480
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 26
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(WW) AIGLX: 3D driver claims to not support visual 0x73
(WW) AIGLX: 3D driver claims to not support visual 0x74
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(**) Option "SHMConfig" "true"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event10
(**) Option "Device" "/dev/input/event10"
(--) Synaptics Touchpad touchpad found
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().

```

---

### Post by Mobidoy on 2008-07-20
Update: i am not sure why or if it is the SGI but, i have tried to remove the radeon (open source) drivers from the kernel by with 
```
sudo modprobe -r radeon 
```

I dont get any errors at all but, after a reboot, it remains in the kernel.... What am i doing wrong ?

---

### Post by Mobidoy on 2008-07-20
After some search, this is not the Radeon (open source) driver but the Mesa driver.... 

Still stuck with that problem. Anyone ?

---

### Post by Mobidoy on 2008-07-21
Still trying to solve this... Anyone ?

---

### Post by Mobidoy on 2008-07-23
Uograded to 8.7, still the same, also, 

No one faced that problem before ?

---


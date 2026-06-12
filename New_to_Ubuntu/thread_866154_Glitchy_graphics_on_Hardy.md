---
title: "Glitchy graphics on Hardy"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by defenestratos on 2008-07-21
Hey all, just did a clean install of Hardy and am having some graphics issues. I have no restricted drivers installed and am using onboard graphics of my 2 year old laptop with no acceleration or effects. 
I have always had graphics glitches in Ubuntu but it just got a lot worse. 
The screen just distorts completely every minute or so and to refresh it I need to change workspaces or sometimes drag a window across the distortion... The distortions are really intensive for the processor as well and the fan goes wild.
Also the login screen is in a dumb resolution which means I can't change languages etc.
please help:)

---

### Post by wolfen69 on 2008-07-21
are you using the nvidia driver?

---

### Post by rogier.de.groot on 2008-07-21
Looks a problem with you video card or the drivers for it. Could you give us some more details about your hardware & X configuration?

---

### Post by defenestratos on 2008-07-21
> **rogier.de.groot said:**
> Looks a problem with you video card or the drivers for it. Could you give us some more details about your hardware & X configuration?

Yeah sure. I have a dead standard laptop, as written in my signature. I am running 64 bit Hardy. The graphics are integrated and I am running no restricted (ie NVIDIA) drivers. The graphics are totally low end and I would have expected that it would all just work because it is totally  unextroadinary. 
How do I find more detailed reports of my hardware?

---

### Post by defenestratos on 2008-07-21
Here's another graphic while I'm at it::popcorn:

---

### Post by rogier.de.groot on 2008-07-21
Could you post the contents of the /var/log/Xorg.0.log file?

---

### Post by defenestratos on 2008-07-21
So here it is

[PHP]This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux hugo-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 21 15:13:15 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 1106,0204 card 1071,8889 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 1524,1410 card 1800,0000 rev 01 class 06,07,00 hdr 02
(II) PCI: 00:0a:0: chip 1814,0201 card 1814,2560 rev 01 class 02,80,00 hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1071,8889 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1071,8889 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1071,8889 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1071,8889 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1071,8889 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1071,8889 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1071,8889 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 1071,8889 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1071,8889 rev 74 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 1106,3108 card 1071,8889 rev 01 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000dfff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xa0000000 - 0xafffffff (0x10000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:9:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[1] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x54000000 - 0x57ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x3108) rev 1, Mem @ 0xa4000000/26, 0xe1000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xb0000000 to 0xafffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[1] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[2] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[3] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[4] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[6] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[7] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[9] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[10] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[11] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[12] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[1] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[2] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[3] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[4] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[5] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[6] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[7] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[9] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[10] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[11] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[12] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
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
	[4] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[5] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[6] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[13] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[16] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[17] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[18] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
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
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched openchrome from file name openchrome.ids in autoconfig
(II) Matched via from file name via.ids in autoconfig
(==) Matched openchrome for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module via: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.2.901
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset K8M800/K8N800 found
(!!) VIA Technologies does not support or endorse this driver in any way.
(!!) For support, refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Wed Jan 23 11:54:32 2008)
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[5] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[6] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[13] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[15] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[16] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[17] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[18] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[5] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[6] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[7] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[8] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[16] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[18] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[19] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[20] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[21] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (==) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: "K8M800/K8N800"
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options...
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): ShadowFB is disabled.
(==) CHROME(0): Acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Hardware two-color cursors; software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xe1000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xe1200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected Mitac 8889.
(II) CHROME(0): Detected MemClk 5
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: PAL.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" removed.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): Enabling panel from PCI-subsystem ID information.
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaVT162xDetect
(II) CHROME(0): I2C device "I2C bus 3:VT162x" registered at address 0x40.
(--) CHROME(0): Detected VIA Technologies VT1622A/VT1623 TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaVT162xInit
(II) CHROME(0): VT162xSave
(II) CHROME(0): VT1622DACSense
(--) CHROME(0): VT162x: Nothing connected.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(II) CHROME(0): ViaOutputsSelect: Panel.
(WW) CHROME(0): Panel on K8M800, PM800, VM800, P4M890, K8M890, CX700 or P4M900 is currently not supported.
(WW) CHROME(0): Using VBE to set modes to work around this.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) CHROME(0): initializing int10
(II) CHROME(0): Primary V_BIOS segment is: 0xc000
(II) CHROME(0): VESA BIOS detected
(II) CHROME(0): VESA VBE Version 3.0
(II) CHROME(0): VESA VBE Total Mem: 65536 kB
(II) CHROME(0): VESA VBE OEM: VIA K8N800


(II) CHROME(0): VESA VBE OEM Software Rev: 1.0
(II) CHROME(0): VESA VBE OEM Vendor: 
(II) CHROME(0): VESA VBE OEM Product: 
(II) CHROME(0): VESA VBE OEM Product Rev: 
(II) CHROME(0): Searching for matching VESA mode(s):
Mode: 101 (640x480)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 203
	LinNumberOfImagePages: 203
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 101
	LinNumberOfImagePages: 101
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (720x480)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 169
	LinNumberOfImagePages: 169
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 173 (720x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 175 (720x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 1b9 (720x540)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 145
	LinNumberOfImagePages: 145
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 1ba (720x540)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 72
	LinNumberOfImagePages: 72
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 1bb (720x540)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17c (720x576)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 145
	LinNumberOfImagePages: 145
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17e (720x576)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 72
	LinNumberOfImagePages: 72
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 17f (720x576)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 103 (800x600)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 179 (1280x768)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 67
	LinNumberOfImagePages: 67
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17a (1280x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 33
	LinNumberOfImagePages: 33
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 17b (1280x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (1280x1024)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13b (1400x1050)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1408
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 39
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1408
	BnkNumberOfImagePages: 39
	LinNumberOfImagePages: 39
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (1400x1050)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 13e (1400x1050)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5600
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
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
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5600
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 120 (1600x1200)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 33
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 33
	LinNumberOfImagePages: 33
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 122 (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 124 (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
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
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 108 (80x60)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 254
	LinNumberOfImagePages: 254
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 102 (800x600)
	ModeAttributes: 0x1f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) CHROME(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) CHROME(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(--) CHROME(0): Virtual size is 1600x1200 (pitch 1600)
(**) CHROME(0): *Built-in mode "1600x1200"
(**) CHROME(0): *Built-in mode "1400x1050"
(**) CHROME(0): *Built-in mode "1280x1024"
(**) CHROME(0): *Built-in mode "1280x768"
(**) CHROME(0): *Built-in mode "1024x768"
(**) CHROME(0): *Built-in mode "800x600": 0.0 MHz, 37879.3 kHz, 60.8 Hz
(II) CHROME(0): Modeline "800x600"x60.8    0.00  800 0 0 0  600 0 0 0 (37879.3 kHz)
(**) CHROME(0): *Built-in mode "720x576"
(**) CHROME(0): *Built-in mode "720x540"
(**) CHROME(0): *Built-in mode "720x480"
(**) CHROME(0): *Built-in mode "640x480": 0.0 MHz, 31469.2 kHz, 60.4 Hz
(II) CHROME(0): Modeline "640x480"x60.4    0.00  640 0 0 0  480 0 0 0 (31469.2 kHz)
(==) CHROME(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe1000000 - 0xe1ffffff (0x1000000) MS[B]
	[1] 0	0	0xa4000000 - 0xa7ffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0002100 - 0xf00021ff (0x100) MX[B]
	[7] -1	0	0xf0002000 - 0xf00020ff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xf0001fff (0x2000) MX[B]
	[9] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[10] -1	0	0xe1000000 - 0xe1ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xa4000000 - 0xa7ffffff (0x4000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[18] -1	0	0x0000e100 - 0x0000e1ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[20] -1	0	0x00001100 - 0x0000110f (0x10) IX[B]
	[21] -1	0	0x00001700 - 0x0000171f (0x20) IX[B]
	[22] -1	0	0x00001300 - 0x0000131f (0x20) IX[B]
	[23] -1	0	0x00001200 - 0x0000121f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xa4000000 with size 0x4000000
(==) CHROME(0): Write-combining range (0xa4000000,0x4000000)
(--) CHROME(0): Frame buffer start: 0x7f928712b000, free start: 0x753000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xe1000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xe1200000 with size 0x20000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VT162xSave
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(II) CHROME(0): Trying VBE Mode 1600x1200 (0xc124) Refresh 60.00:
(II) CHROME(0): ViaVbeSetRefresh
(II) CHROME(0): Active Device: 2
(II) CHROME(0): Refresh Rate Index: 0
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xa4000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xe1000000
(II) CHROME(0): [drm] framebuffer handle = 0xa4000000
(II) CHROME(0): [drm] mmio Registers = 0xe1000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): Using 3600 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		24 256x256 slots
		13 512x512 slots
		32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): - Palette loaded
(II) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x04204
(II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xb0000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xb0000000
(II) CHROME(0): [drm] agpSize = 0x01e00000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] use agp.
(II) CHROME(0): [drm] Using 36109792 bytes for DRM memory heap.
(II) CHROME(0): [dri] frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] kernel data initialized.
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): direct rendering enabled
(II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
(II) CHROME(0): Using default xfree86 memcpy for video.
(II) CHROME(0): [XvMC] Registering chromeXvMC.
(II) CHROME(0): [XvMC] Initialized XvMC extension.
(II) CHROME(0): - Done
(==) RandR enabled
(II) Setting vga for screen 0.
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
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(WW) AIGLX: 3D driver claims to not support visual 0x22
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
Atom 4, CARD32 4, unsigned long 8
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
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
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
(II) CHROME(0): VIASwitchMode
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIAWriteMode
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(II) CHROME(0): Trying VBE Mode 1024x768 (0xc118) Refresh 60.00:
(II) CHROME(0): ViaVbeSetRefresh
(II) CHROME(0): Active Device: 2
(II) CHROME(0): Refresh Rate Index: 0
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
Freed 0 (pool 0)
Fulfilled via DRI at 30726400
Freed 0 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
SetGrabKeysState - disabled
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) CHROME(0): VIALeaveVT
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): ViaCursorStore
(II) CHROME(0): VIARestore
(II) CHROME(0): VT162xRestore
(II) CHROME(0): ViaLCDPower: On.
(II) CHROME(0): ViaDisablePrimaryFIFO
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) CHROME(0): VIAEnterVT
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VT162xSave
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(II) CHROME(0): Trying VBE Mode 1024x768 (0xc118) Refresh 60.00:
(II) CHROME(0): ViaVbeSetRefresh
(II) CHROME(0): Active Device: 2
(II) CHROME(0): Refresh Rate Index: 0
(II) CHROME(0): ViaCursorRestore
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
SetGrabKeysState - enabled
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 31340800 (pool 0)
Fulfilled via DRI at 30988544
DRM command buffer submission failed.

 0000: 0xf0000001 0x00000300 0xf000000d 0x00038d60 
 0004: 0xf000000e 0x83200000 0xf0000003 0x00000241 
 0008: 0xf0000004 0x00920002 0xf0000005 0x58000000 
 000c: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0010: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 0014: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
DRM command buffer submission failed.

 0000: 0xf0000001 0x00000300 0xf000000d 0x00038d60 
 0004: 0xf000000e 0x83200000 0xf0000003 0x00000241 
 0008: 0xf0000004 0x00920002 0xf0000005 0x58000000 
 000c: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0010: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 0014: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
 0018: 0xf0000001 0x00000300 0xf000000d 0x00056220 
 001c: 0xf000000e 0x83200000 0xf0000003 0x00000241 
 0020: 0xf0000004 0x00c60002 0xf0000005 0x18000000 
 0024: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0028: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 002c: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
DRM command buffer submission failed.

 0000: 0xf0000001 0x00000300 0xf000000d 0x00038d60 
 0004: 0xf000000e 0x83200000 0xf0000003 0x00000241 
 0008: 0xf0000004 0x00920002 0xf0000005 0x58000000 
 000c: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0010: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 0014: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
 0018: 0xf0000001 0x00000300 0xf000000d 0x00056220 
 001c: 0xf000000e 0x83200000 0xf0000003 0x00000241 
 0020: 0xf0000004 0x00c60002 0xf0000005 0x18000000 
 0024: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0028: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 002c: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
 0030: 0xf0000001 0x00000300 0xf000000d 0x0007d000 
 0034: 0xf000000e 0x83200000 0xf0000003 0x00000103 
 0038: 0xf0000004 0x0002007d 0xf0000005 0xe0000000 

 003c: 0xf0000006 0x00474747 0xf0000007 0x00474747 
 0040: 0xf000000f 0xffffffff 0xf0000010 0xffffffff 
 0044: 0xf0000000 0xf0000a01 0xf00000be 0x67676767 
Freed 30726400 (pool 2)
Freed 30988544 (pool 2)
Freed 30726400 (pool 0)
Fulfilled via DRI at 30726400
Freed 30988544 (pool 0)
Fulfilled via DRI at 31340800
Freed 30726400 (pool 2)
Freed 31340800 (pool 2)
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
SetGrabKeysState - disabled
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadRgbLut
SetGrabKeysState - enabled[/PHP]

---

### Post by rogier.de.groot on 2008-07-21
Hmmm... you seem to be using the 'openchrome' driver, but it's calling those 'VIALoadRgbLut' and 'VIALoadPalette' functions an awfull lot. Maybe someone else with experience using your video hardware can help...

---

### Post by defenestratos on 2008-07-21
thanks for your reply. I'll hang around here a while:KS

---

### Post by RomeReactor on 2008-07-21
Hi. Just out of interest, does this happen using the default Human theme? Have you tried using another driver?

---

### Post by defenestratos on 2008-07-22
> **RomeReactor said:**
> Hi. Just out of interest, does this happen using the default Human theme? Have you tried using another driver?

Yes it does still happen but the weird thing is that the colours of the human theme are all screwed up...They're all the colours of the previously selected theme.
How do I use another driver?

---

### Post by RomeReactor on 2008-07-22
> **defenestratos said:**
> Yes it does still happen but the weird thing is that the colours of the human theme are all screwed up...They're all the colours of the previously selected theme.
How do I use another driver?

There's an application called 'Screens & Graphics' in 'Applications->Other'; if you don't have that sub-menu enabled, you can launch the application by pressing ALT+F2 and writing or pasting:
```
gksudo displayconfig-gtk
```

There, go to the 'Graphics Card' tab and change the driver in the dropdown menu to either the UniChrome (if it's not the one you're already using), VIA or OpenChrome. If any of these are not installed, you can install them through Synaptic; search for these:

* xserver-xorg-video-via
* xserver-xorg-video-openchrome
* xserver-xorg-video-unichrome

Or, to install them through the terminal:
```
sudo aptitude install DRIVER_NAME
```
just substitute DRIVER_NAME for one of the previous three names. If you're not asked to restart your display, you can do so by pressing CTRL+ALT+BACKSPACE.

---

### Post by defenestratos on 2008-07-22
When I tried to install the three drivers it did not work. The first two are at the newest versions so that is no problem. The last one (openchrome) met unresolved dependencies (See below). I am running a fully updated and stock standard 8.04 LTS 64 bit. I have switched to Openchrome but it doesn't work in the testing function. What now? I mean my graphics work ok. I have a feeling it is when I am using the mouse or keyboard like in word processing where I get this problem. I never lose any data as I just switch workplace and back to refresh the screen. Kind of embaressing when I try and show my proprietary pals Ubuntu though and frustrating when I am typing. Can I file a bug?



[PHP]hugo@hugo-laptop:~$ sudo apt-get install xserver-xorg-video-openchrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hugo@hugo-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E: Broken packages
hugo@hugo-laptop:~$ sudo apt-get install xserver-xorg-video-openchrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hugo@hugo-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E: Broken packages
[/PHP]

---

### Post by defenestratos on 2008-07-22
Just tried to install openchrome in Synaptics but cancelled because I saw that it involved uninstalling Gnome. Thought I should ask about that before proceeding:)

---

### Post by RomeReactor on 2008-07-22
> **defenestratos said:**
> Just tried to install openchrome in Synaptics but cancelled because I saw that it involved uninstalling Gnome. Thought I should ask about that before proceeding:)

I hadn't noticed that trying to install the UniChrome driver removes not only Ubuntu-desktop (which wouldn't be that much of a problem, since it's just a metapackage and doesn't actually remove any application), but Xorg and all the other video drivers as well. Strange.

The terminal output you posted says you have broken packages; to fix that, run:
```
sudo dpkg --configure -a
```
and then:
```
sudo aptitude install -f
```
then reload the repository information:
```
sudo aptitude update
```

You might get some updates after that.

---

### Post by defenestratos on 2008-07-22
So are you sure it is ok for me to uninstall all of the other drivers? What if this one doesn't work? Can I still revert to my old, slightly malfunctioning driver?

---

### Post by RomeReactor on 2008-07-22
> **defenestratos said:**
> So are you sure it is ok for me to uninstall all of the other drivers? What if this one doesn't work? Can I still revert to my old, slightly malfunctioning driver?

No, don't install the UniChrome driver. Did you run the commands to fix the broken package? After that, boot into recovery mode and run XFIX.

---

### Post by defenestratos on 2008-07-22
> **RomeReactor said:**
> No, don't install the UniChrome driver. Did you run the commands to fix the broken package? After that, boot into recovery mode and run XFIX.

I ran the repairs but it still appears broken when I try to install. Synaptics says that I have no broken packages.
Strange though because since I ran the graphics mode program the glitch hasn't occurred yet in three hours of light use. Maybe I have configured something just by running the program?
Doesn't change the mystery of my "broken packages" though...

[PHP]hugo@hugo-laptop:~$ sudo dpkg --configure -a
[sudo] password for hugo: 
hugo@hugo-laptop:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
hugo@hugo-laptop:~$ sudo aptitude update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB                
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]              
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB            
Get:2 http://packages.medibuntu.org hardy Release.gpg [189B]                    
Hit http://ubuntusatanic.org hardy Release.gpg                                  
Ign http://ubuntusatanic.org hardy/main Translation-en_GB                       
Hit http://archive.canonical.com hardy Release                                  
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB      
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB        
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB      
Get:3 http://security.ubuntu.com hardy-security Release [58.5kB]                
Hit http://akirad.cinelerra.org akirad-hardy Release.gpg                        
Ign http://akirad.cinelerra.org akirad-hardy/main Translation-en_GB             
Hit http://de.archive.ubuntu.com hardy Release.gpg                              
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                  
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB              
Hit http://ubuntusatanic.org hardy Release                                      
Get:4 http://de.archive.ubuntu.com hardy/main Translation-en_GB [19.6kB]        
Hit http://akirad.cinelerra.org akirad-hardy Release                            
Hit http://archive.canonical.com hardy/partner Packages                         
Get:5 http://packages.medibuntu.org hardy Release [9335B]                       
Hit http://ubuntusatanic.org hardy/main Packages                                
Hit http://akirad.cinelerra.org akirad-hardy/main Packages                      
Hit http://archive.canonical.com hardy/partner Sources                          
Get:6 http://de.archive.ubuntu.com hardy/restricted Translation-en_GB [1956B]   
Get:7 http://de.archive.ubuntu.com hardy/universe Translation-en_GB [4368B]     
Get:8 http://de.archive.ubuntu.com hardy/multiverse Translation-en_GB [36.1kB]  
Get:9 http://de.archive.ubuntu.com hardy-updates Release.gpg [189B]             
Ign http://de.archive.ubuntu.com hardy-updates/main Translation-en_GB           
Ign http://de.archive.ubuntu.com hardy-updates/restricted Translation-en_GB     
Ign http://de.archive.ubuntu.com hardy-updates/universe Translation-en_GB       
Ign http://de.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB     
Hit http://de.archive.ubuntu.com hardy Release                                  
Get:10 http://security.ubuntu.com hardy-security/main Packages [31.8kB]         
Get:11 http://de.archive.ubuntu.com hardy-updates Release [58.5kB]              
Get:12 http://security.ubuntu.com hardy-security/restricted Packages [6465B]    
Get:13 http://security.ubuntu.com hardy-security/main Sources [8117B]           
Get:14 http://security.ubuntu.com hardy-security/restricted Sources [908B]      
Get:15 http://security.ubuntu.com hardy-security/universe Packages [23.8kB]     
Get:16 http://security.ubuntu.com hardy-security/universe Sources [3318B]       
Get:17 http://packages.medibuntu.org hardy/free Packages [6209B]              
Get:18 http://security.ubuntu.com hardy-security/multiverse Packages [3891B]    
Get:19 http://security.ubuntu.com hardy-security/multiverse Sources [14B]       
Hit http://de.archive.ubuntu.com hardy/main Packages                            
Hit http://de.archive.ubuntu.com hardy/restricted Packages                 
Hit http://de.archive.ubuntu.com hardy/main Sources                        
Hit http://de.archive.ubuntu.com hardy/restricted Sources
Hit http://de.archive.ubuntu.com hardy/universe Packages
Hit http://de.archive.ubuntu.com hardy/universe Sources
Hit http://de.archive.ubuntu.com hardy/multiverse Packages
Hit http://de.archive.ubuntu.com hardy/multiverse Sources
Get:20 http://packages.medibuntu.org hardy/non-free Packages [7801B]
Get:21 http://de.archive.ubuntu.com hardy-updates/main Packages [279kB]
Get:22 http://de.archive.ubuntu.com hardy-updates/restricted Packages [6465B]
Get:23 http://de.archive.ubuntu.com hardy-updates/main Sources [80.8kB]
Get:24 http://de.archive.ubuntu.com hardy-updates/restricted Sources [908B]
Get:25 http://de.archive.ubuntu.com hardy-updates/universe Packages [70.6kB]
Get:26 http://de.archive.ubuntu.com hardy-updates/universe Sources [16.6kB]
Get:27 http://de.archive.ubuntu.com hardy-updates/multiverse Packages [16.1kB]
Get:28 http://de.archive.ubuntu.com hardy-updates/multiverse Sources [2612B]
Fetched 754kB in 4s (170kB/s)                        
Reading package lists... Done
hugo@hugo-laptop:~$ sudo apt-get install xserver-xorg-video-unichrome
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E: Broken packages
[/PHP]

---

### Post by RomeReactor on 2008-07-22
Remember that if you try to install the UniChrome driver it will remove *all other video drivers*, so I suggest you don't.

Regarding the broken packages, open Synaptic, select 'Custom Filters' in the lower left, and highlight 'Broken' in the upper left pane; it should show the package(s), so please post it/them. Then go to 'Edit->Fix Broken Packages' and see if that helps.

---

### Post by defenestratos on 2008-07-22
It says that I have no broken packages in Synaptics. I sense a bug is going on... I've never filed one before. Exciting!

> **RomeReactor said:**
> Remember that if you try to install the UniChrome driver it will remove *all other video drivers*, so I suggest you don't.

Regarding the broken packages, open Synaptic, select 'Custom Filters' in the lower left, and highlight 'Broken' in the upper left pane; it should show the package(s), so please post it/them. Then go to 'Edit->Fix Broken Packages' and see if that helps.

---

### Post by RomeReactor on 2008-07-22
Have you disabled any repositories recently? Also try this:
```
sudo dpkg --audit
```
Sometimes packages installed from .deb files won't show up in Synaptic--or programs compiled from source without using checkinstall. Have you installed any programs lately that might coincide with the display glitch?

Also, the problem *could* come from those repositories you added. It's always best to stick to the official ones.

---

### Post by defenestratos on 2008-07-29
I tried all that. The only thing I didn't was removing the extra repos...It is a pretty slim chance that they would cause conflicting packages...right? Otherwise what can I do to get around this hardware glitch? I still don't know the exact name of the chipset I have. Could someone tell me from the readout above or what do I have to do to find it. If I find it I can google it.

Another possibility is how do I reset my sources.lst? I don't use many extras really. They were for individual programs.


> **RomeReactor said:**
> Have you disabled any repositories recently? Also try this:
```
sudo dpkg --audit
```
Sometimes packages installed from .deb files won't show up in Synaptic--or programs compiled from source without using checkinstall. Have you installed any programs lately that might coincide with the display glitch?

Also, the problem *could* come from those repositories you added. It's always best to stick to the official ones.

---

### Post by RomeReactor on 2008-07-29
> **defenestratos said:**
> I tried all that. The only thing I didn't was removing the extra repos...It is a pretty slim chance that they would cause conflicting packages...right?

The problem seems to be with the video configuration only. To find out which specific video card you have run either of the following:
```
lspci | grep VGA
```
or:
```
sudo lshw -C display
```

I'm not absolutely sure, but Ubuntu should have selected the VIA driver for your video card during the installation. If you installed the OpenChrome driver, and you have backups of all your important data, try reinstalling the system, this time letting Ubuntu choose the driver--which hopefully won't be the OpenChrome.

---

### Post by defenestratos on 2008-07-30
But if I reinstall exactly the same thing will happen because I would be installing from the same image. I believe it these glitches are a bug and I am interested to know whether there is a workaround. Restoring the Sources.lst to it's default settings might find this extra driver.
Reinstalling seems quite extreme to repair an otherwise working system. Can I just reinstall the graphics drivers?

---

### Post by RomeReactor on 2008-07-30
You could try removing (purging, even) the OpenChrome driver and install the VIA. Then reboot, go into Grub, start in recovery mode and use XFIX again. What was the output of the previous commands? Knowing the particular chipset we're dealing with will help a lot.

---

### Post by defenestratos on 2008-07-30
I have had a bit of a snoop around Launchpad and it seems that I am not alone in this. 

"hugo@hugo-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)"


> **RomeReactor said:**
> You could try removing (purging, even) the OpenChrome driver and install the VIA. Then reboot, go into Grub, start in recovery mode and use XFIX again. What was the output of the previous commands? Knowing the particular chipset we're dealing with will help a lot.

---

### Post by RomeReactor on 2008-07-30
Searching for your video card (S3 Unichrome Pro VGA Adapter (rev 01)) at Launchapad only yielded two bug reports, including yours, and both are against the OpenChrome driver; hopefully someone at Launchpad will provide an adequate solution.

Also, give the Live CD a spin for a while, and see if the glitch shows up there as well. If it doesn't, it's possible a re-installation would correct the problem. It's not uncommon to install Ubuntu and have some sort of problem, only to reinstall and have the problem sorted out by itself.

---

### Post by defenestratos on 2008-07-31
The live CD has the glitch too. I have to change the resolution to 1024x768. The weird glitches are not there but it starts to happen on my installation after the system has been up for a few hours. I believe that the glitches started happening after I ran some updates. Is there a log of the updates I installed? If so could I revert to an older version of the driver?

---

### Post by RomeReactor on 2008-07-31
To find the update information, in Synaptic go to 'File->History'. You can get previous versions of the OpenChrome driver [here]("http://packages.ubuntu.com/search?keywords=openchrome&searchon=names&suite=all&section=all"); to install them, double-click on the .DEB file once it downloads.

Before that, boot into a previous kernel and see if the problems happen there as well. I'm out of suggestions for the moment, aside from recommending a backup of your data and reinstalling Ubuntu.

---

### Post by ChocolateChip_Wookie on 2008-07-31
Have you tried installing other Ubuntu derivations such as Linux Mint in another partition? Do you get the same issue? Personally, if this were Windows, I would have said you have a driver problem. Find the driver, fix the problem. Is it possible you have installed something that is conflicting?

As for installing another edition of Ubuntu, it would seem to make sense. When I had a similar problem with the drivers for my video cam, I was getting weird things happen. I re-installed a virgin copy and started the driver install again from scratch. No monkeying with Bash commands or thrashing around in the dark, just one step at a time. Problem solved.

---

### Post by ChocolateChip_Wookie on 2008-07-31
> **defenestratos said:**
> The live CD has the glitch too. I have to change the resolution to 1024x768. [COLOR="Red"]The weird glitches are not there but it starts to happen on my installation after the system has been up for a few hours.[/COLOR] I believe that the glitches started happening after I ran some updates. Is there a log of the updates I installed? If so could I revert to an older version of the driver?

That tells you that something happens within those few hours. Perhaps some process is grabbing all the memory and not letting go? Perhaps there is some driver installed at boot that slowly eats all the graphics memory?

---


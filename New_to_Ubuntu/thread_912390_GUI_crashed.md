---
title: "GUI crashed"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by shankhs on 2008-09-06
I was trying some small ubuntu hacks and suddenly my GUI crashed !!!!
first of all I changed the permission of "/usr" by chmod 777 -R /usr (as a su) then I rechanged the permission of the /usr/bin/sudo by chmod 4755 /usr/bin/sudo because I was getting some messages whenever I was trying to do sudo.

Then once sudo was restored I did "sudo apt-get update" here the problem started , it said some packages need to be fixed so I obeyed and I tried to fix the packages then I restarted and oops!!! I got the message "the GUI has crashed. attempting another one" I can login as root in unix-type screen(CUI) there I attempted "startx" as a result I got a GUI with root and while I am writing this the system has tried atleast 7 times to restore the GUI but failed.
I tried "dpkg-reconfigure xserver-xorg" but I dont know much about it.
What should I do now?????:confused:

---

### Post by zephyrcat on 2008-09-06
Well, the first thing I would try is undoing the changes you made before, restarting, and trying again. I am definitely not an expert on fixing broken systems, though, so see what others say.

---

### Post by shankhs on 2008-09-07
Is there any way to restore GUI using ubuntu live CD???

---

### Post by hyper_ch on 2008-09-07
changing permissions of filesystem paths is a big "No, no"

No clue how to fix that.

---

### Post by shankhs on 2008-09-07
There is always a way to fix things.I am sure somebody will come up with a solution and I will be able to fix it.

Where there is a will there is a way.

---

### Post by Crafty Kisses on 2008-09-07
I'd like to see your X log, your X can be restarting for some reason, let's take a look.
```
sudo gedit /var/log/Xorg.0.log
```

---

### Post by shankhs on 2008-09-07
OOPS!!! I am in college I will give it as soon as I wil reach my room!!!!!

---

### Post by Crafty Kisses on 2008-09-07
> **shankhs said:**
> OOPS!!! I am in college I will give it as soon as I wil reach my room!!!!!

Thanks for the update, I'm just saying it could very well be a X issue, for some odd reason, thanks for the response though. I'm gonna try to solve this, this has me interested. :)

---

### Post by shankhs on 2008-09-07
This is my /var/log/Xorg.0.log
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux shankhs 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  7 18:06:11 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 8086,4c43 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2772 card 8086,4c43 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,27d8 card 8086,0204 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 8086,4c43 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 8086,4c43 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 8086,4c43 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 8086,4c43 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 8086,4c43 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 8086,4c43 rev 01 class 0c,05,00 hdr 00
(II) PCI: 04:08:0: chip 8086,1094 card 8086,0001 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:2), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0x50100000/19, 0x40000000/28, 0x50180000/18, I/O @ 0x20e0/3
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
	[0] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[1] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[2] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[3] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[4] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[5] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[6] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[8] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[9] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[10] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[11] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[12] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[13] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[19] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[20] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[21] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[22] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[1] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[2] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[3] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[4] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[5] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[6] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[8] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[9] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[10] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[11] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[12] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[13] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[19] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[20] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[21] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[22] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
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
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[13] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[14] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[15] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[16] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[17] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[18] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[19] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[25] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[26] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[27] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[28] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
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
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 945G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[13] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[14] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[15] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[16] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[17] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[18] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[19] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[25] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[26] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[27] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[28] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[16] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[17] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[18] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[19] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[20] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[21] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[22] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[28] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[29] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[30] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[31] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50100000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (340, 270) mm
(**) intel(0): DPI set to (95, 120)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50180000 - 0x501bffff (0x40000) MS[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[2] 0	0	0x50100000 - 0x5017ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[8] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[9] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[10] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[11] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[12] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] 0	0	0x000020e0 - 0x000020e7 (0x8) IS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[21] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[22] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[23] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[24] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[25] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[26] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[32] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[33] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[34] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[35] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): [drm] Registers = 0x50100000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] mapped front buffer at 0x41000000, handle = 0x41000000
(II) intel(0): [drm] mapped back buffer at 0x44000000, handle = 0x44000000
(II) intel(0): [drm] mapped depth buffer at 0x45000000, handle = 0x45000000
(II) intel(0): [drm] mapped classic textures at 0x46000000, handle = 0x46000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000003f832000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 20
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 270
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "us"
(**) Generic Keyboard: XkbOptions: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
SetClientVersion: 0 9
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439

```

---

### Post by shankhs on 2008-09-08
I waited for 2 days with the hope that somebody might help but it seems that ubuntu gurus are very busy these days. never mind I started to restore my ubuntu GUI alone using hit and trial method and also with high probability that I might screw the system more.

So I first thought about the possible remedies:
1.Change back the permissions of /usr
I did that using (in su) ```
chmod -R 4755 /usr
```
nothing happened after restart no GUI I got the same CUI.
One very interesting thing happened when I checked the permission of usr in / directory I got```

drwsr-xr-x     usr
```

What is the meaning of **_s_** here?

2.I assumed that GUI is user specific that is it is stored in the home of the user (i made the assumption because I can enter the GUI using root permission ) so I deleted my user account and created a new one in the same group.

so now when I restarted I was redirected to the CUI with these things written on the terminal:(please note that the following is not copy paste I am doing this manually.Although I am writing this with great caution but still I can miss something)
```

Module loader present
Markers:(--- probed,(**)from config file,(==)default setting,(++)from command line,(!!) notice,(II)informational,(WW)warning,(EE)error,(NI) not implemented,(??)unknown.

(==)log file:"/var/log/Xorg.0.log" Time:Mon Sep 8 13:19:01 2008
(==)Using config File: "/etc/X11/xorg-conf"
(II)Module "ddc" already built-in
(II)Module "i2c" already built in
(II)Module "ramdac" already built-in

expected keysym,got XF86KbdLightOnOff:line 70 of PC
expected keysym,got XF86KbdBrightnessDown:line 71 of PC
expected keysym,got XF86KbdBrightnessUp:line 72 of PC
expected keysym,got XF86KbdLightOnOff:line 70 of PC
expected keysym,got XF86KbdBrightnessDown:line 71 of PC
expected keysym,got XF86KbdBrightnessUp:line 72 of PC

Waiting for X server to shut down
FreeFontPath:FPE "/usr/share/fonts/X11/misc"
refcount is 2 should be 1:fixing

xuth: /home/shanx/.Xauthority not writable changes will be ignored.
xuth: /home/shanx/.Xauthority not writable changes ignored.
rm:Cannot remove '/tmp/serverauth.mJJYKn6877:Opereation not permitted.

```
What the hell is this????
I have many questions like why I shouldnt change the permission of /usr?
What happened once I changed the permission of /usr??????
How can I restore the GUI?????

---

### Post by dark_harmonics on 2008-09-08
You should try resetting your usr to 755 using the same command you already figured out. Try this:
```
 sudo chmod -R 755 /usr

```

my /usr folder does not have an S in the permissions.

I need to repeat the wisdom that you should not change the permissions on system folders. Your system NEEDS to access those files and if the permissions are wrong it can open holes in security, or as in your case make these files unavailable to the system processes. 

If fixing your permissions issue does not resolve your GUI problem, you might want to try reconfiguring xorg with:
```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```
^backs up your current configuration

```
sudo dpkg-reconfigure xserver-xorg
```
^reconfigures your xorg

Did you reset permissions in any other folder (like /home/shanx)? If it gets much more complicated than this you should probably either do a clean install or compare your permission settings to another computer to figure out what you need to set them to.

---

### Post by 3rdalbum on 2008-09-08
Any task that you do that requires "sudo" to work, is something that can potentially stuff up your system. Users that shouldn't be fiddling with the operating system don't get access to sudo; only the administrators do.

If resetting the permissions of /usr doesn't help, you could try reinstalling all Xorg packages in Synaptic or apt-get.

---

### Post by ByteJuggler on 2008-09-08
> **shankhs said:**
> ```

drwsr-xr-x     usr
```

What is the meaning of **_s_** here?


It means the folder is setuid.  It's the effect of the "4" in front of the 755 in your "chmod" command.  This is generally a very bad idea.  You should ***_[COLOR="Red"]*never*[/COLOR]_*** make files setuid if you don't know exactly what you're doing!  Such files are a wide gaping security hole, since they run under the account of the owner of the file (which in /usr's case is root...) and not under the initiating user's account as per default!

---

### Post by ByteJuggler on 2008-09-08
> **shankhs said:**
> 
xuth: /home/shanx/.Xauthority not writable changes will be ignored.
xuth: /home/shanx/.Xauthority not writable changes ignored.
rm:Cannot remove '/tmp/serverauth.mJJYKn6877:Opereation not permitted.
[/code]
What the hell is this????
I have many questions like why I shouldnt change the permission of /usr?
What happened once I changed the permission of /usr??????
How can I restore the GUI?????

/usr is like "Program Files" in Windows.  The permissions are set up correctly by the operating system.  Changing them can break the OS in many ways since it can stop you and the rest of the system from accessing files which may be needed for correct operation.  Why do you want to change it anyway?   

It's impossible to know exactly what's happened on your system, except that I note that "/home/shanx/.Xauthority not writable " implies that that file probably doesn't belong to you (probably to root) which is why you can't write to it, and which is why you r X likely won't start.

Try the following:

```
sudo chown -R shankhs.shankhs /home/shankhs/*
```

Then

```
sudo chown -R shankhs.shankhs /home/shankhs/.*
```

Then try starting X again and post the output here.

To get only the error messages, do:
```
grep "(EE)" /var/log/Xorg.0.log
```

---

### Post by shankhs on 2008-09-09
> **ByteJuggler said:**
> /usr is like "Program Files" in Windows.  The permissions are set up correctly by the operating system.  Changing them can break the OS in many ways since it can stop you and the rest of the system from accessing files which may be needed for correct operation.  Why do you want to change it anyway?   
Actually I was trying to make a deb package,I am a newbie (in developing for ubuntu ).I didnt get good tutorials to make .deb packages so I started to learn by myself,I needed to copy some header files in /usr/include which was impossible because of the permissions given by the root so I changed it(and screwed my syatem)
> **ByteJuggler said:**
> 
It's impossible to know exactly what's happened on your system, except that I note that "/home/shanx/.Xauthority not writable " implies that that file probably doesn't belong to you (probably to root) which is why you can't write to it, and which is why you r X likely won't start.

Try the following:

```
sudo chown -R shankhs.shankhs /home/shankhs/*
```

Then

```
sudo chown -R shankhs.shankhs /home/shankhs/.*
```

Then try starting X again and post the output here.

To get only the error messages, do:
```
grep "(EE)" /var/log/Xorg.0.log
```
Tried all of them but no help first of all I dont know anything about how to reconfigure my xorg but still I tried and I dont know what happened except that my GUI was not restored.](*,)](*,)](*,)
```
grep "(EE)" /var/log/Xorg.0.log
```
gave me this:
```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```
thats it!!!!!!.
I did everything but still no progress...](*,)
I have another idea:
[B]Can I assume that nothing has happened to the linux kernel?
If I can do so can i download the gnome source code (or even try to write a new desktop environment) and integrate with the kernel.???
Please give me links to get started if you belief that its possible to create a new desktop environment for the ubuntu linux kernel or download the gnome source code and integrate with the ubuntu linux kernel.If I have screwed the linux kernel can I repair it?[/B]
Thankyou.

---

### Post by shankhs on 2008-09-10
I am moving this posts's discussion to the development sub-forum.

---

### Post by ByteJuggler on 2008-09-10
> **shankhs said:**
> Actually I was trying to make a deb package,I am a newbie (in developing for ubuntu ).I didnt get good tutorials to make .deb packages so I started to learn by myself,I needed to copy some header files in /usr/include which was impossible because of the permissions given by the root so I changed it(and screwed my syatem)

You should've just copied the files with "sudo" so you would've run the copy as root and it consequently would've worked... (Just saying, for future reference.)

> **shankhs said:**
> 
Tried all of them but no help first of all I dont know anything about how to reconfigure my xorg but still I tried and I dont know what happened except that my GUI was not restored.](*,)](*,)](*,)
```
grep "(EE)" /var/log/Xorg.0.log
```
gave me this:
```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```
thats it!!!!!!.

OK Well then your log did not contain any errors.  Can you perhaps post the entire contents of the log instead?  

> **shankhs said:**
> 
I did everything but still no progress...](*,)
I have another idea:
**Can I assume that nothing has happened to the linux kernel? **

Yes, the X Window system is quite separate from the kernel.  Nothing would've happened to it.  

> **shankhs said:**
> 
If I can do so can i download the gnome source code (or even try to write a new desktop environment) and integrate with the kernel.???


You can write another desktop environment, but you won't integrate it with the kernel.  

> **shankhs said:**
> 
Please give me links to get started if you belief that its possible to create a new desktop environment for the ubuntu linux kernel or download the gnome source code and integrate with the ubuntu linux kernel.

Do some googling, there's lots of information on the internet.   I don't however think creating another desktop environment is exactly an easy project for someone who is still having trouble sorting out their X config and having to rely on help in the beginners forum.   

> **shankhs said:**
> 
If I have screwed the linux kernel can I repair it?[/B]
Thankyou.
Yes, but... I don't think you really understand what the kernel is or, what "screwing it" really means.  To be precise:  Your graphics not working has zero to do with whether Linux kernel is working or not. To "screw" the kernel you have to download it's source, modify the source (break it), recompile it, then reboot with the broken kernel.  Then you've "screwed it" in my book.  And of course you can fix such a situation -- boot up with an older working kernel, change the source again and recompile again.  Problem repaired.  None of that however has anything remotely to do with X Windows or Gnome.

---

### Post by shankhs on 2008-09-12
Thanx ByteJuggler and et al for helping me.
ByteJuggler was correct,I must first learn the basics.
The happy news is I solved my problem,
first I changed back the permission of usr to 755 and then I deleted my previous account and created a new one.That worked HOW???? Honestly I dont know!!!!
There are still a few hiccups though.The new account I have created is very restricted that is I cannot do any administrative job,in my initial account it used to ask me the root password everytime i did any administrative work like changing my internet connection settings,etc but now this doesnt happen.Still whenever I enter sudo it says```
sudo: must be setuid root
```!!!I checked the permissions:
```

shanx@shankhs:~$ ls -l /usr/bin/sudo
-rwxr-xr-x 2 root root 107872 2008-05-15 06:11 /usr/bin/sudo

``` its correct I think...then wats the problem????
 WHY is this so????(Please guide me I want to know and learn)
One more thing I would like to learn about
```

sudo dpkg-reconfigure xserver-xorg

```
and how to cofigure the xserver and stuffs related to it I googled a lot but didnt find any tutorials.If you have any links please share it with me.
As instructed by ByteJuggler I am postimg complete log:
```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux shankhs 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 03:34:56 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) PCI: 00:00:0: chip 8086,2770 card 8086,4c43 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2772 card 8086,4c43 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1b:0: chip 8086,27d8 card 8086,0204 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 8086,4c43 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 8086,4c43 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 8086,4c43 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 8086,4c43 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 8086,4c43 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 8086,4c43 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 8086,4c43 rev 01 class 0c,05,00 hdr 00
(II) PCI: 04:08:0: chip 8086,1094 card 8086,0001 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:2), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0x50100000/19, 0x40000000/28, 0x50180000/18, I/O @ 0x20e0/3
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
	[0] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[1] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[2] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[3] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[4] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[5] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[6] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[8] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[9] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[10] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[11] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[12] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[13] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[19] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[20] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[21] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[22] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[1] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[2] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[3] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[4] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[5] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[6] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[7] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[8] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[9] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[10] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[11] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[12] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[13] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[19] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[20] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[21] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[22] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
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
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[13] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[14] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[15] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[16] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[17] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[18] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[19] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[25] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[26] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[27] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[28] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
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
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
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
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 945G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[13] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[14] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[15] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[16] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[17] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[18] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[19] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[25] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[26] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[27] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[28] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[5] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[6] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[7] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[8] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[9] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[16] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[17] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[18] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[19] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[20] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[21] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[22] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[28] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[29] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[30] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[31] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
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
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0x40000000
(--) intel(0): IO registers at addr 0x50100000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (340, 270) mm
(**) intel(0): DPI set to (95, 120)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x50180000 - 0x501bffff (0x40000) MS[B]
	[1] 0	0	0x40000000 - 0x4fffffff (0x10000000) MS[B]
	[2] 0	0	0x50100000 - 0x5017ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x50000000 - 0x50000fff (0x1000) MX[B]
	[8] -1	0	0x501c4000 - 0x501c43ff (0x400) MX[B]
	[9] -1	0	0x501c0000 - 0x501c3fff (0x4000) MX[B]
	[10] -1	0	0x50180000 - 0x501bffff (0x40000) MX[B](B)
	[11] -1	0	0x40000000 - 0x4fffffff (0x10000000) MX[B](B)
	[12] -1	0	0x50100000 - 0x5017ffff (0x80000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] 0	0	0x000020e0 - 0x000020e7 (0x8) IS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00001000 - 0x0000103f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x0000201f (0x20) IX[B]
	[21] -1	0	0x000020a0 - 0x000020af (0x10) IX[B]
	[22] -1	0	0x000020e8 - 0x000020eb (0x4) IX[B]
	[23] -1	0	0x000020c0 - 0x000020c7 (0x8) IX[B]
	[24] -1	0	0x000020ec - 0x000020ef (0x4) IX[B]
	[25] -1	0	0x000020c8 - 0x000020cf (0x8) IX[B]
	[26] -1	0	0x000020b0 - 0x000020bf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00002020 - 0x0000203f (0x20) IX[B]
	[32] -1	0	0x00002040 - 0x0000205f (0x20) IX[B]
	[33] -1	0	0x00002060 - 0x0000207f (0x20) IX[B]
	[34] -1	0	0x00002080 - 0x0000209f (0x20) IX[B]
	[35] -1	0	0x000020e0 - 0x000020e7 (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 238848 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 955388 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): [drm] Registers = 0x50100000
(II) intel(0): [drm] ring buffer = 0x40000000
(II) intel(0): [drm] mapped front buffer at 0x41000000, handle = 0x41000000
(II) intel(0): [drm] mapped back buffer at 0x44000000, handle = 0x44000000
(II) intel(0): [drm] mapped depth buffer at 0x45000000, handle = 0x45000000
(II) intel(0): [drm] mapped classic textures at 0x46000000, handle = 0x46000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0x40000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x06000000 (pgoffset 24576)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000003f832000 physical
)
(II) intel(0): 0x007bf000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x02000000-0x03dfffff: exa offscreen (30720 kB)
(II) intel(0): 0x04000000-0x04ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x05ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x06000000-0x07ffffff: classic textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 20
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
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
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
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
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 270
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
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "us"
(**) Generic Keyboard: XkbOptions: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439
SetClientVersion: 0 9
(II) intel(0): EDID vendor "SAM", prod id 439
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): EDID vendor "SAM", prod id 439

```

---


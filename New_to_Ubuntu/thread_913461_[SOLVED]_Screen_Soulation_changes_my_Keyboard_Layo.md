---
title: "[SOLVED] Screen Soulation changes my Keyboard Layout"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Sugi on 2008-09-07
Well, I plugged my LCD TV into my ASUS G1 laptop and I enjoyed mirror display.  I unplug the monitor and did a restart.  I notice two keys (M-key and I-key) are remapped to numbers after login.

My M-key becomes a 0 (zero) and my I-key becomes a 5.  I have no idea how fix it.  I have the Keyboard layout set to Default of USA.  I have notice everything else seems to be working.  I can even set the brightness of my Laptop with the keyboard (Fn+F6).

I have looked at the xorg.conf and tried switch keyboard layout n System>Pref.>Keyboard, but that is not helping me.

Side Note:  The M-Key and I-Key works during login but once Desktop (x is started) those two keys becomes numbers.

Sugi

**Update:**

> **m_duck said:**
> Is it definitely just the two keys? If there are more as well (u, o, p, j etc) it seems like its just the num lock is enabled and as it is a laptop, the letter keys become number ones. If this isn't the case, I've not the foggiest I'm afraid.

This fixed it.

---

### Post by Sugi on 2008-09-07
Please help me. this is impossible to run my computer without those two keys working.

BUMP

---

### Post by suprfish on 2008-09-07
Please post the output of ```
cat /var/log/Xorg.0.log
```

---

### Post by Sugi on 2008-09-07
```
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
(II) PCI: 00:00:0: chip 8086,27a0 card 1043,1237 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,1339 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,1237 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,1237 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,1237 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,1237 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,1237 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 8086,27b9 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1043,1237 rev 02 class 01,01,80 hdr 00
(II) PCI: 01:00:0: chip 10de,0397 card 1043,1442 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10ec,8168 card 1043,11f5 rev 01 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 8086,4222 card 8086,1000 rev 02 class 02,80,00 hdr 00
(II) PCI: 04:01:0: chip 1180,0476 card d000,0000 rev b3 class 06,07,00 hdr 82
(II) PCI: 04:01:1: chip 1180,0552 card 1043,1437 rev 08 class 0c,00,10 hdr 80
(II) PCI: 04:01:2: chip 1180,0822 card 1043,1437 rev 17 class 08,05,00 hdr 80
(II) PCI: 04:01:3: chip 1180,0592 card 1043,1437 rev 08 class 08,80,00 hdr 80
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf9f00000 - 0xfdffffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbdf00000 - 0xddefffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe000000 - 0xfe0fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe100000 - 0xfe1fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,8), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfe200000 - 0xfeafffff (0x900000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xddf00000 - 0xdfefffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (4:1:0), (4,5,8), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
(--) PCI:*(1:0:0) nVidia Corporation GeForce Go 7700 rev 161, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfc000000/24, I/O @ 0xbc00/7, BIOS @ 0xfbfe0000/17
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
	[0] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[1] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[2] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[3] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[4] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[5] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[7] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[1] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[2] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[3] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[4] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[5] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[7] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[8] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[12] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[13] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[14] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[19] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[20] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
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
	[4] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[5] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[8] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[9] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[11] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[5] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[8] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[9] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[11] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[25] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[26] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[5] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[8] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[9] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[11] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7700 (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.49.12
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7700 at PCI:1:0:0:
(--) NVIDIA(0):     CMO (DFP-0)
(--) NVIDIA(0): CMO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): CMO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (129, 133); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff000 - 0xfeaff0ff (0x100) MX[B]
	[5] -1	0	0xfeaff400 - 0xfeaff4ff (0x100) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
	[8] -1	0	0xfe0ff000 - 0xfe0fffff (0x1000) MX[B]
	[9] -1	0	0xfebfbc00 - 0xfebfbfff (0x400) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfffff (0x4000) MX[B]
	[11] -1	0	0xfbfe0000 - 0xfbffffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000e480 - 0x0000e49f (0x20) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e81f (0x20) IX[B]
	[28] -1	0	0x0000e880 - 0x0000e89f (0x20) IX[B]
	[29] -1	0	0x0000ec00 - 0x0000ec1f (0x20) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(WW) NVIDIA(0): Error: Unable to find DOS (Enable/Disable output switching)
(WW) NVIDIA(0):     file path under /proc/acpi/video. NVIDIA X driver will not
(WW) NVIDIA(0):     be able to respond to  display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
Atom 4, CARD32 4, unsigned long 4
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
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event8
(**) Option "Device" "/dev/input/event8"
(--) Synaptics Touchpad touchpad found
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

---

### Post by suprfish on 2008-09-07
I was hoping someone else would reply, since I don't know. Maybe you could post your xorg.conf file as well?

---

### Post by Sugi on 2008-09-07
I can't.  I can't type the location out in my terminal.

Sugi

---

### Post by m_duck on 2008-09-07
Is it definitely just the two keys? If there are more as well (u, o, p, j etc) it seems like its just the num lock is enabled and as it is a laptop, the letter keys become number ones. If this isn't the case, I've not the foggiest I'm afraid.

---

### Post by Sugi on 2008-09-07
m_duck, Oh my god.  Your right.  I can't believe I didn't even think about that. (I have never even enable those num keys before. >.<  Thanks.  I going to go now, I feel sillly.

Sugi

---


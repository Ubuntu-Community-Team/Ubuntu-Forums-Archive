---
title: "System locks up...."
date: 2013-04-30
forum: New to Ubuntu
---

### Post by ccsylvia1 on 2013-04-30
Good morning;

This is my first post, but I have been a *buntu user for about three years.... Please be gentle!!!

I'm running Lubuntu 12.04.02 LXLE, and have been having problems with the system just freezing when the kiddies are playing on Firefox and chromium (mostly disney.com and lego.com), and most recently it froze during minetest (not online).

I'd like to know if there is a log somewhere that would begin to tell me where the problem is....

Any help would be appreciated.

Thanks

Chris

---

### Post by alhefner on 2013-04-30
> **ccsylvia1 said:**
> Good morning;

This is my first post, but I have been a *buntu user for about three years.... Please be gentle!!!

I'm running Lubuntu 12.04.02 LXLE, and have been having problems with the system just freezing when the kiddies are playing on Firefox and chromium (mostly disney.com and lego.com), and most recently it froze during minetest (not online).

I'd like to know if there is a log somewhere that would begin to tell me where the problem is....

Any help would be appreciated.

Thanks

Chris
I have the same issue currently. It happens more while using Firefox than at any other time but can happen randomly as well.

Take a look in your "system log viewer". It should be one of the installed programs. Viewing the log files, you can scroll through them to times when your system froze and see the last log entries just prior to you having to remove power in order to start the system again. You'll probably find the the GPU (graphics processing) is locking up. This is a known issue and a bug that is being worked on currently.

Some people have had some success with going to an earlier version of the Linux kernel and using that.

---

### Post by ccsylvia1 on 2013-04-30
I will keep an eye on this log.  I'm not sure what to really look for though.

It shows a lot of these type of entries:

SPT=34956 DPT=32412 LEN=29
[UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.1.7 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=34956 DPT=32412 LEN=29
[UFW BLOCK] IN=eth0 OUT= MAC=90:e6:ba:4e:3f:00:00:0d:4b:7a:45:01:08:00 SRC=192.168.1.9 DST=192.168.1.7 LEN=241 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=14998 LEN=221
[UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.1.7 DST=239.0.0.250 LEN=49 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=34956 DPT=32412 LEN=29

I'm not entirely sure of the exact time of the last freeze up though.

I will keep a closer eye.

Thanks!!

Chris

---

### Post by alhefner on 2013-05-03
There was an update to the kernel yesterday. After I installed that, my system hasn't frozen once. I bet that if you installed it too, you can mark this thread as solved.

---

### Post by ccsylvia1 on 2013-05-08
I will check it out....Thank you.

---

### Post by ccsylvia1 on 2013-05-09
Ok....

I did the update, still same problem.

I'm frustrated.  I'm thinking of fresh installing 13.04.

Thoughts?

Chris

---

### Post by ccsylvia1 on 2013-05-09
I realize after reading undecim's sticky post about suggestions on how to get your post answered as quickly as possible, that I've have not included some essential material:

lspci | grep VGA results are:


01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]

and my results of the KSystemlog X.org log are as follows:

	Information	[    14.617] (II) VESA: driver for VESA chipsets: vesa
	Information	[    14.617] (II) FBDEV: driver for framebuffer: fbdev
	Information	[    14.617] (++) using VT number 7
	Information	
	Information	[    14.617] (WW) Falling back to old probe method for fglrx
	Information	[    14.626] (II) Loading PCS database from /etc/ati/amdpcsdb
	Information	[    14.626] (--) Assigning device section with no busID to primary device
	Information	[    14.626] (--) Chipset Supported AMD Graphics Processor (0x9710) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
	Information	[    14.627] (II) AMD Video driver is running on a device belonging to a group targeted for this release
	Information	[    14.627] (II) AMD Video driver is signed
	Information	[    14.627] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
	Information	[    14.627] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
	Information	[    14.627] (II) fglrx(0): pEnt->device->identifier=0xb774e6bf
	Information	[    14.627] (WW) Falling back to old probe method for vesa
	Information	[    14.627] (WW) Falling back to old probe method for fbdev
	Information	[    14.627] (II) Loading sub module "fbdevhw"
	Information	[    14.627] (II) LoadModule: "fbdevhw"
	Information	[    14.627] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
	Information	[    14.627] (II) Module fbdevhw: vendor="X.Org Foundation"
	Information	[    14.627] 	compiled for 1.11.3, module version = 0.0.2
	Information	[    14.627] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.627] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
	Information	[    14.628] (II) Loading sub module "vgahw"
	Information	[    14.628] (II) LoadModule: "vgahw"
	Information	[    14.628] (II) Loading /usr/lib/xorg/modules/libvgahw.so
	Information	[    14.628] (II) Module vgahw: vendor="X.Org Foundation"
	Information	[    14.628] 	compiled for 1.11.3, module version = 0.1.0
	Information	[    14.628] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.628] (II) fglrx(0): Creating default Display subsection in Screen section
	Information		"Default Screen" for depth/fbbpp 24/32
	Information	[    14.628] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
	Information	[    14.628] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
	Information	[    14.628] (==) fglrx(0): Default visual is TrueColor
	Information	[    14.628] (==) fglrx(0): RGB weight 888
	Information	[    14.628] (II) fglrx(0): Using 8 bits per RGB 
	Information	[    14.628] (==) fglrx(0): Buffer Tiling is ON
	Information	[    14.628] (II) Loading sub module "fglrxdrm"
	Information	[    14.628] (II) LoadModule: "fglrxdrm"
	Information	[    14.628] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
	Information	[    14.628] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	Information	[    14.628] 	compiled for 1.4.99.906, module version = 8.96.4
	Information	[    14.630] ukiDynamicMajor: found major device number 250
	Information	[    14.630] ukiDynamicMajor: found major device number 250
	Information	[    14.630] ukiOpenByBusid: Searching for BusID PCI:1:5:0
	Information	[    14.630] ukiOpenDevice: node name is /dev/ati/card0
	Information	[    14.630] ukiOpenDevice: open result is 11, (OK)
	Information	[    14.630] ukiOpenByBusid: ukiOpenMinor returns 11
	Information	[    14.630] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
	Information	[    14.630] (**) fglrx(0): NoAccel = NO
	Information	[    14.630] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
	Information	[    14.630] (--) fglrx(0): Chipset: "ATI Radeon HD 4200" (Chipset = 0x9710)
	Information	[    14.630] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x83a2)
	Information	[    14.630] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
	Information	[    14.630] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
	Information	[    14.630] (--) fglrx(0): MMIO registers at 0xfeaf0000
	Information	[    14.630] (--) fglrx(0): I/O port at 0x0000d000
	Information	[    14.630] (==) fglrx(0): ROM-BIOS at 0x000c0000
	Information	[    14.696] (II) fglrx(0): AC Adapter is used
	Information	[    14.702] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
	Information	[    14.704] (II) Loading sub module "vbe"
	Information	[    14.704] (II) LoadModule: "vbe"
	Information	[    14.704] (II) Loading /usr/lib/xorg/modules/libvbe.so
	Information	[    14.704] (II) Module vbe: vendor="X.Org Foundation"
	Information	[    14.704] 	compiled for 1.11.3, module version = 1.1.0
	Information	[    14.704] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.704] (II) fglrx(0): VESA BIOS detected
	Information	[    14.704] (II) fglrx(0): VESA VBE Version 3.0
	Information	[    14.704] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Software Rev: 10.94
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Product: RS880
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
	Information	[    14.711] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
	Information	[    14.711] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
	Information	[    14.711] (II) fglrx(0): PCIE card detected
	Information	[    14.711] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
	Information	[    14.711] (WW) fglrx(0): board is an unknown third party board, chipset is supported
	Information	[    14.720] (II) fglrx(0): Using adapter: 1:5.0.
	Information	[    14.728] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
	Information	[    14.898] (II) fglrx(0): Interrupt handler installed at IRQ 18.
	Information	[    14.898] (II) fglrx(0): RandR 1.2 support is enabled!
	Information	[    14.898] (II) fglrx(0): RandR 1.2 rotation support is enabled!
	Information	[    14.898] (==) fglrx(0): Center Mode is disabled 
	Information	[    14.898] (II) Loading sub module "fb"
	Information	[    14.898] (II) LoadModule: "fb"
	Information	[    14.898] (II) Loading /usr/lib/xorg/modules/libfb.so
	Information	[    14.898] (II) Module fb: vendor="X.Org Foundation"
	Information	[    14.898] 	compiled for 1.11.3, module version = 1.0.0
	Information	[    14.898] 	ABI class: X.Org ANSI C Emulation, version 0.4
	Information	[    14.899] (II) Loading sub module "ddc"
	Information	[    14.899] (II) LoadModule: "ddc"
	Information	[    14.899] (II) Module "ddc" already built-in
	Information	[    15.373] (II) fglrx(0): Finished Initialize PPLIB!
	Information	[    15.376] (II) fglrx(0): Output DFP1 has no monitor section
	Information	[    15.376] (II) fglrx(0): Output CRT1 has no monitor section
	Information	[    15.376] (II) Loading sub module "ddc"
	Information	[    15.376] (II) LoadModule: "ddc"
	Information	[    15.376] (II) Module "ddc" already built-in
	Information	[    15.376] (II) fglrx(0): Connected Display0: DFP1
	Information	[    15.376] (II) fglrx(0): Display0 EDID data ---------------------------
	Information	[    15.376] (II) fglrx(0): Manufacturer: ACR  Model: e4  Serial#: 2474657703
	Information	[    15.376] (II) fglrx(0): Year: 2009  Week: 38
	Information	[    15.376] (II) fglrx(0): EDID Version: 1.3
	Information	[    15.376] (II) fglrx(0): Digital Display Input
	Information	[    15.376] (II) fglrx(0): Max Image Size [cm]: horiz.: 44  vert.: 25
	Information	[    15.376] (II) fglrx(0): Gamma: 2.20
	Information	[    15.376] (II) fglrx(0): DPMS capabilities: StandBy Suspend
	Information	[    15.376] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
	Information	[    15.376] (II) fglrx(0): First detailed timing is preferred mode
	Information	[    15.376] (II) fglrx(0): redX: 0.646 redY: 0.334   greenX: 0.303 greenY: 0.615
	Information	[    15.376] (II) fglrx(0): blueX: 0.146 blueY: 0.066   whiteX: 0.313 whiteY: 0.328
	Information	[    15.376] (II) fglrx(0): Supported established timings:
	Information	[    15.376] (II) fglrx(0): 720x400@70Hz
	Information	[    15.376] (II) fglrx(0): 640x480@60Hz
	Information	[    15.376] (II) fglrx(0): 640x480@67Hz
	Information	[    15.376] (II) fglrx(0): 640x480@72Hz
	Information	[    15.376] (II) fglrx(0): 640x480@75Hz
	Information	[    15.376] (II) fglrx(0): 800x600@56Hz
	Information	[    15.376] (II) fglrx(0): 800x600@60Hz
	Information	[    15.376] (II) fglrx(0): 800x600@72Hz
	Information	[    15.376] (II) fglrx(0): 800x600@75Hz
	Information	[    15.376] (II) fglrx(0): 832x624@75Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@60Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@70Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@75Hz
	Information	[    15.376] (II) fglrx(0): 1280x1024@75Hz
	Information	[    15.377] (II) fglrx(0): 1152x864@75Hz
	Information	[    15.377] (II) fglrx(0): Manufacturer's mask: 0
	Information	[    15.377] (II) fglrx(0): Supported standard timings:
	Information	[    15.377] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	[    15.377] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
	Information	[    15.377] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
	Information	[    15.377] (II) fglrx(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
	Information	[    15.377] (II) fglrx(0): #4: hsize: 1600  vsize 900  refresh: 60  vid: 49321
	Information	[    15.377] (II) fglrx(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
	Information	[    15.377] (II) fglrx(0): Supported detailed timing:
	Information	[    15.377] (II) fglrx(0): clock: 97.8 MHz   Image Size:  443 x 249 mm
	Information	[    15.377] (II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
	Information	[    15.377] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
	Information	[    15.377] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
	Information	[    15.377] (II) fglrx(0): Monitor name: X203H
	Information	[    15.377] (II) fglrx(0): Serial No: LHC0D0228512
	Information	[    15.377] (II) fglrx(0): EDID (in hex):
	Information	[    15.377] (II) fglrx(0): 	00ffffffffffff000472e400a7478093
	Information	[    15.377] (II) fglrx(0): 	26130103802c1978ca6a84a5554d9d25
	Information	[    15.377] (II) fglrx(0): 	115054bfef80714f8140818081c0a9c0
	Information	[    15.377] (II) fglrx(0): 	8100010101012f2640a060841a303020
	Information	[    15.377] (II) fglrx(0): 	3500bbf91000001a000000fd00384c1f
	Information	[    15.377] (II) fglrx(0): 	5311000a202020202020000000fc0058
	Information	[    15.377] (II) fglrx(0): 	323033480a20202020202020000000ff
	Information	[    15.377] (II) fglrx(0): 	004c48433044303232383531320a0075
	Information	[    15.377] (II) fglrx(0): End of Display0 EDID data --------------------
	Information	[    15.377] (II) fglrx(0): Connected Display1: CRT1
	Information	[    15.377] (II) fglrx(0): Display1 EDID data ---------------------------

These entries seemed to be the only relevant entries.

So, to recap:
[COLOR=#000000]I'm running Lubuntu 12.04.2 LXLE, and have been having problems with the system just freezing when the kiddies are playing on Firefox and chromium (mostly disney.com and lego.com), and most recently it froze during minetest (not online).
[/COLOR]
Can anyone help me??

---

### Post by ronniew on 2013-05-14
> **ccsylvia1 said:**
> I realize after reading undecim's sticky post about suggestions on how to get your post answered as quickly as possible, that I've have not included some essential material:

lspci | grep VGA results are:


01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880 [Radeon HD 4200]

and my results of the KSystemlog X.org log are as follows:

	Information	[    14.617] (II) VESA: driver for VESA chipsets: vesa
	Information	[    14.617] (II) FBDEV: driver for framebuffer: fbdev
	Information	[    14.617] (++) using VT number 7
	Information	
	Information	[    14.617] (WW) Falling back to old probe method for fglrx
	Information	[    14.626] (II) Loading PCS database from /etc/ati/amdpcsdb
	Information	[    14.626] (--) Assigning device section with no busID to primary device
	Information	[    14.626] (--) Chipset Supported AMD Graphics Processor (0x9710) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
	Information	[    14.626] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
	Information	[    14.627] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
	Information	[    14.627] (II) AMD Video driver is running on a device belonging to a group targeted for this release
	Information	[    14.627] (II) AMD Video driver is signed
	Information	[    14.627] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
	Information	[    14.627] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
	Information	[    14.627] (II) fglrx(0): pEnt->device->identifier=0xb774e6bf
	Information	[    14.627] (WW) Falling back to old probe method for vesa
	Information	[    14.627] (WW) Falling back to old probe method for fbdev
	Information	[    14.627] (II) Loading sub module "fbdevhw"
	Information	[    14.627] (II) LoadModule: "fbdevhw"
	Information	[    14.627] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
	Information	[    14.627] (II) Module fbdevhw: vendor="X.Org Foundation"
	Information	[    14.627] 	compiled for 1.11.3, module version = 0.0.2
	Information	[    14.627] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.627] (II) fglrx(0): === [xdl_xs111_atiddxPreInit] === begin
	Information	[    14.628] (II) Loading sub module "vgahw"
	Information	[    14.628] (II) LoadModule: "vgahw"
	Information	[    14.628] (II) Loading /usr/lib/xorg/modules/libvgahw.so
	Information	[    14.628] (II) Module vgahw: vendor="X.Org Foundation"
	Information	[    14.628] 	compiled for 1.11.3, module version = 0.1.0
	Information	[    14.628] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.628] (II) fglrx(0): Creating default Display subsection in Screen section
	Information		"Default Screen" for depth/fbbpp 24/32
	Information	[    14.628] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
	Information	[    14.628] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
	Information	[    14.628] (==) fglrx(0): Default visual is TrueColor
	Information	[    14.628] (==) fglrx(0): RGB weight 888
	Information	[    14.628] (II) fglrx(0): Using 8 bits per RGB 
	Information	[    14.628] (==) fglrx(0): Buffer Tiling is ON
	Information	[    14.628] (II) Loading sub module "fglrxdrm"
	Information	[    14.628] (II) LoadModule: "fglrxdrm"
	Information	[    14.628] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
	Information	[    14.628] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	Information	[    14.628] 	compiled for 1.4.99.906, module version = 8.96.4
	Information	[    14.630] ukiDynamicMajor: found major device number 250
	Information	[    14.630] ukiDynamicMajor: found major device number 250
	Information	[    14.630] ukiOpenByBusid: Searching for BusID PCI:1:5:0
	Information	[    14.630] ukiOpenDevice: node name is /dev/ati/card0
	Information	[    14.630] ukiOpenDevice: open result is 11, (OK)
	Information	[    14.630] ukiOpenByBusid: ukiOpenMinor returns 11
	Information	[    14.630] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
	Information	[    14.630] (**) fglrx(0): NoAccel = NO
	Information	[    14.630] (**) fglrx(0): ATI 2D Acceleration Architecture enabled
	Information	[    14.630] (--) fglrx(0): Chipset: "ATI Radeon HD 4200" (Chipset = 0x9710)
	Information	[    14.630] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x83a2)
	Information	[    14.630] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
	Information	[    14.630] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
	Information	[    14.630] (--) fglrx(0): MMIO registers at 0xfeaf0000
	Information	[    14.630] (--) fglrx(0): I/O port at 0x0000d000
	Information	[    14.630] (==) fglrx(0): ROM-BIOS at 0x000c0000
	Information	[    14.696] (II) fglrx(0): AC Adapter is used
	Information	[    14.702] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
	Information	[    14.704] (II) Loading sub module "vbe"
	Information	[    14.704] (II) LoadModule: "vbe"
	Information	[    14.704] (II) Loading /usr/lib/xorg/modules/libvbe.so
	Information	[    14.704] (II) Module vbe: vendor="X.Org Foundation"
	Information	[    14.704] 	compiled for 1.11.3, module version = 1.1.0
	Information	[    14.704] 	ABI class: X.Org Video Driver, version 11.0
	Information	[    14.704] (II) fglrx(0): VESA BIOS detected
	Information	[    14.704] (II) fglrx(0): VESA VBE Version 3.0
	Information	[    14.704] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Software Rev: 10.94
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Product: RS880
	Information	[    14.704] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
	Information	[    14.711] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
	Information	[    14.711] (--) fglrx(0): Video RAM: 262144 kByte, Type: DDR2
	Information	[    14.711] (II) fglrx(0): PCIE card detected
	Information	[    14.711] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
	Information	[    14.711] (WW) fglrx(0): board is an unknown third party board, chipset is supported
	Information	[    14.720] (II) fglrx(0): Using adapter: 1:5.0.
	Information	[    14.728] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x10000000)
	Information	[    14.898] (II) fglrx(0): Interrupt handler installed at IRQ 18.
	Information	[    14.898] (II) fglrx(0): RandR 1.2 support is enabled!
	Information	[    14.898] (II) fglrx(0): RandR 1.2 rotation support is enabled!
	Information	[    14.898] (==) fglrx(0): Center Mode is disabled 
	Information	[    14.898] (II) Loading sub module "fb"
	Information	[    14.898] (II) LoadModule: "fb"
	Information	[    14.898] (II) Loading /usr/lib/xorg/modules/libfb.so
	Information	[    14.898] (II) Module fb: vendor="X.Org Foundation"
	Information	[    14.898] 	compiled for 1.11.3, module version = 1.0.0
	Information	[    14.898] 	ABI class: X.Org ANSI C Emulation, version 0.4
	Information	[    14.899] (II) Loading sub module "ddc"
	Information	[    14.899] (II) LoadModule: "ddc"
	Information	[    14.899] (II) Module "ddc" already built-in
	Information	[    15.373] (II) fglrx(0): Finished Initialize PPLIB!
	Information	[    15.376] (II) fglrx(0): Output DFP1 has no monitor section
	Information	[    15.376] (II) fglrx(0): Output CRT1 has no monitor section
	Information	[    15.376] (II) Loading sub module "ddc"
	Information	[    15.376] (II) LoadModule: "ddc"
	Information	[    15.376] (II) Module "ddc" already built-in
	Information	[    15.376] (II) fglrx(0): Connected Display0: DFP1
	Information	[    15.376] (II) fglrx(0): Display0 EDID data ---------------------------
	Information	[    15.376] (II) fglrx(0): Manufacturer: ACR  Model: e4  Serial#: 2474657703
	Information	[    15.376] (II) fglrx(0): Year: 2009  Week: 38
	Information	[    15.376] (II) fglrx(0): EDID Version: 1.3
	Information	[    15.376] (II) fglrx(0): Digital Display Input
	Information	[    15.376] (II) fglrx(0): Max Image Size [cm]: horiz.: 44  vert.: 25
	Information	[    15.376] (II) fglrx(0): Gamma: 2.20
	Information	[    15.376] (II) fglrx(0): DPMS capabilities: StandBy Suspend
	Information	[    15.376] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
	Information	[    15.376] (II) fglrx(0): First detailed timing is preferred mode
	Information	[    15.376] (II) fglrx(0): redX: 0.646 redY: 0.334   greenX: 0.303 greenY: 0.615
	Information	[    15.376] (II) fglrx(0): blueX: 0.146 blueY: 0.066   whiteX: 0.313 whiteY: 0.328
	Information	[    15.376] (II) fglrx(0): Supported established timings:
	Information	[    15.376] (II) fglrx(0): 720x400@70Hz
	Information	[    15.376] (II) fglrx(0): 640x480@60Hz
	Information	[    15.376] (II) fglrx(0): 640x480@67Hz
	Information	[    15.376] (II) fglrx(0): 640x480@72Hz
	Information	[    15.376] (II) fglrx(0): 640x480@75Hz
	Information	[    15.376] (II) fglrx(0): 800x600@56Hz
	Information	[    15.376] (II) fglrx(0): 800x600@60Hz
	Information	[    15.376] (II) fglrx(0): 800x600@72Hz
	Information	[    15.376] (II) fglrx(0): 800x600@75Hz
	Information	[    15.376] (II) fglrx(0): 832x624@75Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@60Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@70Hz
	Information	[    15.376] (II) fglrx(0): 1024x768@75Hz
	Information	[    15.376] (II) fglrx(0): 1280x1024@75Hz
	Information	[    15.377] (II) fglrx(0): 1152x864@75Hz
	Information	[    15.377] (II) fglrx(0): Manufacturer's mask: 0
	Information	[    15.377] (II) fglrx(0): Supported standard timings:
	Information	[    15.377] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
	Information	[    15.377] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
	Information	[    15.377] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
	Information	[    15.377] (II) fglrx(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
	Information	[    15.377] (II) fglrx(0): #4: hsize: 1600  vsize 900  refresh: 60  vid: 49321
	Information	[    15.377] (II) fglrx(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
	Information	[    15.377] (II) fglrx(0): Supported detailed timing:
	Information	[    15.377] (II) fglrx(0): clock: 97.8 MHz   Image Size:  443 x 249 mm
	Information	[    15.377] (II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
	Information	[    15.377] (II) fglrx(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
	Information	[    15.377] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
	Information	[    15.377] (II) fglrx(0): Monitor name: X203H
	Information	[    15.377] (II) fglrx(0): Serial No: LHC0D0228512
	Information	[    15.377] (II) fglrx(0): EDID (in hex):
	Information	[    15.377] (II) fglrx(0): 	00ffffffffffff000472e400a7478093
	Information	[    15.377] (II) fglrx(0): 	26130103802c1978ca6a84a5554d9d25
	Information	[    15.377] (II) fglrx(0): 	115054bfef80714f8140818081c0a9c0
	Information	[    15.377] (II) fglrx(0): 	8100010101012f2640a060841a303020
	Information	[    15.377] (II) fglrx(0): 	3500bbf91000001a000000fd00384c1f
	Information	[    15.377] (II) fglrx(0): 	5311000a202020202020000000fc0058
	Information	[    15.377] (II) fglrx(0): 	323033480a20202020202020000000ff
	Information	[    15.377] (II) fglrx(0): 	004c48433044303232383531320a0075
	Information	[    15.377] (II) fglrx(0): End of Display0 EDID data --------------------
	Information	[    15.377] (II) fglrx(0): Connected Display1: CRT1
	Information	[    15.377] (II) fglrx(0): Display1 EDID data ---------------------------

These entries seemed to be the only relevant entries.

So, to recap:
[COLOR=#000000]I'm running Lubuntu 12.04.2 LXLE, and have been having problems with the system just freezing when the kiddies are playing on Firefox and chromium (mostly disney.com and lego.com), and most recently it froze during minetest (not online).
[/COLOR]
Can anyone help me??

Its probably not flash but java, if you switched to java 7 including icedtea7 it would probably fix the issue. I had to address this the other day when it came to frostwire, and since many games site use java as well as flash, i would be that has something to do with it.

---

### Post by ccsylvia1 on 2013-06-08
Okay....

So I fresh installed Ubuntu 13.04 on my home partition, and within a day, had the same system freeze problem.  One difference was that it presented as a "kernel panic" and it reverted to text mode.

I mentioned this to a friend casually, and he told me to check the heat sink on my chip to see about an overheat problem.

Lo and behold, the heat sink was gunked with ~5 years worth of dust.  Cleaned it out, and voila, no more problems.

Thank you all for your help.

---


---
title: "Stuck at &quot;Checking Battery State&quot;"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-09-19
After doing some updates this morning, I can no longer boot - it gets stuck at the ol' "Checking Battery State" point. Can't boot into Recovery mode either, same thing.

However, at that point, I can get to a terminal with ctl-alt-Fn, so I re-installed nvidia-current, but no joy. I did notice that among the updates were a couple of xorg items, but nothing was removed. Guess I'll wait a few hours and try updating

---

### Post by ventrical on 2011-09-19
I had this problem many times. One time I used:

sudo apt-get install fglrx


 and I got my Unity window and LightDM back.

Now .. I just did an update a day or so ago and I only get nautalis when I try to boot in to Ubuntu 3D, but Gnome Shell and Ubuntu 2D work great. I can't figure it out.

---

### Post by sgage on 2011-09-19
> **ventrical said:**
> I had this problem many times. One time I used:

sudo apt-get install fglrx


 and I got my Unity window and LightDM back.

Now .. I just did an update a day or so ago and I only get nautalis when I try to boot in to Ubuntu 3D, but Gnome Shell and Ubuntu 2D work great. I can't figure it out.

It's wonderful, isn't it?  :KS

---

### Post by sgage on 2011-09-19
Update:

I removed the nvidia-current drivers and tried with nouveau. Still no joy.

I reinstalled lightdm. Nope.

I'm out of ideas.

---

### Post by lucazade on 2011-09-19
sgage paste /var/log/Xorg.0.log

---

### Post by sgage on 2011-09-19
> **lucazade said:**
> sgage paste /var/log/Xorg.0.log

Here it is...

```
[    18.298] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.298] X Protocol Version 11, Revision 0
[    18.298] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    18.298] Current Operating System: Linux presa 3.0.0-11-generic-pae #18-Ubuntu SMP Wed Sep 14 01:24:09 UTC 2011 i686
[    18.298] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-11-generic-pae root=UUID=9c9d5f1c-ee12-4081-bba0-47fce68532a7 ro
[    18.298] Build Date: 19 September 2011  06:58:01AM
[    18.298] xorg-server 2:1.10.4-1ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    18.298] Current version of pixman: 0.22.2
[    18.298] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.298] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.298] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 19 08:54:52 2011
[    18.301] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.301] (==) No Layout section.  Using the first Screen section.
[    18.301] (==) No screen section available. Using defaults.
[    18.301] (**) |-->Screen "Default Screen Section" (0)
[    18.301] (**) |   |-->Monitor "<default monitor>"
[    18.301] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    18.301] (==) Automatically adding devices
[    18.301] (==) Automatically enabling devices
[    18.302] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.302] 	Entry deleted from font path.
[    18.302] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.302] 	Entry deleted from font path.
[    18.302] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.302] 	Entry deleted from font path.
[    18.302] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.302] 	Entry deleted from font path.
[    18.302] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.302] 	Entry deleted from font path.
[    18.302] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.302] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.302] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.302] (II) Loader magic: 0x823ada0
[    18.302] (II) Module ABI versions:
[    18.302] 	X.Org ANSI C Emulation: 0.4
[    18.302] 	X.Org Video Driver: 10.0
[    18.302] 	X.Org XInput driver : 12.3
[    18.302] 	X.Org Server Extension : 5.0
[    18.303] (--) PCI:*(0:1:0:0) 10de:0421:1043:8264 rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072
[    18.303] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.303] (II) LoadModule: "extmod"
[    18.316] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.316] (II) Module extmod: vendor="X.Org Foundation"
[    18.316] 	compiled for 1.10.4, module version = 1.0.0
[    18.316] 	Module class: X.Org Server Extension
[    18.316] 	ABI class: X.Org Server Extension, version 5.0
[    18.316] (II) Loading extension MIT-SCREEN-SAVER
[    18.316] (II) Loading extension XFree86-VidModeExtension
[    18.316] (II) Loading extension XFree86-DGA
[    18.316] (II) Loading extension DPMS
[    18.316] (II) Loading extension XVideo
[    18.316] (II) Loading extension XVideo-MotionCompensation
[    18.316] (II) Loading extension X-Resource
[    18.316] (II) LoadModule: "dbe"
[    18.317] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.317] (II) Module dbe: vendor="X.Org Foundation"
[    18.317] 	compiled for 1.10.4, module version = 1.0.0
[    18.317] 	Module class: X.Org Server Extension
[    18.317] 	ABI class: X.Org Server Extension, version 5.0
[    18.317] (II) Loading extension DOUBLE-BUFFER
[    18.317] (II) LoadModule: "glx"
[    18.317] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    18.349] (II) Module glx: vendor="NVIDIA Corporation"
[    18.349] 	compiled for 4.0.2, module version = 1.0.0
[    18.349] 	Module class: X.Org Server Extension
[    18.349] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:14:51 PDT 2011
[    18.349] (II) Loading extension GLX
[    18.349] (II) LoadModule: "record"
[    18.349] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.349] (II) Module record: vendor="X.Org Foundation"
[    18.349] 	compiled for 1.10.4, module version = 1.13.0
[    18.349] 	Module class: X.Org Server Extension
[    18.349] 	ABI class: X.Org Server Extension, version 5.0
[    18.349] (II) Loading extension RECORD
[    18.349] (II) LoadModule: "dri"
[    18.350] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.350] (II) Module dri: vendor="X.Org Foundation"
[    18.350] 	compiled for 1.10.4, module version = 1.0.0
[    18.350] 	ABI class: X.Org Server Extension, version 5.0
[    18.350] (II) Loading extension XFree86-DRI
[    18.350] (II) LoadModule: "dri2"
[    18.350] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.350] (II) Module dri2: vendor="X.Org Foundation"
[    18.350] 	compiled for 1.10.4, module version = 1.2.0
[    18.350] 	ABI class: X.Org Server Extension, version 5.0
[    18.351] (II) Loading extension DRI2
[    18.351] (==) Matched nvidia as autoconfigured driver 0
[    18.351] (==) Matched nouveau as autoconfigured driver 1
[    18.351] (==) Matched nv as autoconfigured driver 2
[    18.351] (==) Matched vesa as autoconfigured driver 3
[    18.351] (==) Matched fbdev as autoconfigured driver 4
[    18.351] (==) Assigned the driver to the xf86ConfigLayout
[    18.351] (II) LoadModule: "nvidia"
[    18.351] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    18.351] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.351] 	compiled for 4.0.2, module version = 1.0.0
[    18.351] 	Module class: X.Org Video Driver
[    18.355] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    18.356] (EE) NVIDIA:     system's kernel log for additional error messages.
[    18.356] (II) UnloadModule: "nvidia"
[    18.356] (II) Unloading nvidia
[    18.356] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    18.356] (II) LoadModule: "nouveau"
[    18.356] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    18.356] (II) Module nouveau: vendor="X.Org Foundation"
[    18.356] 	compiled for 1.10.1, module version = 0.0.16
[    18.356] 	Module class: X.Org Video Driver
[    18.356] 	ABI class: X.Org Video Driver, version 10.0
[    18.356] (II) LoadModule: "nv"
[    18.357] (WW) Warning, couldn't open module nv
[    18.357] (II) UnloadModule: "nv"
[    18.357] (II) Unloading nv
[    18.357] (EE) Failed to load module "nv" (module does not exist, 0)
[    18.357] (II) LoadModule: "vesa"
[    18.357] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.358] (II) Module vesa: vendor="X.Org Foundation"
[    18.358] 	compiled for 1.10.2, module version = 2.3.0
[    18.358] 	Module class: X.Org Video Driver
[    18.358] 	ABI class: X.Org Video Driver, version 10.0
[    18.358] (II) LoadModule: "fbdev"
[    18.362] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.362] (II) Module fbdev: vendor="X.Org Foundation"
[    18.362] 	compiled for 1.10.0, module version = 0.4.2
[    18.362] 	ABI class: X.Org Video Driver, version 10.0
[    18.362] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    18.362] (II) NOUVEAU driver for NVIDIA chipset families :
[    18.362] 	RIVA TNT        (NV04)
[    18.362] 	RIVA TNT2       (NV05)
[    18.362] 	GeForce 256     (NV10)
[    18.362] 	GeForce 2       (NV11, NV15)
[    18.362] 	GeForce 4MX     (NV17, NV18)
[    18.362] 	GeForce 3       (NV20)
[    18.362] 	GeForce 4Ti     (NV25, NV28)
[    18.363] 	GeForce FX      (NV3x)
[    18.363] 	GeForce 6       (NV4x)
[    18.363] 	GeForce 7       (G7x)
[    18.363] 	GeForce 8       (G8x)
[    18.363] 	GeForce GTX 200 (NVA0)
[    18.363] 	GeForce GTX 400 (NVC0)
[    18.363] (II) VESA: driver for VESA chipsets: vesa
[    18.363] (II) FBDEV: driver for framebuffer: fbdev
[    18.363] (++) using VT number 7

[    18.363] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    18.363] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    18.363] drmOpenDevice: node name is /dev/dri/card0
[    18.363] drmOpenDevice: open result is 11, (OK)
[    18.363] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    18.363] drmOpenDevice: node name is /dev/dri/card0
[    18.363] drmOpenDevice: open result is 11, (OK)
[    18.363] drmOpenByBusid: drmOpenMinor returns 11
[    18.363] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    18.363] (II) [drm] nouveau interface version: 0.0.16
[    18.363] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    18.363] (WW) Falling back to old probe method for vesa
[    18.363] (WW) Falling back to old probe method for fbdev
[    18.363] (II) Loading sub module "fbdevhw"
[    18.363] (II) LoadModule: "fbdevhw"
[    18.366] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.366] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.366] 	compiled for 1.10.4, module version = 0.0.2
[    18.366] 	ABI class: X.Org Video Driver, version 10.0
[    18.366] (II) Loading sub module "dri"
[    18.367] (II) LoadModule: "dri"
[    18.367] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.367] (II) Module dri: vendor="X.Org Foundation"
[    18.367] 	compiled for 1.10.4, module version = 1.0.0
[    18.367] 	ABI class: X.Org Server Extension, version 5.0
[    18.367] (II) NOUVEAU(0): Loaded DRI module
[    18.367] drmOpenDevice: node name is /dev/dri/card0
[    18.367] drmOpenDevice: open result is 12, (OK)
[    18.367] drmOpenDevice: node name is /dev/dri/card0
[    18.367] drmOpenDevice: open result is 12, (OK)
[    18.367] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    18.367] drmOpenDevice: node name is /dev/dri/card0
[    18.367] drmOpenDevice: open result is 12, (OK)
[    18.367] drmOpenByBusid: drmOpenMinor returns 12
[    18.367] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    18.367] (II) [drm] DRM interface version 1.4
[    18.367] (II) [drm] DRM open master succeeded.
[    18.367] (--) NOUVEAU(0): Chipset: "NVIDIA NV86"
[    18.367] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.367] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    18.367] (==) NOUVEAU(0): RGB weight 888
[    18.367] (==) NOUVEAU(0): Default visual is TrueColor
[    18.376] (==) NOUVEAU(0): Using HW cursor
[    18.376] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    18.376] (==) NOUVEAU(0): Page flipping enabled
[    18.486] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    18.590] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    18.697] (II) NOUVEAU(0): EDID for output DVI-I-1
[    18.801] (II) NOUVEAU(0): EDID for output VGA-1
[    18.801] (II) NOUVEAU(0): Manufacturer: ACR  Model: 12d  Serial#: 56660038
[    18.801] (II) NOUVEAU(0): Year: 2010  Week: 36
[    18.801] (II) NOUVEAU(0): EDID Version: 1.3
[    18.801] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    18.801] (II) NOUVEAU(0): Sync:  Separate  Composite
[    18.801] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 27
[    18.801] (II) NOUVEAU(0): Gamma: 2.20
[    18.801] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    18.801] (II) NOUVEAU(0): First detailed timing is preferred mode
[    18.801] (II) NOUVEAU(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
[    18.801] (II) NOUVEAU(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    18.801] (II) NOUVEAU(0): Supported established timings:
[    18.801] (II) NOUVEAU(0): 720x400@70Hz
[    18.801] (II) NOUVEAU(0): 640x480@60Hz
[    18.801] (II) NOUVEAU(0): 640x480@67Hz
[    18.801] (II) NOUVEAU(0): 640x480@72Hz
[    18.801] (II) NOUVEAU(0): 640x480@75Hz
[    18.801] (II) NOUVEAU(0): 800x600@56Hz
[    18.801] (II) NOUVEAU(0): 800x600@60Hz
[    18.801] (II) NOUVEAU(0): 800x600@72Hz
[    18.801] (II) NOUVEAU(0): 800x600@75Hz
[    18.801] (II) NOUVEAU(0): 832x624@75Hz
[    18.801] (II) NOUVEAU(0): 1024x768@60Hz
[    18.801] (II) NOUVEAU(0): 1024x768@70Hz
[    18.801] (II) NOUVEAU(0): 1024x768@75Hz
[    18.801] (II) NOUVEAU(0): 1280x1024@75Hz
[    18.801] (II) NOUVEAU(0): 1152x864@75Hz
[    18.801] (II) NOUVEAU(0): Manufacturer's mask: 0
[    18.801] (II) NOUVEAU(0): Supported standard timings:
[    18.801] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    18.801] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    18.801] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.801] (II) NOUVEAU(0): Supported detailed timing:
[    18.801] (II) NOUVEAU(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
[    18.801] (II) NOUVEAU(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
[    18.801] (II) NOUVEAU(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
[    18.801] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 83 kHz, PixClock max 145 MHz
[    18.801] (II) NOUVEAU(0): Monitor name: Acer V173
[    18.801] (II) NOUVEAU(0): Serial No: LKM0W0904340
[    18.801] (II) NOUVEAU(0): EDID (in hex):
[    18.801] (II) NOUVEAU(0): 	00ffffffffffff0004722d0146906003
[    18.801] (II) NOUVEAU(0): 	241401036c221b78ea3d85a6564a9a24
[    18.801] (II) NOUVEAU(0): 	125054bfef80714f8140818001010101
[    18.801] (II) NOUVEAU(0): 	010101010101302a009851002a403070
[    18.801] (II) NOUVEAU(0): 	1300520e1100001e000000fd00384b1f
[    18.801] (II) NOUVEAU(0): 	530e000a202020202020000000fc0041
[    18.801] (II) NOUVEAU(0): 	63657220563137330a202020000000ff
[    18.801] (II) NOUVEAU(0): 	004c4b4d3057303930343334300a0029
[    18.801] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    18.801] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.801] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.802] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.802] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[    18.802] (II) NOUVEAU(0): Output VGA-1 connected
[    18.802] (II) NOUVEAU(0): Using exact sizes for initial modes
[    18.802] (II) NOUVEAU(0): Output VGA-1 using initial mode 1280x1024
[    18.802] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.802] (--) NOUVEAU(0): Virtual size is 1280x1024 (pitch 0)
[    18.802] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[    18.802] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    18.802] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    18.802] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.802] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    18.802] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.802] (==) NOUVEAU(0): DPI set to (96, 96)
[    18.802] (II) Loading sub module "fb"
[    18.802] (II) LoadModule: "fb"
[    18.803] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.803] (II) Module fb: vendor="X.Org Foundation"
[    18.803] 	compiled for 1.10.4, module version = 1.0.0
[    18.803] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.803] (II) Loading sub module "exa"
[    18.803] (II) LoadModule: "exa"
[    18.803] (II) Loading /usr/lib/xorg/modules/libexa.so
[    18.981] (II) Module exa: vendor="X.Org Foundation"
[    18.988] 	compiled for 1.10.4, module version = 2.5.0
[    18.988] 	ABI class: X.Org Video Driver, version 10.0
[    18.988] (II) Loading sub module "shadowfb"
[    18.988] (II) LoadModule: "shadowfb"
[    18.988] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    19.031] (II) Module shadowfb: vendor="X.Org Foundation"
[    19.031] 	compiled for 1.10.4, module version = 1.0.0
[    19.031] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.031] (II) UnloadModule: "vesa"
[    19.031] (II) Unloading vesa
[    19.031] (II) UnloadModule: "fbdev"
[    19.031] (II) Unloading fbdev
[    19.031] (II) UnloadModule: "fbdevhw"
[    19.031] (II) Unloading fbdevhw
[    19.031] (--) Depth 24 pixmap format is 32 bpp
[    19.037] (II) NOUVEAU(0): Opened GPU channel 2
[    19.037] (II) NOUVEAU(0): [DRI2] Setup complete
[    19.037] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    19.037] (II) NOUVEAU(0): GART: 512MiB available
[    19.040] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    19.040] (II) EXA(0): Driver allocated offscreen pixmaps
[    19.040] (II) EXA(0): Driver registered support for the following operations:
[    19.040] (II)         Solid
[    19.040] (II)         Copy
[    19.040] (II)         Composite (RENDER acceleration)
[    19.040] (II)         UploadToScreen
[    19.040] (II)         DownloadFromScreen
[    19.040] (==) NOUVEAU(0): Backing store disabled
[    19.040] (==) NOUVEAU(0): Silken mouse enabled
[    19.060] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    19.061] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    19.061] (==) NOUVEAU(0): DPMS enabled
[    19.061] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.061] (--) RandR disabled
[    19.061] (II) Initializing built-in extension Generic Event Extension
[    19.061] (II) Initializing built-in extension SHAPE
[    19.061] (II) Initializing built-in extension MIT-SHM
[    19.061] (II) Initializing built-in extension XInputExtension
[    19.061] (II) Initializing built-in extension XTEST
[    19.061] (II) Initializing built-in extension BIG-REQUESTS
[    19.061] (II) Initializing built-in extension SYNC
[    19.061] (II) Initializing built-in extension XKEYBOARD
[    19.061] (II) Initializing built-in extension XC-MISC
[    19.061] (II) Initializing built-in extension SECURITY
[    19.061] (II) Initializing built-in extension XINERAMA
[    19.061] (II) Initializing built-in extension XFIXES
[    19.061] (II) Initializing built-in extension RENDER
[    19.061] (II) Initializing built-in extension RANDR
[    19.061] (II) Initializing built-in extension COMPOSITE
[    19.061] (II) Initializing built-in extension DAMAGE
[    19.061] (II) Initializing built-in extension GESTURE
[    19.065] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    19.076] (II) NOUVEAU(0): NVEnterVT is called.
[    19.090] (II) NOUVEAU(0): Setting screen physical size to 338 x 270
[    19.092] resize called 1280 1024
[    19.104] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.113] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    19.113] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.113] (II) LoadModule: "evdev"
[    19.114] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.115] (II) Module evdev: vendor="X.Org Foundation"
[    19.115] 	compiled for 1.10.2, module version = 2.6.0
[    19.115] 	Module class: X.Org XInput Driver
[    19.115] 	ABI class: X.Org XInput driver, version 12.3
[    19.115] (II) Using input driver 'evdev' for 'Power Button'
[    19.115] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.115] (**) Power Button: always reports core events
[    19.115] (**) Power Button: Device: "/dev/input/event1"
[    19.115] (--) Power Button: Found keys
[    19.115] (II) Power Button: Configuring as keyboard
[    19.115] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    19.115] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.115] (**) Option "xkb_rules" "evdev"
[    19.115] (**) Option "xkb_model" "pc105"
[    19.115] (**) Option "xkb_layout" "us"
[    19.118] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.118] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.118] (II) Using input driver 'evdev' for 'Power Button'
[    19.118] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.118] (**) Power Button: always reports core events
[    19.118] (**) Power Button: Device: "/dev/input/event0"
[    19.118] (--) Power Button: Found keys
[    19.118] (II) Power Button: Configuring as keyboard
[    19.118] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    19.118] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    19.118] (**) Option "xkb_rules" "evdev"
[    19.118] (**) Option "xkb_model" "pc105"
[    19.118] (**) Option "xkb_layout" "us"
[    19.120] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event3)
[    19.120] (II) No input driver/identifier specified (ignoring)
[    19.126] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    19.126] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.126] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.126] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.126] (**) AT Translated Set 2 keyboard: always reports core events
[    19.126] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    19.126] (--) AT Translated Set 2 keyboard: Found keys
[    19.126] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.126] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    19.126] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.126] (**) Option "xkb_rules" "evdev"
[    19.126] (**) Option "xkb_model" "pc105"
[    19.127] (**) Option "xkb_layout" "us"
[    19.127] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event4)
[    19.127] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    19.127] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    19.127] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.127] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    19.127] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event4"
[    19.127] (--) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    19.127] (--) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    19.127] (--) ImPS/2 Generic Wheel Mouse: Found relative axes
[    19.127] (--) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    19.127] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    19.127] (II) ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    19.127] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    19.127] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    19.127] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    19.127] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    19.128] (II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    19.128] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    19.128] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    19.128] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    19.128] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    19.128] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    19.128] (II) No input driver/identifier specified (ignoring)
[    19.196] (II) Power Button: Close
[    19.196] (II) UnloadModule: "evdev"
[    19.196] (II) Unloading evdev
[    19.204] (II) Power Button: Close
[    19.204] (II) UnloadModule: "evdev"
[    19.204] (II) Unloading evdev
[    19.204] (II) AT Translated Set 2 keyboard: Close
[    19.204] (II) UnloadModule: "evdev"
[    19.204] (II) Unloading evdev
[    19.204] (II) ImPS/2 Generic Wheel Mouse: Close
[    19.204] (II) UnloadModule: "evdev"
[    19.204] (II) Unloading evdev
[    19.204] (II) NOUVEAU(0): NVLeaveVT is called.
[    19.204] (II) NOUVEAU(0): Closed GPU channel 2
[    19.225]  ddxSigGiveUp: Closing log

```

---

### Post by lucazade on 2011-09-19
it looks like nvidia drivers are not loaded and the system fallback to nouveau.
are the proprietary nvidia drivers properly installed?

```
[    18.351] (II) LoadModule: "nvidia"
[    18.351] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    18.351] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.351] 	compiled for 4.0.2, module version = 1.0.0
[    18.351] 	Module class: X.Org Video Driver
[    18.355] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    18.356] (EE) NVIDIA:     system's kernel log for additional error messages.
[    18.356] (II) UnloadModule: "nvidia"
[    18.356] (II) Unloading nvidia
[    18.356] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    18.356] (II) LoadModule: "nouveau"
[    18.356] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
..
```

---

### Post by sgage on 2011-09-19
> **lucazade said:**
> it looks like nvidia drivers are not loaded and the system fallback to nouveau.
are the proprietary nvidia drivers properly installed?

```
[    18.351] (II) LoadModule: "nvidia"
[    18.351] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    18.351] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.351] 	compiled for 4.0.2, module version = 1.0.0
[    18.351] 	Module class: X.Org Video Driver
[    18.355] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    18.356] (EE) NVIDIA:     system's kernel log for additional error messages.
[    18.356] (II) UnloadModule: "nvidia"
[    18.356] (II) Unloading nvidia
[    18.356] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    18.356] (II) LoadModule: "nouveau"
[    18.356] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
..
```

No, as mentioned above, I removed the nividia-current drivers in the course of troubleshooting. I don't know why it was trying to load nvidia drivers - there is no xorg.conf telling it to do so. 

What should I try next? I would like to avoid reinstalling if I can (downloading today's daily as I type).  :KS

---

### Post by lucazade on 2011-09-19
> **sgage said:**
> No, as mentioned above, I removed the nividia-current drivers in the course of troubleshooting. I don't know why it was trying to load nvidia drivers - there is no xorg.conf telling it to do so. 

What should I try next? I would like to avoid reinstalling if I can (downloading today's daily as I type).  :KS

ops.. I have missed it..
then look in /usr/share/X11/xorg.conf.d/    because new xorg.conf are stored in this dir in the latest ubuntu release, no more in /etc/X11/xorg.
if there is a XX-nvidia or similiar purge it.

---

### Post by ventrical on 2011-09-19
> **sgage said:**
> It's wonderful, isn't it?  :KS

Oh Joy !! Oh rapture !:)

---

### Post by ventrical on 2011-09-19
no xxnvidia here.

---

### Post by sgage on 2011-09-19
> **ventrical said:**
> no xxnvidia here.

I reinstalled nvidia-current, and no go.

After I reinstalled, I checked out /usr/share/X11/xorg.conf.d and there was no XXnvidia...

---

### Post by ventrical on 2011-09-19
> **sgage said:**
> I reinstalled nvidia-current, and no go.

After I reinstalled, I checked out /usr/share/X11/xorg.conf.d and there was no XXnvidia...
  

It was working just beautiful .. then I read somthing about 'not to update'  and so I checked but did not see what was listed in the other forum. I did the updates in good faith ... and now no Unity 3D.

Note... I have  two vewrsions of nvidia when I run the gtk-jockey. One is the binary driver. The other is the accelerator. mabey I should try the other driver.

---

### Post by sgage on 2011-09-19
> **ventrical said:**
> It was working just beautiful .. then I read somthing about 'not to update'  and so I checked but did not see what was listed in the other forum. I did the updates in good faith ... and now no Unity 3D.

Note... I have  two vewrsions of nvidia when I run the gtk-jockey. One is the binary driver. The other is the accelerator. mabey I should try the other driver.

I'm fairly careful about updates, but there since there was nothing that was being removed, I went ahead and did it. I suspect the xorg stuff, but who knows. I'm hoping that in time it will get fixed, but if not, I have no problem reinstalling.

I stay well backed-up :KS

---

### Post by ventrical on 2011-09-19
Until I get Unity 3D working I am going to use the following wallpaper to remind me that "Ocelot" is still just a kitty.!

---

### Post by ventrical on 2011-09-19
> **sgage said:**
> I'm fairly careful about updates, but there since there was nothing that was being removed, I went ahead and did it. I suspect the xorg stuff, but who knows. I'm hoping that in time it will get fixed, but if not, I have no problem reinstalling.

I stay well backed-up :KS


 I think I'll ride the storm out. Beta 2 should be ready soon anyways.

---

### Post by sgage on 2011-09-19
> **ventrical said:**
> Until I get Unity 3D working I am going to use the following wallpaper to remind me that "Ocelot" is still just a kitty.!

That's a beauty! I'm going to see if there are any more updates yet that might help. If not, I think I'll just reinstall - it's about that time anyway.

---

### Post by ventrical on 2011-09-19
I  have done about 5 fresh installs on this machine so far !!

  I tired once to encrypt the home folder - didn't work. 

And I know there is a way to make a seperate parition for home.!! How do I go about proceeding in that direction? I have been at this for over a year now and I have been letting some things slide by.

---

### Post by cariboo on 2011-09-19
@ventrical, you need to choose **Something Else** when you get to the partitioning section, and setup a /home partition manually. I usually set / to 10GiB, 2GiB for swap and the rest of the disk for /home.

---

### Post by ventrical on 2011-09-19
> **cariboo907 said:**
> @ventrical, you need to choose **Something Else** when you get to the partitioning section, and setup a /home partition manually. I usually set / to 10GiB, 2GiB for swap and the rest of the disk for /home.



Thanks Caribou.

 I need some extra help here. I just re-installed Oneiric in a new parition. I had some big probs but I finally got the install done. The install routine initially rejected >installing selected software< so I had to install the kernel manually.

 Now , i am right back where I should be, with Unity 3D but when I go:

sudo apt-get install synaptic

 It says it cannot find synaptic.

 I think I typed in somthing wrong with the code.

---

### Post by sgage on 2011-09-19
Problem solved! :D

I reinstalled. I think I had my system so wrapped around itself that it wouldn't be helpful to myself or anyone else to mess with it any more.

---

### Post by ventrical on 2011-09-19
I fresh installed too but can't seem to be able to install synaptic.

---


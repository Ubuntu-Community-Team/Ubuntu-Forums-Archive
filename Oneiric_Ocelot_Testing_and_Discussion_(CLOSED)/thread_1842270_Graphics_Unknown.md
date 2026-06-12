---
title: "Graphics Unknown"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by suxenexus on 2011-09-11
Hi guys! My GM965 graphics can't be detected on Oneiric.  Is this a recurring problem?  I'm testing the 64-bit version atm.  Another thing, my wifi (BCM4311 802.11a/b/g) is not working.  I tried installing the drivers using the additional drivers app to no avail.  The wifi isn't working properly on Natty too.  Help! :(

[IMG]https://lh5.googleusercontent.com/-rSi8zy5JGKA/TmxcHngOsjI/AAAAAAAAAKw/uCVZclTSDj0/Screenshot%25252520at%252525202011-09-11%2525252014%2525253A57%2525253A41.png[/IMG]

---

### Post by 3rdalbum on 2011-09-11
> **suxenexus said:**
> Hi guys! My GM965 graphics can't be detected on Oneiric.

The shadow around the window in your screenshot suggests that it has been detected and that Compiz/Unity 3D is running, which means that the correct driver is being used. I don't know why that program can't tell what driver is in use, but that's not so important. See if there's a bug report about it, and if not then file one?

[/QUOTE]Another thing, my wifi (BCM4311 802.11a/b/g) is not working.  I tried installing the drivers using the additional drivers app to no avail.[/QUOTE]

Please describe exactly what happens; do the drivers install? Does the Additional Drivers program say afterwards that they are in use? Does Network Manager show any wireless networks? Does dmesg show any error messages regarding the wireless? (wlan).

---

### Post by lucazade on 2011-09-11
shadow may be due to metacity-compositor and this works also with generic vesa drivers.
post /var/log/Xorg.0.log to see what's happening

---

### Post by suxenexus on 2011-09-15
Here it is :)

```
[    25.545] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    25.545] X Protocol Version 11, Revision 0
[    25.545] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    25.545] Current Operating System: Linux jp-Inspiron-1420 3.0.0-11-generic #17-Ubuntu SMP Fri Sep 9 17:48:40 UTC 2011 x86_64
[    25.545] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-11-generic root=UUID=9ac17751-ad78-4de1-835c-4d25dce04fb1 ro quiet splash vt.handoff=7
[    25.545] Build Date: 09 September 2011  11:21:54AM
[    25.545] xorg-server 2:1.10.4-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    25.545] Current version of pixman: 0.22.2
[    25.545] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    25.545] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.545] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 16 07:09:10 2011
[    25.620] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.733] (==) No Layout section.  Using the first Screen section.
[    25.733] (==) No screen section available. Using defaults.
[    25.733] (**) |-->Screen "Default Screen Section" (0)
[    25.733] (**) |   |-->Monitor "<default monitor>"
[    25.733] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    25.733] (==) Automatically adding devices
[    25.733] (==) Automatically enabling devices
[    25.775] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.804] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    25.804] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.804] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.804] (II) Loader magic: 0x7e0220
[    25.804] (II) Module ABI versions:
[    25.804] 	X.Org ANSI C Emulation: 0.4
[    25.804] 	X.Org Video Driver: 10.0
[    25.804] 	X.Org XInput driver : 12.3
[    25.804] 	X.Org Server Extension : 5.0
[    25.805] (--) PCI:*(0:0:2:0) 8086:2a02:1028:01f3 rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[    25.805] (--) PCI: (0:0:2:1) 8086:2a03:1028:01f3 rev 12, Mem @ 0xfeb00000/1048576
[    25.805] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.805] (II) LoadModule: "extmod"
[    25.874] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.900] (II) Module extmod: vendor="X.Org Foundation"
[    25.900] 	compiled for 1.10.4, module version = 1.0.0
[    25.900] 	Module class: X.Org Server Extension
[    25.900] 	ABI class: X.Org Server Extension, version 5.0
[    25.900] (II) Loading extension MIT-SCREEN-SAVER
[    25.900] (II) Loading extension XFree86-VidModeExtension
[    25.900] (II) Loading extension XFree86-DGA
[    25.900] (II) Loading extension DPMS
[    25.900] (II) Loading extension XVideo
[    25.900] (II) Loading extension XVideo-MotionCompensation
[    25.900] (II) Loading extension X-Resource
[    25.900] (II) LoadModule: "dbe"
[    25.901] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.914] (II) Module dbe: vendor="X.Org Foundation"
[    25.914] 	compiled for 1.10.4, module version = 1.0.0
[    25.914] 	Module class: X.Org Server Extension
[    25.914] 	ABI class: X.Org Server Extension, version 5.0
[    25.914] (II) Loading extension DOUBLE-BUFFER
[    25.914] (II) LoadModule: "glx"
[    25.915] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.949] (II) Module glx: vendor="X.Org Foundation"
[    25.949] 	compiled for 1.10.4, module version = 1.0.0
[    25.949] 	ABI class: X.Org Server Extension, version 5.0
[    25.949] (==) AIGLX enabled
[    25.949] (II) Loading extension GLX
[    25.950] (II) LoadModule: "record"
[    25.950] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.970] (II) Module record: vendor="X.Org Foundation"
[    25.970] 	compiled for 1.10.4, module version = 1.13.0
[    25.970] 	Module class: X.Org Server Extension
[    25.970] 	ABI class: X.Org Server Extension, version 5.0
[    25.970] (II) Loading extension RECORD
[    25.970] (II) LoadModule: "dri"
[    25.970] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.993] (II) Module dri: vendor="X.Org Foundation"
[    25.993] 	compiled for 1.10.4, module version = 1.0.0
[    25.993] 	ABI class: X.Org Server Extension, version 5.0
[    25.993] (II) Loading extension XFree86-DRI
[    25.993] (II) LoadModule: "dri2"
[    25.993] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.994] (II) Module dri2: vendor="X.Org Foundation"
[    25.994] 	compiled for 1.10.4, module version = 1.2.0
[    25.994] 	ABI class: X.Org Server Extension, version 5.0
[    25.994] (II) Loading extension DRI2
[    25.994] (==) Matched intel as autoconfigured driver 0
[    25.994] (==) Matched vesa as autoconfigured driver 1
[    25.994] (==) Matched fbdev as autoconfigured driver 2
[    25.994] (==) Assigned the driver to the xf86ConfigLayout
[    25.994] (II) LoadModule: "intel"
[    25.995] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.021] (II) Module intel: vendor="X.Org Foundation"
[    26.021] 	compiled for 1.10.2.902, module version = 2.15.901
[    26.021] 	Module class: X.Org Video Driver
[    26.021] 	ABI class: X.Org Video Driver, version 10.0
[    26.022] (II) LoadModule: "vesa"
[    26.022] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.038] (II) Module vesa: vendor="X.Org Foundation"
[    26.038] 	compiled for 1.10.2, module version = 2.3.0
[    26.038] 	Module class: X.Org Video Driver
[    26.038] 	ABI class: X.Org Video Driver, version 10.0
[    26.038] (II) LoadModule: "fbdev"
[    26.038] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.039] (II) Module fbdev: vendor="X.Org Foundation"
[    26.039] 	compiled for 1.10.0, module version = 0.4.2
[    26.039] 	ABI class: X.Org Video Driver, version 10.0
[    26.039] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    26.039] (II) VESA: driver for VESA chipsets: vesa
[    26.039] (II) FBDEV: driver for framebuffer: fbdev
[    26.039] (++) using VT number 7

[    26.039] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    26.039] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    26.041] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.042] (WW) Falling back to old probe method for vesa
[    26.042] (WW) Falling back to old probe method for fbdev
[    26.042] (II) Loading sub module "fbdevhw"
[    26.042] (II) LoadModule: "fbdevhw"
[    26.042] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.072] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.072] 	compiled for 1.10.4, module version = 0.0.2
[    26.072] 	ABI class: X.Org Video Driver, version 10.0
[    26.072] drmOpenDevice: node name is /dev/dri/card0
[    26.072] drmOpenDevice: open result is 12, (OK)
[    26.072] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.072] drmOpenDevice: node name is /dev/dri/card0
[    26.072] drmOpenDevice: open result is 12, (OK)
[    26.072] drmOpenByBusid: drmOpenMinor returns 12
[    26.072] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.072] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.072] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.072] (==) intel(0): RGB weight 888
[    26.072] (==) intel(0): Default visual is TrueColor
[    26.072] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    26.072] (--) intel(0): Chipset: "965GM"
[    26.072] (**) intel(0): Relaxed fencing enabled
[    26.072] (**) intel(0): Wait on SwapBuffers? enabled
[    26.072] (**) intel(0): Triple buffering? enabled
[    26.072] (**) intel(0): Framebuffer tiled
[    26.072] (**) intel(0): Pixmaps tiled
[    26.072] (**) intel(0): 3D buffers tiled
[    26.072] (**) intel(0): SwapBuffers wait enabled
[    26.072] (==) intel(0): video overlay key set to 0x101fe
[    26.089] (II) intel(0): Output LVDS1 has no monitor section
[    26.091] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.130] (II) intel(0): Output VGA1 has no monitor section
[    26.571] (II) intel(0): Output TV1 has no monitor section
[    26.571] (II) intel(0): EDID for output LVDS1
[    26.571] (II) intel(0): Manufacturer: LPL  Model: d01  Serial#: 0
[    26.571] (II) intel(0): Year: 2007  Week: 0
[    26.571] (II) intel(0): EDID Version: 1.3
[    26.571] (II) intel(0): Digital Display Input
[    26.571] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.571] (II) intel(0): Gamma: 2.20
[    26.571] (II) intel(0): No DPMS capabilities specified
[    26.571] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.571] (II) intel(0): First detailed timing is preferred mode
[    26.571] (II) intel(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.571] (II) intel(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.571] (II) intel(0): Manufacturer's mask: 0
[    26.571] (II) intel(0): Supported detailed timing:
[    26.571] (II) intel(0): clock: 72.2 MHz   Image Size:  304 x 190 mm
[    26.571] (II) intel(0): h_active: 1280  h_sync: 1320  h_sync_end 1352 h_blank_end 1432 h_border: 0
[    26.571] (II) intel(0): v_active: 800  v_sync: 808  v_sync_end 816 v_blanking: 840 v_border: 0
[    26.571] (II) intel(0): Supported detailed timing:
[    26.571] (II) intel(0): clock: 72.2 MHz   Image Size:  304 x 190 mm
[    26.571] (II) intel(0): h_active: 1280  h_sync: 1320  h_sync_end 1352 h_blank_end 1432 h_border: 0
[    26.571] (II) intel(0): v_active: 800  v_sync: 808  v_sync_end 816 v_blanking: 840 v_border: 0
[    26.571] (II) intel(0):  Y276G
[    26.571] (II) intel(0):  '?GRv\98\C8\FF
[    26.571] (II) intel(0): EDID (in hex):
[    26.571] (II) intel(0): 	00ffffffffffff00320c010d00000000
[    26.571] (II) intel(0): 	00110103801e13780ab3859558538a28
[    26.571] (II) intel(0): 	25505400000001010101010101010101
[    26.571] (II) intel(0): 	010101010101311c0098502028302820
[    26.571] (II) intel(0): 	880030be10000018311c009850202830
[    26.571] (II) intel(0): 	2820880030be10000000000000fe0059
[    26.571] (II) intel(0): 	32373647003134315758310a000000fe
[    26.572] (II) intel(0): 	00273f47527698c8ff01010a20200086
[    26.572] (II) intel(0): EDID vendor "LPL", prod id 3329
[    26.572] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    26.572] (II) intel(0): Printing DDC gathered Modelines:
[    26.572] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    26.572] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.572] (II) intel(0): Printing probed modes for output LVDS1
[    26.572] (II) intel(0): Modeline "1280x800"x60.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    26.572] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.572] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.572] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.572] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.610] (II) intel(0): EDID for output VGA1
[    27.051] (II) intel(0): EDID for output TV1
[    27.051] (II) intel(0): Output LVDS1 connected
[    27.051] (II) intel(0): Output VGA1 disconnected
[    27.051] (II) intel(0): Output TV1 disconnected
[    27.051] (II) intel(0): Using exact sizes for initial modes
[    27.051] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    27.051] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.051] (II) intel(0): Kernel page flipping support detected, enabling
[    27.051] (**) intel(0): Display dimensions: (300, 190) mm
[    27.051] (**) intel(0): DPI set to (108, 106)
[    27.051] (II) Loading sub module "fb"
[    27.051] (II) LoadModule: "fb"
[    27.052] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.724] (II) Module fb: vendor="X.Org Foundation"
[    27.780] 	compiled for 1.10.4, module version = 1.0.0
[    27.780] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    27.780] (II) Loading sub module "dri2"
[    27.780] (II) LoadModule: "dri2"
[    27.780] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.780] (II) Module dri2: vendor="X.Org Foundation"
[    27.780] 	compiled for 1.10.4, module version = 1.2.0
[    27.780] 	ABI class: X.Org Server Extension, version 5.0
[    27.780] (II) UnloadModule: "vesa"
[    27.780] (II) Unloading vesa
[    27.780] (II) UnloadModule: "fbdev"
[    27.780] (II) Unloading fbdev
[    27.780] (II) UnloadModule: "fbdevhw"
[    27.780] (II) Unloading fbdevhw
[    27.780] (==) Depth 24 pixmap format is 32 bpp
[    27.780] (II) intel(0): [DRI2] Setup complete
[    27.780] (II) intel(0): [DRI2]   DRI driver: i965
[    27.780] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    28.083] (II) UXA(0): Driver registered support for the following operations:
[    28.084] (II)         solid
[    28.084] (II)         copy
[    28.084] (II)         composite (RENDER acceleration)
[    28.084] (II)         put_image
[    28.084] (II)         get_image
[    28.084] (==) intel(0): Backing store disabled
[    28.084] (==) intel(0): Silken mouse enabled
[    28.140] (II) intel(0): Initializing HW Cursor
[    28.160] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.166] (==) intel(0): DPMS enabled
[    28.166] (==) intel(0): Intel XvMC decoder enabled
[    28.166] (II) intel(0): Set up textured video
[    28.166] (II) intel(0): Set up overlay video
[    28.166] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    28.166] (II) intel(0): direct rendering: DRI2 Enabled
[    28.166] (==) intel(0): hotplug detection: "enabled"
[    28.166] (--) RandR disabled
[    28.166] (II) Initializing built-in extension Generic Event Extension
[    28.166] (II) Initializing built-in extension SHAPE
[    28.166] (II) Initializing built-in extension MIT-SHM
[    28.166] (II) Initializing built-in extension XInputExtension
[    28.166] (II) Initializing built-in extension XTEST
[    28.166] (II) Initializing built-in extension BIG-REQUESTS
[    28.166] (II) Initializing built-in extension SYNC
[    28.166] (II) Initializing built-in extension XKEYBOARD
[    28.166] (II) Initializing built-in extension XC-MISC
[    28.166] (II) Initializing built-in extension SECURITY
[    28.166] (II) Initializing built-in extension XINERAMA
[    28.166] (II) Initializing built-in extension XFIXES
[    28.166] (II) Initializing built-in extension RENDER
[    28.166] (II) Initializing built-in extension RANDR
[    28.166] (II) Initializing built-in extension COMPOSITE
[    28.166] (II) Initializing built-in extension DAMAGE
[    28.166] (II) Initializing built-in extension GESTURE
[    28.209] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    28.922] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.922] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.922] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.922] (II) AIGLX: enabled GLX_SGI_make_current_read
[    28.922] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.923] (II) AIGLX: Loaded and initialized i965
[    28.923] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.923] (II) intel(0): Setting screen physical size to 338 x 211
[    29.300] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.356] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    29.356] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.356] (II) LoadModule: "evdev"
[    29.356] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.687] (II) Module evdev: vendor="X.Org Foundation"
[    29.687] 	compiled for 1.10.2, module version = 2.6.0
[    29.687] 	Module class: X.Org XInput Driver
[    29.687] 	ABI class: X.Org XInput driver, version 12.3
[    29.687] (II) Using input driver 'evdev' for 'Video Bus'
[    29.687] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.687] (**) Video Bus: always reports core events
[    29.687] (**) Video Bus: Device: "/dev/input/event4"
[    29.687] (--) Video Bus: Found keys
[    29.687] (II) Video Bus: Configuring as keyboard
[    29.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    29.687] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    29.687] (**) Option "xkb_rules" "evdev"
[    29.687] (**) Option "xkb_model" "pc105"
[    29.687] (**) Option "xkb_layout" "us"
[    29.696] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.697] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.697] (II) Using input driver 'evdev' for 'Power Button'
[    29.697] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.697] (**) Power Button: always reports core events
[    29.697] (**) Power Button: Device: "/dev/input/event1"
[    29.697] (--) Power Button: Found keys
[    29.697] (II) Power Button: Configuring as keyboard
[    29.697] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    29.697] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.697] (**) Option "xkb_rules" "evdev"
[    29.697] (**) Option "xkb_model" "pc105"
[    29.697] (**) Option "xkb_layout" "us"
[    29.697] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.697] (II) No input driver/identifier specified (ignoring)
[    29.698] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.698] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.698] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.698] (**) Sleep Button: always reports core events
[    29.698] (**) Sleep Button: Device: "/dev/input/event2"
[    29.698] (--) Sleep Button: Found keys
[    29.698] (II) Sleep Button: Configuring as keyboard
[    29.698] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    29.698] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    29.698] (**) Option "xkb_rules" "evdev"
[    29.698] (**) Option "xkb_model" "pc105"
[    29.698] (**) Option "xkb_layout" "us"
[    29.701] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.701] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.701] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.704] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/event7)
[    29.704] (**) A4Tech PS/2+USB Mouse: Applying InputClass "evdev pointer catchall"
[    29.704] (II) Using input driver 'evdev' for 'A4Tech PS/2+USB Mouse'
[    29.704] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.704] (**) A4Tech PS/2+USB Mouse: always reports core events
[    29.704] (**) A4Tech PS/2+USB Mouse: Device: "/dev/input/event7"
[    29.704] (--) A4Tech PS/2+USB Mouse: Found 12 mouse buttons
[    29.704] (--) A4Tech PS/2+USB Mouse: Found scroll wheel(s)
[    29.704] (--) A4Tech PS/2+USB Mouse: Found relative axes
[    29.704] (--) A4Tech PS/2+USB Mouse: Found x and y relative axes
[    29.704] (II) A4Tech PS/2+USB Mouse: Configuring as mouse
[    29.704] (II) A4Tech PS/2+USB Mouse: Adding scrollwheel support
[    29.704] (**) A4Tech PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
[    29.704] (**) A4Tech PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.704] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7/event7"
[    29.704] (II) XINPUT: Adding extended input device "A4Tech PS/2+USB Mouse" (type: MOUSE)
[    29.704] (II) A4Tech PS/2+USB Mouse: initialized for relative axes.
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) keeping acceleration scheme 1
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration profile 0
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration factor: 2.000
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration threshold: 4
[    29.705] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/mouse0)
[    29.705] (II) No input driver/identifier specified (ignoring)
[    29.706] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event5)
[    29.706] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    29.706] (II) Using input driver 'evdev' for '  USB Keyboard'
[    29.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.706] (**)   USB Keyboard: always reports core events
[    29.706] (**)   USB Keyboard: Device: "/dev/input/event5"
[    29.706] (--)   USB Keyboard: Found keys
[    29.706] (II)   USB Keyboard: Configuring as keyboard
[    29.706] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5/event5"
[    29.706] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    29.706] (**) Option "xkb_rules" "evdev"
[    29.706] (**) Option "xkb_model" "pc105"
[    29.706] (**) Option "xkb_layout" "us"
[    29.707] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event6)
[    29.707] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    29.707] (II) Using input driver 'evdev' for '  USB Keyboard'
[    29.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.707] (**)   USB Keyboard: always reports core events
[    29.707] (**)   USB Keyboard: Device: "/dev/input/event6"
[    29.707] (--)   USB Keyboard: Found keys
[    29.707] (II)   USB Keyboard: Configuring as keyboard
[    29.707] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input6/event6"
[    29.707] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    29.707] (**) Option "xkb_rules" "evdev"
[    29.707] (**) Option "xkb_model" "pc105"
[    29.707] (**) Option "xkb_layout" "us"
[    29.708] (II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event11)
[    29.708] (**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[    29.708] (II) Using input driver 'evdev' for 'Laptop Integrated Webcam'
[    29.708] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.708] (**) Laptop Integrated Webcam: always reports core events
[    29.708] (**) Laptop Integrated Webcam: Device: "/dev/input/event11"
[    29.708] (--) Laptop Integrated Webcam: Found keys
[    29.708] (II) Laptop Integrated Webcam: Configuring as keyboard
[    29.708] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input11/event11"
[    29.708] (II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD)
[    29.708] (**) Option "xkb_rules" "evdev"
[    29.708] (**) Option "xkb_model" "pc105"
[    29.708] (**) Option "xkb_layout" "us"
[    29.713] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    29.713] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.713] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.713] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.713] (**) AT Translated Set 2 keyboard: always reports core events
[    29.713] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    29.713] (--) AT Translated Set 2 keyboard: Found keys
[    29.713] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    29.713] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    29.713] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    29.713] (**) Option "xkb_rules" "evdev"
[    29.713] (**) Option "xkb_model" "pc105"
[    29.713] (**) Option "xkb_layout" "us"
[    29.714] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    29.714] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    29.714] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    29.714] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.714] (**) PS/2 Mouse: always reports core events
[    29.714] (**) PS/2 Mouse: Device: "/dev/input/event8"
[    29.714] (--) PS/2 Mouse: Found 3 mouse buttons
[    29.714] (--) PS/2 Mouse: Found relative axes
[    29.714] (--) PS/2 Mouse: Found x and y relative axes
[    29.714] (II) PS/2 Mouse: Configuring as mouse
[    29.714] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    29.714] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.714] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    29.714] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    29.714] (II) PS/2 Mouse: initialized for relative axes.
[    29.714] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    29.714] (**) PS/2 Mouse: (accel) acceleration profile 0
[    29.714] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    29.714] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    29.715] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    29.715] (II) No input driver/identifier specified (ignoring)
[    29.715] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    29.715] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    29.715] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    29.715] (II) LoadModule: "synaptics"
[    29.715] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.753] (II) Module synaptics: vendor="X.Org Foundation"
[    29.753] 	compiled for 1.10.2, module version = 1.4.1
[    29.753] 	Module class: X.Org XInput Driver
[    29.753] 	ABI class: X.Org XInput driver, version 12.3
[    29.753] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    29.753] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.753] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.753] (**) Option "Device" "/dev/input/event9"
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right scroll-buttons
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.760] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.830] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    29.830] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    29.830] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    29.830] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.831] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    29.831] (II) No input driver/identifier specified (ignoring)
[    29.836] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    29.837] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.837] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    29.837] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.837] (**) Dell WMI hotkeys: always reports core events
[    29.837] (**) Dell WMI hotkeys: Device: "/dev/input/event10"
[    29.837] (--) Dell WMI hotkeys: Found keys
[    29.837] (II) Dell WMI hotkeys: Configuring as keyboard
[    29.837] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    29.837] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    29.837] (**) Option "xkb_rules" "evdev"
[    29.837] (**) Option "xkb_model" "pc105"
[    29.837] (**) Option "xkb_layout" "us"
[    34.395] (II) intel(0): EDID vendor "LPL", prod id 3329
[    34.395] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    34.395] (II) intel(0): Printing DDC gathered Modelines:
[    34.395] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    37.387] (II) intel(0): EDID vendor "LPL", prod id 3329
[    37.387] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    37.387] (II) intel(0): Printing DDC gathered Modelines:
[    37.387] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    37.966] (II) intel(0): EDID vendor "LPL", prod id 3329
[    37.966] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    37.966] (II) intel(0): Printing DDC gathered Modelines:
[    37.966] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    38.413] (II) intel(0): EDID vendor "LPL", prod id 3329
[    38.413] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    38.413] (II) intel(0): Printing DDC gathered Modelines:
[    38.413] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    38.863] (II) intel(0): EDID vendor "LPL", prod id 3329
[    38.863] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    38.863] (II) intel(0): Printing DDC gathered Modelines:
[    38.863] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    39.313] (II) intel(0): EDID vendor "LPL", prod id 3329
[    39.313] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    39.313] (II) intel(0): Printing DDC gathered Modelines:
[    39.313] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    40.427] (II) intel(0): EDID vendor "LPL", prod id 3329
[    40.427] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    40.427] (II) intel(0): Printing DDC gathered Modelines:
[    40.427] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    51.132] (II) intel(0): EDID vendor "LPL", prod id 3329
[    51.132] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    51.132] (II) intel(0): Printing DDC gathered Modelines:
[    51.132] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    51.679] (II) intel(0): EDID vendor "LPL", prod id 3329
[    51.679] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    51.679] (II) intel(0): Printing DDC gathered Modelines:
[    51.679] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    52.268] (II) intel(0): EDID vendor "LPL", prod id 3329
[    52.268] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    52.268] (II) intel(0): Printing DDC gathered Modelines:
[    52.268] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    52.843] (II) intel(0): EDID vendor "LPL", prod id 3329
[    52.843] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    52.843] (II) intel(0): Printing DDC gathered Modelines:
[    52.843] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    53.323] (II) intel(0): EDID vendor "LPL", prod id 3329
[    53.323] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    53.323] (II) intel(0): Printing DDC gathered Modelines:
[    53.323] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    53.823] (II) intel(0): EDID vendor "LPL", prod id 3329
[    53.823] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    53.823] (II) intel(0): Printing DDC gathered Modelines:
[    53.823] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    55.651] (II) intel(0): EDID vendor "LPL", prod id 3329
[    55.651] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    55.651] (II) intel(0): Printing DDC gathered Modelines:
[    55.651] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    56.159] (II) intel(0): EDID vendor "LPL", prod id 3329
[    56.159] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    56.159] (II) intel(0): Printing DDC gathered Modelines:
[    56.159] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    58.512] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    63.732] (II) intel(0): EDID vendor "LPL", prod id 3329
[    63.732] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    63.732] (II) intel(0): Printing DDC gathered Modelines:
[    63.732] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[   527.753] (II) intel(0): EDID vendor "LPL", prod id 3329
[   527.753] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[   527.753] (II) intel(0): Printing DDC gathered Modelines:
[   527.753] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[   720.155] (II) intel(0): EDID vendor "LPL", prod id 3329
[   720.155] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[   720.155] (II) intel(0): Printing DDC gathered Modelines:
[   720.155] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[  4909.029] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  4909.383] (II) intel(0): EDID vendor "LPL", prod id 3329
[  4909.383] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[  4909.383] (II) intel(0): Printing DDC gathered Modelines:
[  4909.383] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[  4926.412] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  5284.869] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  5300.404] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```

---

### Post by tista on 2011-09-15
> **suxenexus said:**
> Here it is :)

```
[    25.545] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    25.545] X Protocol Version 11, Revision 0
[    25.545] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    25.545] Current Operating System: Linux jp-Inspiron-1420 3.0.0-11-generic #17-Ubuntu SMP Fri Sep 9 17:48:40 UTC 2011 x86_64
[    25.545] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-11-generic root=UUID=9ac17751-ad78-4de1-835c-4d25dce04fb1 ro quiet splash vt.handoff=7
[    25.545] Build Date: 09 September 2011  11:21:54AM
[    25.545] xorg-server 2:1.10.4-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    25.545] Current version of pixman: 0.22.2
[    25.545] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    25.545] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.545] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 16 07:09:10 2011
[    25.620] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.733] (==) No Layout section.  Using the first Screen section.
[    25.733] (==) No screen section available. Using defaults.
[    25.733] (**) |-->Screen "Default Screen Section" (0)
[    25.733] (**) |   |-->Monitor "<default monitor>"
[    25.733] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    25.733] (==) Automatically adding devices
[    25.733] (==) Automatically enabling devices
[    25.775] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.775] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.775] 	Entry deleted from font path.
[    25.804] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    25.804] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.804] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.804] (II) Loader magic: 0x7e0220
[    25.804] (II) Module ABI versions:
[    25.804] 	X.Org ANSI C Emulation: 0.4
[    25.804] 	X.Org Video Driver: 10.0
[    25.804] 	X.Org XInput driver : 12.3
[    25.804] 	X.Org Server Extension : 5.0
[    25.805] (--) PCI:*(0:0:2:0) 8086:2a02:1028:01f3 rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[    25.805] (--) PCI: (0:0:2:1) 8086:2a03:1028:01f3 rev 12, Mem @ 0xfeb00000/1048576
[    25.805] (II) Open ACPI successful (/var/run/acpid.socket)
[    25.805] (II) LoadModule: "extmod"
[    25.874] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.900] (II) Module extmod: vendor="X.Org Foundation"
[    25.900] 	compiled for 1.10.4, module version = 1.0.0
[    25.900] 	Module class: X.Org Server Extension
[    25.900] 	ABI class: X.Org Server Extension, version 5.0
[    25.900] (II) Loading extension MIT-SCREEN-SAVER
[    25.900] (II) Loading extension XFree86-VidModeExtension
[    25.900] (II) Loading extension XFree86-DGA
[    25.900] (II) Loading extension DPMS
[    25.900] (II) Loading extension XVideo
[    25.900] (II) Loading extension XVideo-MotionCompensation
[    25.900] (II) Loading extension X-Resource
[    25.900] (II) LoadModule: "dbe"
[    25.901] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    25.914] (II) Module dbe: vendor="X.Org Foundation"
[    25.914] 	compiled for 1.10.4, module version = 1.0.0
[    25.914] 	Module class: X.Org Server Extension
[    25.914] 	ABI class: X.Org Server Extension, version 5.0
[    25.914] (II) Loading extension DOUBLE-BUFFER
[    25.914] (II) LoadModule: "glx"
[    25.915] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.949] (II) Module glx: vendor="X.Org Foundation"
[    25.949] 	compiled for 1.10.4, module version = 1.0.0
[    25.949] 	ABI class: X.Org Server Extension, version 5.0
[    25.949] (==) AIGLX enabled
[    25.949] (II) Loading extension GLX
[    25.950] (II) LoadModule: "record"
[    25.950] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.970] (II) Module record: vendor="X.Org Foundation"
[    25.970] 	compiled for 1.10.4, module version = 1.13.0
[    25.970] 	Module class: X.Org Server Extension
[    25.970] 	ABI class: X.Org Server Extension, version 5.0
[    25.970] (II) Loading extension RECORD
[    25.970] (II) LoadModule: "dri"
[    25.970] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.993] (II) Module dri: vendor="X.Org Foundation"
[    25.993] 	compiled for 1.10.4, module version = 1.0.0
[    25.993] 	ABI class: X.Org Server Extension, version 5.0
[    25.993] (II) Loading extension XFree86-DRI
[    25.993] (II) LoadModule: "dri2"
[    25.993] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.994] (II) Module dri2: vendor="X.Org Foundation"
[    25.994] 	compiled for 1.10.4, module version = 1.2.0
[    25.994] 	ABI class: X.Org Server Extension, version 5.0
[    25.994] (II) Loading extension DRI2
[    25.994] (==) Matched intel as autoconfigured driver 0
[    25.994] (==) Matched vesa as autoconfigured driver 1
[    25.994] (==) Matched fbdev as autoconfigured driver 2
[    25.994] (==) Assigned the driver to the xf86ConfigLayout
[    25.994] (II) LoadModule: "intel"
[    25.995] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.021] (II) Module intel: vendor="X.Org Foundation"
[    26.021] 	compiled for 1.10.2.902, module version = 2.15.901
[    26.021] 	Module class: X.Org Video Driver
[    26.021] 	ABI class: X.Org Video Driver, version 10.0
[    26.022] (II) LoadModule: "vesa"
[    26.022] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.038] (II) Module vesa: vendor="X.Org Foundation"
[    26.038] 	compiled for 1.10.2, module version = 2.3.0
[    26.038] 	Module class: X.Org Video Driver
[    26.038] 	ABI class: X.Org Video Driver, version 10.0
[    26.038] (II) LoadModule: "fbdev"
[    26.038] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.039] (II) Module fbdev: vendor="X.Org Foundation"
[    26.039] 	compiled for 1.10.0, module version = 0.4.2
[    26.039] 	ABI class: X.Org Video Driver, version 10.0
[    26.039] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    26.039] (II) VESA: driver for VESA chipsets: vesa
[    26.039] (II) FBDEV: driver for framebuffer: fbdev
[    26.039] (++) using VT number 7

[    26.039] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    26.039] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    26.041] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.042] (WW) Falling back to old probe method for vesa
[    26.042] (WW) Falling back to old probe method for fbdev
[    26.042] (II) Loading sub module "fbdevhw"
[    26.042] (II) LoadModule: "fbdevhw"
[    26.042] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.072] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.072] 	compiled for 1.10.4, module version = 0.0.2
[    26.072] 	ABI class: X.Org Video Driver, version 10.0
[    26.072] drmOpenDevice: node name is /dev/dri/card0
[    26.072] drmOpenDevice: open result is 12, (OK)
[    26.072] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    26.072] drmOpenDevice: node name is /dev/dri/card0
[    26.072] drmOpenDevice: open result is 12, (OK)
[    26.072] drmOpenByBusid: drmOpenMinor returns 12
[    26.072] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    26.072] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.072] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.072] (==) intel(0): RGB weight 888
[    26.072] (==) intel(0): Default visual is TrueColor
[    26.072] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    26.072] (--) intel(0): Chipset: "965GM"
[    26.072] (**) intel(0): Relaxed fencing enabled
[    26.072] (**) intel(0): Wait on SwapBuffers? enabled
[    26.072] (**) intel(0): Triple buffering? enabled
[    26.072] (**) intel(0): Framebuffer tiled
[    26.072] (**) intel(0): Pixmaps tiled
[    26.072] (**) intel(0): 3D buffers tiled
[    26.072] (**) intel(0): SwapBuffers wait enabled
[    26.072] (==) intel(0): video overlay key set to 0x101fe
[    26.089] (II) intel(0): Output LVDS1 has no monitor section
[    26.091] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    26.130] (II) intel(0): Output VGA1 has no monitor section
[    26.571] (II) intel(0): Output TV1 has no monitor section
[    26.571] (II) intel(0): EDID for output LVDS1
[    26.571] (II) intel(0): Manufacturer: LPL  Model: d01  Serial#: 0
[    26.571] (II) intel(0): Year: 2007  Week: 0
[    26.571] (II) intel(0): EDID Version: 1.3
[    26.571] (II) intel(0): Digital Display Input
[    26.571] (II) intel(0): Max Image Size [cm]: horiz.: 30  vert.: 19
[    26.571] (II) intel(0): Gamma: 2.20
[    26.571] (II) intel(0): No DPMS capabilities specified
[    26.571] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.571] (II) intel(0): First detailed timing is preferred mode
[    26.571] (II) intel(0): redX: 0.584 redY: 0.347   greenX: 0.324 greenY: 0.542
[    26.571] (II) intel(0): blueX: 0.158 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    26.571] (II) intel(0): Manufacturer's mask: 0
[    26.571] (II) intel(0): Supported detailed timing:
[    26.571] (II) intel(0): clock: 72.2 MHz   Image Size:  304 x 190 mm
[    26.571] (II) intel(0): h_active: 1280  h_sync: 1320  h_sync_end 1352 h_blank_end 1432 h_border: 0
[    26.571] (II) intel(0): v_active: 800  v_sync: 808  v_sync_end 816 v_blanking: 840 v_border: 0
[    26.571] (II) intel(0): Supported detailed timing:
[    26.571] (II) intel(0): clock: 72.2 MHz   Image Size:  304 x 190 mm
[    26.571] (II) intel(0): h_active: 1280  h_sync: 1320  h_sync_end 1352 h_blank_end 1432 h_border: 0
[    26.571] (II) intel(0): v_active: 800  v_sync: 808  v_sync_end 816 v_blanking: 840 v_border: 0
[    26.571] (II) intel(0):  Y276G
[    26.571] (II) intel(0):  '?GRv\98\C8\FF
[    26.571] (II) intel(0): EDID (in hex):
[    26.571] (II) intel(0): 	00ffffffffffff00320c010d00000000
[    26.571] (II) intel(0): 	00110103801e13780ab3859558538a28
[    26.571] (II) intel(0): 	25505400000001010101010101010101
[    26.571] (II) intel(0): 	010101010101311c0098502028302820
[    26.571] (II) intel(0): 	880030be10000018311c009850202830
[    26.571] (II) intel(0): 	2820880030be10000000000000fe0059
[    26.571] (II) intel(0): 	32373647003134315758310a000000fe
[    26.572] (II) intel(0): 	00273f47527698c8ff01010a20200086
[    26.572] (II) intel(0): EDID vendor "LPL", prod id 3329
[    26.572] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    26.572] (II) intel(0): Printing DDC gathered Modelines:
[    26.572] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    26.572] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    26.572] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    26.572] (II) intel(0): Printing probed modes for output LVDS1
[    26.572] (II) intel(0): Modeline "1280x800"x60.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    26.572] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.572] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.572] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.572] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.610] (II) intel(0): EDID for output VGA1
[    27.051] (II) intel(0): EDID for output TV1
[    27.051] (II) intel(0): Output LVDS1 connected
[    27.051] (II) intel(0): Output VGA1 disconnected
[    27.051] (II) intel(0): Output TV1 disconnected
[    27.051] (II) intel(0): Using exact sizes for initial modes
[    27.051] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    27.051] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.051] (II) intel(0): Kernel page flipping support detected, enabling
[    27.051] (**) intel(0): Display dimensions: (300, 190) mm
[    27.051] (**) intel(0): DPI set to (108, 106)
[    27.051] (II) Loading sub module "fb"
[    27.051] (II) LoadModule: "fb"
[    27.052] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.724] (II) Module fb: vendor="X.Org Foundation"
[    27.780] 	compiled for 1.10.4, module version = 1.0.0
[    27.780] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    27.780] (II) Loading sub module "dri2"
[    27.780] (II) LoadModule: "dri2"
[    27.780] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.780] (II) Module dri2: vendor="X.Org Foundation"
[    27.780] 	compiled for 1.10.4, module version = 1.2.0
[    27.780] 	ABI class: X.Org Server Extension, version 5.0
[    27.780] (II) UnloadModule: "vesa"
[    27.780] (II) Unloading vesa
[    27.780] (II) UnloadModule: "fbdev"
[    27.780] (II) Unloading fbdev
[    27.780] (II) UnloadModule: "fbdevhw"
[    27.780] (II) Unloading fbdevhw
[    27.780] (==) Depth 24 pixmap format is 32 bpp
[    27.780] (II) intel(0): [DRI2] Setup complete
[    27.780] (II) intel(0): [DRI2]   DRI driver: i965
[    27.780] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    28.083] (II) UXA(0): Driver registered support for the following operations:
[    28.084] (II)         solid
[    28.084] (II)         copy
[    28.084] (II)         composite (RENDER acceleration)
[    28.084] (II)         put_image
[    28.084] (II)         get_image
[    28.084] (==) intel(0): Backing store disabled
[    28.084] (==) intel(0): Silken mouse enabled
[    28.140] (II) intel(0): Initializing HW Cursor
[    28.160] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.166] (==) intel(0): DPMS enabled
[    28.166] (==) intel(0): Intel XvMC decoder enabled
[    28.166] (II) intel(0): Set up textured video
[    28.166] (II) intel(0): Set up overlay video
[    28.166] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    28.166] (II) intel(0): direct rendering: DRI2 Enabled
[    28.166] (==) intel(0): hotplug detection: "enabled"
[    28.166] (--) RandR disabled
[    28.166] (II) Initializing built-in extension Generic Event Extension
[    28.166] (II) Initializing built-in extension SHAPE
[    28.166] (II) Initializing built-in extension MIT-SHM
[    28.166] (II) Initializing built-in extension XInputExtension
[    28.166] (II) Initializing built-in extension XTEST
[    28.166] (II) Initializing built-in extension BIG-REQUESTS
[    28.166] (II) Initializing built-in extension SYNC
[    28.166] (II) Initializing built-in extension XKEYBOARD
[    28.166] (II) Initializing built-in extension XC-MISC
[    28.166] (II) Initializing built-in extension SECURITY
[    28.166] (II) Initializing built-in extension XINERAMA
[    28.166] (II) Initializing built-in extension XFIXES
[    28.166] (II) Initializing built-in extension RENDER
[    28.166] (II) Initializing built-in extension RANDR
[    28.166] (II) Initializing built-in extension COMPOSITE
[    28.166] (II) Initializing built-in extension DAMAGE
[    28.166] (II) Initializing built-in extension GESTURE
[    28.209] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/i965_dri.so
[    28.922] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.922] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.922] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.922] (II) AIGLX: enabled GLX_SGI_make_current_read
[    28.922] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.923] (II) AIGLX: Loaded and initialized i965
[    28.923] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.923] (II) intel(0): Setting screen physical size to 338 x 211
[    29.300] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.356] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    29.356] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.356] (II) LoadModule: "evdev"
[    29.356] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.687] (II) Module evdev: vendor="X.Org Foundation"
[    29.687] 	compiled for 1.10.2, module version = 2.6.0
[    29.687] 	Module class: X.Org XInput Driver
[    29.687] 	ABI class: X.Org XInput driver, version 12.3
[    29.687] (II) Using input driver 'evdev' for 'Video Bus'
[    29.687] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.687] (**) Video Bus: always reports core events
[    29.687] (**) Video Bus: Device: "/dev/input/event4"
[    29.687] (--) Video Bus: Found keys
[    29.687] (II) Video Bus: Configuring as keyboard
[    29.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input4/event4"
[    29.687] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    29.687] (**) Option "xkb_rules" "evdev"
[    29.687] (**) Option "xkb_model" "pc105"
[    29.687] (**) Option "xkb_layout" "us"
[    29.696] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.697] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.697] (II) Using input driver 'evdev' for 'Power Button'
[    29.697] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.697] (**) Power Button: always reports core events
[    29.697] (**) Power Button: Device: "/dev/input/event1"
[    29.697] (--) Power Button: Found keys
[    29.697] (II) Power Button: Configuring as keyboard
[    29.697] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    29.697] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    29.697] (**) Option "xkb_rules" "evdev"
[    29.697] (**) Option "xkb_model" "pc105"
[    29.697] (**) Option "xkb_layout" "us"
[    29.697] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.697] (II) No input driver/identifier specified (ignoring)
[    29.698] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.698] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.698] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.698] (**) Sleep Button: always reports core events
[    29.698] (**) Sleep Button: Device: "/dev/input/event2"
[    29.698] (--) Sleep Button: Found keys
[    29.698] (II) Sleep Button: Configuring as keyboard
[    29.698] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    29.698] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    29.698] (**) Option "xkb_rules" "evdev"
[    29.698] (**) Option "xkb_model" "pc105"
[    29.698] (**) Option "xkb_layout" "us"
[    29.701] (II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.701] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.701] (II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
[    29.701] (II) No input driver/identifier specified (ignoring)
[    29.704] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/event7)
[    29.704] (**) A4Tech PS/2+USB Mouse: Applying InputClass "evdev pointer catchall"
[    29.704] (II) Using input driver 'evdev' for 'A4Tech PS/2+USB Mouse'
[    29.704] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.704] (**) A4Tech PS/2+USB Mouse: always reports core events
[    29.704] (**) A4Tech PS/2+USB Mouse: Device: "/dev/input/event7"
[    29.704] (--) A4Tech PS/2+USB Mouse: Found 12 mouse buttons
[    29.704] (--) A4Tech PS/2+USB Mouse: Found scroll wheel(s)
[    29.704] (--) A4Tech PS/2+USB Mouse: Found relative axes
[    29.704] (--) A4Tech PS/2+USB Mouse: Found x and y relative axes
[    29.704] (II) A4Tech PS/2+USB Mouse: Configuring as mouse
[    29.704] (II) A4Tech PS/2+USB Mouse: Adding scrollwheel support
[    29.704] (**) A4Tech PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
[    29.704] (**) A4Tech PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.704] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input7/event7"
[    29.704] (II) XINPUT: Adding extended input device "A4Tech PS/2+USB Mouse" (type: MOUSE)
[    29.704] (II) A4Tech PS/2+USB Mouse: initialized for relative axes.
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) keeping acceleration scheme 1
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration profile 0
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration factor: 2.000
[    29.704] (**) A4Tech PS/2+USB Mouse: (accel) acceleration threshold: 4
[    29.705] (II) config/udev: Adding input device A4Tech PS/2+USB Mouse (/dev/input/mouse0)
[    29.705] (II) No input driver/identifier specified (ignoring)
[    29.706] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event5)
[    29.706] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    29.706] (II) Using input driver 'evdev' for '  USB Keyboard'
[    29.706] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.706] (**)   USB Keyboard: always reports core events
[    29.706] (**)   USB Keyboard: Device: "/dev/input/event5"
[    29.706] (--)   USB Keyboard: Found keys
[    29.706] (II)   USB Keyboard: Configuring as keyboard
[    29.706] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input5/event5"
[    29.706] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    29.706] (**) Option "xkb_rules" "evdev"
[    29.706] (**) Option "xkb_model" "pc105"
[    29.706] (**) Option "xkb_layout" "us"
[    29.707] (II) config/udev: Adding input device   USB Keyboard (/dev/input/event6)
[    29.707] (**)   USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    29.707] (II) Using input driver 'evdev' for '  USB Keyboard'
[    29.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.707] (**)   USB Keyboard: always reports core events
[    29.707] (**)   USB Keyboard: Device: "/dev/input/event6"
[    29.707] (--)   USB Keyboard: Found keys
[    29.707] (II)   USB Keyboard: Configuring as keyboard
[    29.707] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input6/event6"
[    29.707] (II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
[    29.707] (**) Option "xkb_rules" "evdev"
[    29.707] (**) Option "xkb_model" "pc105"
[    29.707] (**) Option "xkb_layout" "us"
[    29.708] (II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event11)
[    29.708] (**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[    29.708] (II) Using input driver 'evdev' for 'Laptop Integrated Webcam'
[    29.708] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.708] (**) Laptop Integrated Webcam: always reports core events
[    29.708] (**) Laptop Integrated Webcam: Device: "/dev/input/event11"
[    29.708] (--) Laptop Integrated Webcam: Found keys
[    29.708] (II) Laptop Integrated Webcam: Configuring as keyboard
[    29.708] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-6/2-6:1.0/input/input11/event11"
[    29.708] (II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD)
[    29.708] (**) Option "xkb_rules" "evdev"
[    29.708] (**) Option "xkb_model" "pc105"
[    29.708] (**) Option "xkb_layout" "us"
[    29.713] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    29.713] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.713] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.713] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.713] (**) AT Translated Set 2 keyboard: always reports core events
[    29.713] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    29.713] (--) AT Translated Set 2 keyboard: Found keys
[    29.713] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    29.713] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    29.713] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    29.713] (**) Option "xkb_rules" "evdev"
[    29.713] (**) Option "xkb_model" "pc105"
[    29.713] (**) Option "xkb_layout" "us"
[    29.714] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    29.714] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    29.714] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    29.714] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.714] (**) PS/2 Mouse: always reports core events
[    29.714] (**) PS/2 Mouse: Device: "/dev/input/event8"
[    29.714] (--) PS/2 Mouse: Found 3 mouse buttons
[    29.714] (--) PS/2 Mouse: Found relative axes
[    29.714] (--) PS/2 Mouse: Found x and y relative axes
[    29.714] (II) PS/2 Mouse: Configuring as mouse
[    29.714] (**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    29.714] (**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.714] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    29.714] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
[    29.714] (II) PS/2 Mouse: initialized for relative axes.
[    29.714] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    29.714] (**) PS/2 Mouse: (accel) acceleration profile 0
[    29.714] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    29.714] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    29.715] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    29.715] (II) No input driver/identifier specified (ignoring)
[    29.715] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    29.715] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    29.715] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    29.715] (II) LoadModule: "synaptics"
[    29.715] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.753] (II) Module synaptics: vendor="X.Org Foundation"
[    29.753] 	compiled for 1.10.2, module version = 1.4.1
[    29.753] 	Module class: X.Org XInput Driver
[    29.753] 	ABI class: X.Org XInput driver, version 12.3
[    29.753] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    29.753] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.753] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.753] (**) Option "Device" "/dev/input/event9"
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: buttons: left right scroll-buttons
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 16
[    29.760] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.760] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    29.830] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    29.830] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    29.830] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    29.830] (II) AlpsPS/2 ALPS GlidePoint: failed to open grail, no gesture support
[    29.830] (--) AlpsPS/2 ALPS GlidePoint: touchpad found
[    29.831] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    29.831] (II) No input driver/identifier specified (ignoring)
[    29.836] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    29.837] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.837] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    29.837] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.837] (**) Dell WMI hotkeys: always reports core events
[    29.837] (**) Dell WMI hotkeys: Device: "/dev/input/event10"
[    29.837] (--) Dell WMI hotkeys: Found keys
[    29.837] (II) Dell WMI hotkeys: Configuring as keyboard
[    29.837] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event10"
[    29.837] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    29.837] (**) Option "xkb_rules" "evdev"
[    29.837] (**) Option "xkb_model" "pc105"
[    29.837] (**) Option "xkb_layout" "us"
[    34.395] (II) intel(0): EDID vendor "LPL", prod id 3329
[    34.395] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    34.395] (II) intel(0): Printing DDC gathered Modelines:
[    34.395] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    37.387] (II) intel(0): EDID vendor "LPL", prod id 3329
[    37.387] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    37.387] (II) intel(0): Printing DDC gathered Modelines:
[    37.387] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    37.966] (II) intel(0): EDID vendor "LPL", prod id 3329
[    37.966] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    37.966] (II) intel(0): Printing DDC gathered Modelines:
[    37.966] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    38.413] (II) intel(0): EDID vendor "LPL", prod id 3329
[    38.413] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    38.413] (II) intel(0): Printing DDC gathered Modelines:
[    38.413] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    38.863] (II) intel(0): EDID vendor "LPL", prod id 3329
[    38.863] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    38.863] (II) intel(0): Printing DDC gathered Modelines:
[    38.863] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    39.313] (II) intel(0): EDID vendor "LPL", prod id 3329
[    39.313] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    39.313] (II) intel(0): Printing DDC gathered Modelines:
[    39.313] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    40.427] (II) intel(0): EDID vendor "LPL", prod id 3329
[    40.427] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    40.427] (II) intel(0): Printing DDC gathered Modelines:
[    40.427] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    51.132] (II) intel(0): EDID vendor "LPL", prod id 3329
[    51.132] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    51.132] (II) intel(0): Printing DDC gathered Modelines:
[    51.132] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    51.679] (II) intel(0): EDID vendor "LPL", prod id 3329
[    51.679] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    51.679] (II) intel(0): Printing DDC gathered Modelines:
[    51.679] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    52.268] (II) intel(0): EDID vendor "LPL", prod id 3329
[    52.268] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    52.268] (II) intel(0): Printing DDC gathered Modelines:
[    52.268] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    52.843] (II) intel(0): EDID vendor "LPL", prod id 3329
[    52.843] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    52.843] (II) intel(0): Printing DDC gathered Modelines:
[    52.843] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    53.323] (II) intel(0): EDID vendor "LPL", prod id 3329
[    53.323] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    53.323] (II) intel(0): Printing DDC gathered Modelines:
[    53.323] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    53.823] (II) intel(0): EDID vendor "LPL", prod id 3329
[    53.823] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    53.823] (II) intel(0): Printing DDC gathered Modelines:
[    53.823] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    55.651] (II) intel(0): EDID vendor "LPL", prod id 3329
[    55.651] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    55.651] (II) intel(0): Printing DDC gathered Modelines:
[    55.651] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    56.159] (II) intel(0): EDID vendor "LPL", prod id 3329
[    56.159] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    56.159] (II) intel(0): Printing DDC gathered Modelines:
[    56.159] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[    58.512] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    63.732] (II) intel(0): EDID vendor "LPL", prod id 3329
[    63.732] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    63.732] (II) intel(0): Printing DDC gathered Modelines:
[    63.732] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[   527.753] (II) intel(0): EDID vendor "LPL", prod id 3329
[   527.753] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[   527.753] (II) intel(0): Printing DDC gathered Modelines:
[   527.753] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[   720.155] (II) intel(0): EDID vendor "LPL", prod id 3329
[   720.155] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[   720.155] (II) intel(0): Printing DDC gathered Modelines:
[   720.155] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[  4909.029] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  4909.383] (II) intel(0): EDID vendor "LPL", prod id 3329
[  4909.383] (II) intel(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[  4909.383] (II) intel(0): Printing DDC gathered Modelines:
[  4909.383] (II) intel(0): Modeline "1280x800"x0.0   72.17  1280 1320 1352 1432  800 808 816 840 -hsync -vsync (50.4 kHz)
[  4926.412] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  5284.869] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[  5300.404] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```

@suxenexus,

seems your open-sourced Intel driver was loaded successfully... ;)
and the name in "System Info" must be shown the name of Mesa/DRI2 renderer name instead of general 2D graphic driver name, OK? so you should check the output of "glxinfo" out as well...

cheers.

---

### Post by suxenexus on 2011-09-16
Here's the output
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, 
    GL_ARB_multitexture, GL_EXT_framebuffer_sRGB, 
    GL_IBM_multimode_draw_arrays, GL_IBM_texture_mirrored_repeat, 
    GL_3DFX_texture_compression_FXT1, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

---

### Post by lucazade on 2011-09-17
> **suxenexus said:**
> Here's the output
```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM 
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_copy_texture, GL_EXT_polygon_offset, GL_EXT_subtexture, 
    GL_EXT_texture_object, GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, 
    GL_EXT_texture, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_ARB_point_parameters, GL_EXT_draw_range_elements, GL_EXT_packed_pixels, 
    GL_EXT_point_parameters, GL_EXT_rescale_normal, 
    GL_EXT_separate_specular_color, GL_EXT_texture_edge_clamp, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_ARB_framebuffer_sRGB, 
    GL_ARB_multitexture, GL_EXT_framebuffer_sRGB, 
    GL_IBM_multimode_draw_arrays, GL_IBM_texture_mirrored_repeat, 
    GL_3DFX_texture_compression_FXT1, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_NV_vertex_program, GL_ARB_depth_texture, 
    GL_ARB_occlusion_query, GL_ARB_shadow, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_window_pos, GL_ATI_envmap_bumpmap, 
    GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, GL_NV_depth_clamp, 
    GL_NV_vertex_program1_1, GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_shader, GL_ARB_shader_objects, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ATI_draw_buffers, 
    GL_ATI_texture_env_combine3, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_ARB_depth_clamp, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_point_sprite, GL_ARB_shading_language_100, GL_ARB_sync, 
    GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_rectangle, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_rgtc, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_packed_depth_stencil, GL_APPLE_object_purgeable, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, GL_EXT_draw_buffers2, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_env_combine, 
    GL_EXT_texture_sRGB_decode, GL_OES_EGL_image, GL_ARB_copy_buffer, 
    GL_ARB_half_float_vertex, GL_ARB_map_buffer_range, GL_ARB_texture_rg, 
    GL_ARB_texture_swizzle, GL_ARB_vertex_array_bgra, 
    GL_EXT_separate_shader_objects, GL_EXT_texture_swizzle, 
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
    GL_ARB_ES2_compatibility, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_provoking_vertex, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map, 
    GL_ARB_shader_texture_lod, GL_EXT_provoking_vertex, GL_EXT_texture_snorm, 
    GL_MESA_texture_signed_rgba, GL_ARB_robustness

32 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x090 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x091 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x092 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x093 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x094 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x095 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x096 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x097 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x098 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x09a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a6 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0a8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0aa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x05d 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

48 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x066 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x06d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06e 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x06f 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x070  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x071  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x072 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x074 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x075 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x076  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x078  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x079  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07a  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x07c 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x07f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x080 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x082 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x083 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x084 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x085 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x087 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x089  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x08b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow

```

also opengl seems working correctly.. I'd say the "Graphic Unknown" in System Settings it is just wrong because from logs everything is ok.

---

### Post by fjgaude on 2011-09-17
I have the same glxinfo output as suxenexus, and my System Info shows for the Graphics: Intel Ironlake Desktop.

All works beautifully under 11.10 Beta.

---

### Post by mitchellcipriano on 2011-09-19
I am running on an Intel Atom D510 with integrated graphics. I get the graphics unknown error and can only select 1024X768 or 800X600. Any ideas on how to get the correct driver to load?

---

### Post by lucazade on 2011-09-19
> **mitchellcipriano said:**
> I am running on an Intel Atom D510 with integrated graphics. I get the graphics unknown error and can only select 1024X768 or 800X600. Any ideas on how to get the correct driver to load?

Is it a netbook or a nettop?
I would not worry too much about 'graphics unknown' dialog because sometimes it reports wrong information.. it is still a new info tool so it has some bugs.

to check if your system is really using correct drivers (and it should because all intel drivers but poulsbo are installed by default and there are no alternatives) is to check these:

sudo lshw -C video

this check your gfx card and you could see if correct driver is loaded..  it should look similiar to this:
..
configuration: driver=i915
..

another thing to look at is xorg log
attach your /var/log/xorg.0.log to this post.

---

### Post by TheNessus on 2011-09-19
do you get an error about packages when trying to installing a wireless driver? 

what other errors do you have when you say wireless "doesn't work properly"?

---

### Post by mitchellcipriano on 2011-09-19
> **lucazade said:**
> Is it a netbook or a nettop?
I would not worry too much about 'graphics unknown' dialog because sometimes it reports wrong information.. it is still a new info tool so it has some bugs.

to check if your system is really using correct drivers (and it should because all intel drivers but poulsbo are installed by default and there are no alternatives) is to check these:

sudo lshw -C video

this check your gfx card and you could see if correct driver is loaded..  it should look similiar to this:
..
configuration: driver=i915
..

another thing to look at is xorg log
attach your /var/log/xorg.0.log to this post.


Here is the lshw output:

  *-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:50280000-502fffff ioport:3140(size=8) memory:40000000-4fffffff memory:50000000-500fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:50200000-5027ffff

My /var/log/xorg.0.log file is attached. I had to delete part of it to fit within the file size. I hope I left all the important parts.

Thanks for the help,

Mitch

---

### Post by lucazade on 2011-09-19
> **mitchellcipriano said:**
> Here is the lshw output:
..
drivers seem correctly installed and working but they detect a lcd panel up to 1024x768.. don't know what is your real resolution.

if it is bigger you probably need to pass to some special modelines to xorg.conf because the panel in not correctly detected via EDID.
What laptop is? brand and model?

---

### Post by mitchellcipriano on 2011-09-20
> **lucazade said:**
> drivers seem correctly installed and working but they detect a lcd panel up to 1024x768.. don't know what is your real resolution.

if it is bigger you probably need to pass to some special modelines to xorg.conf because the panel in not correctly detected via EDID.
What laptop is? brand and model?

It is not a laptop. It is actually an Intel development motherboard. I have it connected to a 22" monitor that can do 1680x1050. Any thoughts on how to get it to pick up the correct settings?

Thanks,

Mitch

---

### Post by dino99 on 2011-09-20
from synaptic: remove/purge ALL the installed video drivers & xserver-xorg-video-all

from nautilus: erase xorg.conf from both:

sudo rm /etc/X11/xorg.conf
sudo rm /usr/share/X11/xorg.conf.d/xorg.conf 
 (as i've not it on my system, maybe this is a little differently named, like xx-xorg.conf, glance at it first)

then from synaptic: reinstall xserver-xorg-video-intel & xserver-xorg-video-vesa

then reboot & check driver activation (additional drivers from menu)

---

### Post by lucazade on 2011-09-20
> **mitchellcipriano said:**
> It is not a laptop. It is actually an Intel development motherboard. I have it connected to a 22" monitor that can do 1680x1050. Any thoughts on how to get it to pick up the correct settings?

Thanks,

Mitch

ok post the output of
xrandr --query

and take a look at the end of this wiki, there are two ways to obtain monitor resolution modelines if EDID doesn't work properly (so no autocofiguration).
via cvt or using powerstrip on windows

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

when you get modelines you have to create an ad-hoc xorg.conf with that in monitor section

---

### Post by mitchellcipriano on 2011-09-21
I got it working!

Many thanks to all,

Mitch

---

### Post by mitchellcipriano on 2011-09-21
Maybe not so fast.

I ran these commands:
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

then
xrandr --addmode VGA1 1680x1050_60.00

When I reboot I get this:

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 1)

Then an ab back at 1024x768 until I run the commands again.

Any ideas?

---

### Post by lucazade on 2011-09-21
you need to create an ad-hoc xorg.conf file with that modeline.+
something like the example you find in this page.. adapt it

[https://help.ubuntu.com/community/NvidiaResolutionXorgConf](https://help.ubuntu.com/community/NvidiaResolutionXorgConf)

---

### Post by mitchellcipriano on 2011-09-21
I created the xorg.conf screen and put it in the xorg.confd directory, but I think I messed it up. Now it seems to boot, but after the Ubuntu logo, I just get a blank screen.

---

### Post by lucazade on 2011-09-21
start in recovery mode and purge it... post here if you can, we'll try to see what's wrong

---

### Post by mitchellcipriano on 2011-09-21
> **mitchellcipriano said:**
> I created the xorg.conf screen and put it in the xorg.confd directory, but I think I messed it up. Now it seems to boot, but after the Ubuntu logo, I just get a blank screen.

OK, I moved the Xorg.conf file I created and it boots fine now and functions as before.

Here is the contents of the Xorg.conf I created:

Section "Monitor"
    Identifier     "Configured Monitor"

    # NOTE: this modeline is generated using the cvt program (see below)
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
    
    # NOTE: A value for HorizSync can be 'guestimated' by using information from the xrandr program. 
    # If this value is too low or too high it can result in 'no screens found' error message and X won't start or your monitor won't be able to display the video.
    HorizSync   63.98  

    # NOTE: For TFT/LCD screens, refresh rates should be 60. For CRT screens, 72 to 100 is better.
    VertRefresh 60

    # NOTE: Measure your monitor's physical screen size by putting a metric ruler to the screen.
    # this is the screen size in millimeters (tweaked a little for better results)
    # You might not need this step, but it can result in the font and icon size being 
    # all wrong.  
    # DisplaySize 337.9 270.3
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "intel”
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24

        # NOTE: This is what made it work for me, use one entry in modes and use the 
        # identifier - 1280x1024_60.00 from the modeline above.
        # putting something else here didn't work for me and the resolution was not available in X.     
        Modes      "1680x10500.00"
    EndSubSection
EndSection

I copied it from the posting and modified the modeline based on my systems. What did I miss?

Thanks,

Mitch

---

### Post by lucazade on 2011-09-21
```
Section "Monitor"
    Identifier     "Configured Monitor"
    Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "intel"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60.00"
    EndSubSection
EndSection
```

try this

---

### Post by mitchellcipriano on 2011-09-21
It still boots with this xorg.conf, but it did not fix the problem. I put it in /usr/share/X11/xorg.conf.d. Is this the right location?

Thanks,

Mitch

---

### Post by lucazade on 2011-09-21
> **mitchellcipriano said:**
> It still boots with this xorg.conf, but it did not fix the problem. I put it in /usr/share/X11/xorg.conf.d. Is this the right location?

Thanks,

Mitch

ah too bad.
don't think it will change even moving to that new folder.

you have to check what xrandr (newmode and addmode functions) really do and how to convert in a working and permanent xorg.conf.
I've never played here with that (fortunately!) so I don't have other ideas.

---

### Post by lucazade on 2011-09-21
take a look at this guide
[http://mac.linux.be/content/setting-xorgconf-manually-xrandr](http://mac.linux.be/content/setting-xorgconf-manually-xrandr)

> Setting xrandr changes persistently
There are several ways to make xrandr customizations permanent from session to session: a) .xprofile, b) kdm/gdm, c) xorg.conf. Each of these mechanisms will be discussed in turn.
...


---

### Post by mitchellcipriano on 2011-09-21
> **lucazade said:**
> take a look at this guide
[http://mac.linux.be/content/setting-xorgconf-manually-xrandr](http://mac.linux.be/content/setting-xorgconf-manually-xrandr)

Thanks for the ideas. So far none worked. I tried to modify the gdm script as shown on the page, but I cannot find the scripts on my system. I do still get this error message when booting:
CRTC 63: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 800x600@56Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 848x480@60Hz with output at 1680x1050@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1680x1050@60Hz (pass 1)


Running the xrandr command manually fixes the resolution.

Best,

Mitch

---

### Post by suxenexus on 2011-09-22
> **lucazade said:**
> Is it a netbook or a nettop?
I would not worry too much about 'graphics unknown' dialog because sometimes it reports wrong information.. it is still a new info tool so it has some bugs.

to check if your system is really using correct drivers (and it should because all intel drivers but poulsbo are installed by default and there are no alternatives) is to check these:

sudo lshw -C video

this check your gfx card and you could see if correct driver is loaded..  it should look similiar to this:
..
configuration: driver=i915
..

another thing to look at is xorg log
attach your /var/log/xorg.0.log to this post.

Is this right?

```
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fea00000-feafffff memory:e0000000-efffffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff

```

---

### Post by suxenexus on 2011-09-22
> **TheNessus said:**
> do you get an error about packages when trying to installing a wireless driver? 

what other errors do you have when you say wireless "doesn't work properly"?

Wireless switch led doesn't turn on, I can't find any wifi network... etc etc

---


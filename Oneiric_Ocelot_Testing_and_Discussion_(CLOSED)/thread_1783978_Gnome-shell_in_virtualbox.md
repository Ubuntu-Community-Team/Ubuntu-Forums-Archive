---
title: "Gnome-shell in virtualbox"
date: 2011-06-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-06-16
Is anyone able to use gnome-shell in virtualbox 4.0.8?
Guest additions are installed from the vbox menu and 3D extension are enabled in guest options with 32mb videoram.

Starting gnome-shell from "Gnome" session in GDM ends in a  "Opps, something went wrong.." and it loads fallback panel automatically.

If I try to start gnome-shell from the fallback session:
$ gnome-shell --replace
failed to create drawable

(gnome-shell:1497): Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Error window manager: Unable to initialize Clutter.

```
$ cat /var/log/Xorg.0.log | more
[    26.154] 
X.Org X Server 1.10.2
Release Date: 2011-05-28
[    26.155] X Protocol Version 11, Revision 0
[    26.155] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    26.155] Current Operating System: Linux vbox 3.0-0-generic #1-Ubuntu SMP Th
u Jun 9 16:32:23 UTC 2011 i686
[    26.155] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0-0-generic root=UU
ID=6e9ecec9-d46a-487e-9dc7-bdd971810b6d ro quiet splash vt.handoff=7
[    26.155] Build Date: 16 June 2011  02:43:32AM
[    26.155] xorg-server 2:1.10.2-1ubuntu1 (For technical support please see htt
p://www.ubuntu.com/support) 
[    26.155] Current version of pixman: 0.21.8
[    26.155] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.155] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.169] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 16 19:25:54 201
1
[    26.180] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.187] (==) No Layout section.  Using the first Screen section.
[    26.187] (==) No screen section available. Using defaults.
[    26.187] (**) |-->Screen "Default Screen Section" (0)
[    26.187] (**) |   |-->Monitor "<default monitor>"
[    26.188] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.188] (==) Automatically adding devices
[    26.188] (==) Automatically enabling devices
[    26.189] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.189] 	Entry deleted from font path.
[    26.189] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.189] 	Entry deleted from font path.
[    26.189] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.189] 	Entry deleted from font path.
[    26.189] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.189] 	Entry deleted from font path.
[    26.189] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.189] 	Entry deleted from font path.
[    26.189] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.189] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.189] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.190] (II) Loader magic: 0x8238da0
[    26.190] (II) Module ABI versions:
[    26.190] 	X.Org ANSI C Emulation: 0.4
[    26.190] 	X.Org Video Driver: 10.0
[    26.190] 	X.Org XInput driver : 12.3
[    26.190] 	X.Org Server Extension : 5.0
[    26.202] (--) PCI:*(0:0:2:0) 80ee:beef:0000:0000 rev 0, Mem @ 0xe0000000/33554432
[    26.207] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.207] (II) LoadModule: "extmod"
[    26.223] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.224] (II) Module extmod: vendor="X.Org Foundation"
[    26.224] 	compiled for 1.10.2, module version = 1.0.0
[    26.224] 	Module class: X.Org Server Extension
[    26.224] 	ABI class: X.Org Server Extension, version 5.0
[    26.224] (II) Loading extension MIT-SCREEN-SAVER
[    26.224] (II) Loading extension XFree86-VidModeExtension
[    26.224] (II) Loading extension XFree86-DGA
[    26.224] (II) Loading extension DPMS
[    26.224] (II) Loading extension XVideo
[    26.224] (II) Loading extension XVideo-MotionCompensation
[    26.224] (II) Loading extension X-Resource
[    26.224] (II) LoadModule: "dbe"
[    26.225] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.226] (II) Module dbe: vendor="X.Org Foundation"
[    26.226] 	compiled for 1.10.2, module version = 1.0.0
[    26.226] 	Module class: X.Org Server Extension
[    26.226] 	ABI class: X.Org Server Extension, version 5.0
[    26.226] (II) Loading extension DOUBLE-BUFFER
[    26.226] (II) LoadModule: "glx"
[    26.227] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.236] (II) Module glx: vendor="X.Org Foundation"
[    26.236] 	compiled for 1.10.2, module version = 1.0.0
[    26.236] 	ABI class: X.Org Server Extension, version 5.0
[    26.236] (==) AIGLX enabled
[    26.237] (II) Loading extension GLX
[    26.237] (II) LoadModule: "record"
[    26.237] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.238] (II) Module record: vendor="X.Org Foundation"
[    26.238] 	compiled for 1.10.2, module version = 1.13.0
[    26.238] 	Module class: X.Org Server Extension
[    26.238] 	ABI class: X.Org Server Extension, version 5.0
[    26.238] (II) Loading extension RECORD
[    26.238] (II) LoadModule: "dri"
[    26.239] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.248] (II) Module dri: vendor="X.Org Foundation"
[    26.249] 	compiled for 1.10.2, module version = 1.0.0
[    26.249] 	ABI class: X.Org Server Extension, version 5.0
[    26.249] (II) Loading extension XFree86-DRI
[    26.249] (II) LoadModule: "dri2"
[    26.250] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.250] (II) Module dri2: vendor="X.Org Foundation"
[    26.250] 	compiled for 1.10.2, module version = 1.2.0
[    26.250] 	ABI class: X.Org Server Extension, version 5.0
[    26.250] (II) Loading extension DRI2
[    26.250] (==) Matched vboxvideo as autoconfigured driver 0
[    26.250] (==) Matched vesa as autoconfigured driver 1
[    26.250] (==) Matched fbdev as autoconfigured driver 2
[    26.250] (==) Assigned the driver to the xf86ConfigLayout
[    26.250] (II) LoadModule: "vboxvideo"
[    26.251] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    26.268] (II) Module vboxvideo: vendor="Oracle Corporation"
[    26.268] 	compiled for 1.5.99.901, module version = 1.0.1
[    26.268] 	Module class: X.Org Video Driver
[    26.268] 	ABI class: X.Org Video Driver, version 10.0
[    26.269] (**) Load address of symbol "VBOXVIDEO" is 0x3e3860
[    26.269] (II) LoadModule: "vesa"
[    26.269] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.270] (II) Module vesa: vendor="X.Org Foundation"
[    26.270] 	compiled for 1.10.2, module version = 2.3.0
[    26.270] 	Module class: X.Org Video Driver
[    26.270] 	ABI class: X.Org Video Driver, version 10.0
[    26.270] (II) LoadModule: "fbdev"
[    26.270] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.271] (II) Module fbdev: vendor="X.Org Foundation"
[    26.271] 	compiled for 1.10.0, module version = 0.4.2
[    26.271] 	ABI class: X.Org Video Driver, version 10.0
[    26.271] (II) VBoxVideo: guest driver for VirtualBox: vbox
[    26.271] (II) VESA: driver for VESA chipsets: vesa
[    26.271] (II) FBDEV: driver for framebuffer: fbdev
[    26.271] (++) using VT number 7

[    26.276] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    26.277] (WW) Falling back to old probe method for vesa
[    26.277] (WW) Falling back to old probe method for fbdev
[    26.277] (II) Loading sub module "fbdevhw"
[    26.277] (II) LoadModule: "fbdevhw"
[    26.277] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.278] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.278] 	compiled for 1.10.2, module version = 0.0.2
[    26.278] 	ABI class: X.Org Video Driver, version 10.0
[    26.278] (EE) open /dev/fb0: No such file or directory
[    26.309] (II) VBoxVideo(0): VirtualBox guest additions video driver version 4.0.8
[    26.310] (II) Loading sub module "ramdac"
[    26.310] (II) LoadModule: "ramdac"
[    26.310] (II) Module "ramdac" already built-in
[    26.310] (II) Loading sub module "vbe"
[    26.310] (II) LoadModule: "vbe"
[    26.310] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    26.311] (II) Module vbe: vendor="X.Org Foundation"
[    26.311] 	compiled for 1.10.2, module version = 1.1.0
[    26.311] 	ABI class: X.Org Video Driver, version 10.0
[    26.311] (II) Loading sub module "fb"
[    26.311] (II) LoadModule: "fb"
[    26.311] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.338] (II) Module fb: vendor="X.Org Foundation"
[    26.338] 	compiled for 1.10.2, module version = 1.0.0
[    26.338] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.338] (II) Loading sub module "shadowfb"
[    26.338] (II) LoadModule: "shadowfb"
[    26.339] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    26.354] (II) Module shadowfb: vendor="X.Org Foundation"
[    26.354] 	compiled for 1.10.2, module version = 1.0.0
[    26.354] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.354] (II) Loading sub module "vgahw"
[    26.354] (II) LoadModule: "vgahw"
[    26.355] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    26.359] (II) Module vgahw: vendor="X.Org Foundation"
[    26.359] 	compiled for 1.10.2, module version = 0.1.0
[    26.359] 	ABI class: X.Org Video Driver, version 10.0
[    26.359] (II) Loading sub module "dri"
[    26.359] (II) LoadModule: "dri"
[    26.360] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.360] (II) Module dri: vendor="X.Org Foundation"
[    26.360] 	compiled for 1.10.2, module version = 1.0.0
[    26.360] 	ABI class: X.Org Server Extension, version 5.0
[    26.362] (II) VBoxVideo(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.363] (==) VBoxVideo(0): Depth 24, (--) framebuffer bpp 32
[    26.363] (--) VBoxVideo(0): Virtual size is 32000x32000 (pitch 32000)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBoxInitialMode": 79.6 MHz (scaled from 0.0 MHz), 59.8 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBoxInitialMode"x0.0   79.60  1326 1328 1330 1332  990 992 994 996 (59.8 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 79.6 MHz (scaled from 0.0 MHz), 59.8 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   79.60  1326 1328 1330 1332  990 992 994 996 (59.8 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 79.6 MHz (scaled from 0.0 MHz), 59.8 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   79.60  1326 1328 1330 1332  990 992 994 996 (59.8 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBox-1280x960": 74.5 MHz (scaled from 0.0 MHz), 58.0 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBox-1280x960"x0.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBox-1024x768": 47.8 MHz (scaled from 0.0 MHz), 46.4 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBox-1024x768"x0.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBox-800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBox-800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    26.363] (**) VBoxVideo(0):  Built-in mode "VBox-640x480": 18.8 MHz (scaled from 0.0 MHz), 29.2 kHz, 60.0 Hz
[    26.363] (II) VBoxVideo(0): Modeline "VBox-640x480"x0.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    26.363] (==) VBoxVideo(0): RGB weight 888
[    26.363] (==) VBoxVideo(0): Default visual is TrueColor
[    26.363] (==) VBoxVideo(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.363] (==) VBoxVideo(0): DPI set to (96, 96)
[    26.363] (II) UnloadModule: "vesa"
[    26.363] (II) Unloading vesa
[    26.363] (II) UnloadModule: "fbdev"
[    26.363] (II) Unloading fbdev
[    26.364] (II) UnloadModule: "fbdevhw"
[    26.365] (II) Unloading fbdevhw
[    26.365] (--) Depth 24 pixmap format is 32 bpp
[    26.365] (II) Loading sub module "int10"
[    26.365] (II) LoadModule: "int10"
[    26.365] (II) Loading /usr/lib/xorg/modules/libint10.so
[    26.366] (II) Module int10: vendor="X.Org Foundation"
[    26.366] 	compiled for 1.10.2, module version = 1.0.0
[    26.366] 	ABI class: X.Org Video Driver, version 10.0
[    26.366] (II) VBoxVideo(0): initializing int10
[    26.369] (II) VBoxVideo(0): Primary V_BIOS segment is: 0xc000
[    26.372] (II) VBoxVideo(0): VESA BIOS detected
[    26.372] (II) VBoxVideo(0): VESA VBE Version 2.0
[    26.373] (II) VBoxVideo(0): VESA VBE Total Mem: 32768 kB
[    26.373] (II) VBoxVideo(0): VESA VBE OEM: VirtualBox VBE BIOS http://www.virtualbox.org/
[    26.373] (II) VBoxVideo(0): VESA VBE OEM Software Rev: 0.2
[    26.373] (II) VBoxVideo(0): VESA VBE OEM Vendor: Oracle Corporation
[    26.373] (II) VBoxVideo(0): VESA VBE OEM Product: Oracle VM VirtualBox VBE Adapter
[    26.373] (II) VBoxVideo(0): VESA VBE OEM Product Rev: Oracle VM VirtualBox Version 4.0.8
[    26.982] (==) VBoxVideo(0): Default visual is TrueColor
[    26.982] drmOpenDevice: node name is /dev/dri/card0
[    27.009] drmOpenDevice: node name is /dev/dri/card0
[    27.173] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    27.173] drmOpenDevice: node name is /dev/dri/card0
[    27.173] drmOpenDevice: open result is 16, (OK)
[    27.173] drmOpenByBusid: drmOpenMinor returns 16
[    27.173] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    27.173] (II) [drm] loaded kernel module for "vboxvideo" driver.
[    27.173] (II) [drm] DRM interface version 1.4
[    27.173] (II) [drm] DRM open master succeeded.
[    27.173] (II) VBoxVideo(0): [drm] Using the DRM lock SAREA also for drawables.
[    27.173] (II) VBoxVideo(0): [drm] framebuffer handle = 0xe0000000
[    27.174] (II) VBoxVideo(0): [drm] added 1 reserved context for kernel
[    27.174] (II) VBoxVideo(0): X context handle = 0x1
[    27.174] (II) VBoxVideo(0): [drm] installed DRM signal handler
[    27.174] (II) VBoxVideo(0): visual configurations initialized
[    27.175] (==) VBoxVideo(0): Backing store disabled
[    27.175] (II) VBoxVideo(0): Requested monitor count: 1
[    27.175] (II) VBoxVideo(0): Output VBOX0 has no monitor section
[    27.175] (II) VBoxVideo(0): Output VBOX0 has no monitor section
[    27.182] (II) VBoxVideo(0): EDID for output VBOX0
[    27.182] (II) VBoxVideo(0): Manufacturer: VBX  Model: 0  Serial#: 64881966
[    27.182] (II) VBoxVideo(0): Year: 1990  Week: 1
[    27.182] (II) VBoxVideo(0): EDID Version: 1.3
[    27.182] (II) VBoxVideo(0): Digital Display Input
[    27.182] (II) VBoxVideo(0): Indeterminate output size
[    27.182] (II) VBoxVideo(0): Gamma: 2.20
[    27.182] (II) VBoxVideo(0): DPMS capabilities: StandBy Suspend Off
[    27.182] (II) VBoxVideo(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    27.182] (II) VBoxVideo(0): Default color space is primary color space
[    27.182] (II) VBoxVideo(0): First detailed timing is preferred mode
[    27.182] (II) VBoxVideo(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    27.182] (II) VBoxVideo(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    27.182] (II) VBoxVideo(0): Manufacturer's mask: 0
[    27.182] (II) VBoxVideo(0): Supported detailed timing:
[    27.182] (II) VBoxVideo(0): clock: 79.6 MHz   Image Size:  0 x 0 mm
[    27.182] (II) VBoxVideo(0): h_active: 1326  h_sync: 1328  h_sync_end 1330 h_blank_end 1332 h_border: 0
[    27.182] (II) VBoxVideo(0): v_active: 990  v_sync: 992  v_sync_end 994 v_blanking: 996 v_border: 0
[    27.182] (II) VBoxVideo(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz, PixClock max 1005 MHz
[    27.182] (II) VBoxVideo(0): Monitor name: VBOX monitor
[    27.182] (II) VBoxVideo(0): EDID (in hex):
[    27.182] (II) VBoxVideo(0): 	00ffffffffffff00585800002e05de03
[    27.182] (II) VBoxVideo(0): 	0100010380000078eeee91a3544c9926
[    27.182] (II) VBoxVideo(0): 	0f505400000001010101010101010101
[    27.182] (II) VBoxVideo(0): 	010101010101181f2e0650de06300202
[    27.182] (II) VBoxVideo(0): 	2200000000000000000000fd0000c800
[    27.182] (II) VBoxVideo(0): 	c864000a202020202020000000fc0056
[    27.183] (II) VBoxVideo(0): 	424f58206d6f6e69746f720a00000010
[    27.183] (II) VBoxVideo(0): 	000a202020202020202020202020005c
[    27.183] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[    27.183] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1326x990 Warning: We only handle separate sync.
[    27.183] (II) VBoxVideo(0): Using hsync ranges from config file
[    27.183] (II) VBoxVideo(0): Using vrefresh ranges from config file
[    27.183] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[    27.183] (II) VBoxVideo(0): Modeline "1326x990"x0.0   79.60  1326 1328 1330 1332  990 992 994 996 -hsync -vsync (59.8 kHz)
[    27.183] (II) VBoxVideo(0): Printing probed modes for output VBOX0
[    27.183] (II) VBoxVideo(0): Modeline "1326x990"x60.0   79.60  1326 1328 1330 1332  990 992 994 996 (59.8 kHz)
[    27.183] (II) VBoxVideo(0): Modeline "1280x960"x60.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    27.183] (II) VBoxVideo(0): Modeline "1024x768"x60.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    27.183] (II) VBoxVideo(0): Modeline "800x600"x60.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    27.183] (II) VBoxVideo(0): Modeline "640x480"x60.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    27.183] (II) VBoxVideo(0): Output VBOX0 connected
[    27.183] (II) VBoxVideo(0): Using exact sizes for initial modes
[    27.183] (II) VBoxVideo(0): Output VBOX0 using initial mode 1326x990
[    27.183] (II) VBoxVideo(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    27.183] (II) VBoxVideo(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.191] (==) VBoxVideo(0): DPMS enabled
[    27.191] (II) VBoxVideo(0): [DRI] installation complete
[    27.191] (--) RandR disabled
[    27.191] (II) Initializing built-in extension Generic Event Extension
[    27.191] (II) Initializing built-in extension SHAPE
[    27.191] (II) Initializing built-in extension MIT-SHM
[    27.191] (II) Initializing built-in extension XInputExtension
[    27.191] (II) Initializing built-in extension XTEST
[    27.191] (II) Initializing built-in extension BIG-REQUESTS
[    27.191] (II) Initializing built-in extension SYNC
[    27.191] (II) Initializing built-in extension XKEYBOARD
[    27.191] (II) Initializing built-in extension XC-MISC
[    27.191] (II) Initializing built-in extension SECURITY
[    27.191] (II) Initializing built-in extension XINERAMA
[    27.191] (II) Initializing built-in extension XFIXES
[    27.191] (II) Initializing built-in extension RENDER
[    27.191] (II) Initializing built-in extension RANDR
[    27.191] (II) Initializing built-in extension COMPOSITE
[    27.191] (II) Initializing built-in extension DAMAGE
[    27.191] (II) Initializing built-in extension GESTURE
[    27.211] (II) AIGLX: Screen 0 is not DRI2 capable
[    27.217] drmOpenDevice: node name is /dev/dri/card0
[    27.217] drmOpenDevice: open result is 17, (OK)
[    27.219] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    27.219] drmOpenDevice: node name is /dev/dri/card0
[    27.219] drmOpenDevice: open result is 17, (OK)
[    27.219] drmOpenByBusid: drmOpenMinor returns 17
[    27.219] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    27.219] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    27.224] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/vboxvideo_dri.so
[    27.224] (II) AIGLX: dlopen of /usr/lib/i386-linux-gnu/dri/vboxvideo_dri.so failed (/usr/lib/i386-linux-gnu/dri/vboxvideo_dri.so: cannot open shared object file: No such file or dire
ctory)
[    27.224] (II) AIGLX: Trying DRI driver /usr/lib/dri/vboxvideo_dri.so
[    27.224] (II) AIGLX: dlopen of /usr/lib/dri/vboxvideo_dri.so failed (/usr/lib/dri/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    27.224] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri-alternates/vboxvideo_dri.so
[    27.224] (II) AIGLX: dlopen of /usr/lib/i386-linux-gnu/dri-alternates/vboxvideo_dri.so failed (/usr/lib/i386-linux-gnu/dri-alternates/vboxvideo_dri.so: cannot open shared object file
: No such file or directory)
[    27.224] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/vboxvideo_dri.so
[    27.225] (II) AIGLX: dlopen of /usr/lib/dri-alternates/vboxvideo_dri.so failed (/usr/lib/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    27.225] (II) AIGLX: Trying DRI driver /usr/lib32/dri/vboxvideo_dri.so
[    27.225] (II) AIGLX: dlopen of /usr/lib32/dri/vboxvideo_dri.so failed (/usr/lib32/dri/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    27.225] (II) AIGLX: Trying DRI driver /usr/lib32/dri-alternates/vboxvideo_dri.so
[    27.225] (II) AIGLX: dlopen of /usr/lib32/dri-alternates/vboxvideo_dri.so failed (/usr/lib32/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or director
y)
[    27.225] (EE) AIGLX: reverting to software rendering
[    27.225] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    27.246] (II) AIGLX: Loaded and initialized swrast
[    27.246] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    27.247] (II) VBoxVideo(0): Setting screen physical size to 350 x 261
[    27.306] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.370] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.370] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.371] (II) LoadModule: "evdev"
[    27.376] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.378] (II) Module evdev: vendor="X.Org Foundation"
[    27.378] 	compiled for 1.10.0.902, module version = 2.6.0
[    27.378] 	Module class: X.Org XInput Driver
[    27.378] 	ABI class: X.Org XInput driver, version 12.3
[    27.378] (II) Using input driver 'evdev' for 'Power Button'
[    27.378] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.378] (**) Power Button: always reports core events
[    27.378] (**) Power Button: Device: "/dev/input/event0"
[    27.378] (--) Power Button: Found keys
[    27.378] (II) Power Button: Configuring as keyboard
[    27.378] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    27.378] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    27.378] (**) Option "xkb_rules" "evdev"
[    27.378] (**) Option "xkb_model" "pc105"
[    27.378] (**) Option "xkb_layout" "it"
[    27.387] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    27.393] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    27.393] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.394] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.394] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.394] (**) Sleep Button: always reports core events
[    27.394] (**) Sleep Button: Device: "/dev/input/event1"
[    27.394] (--) Sleep Button: Found keys
[    27.394] (II) Sleep Button: Configuring as keyboard
[    27.394] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSLPBN:00/input/input1/event1"
[    27.394] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    27.394] (**) Option "xkb_rules" "evdev"

```

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer, GLX_INTEL_swap_event
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_INTEL_swap_event
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.10.3
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_copy_buffer, GL_ARB_depth_clamp, GL_ARB_depth_texture, 
    GL_ARB_draw_buffers, GL_ARB_draw_elements_base_vertex, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object, 
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex, 
    GL_ARB_map_buffer_range, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_occlusion_query, GL_ARB_pixel_buffer_object, 
    GL_ARB_point_parameters, GL_ARB_point_sprite, GL_ARB_provoking_vertex, 
    GL_ARB_shader_objects, GL_ARB_shading_language_100, GL_ARB_shadow_ambient, 
    GL_ARB_shadow, GL_ARB_sync, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_array_bgra, 
    GL_ARB_vertex_array_object, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, 
    GL_EXT_depth_bounds_test, GL_EXT_draw_buffers2, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_blit, 
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_paletted_texture, GL_EXT_pixel_buffer_object, 
    GL_EXT_point_parameters, GL_EXT_polygon_offset, GL_EXT_provoking_vertex, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_shader_objects, GL_EXT_separate_specular_color, 
    GL_EXT_shadow_funcs, GL_EXT_shared_texture_palette, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture3D, GL_EXT_texture_array, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture, GL_EXT_texture_rectangle, 
    GL_EXT_texture_sRGB, GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_EXT_vertex_array, GL_OES_read_format, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_object_purgeable, GL_APPLE_packed_pixels, 
    GL_APPLE_vertex_array_object, GL_ATI_blend_equation_separate, 
    GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_resize_buffers, GL_MESA_texture_array, 
    GL_MESA_window_pos, GL_MESA_ycbcr_texture, GL_NV_blend_square, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_light_max_exponent, 
    GL_NV_packed_depth_stencil, GL_NV_point_sprite, GL_NV_texgen_reflection, 
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGI_texture_color_table, GL_SUN_multi_draw_arrays

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ca 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0cd 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0ce 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0d1 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d2 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0d5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d6 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0d8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0da 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0dd 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0df 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0e0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0e1 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0e2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0e3 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0e4 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0e5 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e7 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0e9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ea 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0eb 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0ec 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ed 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0ee 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0ef 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f0 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f7 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0f8 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0f9 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0fa 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0fb 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0fc 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0fd 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0fe 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0ff 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x100 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x101 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x103 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x104 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x105 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x106 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x048 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None

128 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x049  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x04a  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x04b  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x04c  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x04d  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x04e  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x04f  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x050  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x051  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x052  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x053  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x054  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x055  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x056  0 tc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x057  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x058  0 tc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x059  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05a  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05d  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x05e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x05f  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x060  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x061  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x062  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x063  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x064  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x065  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x066  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x067  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x068  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x069 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x06c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x06e 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x071 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x072 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x073 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x074 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x075 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x076 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x077 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x078 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x079 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07a 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x07b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x07c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x07d 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x07e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x07f 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x080 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x081 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x082 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x083 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x084 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x085 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x086 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x087 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x088 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x089  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08a  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08b  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0  0  0  0  0  0 0 None
0x08c  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x08d  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x08e  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x08f  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8  0  0  0  0  0 0 None
0x090  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x091  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x092  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x093  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0  0  0  0  0  0 0 None
0x094  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  0 16 16 16  0  0 0 Slow
0x095  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x096  0 dc  0   8  0 r  . .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x097  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8  0  0  0  0  0 0 None
0x098  0 dc  0   8  0 r  y .   3  3  2  0 .  .  0  8  8 16 16 16  0  0 0 Slow
0x099  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09a  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09b  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x09c  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x09d  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x09e  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x09f  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0a0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0a1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a2  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0  0  0  0  0  0 0 None
0x0a4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  0 16 16 16  0  0 0 Slow
0x0a5  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0a6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a7  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8  0  0  0  0  0 0 None
0x0a8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 16  8 16 16 16  0  0 0 Slow
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0aa 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ad 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0af 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8  0  0  0  0  0 0 None
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  8 16 16 16  0  0 0 Slow
0x0b1 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0b2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0b4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b6 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b9 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0ba 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0bb 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0bc 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0bd 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0be 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0bf 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8  0  0  0  0  0 0 None
0x0c0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  8 16 16 16 16  0 0 Slow
0x0c1 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c2 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c3 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0c4 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0c5 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c6 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0c7 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0c8 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
```

Any hints?
Is it due to software rasterizer?  :)

---

### Post by rtalcott on 2011-06-16
It's working for me on two machines...vbox 4.08 + guest additions on 10.10 and 11.04 hosts although I have not done much with it  but it does come up..
rt

---

### Post by lucazade on 2011-06-17
can anyone paste the output of "glxinfo" and "/var/log/Xorg.0.log"
of a running gnome-shell session in Virtualbox? thanks

---

### Post by paul_in_london on 2011-06-17
Ok here with **xorg-edgers** ppa enabled.

Running **glxinfo** in the OO VM appeared to produce no output and caused graphical corruption. VM was no longer in a usable state, so rebooted and used the **script** command to try and capture any **glxinfo** output. Here it is - possibly incomplete:

```
paul@oneiric:~$ cat typescript 
Script started on Fri Jun 17 13:05:15 2011
paul@oneiric:~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: Chromium
server glx version string: 1.3 Chromium
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
client glx vendor string: Chromium
client glx version string: 1.3 Chromium
client glx extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
GLX version: 1.3
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_texture_from_pixmap, GLX_SGIX_fbconfig, 
    GLX_ARB_get_proc_address
OpenGL vendor string: Humper
OpenGL renderer string: Chromium
OpenGL version string: 2.1 Chromium 1.9
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
    GL_EXT_texture_compression_s3tc, GL_EXT_draw_range_elements, 
    GL_EXT_framebuffer_object, GL_EXT_compiled_vertex_array, 
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_multisample, 
    GL_ARB_multitexture, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shadow, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_EXT_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_EXT_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_func_separate, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture_cube_map, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture3D, GL_IBM_rasterpos_clip, 
    GL_NV_fog_distance, GL_NV_fragment_program, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_rectangle, GL_ARB_texture_rectangle, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, GL_SGIS_generate_mipmap, 
    GL_ARB_shading_language_100, GL_ARB_shader_objects, GL_ARB_vertex_shader, 
    GL_ARB_fragment_shader, GL_EXT_texture_sRGB, GL_EXT_framebuffer_blit, 
    GL_EXT_blend_equation_separate, GL_EXT_stencil_two_side, 
    GL_CR_state_parameter, GL_CR_cursor_position, GL_CR_bounding_box, 
    GL_CR_print_string, GL_CR_tilesort_info, GL_CR_synchronization, 
    GL_CR_head_spu_name, GL_CR_performance_info, GL_CR_window_size, 
    GL_CR_tile_info, GL_CR_saveframe, GL_CR_readback_barrier_size, 
    GL_CR_server_id_sharing, GL_CR_server_matrix,  GL_EXT_stencil_two_side

64 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0c8 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0c9 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ca 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cb 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cc 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cd 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ce 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0cf 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d0 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d1 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d2 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d3 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d4 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d5 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d6 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d7 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d8 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0d9 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0da 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0db 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0dc 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0dd 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0de 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0df 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e0 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e1 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e2 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e3 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e4 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e5 24 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e6 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e7 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e8 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0e9 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ea 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0eb 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ec 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ed 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ee 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ef 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f0 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f1 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f2 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f3 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f4 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f5 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f6 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f7 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f8 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0f9 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fa 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fb 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fc 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fd 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0fe 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x0ff 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x100 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x101 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x102 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x103 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x104 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x105 24 dc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None
0x047 32 tc  0  32  0 r  y y   8  8  8  8 .  .  0 16  8 16 16 16 16  0 0 None

64 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0c8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0c9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ca 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ce 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0cf 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0d9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0da 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0db 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0dc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0dd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0de 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0df 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0e9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ee 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0ef 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f4 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
0x0f5 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 16  8  0  0  0  0  1 1 None
paul@oneiric:~$ 
```

```
cat /var/log/Xorg.0.log
[    34.986] 
X.Org X Server 1.10.2
Release Date: 2011-05-28
[    34.987] X Protocol Version 11, Revision 0
[    34.987] Build Operating System: Linux 2.6.24-29-xen i686 Ubuntu
[    34.987] Current Operating System: Linux oneiric 3.0.0-0300rc3-generic #201106140913 SMP Tue Jun 14 09:57:16 UTC 2011 i686
[    34.987] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-0300rc3-generic root=UUID=b09d5248-aefc-4128-8a9b-70a7f9afe6bd ro splash quiet vt.handoff=7
[    34.987] Build Date: 16 June 2011  03:48:06PM
[    34.987] xorg-server 2:1.10.2+git20110616+server-1.10-branch.9551f504-0ubuntu0sarvatt (For technical support please see http://www.ubuntu.com/support) 
[    34.987] Current version of pixman: 0.21.8
[    34.987] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    34.987] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.988] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun 17 13:16:54 2011
[    35.003] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    35.120] (==) No Layout section.  Using the first Screen section.
[    35.121] (==) No screen section available. Using defaults.
[    35.121] (**) |-->Screen "Default Screen Section" (0)
[    35.121] (**) |   |-->Monitor "<default monitor>"
[    35.121] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    35.121] (==) Automatically adding devices
[    35.121] (==) Automatically enabling devices
[    35.122] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    35.122] 	Entry deleted from font path.
[    35.122] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	built-ins
[    35.122] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    35.122] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    35.122] (II) Loader magic: 0x8238da0
[    35.122] (II) Module ABI versions:
[    35.122] 	X.Org ANSI C Emulation: 0.4
[    35.122] 	X.Org Video Driver: 10.0
[    35.122] 	X.Org XInput driver : 12.3
[    35.122] 	X.Org Server Extension : 5.0
[    35.147] (--) PCI:*(0:0:2:0) 80ee:beef:0000:0000 rev 0, Mem @ 0xe0000000/134217728
[    35.147] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    35.147] (II) LoadModule: "extmod"
[    35.165] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    35.176] (II) Module extmod: vendor="X.Org Foundation"
[    35.176] 	compiled for 1.10.2, module version = 1.0.0
[    35.176] 	Module class: X.Org Server Extension
[    35.176] 	ABI class: X.Org Server Extension, version 5.0
[    35.176] (II) Loading extension MIT-SCREEN-SAVER
[    35.176] (II) Loading extension XFree86-VidModeExtension
[    35.176] (II) Loading extension XFree86-DGA
[    35.185] (II) Loading extension DPMS
[    35.185] (II) Loading extension XVideo
[    35.185] (II) Loading extension XVideo-MotionCompensation
[    35.185] (II) Loading extension X-Resource
[    35.185] (II) LoadModule: "dbe"
[    35.186] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    35.215] (II) Module dbe: vendor="X.Org Foundation"
[    35.215] 	compiled for 1.10.2, module version = 1.0.0
[    35.215] 	Module class: X.Org Server Extension
[    35.215] 	ABI class: X.Org Server Extension, version 5.0
[    35.215] (II) Loading extension DOUBLE-BUFFER
[    35.215] (II) LoadModule: "glx"
[    35.216] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    35.260] (II) Module glx: vendor="X.Org Foundation"
[    35.260] 	compiled for 1.10.2, module version = 1.0.0
[    35.260] 	ABI class: X.Org Server Extension, version 5.0
[    35.260] (==) AIGLX enabled
[    35.260] (II) Loading extension GLX
[    35.260] (II) LoadModule: "record"
[    35.261] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.273] (II) Module record: vendor="X.Org Foundation"
[    35.273] 	compiled for 1.10.2, module version = 1.13.0
[    35.273] 	Module class: X.Org Server Extension
[    35.273] 	ABI class: X.Org Server Extension, version 5.0
[    35.273] (II) Loading extension RECORD
[    35.273] (II) LoadModule: "dri"
[    35.274] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.294] (II) Module dri: vendor="X.Org Foundation"
[    35.294] 	compiled for 1.10.2, module version = 1.0.0
[    35.294] 	ABI class: X.Org Server Extension, version 5.0
[    35.294] (II) Loading extension XFree86-DRI
[    35.294] (II) LoadModule: "dri2"
[    35.295] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.312] (II) Module dri2: vendor="X.Org Foundation"
[    35.312] 	compiled for 1.10.2, module version = 1.2.0
[    35.312] 	ABI class: X.Org Server Extension, version 5.0
[    35.312] (II) Loading extension DRI2
[    35.312] (==) Matched vboxvideo as autoconfigured driver 0
[    35.312] (==) Matched vesa as autoconfigured driver 1
[    35.312] (==) Matched fbdev as autoconfigured driver 2
[    35.312] (==) Assigned the driver to the xf86ConfigLayout
[    35.312] (II) LoadModule: "vboxvideo"
[    35.315] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    35.340] (II) Module vboxvideo: vendor="Oracle Corporation"
[    35.340] 	compiled for 1.5.99.901, module version = 1.0.1
[    35.340] 	Module class: X.Org Video Driver
[    35.340] 	ABI class: X.Org Video Driver, version 10.0
[    35.340] (**) Load address of symbol "VBOXVIDEO" is 0xb72be860
[    35.340] (II) LoadModule: "vesa"
[    35.343] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.365] (II) Module vesa: vendor="X.Org Foundation"
[    35.365] 	compiled for 1.10.1, module version = 2.3.0
[    35.365] 	Module class: X.Org Video Driver
[    35.365] 	ABI class: X.Org Video Driver, version 10.0
[    35.365] (II) LoadModule: "fbdev"
[    35.367] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.387] (II) Module fbdev: vendor="X.Org Foundation"
[    35.387] 	compiled for 1.10.1, module version = 0.4.2
[    35.387] 	Module class: X.Org Video Driver
[    35.387] 	ABI class: X.Org Video Driver, version 10.0
[    35.387] (II) VBoxVideo: guest driver for VirtualBox: vbox
[    35.387] (II) VESA: driver for VESA chipsets: vesa
[    35.387] (II) FBDEV: driver for framebuffer: fbdev
[    35.387] (++) using VT number 1

[    35.387] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    35.387] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    35.402] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[    35.403] (WW) Falling back to old probe method for vesa
[    35.403] (WW) Falling back to old probe method for fbdev
[    35.403] (II) Loading sub module "fbdevhw"
[    35.403] (II) LoadModule: "fbdevhw"
[    35.411] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.414] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.414] 	compiled for 1.10.2, module version = 0.0.2
[    35.414] 	ABI class: X.Org Video Driver, version 10.0
[    35.415] (EE) open /dev/fb0: No such file or directory
[    35.416] (II) VBoxVideo(0): VirtualBox guest additions video driver version 4.0.8
[    35.416] (II) Loading sub module "ramdac"
[    35.416] (II) LoadModule: "ramdac"
[    35.416] (II) Module "ramdac" already built-in
[    35.416] (II) Loading sub module "vbe"
[    35.417] (II) LoadModule: "vbe"
[    35.418] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    35.434] (II) Module vbe: vendor="X.Org Foundation"
[    35.434] 	compiled for 1.10.2, module version = 1.1.0
[    35.434] 	ABI class: X.Org Video Driver, version 10.0
[    35.434] (II) Loading sub module "fb"
[    35.434] (II) LoadModule: "fb"
[    35.435] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.456] (II) Module fb: vendor="X.Org Foundation"
[    35.456] 	compiled for 1.10.2, module version = 1.0.0
[    35.456] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.456] (II) Loading sub module "shadowfb"
[    35.456] (II) LoadModule: "shadowfb"
[    35.457] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    35.459] (II) Module shadowfb: vendor="X.Org Foundation"
[    35.459] 	compiled for 1.10.2, module version = 1.0.0
[    35.459] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.459] (II) Loading sub module "vgahw"
[    35.459] (II) LoadModule: "vgahw"
[    35.460] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    35.471] (II) Module vgahw: vendor="X.Org Foundation"
[    35.471] 	compiled for 1.10.2, module version = 0.1.0
[    35.471] 	ABI class: X.Org Video Driver, version 10.0
[    35.471] (II) Loading sub module "dri"
[    35.471] (II) LoadModule: "dri"
[    35.472] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.472] (II) Module dri: vendor="X.Org Foundation"
[    35.472] 	compiled for 1.10.2, module version = 1.0.0
[    35.472] 	ABI class: X.Org Server Extension, version 5.0
[    35.474] (II) VBoxVideo(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    35.474] (==) VBoxVideo(0): Depth 24, (--) framebuffer bpp 32
[    35.474] (--) VBoxVideo(0): Virtual size is 32000x32000 (pitch 32000)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBoxInitialMode": 74.5 MHz (scaled from 0.0 MHz), 58.0 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBoxInitialMode"x0.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 74.5 MHz (scaled from 0.0 MHz), 58.0 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBoxDynamicMode": 74.5 MHz (scaled from 0.0 MHz), 58.0 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBoxDynamicMode"x0.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBox-1280x960": 74.5 MHz (scaled from 0.0 MHz), 58.0 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBox-1280x960"x0.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBox-1024x768": 47.8 MHz (scaled from 0.0 MHz), 46.4 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBox-1024x768"x0.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBox-800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBox-800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    35.474] (**) VBoxVideo(0):  Built-in mode "VBox-640x480": 18.8 MHz (scaled from 0.0 MHz), 29.2 kHz, 60.0 Hz
[    35.474] (II) VBoxVideo(0): Modeline "VBox-640x480"x0.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    35.474] (==) VBoxVideo(0): RGB weight 888
[    35.474] (==) VBoxVideo(0): Default visual is TrueColor
[    35.475] (==) VBoxVideo(0): Using gamma correction (1.0, 1.0, 1.0)
[    35.475] (==) VBoxVideo(0): DPI set to (96, 96)
[    35.475] (II) UnloadModule: "vesa"
[    35.475] (II) Unloading vesa
[    35.475] (II) UnloadModule: "fbdev"
[    35.475] (II) Unloading fbdev
[    35.475] (II) UnloadModule: "fbdevhw"
[    35.475] (II) Unloading fbdevhw
[    35.475] (--) Depth 24 pixmap format is 32 bpp
[    35.475] (II) Loading sub module "int10"
[    35.475] (II) LoadModule: "int10"
[    35.487] (II) Loading /usr/lib/xorg/modules/libint10.so
[    35.502] (II) Module int10: vendor="X.Org Foundation"
[    35.502] 	compiled for 1.10.2, module version = 1.0.0
[    35.502] 	ABI class: X.Org Video Driver, version 10.0
[    35.502] (II) VBoxVideo(0): initializing int10
[    35.506] (II) VBoxVideo(0): Primary V_BIOS segment is: 0xc000
[    35.530] (II) VBoxVideo(0): VESA BIOS detected
[    35.530] (II) VBoxVideo(0): VESA VBE Version 2.0
[    35.530] (II) VBoxVideo(0): VESA VBE Total Mem: 131072 kB
[    35.530] (II) VBoxVideo(0): VESA VBE OEM: VirtualBox VBE BIOS http://www.virtualbox.org/
[    35.530] (II) VBoxVideo(0): VESA VBE OEM Software Rev: 0.2
[    35.530] (II) VBoxVideo(0): VESA VBE OEM Vendor: Oracle Corporation
[    35.530] (II) VBoxVideo(0): VESA VBE OEM Product: Oracle VM VirtualBox VBE Adapter
[    35.530] (II) VBoxVideo(0): VESA VBE OEM Product Rev: Oracle VM VirtualBox Version 4.0.8
[    36.545] (==) VBoxVideo(0): Default visual is TrueColor
[    36.551] drmOpenDevice: node name is /dev/dri/card0
[    36.584] drmOpenDevice: node name is /dev/dri/card0
[    36.738] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    36.738] drmOpenDevice: node name is /dev/dri/card0
[    36.738] drmOpenDevice: open result is 15, (OK)
[    36.738] drmOpenByBusid: drmOpenMinor returns 15
[    36.738] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    36.738] (II) [drm] loaded kernel module for "vboxvideo" driver.
[    36.738] (II) [drm] DRM interface version 1.4
[    36.750] (II) [drm] DRM open master succeeded.
[    36.750] (II) VBoxVideo(0): [drm] Using the DRM lock SAREA also for drawables.
[    36.750] (II) VBoxVideo(0): [drm] framebuffer handle = 0xe0000000
[    36.750] (II) VBoxVideo(0): [drm] added 1 reserved context for kernel
[    36.750] (II) VBoxVideo(0): X context handle = 0x1
[    36.751] (II) VBoxVideo(0): [drm] installed DRM signal handler
[    36.751] (II) VBoxVideo(0): visual configurations initialized
[    36.766] (==) VBoxVideo(0): Backing store disabled
[    36.767] (II) VBoxVideo(0): Requested monitor count: 1
[    36.767] (II) VBoxVideo(0): Output VBOX0 has no monitor section
[    36.767] (II) VBoxVideo(0): Output VBOX0 has no monitor section
[    36.769] (II) VBoxVideo(0): EDID for output VBOX0
[    36.769] (II) VBoxVideo(0): Manufacturer: VBX  Model: 0  Serial#: 62915840
[    36.769] (II) VBoxVideo(0): Year: 1990  Week: 1
[    36.769] (II) VBoxVideo(0): EDID Version: 1.3
[    36.769] (II) VBoxVideo(0): Digital Display Input
[    36.769] (II) VBoxVideo(0): Indeterminate output size
[    36.769] (II) VBoxVideo(0): Gamma: 2.20
[    36.769] (II) VBoxVideo(0): DPMS capabilities: StandBy Suspend Off
[    36.769] (II) VBoxVideo(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    36.769] (II) VBoxVideo(0): Default color space is primary color space
[    36.769] (II) VBoxVideo(0): First detailed timing is preferred mode
[    36.769] (II) VBoxVideo(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    36.769] (II) VBoxVideo(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    36.769] (II) VBoxVideo(0): Manufacturer's mask: 0
[    36.770] (II) VBoxVideo(0): Supported detailed timing:
[    36.770] (II) VBoxVideo(0): clock: 74.5 MHz   Image Size:  0 x 0 mm
[    36.770] (II) VBoxVideo(0): h_active: 1280  h_sync: 1282  h_sync_end 1284 h_blank_end 1286 h_border: 0
[    36.770] (II) VBoxVideo(0): v_active: 960  v_sync: 962  v_sync_end 964 v_blanking: 966 v_border: 0
[    36.770] (II) VBoxVideo(0): Ranges: V min: 0 V max: 200 Hz, H min: 0 H max: 200 kHz, PixClock max 1005 MHz
[    36.770] (II) VBoxVideo(0): Monitor name: VBOX monitor
[    36.770] (II) VBoxVideo(0): EDID (in hex):
[    36.770] (II) VBoxVideo(0): 	00ffffffffffff00585800000005c003
[    36.770] (II) VBoxVideo(0): 	0100010380000078eeee91a3544c9926
[    36.770] (II) VBoxVideo(0): 	0f505400000001010101010101010101
[    36.770] (II) VBoxVideo(0): 	0101010101011d1d000650c006300202
[    36.770] (II) VBoxVideo(0): 	2200000000000000000000fd0000c800
[    36.770] (II) VBoxVideo(0): 	c864000a202020202020000000fc0056
[    36.770] (II) VBoxVideo(0): 	424f58206d6f6e69746f720a00000010
[    36.770] (II) VBoxVideo(0): 	000a20202020202020202020202000f1
[    36.770] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[    36.770] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1280x960 Warning: We only handle separate sync.
[    36.770] (II) VBoxVideo(0): Using hsync ranges from config file
[    36.770] (II) VBoxVideo(0): Using vrefresh ranges from config file
[    36.770] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[    36.770] (II) VBoxVideo(0): Modeline "1280x960"x0.0   74.53  1280 1282 1284 1286  960 962 964 966 -hsync -vsync (58.0 kHz)
[    36.772] (II) VBoxVideo(0): Printing probed modes for output VBOX0
[    36.776] (II) VBoxVideo(0): Modeline "1280x960"x60.0   74.54  1280 1282 1284 1286  960 962 964 966 (58.0 kHz)
[    36.776] (II) VBoxVideo(0): Modeline "1024x768"x60.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz)
[    36.776] (II) VBoxVideo(0): Modeline "800x600"x60.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz)
[    36.776] (II) VBoxVideo(0): Modeline "640x480"x60.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz)
[    36.776] (II) VBoxVideo(0): Output VBOX0 connected
[    36.776] (II) VBoxVideo(0): Using exact sizes for initial modes
[    36.776] (II) VBoxVideo(0): Output VBOX0 using initial mode 1280x960
[    36.776] (II) VBoxVideo(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    36.776] (II) VBoxVideo(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.785] (==) VBoxVideo(0): DPMS enabled
[    36.785] (II) VBoxVideo(0): [DRI] installation complete
[    36.785] (--) RandR disabled
[    36.785] (II) Initializing built-in extension Generic Event Extension
[    36.785] (II) Initializing built-in extension SHAPE
[    36.785] (II) Initializing built-in extension MIT-SHM
[    36.785] (II) Initializing built-in extension XInputExtension
[    36.785] (II) Initializing built-in extension XTEST
[    36.785] (II) Initializing built-in extension BIG-REQUESTS
[    36.785] (II) Initializing built-in extension SYNC
[    36.785] (II) Initializing built-in extension XKEYBOARD
[    36.785] (II) Initializing built-in extension XC-MISC
[    36.785] (II) Initializing built-in extension SECURITY
[    36.785] (II) Initializing built-in extension XINERAMA
[    36.785] (II) Initializing built-in extension XFIXES
[    36.785] (II) Initializing built-in extension RENDER
[    36.785] (II) Initializing built-in extension RANDR
[    36.785] (II) Initializing built-in extension COMPOSITE
[    36.785] (II) Initializing built-in extension DAMAGE
[    36.785] (II) Initializing built-in extension GESTURE
[    36.807] (II) AIGLX: Screen 0 is not DRI2 capable
[    36.807] drmOpenDevice: node name is /dev/dri/card0
[    36.807] drmOpenDevice: open result is 16, (OK)
[    36.807] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    36.807] drmOpenDevice: node name is /dev/dri/card0
[    36.807] drmOpenDevice: open result is 16, (OK)
[    36.807] drmOpenByBusid: drmOpenMinor returns 16
[    36.807] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    36.807] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    36.807] (II) AIGLX: Trying DRI driver /usr/lib/dri/vboxvideo_dri.so
[    36.988] (II) Next line is added to allow vboxvideo_drv.so to appear as whitelisted driver
[    36.988] (II) The file referenced, is *NOT* loaded
[    36.988] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    36.988] (II) AIGLX: vboxvideo does not export required DRI extension
[    36.989] (II) AIGLX: Trying DRI driver /usr/lib/dri-alternates/vboxvideo_dri.so
[    36.989] (II) AIGLX: dlopen of /usr/lib/dri-alternates/vboxvideo_dri.so failed (/usr/lib/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    36.989] (II) AIGLX: Trying DRI driver /usr/lib32/dri/vboxvideo_dri.so
[    36.990] (II) AIGLX: dlopen of /usr/lib32/dri/vboxvideo_dri.so failed (/usr/lib32/dri/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    36.990] (II) AIGLX: Trying DRI driver /usr/lib32/dri-alternates/vboxvideo_dri.so
[    36.990] (II) AIGLX: dlopen of /usr/lib32/dri-alternates/vboxvideo_dri.so failed (/usr/lib32/dri-alternates/vboxvideo_dri.so: cannot open shared object file: No such file or directory)
[    36.990] (EE) AIGLX: reverting to software rendering
[    36.990] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[    37.133] (II) AIGLX: Loaded and initialized swrast
[    37.133] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    37.133] (II) VBoxVideo(0): Setting screen physical size to 338 x 253
[    37.260] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.390] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    37.390] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    37.390] (II) LoadModule: "evdev"
[    37.391] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.436] (II) Module evdev: vendor="X.Org Foundation"
[    37.436] 	compiled for 1.10.0.902, module version = 2.6.0
[    37.436] 	Module class: X.Org XInput Driver
[    37.436] 	ABI class: X.Org XInput driver, version 12.3
[    37.436] (II) Using input driver 'evdev' for 'Power Button'
[    37.436] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.436] (**) Power Button: always reports core events
[    37.436] (**) Power Button: Device: "/dev/input/event0"
[    37.436] (--) Power Button: Found keys
[    37.436] (II) Power Button: Configuring as keyboard
[    37.436] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    37.436] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    37.436] (**) Option "xkb_rules" "evdev"
[    37.437] (**) Option "xkb_model" "pc105"
[    37.437] (**) Option "xkb_layout" "gb"
[    37.446] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    37.461] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    37.461] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    37.461] (II) Using input driver 'evdev' for 'Sleep Button'
[    37.461] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.461] (**) Sleep Button: always reports core events
[    37.461] (**) Sleep Button: Device: "/dev/input/event1"
[    37.461] (--) Sleep Button: Found keys
[    37.461] (II) Sleep Button: Configuring as keyboard
[    37.461] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSLPBN:00/input/input1/event1"
[    37.461] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    37.461] (**) Option "xkb_rules" "evdev"
[    37.461] (**) Option "xkb_model" "pc105"
[    37.462] (**) Option "xkb_layout" "gb"
[    37.537] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/event3)
[    37.537] (**) VirtualBox USB Tablet: Applying InputClass "evdev pointer catchall"
[    37.537] (II) Using input driver 'evdev' for 'VirtualBox USB Tablet'
[    37.537] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.537] (**) VirtualBox USB Tablet: always reports core events
[    37.538] (**) VirtualBox USB Tablet: Device: "/dev/input/event3"
[    37.558] (--) VirtualBox USB Tablet: Found 9 mouse buttons
[    37.558] (--) VirtualBox USB Tablet: Found scroll wheel(s)
[    37.558] (--) VirtualBox USB Tablet: Found relative axes
[    37.558] (--) VirtualBox USB Tablet: Found absolute axes
[    37.559] (II) evdev-grail: failed to open grail, no gesture support
[    37.559] (--) VirtualBox USB Tablet: Found x and y absolute axes
[    37.559] (II) VirtualBox USB Tablet: Configuring as mouse
[    37.559] (II) VirtualBox USB Tablet: Adding scrollwheel support
[    37.559] (**) VirtualBox USB Tablet: YAxisMapping: buttons 4 and 5
[    37.559] (**) VirtualBox USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.559] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:06.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    37.559] (II) XINPUT: Adding extended input device "VirtualBox USB Tablet" (type: MOUSE)
[    37.559] (EE) VirtualBox USB Tablet: failed to initialize for relative axes.
[    37.559] (II) VirtualBox USB Tablet: initialized for absolute axes.
[    37.559] (**) VirtualBox USB Tablet: (accel) keeping acceleration scheme 1
[    37.559] (**) VirtualBox USB Tablet: (accel) acceleration profile 0
[    37.559] (**) VirtualBox USB Tablet: (accel) acceleration factor: 2.000
[    37.559] (**) VirtualBox USB Tablet: (accel) acceleration threshold: 4
[    37.561] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/js0)
[    37.561] (II) No input driver/identifier specified (ignoring)
[    37.562] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/mouse0)
[    37.562] (II) No input driver/identifier specified (ignoring)
[    37.615] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    37.615] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    37.615] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    37.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.615] (**) AT Translated Set 2 keyboard: always reports core events
[    37.615] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    37.620] (--) AT Translated Set 2 keyboard: Found keys
[    37.620] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    37.620] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    37.620] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    37.621] (**) Option "xkb_rules" "evdev"
[    37.621] (**) Option "xkb_model" "pc105"
[    37.621] (**) Option "xkb_layout" "gb"
[    37.623] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event4)
[    37.623] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[    37.623] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[    37.623] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.623] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[    37.623] (**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
[    37.624] (--) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[    37.630] (--) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[    37.630] (--) ImExPS/2 Generic Explorer Mouse: Found relative axes
[    37.631] (--) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[    37.631] (II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[    37.631] (II) ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    37.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event4"
[    37.631] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
[    37.631] (II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[    37.631] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[    37.633] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse1)
[    37.633] (II) No input driver/identifier specified (ignoring)
[    37.792] (II) config/udev: Adding input device (unnamed) (/dev/vboxguest)
[    37.792] (**) (unnamed): Applying InputClass "vboxmouse"
[    37.792] (II) LoadModule: "vboxmouse"
[    37.794] (II) Loading /usr/lib/xorg/modules/input/vboxmouse_drv.so
[    37.808] (II) Module vboxmouse: vendor="Oracle Corporation"
[    37.808] 	compiled for 0.0.0, module version = 1.0.0
[    37.808] 	Module class: X.Org XInput Driver
[    37.808] 	ABI class: X.Org XInput driver, version 12.2
[    37.808] (**) Load address of symbol "VBOXMOUSE" is 0xaec21020
[    37.808] (II) Using input driver 'vboxmouse' for '(unnamed)'
[    37.808] (II) Loading /usr/lib/xorg/modules/input/vboxmouse_drv.so
[    37.808] (**) (unnamed): always reports core events
[    37.808] (**) (unnamed): Device: "/dev/vboxguest"
[    37.809] (**) Option "config_info" "udev:/sys/devices/virtual/misc/vboxguest"
[    37.809] (II) XINPUT: Adding extended input device "(unnamed)" (type: MOUSE)
[    37.809] (**) (unnamed): (accel) keeping acceleration scheme 1
[    37.809] (**) (unnamed): (accel) acceleration profile 0
[    37.809] (**) (unnamed): (accel) acceleration factor: 2.000
[    37.809] (**) (unnamed): (accel) acceleration threshold: 4
[    37.809] (II) (unnamed): On.
[   157.257] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[   157.258] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1280x960 Warning: We only handle separate sync.
[   157.258] (II) VBoxVideo(0): Using hsync ranges from config file
[   157.258] (II) VBoxVideo(0): Using vrefresh ranges from config file
[   157.258] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[   157.258] (II) VBoxVideo(0): Modeline "1280x960"x0.0   74.53  1280 1282 1284 1286  960 962 964 966 -hsync -vsync (58.0 kHz)
[   157.266] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[   157.266] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1280x960 Warning: We only handle separate sync.
[   157.266] (II) VBoxVideo(0): Using hsync ranges from config file
[   157.266] (II) VBoxVideo(0): Using vrefresh ranges from config file
[   157.267] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[   157.267] (II) VBoxVideo(0): Modeline "1280x960"x0.0   74.53  1280 1282 1284 1286  960 962 964 966 -hsync -vsync (58.0 kHz)
[   157.274] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[   157.274] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1280x960 Warning: We only handle separate sync.
[   157.274] (II) VBoxVideo(0): Using hsync ranges from config file
[   157.274] (II) VBoxVideo(0): Using vrefresh ranges from config file
[   157.274] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[   157.274] (II) VBoxVideo(0): Modeline "1280x960"x0.0   74.53  1280 1282 1284 1286  960 962 964 966 -hsync -vsync (58.0 kHz)
[   157.281] (II) VBoxVideo(0): EDID vendor "VBX", prod id 0
[   157.281] (II) VBoxVideo(0): DDCModeFromDetailedTiming: 1280x960 Warning: We only handle separate sync.
[   157.281] (II) VBoxVideo(0): Using hsync ranges from config file
[   157.281] (II) VBoxVideo(0): Using vrefresh ranges from config file
[   157.281] (II) VBoxVideo(0): Printing DDC gathered Modelines:
[   157.281] (II) VBoxVideo(0): Modeline "1280x960"x0.0   74.53  1280 1282 1284 1286  960 962 964 966 -hsync -vsync (58.0 kHz)
[   162.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-58118CAC4FF2A02B3A940F3A7A58FD5C451401BC.xkm
paul@oneiric:~$ 
```

HTH

---

### Post by lucazade on 2011-06-17
@paul_in_london
great!
going to spot the differences :)

---

### Post by paul_in_london on 2011-06-17
@lucazade

Sorry, I forgot to mention that I'm also using the **ricotz** ppa and I still have the **gnome3-team** ppa enabled at the moment.

---

### Post by pressureman on 2011-06-18
I just did a clean install in VirtualBox from a daily ISO from June 17, and even after installing gnome-session, Gnome Shell would not start (it fell back to Gnome Panel) until I installed gnome-themes-standard package.

Applications menu is still borked though... as in... empty.

---

### Post by lucazade on 2011-06-18
> **pressureman said:**
> I just did a clean install in VirtualBox from a daily ISO from June 17, and even after installing gnome-session, Gnome Shell would not start (it fell back to Gnome Panel) until I installed gnome-themes-standard package.

Applications menu is still borked though... as in... empty.

I tried almost everything to make GS work in vbox.. always same results, doesn't work because Vbox driver doesn't provide OpenGl extension, at least here.

I've installed GuestAdditions from both /usr/share/Virtualbox/guestaddtions.iso (don't recall exact name), from Restricted Hardware and using virtualbox-guest-additions package available in repos. 

Finished ideas and fantasia.. ;)

---

### Post by paul_in_london on 2011-06-21
@lucazade: Just to clarify, it's been working fine for me since Natty on a Win XP host but I haven't been able to get it working properly so far on an Ubuntu (OO) host even after removing the ose guest additions and using the standard ones.

G-S loads ok initially, but the panel crashes randomly even if I don't click on it so it's not usable.

Btw (slightly off-topic I know), on a fresh install of OO the G-S **Applications** window does not show any of the installed apps - although they're accessible via the CLI or via the ALT+F2 dialog etc.

If I come up with anything I'll let you know! :)

---

### Post by pressureman on 2011-06-28
I just tried installing the latest VirtualBox 4.0.10 directly from Oracle. Gnome3 client support was supposedly added in 4.0.8, and 4.0.10 makes it work on MacOS hosts too.

Sadly, my Oneiric guest is still falling back to gnome-panel... and I'm not brave enough to actually install Oneiric on real hardware yet.

---

### Post by lucazade on 2011-06-28
> **pressureman said:**
> I just tried installing the latest VirtualBox 4.0.10 directly from Oracle. Gnome3 client support was supposedly added in 4.0.8, and 4.0.10 makes it work on MacOS hosts too.

Sadly, my Oneiric guest is still falling back to gnome-panel... and I'm not brave enough to actually install Oneiric on real hardware yet.

I tried 4.0.10 as well, opengl and 3d are stil broken here, so no unity, compiz and gshell.
IIRC well webupd8 author said the problem was due to some xorg updates came out after alpha1.

---

### Post by MacUntu on 2011-06-28
Maybe that's why Unity won't run on Nouveau. !:****-)

---


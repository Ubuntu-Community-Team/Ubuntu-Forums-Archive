---
title: "Unable to set desired graphics resolution"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fhd on 2011-07-30
Hi,

I've set up Oneiric to get started with Ubuntu development. However, I can't get it to use my desired graphics resolution. Works fine on Natty.

Here's xrandr's output from Natty:

```

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```

And here from Oneiric:

```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 800 x 600, maximum 1024 x 768
default connected 800x600+0+0 0mm x 0mm
   1024x768        0.0  
   800x600        61.0* 

```

I've tried to set the resolution with xrandr, but all I get is an error message:

```

$ xrandr --newmode "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
xrandr: Failed to get size of gamma for output default
$ xrandr --addmode default 1024x600_60.00
xrandr: Failed to get size of gamma for output default
$ xrandr --output default --mode 1024x600_60.00
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

What can I do about these problems?

PS:
grub uses the resolution 1024x768 (instead of 1024x600 as on Natty) for some reason, but I could live with that.

---

### Post by lucazade on 2011-07-31
What gfx card is?
If you post /var/log/Xorg.0.log we can look into it and if you provide also this log of natty we could make a comparision :)

---

### Post by fhd on 2011-07-31
> **lucazade said:**
> What gfx card is?
If you post /var/log/Xorg.0.log we can look into it and if you provide also this log of natty we could make a comparision :)

Sorry, forgot to tell you the graphics card model, it's an Intel N10:

```

$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

```

Here is /var/log/Xorg.0.log from Oneiric:

```

[    17.924] 
X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[    17.924] X Protocol Version 11, Revision 0
[    17.924] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    17.925] Current Operating System: Linux ixion 3.0.0-7-generic #8-Ubuntu SMP Fri Jul 22 20:24:22 UTC 2011 i686
[    17.925] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=81121aa0-2c37-4de0-93cc-d445fdd56ef8 ro nomodeset
[    17.925] Build Date: 13 July 2011  12:18:21AM
[    17.925] xorg-server 2:1.10.2.902-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[    17.925] Current version of pixman: 0.22.2
[    17.925] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.925] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.925] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 31 09:33:47 2011
[    17.944] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.945] (==) No Layout section.  Using the first Screen section.
[    17.945] (==) No screen section available. Using defaults.
[    17.945] (**) |-->Screen "Default Screen Section" (0)
[    17.945] (**) |   |-->Monitor "<default monitor>"
[    17.946] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    17.946] (==) Automatically adding devices
[    17.946] (==) Automatically enabling devices
[    17.947] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.947] 	Entry deleted from font path.
[    17.947] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.947] 	Entry deleted from font path.
[    17.947] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.947] 	Entry deleted from font path.
[    17.947] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.947] 	Entry deleted from font path.
[    17.947] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.947] 	Entry deleted from font path.
[    17.947] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    17.947] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.947] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.947] (II) Loader magic: 0x8239da0
[    17.947] (II) Module ABI versions:
[    17.947] 	X.Org ANSI C Emulation: 0.4
[    17.947] 	X.Org Video Driver: 10.0
[    17.947] 	X.Org XInput driver : 12.3
[    17.947] 	X.Org Server Extension : 5.0
[    17.949] (--) PCI:*(0:0:2:0) 8086:a011:1b7d:0002 rev 0, Mem @ 0x58180000/524288, 0x40000000/268435456, 0x58000000/1048576, I/O @ 0x000060c0/8
[    17.950] (--) PCI: (0:0:2:1) 8086:a012:1b7d:0002 rev 0, Mem @ 0x58100000/524288
[    17.950] (II) Open ACPI successful (/var/run/acpid.socket)
[    17.950] (II) LoadModule: "extmod"
[    17.969] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.969] (II) Module extmod: vendor="X.Org Foundation"
[    17.969] 	compiled for 1.10.2.902, module version = 1.0.0
[    17.969] 	Module class: X.Org Server Extension
[    17.969] 	ABI class: X.Org Server Extension, version 5.0
[    17.970] (II) Loading extension MIT-SCREEN-SAVER
[    17.970] (II) Loading extension XFree86-VidModeExtension
[    17.970] (II) Loading extension XFree86-DGA
[    17.970] (II) Loading extension DPMS
[    17.970] (II) Loading extension XVideo
[    17.970] (II) Loading extension XVideo-MotionCompensation
[    17.970] (II) Loading extension X-Resource
[    17.970] (II) LoadModule: "dbe"
[    17.970] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.970] (II) Module dbe: vendor="X.Org Foundation"
[    17.970] 	compiled for 1.10.2.902, module version = 1.0.0
[    17.971] 	Module class: X.Org Server Extension
[    17.971] 	ABI class: X.Org Server Extension, version 5.0
[    17.971] (II) Loading extension DOUBLE-BUFFER
[    17.971] (II) LoadModule: "glx"
[    17.971] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    17.971] (II) Module glx: vendor="X.Org Foundation"
[    17.971] 	compiled for 1.10.2.902, module version = 1.0.0
[    17.971] 	ABI class: X.Org Server Extension, version 5.0
[    17.971] (==) AIGLX enabled
[    17.971] (II) Loading extension GLX
[    17.972] (II) LoadModule: "record"
[    17.972] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    17.972] (II) Module record: vendor="X.Org Foundation"
[    17.972] 	compiled for 1.10.2.902, module version = 1.13.0
[    17.972] 	Module class: X.Org Server Extension
[    17.972] 	ABI class: X.Org Server Extension, version 5.0
[    17.972] (II) Loading extension RECORD
[    17.972] (II) LoadModule: "dri"
[    17.973] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    17.973] (II) Module dri: vendor="X.Org Foundation"
[    17.973] 	compiled for 1.10.2.902, module version = 1.0.0
[    17.973] 	ABI class: X.Org Server Extension, version 5.0
[    17.973] (II) Loading extension XFree86-DRI
[    17.973] (II) LoadModule: "dri2"
[    17.974] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.974] (II) Module dri2: vendor="X.Org Foundation"
[    17.974] 	compiled for 1.10.2.902, module version = 1.2.0
[    17.974] 	ABI class: X.Org Server Extension, version 5.0
[    17.974] (II) Loading extension DRI2
[    17.974] (==) Matched intel as autoconfigured driver 0
[    17.974] (==) Matched vesa as autoconfigured driver 1
[    17.974] (==) Matched fbdev as autoconfigured driver 2
[    17.974] (==) Assigned the driver to the xf86ConfigLayout
[    17.974] (II) LoadModule: "intel"
[    17.976] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    17.976] (II) Module intel: vendor="X.Org Foundation"
[    17.976] 	compiled for 1.10.2, module version = 2.15.0
[    17.976] 	Module class: X.Org Video Driver
[    17.976] 	ABI class: X.Org Video Driver, version 10.0
[    17.976] (II) LoadModule: "vesa"
[    17.977] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.977] (II) Module vesa: vendor="X.Org Foundation"
[    17.978] 	compiled for 1.10.2, module version = 2.3.0
[    17.978] 	Module class: X.Org Video Driver
[    17.978] 	ABI class: X.Org Video Driver, version 10.0
[    17.978] (II) LoadModule: "fbdev"
[    17.978] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    17.979] (II) Module fbdev: vendor="X.Org Foundation"
[    17.979] 	compiled for 1.10.0, module version = 0.4.2
[    17.979] 	ABI class: X.Org Video Driver, version 10.0
[    17.979] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    17.980] (II) VESA: driver for VESA chipsets: vesa
[    17.980] (II) FBDEV: driver for framebuffer: fbdev
[    17.980] (++) using VT number 7

[    17.980] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    17.980] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    17.986] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    17.986] (WW) Falling back to old probe method for fbdev
[    17.986] (II) Loading sub module "fbdevhw"
[    17.986] (II) LoadModule: "fbdevhw"
[    17.987] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    17.987] (II) Module fbdevhw: vendor="X.Org Foundation"
[    17.987] 	compiled for 1.10.2.902, module version = 0.0.2
[    17.987] 	ABI class: X.Org Video Driver, version 10.0
[    17.987] (EE) open /dev/fb0: No such file or directory
[    18.125] (II) Loading sub module "vbe"
[    18.125] (II) LoadModule: "vbe"
[    18.358] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    18.358] (II) Module vbe: vendor="X.Org Foundation"
[    18.358] 	compiled for 1.10.2.902, module version = 1.1.0
[    18.358] 	ABI class: X.Org Video Driver, version 10.0
[    18.358] (II) Loading sub module "int10"
[    18.358] (II) LoadModule: "int10"
[    18.359] (II) Loading /usr/lib/xorg/modules/libint10.so
[    18.359] (II) Module int10: vendor="X.Org Foundation"
[    18.359] 	compiled for 1.10.2.902, module version = 1.0.0
[    18.359] 	ABI class: X.Org Video Driver, version 10.0
[    18.359] (II) VESA(0): initializing int10
[    18.360] (II) VESA(0): Bad V_BIOS checksum
[    18.360] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    18.361] (II) VESA(0): VESA BIOS detected
[    18.361] (II) VESA(0): VESA VBE Version 3.0
[    18.361] (II) VESA(0): VESA VBE Total Mem: 8128 kB
[    18.361] (II) VESA(0): VESA VBE OEM: Intel(r)PineView Graphics Chip Accelerated VGA BIOS
[    18.361] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    18.361] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    18.361] (II) VESA(0): VESA VBE OEM Product: Intel(r)PineView Graphics Controller
[    18.361] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    18.384] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    18.384] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    18.384] (==) VESA(0): RGB weight 888
[    18.384] (==) VESA(0): Default visual is TrueColor
[    18.384] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.384] (II) Loading sub module "ddc"
[    18.384] (II) LoadModule: "ddc"
[    18.384] (II) Module "ddc" already built-in
[    18.421] (II) VESA(0): VESA VBE DDC supported
[    18.421] (II) VESA(0): VESA VBE DDC Level none
[    18.421] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[    18.422] (II) VESA(0): VESA VBE DDC read failed
[    18.423] (II) VESA(0): VESA VBE PanelID read successfully
[    18.423] (II) VESA(0): PanelID returned panel resolution 1024x768
[    18.423] (II) VESA(0): Searching for matching VESA mode(s):
[    18.423] Mode: 160 (0x0)
[    18.423] 	ModeAttributes: 0x0
[    18.423] 	WinAAttributes: 0x0
[    18.424] 	WinBAttributes: 0x0
[    18.424] 	WinGranularity: 0
[    18.424] 	WinSize: 0
[    18.424] 	WinASegment: 0x0
[    18.424] 	WinBSegment: 0x0
[    18.424] 	WinFuncPtr: 0x0
[    18.424] 	BytesPerScanline: 0
[    18.424] 	XResolution: 0
[    18.424] 	YResolution: 0
[    18.424] 	XCharSize: 0
[    18.424] 	YCharSize: 0
[    18.424] 	NumberOfPlanes: 0
[    18.424] 	BitsPerPixel: 0
[    18.424] 	NumberOfBanks: 0
[    18.424] 	MemoryModel: 0
[    18.424] 	BankSize: 0
[    18.425] 	NumberOfImages: 0
[    18.425] 	RedMaskSize: 0
[    18.425] 	RedFieldPosition: 0
[    18.425] 	GreenMaskSize: 0
[    18.425] 	GreenFieldPosition: 0
[    18.425] 	BlueMaskSize: 0
[    18.425] 	BlueFieldPosition: 0
[    18.425] 	RsvdMaskSize: 0
[    18.425] 	RsvdFieldPosition: 0
[    18.425] 	DirectColorModeInfo: 0
[    18.425] 	PhysBasePtr: 0x0
[    18.425] 	LinBytesPerScanLine: 0
[    18.425] 	BnkNumberOfImagePages: 0
[    18.425] 	LinNumberOfImagePages: 0
[    18.425] 	LinRedMaskSize: 0
[    18.425] 	LinRedFieldPosition: 0
[    18.425] 	LinGreenMaskSize: 0
[    18.425] 	LinGreenFieldPosition: 0
[    18.425] 	LinBlueMaskSize: 0
[    18.425] 	LinBlueFieldPosition: 0
[    18.425] 	LinRsvdMaskSize: 0
[    18.426] 	LinRsvdFieldPosition: 0
[    18.426] 	MaxPixelClock: 0
[    18.426] Mode: 161 (0x0)
[    18.426] 	ModeAttributes: 0x0
[    18.426] 	WinAAttributes: 0x0
[    18.426] 	WinBAttributes: 0x0
[    18.426] 	WinGranularity: 0
[    18.427] 	WinSize: 0
[    18.427] 	WinASegment: 0x0
[    18.427] 	WinBSegment: 0x0
[    18.427] 	WinFuncPtr: 0x0
[    18.427] 	BytesPerScanline: 0
[    18.427] 	XResolution: 0
[    18.427] 	YResolution: 0
[    18.427] 	XCharSize: 0
[    18.427] 	YCharSize: 0
[    18.427] 	NumberOfPlanes: 0
[    18.427] 	BitsPerPixel: 0
[    18.427] 	NumberOfBanks: 0
[    18.427] 	MemoryModel: 0
[    18.427] 	BankSize: 0
[    18.427] 	NumberOfImages: 0
[    18.427] 	RedMaskSize: 0
[    18.427] 	RedFieldPosition: 0
[    18.427] 	GreenMaskSize: 0
[    18.427] 	GreenFieldPosition: 0
[    18.428] 	BlueMaskSize: 0
[    18.428] 	BlueFieldPosition: 0
[    18.428] 	RsvdMaskSize: 0
[    18.428] 	RsvdFieldPosition: 0
[    18.428] 	DirectColorModeInfo: 0
[    18.428] 	PhysBasePtr: 0x0
[    18.428] 	LinBytesPerScanLine: 0
[    18.428] 	BnkNumberOfImagePages: 0
[    18.428] 	LinNumberOfImagePages: 0
[    18.428] 	LinRedMaskSize: 0
[    18.428] 	LinRedFieldPosition: 0
[    18.428] 	LinGreenMaskSize: 0
[    18.428] 	LinGreenFieldPosition: 0
[    18.428] 	LinBlueMaskSize: 0
[    18.428] 	LinBlueFieldPosition: 0
[    18.428] 	LinRsvdMaskSize: 0
[    18.428] 	LinRsvdFieldPosition: 0
[    18.428] 	MaxPixelClock: 0
[    18.429] Mode: 162 (0x0)
[    18.429] 	ModeAttributes: 0x0
[    18.429] 	WinAAttributes: 0x0
[    18.429] 	WinBAttributes: 0x0
[    18.429] 	WinGranularity: 0
[    18.429] 	WinSize: 0
[    18.429] 	WinASegment: 0x0
[    18.429] 	WinBSegment: 0x0
[    18.430] 	WinFuncPtr: 0x0
[    18.430] 	BytesPerScanline: 0
[    18.430] 	XResolution: 0
[    18.430] 	YResolution: 0
[    18.430] 	XCharSize: 0
[    18.430] 	YCharSize: 0
[    18.430] 	NumberOfPlanes: 0
[    18.430] 	BitsPerPixel: 0
[    18.430] 	NumberOfBanks: 0
[    18.430] 	MemoryModel: 0
[    18.430] 	BankSize: 0
[    18.430] 	NumberOfImages: 0
[    18.430] 	RedMaskSize: 0
[    18.430] 	RedFieldPosition: 0
[    18.430] 	GreenMaskSize: 0
[    18.430] 	GreenFieldPosition: 0
[    18.430] 	BlueMaskSize: 0
[    18.430] 	BlueFieldPosition: 0
[    18.430] 	RsvdMaskSize: 0
[    18.430] 	RsvdFieldPosition: 0
[    18.431] 	DirectColorModeInfo: 0
[    18.431] 	PhysBasePtr: 0x0
[    18.431] 	LinBytesPerScanLine: 0
[    18.431] 	BnkNumberOfImagePages: 0
[    18.431] 	LinNumberOfImagePages: 0
[    18.431] 	LinRedMaskSize: 0
[    18.431] 	LinRedFieldPosition: 0
[    18.431] 	LinGreenMaskSize: 0
[    18.431] 	LinGreenFieldPosition: 0
[    18.431] 	LinBlueMaskSize: 0
[    18.431] 	LinBlueFieldPosition: 0
[    18.431] 	LinRsvdMaskSize: 0
[    18.431] 	LinRsvdFieldPosition: 0
[    18.431] 	MaxPixelClock: 0
[    18.432] Mode: 163 (0x0)
[    18.432] 	ModeAttributes: 0x0
[    18.432] 	WinAAttributes: 0x0
[    18.432] 	WinBAttributes: 0x0
[    18.432] 	WinGranularity: 0
[    18.432] 	WinSize: 0
[    18.432] 	WinASegment: 0x0
[    18.432] 	WinBSegment: 0x0
[    18.432] 	WinFuncPtr: 0x0
[    18.432] 	BytesPerScanline: 0
[    18.432] 	XResolution: 0
[    18.432] 	YResolution: 0
[    18.432] 	XCharSize: 0
[    18.432] 	YCharSize: 0
[    18.432] 	NumberOfPlanes: 0
[    18.432] 	BitsPerPixel: 0
[    18.432] 	NumberOfBanks: 0
[    18.432] 	MemoryModel: 0
[    18.432] 	BankSize: 0
[    18.432] 	NumberOfImages: 0
[    18.433] 	RedMaskSize: 0
[    18.433] 	RedFieldPosition: 0
[    18.433] 	GreenMaskSize: 0
[    18.433] 	GreenFieldPosition: 0
[    18.433] 	BlueMaskSize: 0
[    18.433] 	BlueFieldPosition: 0
[    18.433] 	RsvdMaskSize: 0
[    18.433] 	RsvdFieldPosition: 0
[    18.433] 	DirectColorModeInfo: 0
[    18.433] 	PhysBasePtr: 0x0
[    18.433] 	LinBytesPerScanLine: 0
[    18.433] 	BnkNumberOfImagePages: 0
[    18.433] 	LinNumberOfImagePages: 0
[    18.433] 	LinRedMaskSize: 0
[    18.433] 	LinRedFieldPosition: 0
[    18.433] 	LinGreenMaskSize: 0
[    18.433] 	LinGreenFieldPosition: 0
[    18.433] 	LinBlueMaskSize: 0
[    18.433] 	LinBlueFieldPosition: 0
[    18.433] 	LinRsvdMaskSize: 0
[    18.433] 	LinRsvdFieldPosition: 0
[    18.434] 	MaxPixelClock: 0
[    18.434] Mode: 164 (0x0)
[    18.434] 	ModeAttributes: 0x0
[    18.434] 	WinAAttributes: 0x0
[    18.434] 	WinBAttributes: 0x0
[    18.434] 	WinGranularity: 0
[    18.434] 	WinSize: 0
[    18.435] 	WinASegment: 0x0
[    18.435] 	WinBSegment: 0x0
[    18.435] 	WinFuncPtr: 0x0
[    18.435] 	BytesPerScanline: 0
[    18.435] 	XResolution: 0
[    18.435] 	YResolution: 0
[    18.435] 	XCharSize: 0
[    18.435] 	YCharSize: 0
[    18.435] 	NumberOfPlanes: 0
[    18.435] 	BitsPerPixel: 0
[    18.435] 	NumberOfBanks: 0
[    18.435] 	MemoryModel: 0
[    18.435] 	BankSize: 0
[    18.435] 	NumberOfImages: 0
[    18.435] 	RedMaskSize: 0
[    18.435] 	RedFieldPosition: 0
[    18.435] 	GreenMaskSize: 0
[    18.435] 	GreenFieldPosition: 0
[    18.435] 	BlueMaskSize: 0
[    18.435] 	BlueFieldPosition: 0
[    18.436] 	RsvdMaskSize: 0
[    18.436] 	RsvdFieldPosition: 0
[    18.436] 	DirectColorModeInfo: 0
[    18.436] 	PhysBasePtr: 0x0
[    18.436] 	LinBytesPerScanLine: 0
[    18.436] 	BnkNumberOfImagePages: 0
[    18.436] 	LinNumberOfImagePages: 0
[    18.436] 	LinRedMaskSize: 0
[    18.436] 	LinRedFieldPosition: 0
[    18.436] 	LinGreenMaskSize: 0
[    18.436] 	LinGreenFieldPosition: 0
[    18.436] 	LinBlueMaskSize: 0
[    18.436] 	LinBlueFieldPosition: 0
[    18.436] 	LinRsvdMaskSize: 0
[    18.436] 	LinRsvdFieldPosition: 0
[    18.436] 	MaxPixelClock: 0
[    18.437] Mode: 165 (0x0)
[    18.437] 	ModeAttributes: 0x0
[    18.437] 	WinAAttributes: 0x0
[    18.437] 	WinBAttributes: 0x0
[    18.437] 	WinGranularity: 0
[    18.437] 	WinSize: 0
[    18.437] 	WinASegment: 0x0
[    18.437] 	WinBSegment: 0x0
[    18.437] 	WinFuncPtr: 0x0
[    18.437] 	BytesPerScanline: 0
[    18.438] 	XResolution: 0
[    18.438] 	YResolution: 0
[    18.438] 	XCharSize: 0
[    18.438] 	YCharSize: 0
[    18.438] 	NumberOfPlanes: 0
[    18.438] 	BitsPerPixel: 0
[    18.438] 	NumberOfBanks: 0
[    18.438] 	MemoryModel: 0
[    18.438] 	BankSize: 0
[    18.438] 	NumberOfImages: 0
[    18.438] 	RedMaskSize: 0
[    18.438] 	RedFieldPosition: 0
[    18.438] 	GreenMaskSize: 0
[    18.438] 	GreenFieldPosition: 0
[    18.438] 	BlueMaskSize: 0
[    18.438] 	BlueFieldPosition: 0
[    18.438] 	RsvdMaskSize: 0
[    18.438] 	RsvdFieldPosition: 0
[    18.438] 	DirectColorModeInfo: 0
[    18.438] 	PhysBasePtr: 0x0
[    18.438] 	LinBytesPerScanLine: 0
[    18.439] 	BnkNumberOfImagePages: 0
[    18.439] 	LinNumberOfImagePages: 0
[    18.439] 	LinRedMaskSize: 0
[    18.439] 	LinRedFieldPosition: 0
[    18.439] 	LinGreenMaskSize: 0
[    18.439] 	LinGreenFieldPosition: 0
[    18.439] 	LinBlueMaskSize: 0
[    18.439] 	LinBlueFieldPosition: 0
[    18.439] 	LinRsvdMaskSize: 0
[    18.439] 	LinRsvdFieldPosition: 0
[    18.439] 	MaxPixelClock: 0
[    18.440] Mode: 166 (0x0)
[    18.440] 	ModeAttributes: 0x0
[    18.440] 	WinAAttributes: 0x0
[    18.440] 	WinBAttributes: 0x0
[    18.440] 	WinGranularity: 0
[    18.440] 	WinSize: 0
[    18.440] 	WinASegment: 0x0
[    18.440] 	WinBSegment: 0x0
[    18.440] 	WinFuncPtr: 0x0
[    18.440] 	BytesPerScanline: 0
[    18.440] 	XResolution: 0
[    18.440] 	YResolution: 0
[    18.440] 	XCharSize: 0
[    18.440] 	YCharSize: 0
[    18.441] 	NumberOfPlanes: 0
[    18.441] 	BitsPerPixel: 0
[    18.441] 	NumberOfBanks: 0
[    18.441] 	MemoryModel: 0
[    18.441] 	BankSize: 0
[    18.441] 	NumberOfImages: 0
[    18.441] 	RedMaskSize: 0
[    18.441] 	RedFieldPosition: 0
[    18.441] 	GreenMaskSize: 0
[    18.441] 	GreenFieldPosition: 0
[    18.441] 	BlueMaskSize: 0
[    18.441] 	BlueFieldPosition: 0
[    18.441] 	RsvdMaskSize: 0
[    18.441] 	RsvdFieldPosition: 0
[    18.441] 	DirectColorModeInfo: 0
[    18.441] 	PhysBasePtr: 0x0
[    18.441] 	LinBytesPerScanLine: 0
[    18.441] 	BnkNumberOfImagePages: 0
[    18.441] 	LinNumberOfImagePages: 0
[    18.441] 	LinRedMaskSize: 0
[    18.441] 	LinRedFieldPosition: 0
[    18.441] 	LinGreenMaskSize: 0
[    18.441] 	LinGreenFieldPosition: 0
[    18.442] 	LinBlueMaskSize: 0
[    18.442] 	LinBlueFieldPosition: 0
[    18.442] 	LinRsvdMaskSize: 0
[    18.442] 	LinRsvdFieldPosition: 0
[    18.442] 	MaxPixelClock: 0
[    18.442] Mode: 167 (0x0)
[    18.442] 	ModeAttributes: 0x0
[    18.442] 	WinAAttributes: 0x0
[    18.443] 	WinBAttributes: 0x0
[    18.443] 	WinGranularity: 0
[    18.443] 	WinSize: 0
[    18.443] 	WinASegment: 0x0
[    18.443] 	WinBSegment: 0x0
[    18.443] 	WinFuncPtr: 0x0
[    18.443] 	BytesPerScanline: 0
[    18.443] 	XResolution: 0
[    18.443] 	YResolution: 0
[    18.443] 	XCharSize: 0
[    18.443] 	YCharSize: 0
[    18.443] 	NumberOfPlanes: 0
[    18.443] 	BitsPerPixel: 0
[    18.443] 	NumberOfBanks: 0
[    18.443] 	MemoryModel: 0
[    18.443] 	BankSize: 0
[    18.443] 	NumberOfImages: 0
[    18.443] 	RedMaskSize: 0
[    18.443] 	RedFieldPosition: 0
[    18.443] 	GreenMaskSize: 0
[    18.443] 	GreenFieldPosition: 0
[    18.443] 	BlueMaskSize: 0
[    18.443] 	BlueFieldPosition: 0
[    18.443] 	RsvdMaskSize: 0
[    18.444] 	RsvdFieldPosition: 0
[    18.444] 	DirectColorModeInfo: 0
[    18.444] 	PhysBasePtr: 0x0
[    18.444] 	LinBytesPerScanLine: 0
[    18.444] 	BnkNumberOfImagePages: 0
[    18.444] 	LinNumberOfImagePages: 0
[    18.444] 	LinRedMaskSize: 0
[    18.444] 	LinRedFieldPosition: 0
[    18.444] 	LinGreenMaskSize: 0
[    18.444] 	LinGreenFieldPosition: 0
[    18.444] 	LinBlueMaskSize: 0
[    18.444] 	LinBlueFieldPosition: 0
[    18.444] 	LinRsvdMaskSize: 0
[    18.444] 	LinRsvdFieldPosition: 0
[    18.444] 	MaxPixelClock: 0
[    18.445] Mode: 168 (0x0)
[    18.445] 	ModeAttributes: 0x0
[    18.445] 	WinAAttributes: 0x0
[    18.445] 	WinBAttributes: 0x0
[    18.445] 	WinGranularity: 0
[    18.445] 	WinSize: 0
[    18.445] 	WinASegment: 0x0
[    18.445] 	WinBSegment: 0x0
[    18.445] 	WinFuncPtr: 0x0
[    18.445] 	BytesPerScanline: 0
[    18.445] 	XResolution: 0
[    18.445] 	YResolution: 0
[    18.445] 	XCharSize: 0
[    18.446] 	YCharSize: 0
[    18.446] 	NumberOfPlanes: 0
[    18.446] 	BitsPerPixel: 0
[    18.446] 	NumberOfBanks: 0
[    18.446] 	MemoryModel: 0
[    18.446] 	BankSize: 0
[    18.446] 	NumberOfImages: 0
[    18.446] 	RedMaskSize: 0
[    18.446] 	RedFieldPosition: 0
[    18.446] 	GreenMaskSize: 0
[    18.446] 	GreenFieldPosition: 0
[    18.446] 	BlueMaskSize: 0
[    18.446] 	BlueFieldPosition: 0
[    18.446] 	RsvdMaskSize: 0
[    18.447] 	RsvdFieldPosition: 0
[    18.447] 	DirectColorModeInfo: 0
[    18.447] 	PhysBasePtr: 0x0
[    18.447] 	LinBytesPerScanLine: 0
[    18.447] 	BnkNumberOfImagePages: 0
[    18.447] 	LinNumberOfImagePages: 0
[    18.447] 	LinRedMaskSize: 0
[    18.447] 	LinRedFieldPosition: 0
[    18.447] 	LinGreenMaskSize: 0
[    18.447] 	LinGreenFieldPosition: 0
[    18.447] 	LinBlueMaskSize: 0
[    18.447] 	LinBlueFieldPosition: 0
[    18.447] 	LinRsvdMaskSize: 0
[    18.447] 	LinRsvdFieldPosition: 0
[    18.447] 	MaxPixelClock: 0
[    18.448] Mode: 169 (0x0)
[    18.448] 	ModeAttributes: 0x0
[    18.448] 	WinAAttributes: 0x0
[    18.448] 	WinBAttributes: 0x0
[    18.448] 	WinGranularity: 0
[    18.448] 	WinSize: 0
[    18.448] 	WinASegment: 0x0
[    18.448] 	WinBSegment: 0x0
[    18.449] 	WinFuncPtr: 0x0
[    18.449] 	BytesPerScanline: 0
[    18.449] 	XResolution: 0
[    18.449] 	YResolution: 0
[    18.449] 	XCharSize: 0
[    18.449] 	YCharSize: 0
[    18.449] 	NumberOfPlanes: 0
[    18.449] 	BitsPerPixel: 0
[    18.449] 	NumberOfBanks: 0
[    18.449] 	MemoryModel: 0
[    18.449] 	BankSize: 0
[    18.449] 	NumberOfImages: 0
[    18.449] 	RedMaskSize: 0
[    18.449] 	RedFieldPosition: 0
[    18.449] 	GreenMaskSize: 0
[    18.449] 	GreenFieldPosition: 0
[    18.449] 	BlueMaskSize: 0
[    18.449] 	BlueFieldPosition: 0
[    18.449] 	RsvdMaskSize: 0
[    18.449] 	RsvdFieldPosition: 0
[    18.449] 	DirectColorModeInfo: 0
[    18.449] 	PhysBasePtr: 0x0
[    18.450] 	LinBytesPerScanLine: 0
[    18.450] 	BnkNumberOfImagePages: 0
[    18.450] 	LinNumberOfImagePages: 0
[    18.450] 	LinRedMaskSize: 0
[    18.450] 	LinRedFieldPosition: 0
[    18.450] 	LinGreenMaskSize: 0
[    18.450] 	LinGreenFieldPosition: 0
[    18.450] 	LinBlueMaskSize: 0
[    18.450] 	LinBlueFieldPosition: 0
[    18.450] 	LinRsvdMaskSize: 0
[    18.450] 	LinRsvdFieldPosition: 0
[    18.450] 	MaxPixelClock: 0
[    18.451] Mode: 16a (0x0)
[    18.451] 	ModeAttributes: 0x0
[    18.451] 	WinAAttributes: 0x0
[    18.451] 	WinBAttributes: 0x0
[    18.451] 	WinGranularity: 0
[    18.451] 	WinSize: 0
[    18.451] 	WinASegment: 0x0
[    18.451] 	WinBSegment: 0x0
[    18.451] 	WinFuncPtr: 0x0
[    18.451] 	BytesPerScanline: 0
[    18.452] 	XResolution: 0
[    18.452] 	YResolution: 0
[    18.452] 	XCharSize: 0
[    18.452] 	YCharSize: 0
[    18.452] 	NumberOfPlanes: 0
[    18.452] 	BitsPerPixel: 0
[    18.452] 	NumberOfBanks: 0
[    18.452] 	MemoryModel: 0
[    18.452] 	BankSize: 0
[    18.452] 	NumberOfImages: 0
[    18.452] 	RedMaskSize: 0
[    18.452] 	RedFieldPosition: 0
[    18.452] 	GreenMaskSize: 0
[    18.452] 	GreenFieldPosition: 0
[    18.452] 	BlueMaskSize: 0
[    18.452] 	BlueFieldPosition: 0
[    18.452] 	RsvdMaskSize: 0
[    18.452] 	RsvdFieldPosition: 0
[    18.452] 	DirectColorModeInfo: 0
[    18.452] 	PhysBasePtr: 0x0
[    18.453] 	LinBytesPerScanLine: 0
[    18.453] 	BnkNumberOfImagePages: 0
[    18.453] 	LinNumberOfImagePages: 0
[    18.453] 	LinRedMaskSize: 0
[    18.453] 	LinRedFieldPosition: 0
[    18.453] 	LinGreenMaskSize: 0
[    18.453] 	LinGreenFieldPosition: 0
[    18.453] 	LinBlueMaskSize: 0
[    18.453] 	LinBlueFieldPosition: 0
[    18.453] 	LinRsvdMaskSize: 0
[    18.453] 	LinRsvdFieldPosition: 0
[    18.453] 	MaxPixelClock: 0
[    18.454] Mode: 16b (0x0)
[    18.454] 	ModeAttributes: 0x0
[    18.454] 	WinAAttributes: 0x0
[    18.454] 	WinBAttributes: 0x0
[    18.454] 	WinGranularity: 0
[    18.454] 	WinSize: 0
[    18.454] 	WinASegment: 0x0
[    18.454] 	WinBSegment: 0x0
[    18.455] 	WinFuncPtr: 0x0
[    18.455] 	BytesPerScanline: 0
[    18.455] 	XResolution: 0
[    18.455] 	YResolution: 0
[    18.455] 	XCharSize: 0
[    18.455] 	YCharSize: 0
[    18.455] 	NumberOfPlanes: 0
[    18.455] 	BitsPerPixel: 0
[    18.455] 	NumberOfBanks: 0
[    18.455] 	MemoryModel: 0
[    18.455] 	BankSize: 0
[    18.455] 	NumberOfImages: 0
[    18.455] 	RedMaskSize: 0
[    18.455] 	RedFieldPosition: 0
[    18.455] 	GreenMaskSize: 0
[    18.455] 	GreenFieldPosition: 0
[    18.455] 	BlueMaskSize: 0
[    18.455] 	BlueFieldPosition: 0
[    18.455] 	RsvdMaskSize: 0
[    18.456] 	RsvdFieldPosition: 0
[    18.456] 	DirectColorModeInfo: 0
[    18.456] 	PhysBasePtr: 0x0
[    18.456] 	LinBytesPerScanLine: 0
[    18.456] 	BnkNumberOfImagePages: 0
[    18.456] 	LinNumberOfImagePages: 0
[    18.456] 	LinRedMaskSize: 0
[    18.456] 	LinRedFieldPosition: 0
[    18.456] 	LinGreenMaskSize: 0
[    18.456] 	LinGreenFieldPosition: 0
[    18.456] 	LinBlueMaskSize: 0
[    18.456] 	LinBlueFieldPosition: 0
[    18.456] 	LinRsvdMaskSize: 0
[    18.456] 	LinRsvdFieldPosition: 0
[    18.456] 	MaxPixelClock: 0
[    18.457] Mode: 16c (0x0)
[    18.457] 	ModeAttributes: 0x0
[    18.457] 	WinAAttributes: 0x0
[    18.457] 	WinBAttributes: 0x0
[    18.457] 	WinGranularity: 0
[    18.457] 	WinSize: 0
[    18.457] 	WinASegment: 0x0
[    18.457] 	WinBSegment: 0x0
[    18.457] 	WinFuncPtr: 0x0
[    18.457] 	BytesPerScanline: 0
[    18.458] 	XResolution: 0
[    18.458] 	YResolution: 0
[    18.458] 	XCharSize: 0
[    18.458] 	YCharSize: 0
[    18.458] 	NumberOfPlanes: 0
[    18.458] 	BitsPerPixel: 0
[    18.458] 	NumberOfBanks: 0
[    18.458] 	MemoryModel: 0
[    18.458] 	BankSize: 0
[    18.458] 	NumberOfImages: 0
[    18.458] 	RedMaskSize: 0
[    18.458] 	RedFieldPosition: 0
[    18.458] 	GreenMaskSize: 0
[    18.458] 	GreenFieldPosition: 0
[    18.458] 	BlueMaskSize: 0
[    18.458] 	BlueFieldPosition: 0
[    18.458] 	RsvdMaskSize: 0
[    18.458] 	RsvdFieldPosition: 0
[    18.458] 	DirectColorModeInfo: 0
[    18.458] 	PhysBasePtr: 0x0
[    18.458] 	LinBytesPerScanLine: 0
[    18.458] 	BnkNumberOfImagePages: 0
[    18.458] 	LinNumberOfImagePages: 0
[    18.459] 	LinRedMaskSize: 0
[    18.459] 	LinRedFieldPosition: 0
[    18.459] 	LinGreenMaskSize: 0
[    18.459] 	LinGreenFieldPosition: 0
[    18.459] 	LinBlueMaskSize: 0
[    18.459] 	LinBlueFieldPosition: 0
[    18.459] 	LinRsvdMaskSize: 0
[    18.459] 	LinRsvdFieldPosition: 0
[    18.459] 	MaxPixelClock: 0
[    18.460] Mode: 16d (0x0)
[    18.460] 	ModeAttributes: 0x0
[    18.460] 	WinAAttributes: 0x0
[    18.460] 	WinBAttributes: 0x0
[    18.460] 	WinGranularity: 0
[    18.460] 	WinSize: 0
[    18.460] 	WinASegment: 0x0
[    18.460] 	WinBSegment: 0x0
[    18.460] 	WinFuncPtr: 0x0
[    18.460] 	BytesPerScanline: 0
[    18.460] 	XResolution: 0
[    18.461] 	YResolution: 0
[    18.461] 	XCharSize: 0
[    18.461] 	YCharSize: 0
[    18.461] 	NumberOfPlanes: 0
[    18.461] 	BitsPerPixel: 0
[    18.461] 	NumberOfBanks: 0
[    18.461] 	MemoryModel: 0
[    18.461] 	BankSize: 0
[    18.461] 	NumberOfImages: 0
[    18.461] 	RedMaskSize: 0
[    18.461] 	RedFieldPosition: 0
[    18.461] 	GreenMaskSize: 0
[    18.461] 	GreenFieldPosition: 0
[    18.461] 	BlueMaskSize: 0
[    18.461] 	BlueFieldPosition: 0
[    18.461] 	RsvdMaskSize: 0
[    18.461] 	RsvdFieldPosition: 0
[    18.461] 	DirectColorModeInfo: 0
[    18.461] 	PhysBasePtr: 0x0
[    18.461] 	LinBytesPerScanLine: 0
[    18.461] 	BnkNumberOfImagePages: 0
[    18.461] 	LinNumberOfImagePages: 0
[    18.462] 	LinRedMaskSize: 0
[    18.462] 	LinRedFieldPosition: 0
[    18.462] 	LinGreenMaskSize: 0
[    18.462] 	LinGreenFieldPosition: 0
[    18.462] 	LinBlueMaskSize: 0
[    18.462] 	LinBlueFieldPosition: 0
[    18.462] 	LinRsvdMaskSize: 0
[    18.462] 	LinRsvdFieldPosition: 0
[    18.462] 	MaxPixelClock: 0
[    18.463] Mode: 16e (0x0)
[    18.463] 	ModeAttributes: 0x0
[    18.463] 	WinAAttributes: 0x0
[    18.463] 	WinBAttributes: 0x0
[    18.463] 	WinGranularity: 0
[    18.463] 	WinSize: 0
[    18.463] 	WinASegment: 0x0
[    18.463] 	WinBSegment: 0x0
[    18.463] 	WinFuncPtr: 0x0
[    18.463] 	BytesPerScanline: 0
[    18.463] 	XResolution: 0
[    18.463] 	YResolution: 0
[    18.463] 	XCharSize: 0
[    18.463] 	YCharSize: 0
[    18.463] 	NumberOfPlanes: 0
[    18.463] 	BitsPerPixel: 0
[    18.464] 	NumberOfBanks: 0
[    18.464] 	MemoryModel: 0
[    18.464] 	BankSize: 0
[    18.464] 	NumberOfImages: 0
[    18.464] 	RedMaskSize: 0
[    18.464] 	RedFieldPosition: 0
[    18.464] 	GreenMaskSize: 0
[    18.464] 	GreenFieldPosition: 0
[    18.464] 	BlueMaskSize: 0
[    18.464] 	BlueFieldPosition: 0
[    18.464] 	RsvdMaskSize: 0
[    18.464] 	RsvdFieldPosition: 0
[    18.464] 	DirectColorModeInfo: 0
[    18.464] 	PhysBasePtr: 0x0
[    18.464] 	LinBytesPerScanLine: 0
[    18.464] 	BnkNumberOfImagePages: 0
[    18.464] 	LinNumberOfImagePages: 0
[    18.464] 	LinRedMaskSize: 0
[    18.464] 	LinRedFieldPosition: 0
[    18.464] 	LinGreenMaskSize: 0
[    18.465] 	LinGreenFieldPosition: 0
[    18.465] 	LinBlueMaskSize: 0
[    18.465] 	LinBlueFieldPosition: 0
[    18.465] 	LinRsvdMaskSize: 0
[    18.465] 	LinRsvdFieldPosition: 0
[    18.465] 	MaxPixelClock: 0
[    18.466] Mode: 16f (0x0)
[    18.466] 	ModeAttributes: 0x0
[    18.466] 	WinAAttributes: 0x0
[    18.466] 	WinBAttributes: 0x0
[    18.466] 	WinGranularity: 0
[    18.466] 	WinSize: 0
[    18.466] 	WinASegment: 0x0
[    18.466] 	WinBSegment: 0x0
[    18.466] 	WinFuncPtr: 0x0
[    18.466] 	BytesPerScanline: 0
[    18.466] 	XResolution: 0
[    18.466] 	YResolution: 0
[    18.466] 	XCharSize: 0
[    18.466] 	YCharSize: 0
[    18.466] 	NumberOfPlanes: 0
[    18.466] 	BitsPerPixel: 0
[    18.466] 	NumberOfBanks: 0
[    18.466] 	MemoryModel: 0
[    18.466] 	BankSize: 0
[    18.466] 	NumberOfImages: 0
[    18.466] 	RedMaskSize: 0
[    18.466] 	RedFieldPosition: 0
[    18.466] 	GreenMaskSize: 0
[    18.466] 	GreenFieldPosition: 0
[    18.466] 	BlueMaskSize: 0
[    18.467] 	BlueFieldPosition: 0
[    18.467] 	RsvdMaskSize: 0
[    18.467] 	RsvdFieldPosition: 0
[    18.467] 	DirectColorModeInfo: 0
[    18.467] 	PhysBasePtr: 0x0
[    18.467] 	LinBytesPerScanLine: 0
[    18.467] 	BnkNumberOfImagePages: 0
[    18.467] 	LinNumberOfImagePages: 0
[    18.467] 	LinRedMaskSize: 0
[    18.467] 	LinRedFieldPosition: 0
[    18.467] 	LinGreenMaskSize: 0
[    18.467] 	LinGreenFieldPosition: 0
[    18.467] 	LinBlueMaskSize: 0
[    18.467] 	LinBlueFieldPosition: 0
[    18.467] 	LinRsvdMaskSize: 0
[    18.467] 	LinRsvdFieldPosition: 0
[    18.467] 	MaxPixelClock: 0
[    18.468] Mode: 170 (0x0)
[    18.468] 	ModeAttributes: 0x0
[    18.468] 	WinAAttributes: 0x0
[    18.468] 	WinBAttributes: 0x0
[    18.468] 	WinGranularity: 0
[    18.468] 	WinSize: 0
[    18.468] 	WinASegment: 0x0
[    18.468] 	WinBSegment: 0x0
[    18.468] 	WinFuncPtr: 0x0
[    18.468] 	BytesPerScanline: 0
[    18.468] 	XResolution: 0
[    18.468] 	YResolution: 0
[    18.468] 	XCharSize: 0
[    18.468] 	YCharSize: 0
[    18.468] 	NumberOfPlanes: 0
[    18.468] 	BitsPerPixel: 0
[    18.468] 	NumberOfBanks: 0
[    18.468] 	MemoryModel: 0
[    18.468] 	BankSize: 0
[    18.468] 	NumberOfImages: 0
[    18.468] 	RedMaskSize: 0
[    18.468] 	RedFieldPosition: 0
[    18.468] 	GreenMaskSize: 0
[    18.468] 	GreenFieldPosition: 0
[    18.468] 	BlueMaskSize: 0
[    18.468] 	BlueFieldPosition: 0
[    18.469] 	RsvdMaskSize: 0
[    18.469] 	RsvdFieldPosition: 0
[    18.469] 	DirectColorModeInfo: 0
[    18.469] 	PhysBasePtr: 0x0
[    18.469] 	LinBytesPerScanLine: 0
[    18.469] 	BnkNumberOfImagePages: 0
[    18.469] 	LinNumberOfImagePages: 0
[    18.469] 	LinRedMaskSize: 0
[    18.469] 	LinRedFieldPosition: 0
[    18.469] 	LinGreenMaskSize: 0
[    18.469] 	LinGreenFieldPosition: 0
[    18.469] 	LinBlueMaskSize: 0
[    18.469] 	LinBlueFieldPosition: 0
[    18.469] 	LinRsvdMaskSize: 0
[    18.469] 	LinRsvdFieldPosition: 0
[    18.469] 	MaxPixelClock: 0
[    18.470] Mode: 171 (0x0)
[    18.470] 	ModeAttributes: 0x0
[    18.470] 	WinAAttributes: 0x0
[    18.470] 	WinBAttributes: 0x0
[    18.470] 	WinGranularity: 0
[    18.470] 	WinSize: 0
[    18.470] 	WinASegment: 0x0
[    18.470] 	WinBSegment: 0x0
[    18.470] 	WinFuncPtr: 0x0
[    18.470] 	BytesPerScanline: 0
[    18.470] 	XResolution: 0
[    18.470] 	YResolution: 0
[    18.470] 	XCharSize: 0
[    18.470] 	YCharSize: 0
[    18.470] 	NumberOfPlanes: 0
[    18.470] 	BitsPerPixel: 0
[    18.470] 	NumberOfBanks: 0
[    18.470] 	MemoryModel: 0
[    18.470] 	BankSize: 0
[    18.470] 	NumberOfImages: 0
[    18.471] 	RedMaskSize: 0
[    18.471] 	RedFieldPosition: 0
[    18.471] 	GreenMaskSize: 0
[    18.471] 	GreenFieldPosition: 0
[    18.471] 	BlueMaskSize: 0
[    18.471] 	BlueFieldPosition: 0
[    18.471] 	RsvdMaskSize: 0
[    18.471] 	RsvdFieldPosition: 0
[    18.471] 	DirectColorModeInfo: 0
[    18.471] 	PhysBasePtr: 0x0
[    18.471] 	LinBytesPerScanLine: 0
[    18.471] 	BnkNumberOfImagePages: 0
[    18.471] 	LinNumberOfImagePages: 0
[    18.471] 	LinRedMaskSize: 0
[    18.471] 	LinRedFieldPosition: 0
[    18.471] 	LinGreenMaskSize: 0
[    18.471] 	LinGreenFieldPosition: 0
[    18.471] 	LinBlueMaskSize: 0
[    18.471] 	LinBlueFieldPosition: 0
[    18.471] 	LinRsvdMaskSize: 0
[    18.471] 	LinRsvdFieldPosition: 0
[    18.471] 	MaxPixelClock: 0
[    18.472] Mode: 13c (0x0)
[    18.472] 	ModeAttributes: 0x0
[    18.472] 	WinAAttributes: 0x0
[    18.472] 	WinBAttributes: 0x0
[    18.472] 	WinGranularity: 0
[    18.472] 	WinSize: 0
[    18.472] 	WinASegment: 0x0
[    18.472] 	WinBSegment: 0x0
[    18.472] 	WinFuncPtr: 0x0
[    18.472] 	BytesPerScanline: 0
[    18.472] 	XResolution: 0
[    18.472] 	YResolution: 0
[    18.472] 	XCharSize: 0
[    18.472] 	YCharSize: 0
[    18.472] 	NumberOfPlanes: 0
[    18.472] 	BitsPerPixel: 0
[    18.472] 	NumberOfBanks: 0
[    18.473] 	MemoryModel: 0
[    18.473] 	BankSize: 0
[    18.473] 	NumberOfImages: 0
[    18.473] 	RedMaskSize: 0
[    18.473] 	RedFieldPosition: 0
[    18.473] 	GreenMaskSize: 0
[    18.473] 	GreenFieldPosition: 0
[    18.473] 	BlueMaskSize: 0
[    18.473] 	BlueFieldPosition: 0
[    18.473] 	RsvdMaskSize: 0
[    18.473] 	RsvdFieldPosition: 0
[    18.473] 	DirectColorModeInfo: 0
[    18.473] 	PhysBasePtr: 0x0
[    18.473] 	LinBytesPerScanLine: 0
[    18.473] 	BnkNumberOfImagePages: 0
[    18.473] 	LinNumberOfImagePages: 0
[    18.473] 	LinRedMaskSize: 0
[    18.473] 	LinRedFieldPosition: 0
[    18.473] 	LinGreenMaskSize: 0
[    18.473] 	LinGreenFieldPosition: 0
[    18.473] 	LinBlueMaskSize: 0
[    18.473] 	LinBlueFieldPosition: 0
[    18.473] 	LinRsvdMaskSize: 0
[    18.473] 	LinRsvdFieldPosition: 0
[    18.473] 	MaxPixelClock: 0
[    18.474] Mode: 14d (0x0)
[    18.475] 	ModeAttributes: 0x0
[    18.475] 	WinAAttributes: 0x0
[    18.475] 	WinBAttributes: 0x0
[    18.475] 	WinGranularity: 0
[    18.475] 	WinSize: 0
[    18.475] 	WinASegment: 0x0
[    18.475] 	WinBSegment: 0x0
[    18.475] 	WinFuncPtr: 0x0
[    18.475] 	BytesPerScanline: 0
[    18.475] 	XResolution: 0
[    18.475] 	YResolution: 0
[    18.475] 	XCharSize: 0
[    18.475] 	YCharSize: 0
[    18.475] 	NumberOfPlanes: 0
[    18.475] 	BitsPerPixel: 0
[    18.475] 	NumberOfBanks: 0
[    18.475] 	MemoryModel: 0
[    18.475] 	BankSize: 0
[    18.475] 	NumberOfImages: 0
[    18.475] 	RedMaskSize: 0
[    18.475] 	RedFieldPosition: 0
[    18.475] 	GreenMaskSize: 0
[    18.475] 	GreenFieldPosition: 0
[    18.475] 	BlueMaskSize: 0
[    18.475] 	BlueFieldPosition: 0
[    18.476] 	RsvdMaskSize: 0
[    18.476] 	RsvdFieldPosition: 0
[    18.476] 	DirectColorModeInfo: 0
[    18.476] 	PhysBasePtr: 0x0
[    18.476] 	LinBytesPerScanLine: 0
[    18.476] 	BnkNumberOfImagePages: 0
[    18.476] 	LinNumberOfImagePages: 0
[    18.476] 	LinRedMaskSize: 0
[    18.476] 	LinRedFieldPosition: 0
[    18.476] 	LinGreenMaskSize: 0
[    18.476] 	LinGreenFieldPosition: 0
[    18.476] 	LinBlueMaskSize: 0
[    18.476] 	LinBlueFieldPosition: 0
[    18.476] 	LinRsvdMaskSize: 0
[    18.476] 	LinRsvdFieldPosition: 0
[    18.476] 	MaxPixelClock: 0
[    18.477] Mode: 15c (0x0)
[    18.477] 	ModeAttributes: 0x0
[    18.477] 	WinAAttributes: 0x0
[    18.477] 	WinBAttributes: 0x0
[    18.477] 	WinGranularity: 0
[    18.477] 	WinSize: 0
[    18.477] 	WinASegment: 0x0
[    18.478] 	WinBSegment: 0x0
[    18.478] 	WinFuncPtr: 0x0
[    18.478] 	BytesPerScanline: 0
[    18.478] 	XResolution: 0
[    18.478] 	YResolution: 0
[    18.478] 	XCharSize: 0
[    18.478] 	YCharSize: 0
[    18.478] 	NumberOfPlanes: 0
[    18.478] 	BitsPerPixel: 0
[    18.478] 	NumberOfBanks: 0
[    18.478] 	MemoryModel: 0
[    18.478] 	BankSize: 0
[    18.478] 	NumberOfImages: 0
[    18.478] 	RedMaskSize: 0
[    18.478] 	RedFieldPosition: 0
[    18.478] 	GreenMaskSize: 0
[    18.478] 	GreenFieldPosition: 0
[    18.478] 	BlueMaskSize: 0
[    18.478] 	BlueFieldPosition: 0
[    18.478] 	RsvdMaskSize: 0
[    18.478] 	RsvdFieldPosition: 0
[    18.478] 	DirectColorModeInfo: 0
[    18.478] 	PhysBasePtr: 0x0
[    18.478] 	LinBytesPerScanLine: 0
[    18.478] 	BnkNumberOfImagePages: 0
[    18.479] 	LinNumberOfImagePages: 0
[    18.479] 	LinRedMaskSize: 0
[    18.479] 	LinRedFieldPosition: 0
[    18.479] 	LinGreenMaskSize: 0
[    18.479] 	LinGreenFieldPosition: 0
[    18.479] 	LinBlueMaskSize: 0
[    18.479] 	LinBlueFieldPosition: 0
[    18.479] 	LinRsvdMaskSize: 0
[    18.479] 	LinRsvdFieldPosition: 0
[    18.479] 	MaxPixelClock: 0
[    18.480] Mode: 13a (0x0)
[    18.480] 	ModeAttributes: 0x0
[    18.480] 	WinAAttributes: 0x0
[    18.480] 	WinBAttributes: 0x0
[    18.480] 	WinGranularity: 0
[    18.480] 	WinSize: 0
[    18.480] 	WinASegment: 0x0
[    18.480] 	WinBSegment: 0x0
[    18.480] 	WinFuncPtr: 0x0
[    18.480] 	BytesPerScanline: 0
[    18.480] 	XResolution: 0
[    18.480] 	YResolution: 0
[    18.480] 	XCharSize: 0
[    18.480] 	YCharSize: 0
[    18.480] 	NumberOfPlanes: 0
[    18.480] 	BitsPerPixel: 0
[    18.480] 	NumberOfBanks: 0
[    18.481] 	MemoryModel: 0
[    18.481] 	BankSize: 0
[    18.481] 	NumberOfImages: 0
[    18.481] 	RedMaskSize: 0
[    18.481] 	RedFieldPosition: 0
[    18.481] 	GreenMaskSize: 0
[    18.481] 	GreenFieldPosition: 0
[    18.481] 	BlueMaskSize: 0
[    18.481] 	BlueFieldPosition: 0
[    18.481] 	RsvdMaskSize: 0
[    18.481] 	RsvdFieldPosition: 0
[    18.481] 	DirectColorModeInfo: 0
[    18.481] 	PhysBasePtr: 0x0
[    18.481] 	LinBytesPerScanLine: 0
[    18.481] 	BnkNumberOfImagePages: 0
[    18.481] 	LinNumberOfImagePages: 0
[    18.481] 	LinRedMaskSize: 0
[    18.481] 	LinRedFieldPosition: 0
[    18.481] 	LinGreenMaskSize: 0
[    18.481] 	LinGreenFieldPosition: 0
[    18.481] 	LinBlueMaskSize: 0
[    18.492] 	LinBlueFieldPosition: 0
[    18.492] 	LinRsvdMaskSize: 0
[    18.492] 	LinRsvdFieldPosition: 0
[    18.492] 	MaxPixelClock: 0
[    18.492] Mode: 14b (0x0)
[    18.493] 	ModeAttributes: 0x0
[    18.493] 	WinAAttributes: 0x0
[    18.493] 	WinBAttributes: 0x0
[    18.493] 	WinGranularity: 0
[    18.493] 	WinSize: 0
[    18.493] 	WinASegment: 0x0
[    18.493] 	WinBSegment: 0x0
[    18.493] 	WinFuncPtr: 0x0
[    18.493] 	BytesPerScanline: 0
[    18.493] 	XResolution: 0
[    18.493] 	YResolution: 0
[    18.493] 	XCharSize: 0
[    18.493] 	YCharSize: 0
[    18.493] 	NumberOfPlanes: 0
[    18.493] 	BitsPerPixel: 0
[    18.493] 	NumberOfBanks: 0
[    18.493] 	MemoryModel: 0
[    18.493] 	BankSize: 0
[    18.493] 	NumberOfImages: 0
[    18.493] 	RedMaskSize: 0
[    18.493] 	RedFieldPosition: 0
[    18.493] 	GreenMaskSize: 0
[    18.493] 	GreenFieldPosition: 0
[    18.493] 	BlueMaskSize: 0
[    18.493] 	BlueFieldPosition: 0
[    18.493] 	RsvdMaskSize: 0
[    18.493] 	RsvdFieldPosition: 0
[    18.493] 	DirectColorModeInfo: 0
[    18.493] 	PhysBasePtr: 0x0
[    18.493] 	LinBytesPerScanLine: 0
[    18.493] 	BnkNumberOfImagePages: 0
[    18.493] 	LinNumberOfImagePages: 0
[    18.493] 	LinRedMaskSize: 0
[    18.493] 	LinRedFieldPosition: 0
[    18.493] 	LinGreenMaskSize: 0
[    18.493] 	LinGreenFieldPosition: 0
[    18.494] 	LinBlueMaskSize: 0
[    18.494] 	LinBlueFieldPosition: 0
[    18.494] 	LinRsvdMaskSize: 0
[    18.494] 	LinRsvdFieldPosition: 0
[    18.494] 	MaxPixelClock: 0
[    18.494] Mode: 15a (0x0)
[    18.494] 	ModeAttributes: 0x0
[    18.494] 	WinAAttributes: 0x0
[    18.494] 	WinBAttributes: 0x0
[    18.495] 	WinGranularity: 0
[    18.495] 	WinSize: 0
[    18.495] 	WinASegment: 0x0
[    18.495] 	WinBSegment: 0x0
[    18.495] 	WinFuncPtr: 0x0
[    18.495] 	BytesPerScanline: 0
[    18.495] 	XResolution: 0
[    18.495] 	YResolution: 0
[    18.495] 	XCharSize: 0
[    18.495] 	YCharSize: 0
[    18.495] 	NumberOfPlanes: 0
[    18.495] 	BitsPerPixel: 0
[    18.495] 	NumberOfBanks: 0
[    18.495] 	MemoryModel: 0
[    18.495] 	BankSize: 0
[    18.495] 	NumberOfImages: 0
[    18.495] 	RedMaskSize: 0
[    18.495] 	RedFieldPosition: 0
[    18.495] 	GreenMaskSize: 0
[    18.495] 	GreenFieldPosition: 0
[    18.495] 	BlueMaskSize: 0
[    18.495] 	BlueFieldPosition: 0
[    18.495] 	RsvdMaskSize: 0
[    18.495] 	RsvdFieldPosition: 0
[    18.495] 	DirectColorModeInfo: 0
[    18.495] 	PhysBasePtr: 0x0
[    18.495] 	LinBytesPerScanLine: 0
[    18.495] 	BnkNumberOfImagePages: 0
[    18.495] 	LinNumberOfImagePages: 0
[    18.495] 	LinRedMaskSize: 0
[    18.495] 	LinRedFieldPosition: 0
[    18.495] 	LinGreenMaskSize: 0
[    18.495] 	LinGreenFieldPosition: 0
[    18.495] 	LinBlueMaskSize: 0
[    18.495] 	LinBlueFieldPosition: 0
[    18.495] 	LinRsvdMaskSize: 0
[    18.495] 	LinRsvdFieldPosition: 0
[    18.495] 	MaxPixelClock: 0
[    18.496] Mode: 107 (0x0)
[    18.496] 	ModeAttributes: 0x0
[    18.496] 	WinAAttributes: 0x0
[    18.496] 	WinBAttributes: 0x0
[    18.496] 	WinGranularity: 0
[    18.496] 	WinSize: 0
[    18.496] 	WinASegment: 0x0
[    18.496] 	WinBSegment: 0x0
[    18.496] 	WinFuncPtr: 0x0
[    18.496] 	BytesPerScanline: 0
[    18.496] 	XResolution: 0
[    18.496] 	YResolution: 0
[    18.496] 	XCharSize: 0
[    18.496] 	YCharSize: 0
[    18.497] 	NumberOfPlanes: 0
[    18.497] 	BitsPerPixel: 0
[    18.497] 	NumberOfBanks: 0
[    18.497] 	MemoryModel: 0
[    18.497] 	BankSize: 0
[    18.497] 	NumberOfImages: 0
[    18.497] 	RedMaskSize: 0
[    18.497] 	RedFieldPosition: 0
[    18.497] 	GreenMaskSize: 0
[    18.497] 	GreenFieldPosition: 0
[    18.497] 	BlueMaskSize: 0
[    18.497] 	BlueFieldPosition: 0
[    18.497] 	RsvdMaskSize: 0
[    18.497] 	RsvdFieldPosition: 0
[    18.497] 	DirectColorModeInfo: 0
[    18.497] 	PhysBasePtr: 0x0
[    18.497] 	LinBytesPerScanLine: 0
[    18.497] 	BnkNumberOfImagePages: 0
[    18.497] 	LinNumberOfImagePages: 0
[    18.497] 	LinRedMaskSize: 0
[    18.497] 	LinRedFieldPosition: 0
[    18.497] 	LinGreenMaskSize: 0
[    18.497] 	LinGreenFieldPosition: 0
[    18.497] 	LinBlueMaskSize: 0
[    18.497] 	LinBlueFieldPosition: 0
[    18.497] 	LinRsvdMaskSize: 0
[    18.497] 	LinRsvdFieldPosition: 0
[    18.497] 	MaxPixelClock: 0
[    18.498] Mode: 11a (0x0)
[    18.498] 	ModeAttributes: 0x0
[    18.498] 	WinAAttributes: 0x0
[    18.498] 	WinBAttributes: 0x0
[    18.498] 	WinGranularity: 0
[    18.498] 	WinSize: 0
[    18.498] 	WinASegment: 0x0
[    18.498] 	WinBSegment: 0x0
[    18.498] 	WinFuncPtr: 0x0
[    18.498] 	BytesPerScanline: 0
[    18.498] 	XResolution: 0
[    18.498] 	YResolution: 0
[    18.498] 	XCharSize: 0
[    18.498] 	YCharSize: 0
[    18.498] 	NumberOfPlanes: 0
[    18.498] 	BitsPerPixel: 0
[    18.498] 	NumberOfBanks: 0
[    18.498] 	MemoryModel: 0
[    18.498] 	BankSize: 0
[    18.498] 	NumberOfImages: 0
[    18.498] 	RedMaskSize: 0
[    18.498] 	RedFieldPosition: 0
[    18.498] 	GreenMaskSize: 0
[    18.499] 	GreenFieldPosition: 0
[    18.499] 	BlueMaskSize: 0
[    18.499] 	BlueFieldPosition: 0
[    18.499] 	RsvdMaskSize: 0
[    18.499] 	RsvdFieldPosition: 0
[    18.499] 	DirectColorModeInfo: 0
[    18.499] 	PhysBasePtr: 0x0
[    18.499] 	LinBytesPerScanLine: 0
[    18.499] 	BnkNumberOfImagePages: 0
[    18.499] 	LinNumberOfImagePages: 0
[    18.499] 	LinRedMaskSize: 0
[    18.499] 	LinRedFieldPosition: 0
[    18.499] 	LinGreenMaskSize: 0
[    18.499] 	LinGreenFieldPosition: 0
[    18.499] 	LinBlueMaskSize: 0
[    18.499] 	LinBlueFieldPosition: 0
[    18.499] 	LinRsvdMaskSize: 0
[    18.499] 	LinRsvdFieldPosition: 0
[    18.499] 	MaxPixelClock: 0
[    18.504] Mode: 11b (0x0)
[    18.504] 	ModeAttributes: 0x0
[    18.504] 	WinAAttributes: 0x0
[    18.504] 	WinBAttributes: 0x0
[    18.504] 	WinGranularity: 0
[    18.504] 	WinSize: 0
[    18.504] 	WinASegment: 0x0
[    18.504] 	WinBSegment: 0x0
[    18.504] 	WinFuncPtr: 0x0
[    18.504] 	BytesPerScanline: 0
[    18.504] 	XResolution: 0
[    18.504] 	YResolution: 0
[    18.504] 	XCharSize: 0
[    18.504] 	YCharSize: 0
[    18.504] 	NumberOfPlanes: 0
[    18.504] 	BitsPerPixel: 0
[    18.504] 	NumberOfBanks: 0
[    18.504] 	MemoryModel: 0
[    18.504] 	BankSize: 0
[    18.504] 	NumberOfImages: 0
[    18.505] 	RedMaskSize: 0
[    18.505] 	RedFieldPosition: 0
[    18.505] 	GreenMaskSize: 0
[    18.505] 	GreenFieldPosition: 0
[    18.505] 	BlueMaskSize: 0
[    18.505] 	BlueFieldPosition: 0
[    18.505] 	RsvdMaskSize: 0
[    18.505] 	RsvdFieldPosition: 0
[    18.505] 	DirectColorModeInfo: 0
[    18.505] 	PhysBasePtr: 0x0
[    18.505] 	LinBytesPerScanLine: 0
[    18.505] 	BnkNumberOfImagePages: 0
[    18.505] 	LinNumberOfImagePages: 0
[    18.505] 	LinRedMaskSize: 0
[    18.505] 	LinRedFieldPosition: 0
[    18.505] 	LinGreenMaskSize: 0
[    18.505] 	LinGreenFieldPosition: 0
[    18.505] 	LinBlueMaskSize: 0
[    18.505] 	LinBlueFieldPosition: 0
[    18.505] 	LinRsvdMaskSize: 0
[    18.505] 	LinRsvdFieldPosition: 0
[    18.505] 	MaxPixelClock: 0
[    18.507] Mode: 105 (1024x768)
[    18.507] 	ModeAttributes: 0x9b
[    18.507] 	WinAAttributes: 0x7
[    18.507] 	WinBAttributes: 0x0
[    18.507] 	WinGranularity: 64
[    18.507] 	WinSize: 64
[    18.507] 	WinASegment: 0xa000
[    18.507] 	WinBSegment: 0x0
[    18.507] 	WinFuncPtr: 0xc0007a6d
[    18.507] 	BytesPerScanline: 1024
[    18.507] 	XResolution: 1024
[    18.507] 	YResolution: 768
[    18.507] 	XCharSize: 8
[    18.507] 	YCharSize: 16
[    18.508] 	NumberOfPlanes: 1
[    18.508] 	BitsPerPixel: 8
[    18.508] 	NumberOfBanks: 1
[    18.508] 	MemoryModel: 4
[    18.508] 	BankSize: 0
[    18.508] 	NumberOfImages: 9
[    18.508] 	RedMaskSize: 0
[    18.508] 	RedFieldPosition: 0
[    18.508] 	GreenMaskSize: 0
[    18.508] 	GreenFieldPosition: 0
[    18.508] 	BlueMaskSize: 0
[    18.508] 	BlueFieldPosition: 0
[    18.508] 	RsvdMaskSize: 0
[    18.508] 	RsvdFieldPosition: 0
[    18.508] 	DirectColorModeInfo: 0
[    18.508] 	PhysBasePtr: 0x40000000
[    18.508] 	LinBytesPerScanLine: 1024
[    18.508] 	BnkNumberOfImagePages: 9
[    18.508] 	LinNumberOfImagePages: 9
[    18.508] 	LinRedMaskSize: 0
[    18.508] 	LinRedFieldPosition: 0
[    18.508] 	LinGreenMaskSize: 0
[    18.508] 	LinGreenFieldPosition: 0
[    18.508] 	LinBlueMaskSize: 0
[    18.508] 	LinBlueFieldPosition: 0
[    18.508] 	LinRsvdMaskSize: 0
[    18.508] 	LinRsvdFieldPosition: 0
[    18.508] 	MaxPixelClock: 230000000
[    18.510] Mode: 117 (1024x768)
[    18.510] 	ModeAttributes: 0x9b
[    18.510] 	WinAAttributes: 0x7
[    18.510] 	WinBAttributes: 0x0
[    18.510] 	WinGranularity: 64
[    18.510] 	WinSize: 64
[    18.510] 	WinASegment: 0xa000
[    18.510] 	WinBSegment: 0x0
[    18.510] 	WinFuncPtr: 0xc0007a6d
[    18.510] 	BytesPerScanline: 2048
[    18.510] 	XResolution: 1024
[    18.510] 	YResolution: 768
[    18.510] 	XCharSize: 8
[    18.510] 	YCharSize: 16
[    18.510] 	NumberOfPlanes: 1
[    18.510] 	BitsPerPixel: 16
[    18.510] 	NumberOfBanks: 1
[    18.510] 	MemoryModel: 6
[    18.510] 	BankSize: 0
[    18.510] 	NumberOfImages: 4
[    18.510] 	RedMaskSize: 5
[    18.510] 	RedFieldPosition: 11
[    18.510] 	GreenMaskSize: 6
[    18.510] 	GreenFieldPosition: 5
[    18.511] 	BlueMaskSize: 5
[    18.511] 	BlueFieldPosition: 0
[    18.511] 	RsvdMaskSize: 0
[    18.511] 	RsvdFieldPosition: 0
[    18.511] 	DirectColorModeInfo: 0
[    18.511] 	PhysBasePtr: 0x40000000
[    18.511] 	LinBytesPerScanLine: 2048
[    18.511] 	BnkNumberOfImagePages: 4
[    18.511] 	LinNumberOfImagePages: 4
[    18.511] 	LinRedMaskSize: 5
[    18.511] 	LinRedFieldPosition: 11
[    18.511] 	LinGreenMaskSize: 6
[    18.511] 	LinGreenFieldPosition: 5
[    18.511] 	LinBlueMaskSize: 5
[    18.511] 	LinBlueFieldPosition: 0
[    18.511] 	LinRsvdMaskSize: 0
[    18.511] 	LinRsvdFieldPosition: 0
[    18.511] 	MaxPixelClock: 230000000
[    18.513] *Mode: 118 (1024x768)
[    18.513] 	ModeAttributes: 0x9b
[    18.513] 	WinAAttributes: 0x7
[    18.513] 	WinBAttributes: 0x0
[    18.513] 	WinGranularity: 64
[    18.513] 	WinSize: 64
[    18.513] 	WinASegment: 0xa000
[    18.513] 	WinBSegment: 0x0
[    18.513] 	WinFuncPtr: 0xc0007a6d
[    18.513] 	BytesPerScanline: 4096
[    18.513] 	XResolution: 1024
[    18.513] 	YResolution: 768
[    18.513] 	XCharSize: 8
[    18.513] 	YCharSize: 16
[    18.513] 	NumberOfPlanes: 1
[    18.513] 	BitsPerPixel: 32
[    18.513] 	NumberOfBanks: 1
[    18.513] 	MemoryModel: 6
[    18.513] 	BankSize: 0
[    18.513] 	NumberOfImages: 1
[    18.513] 	RedMaskSize: 8
[    18.513] 	RedFieldPosition: 16
[    18.513] 	GreenMaskSize: 8
[    18.513] 	GreenFieldPosition: 8
[    18.513] 	BlueMaskSize: 8
[    18.513] 	BlueFieldPosition: 0
[    18.513] 	RsvdMaskSize: 8
[    18.513] 	RsvdFieldPosition: 24
[    18.513] 	DirectColorModeInfo: 0
[    18.513] 	PhysBasePtr: 0x40000000
[    18.513] 	LinBytesPerScanLine: 4096
[    18.513] 	BnkNumberOfImagePages: 1
[    18.513] 	LinNumberOfImagePages: 1
[    18.513] 	LinRedMaskSize: 8
[    18.514] 	LinRedFieldPosition: 16
[    18.514] 	LinGreenMaskSize: 8
[    18.514] 	LinGreenFieldPosition: 8
[    18.514] 	LinBlueMaskSize: 8
[    18.514] 	LinBlueFieldPosition: 0
[    18.514] 	LinRsvdMaskSize: 8
[    18.514] 	LinRsvdFieldPosition: 24
[    18.514] 	MaxPixelClock: 230000000
[    18.515] *Mode: 112 (640x480)
[    18.515] 	ModeAttributes: 0x9b
[    18.515] 	WinAAttributes: 0x7
[    18.515] 	WinBAttributes: 0x0
[    18.515] 	WinGranularity: 64
[    18.515] 	WinSize: 64
[    18.515] 	WinASegment: 0xa000
[    18.515] 	WinBSegment: 0x0
[    18.515] 	WinFuncPtr: 0xc0007a6d
[    18.515] 	BytesPerScanline: 2560
[    18.515] 	XResolution: 640
[    18.515] 	YResolution: 480
[    18.516] 	XCharSize: 8
[    18.516] 	YCharSize: 16
[    18.516] 	NumberOfPlanes: 1
[    18.516] 	BitsPerPixel: 32
[    18.516] 	NumberOfBanks: 1
[    18.516] 	MemoryModel: 6
[    18.516] 	BankSize: 0
[    18.516] 	NumberOfImages: 5
[    18.516] 	RedMaskSize: 8
[    18.516] 	RedFieldPosition: 16
[    18.516] 	GreenMaskSize: 8
[    18.516] 	GreenFieldPosition: 8
[    18.516] 	BlueMaskSize: 8
[    18.516] 	BlueFieldPosition: 0
[    18.516] 	RsvdMaskSize: 8
[    18.516] 	RsvdFieldPosition: 24
[    18.516] 	DirectColorModeInfo: 0
[    18.516] 	PhysBasePtr: 0x40000000
[    18.516] 	LinBytesPerScanLine: 2560
[    18.516] 	BnkNumberOfImagePages: 5
[    18.516] 	LinNumberOfImagePages: 5
[    18.516] 	LinRedMaskSize: 8
[    18.516] 	LinRedFieldPosition: 16
[    18.516] 	LinGreenMaskSize: 8
[    18.516] 	LinGreenFieldPosition: 8
[    18.516] 	LinBlueMaskSize: 8
[    18.516] 	LinBlueFieldPosition: 0
[    18.516] 	LinRsvdMaskSize: 8
[    18.516] 	LinRsvdFieldPosition: 24
[    18.516] 	MaxPixelClock: 230000000
[    18.518] Mode: 114 (800x600)
[    18.518] 	ModeAttributes: 0x9b
[    18.518] 	WinAAttributes: 0x7
[    18.518] 	WinBAttributes: 0x0
[    18.518] 	WinGranularity: 64
[    18.518] 	WinSize: 64
[    18.518] 	WinASegment: 0xa000
[    18.518] 	WinBSegment: 0x0
[    18.518] 	WinFuncPtr: 0xc0007a6d
[    18.518] 	BytesPerScanline: 1600
[    18.518] 	XResolution: 800
[    18.518] 	YResolution: 600
[    18.518] 	XCharSize: 8
[    18.518] 	YCharSize: 16
[    18.518] 	NumberOfPlanes: 1
[    18.518] 	BitsPerPixel: 16
[    18.518] 	NumberOfBanks: 1
[    18.518] 	MemoryModel: 6
[    18.518] 	BankSize: 0
[    18.518] 	NumberOfImages: 7
[    18.518] 	RedMaskSize: 5
[    18.518] 	RedFieldPosition: 11
[    18.518] 	GreenMaskSize: 6
[    18.518] 	GreenFieldPosition: 5
[    18.518] 	BlueMaskSize: 5
[    18.518] 	BlueFieldPosition: 0
[    18.518] 	RsvdMaskSize: 0
[    18.518] 	RsvdFieldPosition: 0
[    18.518] 	DirectColorModeInfo: 0
[    18.518] 	PhysBasePtr: 0x40000000
[    18.518] 	LinBytesPerScanLine: 1600
[    18.518] 	BnkNumberOfImagePages: 7
[    18.518] 	LinNumberOfImagePages: 7
[    18.518] 	LinRedMaskSize: 5
[    18.519] 	LinRedFieldPosition: 11
[    18.519] 	LinGreenMaskSize: 6
[    18.519] 	LinGreenFieldPosition: 5
[    18.519] 	LinBlueMaskSize: 5
[    18.519] 	LinBlueFieldPosition: 0
[    18.519] 	LinRsvdMaskSize: 0
[    18.519] 	LinRsvdFieldPosition: 0
[    18.519] 	MaxPixelClock: 230000000
[    18.520] *Mode: 115 (800x600)
[    18.520] 	ModeAttributes: 0x9b
[    18.520] 	WinAAttributes: 0x7
[    18.520] 	WinBAttributes: 0x0
[    18.520] 	WinGranularity: 64
[    18.520] 	WinSize: 64
[    18.520] 	WinASegment: 0xa000
[    18.520] 	WinBSegment: 0x0
[    18.521] 	WinFuncPtr: 0xc0007a6d
[    18.521] 	BytesPerScanline: 3200
[    18.521] 	XResolution: 800
[    18.521] 	YResolution: 600
[    18.521] 	XCharSize: 8
[    18.521] 	YCharSize: 16
[    18.521] 	NumberOfPlanes: 1
[    18.521] 	BitsPerPixel: 32
[    18.521] 	NumberOfBanks: 1
[    18.521] 	MemoryModel: 6
[    18.521] 	BankSize: 0
[    18.521] 	NumberOfImages: 3
[    18.521] 	RedMaskSize: 8
[    18.521] 	RedFieldPosition: 16
[    18.521] 	GreenMaskSize: 8
[    18.521] 	GreenFieldPosition: 8
[    18.521] 	BlueMaskSize: 8
[    18.521] 	BlueFieldPosition: 0
[    18.521] 	RsvdMaskSize: 8
[    18.521] 	RsvdFieldPosition: 24
[    18.521] 	DirectColorModeInfo: 0
[    18.521] 	PhysBasePtr: 0x40000000
[    18.521] 	LinBytesPerScanLine: 3200
[    18.521] 	BnkNumberOfImagePages: 3
[    18.521] 	LinNumberOfImagePages: 3
[    18.521] 	LinRedMaskSize: 8
[    18.521] 	LinRedFieldPosition: 16
[    18.521] 	LinGreenMaskSize: 8
[    18.521] 	LinGreenFieldPosition: 8
[    18.521] 	LinBlueMaskSize: 8
[    18.521] 	LinBlueFieldPosition: 0
[    18.521] 	LinRsvdMaskSize: 8
[    18.521] 	LinRsvdFieldPosition: 24
[    18.521] 	MaxPixelClock: 230000000
[    18.522] Mode: 101 (640x480)
[    18.522] 	ModeAttributes: 0x9b
[    18.522] 	WinAAttributes: 0x7
[    18.522] 	WinBAttributes: 0x0
[    18.522] 	WinGranularity: 64
[    18.522] 	WinSize: 64
[    18.522] 	WinASegment: 0xa000
[    18.522] 	WinBSegment: 0x0
[    18.523] 	WinFuncPtr: 0xc0007a6d
[    18.523] 	BytesPerScanline: 640
[    18.523] 	XResolution: 640
[    18.523] 	YResolution: 480
[    18.523] 	XCharSize: 8
[    18.523] 	YCharSize: 16
[    18.523] 	NumberOfPlanes: 1
[    18.523] 	BitsPerPixel: 8
[    18.523] 	NumberOfBanks: 1
[    18.523] 	MemoryModel: 4
[    18.523] 	BankSize: 0
[    18.523] 	NumberOfImages: 24
[    18.523] 	RedMaskSize: 0
[    18.523] 	RedFieldPosition: 0
[    18.523] 	GreenMaskSize: 0
[    18.523] 	GreenFieldPosition: 0
[    18.523] 	BlueMaskSize: 0
[    18.523] 	BlueFieldPosition: 0
[    18.523] 	RsvdMaskSize: 0
[    18.523] 	RsvdFieldPosition: 0
[    18.523] 	DirectColorModeInfo: 0
[    18.523] 	PhysBasePtr: 0x40000000
[    18.523] 	LinBytesPerScanLine: 640
[    18.523] 	BnkNumberOfImagePages: 24
[    18.523] 	LinNumberOfImagePages: 24
[    18.523] 	LinRedMaskSize: 0
[    18.523] 	LinRedFieldPosition: 0
[    18.523] 	LinGreenMaskSize: 0
[    18.523] 	LinGreenFieldPosition: 0
[    18.523] 	LinBlueMaskSize: 0
[    18.523] 	LinBlueFieldPosition: 0
[    18.523] 	LinRsvdMaskSize: 0
[    18.523] 	LinRsvdFieldPosition: 0
[    18.523] 	MaxPixelClock: 230000000
[    18.524] Mode: 103 (800x600)
[    18.524] 	ModeAttributes: 0x9b
[    18.524] 	WinAAttributes: 0x7
[    18.525] 	WinBAttributes: 0x0
[    18.525] 	WinGranularity: 64
[    18.525] 	WinSize: 64
[    18.525] 	WinASegment: 0xa000
[    18.525] 	WinBSegment: 0x0
[    18.525] 	WinFuncPtr: 0xc0007a6d
[    18.525] 	BytesPerScanline: 832
[    18.525] 	XResolution: 800
[    18.525] 	YResolution: 600
[    18.525] 	XCharSize: 8
[    18.525] 	YCharSize: 16
[    18.525] 	NumberOfPlanes: 1
[    18.525] 	BitsPerPixel: 8
[    18.525] 	NumberOfBanks: 1
[    18.525] 	MemoryModel: 4
[    18.525] 	BankSize: 0
[    18.525] 	NumberOfImages: 14
[    18.525] 	RedMaskSize: 0
[    18.525] 	RedFieldPosition: 0
[    18.525] 	GreenMaskSize: 0
[    18.525] 	GreenFieldPosition: 0
[    18.525] 	BlueMaskSize: 0
[    18.525] 	BlueFieldPosition: 0
[    18.525] 	RsvdMaskSize: 0
[    18.525] 	RsvdFieldPosition: 0
[    18.525] 	DirectColorModeInfo: 0
[    18.525] 	PhysBasePtr: 0x40000000
[    18.525] 	LinBytesPerScanLine: 832
[    18.525] 	BnkNumberOfImagePages: 14
[    18.525] 	LinNumberOfImagePages: 14
[    18.525] 	LinRedMaskSize: 0
[    18.525] 	LinRedFieldPosition: 0
[    18.525] 	LinGreenMaskSize: 0
[    18.525] 	LinGreenFieldPosition: 0
[    18.525] 	LinBlueMaskSize: 0
[    18.525] 	LinBlueFieldPosition: 0
[    18.525] 	LinRsvdMaskSize: 0
[    18.526] 	LinRsvdFieldPosition: 0
[    18.526] 	MaxPixelClock: 230000000
[    18.527] Mode: 111 (640x480)
[    18.527] 	ModeAttributes: 0x9b
[    18.527] 	WinAAttributes: 0x7
[    18.527] 	WinBAttributes: 0x0
[    18.527] 	WinGranularity: 64
[    18.527] 	WinSize: 64
[    18.527] 	WinASegment: 0xa000
[    18.527] 	WinBSegment: 0x0
[    18.527] 	WinFuncPtr: 0xc0007a6d
[    18.527] 	BytesPerScanline: 1280
[    18.527] 	XResolution: 640
[    18.527] 	YResolution: 480
[    18.527] 	XCharSize: 8
[    18.527] 	YCharSize: 16
[    18.527] 	NumberOfPlanes: 1
[    18.527] 	BitsPerPixel: 16
[    18.527] 	NumberOfBanks: 1
[    18.527] 	MemoryModel: 6
[    18.527] 	BankSize: 0
[    18.527] 	NumberOfImages: 11
[    18.527] 	RedMaskSize: 5
[    18.527] 	RedFieldPosition: 11
[    18.527] 	GreenMaskSize: 6
[    18.527] 	GreenFieldPosition: 5
[    18.527] 	BlueMaskSize: 5
[    18.527] 	BlueFieldPosition: 0
[    18.527] 	RsvdMaskSize: 0
[    18.527] 	RsvdFieldPosition: 0
[    18.527] 	DirectColorModeInfo: 0
[    18.528] 	PhysBasePtr: 0x40000000
[    18.528] 	LinBytesPerScanLine: 1280
[    18.528] 	BnkNumberOfImagePages: 11
[    18.528] 	LinNumberOfImagePages: 11
[    18.528] 	LinRedMaskSize: 5
[    18.528] 	LinRedFieldPosition: 11
[    18.528] 	LinGreenMaskSize: 6
[    18.528] 	LinGreenFieldPosition: 5
[    18.528] 	LinBlueMaskSize: 5
[    18.528] 	LinBlueFieldPosition: 0
[    18.528] 	LinRsvdMaskSize: 0
[    18.528] 	LinRsvdFieldPosition: 0
[    18.528] 	MaxPixelClock: 230000000
[    18.528] 
[    18.528] (II) VESA(0): Total Memory: 127 64KB banks (8128kB)
[    18.528] (II) VESA(0): <default monitor>: Using hsync range of 31.50-47.30 kHz
[    18.528] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-59.87 Hz
[    18.528] (WW) VESA(0): Unable to estimate virtual size
[    18.528] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    18.528] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    18.528] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    18.528] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    18.528] (II) VESA(0): <default monitor>: Using hsync range of 31.50-47.30 kHz
[    18.528] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-59.87 Hz
[    18.528] (WW) VESA(0): Unable to estimate virtual size
[    18.529] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    18.529] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    18.529] (**) VESA(0): *Built-in mode "1024x768"
[    18.529] (**) VESA(0): *Built-in mode "800x600"
[    18.529] (==) VESA(0): DPI set to (96, 96)
[    18.529] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    18.535] (**) VESA(0): Using "Shadow Framebuffer"
[    18.535] (II) Loading sub module "shadow"
[    18.535] (II) LoadModule: "shadow"
[    18.536] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    18.536] (II) Module shadow: vendor="X.Org Foundation"
[    18.536] 	compiled for 1.10.2.902, module version = 1.1.0
[    18.536] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.536] (II) Loading sub module "fb"
[    18.536] (II) LoadModule: "fb"
[    18.537] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.537] (II) Module fb: vendor="X.Org Foundation"
[    18.537] 	compiled for 1.10.2.902, module version = 1.0.0
[    18.537] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.538] (II) UnloadModule: "fbdev"
[    18.538] (II) Unloading fbdev
[    18.538] (II) UnloadModule: "fbdevhw"
[    18.538] (II) Unloading fbdevhw
[    18.538] (==) Depth 24 pixmap format is 32 bpp
[    18.538] (II) Loading sub module "int10"
[    18.538] (II) LoadModule: "int10"
[    18.538] (II) Loading /usr/lib/xorg/modules/libint10.so
[    18.538] (II) Module int10: vendor="X.Org Foundation"
[    18.538] 	compiled for 1.10.2.902, module version = 1.0.0
[    18.538] 	ABI class: X.Org Video Driver, version 10.0
[    18.538] (II) VESA(0): initializing int10
[    18.539] (II) VESA(0): Bad V_BIOS checksum
[    18.539] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    18.540] (II) VESA(0): VESA BIOS detected
[    18.540] (II) VESA(0): VESA VBE Version 3.0
[    18.540] (II) VESA(0): VESA VBE Total Mem: 8128 kB
[    18.540] (II) VESA(0): VESA VBE OEM: Intel(r)PineView Graphics Chip Accelerated VGA BIOS
[    18.540] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    18.540] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    18.540] (II) VESA(0): VESA VBE OEM Product: Intel(r)PineView Graphics Controller
[    18.540] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    18.543] (II) VESA(0): virtual address = 0xb6e06000,
	physical address = 0x40000000, size = 8323072
[    18.562] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    18.661] (==) VESA(0): Default visual is TrueColor
[    18.662] (==) VESA(0): Backing store disabled
[    18.662] (==) VESA(0): DPMS enabled
[    18.662] (==) RandR enabled
[    18.662] (II) Initializing built-in extension Generic Event Extension
[    18.662] (II) Initializing built-in extension SHAPE
[    18.662] (II) Initializing built-in extension MIT-SHM
[    18.662] (II) Initializing built-in extension XInputExtension
[    18.662] (II) Initializing built-in extension XTEST
[    18.662] (II) Initializing built-in extension BIG-REQUESTS
[    18.662] (II) Initializing built-in extension SYNC
[    18.662] (II) Initializing built-in extension XKEYBOARD
[    18.662] (II) Initializing built-in extension XC-MISC
[    18.662] (II) Initializing built-in extension SECURITY
[    18.662] (II) Initializing built-in extension XINERAMA
[    18.662] (II) Initializing built-in extension XFIXES
[    18.662] (II) Initializing built-in extension RENDER
[    18.662] (II) Initializing built-in extension RANDR
[    18.662] (II) Initializing built-in extension COMPOSITE
[    18.662] (II) Initializing built-in extension DAMAGE
[    18.662] (II) Initializing built-in extension GESTURE
[    18.691] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.691] (II) AIGLX: Screen 0 is not DRI capable
[    18.691] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    18.701] (II) AIGLX: Loaded and initialized swrast
[    18.702] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.736] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.761] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.761] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.761] (II) LoadModule: "evdev"
[    18.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.764] (II) Module evdev: vendor="X.Org Foundation"
[    18.764] 	compiled for 1.10.2, module version = 2.6.0
[    18.764] 	Module class: X.Org XInput Driver
[    18.764] 	ABI class: X.Org XInput driver, version 12.3
[    18.764] (II) Using input driver 'evdev' for 'Power Button'
[    18.764] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.764] (**) Power Button: always reports core events
[    18.764] (**) Power Button: Device: "/dev/input/event2"
[    18.764] (--) Power Button: Found keys
[    18.764] (II) Power Button: Configuring as keyboard
[    18.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.764] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.765] (**) Option "xkb_rules" "evdev"
[    18.765] (**) Option "xkb_model" "pc105"
[    18.765] (**) Option "xkb_layout" "gb"
[    18.765] (**) Option "xkb_variant" "intl"
[    18.773] (II) XKB: reuse xkmfile /var/lib/xkb/server-4D45FCF9E775DF4D6C65C7F4AC1BB403C67FAAA1.xkm
[    18.777] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    18.777] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.777] (II) Using input driver 'evdev' for 'Video Bus'
[    18.777] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.777] (**) Video Bus: always reports core events
[    18.777] (**) Video Bus: Device: "/dev/input/event4"
[    18.777] (--) Video Bus: Found keys
[    18.777] (II) Video Bus: Configuring as keyboard
[    18.777] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    18.777] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.777] (**) Option "xkb_rules" "evdev"
[    18.777] (**) Option "xkb_model" "pc105"
[    18.777] (**) Option "xkb_layout" "gb"
[    18.778] (**) Option "xkb_variant" "intl"
[    18.793] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.793] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.793] (II) Using input driver 'evdev' for 'Power Button'
[    18.793] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.793] (**) Power Button: always reports core events
[    18.793] (**) Power Button: Device: "/dev/input/event0"
[    18.793] (--) Power Button: Found keys
[    18.793] (II) Power Button: Configuring as keyboard
[    18.793] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.794] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.794] (**) Option "xkb_rules" "evdev"
[    18.794] (**) Option "xkb_model" "pc105"
[    18.794] (**) Option "xkb_layout" "gb"
[    18.794] (**) Option "xkb_variant" "intl"
[    18.795] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    18.795] (II) No input driver/identifier specified (ignoring)
[    18.800] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event5)
[    18.800] (II) No input driver/identifier specified (ignoring)
[    18.801] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event6)
[    18.801] (II) No input driver/identifier specified (ignoring)
[    18.808] (II) config/udev: Adding input device Sunny 1.3M Webcam (/dev/input/event7)
[    18.808] (**) Sunny 1.3M Webcam: Applying InputClass "evdev keyboard catchall"
[    18.808] (II) Using input driver 'evdev' for 'Sunny 1.3M Webcam'
[    18.808] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.808] (**) Sunny 1.3M Webcam: always reports core events
[    18.808] (**) Sunny 1.3M Webcam: Device: "/dev/input/event7"
[    18.809] (--) Sunny 1.3M Webcam: Found keys
[    18.809] (II) Sunny 1.3M Webcam: Configuring as keyboard
[    18.809] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7/event7"
[    18.809] (II) XINPUT: Adding extended input device "Sunny 1.3M Webcam" (type: KEYBOARD)
[    18.809] (**) Option "xkb_rules" "evdev"
[    18.809] (**) Option "xkb_model" "pc105"
[    18.809] (**) Option "xkb_layout" "gb"
[    18.809] (**) Option "xkb_variant" "intl"
[    18.819] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    18.819] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.819] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.819] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.819] (**) AT Translated Set 2 keyboard: always reports core events
[    18.819] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    18.819] (--) AT Translated Set 2 keyboard: Found keys
[    18.819] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.819] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    18.819] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.820] (**) Option "xkb_rules" "evdev"
[    18.820] (**) Option "xkb_model" "pc105"
[    18.820] (**) Option "xkb_layout" "gb"
[    18.820] (**) Option "xkb_variant" "intl"
[    18.822] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    18.822] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.822] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.822] (II) LoadModule: "synaptics"
[    18.822] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.823] (II) Module synaptics: vendor="X.Org Foundation"
[    18.823] 	compiled for 1.10.2, module version = 1.4.1
[    18.823] 	Module class: X.Org XInput Driver
[    18.823] 	ABI class: X.Org XInput driver, version 12.3
[    18.823] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.823] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.823] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.823] (**) Option "Device" "/dev/input/event8"
[    18.823] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5382
[    18.823] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754
[    18.824] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.824] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.824] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.824] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.824] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.828] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    18.828] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    18.828] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.828] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    18.828] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.039
[    18.828] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.828] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.828] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.829] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.830] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    18.831] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    18.831] (II) No input driver/identifier specified (ignoring)
[    42.494] (II) VESA(0): Setting up VESA Mode 0x115 (800x600)
[    44.205] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A53EF37D77607CB32F418FF9A43E7B3D6A6FBBA.xkm

```

And here's the one from Natty:

```

[    19.862] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    19.863] X Protocol Version 11, Revision 0
[    19.863] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    19.863] Current Operating System: Linux orpheus 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686
[    19.863] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=01db63bc-7aee-47c0-9ecd-2a2f30dff9d1 ro quiet splash vga=771 vt.handoff=7
[    19.863] Build Date: 21 May 2011  11:38:35AM
[    19.863] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    19.863] Current version of pixman: 0.20.2
[    19.863] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.863] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.864] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 30 20:42:23 2011
[    19.874] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.875] (==) No Layout section.  Using the first Screen section.
[    19.875] (==) No screen section available. Using defaults.
[    19.875] (**) |-->Screen "Default Screen Section" (0)
[    19.875] (**) |   |-->Monitor "<default monitor>"
[    19.876] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    19.876] (==) Automatically adding devices
[    19.877] (==) Automatically enabling devices
[    19.877] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.877] 	Entry deleted from font path.
[    19.877] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    19.877] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.877] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.877] (II) Loader magic: 0x81ffde0
[    19.877] (II) Module ABI versions:
[    19.877] 	X.Org ANSI C Emulation: 0.4
[    19.877] 	X.Org Video Driver: 10.0
[    19.878] 	X.Org XInput driver : 12.3
[    19.878] 	X.Org Server Extension : 5.0
[    19.882] (--) PCI:*(0:0:2:0) 8086:a011:1b7d:0002 rev 0, Mem @ 0x58180000/524288, 0x40000000/268435456, 0x58000000/1048576, I/O @ 0x000060c0/8
[    19.882] (--) PCI: (0:0:2:1) 8086:a012:1b7d:0002 rev 0, Mem @ 0x58100000/524288
[    19.882] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    19.883] (II) LoadModule: "extmod"
[    19.899] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    19.901] (II) Module extmod: vendor="X.Org Foundation"
[    19.902] 	compiled for 1.10.1, module version = 1.0.0
[    19.902] 	Module class: X.Org Server Extension
[    19.902] 	ABI class: X.Org Server Extension, version 5.0
[    19.902] (II) Loading extension MIT-SCREEN-SAVER
[    19.902] (II) Loading extension XFree86-VidModeExtension
[    19.902] (II) Loading extension XFree86-DGA
[    19.902] (II) Loading extension DPMS
[    19.902] (II) Loading extension XVideo
[    19.902] (II) Loading extension XVideo-MotionCompensation
[    19.902] (II) Loading extension X-Resource
[    19.902] (II) LoadModule: "dbe"
[    19.903] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    19.904] (II) Module dbe: vendor="X.Org Foundation"
[    19.904] 	compiled for 1.10.1, module version = 1.0.0
[    19.904] 	Module class: X.Org Server Extension
[    19.904] 	ABI class: X.Org Server Extension, version 5.0
[    19.904] (II) Loading extension DOUBLE-BUFFER
[    19.904] (II) LoadModule: "glx"
[    19.905] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    19.906] (II) Module glx: vendor="X.Org Foundation"
[    19.906] 	compiled for 1.10.1, module version = 1.0.0
[    19.906] 	ABI class: X.Org Server Extension, version 5.0
[    19.906] (==) AIGLX enabled
[    19.906] (II) Loading extension GLX
[    19.906] (II) LoadModule: "record"
[    19.907] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.910] (II) Module record: vendor="X.Org Foundation"
[    19.910] 	compiled for 1.10.1, module version = 1.13.0
[    19.910] 	Module class: X.Org Server Extension
[    19.910] 	ABI class: X.Org Server Extension, version 5.0
[    19.910] (II) Loading extension RECORD
[    19.910] (II) LoadModule: "dri"
[    19.911] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.912] (II) Module dri: vendor="X.Org Foundation"
[    19.912] 	compiled for 1.10.1, module version = 1.0.0
[    19.912] 	ABI class: X.Org Server Extension, version 5.0
[    19.912] (II) Loading extension XFree86-DRI
[    19.912] (II) LoadModule: "dri2"
[    19.913] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.914] (II) Module dri2: vendor="X.Org Foundation"
[    19.914] 	compiled for 1.10.1, module version = 1.2.0
[    19.914] 	ABI class: X.Org Server Extension, version 5.0
[    19.914] (II) Loading extension DRI2
[    19.914] (==) Matched intel as autoconfigured driver 0
[    19.914] (==) Matched vesa as autoconfigured driver 1
[    19.914] (==) Matched fbdev as autoconfigured driver 2
[    19.914] (==) Assigned the driver to the xf86ConfigLayout
[    19.914] (II) LoadModule: "intel"
[    19.915] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.916] (II) Module intel: vendor="X.Org Foundation"
[    19.916] 	compiled for 1.10.1, module version = 2.14.0
[    19.916] 	Module class: X.Org Video Driver
[    19.916] 	ABI class: X.Org Video Driver, version 10.0
[    19.916] (II) LoadModule: "vesa"
[    19.917] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.917] (II) Module vesa: vendor="X.Org Foundation"
[    19.917] 	compiled for 1.10.0, module version = 2.3.0
[    19.917] 	Module class: X.Org Video Driver
[    19.917] 	ABI class: X.Org Video Driver, version 10.0
[    19.917] (II) LoadModule: "fbdev"
[    19.918] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.918] (II) Module fbdev: vendor="X.Org Foundation"
[    19.918] 	compiled for 1.10.0, module version = 0.4.2
[    19.918] 	ABI class: X.Org Video Driver, version 10.0
[    19.919] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    19.922] (II) VESA: driver for VESA chipsets: vesa
[    19.922] (II) FBDEV: driver for framebuffer: fbdev
[    19.923] (++) using VT number 7

[    19.985] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.985] (WW) Falling back to old probe method for vesa
[    19.985] (WW) Falling back to old probe method for fbdev
[    19.985] (II) Loading sub module "fbdevhw"
[    19.985] (II) LoadModule: "fbdevhw"
[    19.986] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    19.986] (II) Module fbdevhw: vendor="X.Org Foundation"
[    19.986] 	compiled for 1.10.1, module version = 0.0.2
[    19.986] 	ABI class: X.Org Video Driver, version 10.0
[    19.987] drmOpenDevice: node name is /dev/dri/card0
[    19.987] drmOpenDevice: open result is 8, (OK)
[    19.987] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    19.987] drmOpenDevice: node name is /dev/dri/card0
[    19.987] drmOpenDevice: open result is 8, (OK)
[    19.987] drmOpenByBusid: drmOpenMinor returns 8
[    19.987] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    19.987] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    19.987] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    19.988] (==) intel(0): RGB weight 888
[    19.988] (==) intel(0): Default visual is TrueColor
[    19.988] (II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview GM
[    19.988] (--) intel(0): Chipset: "Pineview GM"
[    19.988] (**) intel(0): Relaxed fencing enabled
[    19.988] (**) intel(0): Tiling enabled
[    19.996] (**) intel(0): SwapBuffers wait enabled
[    19.996] (==) intel(0): video overlay key set to 0x101fe
[    19.996] (II) intel(0): Output LVDS1 has no monitor section
[    20.004] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    20.036] (II) intel(0): Output VGA1 has no monitor section
[    20.036] (II) intel(0): EDID for output LVDS1
[    20.037] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    20.037] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    20.038] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    20.038] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.038] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    20.038] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    20.038] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    20.038] (II) intel(0): Printing probed modes for output LVDS1
[    20.038] (II) intel(0): Modeline "1024x600"x60.0   50.40  1024 1048 1184 1344  600 603 604 625 -hsync -vsync (37.5 kHz)
[    20.038] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    20.038] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    20.038] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    20.068] (II) intel(0): EDID for output VGA1
[    20.068] (II) intel(0): Output LVDS1 connected
[    20.068] (II) intel(0): Output VGA1 disconnected
[    20.068] (II) intel(0): Using exact sizes for initial modes
[    20.068] (II) intel(0): Output LVDS1 using initial mode 1024x600
[    20.068] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    20.068] (II) intel(0): Kernel page flipping support detected, enabling
[    20.068] (==) intel(0): DPI set to (96, 96)
[    20.068] (II) Loading sub module "fb"
[    20.068] (II) LoadModule: "fb"
[    20.070] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.071] (II) Module fb: vendor="X.Org Foundation"
[    20.071] 	compiled for 1.10.1, module version = 1.0.0
[    20.071] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    20.071] (II) UnloadModule: "vesa"
[    20.071] (II) Unloading vesa
[    20.071] (II) UnloadModule: "fbdev"
[    20.071] (II) Unloading fbdev
[    20.071] (II) UnloadModule: "fbdevhw"
[    20.071] (II) Unloading fbdevhw
[    20.071] (==) Depth 24 pixmap format is 32 bpp
[    20.071] (==) intel(0): VideoRam: 262144 KB
[    20.071] (II) intel(0): [DRI2] Setup complete
[    20.072] (II) intel(0): [DRI2]   DRI driver: i915
[    20.072] (II) intel(0): Allocated new frame buffer 1024x600 stride 4096, tiled
[    20.072] (II) UXA(0): Driver registered support for the following operations:
[    20.072] (II)         solid
[    20.072] (II)         copy
[    20.072] (II)         composite (RENDER acceleration)
[    20.072] (II)         put_image
[    20.072] (II)         get_image
[    20.072] (==) intel(0): Backing store disabled
[    20.073] (==) intel(0): Silken mouse enabled
[    20.073] (II) intel(0): Initializing HW Cursor
[    20.092] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    20.094] (==) intel(0): DPMS enabled
[    20.094] (==) intel(0): Intel XvMC decoder disabled
[    20.094] (II) intel(0): Set up textured video
[    20.094] (II) intel(0): Set up overlay video
[    20.094] (II) intel(0): direct rendering: DRI2 Enabled
[    20.094] (==) intel(0): hotplug detection: "enabled"
[    20.095] (--) RandR disabled
[    20.095] (II) Initializing built-in extension Generic Event Extension
[    20.095] (II) Initializing built-in extension SHAPE
[    20.095] (II) Initializing built-in extension MIT-SHM
[    20.095] (II) Initializing built-in extension XInputExtension
[    20.095] (II) Initializing built-in extension XTEST
[    20.095] (II) Initializing built-in extension BIG-REQUESTS
[    20.095] (II) Initializing built-in extension SYNC
[    20.095] (II) Initializing built-in extension XKEYBOARD
[    20.095] (II) Initializing built-in extension XC-MISC
[    20.095] (II) Initializing built-in extension SECURITY
[    20.095] (II) Initializing built-in extension XINERAMA
[    20.095] (II) Initializing built-in extension XFIXES
[    20.095] (II) Initializing built-in extension RENDER
[    20.095] (II) Initializing built-in extension RANDR
[    20.095] (II) Initializing built-in extension COMPOSITE
[    20.095] (II) Initializing built-in extension DAMAGE
[    20.095] (II) Initializing built-in extension GESTURE
[    20.191] (II) AIGLX: Trying DRI driver /usr/lib/dri/i915_dri.so
[    20.249] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    20.249] (II) AIGLX: enabled GLX_INTEL_swap_event
[    20.249] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    20.249] (II) AIGLX: enabled GLX_SGI_make_current_read
[    20.249] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    20.249] (II) AIGLX: Loaded and initialized i915
[    20.249] (II) GLX: Initialized DRI2 GL provider for screen 0
[    20.251] (II) intel(0): Setting screen physical size to 270 x 158
[    20.599] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    20.690] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    20.690] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.690] (II) LoadModule: "evdev"
[    20.691] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.693] (II) Module evdev: vendor="X.Org Foundation"
[    20.693] 	compiled for 1.10.0.902, module version = 2.6.0
[    20.693] 	Module class: X.Org XInput Driver
[    20.693] 	ABI class: X.Org XInput driver, version 12.3
[    20.693] (II) Using input driver 'evdev' for 'Power Button'
[    20.693] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.694] (**) Power Button: always reports core events
[    20.694] (**) Power Button: Device: "/dev/input/event2"
[    20.715] (--) Power Button: Found keys
[    20.715] (II) Power Button: Configuring as keyboard
[    20.715] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    20.715] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.715] (**) Option "xkb_rules" "evdev"
[    20.715] (**) Option "xkb_model" "pc104"
[    20.715] (**) Option "xkb_layout" "gb"
[    20.716] (**) Option "xkb_variant" "intl"
[    20.742] (II) XKB: reuse xkmfile /var/lib/xkb/server-8CD30BBC79737FB92B2E1013175C8A0204B4D460.xkm
[    20.759] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    20.759] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    20.759] (II) Using input driver 'evdev' for 'Video Bus'
[    20.759] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.759] (**) Video Bus: always reports core events
[    20.759] (**) Video Bus: Device: "/dev/input/event4"
[    20.772] (--) Video Bus: Found keys
[    20.772] (II) Video Bus: Configuring as keyboard
[    20.772] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[    20.772] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    20.772] (**) Option "xkb_rules" "evdev"
[    20.772] (**) Option "xkb_model" "pc104"
[    20.772] (**) Option "xkb_layout" "gb"
[    20.772] (**) Option "xkb_variant" "intl"
[    20.797] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    20.798] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    20.798] (II) Using input driver 'evdev' for 'Power Button'
[    20.798] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.798] (**) Power Button: always reports core events
[    20.798] (**) Power Button: Device: "/dev/input/event0"
[    20.820] (--) Power Button: Found keys
[    20.820] (II) Power Button: Configuring as keyboard
[    20.820] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    20.820] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    20.821] (**) Option "xkb_rules" "evdev"
[    20.821] (**) Option "xkb_model" "pc104"
[    20.821] (**) Option "xkb_layout" "gb"
[    20.821] (**) Option "xkb_variant" "intl"
[    20.823] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    20.823] (II) No input driver/identifier specified (ignoring)
[    20.943] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    20.943] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    20.957] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    20.957] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    20.957] (**) AT Translated Set 2 keyboard: always reports core events
[    20.957] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    20.972] (--) AT Translated Set 2 keyboard: Found keys
[    20.972] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    20.972] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    20.973] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    20.973] (**) Option "xkb_rules" "evdev"
[    20.973] (**) Option "xkb_model" "pc104"
[    20.973] (**) Option "xkb_layout" "gb"
[    20.973] (**) Option "xkb_variant" "intl"
[    21.494] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    21.494] (II) No input driver/identifier specified (ignoring)
[    21.497] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    21.497] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.498] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.498] (II) LoadModule: "synaptics"
[    21.499] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.500] (II) Module synaptics: vendor="X.Org Foundation"
[    21.500] 	compiled for 1.10.1, module version = 1.3.99
[    21.500] 	Module class: X.Org XInput Driver
[    21.500] 	ABI class: X.Org XInput driver, version 12.3
[    21.500] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    21.500] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.500] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.500] (**) Option "Device" "/dev/input/event6"
[    21.588] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5382
[    21.588] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4754
[    21.588] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.588] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.588] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    21.692] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    21.692] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.730] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input6/event6"
[    21.730] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    21.730] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.730] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    21.730] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.039
[    21.731] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.731] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.731] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.731] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.793] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    21.817] (II) config/udev: Adding input device Sunny 1.3M Webcam (/dev/input/event5)
[    21.817] (**) Sunny 1.3M Webcam: Applying InputClass "evdev keyboard catchall"
[    21.817] (II) Using input driver 'evdev' for 'Sunny 1.3M Webcam'
[    21.817] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.817] (**) Sunny 1.3M Webcam: always reports core events
[    21.818] (**) Sunny 1.3M Webcam: Device: "/dev/input/event5"
[    21.844] (--) Sunny 1.3M Webcam: Found keys
[    21.844] (II) Sunny 1.3M Webcam: Configuring as keyboard
[    21.844] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5/event5"
[    21.844] (II) XINPUT: Adding extended input device "Sunny 1.3M Webcam" (type: KEYBOARD)
[    21.844] (**) Option "xkb_rules" "evdev"
[    21.844] (**) Option "xkb_model" "pc104"
[    21.844] (**) Option "xkb_layout" "gb"
[    21.844] (**) Option "xkb_variant" "intl"
[    22.334] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[    22.334] (II) No input driver/identifier specified (ignoring)
[    22.338] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[    22.338] (II) No input driver/identifier specified (ignoring)
[  1244.640] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1248.760] (II) Open ACPI successful (/var/run/acpid.socket)
[  1248.760] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1248.760] (EE) intel(0): Couldn't create pixmap for fbcon
[  1248.913] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1388.512] (II) Power Button: Close
[  1388.512] (II) UnloadModule: "evdev"
[  1388.512] (II) Unloading evdev
[  1388.536] (II) Video Bus: Close
[  1388.536] (II) UnloadModule: "evdev"
[  1388.536] (II) Unloading evdev
[  1388.568] (II) Power Button: Close
[  1388.568] (II) UnloadModule: "evdev"
[  1388.568] (II) Unloading evdev
[  1388.596] (II) AT Translated Set 2 keyboard: Close
[  1388.596] (II) UnloadModule: "evdev"
[  1388.596] (II) Unloading evdev
[  1388.632] (II) UnloadModule: "synaptics"
[  1388.632] (II) Unloading synaptics
[  1388.648] (II) Sunny 1.3M Webcam: Close
[  1388.648] (II) UnloadModule: "evdev"
[  1388.648] (II) Unloading evdev
[  1390.010]  ddxSigGiveUp: Closing log

```

---

### Post by dino99 on 2011-07-31
if you use a xorg.conf, then try without it (sudo rm /etc/X11/xorg.conf)

---

### Post by fhd on 2011-07-31
> **dino99 said:**
> if you use a xorg.conf, then try without it (sudo rm /etc/X11/xorg.conf)

There is no xorg.conf, I just installed Oneiric and made no changes.

---

### Post by lucazade on 2011-07-31
> **fhd said:**
> There is no xorg.conf, I just installed Oneiric and made no changes.

While in natty you are using intel drivers, your oneiric installation is using standard vesa drivers so it is not able to handle correct resolution.
Intel drivers from your log seem corretly installed but are not employed.

could you paste the output of (also in natty):
```
ls /usr/share/X11/xorg.conf.d/

```
to ckeck if there is any template of xorg.conf for intel (should be something like 10-intel.conf)

if exists this file:
```
cat /usr/share/X11/xorg.conf.d/10-intel.conf

```

if not exist create a new xorg.conf with intel as driver:
```
gksu gedit /etc/X11/xorg.conf

```

and paste in this new file the following:
```
Section "Device"
        Identifier    "Intel N10"
        Driver         "intel"
EndSection
```

save and reboot.

if it doesn't work as well, we'll see why.

---

### Post by fhd on 2011-07-31
> **lucazade said:**
> 
could you paste the output of (also in natty):
```
ls /usr/share/X11/xorg.conf.d/

```
to ckeck if there is any template of xorg.conf for intel (should be something like 10-intel.conf)


As you can see, there is no such file (not on Natty, either):

```

10-evdev.conf         11-evdev-trackpoint.conf  50-vmmouse.conf
11-evdev-quirks.conf  50-synaptics.conf         50-wacom.conf

```

> 
if not exist create a new xorg.conf with intel as driver:
```
gksu gedit /etc/X11/xorg.conf

```

and paste in this new file the following:
```
Section "Device"
        Identifier    "Intel N10"
        Driver         "intel"
EndSection
```

save and reboot.

if it doesn't work as well, we'll see why.

X didn't start after I did that, here is the Xorg.0.log:

```

[   431.221] 
X.Org X Server 1.10.2.902 (1.10.3 RC 2)
Release Date: 2011-07-01
[   431.222] X Protocol Version 11, Revision 0
[   431.222] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   431.222] Current Operating System: Linux orpheus 3.0.0-7-generic #9-Ubuntu SMP Fri Jul 29 21:24:57 UTC 2011 i686
[   431.222] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=81121aa0-2c37-4de0-93cc-d445fdd56ef8 ro nomodeset
[   431.222] Build Date: 13 July 2011  12:18:21AM
[   431.223] xorg-server 2:1.10.2.902-1ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[   431.223] Current version of pixman: 0.22.2
[   431.223] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   431.223] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   431.224] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 31 17:55:31 2011
[   431.225] (==) Using config file: "/etc/X11/xorg.conf"
[   431.225] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   431.226] (==) No Layout section.  Using the first Screen section.
[   431.226] (==) No screen section available. Using defaults.
[   431.226] (**) |-->Screen "Default Screen Section" (0)
[   431.226] (**) |   |-->Monitor "<default monitor>"
[   431.226] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[   431.226] (**) |   |-->Device "Intel N10"
[   431.226] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   431.226] (==) Automatically adding devices
[   431.227] (==) Automatically enabling devices
[   431.227] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   431.227] 	Entry deleted from font path.
[   431.227] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   431.227] 	Entry deleted from font path.
[   431.227] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   431.227] 	Entry deleted from font path.
[   431.227] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   431.227] 	Entry deleted from font path.
[   431.227] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   431.227] 	Entry deleted from font path.
[   431.227] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   431.227] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   431.227] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   431.227] (II) Loader magic: 0x8239da0
[   431.227] (II) Module ABI versions:
[   431.227] 	X.Org ANSI C Emulation: 0.4
[   431.227] 	X.Org Video Driver: 10.0
[   431.227] 	X.Org XInput driver : 12.3
[   431.227] 	X.Org Server Extension : 5.0
[   431.229] (--) PCI:*(0:0:2:0) 8086:a011:1b7d:0002 rev 0, Mem @ 0x58180000/524288, 0x40000000/268435456, 0x58000000/1048576, I/O @ 0x000060c0/8
[   431.229] (--) PCI: (0:0:2:1) 8086:a012:1b7d:0002 rev 0, Mem @ 0x58100000/524288
[   431.229] (II) Open ACPI successful (/var/run/acpid.socket)
[   431.229] (II) LoadModule: "extmod"
[   431.231] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   431.231] (II) Module extmod: vendor="X.Org Foundation"
[   431.231] 	compiled for 1.10.2.902, module version = 1.0.0
[   431.231] 	Module class: X.Org Server Extension
[   431.231] 	ABI class: X.Org Server Extension, version 5.0
[   431.231] (II) Loading extension MIT-SCREEN-SAVER
[   431.231] (II) Loading extension XFree86-VidModeExtension
[   431.231] (II) Loading extension XFree86-DGA
[   431.231] (II) Loading extension DPMS
[   431.231] (II) Loading extension XVideo
[   431.231] (II) Loading extension XVideo-MotionCompensation
[   431.231] (II) Loading extension X-Resource
[   431.231] (II) LoadModule: "dbe"
[   431.232] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   431.232] (II) Module dbe: vendor="X.Org Foundation"
[   431.232] 	compiled for 1.10.2.902, module version = 1.0.0
[   431.232] 	Module class: X.Org Server Extension
[   431.232] 	ABI class: X.Org Server Extension, version 5.0
[   431.232] (II) Loading extension DOUBLE-BUFFER
[   431.232] (II) LoadModule: "glx"
[   431.233] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   431.233] (II) Module glx: vendor="X.Org Foundation"
[   431.233] 	compiled for 1.10.2.902, module version = 1.0.0
[   431.233] 	ABI class: X.Org Server Extension, version 5.0
[   431.233] (==) AIGLX enabled
[   431.233] (II) Loading extension GLX
[   431.233] (II) LoadModule: "record"
[   431.234] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   431.234] (II) Module record: vendor="X.Org Foundation"
[   431.234] 	compiled for 1.10.2.902, module version = 1.13.0
[   431.234] 	Module class: X.Org Server Extension
[   431.234] 	ABI class: X.Org Server Extension, version 5.0
[   431.234] (II) Loading extension RECORD
[   431.234] (II) LoadModule: "dri"
[   431.235] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   431.235] (II) Module dri: vendor="X.Org Foundation"
[   431.235] 	compiled for 1.10.2.902, module version = 1.0.0
[   431.235] 	ABI class: X.Org Server Extension, version 5.0
[   431.235] (II) Loading extension XFree86-DRI
[   431.235] (II) LoadModule: "dri2"
[   431.236] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   431.236] (II) Module dri2: vendor="X.Org Foundation"
[   431.236] 	compiled for 1.10.2.902, module version = 1.2.0
[   431.236] 	ABI class: X.Org Server Extension, version 5.0
[   431.236] (II) Loading extension DRI2
[   431.236] (II) LoadModule: "intel"
[   431.237] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   431.237] (II) Module intel: vendor="X.Org Foundation"
[   431.238] 	compiled for 1.10.2, module version = 2.15.0
[   431.238] 	Module class: X.Org Video Driver
[   431.238] 	ABI class: X.Org Video Driver, version 10.0
[   431.238] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[   431.239] (--) using VT number 8

[   431.251] (EE) No devices detected.
[   431.251] 
Fatal server error:
[   431.251] no screens found
[   431.251] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   431.251] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   431.252] 

```

---

### Post by lucazade on 2011-07-31
(EE) No devices detected
weird.

boot in recovery mode and purge this trial:
sudo rm /etc/X11/xorg.conf
then reboot

try to see if the updated intel driver contained in this ppa could help:
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

---

### Post by fhd on 2011-07-31
> **lucazade said:**
> 
try to see if the updated intel driver contained in this ppa could help:
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=oneiric)

Just added that PPA, did a dist-upgrade and rebooted. Same problem, I fear :(

---

### Post by lucazade on 2011-07-31
in the meantime open a bug report, it is a regression from natty.
probably intel driver are not so ready in OO.

```
ubuntu-bug xorg
```

when in the logs there was "no-device" looks like the pciid of the card is not included in pci list of supported hardware by the drivers.

---

### Post by fhd on 2011-07-31
> **lucazade said:**
> in the meantime open a bug report, it is a regression from natty.
probably intel driver are not so ready in OO.

```
ubuntu-bug xorg
```

when in the logs there was "no-device" looks like the pciid of the card is not included in pci list of supported hardware by the drivers.

Okay, I've created a bug report:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/818941](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/818941)

Thanks for your help.

---


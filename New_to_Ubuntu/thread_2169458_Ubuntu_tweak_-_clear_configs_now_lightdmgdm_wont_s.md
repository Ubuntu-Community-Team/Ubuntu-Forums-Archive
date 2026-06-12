---
title: "Ubuntu tweak - clear configs now lightdm/gdm wont start"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by keno10 on 2013-08-22
i used ubuntu tweak to clean my system but after cleaning config and reboot system was unable to boot again only recovery was possible and from there do terminal
lightdm try to run X but it sememed to me i dont have it and i have Xorg instead 
log/lightdm
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=5475
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Adding default seat
[+0.01s] DEBUG: Starting seat
[+0.01s] DEBUG: Starting new display for automatic login as user keno10
[+0.01s] DEBUG: Starting local X display
[+0.01s] DEBUG: Using VT 7
[+0.01s] DEBUG: Activating VT 7
[+0.01s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.02s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.02s] DEBUG: Launching X Server
[+0.02s] DEBUG: Launching process 5482: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.02s] DEBUG: Waiting for ready signal from X server :0
[+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.02s] DEBUG: Process 5482 exited with return value 1
[+0.02s] DEBUG: X server stopped
[+0.02s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.02s] DEBUG: Releasing VT 7
[+0.02s] DEBUG: Display server stopped
[+0.02s] DEBUG: Stopping display
[+0.02s] DEBUG: Display stopped
[+0.02s] DEBUG: Stopping X local seat, failed to start a display
[+0.02s] DEBUG: Stopping seat
[+0.02s] DEBUG: Seat stopped
[+0.02s] DEBUG: Required seat has stopped
[+0.02s] DEBUG: Stopping display manager
[+0.02s] DEBUG: Display manager stopped
[+0.02s] DEBUG: Stopping daemon
[+0.02s] DEBUG: Exiting with return value 1

```
in same folder x-0.log
```
X: cannot stat /etc/X11/X (No such file or directory), aborting.
```
in log folder  Xorg.0.log
```
[   842.402] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   842.404] X Protocol Version 11, Revision 0
[   842.405] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[   842.407] Current Operating System: Linux a04-0533a 3.2.0-52-lowlatency #54-Ubuntu SMP PREEMPT Tue Aug 6 02:04:12 UTC 2013 x86_64
[   842.407] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-52-lowlatency root=UUID=377c4509-b9ca-4139-9b84-69d1a92bc46d ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
[   842.410] Build Date: 11 April 2013  11:49:23PM
[   842.411] xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see http://www.ubuntu.com/support) 
[   842.412] Current version of pixman: 0.24.4
[   842.413]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   842.413] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   842.416] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 21 20:51:42 2013
[   842.417] (==) Using config file: "/etc/X11/xorg.conf"
[   842.418] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   842.418] (==) ServerLayout "Layout0"
[   842.418] (**) |-->Screen "Screen0" (0)
[   842.418] (**) |   |-->Monitor "Monitor0"
[   842.419] (**) |   |-->Device "Device0"
[   842.419] (**) |-->Input Device "Keyboard0"
[   842.419] (**) |-->Input Device "Mouse0"
[   842.419] (==) Automatically adding devices
[   842.419] (==) Automatically enabling devices
[   842.419] (==) Automatically adding GPU devices
[   842.419] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   842.419]     Entry deleted from font path.
[   842.419] (**) FontPath set to:
    unix/:7100,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   842.419] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   842.419] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   842.419] (WW) Disabling Keyboard0
[   842.419] (WW) Disabling Mouse0
[   842.419] (II) Loader magic: 0x7fc327b37c20
[   842.419] (II) Module ABI versions:
[   842.419]     X.Org ANSI C Emulation: 0.4
[   842.419]     X.Org Video Driver: 13.0
[   842.419]     X.Org XInput driver : 18.0
[   842.419]     X.Org Server Extension : 7.0
[   842.421] (--) PCI:*(0:8:0:0) 10de:0631:1462:1014 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[   842.421] (II) Open ACPI successful (/var/run/acpid.socket)
[   842.422] Initializing built-in extension Generic Event Extension
[   842.423] Initializing built-in extension SHAPE
[   842.424] Initializing built-in extension MIT-SHM
[   842.425] Initializing built-in extension XInputExtension
[   842.426] Initializing built-in extension XTEST
[   842.426] Initializing built-in extension BIG-REQUESTS
[   842.427] Initializing built-in extension SYNC
[   842.428] Initializing built-in extension XKEYBOARD
[   842.429] Initializing built-in extension XC-MISC
[   842.429] Initializing built-in extension SECURITY
[   842.430] Initializing built-in extension XINERAMA
[   842.431] Initializing built-in extension XFIXES
[   842.431] Initializing built-in extension RENDER
[   842.432] Initializing built-in extension RANDR
[   842.433] Initializing built-in extension COMPOSITE
[   842.433] Initializing built-in extension DAMAGE
[   842.434] Initializing built-in extension MIT-SCREEN-SAVER
[   842.434] Initializing built-in extension DOUBLE-BUFFER
[   842.435] Initializing built-in extension RECORD
[   842.435] Initializing built-in extension DPMS
[   842.436] Initializing built-in extension X-Resource
[   842.436] Initializing built-in extension XVideo
[   842.436] Initializing built-in extension XVideo-MotionCompensation
[   842.437] Initializing built-in extension XFree86-VidModeExtension
[   842.437] Initializing built-in extension XFree86-DGA
[   842.438] Initializing built-in extension XFree86-DRI
[   842.438] Initializing built-in extension DRI2
[   842.438] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   842.438] (II) LoadModule: "dbe"
[   842.438] (II) Module "dbe" already built-in
[   842.438] (II) LoadModule: "extmod"
[   842.438] (II) Module "extmod" already built-in
[   842.438] (II) LoadModule: "glx"
[   842.438] (WW) Warning, couldn't open module glx
[   842.438] (II) UnloadModule: "glx"
[   842.438] (II) Unloading glx
[   842.438] (EE) Failed to load module "glx" (module does not exist, 0)
[   842.438] (II) LoadModule: "nvidia"
[   842.439] (WW) Warning, couldn't open module nvidia
[   842.439] (II) UnloadModule: "nvidia"
[   842.439] (II) Unloading nvidia
[   842.439] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   842.439] (==) Matched nvidia as autoconfigured driver 0
[   842.439] (==) Matched nouveau as autoconfigured driver 1
[   842.439] (==) Matched nv as autoconfigured driver 2
[   842.439] (==) Matched vesa as autoconfigured driver 3
[   842.439] (==) Matched modesetting as autoconfigured driver 4
[   842.439] (==) Matched fbdev as autoconfigured driver 5
[   842.439] (==) Assigned the driver to the xf86ConfigLayout
[   842.439] (II) LoadModule: "nvidia"
[   842.439] (WW) Warning, couldn't open module nvidia
[   842.439] (II) UnloadModule: "nvidia"
[   842.439] (II) Unloading nvidia
[   842.439] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   842.439] (II) LoadModule: "nouveau"
[   842.440] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   842.440] (II) Module nouveau: vendor="X.Org Foundation"
[   842.440]     compiled for 1.13.0, module version = 1.0.2
[   842.440]     Module class: X.Org Video Driver
[   842.440]     ABI class: X.Org Video Driver, version 13.0
[   842.440] (II) LoadModule: "nv"
[   842.440] (WW) Warning, couldn't open module nv
[   842.440] (II) UnloadModule: "nv"
[   842.440] (II) Unloading nv
[   842.440] (EE) Failed to load module "nv" (module does not exist, 0)
[   842.440] (II) LoadModule: "vesa"
[   842.441] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   842.441] (II) Module vesa: vendor="X.Org Foundation"
[   842.441]     compiled for 1.13.0, module version = 2.3.2
[   842.441]     Module class: X.Org Video Driver
[   842.441]     ABI class: X.Org Video Driver, version 13.0
[   842.441] (II) LoadModule: "modesetting"
[   842.441] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   842.441] (II) Module modesetting: vendor="X.Org Foundation"
[   842.441]     compiled for 1.13.0, module version = 0.5.0
[   842.441]     Module class: X.Org Video Driver
[   842.441]     ABI class: X.Org Video Driver, version 13.0
[   842.441] (II) LoadModule: "fbdev"
[   842.441] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   842.441] (II) Module fbdev: vendor="X.Org Foundation"
[   842.441]     compiled for 1.13.0, module version = 0.4.3
[   842.441]     Module class: X.Org Video Driver
[   842.441]     ABI class: X.Org Video Driver, version 13.0
[   842.441] (II) NOUVEAU driver Date:   Wed Sep 12 13:42:43 2012 +0200
[   842.441] (II) NOUVEAU driver for NVIDIA chipset families :
[   842.441]     RIVA TNT        (NV04)
[   842.441]     RIVA TNT2       (NV05)
[   842.441]     GeForce 256     (NV10)
[   842.441]     GeForce 2       (NV11, NV15)
[   842.441]     GeForce 4MX     (NV17, NV18)
[   842.441]     GeForce 3       (NV20)
[   842.441]     GeForce 4Ti     (NV25, NV28)
[   842.442]     GeForce FX      (NV3x)
[   842.442]     GeForce 6       (NV4x)
[   842.442]     GeForce 7       (G7x)
[   842.442]     GeForce 8       (G8x)
[   842.442]     GeForce GTX 200 (NVA0)
[   842.442]     GeForce GTX 400 (NVC0)
[   842.442] (II) VESA: driver for VESA chipsets: vesa
[   842.442] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   842.442] (II) FBDEV: driver for framebuffer: fbdev
[   842.442] (--) using VT number 7

[   842.533] (EE) [drm] failed to open device
[   842.533] (WW) Falling back to old probe method for modesetting
[   842.534] (EE) open /dev/dri/card0: No such file or directory
[   842.534] (WW) Falling back to old probe method for fbdev
[   842.534] (II) Loading sub module "fbdevhw"
[   842.534] (II) LoadModule: "fbdevhw"
[   842.534] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   842.534] (II) Module fbdevhw: vendor="X.Org Foundation"
[   842.534]     compiled for 1.13.0, module version = 0.0.2
[   842.534]     ABI class: X.Org Video Driver, version 13.0
[   842.534] (II) Loading sub module "vbe"
[   842.534] (II) LoadModule: "vbe"
[   842.535] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   842.535] (II) Module vbe: vendor="X.Org Foundation"
[   842.535]     compiled for 1.13.0, module version = 1.1.0
[   842.535]     ABI class: X.Org Video Driver, version 13.0
[   842.535] (II) Loading sub module "int10"
[   842.535] (II) LoadModule: "int10"
[   842.535] (II) Loading /usr/lib/xorg/modules/libint10.so
[   842.535] (II) Module int10: vendor="X.Org Foundation"
[   842.535]     compiled for 1.13.0, module version = 1.0.0
[   842.536]     ABI class: X.Org Video Driver, version 13.0
[   842.536] (II) VESA(0): initializing int10
[   842.536] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   842.621] (II) VESA(0): VESA BIOS detected
[   842.621] (II) VESA(0): VESA VBE Version 3.0
[   842.621] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[   842.621] (II) VESA(0): VESA VBE OEM: NVIDIA
[   842.621] (II) VESA(0): VESA VBE OEM Software Rev: 98.148
[   842.621] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[   842.621] (II) VESA(0): VESA VBE OEM Product: G94 Board - 06100005
[   842.621] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[   842.760] (**) VESA(0): Depth 24, (--) framebuffer bpp 32
[   842.760] (==) VESA(0): RGB weight 888
[   842.761] (==) VESA(0): Default visual is TrueColor
[   842.761] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   842.761] (II) Loading sub module "ddc"
[   842.761] (II) LoadModule: "ddc"
[   842.761] (II) Module "ddc" already built-in
[   842.828] (II) VESA(0): VESA VBE DDC supported
[   842.828] (II) VESA(0): VESA VBE DDC Level none
[   842.828] (II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
[   843.104] (II) VESA(0): VESA VBE DDC read failed
[   843.104] (II) VESA(0): Searching for matching VESA mode(s):
[   843.106] Mode: 100 (640x400)
[   843.106]     ModeAttributes: 0x3bf
[   843.106]     WinAAttributes: 0x7
[   843.106]     WinBAttributes: 0x0
[   843.106]     WinGranularity: 64
[   843.106]     WinSize: 64
[   843.106]     WinASegment: 0xa000
[   843.106]     WinBSegment: 0x0
[   843.106]     WinFuncPtr: 0xc0008ec8
[   843.106]     BytesPerScanline: 640
[   843.106]     XResolution: 640
[   843.106]     YResolution: 400
[   843.106]     XCharSize: 8
[   843.106]     YCharSize: 16
[   843.106]     NumberOfPlanes: 1
[   843.106]     BitsPerPixel: 8
[   843.106]     NumberOfBanks: 1
[   843.106]     MemoryModel: 4
[   843.106]     BankSize: 0
[   843.106]     NumberOfImages: 14
[   843.106]     RedMaskSize: 0
[   843.106]     RedFieldPosition: 0
[   843.106]     GreenMaskSize: 0
[   843.106]     GreenFieldPosition: 0
[   843.106]     BlueMaskSize: 0
[   843.106]     BlueFieldPosition: 0
[   843.106]     RsvdMaskSize: 0
[   843.106]     RsvdFieldPosition: 0
[   843.106]     DirectColorModeInfo: 0
[   843.106]     PhysBasePtr: 0xfb000000
[   843.106]     LinBytesPerScanLine: 640
[   843.106]     BnkNumberOfImagePages: 14
[   843.106]     LinNumberOfImagePages: 14
[   843.106]     LinRedMaskSize: 0
[   843.106]     LinRedFieldPosition: 0
[   843.106]     LinGreenMaskSize: 0
[   843.106]     LinGreenFieldPosition: 0
[   843.106]     LinBlueMaskSize: 0
[   843.106]     LinBlueFieldPosition: 0
[   843.106]     LinRsvdMaskSize: 0
[   843.106]     LinRsvdFieldPosition: 0
[   843.106]     MaxPixelClock: 229500000
[   843.108] Mode: 101 (640x480)
[   843.108]     ModeAttributes: 0x3bf
[   843.108]     WinAAttributes: 0x7
[   843.108]     WinBAttributes: 0x0
[   843.108]     WinGranularity: 64
[   843.108]     WinSize: 64
[   843.108]     WinASegment: 0xa000
[   843.108]     WinBSegment: 0x0
[   843.108]     WinFuncPtr: 0xc0008ec8
[   843.108]     BytesPerScanline: 640
[   843.108]     XResolution: 640
[   843.108]     YResolution: 480
[   843.108]     XCharSize: 8
[   843.108]     YCharSize: 16
[   843.108]     NumberOfPlanes: 1
[   843.108]     BitsPerPixel: 8
[   843.108]     NumberOfBanks: 1
[   843.108]     MemoryModel: 4
[   843.108]     BankSize: 0
[   843.108]     NumberOfImages: 10
[   843.108]     RedMaskSize: 0
[   843.108]     RedFieldPosition: 0
[   843.108]     GreenMaskSize: 0
[   843.108]     GreenFieldPosition: 0
[   843.108]     BlueMaskSize: 0
[   843.108]     BlueFieldPosition: 0
[   843.108]     RsvdMaskSize: 0
[   843.108]     RsvdFieldPosition: 0
[   843.108]     DirectColorModeInfo: 0
[   843.108]     PhysBasePtr: 0xfb000000
[   843.108]     LinBytesPerScanLine: 640
[   843.108]     BnkNumberOfImagePages: 10
[   843.108]     LinNumberOfImagePages: 10
[   843.108]     LinRedMaskSize: 0
[   843.108]     LinRedFieldPosition: 0
[   843.108]     LinGreenMaskSize: 0
[   843.108]     LinGreenFieldPosition: 0
[   843.108]     LinBlueMaskSize: 0
[   843.108]     LinBlueFieldPosition: 0
[   843.108]     LinRsvdMaskSize: 0
[   843.108]     LinRsvdFieldPosition: 0
[   843.108]     MaxPixelClock: 229500000
[   843.110] Mode: 102 (800x600)
[   843.110]     ModeAttributes: 0x33f
[   843.110]     WinAAttributes: 0x7
[   843.110]     WinBAttributes: 0x0
[   843.110]     WinGranularity: 64
[   843.110]     WinSize: 64
[   843.110]     WinASegment: 0xa000
[   843.110]     WinBSegment: 0x0
[   843.110]     WinFuncPtr: 0xc0008ec8
[   843.110]     BytesPerScanline: 100
[   843.110]     XResolution: 800
[   843.110]     YResolution: 600
[   843.110]     XCharSize: 8
[   843.110]     YCharSize: 16
[   843.110]     NumberOfPlanes: 4
[   843.110]     BitsPerPixel: 4
[   843.110]     NumberOfBanks: 1
[   843.110]     MemoryModel: 3
[   843.110]     BankSize: 0
[   843.110]     NumberOfImages: 2
[   843.110]     RedMaskSize: 0
[   843.110]     RedFieldPosition: 0
[   843.110]     GreenMaskSize: 0
[   843.110]     GreenFieldPosition: 0
[   843.110]     BlueMaskSize: 0
[   843.110]     BlueFieldPosition: 0
[   843.110]     RsvdMaskSize: 0
[   843.110]     RsvdFieldPosition: 0
[   843.110]     DirectColorModeInfo: 0
[   843.110]     PhysBasePtr: 0x0
[   843.110]     LinBytesPerScanLine: 100
[   843.110]     BnkNumberOfImagePages: 2
[   843.110]     LinNumberOfImagePages: 2
[   843.110]     LinRedMaskSize: 0
[   843.110]     LinRedFieldPosition: 0
[   843.110]     LinGreenMaskSize: 0
[   843.110]     LinGreenFieldPosition: 0
[   843.110]     LinBlueMaskSize: 0
[   843.110]     LinBlueFieldPosition: 0
[   843.110]     LinRsvdMaskSize: 0
[   843.110]     LinRsvdFieldPosition: 0
[   843.110]     MaxPixelClock: 108500000
[   843.112] Mode: 103 (800x600)
[   843.112]     ModeAttributes: 0x3bf
[   843.112]     WinAAttributes: 0x7
[   843.112]     WinBAttributes: 0x0
[   843.112]     WinGranularity: 64
[   843.112]     WinSize: 64
[   843.112]     WinASegment: 0xa000
[   843.112]     WinBSegment: 0x0
[   843.112]     WinFuncPtr: 0xc0008ec8
[   843.112]     BytesPerScanline: 800
[   843.112]     XResolution: 800
[   843.112]     YResolution: 600
[   843.112]     XCharSize: 8
[   843.112]     YCharSize: 16
[   843.112]     NumberOfPlanes: 1
[   843.112]     BitsPerPixel: 8
[   843.112]     NumberOfBanks: 1
[   843.112]     MemoryModel: 4
[   843.112]     BankSize: 0
[   843.112]     NumberOfImages: 6
[   843.112]     RedMaskSize: 0
[   843.112]     RedFieldPosition: 0
[   843.112]     GreenMaskSize: 0
[   843.112]     GreenFieldPosition: 0
[   843.112]     BlueMaskSize: 0
[   843.112]     BlueFieldPosition: 0
[   843.112]     RsvdMaskSize: 0
[   843.112]     RsvdFieldPosition: 0
[   843.112]     DirectColorModeInfo: 0
[   843.112]     PhysBasePtr: 0xfb000000
[   843.113]     LinBytesPerScanLine: 800
[   843.113]     BnkNumberOfImagePages: 6
[   843.113]     LinNumberOfImagePages: 6
[   843.113]     LinRedMaskSize: 0
[   843.113]     LinRedFieldPosition: 0
[   843.113]     LinGreenMaskSize: 0
[   843.113]     LinGreenFieldPosition: 0
[   843.113]     LinBlueMaskSize: 0
[   843.113]     LinBlueFieldPosition: 0
[   843.113]     LinRsvdMaskSize: 0
[   843.113]     LinRsvdFieldPosition: 0
[   843.113]     MaxPixelClock: 229500000
[   843.114] Mode: 104 (1024x768)
[   843.114]     ModeAttributes: 0x33f
[   843.114]     WinAAttributes: 0x7
[   843.114]     WinBAttributes: 0x0
[   843.114]     WinGranularity: 64
[   843.114]     WinSize: 64
[   843.114]     WinASegment: 0xa000
[   843.114]     WinBSegment: 0x0
[   843.114]     WinFuncPtr: 0xc0008ec8
[   843.114]     BytesPerScanline: 128
[   843.114]     XResolution: 1024
[   843.114]     YResolution: 768
[   843.114]     XCharSize: 8
[   843.115]     YCharSize: 16
[   843.115]     NumberOfPlanes: 4
[   843.115]     BitsPerPixel: 4
[   843.115]     NumberOfBanks: 1
[   843.115]     MemoryModel: 3
[   843.115]     BankSize: 0
[   843.115]     NumberOfImages: 1
[   843.115]     RedMaskSize: 0
[   843.115]     RedFieldPosition: 0
[   843.115]     GreenMaskSize: 0
[   843.115]     GreenFieldPosition: 0
[   843.115]     BlueMaskSize: 0
[   843.115]     BlueFieldPosition: 0
[   843.115]     RsvdMaskSize: 0
[   843.115]     RsvdFieldPosition: 0
[   843.115]     DirectColorModeInfo: 0
[   843.115]     PhysBasePtr: 0x0
[   843.115]     LinBytesPerScanLine: 128
[   843.115]     BnkNumberOfImagePages: 1
[   843.115]     LinNumberOfImagePages: 1
[   843.115]     LinRedMaskSize: 0
[   843.115]     LinRedFieldPosition: 0
[   843.115]     LinGreenMaskSize: 0
[   843.115]     LinGreenFieldPosition: 0
[   843.115]     LinBlueMaskSize: 0
[   843.115]     LinBlueFieldPosition: 0
[   843.115]     LinRsvdMaskSize: 0
[   843.115]     LinRsvdFieldPosition: 0
[   843.115]     MaxPixelClock: 108500000
[   843.117] Mode: 105 (1024x768)
[   843.117]     ModeAttributes: 0x3bf
[   843.117]     WinAAttributes: 0x7
[   843.117]     WinBAttributes: 0x0
[   843.117]     WinGranularity: 64
[   843.117]     WinSize: 64
[   843.117]     WinASegment: 0xa000
[   843.117]     WinBSegment: 0x0
[   843.117]     WinFuncPtr: 0xc0008ec8
[   843.117]     BytesPerScanline: 1024
[   843.117]     XResolution: 1024
[   843.117]     YResolution: 768
[   843.117]     XCharSize: 8
[   843.117]     YCharSize: 16
[   843.117]     NumberOfPlanes: 1
[   843.117]     BitsPerPixel: 8
[   843.117]     NumberOfBanks: 1
[   843.117]     MemoryModel: 4
[   843.117]     BankSize: 0
[   843.117]     NumberOfImages: 3
[   843.117]     RedMaskSize: 0
[   843.117]     RedFieldPosition: 0
[   843.117]     GreenMaskSize: 0
[   843.117]     GreenFieldPosition: 0
[   843.117]     BlueMaskSize: 0
[   843.117]     BlueFieldPosition: 0
[   843.117]     RsvdMaskSize: 0
[   843.117]     RsvdFieldPosition: 0
[   843.117]     DirectColorModeInfo: 0
[   843.117]     PhysBasePtr: 0xfb000000
[   843.117]     LinBytesPerScanLine: 1024
[   843.117]     BnkNumberOfImagePages: 3
[   843.117]     LinNumberOfImagePages: 3
[   843.117]     LinRedMaskSize: 0
[   843.117]     LinRedFieldPosition: 0
[   843.117]     LinGreenMaskSize: 0
[   843.117]     LinGreenFieldPosition: 0
[   843.117]     LinBlueMaskSize: 0
[   843.117]     LinBlueFieldPosition: 0
[   843.117]     LinRsvdMaskSize: 0
[   843.117]     LinRsvdFieldPosition: 0
[   843.117]     MaxPixelClock: 229500000
[   843.119] Mode: 106 (1280x1024)
[   843.119]     ModeAttributes: 0x33f
[   843.119]     WinAAttributes: 0x7
[   843.119]     WinBAttributes: 0x0
[   843.119]     WinGranularity: 64
[   843.119]     WinSize: 64
[   843.119]     WinASegment: 0xa000
[   843.119]     WinBSegment: 0x0
[   843.119]     WinFuncPtr: 0xc0008ec8
[   843.119]     BytesPerScanline: 160
[   843.119]     XResolution: 1280
[   843.119]     YResolution: 1024
[   843.119]     XCharSize: 8
[   843.119]     YCharSize: 16
[   843.119]     NumberOfPlanes: 4
[   843.119]     BitsPerPixel: 4
[   843.119]     NumberOfBanks: 1
[   843.119]     MemoryModel: 3
[   843.119]     BankSize: 0
[   843.119]     NumberOfImages: 1
[   843.119]     RedMaskSize: 0
[   843.119]     RedFieldPosition: 0
[   843.119]     GreenMaskSize: 0
[   843.119]     GreenFieldPosition: 0
[   843.119]     BlueMaskSize: 0
[   843.119]     BlueFieldPosition: 0
[   843.119]     RsvdMaskSize: 0
[   843.119]     RsvdFieldPosition: 0
[   843.119]     DirectColorModeInfo: 0
[   843.119]     PhysBasePtr: 0x0
[   843.119]     LinBytesPerScanLine: 160
[   843.119]     BnkNumberOfImagePages: 1
[   843.119]     LinNumberOfImagePages: 1
[   843.119]     LinRedMaskSize: 0
[   843.119]     LinRedFieldPosition: 0
[   843.119]     LinGreenMaskSize: 0
[   843.119]     LinGreenFieldPosition: 0
[   843.119]     LinBlueMaskSize: 0
[   843.119]     LinBlueFieldPosition: 0
[   843.119]     LinRsvdMaskSize: 0
[   843.119]     LinRsvdFieldPosition: 0
[   843.119]     MaxPixelClock: 108500000
[   843.121] Mode: 107 (1280x1024)
[   843.121]     ModeAttributes: 0x3bf
[   843.121]     WinAAttributes: 0x7
[   843.121]     WinBAttributes: 0x0
[   843.121]     WinGranularity: 64
[   843.121]     WinSize: 64
[   843.121]     WinASegment: 0xa000
[   843.121]     WinBSegment: 0x0
[   843.121]     WinFuncPtr: 0xc0008ec8
[   843.121]     BytesPerScanline: 1280
[   843.121]     XResolution: 1280
[   843.121]     YResolution: 1024
[   843.121]     XCharSize: 8
[   843.121]     YCharSize: 16
[   843.121]     NumberOfPlanes: 1
[   843.121]     BitsPerPixel: 8
[   843.121]     NumberOfBanks: 1
[   843.121]     MemoryModel: 4
[   843.121]     BankSize: 0
[   843.121]     NumberOfImages: 1
[   843.121]     RedMaskSize: 0
[   843.121]     RedFieldPosition: 0
[   843.121]     GreenMaskSize: 0
[   843.121]     GreenFieldPosition: 0
[   843.121]     BlueMaskSize: 0
[   843.121]     BlueFieldPosition: 0
[   843.121]     RsvdMaskSize: 0
[   843.121]     RsvdFieldPosition: 0
[   843.121]     DirectColorModeInfo: 0
[   843.121]     PhysBasePtr: 0xfb000000
[   843.121]     LinBytesPerScanLine: 1280
[   843.121]     BnkNumberOfImagePages: 1
[   843.121]     LinNumberOfImagePages: 1
[   843.121]     LinRedMaskSize: 0
[   843.121]     LinRedFieldPosition: 0
[   843.121]     LinGreenMaskSize: 0
[   843.121]     LinGreenFieldPosition: 0
[   843.121]     LinBlueMaskSize: 0
[   843.121]     LinBlueFieldPosition: 0
[   843.121]     LinRsvdMaskSize: 0
[   843.121]     LinRsvdFieldPosition: 0
[   843.121]     MaxPixelClock: 229500000
[   843.123] Mode: 10e (320x200)
[   843.123]     ModeAttributes: 0x3bf
[   843.123]     WinAAttributes: 0x7
[   843.123]     WinBAttributes: 0x0
[   843.123]     WinGranularity: 64
[   843.123]     WinSize: 64
[   843.123]     WinASegment: 0xa000
[   843.123]     WinBSegment: 0x0
[   843.123]     WinFuncPtr: 0xc0008ec8
[   843.123]     BytesPerScanline: 640
[   843.123]     XResolution: 320
[   843.123]     YResolution: 200
[   843.123]     XCharSize: 8
[   843.123]     YCharSize: 8
[   843.123]     NumberOfPlanes: 1
[   843.123]     BitsPerPixel: 16
[   843.123]     NumberOfBanks: 1
[   843.123]     MemoryModel: 6
[   843.123]     BankSize: 0
[   843.123]     NumberOfImages: 30
[   843.123]     RedMaskSize: 5
[   843.123]     RedFieldPosition: 11
[   843.123]     GreenMaskSize: 6
[   843.123]     GreenFieldPosition: 5
[   843.123]     BlueMaskSize: 5
[   843.123]     BlueFieldPosition: 0
[   843.123]     RsvdMaskSize: 0
[   843.123]     RsvdFieldPosition: 0
[   843.123]     DirectColorModeInfo: 0
[   843.123]     PhysBasePtr: 0xfb000000
[   843.123]     LinBytesPerScanLine: 640
[   843.123]     BnkNumberOfImagePages: 30
[   843.123]     LinNumberOfImagePages: 30
[   843.123]     LinRedMaskSize: 5
[   843.123]     LinRedFieldPosition: 11
[   843.123]     LinGreenMaskSize: 6
[   843.123]     LinGreenFieldPosition: 5
[   843.123]     LinBlueMaskSize: 5
[   843.123]     LinBlueFieldPosition: 0
[   843.123]     LinRsvdMaskSize: 0
[   843.123]     LinRsvdFieldPosition: 0
[   843.123]     MaxPixelClock: 229500000
[   843.125] *Mode: 10f (320x200)
[   843.125]     ModeAttributes: 0x3bf
[   843.125]     WinAAttributes: 0x7
[   843.125]     WinBAttributes: 0x0
[   843.125]     WinGranularity: 64
[   843.125]     WinSize: 64
[   843.125]     WinASegment: 0xa000
[   843.125]     WinBSegment: 0x0
[   843.125]     WinFuncPtr: 0xc0008ec8
[   843.125]     BytesPerScanline: 1280
[   843.125]     XResolution: 320
[   843.125]     YResolution: 200
[   843.125]     XCharSize: 8
[   843.125]     YCharSize: 8
[   843.125]     NumberOfPlanes: 1
[   843.125]     BitsPerPixel: 32
[   843.125]     NumberOfBanks: 1
[   843.125]     MemoryModel: 6
[   843.125]     BankSize: 0
[   843.125]     NumberOfImages: 14
[   843.125]     RedMaskSize: 8
[   843.125]     RedFieldPosition: 16
[   843.125]     GreenMaskSize: 8
[   843.125]     GreenFieldPosition: 8
[   843.125]     BlueMaskSize: 8
[   843.125]     BlueFieldPosition: 0
[   843.125]     RsvdMaskSize: 8
[   843.125]     RsvdFieldPosition: 24
[   843.125]     DirectColorModeInfo: 0
[   843.125]     PhysBasePtr: 0xfb000000
[   843.125]     LinBytesPerScanLine: 1280
[   843.125]     BnkNumberOfImagePages: 14
[   843.125]     LinNumberOfImagePages: 14
[   843.125]     LinRedMaskSize: 8
[   843.125]     LinRedFieldPosition: 16
[   843.125]     LinGreenMaskSize: 8
[   843.125]     LinGreenFieldPosition: 8
[   843.125]     LinBlueMaskSize: 8
[   843.125]     LinBlueFieldPosition: 0
[   843.125]     LinRsvdMaskSize: 8
[   843.125]     LinRsvdFieldPosition: 24
[   843.125]     MaxPixelClock: 229500000
[   843.127] Mode: 111 (640x480)
[   843.127]     ModeAttributes: 0x3bf
[   843.127]     WinAAttributes: 0x7
[   843.127]     WinBAttributes: 0x0
[   843.127]     WinGranularity: 64
[   843.127]     WinSize: 64
[   843.127]     WinASegment: 0xa000
[   843.127]     WinBSegment: 0x0
[   843.127]     WinFuncPtr: 0xc0008ec8
[   843.127]     BytesPerScanline: 1280
[   843.127]     XResolution: 640
[   843.127]     YResolution: 480
[   843.127]     XCharSize: 8
[   843.127]     YCharSize: 16
[   843.127]     NumberOfPlanes: 1
[   843.127]     BitsPerPixel: 16
[   843.127]     NumberOfBanks: 1
[   843.127]     MemoryModel: 6
[   843.127]     BankSize: 0
[   843.127]     NumberOfImages: 4
[   843.127]     RedMaskSize: 5
[   843.127]     RedFieldPosition: 11
[   843.127]     GreenMaskSize: 6
[   843.127]     GreenFieldPosition: 5
[   843.127]     BlueMaskSize: 5
[   843.127]     BlueFieldPosition: 0
[   843.127]     RsvdMaskSize: 0
[   843.127]     RsvdFieldPosition: 0
[   843.127]     DirectColorModeInfo: 0
[   843.127]     PhysBasePtr: 0xfb000000
[   843.127]     LinBytesPerScanLine: 1280
[   843.127]     BnkNumberOfImagePages: 4
[   843.127]     LinNumberOfImagePages: 4
[   843.127]     LinRedMaskSize: 5
[   843.127]     LinRedFieldPosition: 11
[   843.127]     LinGreenMaskSize: 6
[   843.127]     LinGreenFieldPosition: 5
[   843.127]     LinBlueMaskSize: 5
[   843.127]     LinBlueFieldPosition: 0
[   843.127]     LinRsvdMaskSize: 0
[   843.127]     LinRsvdFieldPosition: 0
[   843.127]     MaxPixelClock: 229500000
[   843.129] *Mode: 112 (640x480)
[   843.129]     ModeAttributes: 0x3bf
[   843.129]     WinAAttributes: 0x7
[   843.129]     WinBAttributes: 0x0
[   843.129]     WinGranularity: 64
[   843.129]     WinSize: 64
[   843.129]     WinASegment: 0xa000
[   843.129]     WinBSegment: 0x0
[   843.129]     WinFuncPtr: 0xc0008ec8
[   843.129]     BytesPerScanline: 2560
[   843.129]     XResolution: 640
[   843.129]     YResolution: 480
[   843.129]     XCharSize: 8
[   843.129]     YCharSize: 16
[   843.129]     NumberOfPlanes: 1
[   843.129]     BitsPerPixel: 32
[   843.129]     NumberOfBanks: 1
[   843.129]     MemoryModel: 6
[   843.129]     BankSize: 0
[   843.129]     NumberOfImages: 1
[   843.129]     RedMaskSize: 8
[   843.129]     RedFieldPosition: 16
[   843.129]     GreenMaskSize: 8
[   843.129]     GreenFieldPosition: 8
[   843.129]     BlueMaskSize: 8
[   843.129]     BlueFieldPosition: 0
[   843.129]     RsvdMaskSize: 8
[   843.129]     RsvdFieldPosition: 24
[   843.129]     DirectColorModeInfo: 0
[   843.129]     PhysBasePtr: 0xfb000000
[   843.129]     LinBytesPerScanLine: 2560
[   843.129]     BnkNumberOfImagePages: 1
[   843.129]     LinNumberOfImagePages: 1
[   843.129]     LinRedMaskSize: 8
[   843.129]     LinRedFieldPosition: 16
[   843.129]     LinGreenMaskSize: 8
[   843.129]     LinGreenFieldPosition: 8
[   843.130]     LinBlueMaskSize: 8
[   843.130]     LinBlueFieldPosition: 0
[   843.130]     LinRsvdMaskSize: 8
[   843.130]     LinRsvdFieldPosition: 24
[   843.130]     MaxPixelClock: 229500000
[   843.131] Mode: 114 (800x600)
[   843.131]     ModeAttributes: 0x3bf
[   843.131]     WinAAttributes: 0x7
[   843.131]     WinBAttributes: 0x0
[   843.131]     WinGranularity: 64
[   843.131]     WinSize: 64
[   843.131]     WinASegment: 0xa000
[   843.131]     WinBSegment: 0x0
[   843.131]     WinFuncPtr: 0xc0008ec8
[   843.131]     BytesPerScanline: 1600
[   843.131]     XResolution: 800
[   843.131]     YResolution: 600
[   843.131]     XCharSize: 8
[   843.131]     YCharSize: 16
[   843.131]     NumberOfPlanes: 1
[   843.131]     BitsPerPixel: 16
[   843.132]     NumberOfBanks: 1
[   843.132]     MemoryModel: 6
[   843.132]     BankSize: 0
[   843.132]     NumberOfImages: 2
[   843.132]     RedMaskSize: 5
[   843.132]     RedFieldPosition: 11
[   843.132]     GreenMaskSize: 6
[   843.132]     GreenFieldPosition: 5
[   843.132]     BlueMaskSize: 5
[   843.132]     BlueFieldPosition: 0
[   843.132]     RsvdMaskSize: 0
[   843.132]     RsvdFieldPosition: 0
[   843.132]     DirectColorModeInfo: 0
[   843.132]     PhysBasePtr: 0xfb000000
[   843.132]     LinBytesPerScanLine: 1600
[   843.132]     BnkNumberOfImagePages: 2
[   843.132]     LinNumberOfImagePages: 2
[   843.132]     LinRedMaskSize: 5
[   843.132]     LinRedFieldPosition: 11
[   843.132]     LinGreenMaskSize: 6
[   843.132]     LinGreenFieldPosition: 5
[   843.132]     LinBlueMaskSize: 5
[   843.132]     LinBlueFieldPosition: 0
[   843.132]     LinRsvdMaskSize: 0
[   843.132]     LinRsvdFieldPosition: 0
[   843.132]     MaxPixelClock: 229500000
[   843.133] *Mode: 115 (800x600)
[   843.133]     ModeAttributes: 0x3bf
[   843.134]     WinAAttributes: 0x7
[   843.134]     WinBAttributes: 0x0
[   843.134]     WinGranularity: 64
[   843.134]     WinSize: 64
[   843.134]     WinASegment: 0xa000
[   843.134]     WinBSegment: 0x0
[   843.134]     WinFuncPtr: 0xc0008ec8
[   843.134]     BytesPerScanline: 3200
[   843.134]     XResolution: 800
[   843.134]     YResolution: 600
[   843.134]     XCharSize: 8
[   843.134]     YCharSize: 16
[   843.134]     NumberOfPlanes: 1
[   843.134]     BitsPerPixel: 32
[   843.134]     NumberOfBanks: 1
[   843.134]     MemoryModel: 6
[   843.134]     BankSize: 0
[   843.134]     NumberOfImages: 1
[   843.134]     RedMaskSize: 8
[   843.134]     RedFieldPosition: 16
[   843.134]     GreenMaskSize: 8
[   843.134]     GreenFieldPosition: 8
[   843.134]     BlueMaskSize: 8
[   843.134]     BlueFieldPosition: 0
[   843.134]     RsvdMaskSize: 8
[   843.134]     RsvdFieldPosition: 24
[   843.134]     DirectColorModeInfo: 0
[   843.134]     PhysBasePtr: 0xfb000000
[   843.134]     LinBytesPerScanLine: 3200
[   843.134]     BnkNumberOfImagePages: 1
[   843.134]     LinNumberOfImagePages: 1
[   843.134]     LinRedMaskSize: 8
[   843.134]     LinRedFieldPosition: 16
[   843.134]     LinGreenMaskSize: 8
[   843.134]     LinGreenFieldPosition: 8
[   843.134]     LinBlueMaskSize: 8
[   843.134]     LinBlueFieldPosition: 0
[   843.134]     LinRsvdMaskSize: 8
[   843.134]     LinRsvdFieldPosition: 24
[   843.134]     MaxPixelClock: 229500000
[   843.136] Mode: 117 (1024x768)
[   843.136]     ModeAttributes: 0x3bf
[   843.136]     WinAAttributes: 0x7
[   843.136]     WinBAttributes: 0x0
[   843.136]     WinGranularity: 64
[   843.136]     WinSize: 64
[   843.136]     WinASegment: 0xa000
[   843.136]     WinBSegment: 0x0
[   843.136]     WinFuncPtr: 0xc0008ec8
[   843.136]     BytesPerScanline: 2048
[   843.136]     XResolution: 1024
[   843.136]     YResolution: 768
[   843.136]     XCharSize: 8
[   843.136]     YCharSize: 16
[   843.136]     NumberOfPlanes: 1
[   843.136]     BitsPerPixel: 16
[   843.136]     NumberOfBanks: 1
[   843.136]     MemoryModel: 6
[   843.136]     BankSize: 0
[   843.136]     NumberOfImages: 1
[   843.136]     RedMaskSize: 5
[   843.136]     RedFieldPosition: 11
[   843.136]     GreenMaskSize: 6
[   843.136]     GreenFieldPosition: 5
[   843.136]     BlueMaskSize: 5
[   843.136]     BlueFieldPosition: 0
[   843.136]     RsvdMaskSize: 0
[   843.136]     RsvdFieldPosition: 0
[   843.136]     DirectColorModeInfo: 0
[   843.136]     PhysBasePtr: 0xfb000000
[   843.136]     LinBytesPerScanLine: 2048
[   843.136]     BnkNumberOfImagePages: 1
[   843.136]     LinNumberOfImagePages: 1
[   843.136]     LinRedMaskSize: 5
[   843.136]     LinRedFieldPosition: 11
[   843.136]     LinGreenMaskSize: 6
[   843.136]     LinGreenFieldPosition: 5
[   843.136]     LinBlueMaskSize: 5
[   843.136]     LinBlueFieldPosition: 0
[   843.136]     LinRsvdMaskSize: 0
[   843.136]     LinRsvdFieldPosition: 0
[   843.136]     MaxPixelClock: 229500000
[   843.138] *Mode: 118 (1024x768)
[   843.138]     ModeAttributes: 0x3bf
[   843.138]     WinAAttributes: 0x7
[   843.138]     WinBAttributes: 0x0
[   843.138]     WinGranularity: 64
[   843.138]     WinSize: 64
[   843.138]     WinASegment: 0xa000
[   843.138]     WinBSegment: 0x0
[   843.138]     WinFuncPtr: 0xc0008ec8
[   843.138]     BytesPerScanline: 4096
[   843.138]     XResolution: 1024
[   843.138]     YResolution: 768
[   843.138]     XCharSize: 8
[   843.138]     YCharSize: 16
[   843.138]     NumberOfPlanes: 1
[   843.138]     BitsPerPixel: 32
[   843.138]     NumberOfBanks: 1
[   843.138]     MemoryModel: 6
[   843.138]     BankSize: 0
[   843.138]     NumberOfImages: 1
[   843.138]     RedMaskSize: 8
[   843.138]     RedFieldPosition: 16
[   843.138]     GreenMaskSize: 8
[   843.138]     GreenFieldPosition: 8
[   843.138]     BlueMaskSize: 8
[   843.138]     BlueFieldPosition: 0
[   843.138]     RsvdMaskSize: 8
[   843.138]     RsvdFieldPosition: 24
[   843.138]     DirectColorModeInfo: 0
[   843.138]     PhysBasePtr: 0xfb000000
[   843.138]     LinBytesPerScanLine: 4096
[   843.138]     BnkNumberOfImagePages: 1
[   843.138]     LinNumberOfImagePages: 1
[   843.138]     LinRedMaskSize: 8
[   843.138]     LinRedFieldPosition: 16
[   843.138]     LinGreenMaskSize: 8
[   843.138]     LinGreenFieldPosition: 8
[   843.138]     LinBlueMaskSize: 8
[   843.138]     LinBlueFieldPosition: 0
[   843.138]     LinRsvdMaskSize: 8
[   843.138]     LinRsvdFieldPosition: 24
[   843.138]     MaxPixelClock: 229500000
[   843.140] Mode: 11a (1280x1024)
[   843.140]     ModeAttributes: 0x3bf
[   843.140]     WinAAttributes: 0x7
[   843.140]     WinBAttributes: 0x0
[   843.140]     WinGranularity: 64
[   843.140]     WinSize: 64
[   843.140]     WinASegment: 0xa000
[   843.140]     WinBSegment: 0x0
[   843.140]     WinFuncPtr: 0xc0008ec8
[   843.140]     BytesPerScanline: 2560
[   843.140]     XResolution: 1280
[   843.140]     YResolution: 1024
[   843.140]     XCharSize: 8
[   843.140]     YCharSize: 16
[   843.140]     NumberOfPlanes: 1
[   843.140]     BitsPerPixel: 16
[   843.140]     NumberOfBanks: 1
[   843.140]     MemoryModel: 6
[   843.140]     BankSize: 0
[   843.140]     NumberOfImages: 1
[   843.140]     RedMaskSize: 5
[   843.140]     RedFieldPosition: 11
[   843.140]     GreenMaskSize: 6
[   843.140]     GreenFieldPosition: 5
[   843.140]     BlueMaskSize: 5
[   843.140]     BlueFieldPosition: 0
[   843.140]     RsvdMaskSize: 0
[   843.140]     RsvdFieldPosition: 0
[   843.140]     DirectColorModeInfo: 0
[   843.140]     PhysBasePtr: 0xfb000000
[   843.140]     LinBytesPerScanLine: 2560
[   843.140]     BnkNumberOfImagePages: 1
[   843.140]     LinNumberOfImagePages: 1
[   843.140]     LinRedMaskSize: 5
[   843.140]     LinRedFieldPosition: 11
[   843.140]     LinGreenMaskSize: 6
[   843.140]     LinGreenFieldPosition: 5
[   843.140]     LinBlueMaskSize: 5
[   843.140]     LinBlueFieldPosition: 0
[   843.140]     LinRsvdMaskSize: 0
[   843.140]     LinRsvdFieldPosition: 0
[   843.140]     MaxPixelClock: 229500000
[   843.142] *Mode: 11b (1280x1024)
[   843.142]     ModeAttributes: 0x3bf
[   843.142]     WinAAttributes: 0x7
[   843.142]     WinBAttributes: 0x0
[   843.142]     WinGranularity: 64
[   843.142]     WinSize: 64
[   843.142]     WinASegment: 0xa000
[   843.142]     WinBSegment: 0x0
[   843.142]     WinFuncPtr: 0xc0008ec8
[   843.142]     BytesPerScanline: 5120
[   843.142]     XResolution: 1280
[   843.142]     YResolution: 1024
[   843.142]     XCharSize: 8
[   843.142]     YCharSize: 16
[   843.142]     NumberOfPlanes: 1
[   843.142]     BitsPerPixel: 32
[   843.142]     NumberOfBanks: 1
[   843.142]     MemoryModel: 6
[   843.142]     BankSize: 0
[   843.142]     NumberOfImages: 1
[   843.142]     RedMaskSize: 8
[   843.142]     RedFieldPosition: 16
[   843.142]     GreenMaskSize: 8
[   843.142]     GreenFieldPosition: 8
[   843.142]     BlueMaskSize: 8
[   843.142]     BlueFieldPosition: 0
[   843.142]     RsvdMaskSize: 8
[   843.142]     RsvdFieldPosition: 24
[   843.142]     DirectColorModeInfo: 0
[   843.142]     PhysBasePtr: 0xfb000000
[   843.142]     LinBytesPerScanLine: 5120
[   843.142]     BnkNumberOfImagePages: 1
[   843.142]     LinNumberOfImagePages: 1
[   843.142]     LinRedMaskSize: 8
[   843.142]     LinRedFieldPosition: 16
[   843.142]     LinGreenMaskSize: 8
[   843.142]     LinGreenFieldPosition: 8
[   843.142]     LinBlueMaskSize: 8
[   843.142]     LinBlueFieldPosition: 0
[   843.142]     LinRsvdMaskSize: 8
[   843.142]     LinRsvdFieldPosition: 24
[   843.142]     MaxPixelClock: 229500000
[   843.144] Mode: 130 (320x200)
[   843.144]     ModeAttributes: 0x3bf
[   843.144]     WinAAttributes: 0x7
[   843.144]     WinBAttributes: 0x0
[   843.144]     WinGranularity: 64
[   843.144]     WinSize: 64
[   843.144]     WinASegment: 0xa000
[   843.144]     WinBSegment: 0x0
[   843.144]     WinFuncPtr: 0xc0008ec8
[   843.144]     BytesPerScanline: 320
[   843.144]     XResolution: 320
[   843.144]     YResolution: 200
[   843.144]     XCharSize: 8
[   843.144]     YCharSize: 8
[   843.144]     NumberOfPlanes: 1
[   843.144]     BitsPerPixel: 8
[   843.144]     NumberOfBanks: 1
[   843.144]     MemoryModel: 4
[   843.144]     BankSize: 0
[   843.144]     NumberOfImages: 62
[   843.144]     RedMaskSize: 0
[   843.144]     RedFieldPosition: 0
[   843.144]     GreenMaskSize: 0
[   843.144]     GreenFieldPosition: 0
[   843.144]     BlueMaskSize: 0
[   843.144]     BlueFieldPosition: 0
[   843.144]     RsvdMaskSize: 0
[   843.144]     RsvdFieldPosition: 0
[   843.144]     DirectColorModeInfo: 0
[   843.144]     PhysBasePtr: 0xfb000000
[   843.144]     LinBytesPerScanLine: 320
[   843.144]     BnkNumberOfImagePages: 62
[   843.144]     LinNumberOfImagePages: 62
[   843.144]     LinRedMaskSize: 0
[   843.144]     LinRedFieldPosition: 0
[   843.144]     LinGreenMaskSize: 0
[   843.144]     LinGreenFieldPosition: 0
[   843.144]     LinBlueMaskSize: 0
[   843.144]     LinBlueFieldPosition: 0
[   843.144]     LinRsvdMaskSize: 0
[   843.144]     LinRsvdFieldPosition: 0
[   843.144]     MaxPixelClock: 229500000
[   843.146] Mode: 131 (320x400)
[   843.146]     ModeAttributes: 0x3bf
[   843.146]     WinAAttributes: 0x7
[   843.146]     WinBAttributes: 0x0
[   843.146]     WinGranularity: 64
[   843.146]     WinSize: 64
[   843.146]     WinASegment: 0xa000
[   843.146]     WinBSegment: 0x0
[   843.146]     WinFuncPtr: 0xc0008ec8
[   843.146]     BytesPerScanline: 320
[   843.146]     XResolution: 320
[   843.146]     YResolution: 400
[   843.146]     XCharSize: 8
[   843.146]     YCharSize: 16
[   843.146]     NumberOfPlanes: 1
[   843.146]     BitsPerPixel: 8
[   843.146]     NumberOfBanks: 1
[   843.146]     MemoryModel: 4
[   843.146]     BankSize: 0
[   843.146]     NumberOfImages: 30
[   843.146]     RedMaskSize: 0
[   843.146]     RedFieldPosition: 0
[   843.146]     GreenMaskSize: 0
[   843.146]     GreenFieldPosition: 0
[   843.146]     BlueMaskSize: 0
[   843.146]     BlueFieldPosition: 0
[   843.146]     RsvdMaskSize: 0
[   843.146]     RsvdFieldPosition: 0
[   843.146]     DirectColorModeInfo: 0
[   843.146]     PhysBasePtr: 0xfb000000
[   843.146]     LinBytesPerScanLine: 320
[   843.146]     BnkNumberOfImagePages: 30
[   843.146]     LinNumberOfImagePages: 30
[   843.146]     LinRedMaskSize: 0
[   843.146]     LinRedFieldPosition: 0
[   843.146]     LinGreenMaskSize: 0
[   843.146]     LinGreenFieldPosition: 0
[   843.146]     LinBlueMaskSize: 0
[   843.146]     LinBlueFieldPosition: 0
[   843.146]     LinRsvdMaskSize: 0
[   843.146]     LinRsvdFieldPosition: 0
[   843.146]     MaxPixelClock: 229500000
[   843.148] Mode: 132 (320x400)
[   843.148]     ModeAttributes: 0x3bf
[   843.148]     WinAAttributes: 0x7
[   843.148]     WinBAttributes: 0x0
[   843.148]     WinGranularity: 64
[   843.148]     WinSize: 64
[   843.148]     WinASegment: 0xa000
[   843.148]     WinBSegment: 0x0
[   843.148]     WinFuncPtr: 0xc0008ec8
[   843.148]     BytesPerScanline: 640
[   843.148]     XResolution: 320
[   843.148]     YResolution: 400
[   843.148]     XCharSize: 8
[   843.148]     YCharSize: 16
[   843.148]     NumberOfPlanes: 1
[   843.148]     BitsPerPixel: 16
[   843.148]     NumberOfBanks: 1
[   843.148]     MemoryModel: 6
[   843.148]     BankSize: 0
[   843.148]     NumberOfImages: 14
[   843.148]     RedMaskSize: 5
[   843.148]     RedFieldPosition: 11
[   843.148]     GreenMaskSize: 6
[   843.148]     GreenFieldPosition: 5
[   843.148]     BlueMaskSize: 5
[   843.148]     BlueFieldPosition: 0
[   843.148]     RsvdMaskSize: 0
[   843.148]     RsvdFieldPosition: 0
[   843.148]     DirectColorModeInfo: 0
[   843.148]     PhysBasePtr: 0xfb000000
[   843.148]     LinBytesPerScanLine: 640
[   843.148]     BnkNumberOfImagePages: 14
[   843.148]     LinNumberOfImagePages: 14
[   843.149]     LinRedMaskSize: 5
[   843.149]     LinRedFieldPosition: 11
[   843.149]     LinGreenMaskSize: 6
[   843.149]     LinGreenFieldPosition: 5
[   843.149]     LinBlueMaskSize: 5
[   843.149]     LinBlueFieldPosition: 0
[   843.149]     LinRsvdMaskSize: 0
[   843.149]     LinRsvdFieldPosition: 0
[   843.149]     MaxPixelClock: 229500000
[   843.150] *Mode: 133 (320x400)
[   843.150]     ModeAttributes: 0x3bf
[   843.150]     WinAAttributes: 0x7
[   843.150]     WinBAttributes: 0x0
[   843.150]     WinGranularity: 64
[   843.150]     WinSize: 64
[   843.150]     WinASegment: 0xa000
[   843.150]     WinBSegment: 0x0
[   843.150]     WinFuncPtr: 0xc0008ec8
[   843.150]     BytesPerScanline: 1280
[   843.150]     XResolution: 320
[   843.150]     YResolution: 400
[   843.150]     XCharSize: 8
[   843.150]     YCharSize: 16
[   843.150]     NumberOfPlanes: 1
[   843.150]     BitsPerPixel: 32
[   843.150]     NumberOfBanks: 1
[   843.150]     MemoryModel: 6
[   843.150]     BankSize: 0
[   843.150]     NumberOfImages: 6
[   843.151]     RedMaskSize: 8
[   843.151]     RedFieldPosition: 16
[   843.151]     GreenMaskSize: 8
[   843.151]     GreenFieldPosition: 8
[   843.151]     BlueMaskSize: 8
[   843.151]     BlueFieldPosition: 0
[   843.151]     RsvdMaskSize: 8
[   843.151]     RsvdFieldPosition: 24
[   843.151]     DirectColorModeInfo: 0
[   843.151]     PhysBasePtr: 0xfb000000
[   843.151]     LinBytesPerScanLine: 1280
[   843.151]     BnkNumberOfImagePages: 6
[   843.151]     LinNumberOfImagePages: 6
[   843.151]     LinRedMaskSize: 8
[   843.151]     LinRedFieldPosition: 16
[   843.151]     LinGreenMaskSize: 8
[   843.151]     LinGreenFieldPosition: 8
[   843.151]     LinBlueMaskSize: 8
[   843.151]     LinBlueFieldPosition: 0
[   843.151]     LinRsvdMaskSize: 8
[   843.151]     LinRsvdFieldPosition: 24
[   843.151]     MaxPixelClock: 229500000
[   843.152] Mode: 134 (320x240)
[   843.152]     ModeAttributes: 0x3bf
[   843.152]     WinAAttributes: 0x7
[   843.152]     WinBAttributes: 0x0
[   843.152]     WinGranularity: 64
[   843.153]     WinSize: 64
[   843.153]     WinASegment: 0xa000
[   843.153]     WinBSegment: 0x0
[   843.153]     WinFuncPtr: 0xc0008ec8
[   843.153]     BytesPerScanline: 320
[   843.153]     XResolution: 320
[   843.153]     YResolution: 240
[   843.153]     XCharSize: 8
[   843.153]     YCharSize: 8
[   843.153]     NumberOfPlanes: 1
[   843.153]     BitsPerPixel: 8
[   843.153]     NumberOfBanks: 1
[   843.153]     MemoryModel: 4
[   843.153]     BankSize: 0
[   843.153]     NumberOfImages: 30
[   843.153]     RedMaskSize: 0
[   843.153]     RedFieldPosition: 0
[   843.153]     GreenMaskSize: 0
[   843.153]     GreenFieldPosition: 0
[   843.153]     BlueMaskSize: 0
[   843.153]     BlueFieldPosition: 0
[   843.153]     RsvdMaskSize: 0
[   843.153]     RsvdFieldPosition: 0
[   843.153]     DirectColorModeInfo: 0
[   843.153]     PhysBasePtr: 0xfb000000
[   843.153]     LinBytesPerScanLine: 320
[   843.153]     BnkNumberOfImagePages: 30
[   843.153]     LinNumberOfImagePages: 30
[   843.153]     LinRedMaskSize: 0
[   843.153]     LinRedFieldPosition: 0
[   843.153]     LinGreenMaskSize: 0
[   843.153]     LinGreenFieldPosition: 0
[   843.153]     LinBlueMaskSize: 0
[   843.153]     LinBlueFieldPosition: 0
[   843.153]     LinRsvdMaskSize: 0
[   843.153]     LinRsvdFieldPosition: 0
[   843.153]     MaxPixelClock: 229500000
[   843.155] Mode: 135 (320x240)
[   843.155]     ModeAttributes: 0x3bf
[   843.155]     WinAAttributes: 0x7
[   843.155]     WinBAttributes: 0x0
[   843.155]     WinGranularity: 64
[   843.155]     WinSize: 64
[   843.155]     WinASegment: 0xa000
[   843.155]     WinBSegment: 0x0
[   843.155]     WinFuncPtr: 0xc0008ec8
[   843.155]     BytesPerScanline: 640
[   843.155]     XResolution: 320
[   843.155]     YResolution: 240
[   843.155]     XCharSize: 8
[   843.155]     YCharSize: 8
[   843.155]     NumberOfPlanes: 1
[   843.155]     BitsPerPixel: 16
[   843.155]     NumberOfBanks: 1
[   843.155]     MemoryModel: 6
[   843.155]     BankSize: 0
[   843.155]     NumberOfImages: 19
[   843.155]     RedMaskSize: 5
[   843.155]     RedFieldPosition: 11
[   843.155]     GreenMaskSize: 6
[   843.155]     GreenFieldPosition: 5
[   843.155]     BlueMaskSize: 5
[   843.155]     BlueFieldPosition: 0
[   843.155]     RsvdMaskSize: 0
[   843.155]     RsvdFieldPosition: 0
[   843.155]     DirectColorModeInfo: 0
[   843.155]     PhysBasePtr: 0xfb000000
[   843.155]     LinBytesPerScanLine: 640
[   843.155]     BnkNumberOfImagePages: 19
[   843.155]     LinNumberOfImagePages: 19
[   843.155]     LinRedMaskSize: 5
[   843.155]     LinRedFieldPosition: 11
[   843.155]     LinGreenMaskSize: 6
[   843.155]     LinGreenFieldPosition: 5
[   843.155]     LinBlueMaskSize: 5
[   843.155]     LinBlueFieldPosition: 0
[   843.155]     LinRsvdMaskSize: 0
[   843.155]     LinRsvdFieldPosition: 0
[   843.155]     MaxPixelClock: 229500000
[   843.157] *Mode: 136 (320x240)
[   843.157]     ModeAttributes: 0x3bf
[   843.157]     WinAAttributes: 0x7
[   843.157]     WinBAttributes: 0x0
[   843.157]     WinGranularity: 64
[   843.157]     WinSize: 64
[   843.157]     WinASegment: 0xa000
[   843.157]     WinBSegment: 0x0
[   843.157]     WinFuncPtr: 0xc0008ec8
[   843.157]     BytesPerScanline: 1280
[   843.157]     XResolution: 320
[   843.157]     YResolution: 240
[   843.157]     XCharSize: 8
[   843.157]     YCharSize: 8
[   843.157]     NumberOfPlanes: 1
[   843.157]     BitsPerPixel: 32
[   843.157]     NumberOfBanks: 1
[   843.157]     MemoryModel: 6
[   843.157]     BankSize: 0
[   843.157]     NumberOfImages: 10
[   843.157]     RedMaskSize: 8
[   843.157]     RedFieldPosition: 16
[   843.157]     GreenMaskSize: 8
[   843.157]     GreenFieldPosition: 8
[   843.157]     BlueMaskSize: 8
[   843.157]     BlueFieldPosition: 0
[   843.157]     RsvdMaskSize: 8
[   843.157]     RsvdFieldPosition: 24
[   843.157]     DirectColorModeInfo: 0
[   843.157]     PhysBasePtr: 0xfb000000
[   843.157]     LinBytesPerScanLine: 1280
[   843.157]     BnkNumberOfImagePages: 10
[   843.157]     LinNumberOfImagePages: 10
[   843.157]     LinRedMaskSize: 8
[   843.157]     LinRedFieldPosition: 16
[   843.157]     LinGreenMaskSize: 8
[   843.157]     LinGreenFieldPosition: 8
[   843.157]     LinBlueMaskSize: 8
[   843.157]     LinBlueFieldPosition: 0
[   843.157]     LinRsvdMaskSize: 8
[   843.157]     LinRsvdFieldPosition: 24
[   843.157]     MaxPixelClock: 229500000
[   843.159] Mode: 13d (640x400)
[   843.159]     ModeAttributes: 0x3bf
[   843.159]     WinAAttributes: 0x7
[   843.159]     WinBAttributes: 0x0
[   843.159]     WinGranularity: 64
[   843.159]     WinSize: 64
[   843.159]     WinASegment: 0xa000
[   843.159]     WinBSegment: 0x0
[   843.159]     WinFuncPtr: 0xc0008ec8
[   843.159]     BytesPerScanline: 1280
[   843.159]     XResolution: 640
[   843.159]     YResolution: 400
[   843.159]     XCharSize: 8
[   843.159]     YCharSize: 16
[   843.159]     NumberOfPlanes: 1
[   843.159]     BitsPerPixel: 16
[   843.159]     NumberOfBanks: 1
[   843.159]     MemoryModel: 6
[   843.159]     BankSize: 0
[   843.159]     NumberOfImages: 6
[   843.159]     RedMaskSize: 5
[   843.159]     RedFieldPosition: 11
[   843.159]     GreenMaskSize: 6
[   843.159]     GreenFieldPosition: 5
[   843.159]     BlueMaskSize: 5
[   843.159]     BlueFieldPosition: 0
[   843.159]     RsvdMaskSize: 0
[   843.159]     RsvdFieldPosition: 0
[   843.159]     DirectColorModeInfo: 0
[   843.159]     PhysBasePtr: 0xfb000000
[   843.159]     LinBytesPerScanLine: 1280
[   843.159]     BnkNumberOfImagePages: 6
[   843.159]     LinNumberOfImagePages: 6
[   843.159]     LinRedMaskSize: 5
[   843.159]     LinRedFieldPosition: 11
[   843.159]     LinGreenMaskSize: 6
[   843.159]     LinGreenFieldPosition: 5
[   843.159]     LinBlueMaskSize: 5
[   843.159]     LinBlueFieldPosition: 0
[   843.159]     LinRsvdMaskSize: 0
[   843.159]     LinRsvdFieldPosition: 0
[   843.159]     MaxPixelClock: 229500000
[   843.161] *Mode: 13e (640x400)
[   843.161]     ModeAttributes: 0x3bf
[   843.161]     WinAAttributes: 0x7
[   843.161]     WinBAttributes: 0x0
[   843.161]     WinGranularity: 64
[   843.161]     WinSize: 64
[   843.161]     WinASegment: 0xa000
[   843.161]     WinBSegment: 0x0
[   843.161]     WinFuncPtr: 0xc0008ec8
[   843.161]     BytesPerScanline: 2560
[   843.161]     XResolution: 640
[   843.161]     YResolution: 400
[   843.161]     XCharSize: 8
[   843.161]     YCharSize: 16
[   843.161]     NumberOfPlanes: 1
[   843.161]     BitsPerPixel: 32
[   843.161]     NumberOfBanks: 1
[   843.161]     MemoryModel: 6
[   843.161]     BankSize: 0
[   843.161]     NumberOfImages: 2
[   843.161]     RedMaskSize: 8
[   843.161]     RedFieldPosition: 16
[   843.161]     GreenMaskSize: 8
[   843.161]     GreenFieldPosition: 8
[   843.161]     BlueMaskSize: 8
[   843.161]     BlueFieldPosition: 0
[   843.161]     RsvdMaskSize: 8
[   843.161]     RsvdFieldPosition: 24
[   843.161]     DirectColorModeInfo: 0
[   843.161]     PhysBasePtr: 0xfb000000
[   843.161]     LinBytesPerScanLine: 2560
[   843.161]     BnkNumberOfImagePages: 2
[   843.161]     LinNumberOfImagePages: 2
[   843.161]     LinRedMaskSize: 8
[   843.161]     LinRedFieldPosition: 16
[   843.161]     LinGreenMaskSize: 8
[   843.161]     LinGreenFieldPosition: 8
[   843.161]     LinBlueMaskSize: 8
[   843.161]     LinBlueFieldPosition: 0
[   843.161]     LinRsvdMaskSize: 8
[   843.161]     LinRsvdFieldPosition: 24
[   843.161]     MaxPixelClock: 229500000
[   843.163] Mode: 160 (1280x800)
[   843.163]     ModeAttributes: 0x3bf
[   843.163]     WinAAttributes: 0x7
[   843.163]     WinBAttributes: 0x0
[   843.163]     WinGranularity: 64
[   843.163]     WinSize: 64
[   843.163]     WinASegment: 0xa000
[   843.163]     WinBSegment: 0x0
[   843.163]     WinFuncPtr: 0xc0008ec8
[   843.163]     BytesPerScanline: 1280
[   843.163]     XResolution: 1280
[   843.163]     YResolution: 800
[   843.163]     XCharSize: 8
[   843.163]     YCharSize: 16
[   843.163]     NumberOfPlanes: 1
[   843.163]     BitsPerPixel: 8
[   843.163]     NumberOfBanks: 1
[   843.163]     MemoryModel: 4
[   843.163]     BankSize: 0
[   843.163]     NumberOfImages: 2
[   843.163]     RedMaskSize: 0
[   843.163]     RedFieldPosition: 0
[   843.163]     GreenMaskSize: 0
[   843.163]     GreenFieldPosition: 0
[   843.163]     BlueMaskSize: 0
[   843.163]     BlueFieldPosition: 0
[   843.163]     RsvdMaskSize: 0
[   843.163]     RsvdFieldPosition: 0
[   843.163]     DirectColorModeInfo: 0
[   843.163]     PhysBasePtr: 0xfb000000
[   843.163]     LinBytesPerScanLine: 1280
[   843.163]     BnkNumberOfImagePages: 2
[   843.163]     LinNumberOfImagePages: 2
[   843.163]     LinRedMaskSize: 0
[   843.163]     LinRedFieldPosition: 0
[   843.163]     LinGreenMaskSize: 0
[   843.163]     LinGreenFieldPosition: 0
[   843.163]     LinBlueMaskSize: 0
[   843.163]     LinBlueFieldPosition: 0
[   843.163]     LinRsvdMaskSize: 0
[   843.163]     LinRsvdFieldPosition: 0
[   843.163]     MaxPixelClock: 229500000
[   843.165] *Mode: 161 (1280x800)
[   843.165]     ModeAttributes: 0x3bf
[   843.165]     WinAAttributes: 0x7
[   843.165]     WinBAttributes: 0x0
[   843.165]     WinGranularity: 64
[   843.165]     WinSize: 64
[   843.165]     WinASegment: 0xa000
[   843.165]     WinBSegment: 0x0
[   843.165]     WinFuncPtr: 0xc0008ec8
[   843.165]     BytesPerScanline: 5120
[   843.165]     XResolution: 1280
[   843.165]     YResolution: 800
[   843.165]     XCharSize: 8
[   843.165]     YCharSize: 16
[   843.165]     NumberOfPlanes: 1
[   843.165]     BitsPerPixel: 32
[   843.165]     NumberOfBanks: 1
[   843.165]     MemoryModel: 6
[   843.165]     BankSize: 0
[   843.165]     NumberOfImages: 1
[   843.165]     RedMaskSize: 8
[   843.165]     RedFieldPosition: 16
[   843.165]     GreenMaskSize: 8
[   843.165]     GreenFieldPosition: 8
[   843.165]     BlueMaskSize: 8
[   843.165]     BlueFieldPosition: 0
[   843.165]     RsvdMaskSize: 8
[   843.165]     RsvdFieldPosition: 24
[   843.165]     DirectColorModeInfo: 0
[   843.165]     PhysBasePtr: 0xfb000000
[   843.165]     LinBytesPerScanLine: 5120
[   843.165]     BnkNumberOfImagePages: 1
[   843.165]     LinNumberOfImagePages: 1
[   843.165]     LinRedMaskSize: 8
[   843.165]     LinRedFieldPosition: 16
[   843.165]     LinGreenMaskSize: 8
[   843.165]     LinGreenFieldPosition: 8
[   843.165]     LinBlueMaskSize: 8
[   843.165]     LinBlueFieldPosition: 0
[   843.165]     LinRsvdMaskSize: 8
[   843.166]     LinRsvdFieldPosition: 24
[   843.166]     MaxPixelClock: 229500000
[   843.167] Mode: 162 (768x480)
[   843.167]     ModeAttributes: 0x3bf
[   843.167]     WinAAttributes: 0x7
[   843.167]     WinBAttributes: 0x0
[   843.167]     WinGranularity: 64
[   843.167]     WinSize: 64
[   843.167]     WinASegment: 0xa000
[   843.167]     WinBSegment: 0x0
[   843.167]     WinFuncPtr: 0xc0008ec8
[   843.167]     BytesPerScanline: 768
[   843.167]     XResolution: 768
[   843.167]     YResolution: 480
[   843.167]     XCharSize: 8
[   843.167]     YCharSize: 16
[   843.167]     NumberOfPlanes: 1
[   843.167]     BitsPerPixel: 8
[   843.167]     NumberOfBanks: 1
[   843.168]     MemoryModel: 4
[   843.168]     BankSize: 0
[   843.168]     NumberOfImages: 8
[   843.168]     RedMaskSize: 0
[   843.168]     RedFieldPosition: 0
[   843.168]     GreenMaskSize: 0
[   843.168]     GreenFieldPosition: 0
[   843.168]     BlueMaskSize: 0
[   843.168]     BlueFieldPosition: 0
[   843.168]     RsvdMaskSize: 0
[   843.168]     RsvdFieldPosition: 0
[   843.168]     DirectColorModeInfo: 0
[   843.168]     PhysBasePtr: 0xfb000000
[   843.168]     LinBytesPerScanLine: 768
[   843.168]     BnkNumberOfImagePages: 8
[   843.168]     LinNumberOfImagePages: 8
[   843.168]     LinRedMaskSize: 0
[   843.168]     LinRedFieldPosition: 0
[   843.168]     LinGreenMaskSize: 0
[   843.168]     LinGreenFieldPosition: 0
[   843.168]     LinBlueMaskSize: 0
[   843.168]     LinBlueFieldPosition: 0
[   843.168]     LinRsvdMaskSize: 0
[   843.168]     LinRsvdFieldPosition: 0
[   843.168]     MaxPixelClock: 229500000
[   843.170] Mode: 168 (1680x1050)
[   843.170]     ModeAttributes: 0x3bf
[   843.170]     WinAAttributes: 0x7
[   843.170]     WinBAttributes: 0x0
[   843.170]     WinGranularity: 64
[   843.170]     WinSize: 64
[   843.170]     WinASegment: 0xa000
[   843.170]     WinBSegment: 0x0
[   843.170]     WinFuncPtr: 0xc0008ec8
[   843.170]     BytesPerScanline: 1680
[   843.170]     XResolution: 1680
[   843.170]     YResolution: 1050
[   843.170]     XCharSize: 8
[   843.170]     YCharSize: 16
[   843.170]     NumberOfPlanes: 1
[   843.170]     BitsPerPixel: 8
[   843.170]     NumberOfBanks: 1
[   843.170]     MemoryModel: 4
[   843.170]     BankSize: 0
[   843.170]     NumberOfImages: 1
[   843.170]     RedMaskSize: 0
[   843.170]     RedFieldPosition: 0
[   843.170]     GreenMaskSize: 0
[   843.170]     GreenFieldPosition: 0
[   843.170]     BlueMaskSize: 0
[   843.170]     BlueFieldPosition: 0
[   843.170]     RsvdMaskSize: 0
[   843.170]     RsvdFieldPosition: 0
[   843.170]     DirectColorModeInfo: 0
[   843.170]     PhysBasePtr: 0xfb000000
[   843.170]     LinBytesPerScanLine: 1680
[   843.170]     BnkNumberOfImagePages: 1
[   843.170]     LinNumberOfImagePages: 1
[   843.170]     LinRedMaskSize: 0
[   843.170]     LinRedFieldPosition: 0
[   843.170]     LinGreenMaskSize: 0
[   843.170]     LinGreenFieldPosition: 0
[   843.170]     LinBlueMaskSize: 0
[   843.170]     LinBlueFieldPosition: 0
[   843.170]     LinRsvdMaskSize: 0
[   843.170]     LinRsvdFieldPosition: 0
[   843.170]     MaxPixelClock: 229500000
[   843.172] *Mode: 169 (1680x1050)
[   843.172]     ModeAttributes: 0x3bf
[   843.172]     WinAAttributes: 0x7
[   843.172]     WinBAttributes: 0x0
[   843.172]     WinGranularity: 64
[   843.172]     WinSize: 64
[   843.172]     WinASegment: 0xa000
[   843.172]     WinBSegment: 0x0
[   843.172]     WinFuncPtr: 0xc0008ec8
[   843.172]     BytesPerScanline: 6720
[   843.172]     XResolution: 1680
[   843.172]     YResolution: 1050
[   843.172]     XCharSize: 8
[   843.172]     YCharSize: 16
[   843.172]     NumberOfPlanes: 1
[   843.172]     BitsPerPixel: 32
[   843.172]     NumberOfBanks: 1
[   843.172]     MemoryModel: 6
[   843.172]     BankSize: 0
[   843.172]     NumberOfImages: 1
[   843.172]     RedMaskSize: 8
[   843.172]     RedFieldPosition: 16
[   843.172]     GreenMaskSize: 8
[   843.172]     GreenFieldPosition: 8
[   843.172]     BlueMaskSize: 8
[   843.172]     BlueFieldPosition: 0
[   843.172]     RsvdMaskSize: 8
[   843.172]     RsvdFieldPosition: 24
[   843.172]     DirectColorModeInfo: 0
[   843.172]     PhysBasePtr: 0xfb000000
[   843.172]     LinBytesPerScanLine: 6720
[   843.172]     BnkNumberOfImagePages: 1
[   843.172]     LinNumberOfImagePages: 1
[   843.172]     LinRedMaskSize: 8
[   843.172]     LinRedFieldPosition: 16
[   843.172]     LinGreenMaskSize: 8
[   843.172]     LinGreenFieldPosition: 8
[   843.172]     LinBlueMaskSize: 8
[   843.172]     LinBlueFieldPosition: 0
[   843.172]     LinRsvdMaskSize: 8
[   843.172]     LinRsvdFieldPosition: 24
[   843.172]     MaxPixelClock: 229500000
[   843.174] *Mode: 17b (1280x720)
[   843.174]     ModeAttributes: 0x3bf
[   843.174]     WinAAttributes: 0x7
[   843.174]     WinBAttributes: 0x0
[   843.174]     WinGranularity: 64
[   843.174]     WinSize: 64
[   843.174]     WinASegment: 0xa000
[   843.174]     WinBSegment: 0x0
[   843.174]     WinFuncPtr: 0xc0008ec8
[   843.174]     BytesPerScanline: 5120
[   843.174]     XResolution: 1280
[   843.174]     YResolution: 720
[   843.174]     XCharSize: 8
[   843.174]     YCharSize: 16
[   843.174]     NumberOfPlanes: 1
[   843.174]     BitsPerPixel: 32
[   843.174]     NumberOfBanks: 1
[   843.174]     MemoryModel: 6
[   843.174]     BankSize: 0
[   843.174]     NumberOfImages: 1
[   843.174]     RedMaskSize: 8
[   843.174]     RedFieldPosition: 16
[   843.174]     GreenMaskSize: 8
[   843.174]     GreenFieldPosition: 8
[   843.174]     BlueMaskSize: 8
[   843.174]     BlueFieldPosition: 0
[   843.174]     RsvdMaskSize: 8
[   843.174]     RsvdFieldPosition: 24
[   843.174]     DirectColorModeInfo: 0
[   843.174]     PhysBasePtr: 0xfb000000
[   843.174]     LinBytesPerScanLine: 5120
[   843.174]     BnkNumberOfImagePages: 1
[   843.174]     LinNumberOfImagePages: 1
[   843.174]     LinRedMaskSize: 8
[   843.174]     LinRedFieldPosition: 16
[   843.174]     LinGreenMaskSize: 8
[   843.174]     LinGreenFieldPosition: 8
[   843.174]     LinBlueMaskSize: 8
[   843.174]     LinBlueFieldPosition: 0
[   843.174]     LinRsvdMaskSize: 8
[   843.174]     LinRsvdFieldPosition: 24
[   843.174]     MaxPixelClock: 229500000
[   843.174] 
[   843.174] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[   843.174] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[   843.174] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[   843.174] (WW) VESA(0): Unable to estimate virtual size
[   843.174] (II) VESA(0): Not using built-in mode "1680x1050" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   843.174] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   843.174] (WW) VESA(0): No valid modes left. Trying less strict filter...
[   843.174] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[   843.174] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[   843.174] (WW) VESA(0): Unable to estimate virtual size
[   843.174] (II) VESA(0): Not using built-in mode "1680x1050" (hsync out of range)
[   843.175] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[   843.175] (II) VESA(0): Not using built-in mode "1280x800" (hsync out of range)
[   843.175] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[   843.175] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[   843.175] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[   843.175] (--) VESA(0): Virtual size is 1280x720 (pitch 1280)
[   843.175] (**) VESA(0): *Built-in mode "1280x720"
[   843.175] (**) VESA(0): *Built-in mode "800x600"
[   843.175] (**) VESA(0): *Built-in mode "640x480"
[   843.175] (**) VESA(0): *Built-in mode "640x400"
[   843.175] (**) VESA(0): *Built-in mode "320x400"
[   843.175] (==) VESA(0): DPI set to (96, 96)
[   843.175] (II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
[   843.176] (**) VESA(0): Using "Shadow Framebuffer"
[   843.176] (II) Loading sub module "shadow"
[   843.176] (II) LoadModule: "shadow"
[   843.176] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   843.176] (II) Module shadow: vendor="X.Org Foundation"
[   843.176]     compiled for 1.13.0, module version = 1.1.0
[   843.176]     ABI class: X.Org ANSI C Emulation, version 0.4
[   843.176] (II) Loading sub module "fb"
[   843.176] (II) LoadModule: "fb"
[   843.176] (II) Loading /usr/lib/xorg/modules/libfb.so
[   843.176] (II) Module fb: vendor="X.Org Foundation"
[   843.176]     compiled for 1.13.0, module version = 1.0.0
[   843.176]     ABI class: X.Org ANSI C Emulation, version 0.4
[   843.176] (II) UnloadModule: "modesetting"
[   843.176] (II) Unloading modesetting
[   843.176] (II) UnloadModule: "fbdev"
[   843.176] (II) Unloading fbdev
[   843.176] (II) UnloadSubModule: "fbdevhw"
[   843.176] (II) Unloading fbdevhw
[   843.176] (==) Depth 24 pixmap format is 32 bpp
[   843.176] (II) Loading sub module "int10"
[   843.176] (II) LoadModule: "int10"
[   843.176] (II) Loading /usr/lib/xorg/modules/libint10.so
[   843.176] (II) Module int10: vendor="X.Org Foundation"
[   843.176]     compiled for 1.13.0, module version = 1.0.0
[   843.176]     ABI class: X.Org Video Driver, version 13.0
[   843.176] (II) VESA(0): initializing int10
[   843.177] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   843.256] (II) VESA(0): VESA BIOS detected
[   843.256] (II) VESA(0): VESA VBE Version 3.0
[   843.256] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[   843.256] (II) VESA(0): VESA VBE OEM: NVIDIA
[   843.256] (II) VESA(0): VESA VBE OEM Software Rev: 98.148
[   843.256] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[   843.256] (II) VESA(0): VESA VBE OEM Product: G94 Board - 06100005
[   843.256] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[   843.260] (II) VESA(0): virtual address = 0x7fc32270a000,
    physical address = 0xfb000000, size = 14680064
[   843.265] (II) VESA(0): Setting up VESA Mode 0x17B (1280x720)
[   843.471] (==) VESA(0): Default visual is TrueColor
[   843.471] (==) VESA(0): Backing store disabled
[   843.471] (**) VESA(0): DPMS enabled
[   843.471] (==) RandR enabled
[   843.498] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   843.501] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   843.501] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   843.501] (II) LoadModule: "evdev"
[   843.501] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   843.501] (II) Module evdev: vendor="X.Org Foundation"
[   843.501]     compiled for 1.13.0, module version = 2.7.3
[   843.501]     Module class: X.Org XInput Driver
[   843.501]     ABI class: X.Org XInput driver, version 18.0
[   843.501] (II) Using input driver 'evdev' for 'Power Button'
[   843.501] (**) Power Button: always reports core events
[   843.501] (**) evdev: Power Button: Device: "/dev/input/event2"
[   843.501] (--) evdev: Power Button: Vendor 0 Product 0x1
[   843.501] (--) evdev: Power Button: Found keys
[   843.501] (II) evdev: Power Button: Configuring as keyboard
[   843.501] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   843.501] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   843.501] (**) Option "xkb_rules" "evdev"
[   843.501] (**) Option "xkb_model" "pc105"
[   843.501] (**) Option "xkb_layout" "sk"
[   843.502] (**) Option "xkb_variant" "qwerty_bksl"
[   843.503] (II) XKB: reuse xkmfile /var/lib/xkb/server-58057374D93C30C52CBE139116123236FFDE4C8A.xkm
[   843.504] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[   843.504] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   843.504] (II) Using input driver 'evdev' for 'Video Bus'
[   843.504] (**) Video Bus: always reports core events
[   843.504] (**) evdev: Video Bus: Device: "/dev/input/event4"
[   843.504] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   843.504] (--) evdev: Video Bus: Found keys
[   843.504] (II) evdev: Video Bus: Configuring as keyboard
[   843.504] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input4/event4"
[   843.504] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   843.504] (**) Option "xkb_rules" "evdev"
[   843.504] (**) Option "xkb_model" "pc105"
[   843.504] (**) Option "xkb_layout" "sk"
[   843.504] (**) Option "xkb_variant" "qwerty_bksl"
[   843.505] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   843.505] (II) No input driver specified, ignoring this device.
[   843.505] (II) This device may have been added with another device file.
[   843.505] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   843.505] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   843.505] (II) Using input driver 'evdev' for 'Power Button'
[   843.505] (**) Power Button: always reports core events
[   843.505] (**) evdev: Power Button: Device: "/dev/input/event1"
[   843.505] (--) evdev: Power Button: Vendor 0 Product 0x1
[   843.505] (--) evdev: Power Button: Found keys
[   843.505] (II) evdev: Power Button: Configuring as keyboard
[   843.505] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   843.505] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   843.505] (**) Option "xkb_rules" "evdev"
[   843.505] (**) Option "xkb_model" "pc105"
[   843.505] (**) Option "xkb_layout" "sk"
[   843.505] (**) Option "xkb_variant" "qwerty_bksl"
[   843.506] (II) config/udev: Adding input device Genius DeathTaker Gaming Mouse (/dev/input/event5)
[   843.506] (**) Genius DeathTaker Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[   843.506] (II) Using input driver 'evdev' for 'Genius DeathTaker Gaming Mouse'
[   843.506] (**) Genius DeathTaker Gaming Mouse: always reports core events
[   843.506] (**) evdev: Genius DeathTaker Gaming Mouse: Device: "/dev/input/event5"
[   843.506] (--) evdev: Genius DeathTaker Gaming Mouse: Vendor 0x458 Product 0xef
[   843.506] (--) evdev: Genius DeathTaker Gaming Mouse: Found keys
[   843.506] (II) evdev: Genius DeathTaker Gaming Mouse: Configuring as keyboard
[   843.506] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input5/event5"
[   843.506] (II) XINPUT: Adding extended input device "Genius DeathTaker Gaming Mouse" (type: KEYBOARD, id 9)
[   843.506] (**) Option "xkb_rules" "evdev"
[   843.506] (**) Option "xkb_model" "pc105"
[   843.506] (**) Option "xkb_layout" "sk"
[   843.506] (**) Option "xkb_variant" "qwerty_bksl"
[   843.507] (II) config/udev: Adding input device Genius DeathTaker Gaming Mouse (/dev/input/event6)
[   843.507] (**) Genius DeathTaker Gaming Mouse: Applying InputClass "evdev pointer catchall"
[   843.507] (**) Genius DeathTaker Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[   843.507] (II) Using input driver 'evdev' for 'Genius DeathTaker Gaming Mouse'
[   843.507] (**) Genius DeathTaker Gaming Mouse: always reports core events
[   843.507] (**) evdev: Genius DeathTaker Gaming Mouse: Device: "/dev/input/event6"
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Vendor 0x458 Product 0xef
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found 9 mouse buttons
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found scroll wheel(s)
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found relative axes
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found x and y relative axes
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found absolute axes
[   843.507] (II) evdev: Genius DeathTaker Gaming Mouse: Forcing absolute x/y axes to exist.
[   843.507] (--) evdev: Genius DeathTaker Gaming Mouse: Found keys
[   843.507] (II) evdev: Genius DeathTaker Gaming Mouse: Configuring as mouse
[   843.507] (II) evdev: Genius DeathTaker Gaming Mouse: Configuring as keyboard
[   843.507] (II) evdev: Genius DeathTaker Gaming Mouse: Adding scrollwheel support
[   843.507] (**) evdev: Genius DeathTaker Gaming Mouse: YAxisMapping: buttons 4 and 5
[   843.507] (**) evdev: Genius DeathTaker Gaming Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   843.507] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input6/event6"
[   843.507] (II) XINPUT: Adding extended input device "Genius DeathTaker Gaming Mouse" (type: KEYBOARD, id 10)
[   843.507] (**) Option "xkb_rules" "evdev"
[   843.507] (**) Option "xkb_model" "pc105"
[   843.507] (**) Option "xkb_layout" "sk"
[   843.507] (**) Option "xkb_variant" "qwerty_bksl"
[   843.507] (II) evdev: Genius DeathTaker Gaming Mouse: initialized for relative axes.
[   843.507] (WW) evdev: Genius DeathTaker Gaming Mouse: ignoring absolute axes.
[   843.507] (**) Genius DeathTaker Gaming Mouse: (accel) keeping acceleration scheme 1
[   843.507] (**) Genius DeathTaker Gaming Mouse: (accel) acceleration profile 0
[   843.507] (**) Genius DeathTaker Gaming Mouse: (accel) acceleration factor: 2.000
[   843.507] (**) Genius DeathTaker Gaming Mouse: (accel) acceleration threshold: 4
[   843.508] (II) config/udev: Adding input device Genius DeathTaker Gaming Mouse (/dev/input/mouse0)
[   843.508] (II) No input driver specified, ignoring this device.
[   843.508] (II) This device may have been added with another device file.
[   843.508] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   843.508] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   843.508] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   843.508] (**) AT Translated Set 2 keyboard: always reports core events
[   843.508] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   843.508] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   843.508] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   843.508] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   843.508] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   843.508] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   843.508] (**) Option "xkb_rules" "evdev"
[   843.508] (**) Option "xkb_model" "pc105"
[   843.508] (**) Option "xkb_layout" "sk"
[   843.508] (**) Option "xkb_variant" "qwerty_bksl"
[   843.509] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[   843.509] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   843.509] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   843.509] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   843.509] (II) LoadModule: "synaptics"
[   843.509] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   843.509] (II) Module synaptics: vendor="X.Org Foundation"
[   843.509]     compiled for 1.13.0, module version = 1.6.2
[   843.509]     Module class: X.Org XInput Driver
[   843.509]     ABI class: X.Org XInput driver, version 18.0
[   843.509] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   843.509] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   843.509] (**) Option "Device" "/dev/input/event9"
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   843.547] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   843.547] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   843.565] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[   843.565] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[   843.565] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   843.565] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   843.565] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[   843.565] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   843.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   843.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   843.565] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   843.565] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   843.566] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[   843.566] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   843.570] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (ene_ir) (/dev/input/event8)
[   843.570] (**) MCE IR Keyboard/Mouse (ene_ir): Applying InputClass "evdev pointer catchall"
[   843.570] (**) MCE IR Keyboard/Mouse (ene_ir): Applying InputClass "evdev keyboard catchall"
[   843.570] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (ene_ir)'
[   843.570] (**) MCE IR Keyboard/Mouse (ene_ir): always reports core events
[   843.570] (**) evdev: MCE IR Keyboard/Mouse (ene_ir): Device: "/dev/input/event8"
[   843.570] (--) evdev: MCE IR Keyboard/Mouse (ene_ir): Vendor 0 Product 0
[   843.570] (--) evdev: MCE IR Keyboard/Mouse (ene_ir): Found 3 mouse buttons
[   843.570] (--) evdev: MCE IR Keyboard/Mouse (ene_ir): Found relative axes
[   843.570] (--) evdev: MCE IR Keyboard/Mouse (ene_ir): Found x and y relative axes
[   843.570] (--) evdev: MCE IR Keyboard/Mouse (ene_ir): Found keys
[   843.570] (II) evdev: MCE IR Keyboard/Mouse (ene_ir): Configuring as mouse
[   843.570] (II) evdev: MCE IR Keyboard/Mouse (ene_ir): Configuring as keyboard
[   843.570] (**) evdev: MCE IR Keyboard/Mouse (ene_ir): YAxisMapping: buttons 4 and 5
[   843.570] (**) evdev: MCE IR Keyboard/Mouse (ene_ir): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   843.570] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[   843.570] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (ene_ir)" (type: KEYBOARD, id 13)
[   843.570] (**) Option "xkb_rules" "evdev"
[   843.570] (**) Option "xkb_model" "pc105"
[   843.570] (**) Option "xkb_layout" "sk"
[   843.570] (**) Option "xkb_variant" "qwerty_bksl"
[   843.571] (II) evdev: MCE IR Keyboard/Mouse (ene_ir): initialized for relative axes.
[   843.571] (**) MCE IR Keyboard/Mouse (ene_ir): (accel) keeping acceleration scheme 1
[   843.571] (**) MCE IR Keyboard/Mouse (ene_ir): (accel) acceleration profile 0
[   843.571] (**) MCE IR Keyboard/Mouse (ene_ir): (accel) acceleration factor: 2.000
[   843.571] (**) MCE IR Keyboard/Mouse (ene_ir): (accel) acceleration threshold: 4
[   843.571] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (ene_ir) (/dev/input/mouse1)
[   843.571] (II) No input driver specified, ignoring this device.
[   843.571] (II) This device may have been added with another device file.
[   843.572] (II) config/udev: Adding input device ENE eHome Infrared Remote Receiver (/dev/input/event7)
[   843.572] (**) ENE eHome Infrared Remote Receiver: Applying InputClass "evdev keyboard catchall"
[   843.572] (II) Using input driver 'evdev' for 'ENE eHome Infrared Remote Receiver'
[   843.572] (**) ENE eHome Infrared Remote Receiver: always reports core events
[   843.572] (**) evdev: ENE eHome Infrared Remote Receiver: Device: "/dev/input/event7"
[   843.572] (--) evdev: ENE eHome Infrared Remote Receiver: Vendor 0 Product 0
[   843.572] (--) evdev: ENE eHome Infrared Remote Receiver: Found keys
[   843.572] (II) evdev: ENE eHome Infrared Remote Receiver: Configuring as keyboard
[   843.572] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input7/event7"
[   843.572] (II) XINPUT: Adding extended input device "ENE eHome Infrared Remote Receiver" (type: KEYBOARD, id 14)
[   843.572] (**) Option "xkb_rules" "evdev"
[   843.572] (**) Option "xkb_model" "pc105"
[   843.572] (**) Option "xkb_layout" "sk"
[   843.572] (**) Option "xkb_variant" "qwerty_bksl"
[   872.680] (II) evdev: ENE eHome Infrared Remote Receiver: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: MCE IR Keyboard/Mouse (ene_ir): Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) UnloadModule: "synaptics"
[   872.681] (II) evdev: AT Translated Set 2 keyboard: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: Genius DeathTaker Gaming Mouse: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: Genius DeathTaker Gaming Mouse: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: Power Button: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: Video Bus: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.681] (II) evdev: Power Button: Close
[   872.681] (II) UnloadModule: "evdev"
[   872.683] Server terminated successfully (0). Closing log file.


```
i reinstaled packages gdm,lightdm,ubuntu-desktop,nvidia drivers and tried mess with xorg.conf (generate new) and now atleast i end up in tty when booting normal kernel
failsafe dont work

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 325.15  (buildmeister@swio-display-x64-rhel04-03)  Wed Jul 31 19:04:27 PDT 2013


Section "ServerLayout"
    Identifier     "Layout0"
    Screen         "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "unix/:7100"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
is there some backup of that configs ? there was around 100 of them wich ubuntu tweak delete


ty for any help

---

### Post by oldos2er on 2013-08-22
Moved to Absolute Beginners.

---

### Post by Perfect Storm on 2013-08-22
Try:
```
sudo apt-get remove --purge lightdm
sudo apt-get install lightdm xorg 
sudo nvidia-xconfig
sudo /etc/init.d/lightdm restart
```

Which version of nvidia driver do you use?

---


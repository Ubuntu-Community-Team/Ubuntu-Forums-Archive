---
title: "Screen resolution painfully low! Please help! (Ubuntu 12.04 - GMA 4500M - VGN-NS10L)"
date: 2013-09-16
forum: New to Ubuntu
---

### Post by chin2 on 2013-09-16
Hi all,

This is my first post on this forum. I have never used any Linux dist  before. Been a Windows user for 15+ years, and I am finally taking the  plunge and wanting to get into the wonderful world of Linux. I just did a  fresh install of Ubuntu 12.04LTS, and the problem I am having is that  the resolution my graphics card is putting out is painfully low compared  to what it was managing with Windows 7 installed. I imagine it is a  graphics driver issue of some kind, but being that I have never touched  Linux before today, I am hopelessly lost in trying to solve the issue. I  have done a fair bit of reading over the last couple of days, but the  posts that seem to address similar issues get a bit too technical for  me, and I get rather lost. So, I am here begging for some assistance  from someone who has vastly more experience than I, and is willing to  hold my hand through the process of fixing this, and answer any  irritatingly stupid questions I might have. I hope such a kind soul is  out there somewhere!

Right now I am running on a Sony Vaio, with a Dell 19" monitor connected  via VGA cable. The max resolution I can get on the laptop display is  1280x800, and on the VGA display 1024x768. When running Windows 7 and  current Intel drivers, I was able to output 1680x1050, and 1600x1200  respectively. So, one would assume that Linux drivers should be able to  achieve similar performance. Having never used Linux before, ever, I  have no idea whether this is the case, but I very much hope it is.  Following is some information that I hope should be helpful in  troubleshooting my query. Thanks in advance for the help.. :smile:

Details:

OS: Ubuntu 12.04
Machine: Sony Vaio VGN-NS10L
Architecture: Intel GL40
Processor: Intel Pentium Dual-Core T3200 / 2000 Mhz / L2 Cache 1024 kb
Memory: DDR2 - PC2-5300 (SO-DIMM) / 3072 MB/ 667nMhz
Graphic Card: Mobile Intel Graphics Media Accelerator 4500M
Laptop Display: WXGA 1280 x 800
VGA Display: Dell E196FPf 19" Flat Panel TFT LCD

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: Intel Open Source Technology Center

$ lspci -vvnn |grep Graphics
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4  Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)  (prog-if 00 [VGA controller])
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)

Xorg.0.log:
[    23.226] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    23.226] X Protocol Version 11, Revision 0
[    23.226] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    23.226] Current Operating System: Linux me-VGN-NS10L-S  3.8.0-30-generic #44~precise1-Ubuntu SMP Fri Aug 23 18:32:41 UTC 2013  x86_64
[    23.226] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-3.8.0-30-generic  root=UUID=b59bfced-e55e-4dc7-b3a6-cb9d8ca679bb ro quiet splash  vt.handoff=7
[    23.226] Build Date: 07 June 2013  09:48:08AM
[    23.226] xorg-server 2:1.13.3-0ubuntu6~precise2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    23.226] Current version of pixman: 0.24.4
[    23.226]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    23.226] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.226] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 16 15:44:38 2013
[    23.260] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.419] (==) No Layout section.  Using the first Screen section.
[    23.419] (==) No screen section available. Using defaults.
[    23.419] (**) |-->Screen "Default Screen Section" (0)
[    23.419] (**) |   |-->Monitor "<default monitor>"
[    23.419] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    23.419] (==) Automatically adding devices
[    23.419] (==) Automatically enabling devices
[    23.419] (==) Automatically adding GPU devices
[    23.530] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    23.530]     Entry deleted from font path.
[    23.530] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    23.530] (==) ModulePath set to  "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.530] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.530] (II) Loader magic: 0x7f07379ddc20
[    23.530] (II) Module ABI versions:
[    23.530]     X.Org ANSI C Emulation: 0.4
[    23.530]     X.Org Video Driver: 13.1
[    23.530]     X.Org XInput driver : 18.0
[    23.530]     X.Org Server Extension : 7.0
[    23.531] (II) config/udev: Adding drm device (/dev/dri/card0)
[    23.533] (--) PCI:*(0:0:2:0) 8086:2a42:104d:9045 rev 7, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e140/8
[    23.533] (--) PCI: (0:0:2:1) 8086:2a43:104d:9045 rev 7, Mem @ 0xd0400000/1048576
[    23.533] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.581] Initializing built-in extension Generic Event Extension
[    23.581] Initializing built-in extension SHAPE
[    23.581] Initializing built-in extension MIT-SHM
[    23.581] Initializing built-in extension XInputExtension
[    23.581] Initializing built-in extension XTEST
[    23.581] Initializing built-in extension BIG-REQUESTS
[    23.581] Initializing built-in extension SYNC
[    23.581] Initializing built-in extension XKEYBOARD
[    23.581] Initializing built-in extension XC-MISC
[    23.581] Initializing built-in extension SECURITY
[    23.581] Initializing built-in extension XINERAMA
[    23.581] Initializing built-in extension XFIXES
[    23.581] Initializing built-in extension RENDER
[    23.581] Initializing built-in extension RANDR
[    23.581] Initializing built-in extension COMPOSITE
[    23.581] Initializing built-in extension DAMAGE
[    23.581] Initializing built-in extension MIT-SCREEN-SAVER
[    23.581] Initializing built-in extension DOUBLE-BUFFER
[    23.581] Initializing built-in extension RECORD
[    23.581] Initializing built-in extension DPMS
[    23.581] Initializing built-in extension X-Resource
[    23.581] Initializing built-in extension XVideo
[    23.581] Initializing built-in extension XVideo-MotionCompensation
[    23.581] Initializing built-in extension XFree86-VidModeExtension
[    23.581] Initializing built-in extension XFree86-DGA
[    23.581] Initializing built-in extension XFree86-DRI
[    23.581] Initializing built-in extension DRI2
[    23.581] (II) LoadModule: "glx"
[    23.698] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.768] (II) Module glx: vendor="X.Org Foundation"
[    23.768]     compiled for 1.13.3, module version = 1.0.0
[    23.768]     ABI class: X.Org Server Extension, version 7.0
[    23.768] (==) AIGLX enabled
[    23.768] Loading extension GLX
[    23.768] (==) Matched intel as autoconfigured driver 0
[    23.768] (==) Matched intel as autoconfigured driver 1
[    23.768] (==) Matched vesa as autoconfigured driver 2
[    23.768] (==) Matched modesetting as autoconfigured driver 3
[    23.768] (==) Matched fbdev as autoconfigured driver 4
[    23.768] (==) Assigned the driver to the xf86ConfigLayout
[    23.768] (II) LoadModule: "intel"
[    23.769] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    23.892] (II) Module intel: vendor="X.Org Foundation"
[    23.892]     compiled for 1.13.3, module version = 2.21.6
[    23.892]     Module class: X.Org Video Driver
[    23.892]     ABI class: X.Org Video Driver, version 13.1
[    23.892] (II) LoadModule: "vesa"
[    23.892] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.902] (II) Module vesa: vendor="X.Org Foundation"
[    23.902]     compiled for 1.13.3, module version = 2.3.2
[    23.902]     Module class: X.Org Video Driver
[    23.902]     ABI class: X.Org Video Driver, version 13.1
[    23.902] (II) LoadModule: "modesetting"
[    23.902] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.913] (II) Module modesetting: vendor="X.Org Foundation"
[    23.913]     compiled for 1.13.3, module version = 0.7.0
[    23.913]     Module class: X.Org Video Driver
[    23.913]     ABI class: X.Org Video Driver, version 13.1
[    23.913] (II) LoadModule: "fbdev"
[    23.913] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.914] (II) Module fbdev: vendor="X.Org Foundation"
[    23.914]     compiled for 1.13.3, module version = 0.4.3
[    23.914]     Module class: X.Org Video Driver
[    23.914]     ABI class: X.Org Video Driver, version 13.1
[    23.914] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), HD Graphics, HD Graphics 4600,
    Haswell Desktop (GT3), HD Graphics, HD Graphics 4600,
    Haswell Mobile (GT3), HD Graphics, HD Graphics P4600/P4700,
    Haswell Server (GT3), Haswell (GT1), Haswell (GT2), Haswell (GT3),
    HD Graphics, Haswell (GT2), Haswell (GT3), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT3),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT3), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell SDV (GT1), Haswell SDV (GT2), Haswell SDV (GT3),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4400,
    HD Graphics 5000, Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Iris(TM) Graphics 5100, Haswell ULT (GT1), Haswell ULT (GT2),
    Iris(TM) Graphics 5100, HD Graphics, HD Graphics 4200,
    Iris(TM) Graphics 5100, Haswell CRW Desktop (GT1), HD Graphics 4600,
    Iris(TM) Pro Graphics 5200, Haswell CRW Mobile (GT1),
    HD Graphics 4600, Iris(TM) Pro Graphics 5200,
    Haswell CRW Server (GT1), Haswell CRW Server (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, Haswell CRW (GT1), Haswell CRW (GT2),
    Iris(TM) Pro Graphics 5200, ValleyView PO board
[    23.915] (II) VESA: driver for VESA chipsets: vesa
[    23.915] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.915] (II) FBDEV: driver for framebuffer: fbdev
[    23.915] (++) using VT number 7

[    23.936] (II) intel(0): SNA compiled:  xserver-xorg-video-intel-lts-raring 2:2.21.6-0ubuntu4.1~precise1  (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[    23.939] (WW) Falling back to old probe method for vesa
[    23.939] (WW) Falling back to old probe method for modesetting
[    23.939] (WW) Falling back to old probe method for fbdev
[    23.939] (II) Loading sub module "fbdevhw"
[    23.939] (II) LoadModule: "fbdevhw"
[    23.939] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.946] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.946]     compiled for 1.13.3, module version = 0.0.2
[    23.946]     ABI class: X.Org Video Driver, version 13.1
[    23.946] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    23.946] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    23.946] (==) intel(0): RGB weight 888
[    23.946] (==) intel(0): Default visual is TrueColor
[    23.946] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    23.947] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3
[    23.947] (**) intel(0): Framebuffer tiled
[    23.947] (**) intel(0): Pixmaps tiled
[    23.947] (**) intel(0): "Tear free" disabled
[    23.947] (**) intel(0): Forcing per-crtc-pixmaps? no
[    23.947] (II) intel(0): Output LVDS1 has no monitor section
[    23.948] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[    23.980] (II) intel(0): Output VGA1 has no monitor section
[    24.028] (II) intel(0): Output DP1 has no monitor section
[    24.028] (II) intel(0): EDID for output LVDS1
[    24.028] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    24.028] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    24.028] (II) intel(0): Printing probed modes for output LVDS1
[    24.028] (II) intel(0): Modeline "1280x800"x59.9   70.71  1280 1296 1344 1430  800 804 807 825 -hsync -vsync (49.4 kHz P)
[    24.028] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    24.028] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    24.028] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    24.028] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    24.060] (II) intel(0): EDID for output VGA1
[    24.108] (II) intel(0): EDID for output DP1
[    24.108] (II) intel(0): Output LVDS1 connected
[    24.108] (II) intel(0): Output VGA1 disconnected
[    24.108] (II) intel(0): Output DP1 disconnected
[    24.108] (II) intel(0): Using exact sizes for initial modes
[    24.108] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    24.108] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    24.108] (==) intel(0): DPI set to (96, 96)
[    24.108] (II) Loading sub module "dri2"
[    24.108] (II) LoadModule: "dri2"
[    24.108] (II) Module "dri2" already built-in
[    24.108] (II) UnloadModule: "vesa"
[    24.108] (II) Unloading vesa
[    24.108] (II) UnloadModule: "modesetting"
[    24.108] (II) Unloading modesetting
[    24.108] (II) UnloadModule: "fbdev"
[    24.108] (II) Unloading fbdev
[    24.108] (II) UnloadSubModule: "fbdevhw"
[    24.108] (II) Unloading fbdevhw
[    24.108] (==) Depth 24 pixmap format is 32 bpp
[    24.136] (II) intel(0): SNA initialized with Broadwater/Crestline backend
[    24.136] (==) intel(0): Backing store disabled
[    24.136] (==) intel(0): Silken mouse enabled
[    24.136] (II) intel(0): HW Cursor enabled
[    24.136] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    24.138] (==) intel(0): DPMS enabled
[    24.139] (II) intel(0): Overlay video not supported on this hardware
[    24.139] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    24.139] (II) intel(0): [DRI2] Setup complete
[    24.139] (II) intel(0): [DRI2]   DRI driver: i965
[    24.139] (II) intel(0): direct rendering: DRI2 Enabled
[    24.139] (==) intel(0): hotplug detection: "enabled"
[    24.139] (--) RandR disabled
[    24.320] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    24.320] (II) AIGLX: enabled GLX_INTEL_swap_event
[    24.320] (II) AIGLX: enabled GLX_ARB_create_context
[    24.320] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    24.320] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    24.320] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    24.320] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    24.320] (II) AIGLX: Loaded and initialized i965
[    24.320] (II) GLX: Initialized DRI2 GL provider for screen 0
[    24.321] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[    24.372] (II) intel(0): Setting screen physical size to 338 x 211
[    24.494] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.510] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[    24.511] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    24.511] (II) LoadModule: "evdev"
[    24.511] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.536] (II) Module evdev: vendor="X.Org Foundation"
[    24.537]     compiled for 1.13.3, module version = 2.7.3
[    24.537]     Module class: X.Org XInput Driver
[    24.537]     ABI class: X.Org XInput driver, version 18.0
[    24.537] (II) Using input driver 'evdev' for 'Video Bus'
[    24.537] (**) Video Bus: always reports core events
[    24.537] (**) evdev: Video Bus: Device: "/dev/input/event3"
[    24.537] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    24.537] (--) evdev: Video Bus: Found keys
[    24.537] (II) evdev: Video Bus: Configuring as keyboard
[    24.537] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3/event3"
[    24.537] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    24.537] (**) Option "xkb_rules" "evdev"
[    24.537] (**) Option "xkb_model" "pc105"
[    24.537] (**) Option "xkb_layout" "gb"
[    24.541] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    24.561] (II) config/udev: Adding input device Sony Vaio Keys (/dev/input/event4)
[    24.561] (**) Sony Vaio Keys: Applying InputClass "evdev keyboard catchall"
[    24.561] (II) Using input driver 'evdev' for 'Sony Vaio Keys'
[    24.561] (**) Sony Vaio Keys: always reports core events
[    24.561] (**) evdev: Sony Vaio Keys: Device: "/dev/input/event4"
[    24.561] (--) evdev: Sony Vaio Keys: Vendor 0x104d Product 0
[    24.561] (--) evdev: Sony Vaio Keys: Found keys
[    24.561] (II) evdev: Sony Vaio Keys: Configuring as keyboard
[    24.561] (**) Option "config_info"  "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input4/event4"
[    24.561] (II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD, id 7)
[    24.561] (**) Option "xkb_rules" "evdev"
[    24.561] (**) Option "xkb_model" "pc105"
[    24.561] (**) Option "xkb_layout" "gb"
[    24.562] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/event5)
[    24.562] (II) No input driver specified, ignoring this device.
[    24.562] (II) This device may have been added with another device file.
[    24.562] (II) config/udev: Adding input device Sony Vaio Jogdial (/dev/input/mouse0)
[    24.562] (II) No input driver specified, ignoring this device.
[    24.562] (II) This device may have been added with another device file.
[    24.562] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.562] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.562] (II) Using input driver 'evdev' for 'Power Button'
[    24.562] (**) Power Button: always reports core events
[    24.562] (**) evdev: Power Button: Device: "/dev/input/event1"
[    24.563] (--) evdev: Power Button: Vendor 0 Product 0x1
[    24.563] (--) evdev: Power Button: Found keys
[    24.563] (II) evdev: Power Button: Configuring as keyboard
[    24.563] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    24.563] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    24.563] (**) Option "xkb_rules" "evdev"
[    24.563] (**) Option "xkb_model" "pc105"
[    24.563] (**) Option "xkb_layout" "gb"
[    24.563] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    24.563] (II) No input driver specified, ignoring this device.
[    24.563] (II) This device may have been added with another device file.
[    24.563] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    24.563] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    24.564] (II) config/udev: Adding input device UVC Camera (05ca:18b3) (/dev/input/event7)
[    24.564] (**) UVC Camera (05ca:18b3): Applying InputClass "evdev keyboard catchall"
[    24.564] (II) Using input driver 'evdev' for 'UVC Camera (05ca:18b3)'
[    24.564] (**) UVC Camera (05ca:18b3): always reports core events
[    24.564] (**) evdev: UVC Camera (05ca:18b3): Device: "/dev/input/event7"
[    24.564] (--) evdev: UVC Camera (05ca:18b3): Vendor 0x5ca Product 0x18b3
[    24.564] (--) evdev: UVC Camera (05ca:18b3): Found keys
[    24.564] (II) evdev: UVC Camera (05ca:18b3): Configuring as keyboard
[    24.564] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input7/event7"
[    24.564] (II) XINPUT: Adding extended input device "UVC Camera (05ca:18b3)" (type: KEYBOARD, id 9)
[    24.564] (**) Option "xkb_rules" "evdev"
[    24.564] (**) Option "xkb_model" "pc105"
[    24.564] (**) Option "xkb_layout" "gb"
[    24.565] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    24.565] (II) No input driver specified, ignoring this device.
[    24.565] (II) This device may have been added with another device file.
[    24.565] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    24.565] (II) No input driver specified, ignoring this device.
[    24.565] (II) This device may have been added with another device file.
[    24.566] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    24.566] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    24.566] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    24.566] (**) AT Translated Set 2 keyboard: always reports core events
[    24.566] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    24.566] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    24.566] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    24.566] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    24.566] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    24.566] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    24.566] (**) Option "xkb_rules" "evdev"
[    24.566] (**) Option "xkb_model" "pc105"
[    24.566] (**) Option "xkb_layout" "gb"
[    24.567] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    24.567] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    24.567] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    24.567] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    24.567] (II) LoadModule: "synaptics"
[    24.567] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    24.587] (II) Module synaptics: vendor="X.Org Foundation"
[    24.587]     compiled for 1.13.3, module version = 1.6.2
[    24.587]     Module class: X.Org XInput Driver
[    24.587]     ABI class: X.Org XInput driver, version 18.0
[    24.587] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    24.587] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.587] (**) Option "Device" "/dev/input/event6"
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5696
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5232
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    24.592] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    24.592] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    24.592] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    24.592] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    24.592] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    24.592] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    24.592] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    24.592] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    24.592] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    24.593] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    24.593] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    24.593] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    24.593] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    24.593] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    58.054] (II) XKB: reuse xkmfile /var/lib/xkb/server-4E634B280B0E5C069EA80E39EF9080F0A8FC0600.xkm
[  2286.368] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2286.443] (II) intel(0): switch to mode 1024x768 on crtc 4 (pipe 1)
[  2291.094] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2294.473] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2294.539] (II) intel(0): switch to mode 1024x768 on crtc 4 (pipe 1)
[  2589.253] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2589.290] (II) intel(0): switch to mode 1024x768 on crtc 4 (pipe 1)
[  2589.329] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2782.424] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2801.996] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  2802.010] (II) intel(0): switch to mode 1024x768 on crtc 4 (pipe 1)
[  2802.049] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  4739.996] (II) intel(0): switch to mode 1280x800 on crtc 3 (pipe 0)
[  4740.037] (II) intel(0): switch to mode 1024x768 on crtc 4 (pipe 1)

PS. Apologies for the long log. :-/

---


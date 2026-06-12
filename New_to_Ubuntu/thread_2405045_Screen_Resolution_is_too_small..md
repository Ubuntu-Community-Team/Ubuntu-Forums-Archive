---
title: "Screen Resolution is too small."
date: 2018-10-31
forum: New to Ubuntu
---

### Post by billy-fergy on 2018-10-31
Hi, I'm using Lubuntu-core on Ubuntu server 18.04, and I can't improve the resolution past 1024*768. 
I only have one monitor, but xrandr returns
```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-0 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94  
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00 +
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00* 
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08
```

The actual monitor is VGA-0, and I'm not sure what the problem is. I've tried installing drivers and updating software but I'm not sure where I'm going wrong. Monitor Settings don't give me an option to make the resolution better.

Here is var/log/Xorg.0.log
```
[    48.087] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    48.088] X Protocol Version 11, Revision 0
[    48.088] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[    48.088] Current Operating System: Linux ubuntu1804 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64
[    48.088] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=c68234be-dc3e-11e8-8b74-00237d24134c ro maybe-ubiquity
[    48.088] Build Date: 25 October 2018  04:11:27PM
[    48.088] xorg-server 2:1.19.6-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    48.088] Current version of pixman: 0.34.0
[    48.088]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    48.088] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    48.088] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 31 16:14:01 2018
[    48.098] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    48.131] (==) No Layout section.  Using the first Screen section.
[    48.131] (==) No screen section available. Using defaults.
[    48.131] (**) |-->Screen "Default Screen Section" (0)
[    48.131] (**) |   |-->Monitor "<default monitor>"
[    48.139] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    48.139] (==) Automatically adding devices
[    48.139] (==) Automatically enabling devices
[    48.139] (==) Automatically adding GPU devices
[    48.139] (==) Automatically binding GPU devices
[    48.139] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    48.385] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    48.385]     Entry deleted from font path.
[    48.385] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    48.385] (==) ModulePath set to "/usr/lib/xorg/modules"
[    48.385] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    48.386] (II) Loader magic: 0x5570e2906020
[    48.386] (II) Module ABI versions:
[    48.386]     X.Org ANSI C Emulation: 0.4
[    48.386]     X.Org Video Driver: 23.0
[    48.386]     X.Org XInput driver : 24.1
[    48.386]     X.Org Server Extension : 10.0
[    48.387] (++) using VT number 7

[    48.387] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    48.388] (II) xfree86: Adding drm device (/dev/dri/card0)
[    48.396] (--) PCI:*(0:1:3:0) 1002:515e:103c:31fb rev 2, Mem @ 0xd8000000/134217728, 0xf7ff0000/65536, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    48.397] (II) LoadModule: "glx"
[    48.527] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    48.829] (II) Module glx: vendor="X.Org Foundation"
[    48.829]     compiled for 1.19.6, module version = 1.0.0
[    48.829]     ABI class: X.Org Server Extension, version 10.0
[    48.829] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[    48.829]     loading driver: radeon
[    48.829] (==) Matched radeon as autoconfigured driver 0
[    48.829] (==) Matched ati as autoconfigured driver 1
[    48.829] (==) Matched ati as autoconfigured driver 2
[    48.829] (==) Matched modesetting as autoconfigured driver 3
[    48.829] (==) Matched fbdev as autoconfigured driver 4
[    48.829] (==) Matched vesa as autoconfigured driver 5
[    48.829] (==) Assigned the driver to the xf86ConfigLayout
[    48.829] (II) LoadModule: "radeon"
[    48.829] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    48.904] (II) Module radeon: vendor="X.Org Foundation"
[    48.904]     compiled for 1.19.6, module version = 18.0.1
[    48.904]     Module class: X.Org Video Driver
[    48.904]     ABI class: X.Org Video Driver, version 23.0
[    48.904] (II) LoadModule: "ati"
[    48.904] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    48.915] (II) Module ati: vendor="X.Org Foundation"
[    48.915]     compiled for 1.19.6, module version = 18.0.1
[    48.915]     Module class: X.Org Video Driver
[    48.915]     ABI class: X.Org Video Driver, version 23.0
[    48.916] (II) LoadModule: "modesetting"
[    48.916] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    48.924] (II) Module modesetting: vendor="X.Org Foundation"
[    48.924]     compiled for 1.19.6, module version = 1.19.6
[    48.924]     Module class: X.Org Video Driver
[    48.924]     ABI class: X.Org Video Driver, version 23.0
[    48.924] (II) LoadModule: "fbdev"
[    48.924] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    48.951] (II) Module fbdev: vendor="X.Org Foundation"
[    48.951]     compiled for 1.19.3, module version = 0.4.4
[    48.951]     Module class: X.Org Video Driver
[    48.951]     ABI class: X.Org Video Driver, version 23.0
[    48.951] (II) LoadModule: "vesa"
[    48.951] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    48.956] (II) Module vesa: vendor="X.Org Foundation"
[    48.956]     compiled for 1.19.3, module version = 2.3.4
[    48.956]     Module class: X.Org Video Driver
[    48.956]     ABI class: X.Org Video Driver, version 23.0
[    48.956] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[    48.961] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    48.961] (II) FBDEV: driver for framebuffer: fbdev
[    48.961] (II) VESA: driver for VESA chipsets: vesa
[    49.011] (II) [KMS] Kernel modesetting enabled.
[    49.011] (WW) Falling back to old probe method for modesetting
[    49.011] (WW) Falling back to old probe method for fbdev
[    49.011] (II) Loading sub module "fbdevhw"
[    49.011] (II) LoadModule: "fbdevhw"
[    49.011] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    49.030] (II) Module fbdevhw: vendor="X.Org Foundation"
[    49.030]     compiled for 1.19.6, module version = 0.0.2
[    49.030]     ABI class: X.Org Video Driver, version 23.0
[    49.030] (WW) Falling back to old probe method for vesa
[    49.030] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    49.030] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    49.030] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    49.030] (==) RADEON(0): Default visual is TrueColor
[    49.030] (==) RADEON(0): RGB weight 888
[    49.030] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    49.030] (--) RADEON(0): Chipset: "ATI ES1000" (ChipID = 0x515e)
[    49.030] (II) Loading sub module "fb"
[    49.030] (II) LoadModule: "fb"
[    49.030] (II) Loading /usr/lib/xorg/modules/libfb.so
[    49.053] (II) Module fb: vendor="X.Org Foundation"
[    49.053]     compiled for 1.19.6, module version = 1.0.0
[    49.053]     ABI class: X.Org ANSI C Emulation, version 0.4
[    49.053] (II) Loading sub module "dri2"
[    49.053] (II) LoadModule: "dri2"
[    49.053] (II) Module "dri2" already built-in
[    49.053] (II) Loading sub module "exa"
[    49.053] (II) LoadModule: "exa"
[    49.053] (II) Loading /usr/lib/xorg/modules/libexa.so
[    49.065] (II) Module exa: vendor="X.Org Foundation"
[    49.065]     compiled for 1.19.6, module version = 2.6.0
[    49.065]     ABI class: X.Org Video Driver, version 23.0
[    49.071] (II) RADEON(0): KMS Color Tiling: disabled
[    49.071] (II) RADEON(0): KMS Color Tiling 2D: disabled
[    49.071] (==) RADEON(0): TearFree property default: auto
[    49.071] (II) RADEON(0): KMS Pageflipping: enabled
[    49.071] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    49.073] (II) RADEON(0): Output VGA-0 has no monitor section
[    49.107] (II) RADEON(0): Output VGA-1 has no monitor section
[    49.109] (II) RADEON(0): EDID for output VGA-0
[    49.109] (II) RADEON(0): Printing probed modes for output VGA-0
[    49.109] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.109] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.109] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.109] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    49.109] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.142] (II) RADEON(0): EDID for output VGA-1
[    49.142] (II) RADEON(0): Manufacturer: AOC  Model: 246a  Serial#: 38795
[    49.142] (II) RADEON(0): Year: 2017  Week: 47
[    49.142] (II) RADEON(0): EDID Version: 1.3
[    49.142] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    49.142] (II) RADEON(0): Sync:  Separate
[    49.142] (II) RADEON(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[    49.142] (II) RADEON(0): Gamma: 2.20
[    49.142] (II) RADEON(0): DPMS capabilities: Off; RGB/Color Display
[    49.142] (II) RADEON(0): First detailed timing is preferred mode
[    49.143] (II) RADEON(0): redX: 0.650 redY: 0.334   greenX: 0.332 greenY: 0.623
[    49.143] (II) RADEON(0): blueX: 0.157 blueY: 0.053   whiteX: 0.313 whiteY: 0.329
[    49.143] (II) RADEON(0): Supported established timings:
[    49.143] (II) RADEON(0): 720x400@70Hz
[    49.143] (II) RADEON(0): 640x480@60Hz
[    49.143] (II) RADEON(0): 640x480@67Hz
[    49.143] (II) RADEON(0): 640x480@72Hz
[    49.143] (II) RADEON(0): 640x480@75Hz
[    49.143] (II) RADEON(0): 800x600@56Hz
[    49.143] (II) RADEON(0): 800x600@60Hz
[    49.143] (II) RADEON(0): 800x600@72Hz
[    49.143] (II) RADEON(0): 800x600@75Hz
[    49.143] (II) RADEON(0): 832x624@75Hz
[    49.143] (II) RADEON(0): 1024x768@60Hz
[    49.143] (II) RADEON(0): 1024x768@70Hz
[    49.143] (II) RADEON(0): 1024x768@75Hz
[    49.143] (II) RADEON(0): 1280x1024@75Hz
[    49.143] (II) RADEON(0): Manufacturer's mask: 0
[    49.143] (II) RADEON(0): Supported standard timings:
[    49.143] (II) RADEON(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    49.143] (II) RADEON(0): #1: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    49.143] (II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    49.143] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    49.143] (II) RADEON(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    49.143] (II) RADEON(0): #5: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    49.143] (II) RADEON(0): Supported detailed timing:
[    49.143] (II) RADEON(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[    49.143] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    49.143] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    49.143] (II) RADEON(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    49.143] (II) RADEON(0): Monitor name: 2460
[    49.143] (II) RADEON(0): Serial No: GJPHBHA038795
[    49.143] (II) RADEON(0): EDID (in hex):
[    49.143] (II) RADEON(0):     00ffffffffffff0005e36a248b970000
[    49.143] (II) RADEON(0):     2f1b010368351e782aa265a655559f28
[    49.143] (II) RADEON(0):     0d5054bfef00d1c0b300950081808140
[    49.143] (II) RADEON(0):     81c001010101023a801871382d40582c
[    49.143] (II) RADEON(0):     4500132b2100001e000000fd00324c1e
[    49.143] (II) RADEON(0):     5311000a202020202020000000fc0032
[    49.143] (II) RADEON(0):     3436300a2020202020202020000000ff
[    49.143] (II) RADEON(0):     00474a5048424841303338373935006a
[    49.143] (II) RADEON(0): Printing probed modes for output VGA-1
[    49.143] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    49.143] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    49.143] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    49.143] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    49.143] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    49.143] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    49.143] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    49.143] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    49.143] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    49.143] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    49.143] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    49.143] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    49.143] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    49.143] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    49.143] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    49.143] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    49.143] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    49.144] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    49.144] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    49.144] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    49.144] (II) RADEON(0): Output VGA-0 connected
[    49.144] (II) RADEON(0): Output VGA-1 connected
[    49.144] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    49.144] (II) RADEON(0): Output VGA-0 using initial mode 1024x768 +0+0
[    49.144] (II) RADEON(0): Output VGA-1 using initial mode 1024x768 +0+0
[    49.144] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:2000000 visible:3e40000
[    49.144] (II) RADEON(0): EXA: Driver will not allow EXA pixmaps in VRAM
[    49.144] (==) RADEON(0): DPI set to (96, 96)
[    49.144] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    49.144] (II) Loading sub module "ramdac"
[    49.144] (II) LoadModule: "ramdac"
[    49.144] (II) Module "ramdac" already built-in
[    49.144] (II) UnloadModule: "modesetting"
[    49.144] (II) Unloading modesetting
[    49.144] (II) UnloadModule: "fbdev"
[    49.144] (II) Unloading fbdev
[    49.144] (II) UnloadSubModule: "fbdevhw"
[    49.144] (II) Unloading fbdevhw
[    49.144] (II) UnloadModule: "vesa"
[    49.144] (II) Unloading vesa
[    49.144] (--) Depth 24 pixmap format is 32 bpp
[    49.145] (II) RADEON(0): [DRI2] Setup complete
[    49.145] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    49.145] (II) RADEON(0): Front buffer size: 3072K
[    49.145] (II) RADEON(0): VRAM usage limit set to 54590K
[    49.147] (==) RADEON(0): DRI3 disabled
[    49.147] (==) RADEON(0): Backing store enabled
[    49.147] (II) RADEON(0): Direct rendering enabled
[    49.147] (II) EXA(0): Driver allocated offscreen pixmaps
[    49.147] (II) EXA(0): Driver registered support for the following operations:
[    49.147] (II)         Solid
[    49.147] (II)         Copy
[    49.147] (II)         UploadToScreen
[    49.147] (II)         DownloadFromScreen
[    49.147] (II) RADEON(0): Acceleration enabled
[    49.147] (==) RADEON(0): DPMS enabled
[    49.147] (==) RADEON(0): Silken mouse enabled
[    49.147] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    49.148] (--) RandR disabled
[    49.160] (II) SELinux: Disabled on system
[    49.361] (EE) AIGLX error: Calling driver entry point failed
[    49.369] (EE) AIGLX: reverting to software rendering
[    50.584] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[    50.585] (II) IGLX: Loaded and initialized swrast
[    50.585] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    50.586] (II) RADEON(0): Setting screen physical size to 270 x 203
[    51.659] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    51.659] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    51.659] (II) LoadModule: "libinput"
[    51.675] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    51.746] (II) Module libinput: vendor="X.Org Foundation"
[    51.746]     compiled for 1.19.6, module version = 0.27.1
[    51.746]     Module class: X.Org XInput Driver
[    51.746]     ABI class: X.Org XInput driver, version 24.1
[    51.746] (II) Using input driver 'libinput' for 'Power Button'
[    51.746] (**) Power Button: always reports core events
[    51.747] (**) Option "Device" "/dev/input/event0"
[    51.747] (**) Option "_source" "server/udev"
[    51.747] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    51.747] (II) event0  - Power Button: device is a keyboard
[    51.747] (II) event0  - Power Button: device removed
[    51.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[    51.764] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    51.764] (**) Option "xkb_model" "pc105"
[    51.764] (**) Option "xkb_layout" "gb"
[    51.788] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    51.788] (II) event0  - Power Button: device is a keyboard
[    51.789] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event3)
[    51.789] (**) Microsoft Wired Keyboard 600: Applying InputClass "libinput keyboard catchall"
[    51.789] (II) Using input driver 'libinput' for 'Microsoft Wired Keyboard 600'
[    51.789] (**) Microsoft Wired Keyboard 600: always reports core events
[    51.789] (**) Option "Device" "/dev/input/event3"
[    51.789] (**) Option "_source" "server/udev"
[    51.790] (II) event3  - Microsoft Wired Keyboard 600: is tagged by udev as: Keyboard
[    51.790] (II) event3  - Microsoft Wired Keyboard 600: device is a keyboard
[    51.790] (II) event3  - Microsoft Wired Keyboard 600: device removed
[    51.808] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/0003:045E:07F8.0003/input/input6/event3"
[    51.808] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 7)
[    51.808] (**) Option "xkb_model" "pc105"
[    51.808] (**) Option "xkb_layout" "gb"
[    51.809] (II) event3  - Microsoft Wired Keyboard 600: is tagged by udev as: Keyboard
[    51.809] (II) event3  - Microsoft Wired Keyboard 600: device is a keyboard
[    51.810] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event4)
[    51.810] (**) Microsoft Wired Keyboard 600: Applying InputClass "libinput keyboard catchall"
[    51.810] (II) Using input driver 'libinput' for 'Microsoft Wired Keyboard 600'
[    51.810] (**) Microsoft Wired Keyboard 600: always reports core events
[    51.810] (**) Option "Device" "/dev/input/event4"
[    51.810] (**) Option "_source" "server/udev"
[    51.811] (II) event4  - Microsoft Wired Keyboard 600: is tagged by udev as: Keyboard
[    51.811] (II) event4  - Microsoft Wired Keyboard 600: device is a keyboard
[    51.811] (II) event4  - Microsoft Wired Keyboard 600: device removed
[    51.824] (II) libinput: Microsoft Wired Keyboard 600: needs a virtual subdevice
[    51.824] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/0003:045E:07F8.0004/input/input7/event4"
[    51.824] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: MOUSE, id 8)
[    51.824] (**) Option "AccelerationScheme" "none"
[    51.824] (**) Microsoft Wired Keyboard 600: (accel) selected scheme none/0
[    51.824] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[    51.824] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
[    51.825] (II) event4  - Microsoft Wired Keyboard 600: is tagged by udev as: Keyboard
[    51.825] (II) event4  - Microsoft Wired Keyboard 600: device is a keyboard
[    51.826] (II) config/udev: Adding input device PixArt Microsoft USB Optical Mouse (/dev/input/event5)
[    51.826] (**) PixArt Microsoft USB Optical Mouse: Applying InputClass "libinput pointer catchall"
[    51.826] (II) Using input driver 'libinput' for 'PixArt Microsoft USB Optical Mouse'
[    51.826] (**) PixArt Microsoft USB Optical Mouse: always reports core events
[    51.826] (**) Option "Device" "/dev/input/event5"
[    51.826] (**) Option "_source" "server/udev"
[    51.888] (II) event5  - PixArt Microsoft USB Optical Mouse: is tagged by udev as: Mouse
[    51.888] (II) event5  - PixArt Microsoft USB Optical Mouse: device is a pointer
[    51.888] (II) event5  - PixArt Microsoft USB Optical Mouse: device removed
[    51.944] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/0003:045E:00CB.0005/input/input8/event5"
[    51.944] (II) XINPUT: Adding extended input device "PixArt Microsoft USB Optical Mouse" (type: MOUSE, id 9)
[    51.944] (**) Option "AccelerationScheme" "none"
[    51.944] (**) PixArt Microsoft USB Optical Mouse: (accel) selected scheme none/0
[    51.944] (**) PixArt Microsoft USB Optical Mouse: (accel) acceleration factor: 2.000
[    51.944] (**) PixArt Microsoft USB Optical Mouse: (accel) acceleration threshold: 4
[    52.004] (II) event5  - PixArt Microsoft USB Optical Mouse: is tagged by udev as: Mouse
[    52.004] (II) event5  - PixArt Microsoft USB Optical Mouse: device is a pointer
[    52.005] (II) config/udev: Adding input device PixArt Microsoft USB Optical Mouse (/dev/input/mouse1)
[    52.006] (II) No input driver specified, ignoring this device.
[    52.006] (II) This device may have been added with another device file.
[    52.007] (II) config/udev: Adding input device HP Virtual Keyboard (/dev/input/event1)
[    52.007] (**) HP Virtual Keyboard: Applying InputClass "libinput keyboard catchall"
[    52.007] (II) Using input driver 'libinput' for 'HP Virtual Keyboard'
[    52.007] (**) HP Virtual Keyboard: always reports core events
[    52.007] (**) Option "Device" "/dev/input/event1"
[    52.007] (**) Option "_source" "server/udev"
[    52.008] (II) event1  - HP Virtual Keyboard: is tagged by udev as: Keyboard
[    52.008] (II) event1  - HP Virtual Keyboard: device is a keyboard
[    52.009] (II) event1  - HP Virtual Keyboard: device removed
[    52.036] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.0/0003:03F0:1027.0001/input/input4/event1"
[    52.036] (II) XINPUT: Adding extended input device "HP Virtual Keyboard" (type: KEYBOARD, id 10)
[    52.036] (**) Option "xkb_model" "pc105"
[    52.036] (**) Option "xkb_layout" "gb"
[    52.037] (II) event1  - HP Virtual Keyboard: is tagged by udev as: Keyboard
[    52.037] (II) event1  - HP Virtual Keyboard: device is a keyboard
[    52.038] (II) config/udev: Adding input device HP Virtual Keyboard (/dev/input/event2)
[    52.038] (**) HP Virtual Keyboard: Applying InputClass "libinput pointer catchall"
[    52.038] (II) Using input driver 'libinput' for 'HP Virtual Keyboard'
[    52.039] (**) HP Virtual Keyboard: always reports core events
[    52.039] (**) Option "Device" "/dev/input/event2"
[    52.039] (**) Option "_source" "server/udev"
[    52.096] (II) event2  - HP Virtual Keyboard: is tagged by udev as: Mouse
[    52.096] (II) event2  - HP Virtual Keyboard: device is a pointer
[    52.096] (II) event2  - HP Virtual Keyboard: device removed
[    52.136] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.1/0003:03F0:1027.0002/input/input5/event2"
[    52.136] (II) XINPUT: Adding extended input device "HP Virtual Keyboard" (type: MOUSE, id 11)
[    52.136] (**) Option "AccelerationScheme" "none"
[    52.136] (**) HP Virtual Keyboard: (accel) selected scheme none/0
[    52.136] (**) HP Virtual Keyboard: (accel) acceleration factor: 2.000
[    52.136] (**) HP Virtual Keyboard: (accel) acceleration threshold: 4
[    52.196] (II) event2  - HP Virtual Keyboard: is tagged by udev as: Mouse
[    52.196] (II) event2  - HP Virtual Keyboard: device is a pointer
[    52.198] (II) config/udev: Adding input device HP Virtual Keyboard (/dev/input/mouse0)
[    52.198] (II) No input driver specified, ignoring this device.
[    52.198] (II) This device may have been added with another device file.
[    52.210] (**) Microsoft Wired Keyboard 600: Applying InputClass "libinput keyboard catchall"
[    52.210] (II) Using input driver 'libinput' for 'Microsoft Wired Keyboard 600'
[    52.210] (**) Microsoft Wired Keyboard 600: always reports core events
[    52.210] (**) Option "Device" "/dev/input/event4"
[    52.210] (**) Option "_source" "_driver/libinput"
[    52.210] (II) libinput: Microsoft Wired Keyboard 600: is a virtual subdevice
[    52.210] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/0003:045E:07F8.0004/input/input7/event4"
[    52.210] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 12)
[    52.210] (**) Option "xkb_model" "pc105"
[    52.210] (**) Option "xkb_layout" "gb"
[    95.072] (II) RADEON(0): Allocate new frame buffer 1920x1080 stride 1920
[    95.092] (II) RADEON(0): VRAM usage limit set to 50065K
```

---


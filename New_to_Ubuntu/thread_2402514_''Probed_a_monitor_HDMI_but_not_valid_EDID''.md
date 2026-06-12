---
title: "''Probed a monitor HDMI but not valid EDID''"
date: 2018-10-01
forum: New to Ubuntu
---

### Post by seby21932 on 2018-10-01
Hi everyone, im barely new to linux.. I use a old Monitor from LG model W2442PE whit FullHD capability
and HDMI output,, the video card from computer is ''Sapphire HD 6750 512MB'' a.k.a Radeon HD6750, i have always
problems to put togheter the video card and monitor.. the monitor have corrupt EDID but good functionability, even in windows
its need to put manually the INF from monitor (downloadable from lg website)..but in Ubuntu i dont know how to do / or from which point
to start , there are plenty solution from google but many old and not coresponding to my situation...

The reason why i want to fix EDID on my ubuntu is :

- No HDMI audio through cable ( on volume control says 'unplugged' ) - nothing to do
- I can't get the maxim resolution of 1080p (only 1024x768)
- The quality of image on my monitor is somewhat look like a classic LCD monitor 

I have to mention that i tryed to install the propietary drivers for my HD6750 from ATI AMD website
but always get 'black screen' after reboot maybe all this from my corrupt EDID..

The version i use is XUBUNTU 18.04 x64 On a desktop PC (6 GB DDR2, 3GHZ Dual-Core ,t3400)

---

### Post by Yellow Pasque on 2018-10-01
Try creating an /etc/X11/xorg.conf with following contents:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync     30.0 - 83.0
        VertRefresh   56.0 - 75.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Reboot and see if you have more resolutions to choose from. If not, please copy/paste your /var/log/Xorg.0.log file.
Note: I'm assuming you don't already have an /etc/X11/xorg.conf file, which is the default.

---

### Post by seby21932 on 2018-10-01
HI

Im still unable to get resolution above 1024x768... i was created that file, whit text command you gived me
and granded permission 755 to file but nothing .. 

This is the log, after reboot & relaunch desktop

> [    29.882] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[    29.882] X Protocol Version 11, Revision 0
[    29.882] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[    29.882] Current Operating System: Linux seby-Precision-WorkStation-T3400 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64
[    29.882] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-34-generic root=UUID=e2abe3eb-9e92-4c07-bbf9-a79e0ba48f9a ro quiet splash vt.handoff=1
[    29.882] Build Date: 13 April 2018  08:07:36PM
[    29.882] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    29.882] Current version of pixman: 0.34.0
[    29.882]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    29.882] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.882] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct  2 00:00:41 2018
[    29.882] (==) Using config file: "/etc/X11/xorg.conf"
[    29.882] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.915] (==) No Layout section.  Using the first Screen section.
[    29.915] (**) |-->Screen "Default Screen" (0)
[    29.915] (**) |   |-->Monitor "Configured Monitor"
[    29.916] (**) |   |-->Device "Configured Video Device"
[    29.916] (==) Automatically adding devices
[    29.916] (==) Automatically enabling devices
[    29.916] (==) Automatically adding GPU devices
[    29.916] (==) Automatically binding GPU devices
[    29.916] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    29.916] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.916]     Entry deleted from font path.
[    29.916] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.916]     Entry deleted from font path.
[    29.916] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.916]     Entry deleted from font path.
[    29.916] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.916]     Entry deleted from font path.
[    29.916] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.916]     Entry deleted from font path.
[    29.916] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.916] (==) ModulePath set to "/usr/lib/xorg/modules"
[    29.916] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.916] (II) Loader magic: 0x55ff55cfe020
[    29.916] (II) Module ABI versions:
[    29.916]     X.Org ANSI C Emulation: 0.4
[    29.916]     X.Org Video Driver: 23.0
[    29.916]     X.Org XInput driver : 24.1
[    29.916]     X.Org Server Extension : 10.0
[    29.917] (++) using VT number 7

[    29.917] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    29.917] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.921] (--) PCI:*(0:1:0:0) 1002:68bf:174b:e144 rev 0, Mem @ 0xc0000000/268435456, 0xfe9e0000/131072, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
[    29.921] (II) LoadModule: "glx"
[    29.921] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.204] (II) Module glx: vendor="X.Org Foundation"
[    30.204]     compiled for 1.19.6, module version = 1.0.0
[    30.204]     ABI class: X.Org Server Extension, version 10.0
[    30.204] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[    30.204]     loading driver: radeon
[    30.204] (==) Matched radeon as autoconfigured driver 0
[    30.204] (==) Matched ati as autoconfigured driver 1
[    30.204] (==) Matched ati as autoconfigured driver 2
[    30.204] (==) Matched modesetting as autoconfigured driver 3
[    30.204] (==) Matched fbdev as autoconfigured driver 4
[    30.204] (==) Matched vesa as autoconfigured driver 5
[    30.204] (==) Assigned the driver to the xf86ConfigLayout
[    30.204] (II) LoadModule: "radeon"
[    30.205] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.260] (II) Module radeon: vendor="X.Org Foundation"
[    30.260]     compiled for 1.19.6, module version = 18.0.1
[    30.260]     Module class: X.Org Video Driver
[    30.260]     ABI class: X.Org Video Driver, version 23.0
[    30.260] (II) LoadModule: "ati"
[    30.260] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.261] (II) Module ati: vendor="X.Org Foundation"
[    30.261]     compiled for 1.19.6, module version = 18.0.1
[    30.261]     Module class: X.Org Video Driver
[    30.261]     ABI class: X.Org Video Driver, version 23.0
[    30.324] (II) LoadModule: "modesetting"
[    30.325] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.325] (II) Module modesetting: vendor="X.Org Foundation"
[    30.325]     compiled for 1.19.6, module version = 1.19.6
[    30.325]     Module class: X.Org Video Driver
[    30.325]     ABI class: X.Org Video Driver, version 23.0
[    30.325] (II) LoadModule: "fbdev"
[    30.325] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.325] (II) Module fbdev: vendor="X.Org Foundation"
[    30.325]     compiled for 1.19.3, module version = 0.4.4
[    30.325]     Module class: X.Org Video Driver
[    30.325]     ABI class: X.Org Video Driver, version 23.0
[    30.325] (II) LoadModule: "vesa"
[    30.325] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.325] (II) Module vesa: vendor="X.Org Foundation"
[    30.325]     compiled for 1.19.3, module version = 2.3.4
[    30.325]     Module class: X.Org Video Driver
[    30.325]     ABI class: X.Org Video Driver, version 23.0
[    30.325] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
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
[    30.328] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.328] (II) FBDEV: driver for framebuffer: fbdev
[    30.329] (II) VESA: driver for VESA chipsets: vesa
[    30.343] (II) [KMS] Kernel modesetting enabled.
[    30.344] (WW) Falling back to old probe method for modesetting
[    30.344] (WW) Falling back to old probe method for fbdev
[    30.344] (II) Loading sub module "fbdevhw"
[    30.344] (II) LoadModule: "fbdevhw"
[    30.344] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.344] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.344]     compiled for 1.19.6, module version = 0.0.2
[    30.344]     ABI class: X.Org Video Driver, version 23.0
[    30.344] (WW) Falling back to old probe method for vesa
[    30.344] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    30.344] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    30.344] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.344] (==) RADEON(0): Default visual is TrueColor
[    30.344] (==) RADEON(0): RGB weight 888
[    30.344] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    30.344] (--) RADEON(0): Chipset: "ATI Radeon HD 6700 Series" (ChipID = 0x68bf)
[    30.345] (II) Loading sub module "fb"
[    30.345] (II) LoadModule: "fb"
[    30.345] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.345] (II) Module fb: vendor="X.Org Foundation"
[    30.345]     compiled for 1.19.6, module version = 1.0.0
[    30.345]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.345] (II) Loading sub module "dri2"
[    30.345] (II) LoadModule: "dri2"
[    30.345] (II) Module "dri2" already built-in
[    30.345] (II) Loading sub module "glamoregl"
[    30.345] (II) LoadModule: "glamoregl"
[    30.345] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    30.485] (II) Module glamoregl: vendor="X.Org Foundation"
[    30.485]     compiled for 1.19.6, module version = 1.0.0
[    30.485]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.486] (II) glamor: OpenGL accelerated X.org driver based.
[    32.355] (II) glamor: EGL version 1.5 (DRI2):
[    32.396] (II) RADEON(0): glamor detected, initialising EGL layer.
[    32.396] (II) RADEON(0): KMS Color Tiling: enabled
[    32.396] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    32.396] (==) RADEON(0): TearFree property default: auto
[    32.396] (II) RADEON(0): KMS Pageflipping: enabled
[    32.428] (II) RADEON(0): Output DisplayPort-0 using monitor section Configured Monitor
[    32.670] (II) RADEON(0): Output HDMI-0 has no monitor section
[    32.684] (II) RADEON(0): Output DVI-0 has no monitor section
[    32.718] (II) RADEON(0): EDID for output DisplayPort-0
[    32.957] (II) RADEON(0): EDID for output HDMI-0
[    32.957] (II) RADEON(0): Printing probed modes for output HDMI-0
[    32.957] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    32.957] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    32.957] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    32.957] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    32.957] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    32.972] (II) RADEON(0): EDID for output DVI-0
[    32.972] (II) RADEON(0): Output DisplayPort-0 disconnected
[    32.972] (II) RADEON(0): Output HDMI-0 connected
[    32.972] (II) RADEON(0): Output DVI-0 disconnected
[    32.972] (II) RADEON(0): Using exact sizes for initial modes
[    32.972] (II) RADEON(0): Output HDMI-0 using initial mode 1024x768 +0+0
[    32.972] (II) RADEON(0): mem size init: gart size :3fdde000 vram size: s:20000000 visible:f9b3000
[    32.972] (==) RADEON(0): DPI set to (96, 96)
[    32.972] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    32.972] (II) Loading sub module "ramdac"
[    32.972] (II) LoadModule: "ramdac"
[    32.972] (II) Module "ramdac" already built-in
[    32.972] (II) UnloadModule: "modesetting"
[    32.972] (II) Unloading modesetting
[    32.972] (II) UnloadModule: "fbdev"
[    32.972] (II) Unloading fbdev
[    32.972] (II) UnloadSubModule: "fbdevhw"
[    32.972] (II) Unloading fbdevhw
[    32.972] (II) UnloadModule: "vesa"
[    32.972] (II) Unloading vesa
[    32.972] (--) Depth 24 pixmap format is 32 bpp
[    33.010] (II) RADEON(0): [DRI2] Setup complete
[    33.023] (II) RADEON(0): [DRI2]   DRI driver: r600
[    33.023] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    33.023] (II) RADEON(0): Front buffer size: 3072K
[    33.023] (II) RADEON(0): VRAM usage limit set to 227271K
[    33.023] (II) RADEON(0): SYNC extension fences enabled
[    33.023] (II) RADEON(0): Present extension enabled
[    33.023] (==) RADEON(0): DRI3 enabled
[    33.023] (==) RADEON(0): Backing store enabled
[    33.023] (II) RADEON(0): Direct rendering enabled
[    33.027] (II) RADEON(0): Use GLAMOR acceleration.
[    33.027] (II) RADEON(0): Acceleration enabled
[    33.027] (==) RADEON(0): DPMS enabled
[    33.027] (==) RADEON(0): Silken mouse enabled
[    33.027] (II) RADEON(0): Set up textured video (glamor)
[    33.027] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[    33.027] (II) RADEON(0): [XvMC] Extension initialized.
[    33.027] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    33.028] (--) RandR disabled
[    33.092] (II) SELinux: Disabled on system
[    33.095] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    33.095] (II) AIGLX: enabled GLX_ARB_create_context
[    33.095] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    33.095] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    33.095] (II) AIGLX: enabled GLX_INTEL_swap_event
[    33.095] (II) AIGLX: enabled GLX_SGI_swap_control
[    33.095] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    33.095] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    33.095] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    33.095] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    33.095] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    33.096] (II) AIGLX: Loaded and initialized r600
[    33.096] (II) GLX: Initialized DRI2 GL provider for screen 0
[    33.098] (II) RADEON(0): Setting screen physical size to 270 x 203
[    33.320] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    33.320] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    33.320] (II) LoadModule: "libinput"
[    33.320] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    33.784] (II) Module libinput: vendor="X.Org Foundation"
[    33.784]     compiled for 1.19.6, module version = 0.27.1
[    33.784]     Module class: X.Org XInput Driver
[    33.784]     ABI class: X.Org XInput driver, version 24.1
[    33.784] (II) Using input driver 'libinput' for 'Power Button'
[    33.784] (**) Power Button: always reports core events
[    33.784] (**) Option "Device" "/dev/input/event1"
[    33.816] (**) Option "_source" "server/udev"
[    33.817] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    33.817] (II) event1  - Power Button: device is a keyboard
[    33.817] (II) event1  - Power Button: device removed
[    33.832] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    33.832] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    33.832] (**) Option "xkb_model" "pc105"
[    33.832] (**) Option "xkb_layout" "us"
[    33.832] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    33.832] (II) event1  - Power Button: device is a keyboard
[    33.833] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    33.833] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    33.833] (II) Using input driver 'libinput' for 'Power Button'
[    33.833] (**) Power Button: always reports core events
[    33.833] (**) Option "Device" "/dev/input/event0"
[    33.833] (**) Option "_source" "server/udev"
[    33.833] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    33.834] (II) event0  - Power Button: device is a keyboard
[    33.834] (II) event0  - Power Button: device removed
[    33.848] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    33.848] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    33.848] (**) Option "xkb_model" "pc105"
[    33.848] (**) Option "xkb_layout" "us"
[    33.848] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    33.848] (II) event0  - Power Button: device is a keyboard
[    33.849] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    33.849] (II) No input driver specified, ignoring this device.
[    33.849] (II) This device may have been added with another device file.
[    33.850] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/event2)
[    33.850] (**) HID 1241:1166: Applying InputClass "libinput pointer catchall"
[    33.850] (II) Using input driver 'libinput' for 'HID 1241:1166'
[    33.850] (**) HID 1241:1166: always reports core events
[    33.850] (**) Option "Device" "/dev/input/event2"
[    33.850] (**) Option "_source" "server/udev"
[    33.908] (II) event2  - HID 1241:1166: is tagged by udev as: Mouse
[    33.908] (II) event2  - HID 1241:1166: device is a pointer
[    33.908] (II) event2  - HID 1241:1166: device removed
[    33.948] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/0003:1241:1166.0001/input/input5/event2"
[    33.948] (II) XINPUT: Adding extended input device "HID 1241:1166" (type: MOUSE, id 8)
[    33.948] (**) Option "AccelerationScheme" "none"
[    33.948] (**) HID 1241:1166: (accel) selected scheme none/0
[    33.948] (**) HID 1241:1166: (accel) acceleration factor: 2.000
[    33.948] (**) HID 1241:1166: (accel) acceleration threshold: 4
[    34.008] (II) event2  - HID 1241:1166: is tagged by udev as: Mouse
[    34.008] (II) event2  - HID 1241:1166: device is a pointer
[    34.009] (II) config/udev: Adding input device HID 1241:1166 (/dev/input/mouse0)
[    34.009] (II) No input driver specified, ignoring this device.
[    34.009] (II) This device may have been added with another device file.
[    34.010] (II) config/udev: Adding input device SEM USB Keyboard (/dev/input/event3)
[    34.010] (**) SEM USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    34.010] (II) Using input driver 'libinput' for 'SEM USB Keyboard'
[    34.010] (**) SEM USB Keyboard: always reports core events
[    34.010] (**) Option "Device" "/dev/input/event3"
[    34.010] (**) Option "_source" "server/udev"
[    34.011] (II) event3  - SEM USB Keyboard: is tagged by udev as: Keyboard
[    34.011] (II) event3  - SEM USB Keyboard: device is a keyboard
[    34.011] (II) event3  - SEM USB Keyboard: device removed
[    34.028] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/0003:1A2C:2124.0002/input/input6/event3"
[    34.028] (II) XINPUT: Adding extended input device "SEM USB Keyboard" (type: KEYBOARD, id 9)
[    34.028] (**) Option "xkb_model" "pc105"
[    34.028] (**) Option "xkb_layout" "us"
[    34.029] (II) event3  - SEM USB Keyboard: is tagged by udev as: Keyboard
[    34.029] (II) event3  - SEM USB Keyboard: device is a keyboard
[    34.030] (II) config/udev: Adding input device SEM USB Keyboard (/dev/input/event4)
[    34.030] (**) SEM USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    34.030] (II) Using input driver 'libinput' for 'SEM USB Keyboard'
[    34.030] (**) SEM USB Keyboard: always reports core events
[    34.030] (**) Option "Device" "/dev/input/event4"
[    34.030] (**) Option "_source" "server/udev"
[    34.030] (II) event4  - SEM USB Keyboard: is tagged by udev as: Keyboard
[    34.030] (II) event4  - SEM USB Keyboard: device is a keyboard
[    34.030] (II) event4  - SEM USB Keyboard: device removed
[    34.040] (II) libinput: SEM USB Keyboard: needs a virtual subdevice
[    34.040] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/0003:1A2C:2124.0003/input/input7/event4"
[    34.040] (II) XINPUT: Adding extended input device "SEM USB Keyboard" (type: MOUSE, id 10)
[    34.040] (**) Option "AccelerationScheme" "none"
[    34.040] (**) SEM USB Keyboard: (accel) selected scheme none/0
[    34.040] (**) SEM USB Keyboard: (accel) acceleration factor: 2.000
[    34.040] (**) SEM USB Keyboard: (accel) acceleration threshold: 4
[    34.041] (II) event4  - SEM USB Keyboard: is tagged by udev as: Keyboard
[    34.041] (II) event4  - SEM USB Keyboard: device is a keyboard
[    34.041] (II) config/udev: Adding input device UVC Camera (046d:0825) (/dev/input/event11)
[    34.042] (**) UVC Camera (046d:0825): Applying InputClass "libinput keyboard catchall"
[    34.042] (II) Using input driver 'libinput' for 'UVC Camera (046d:0825)'
[    34.042] (**) UVC Camera (046d:0825): always reports core events
[    34.042] (**) Option "Device" "/dev/input/event11"
[    34.042] (**) Option "_source" "server/udev"
[    34.042] (II) event11 - UVC Camera (046d:0825): is tagged by udev as: Keyboard
[    34.042] (II) event11 - UVC Camera (046d:0825): device is a keyboard
[    34.042] (II) event11 - UVC Camera (046d:0825): device removed
[    34.072] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input14/event11"
[    34.072] (II) XINPUT: Adding extended input device "UVC Camera (046d:0825)" (type: KEYBOARD, id 11)
[    34.072] (**) Option "xkb_model" "pc105"
[    34.072] (**) Option "xkb_layout" "us"
[    34.072] (II) event11 - UVC Camera (046d:0825): is tagged by udev as: Keyboard
[    34.073] (II) event11 - UVC Camera (046d:0825): device is a keyboard
[    34.073] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event7)
[    34.073] (II) No input driver specified, ignoring this device.
[    34.073] (II) This device may have been added with another device file.
[    34.073] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event8)
[    34.073] (II) No input driver specified, ignoring this device.
[    34.073] (II) This device may have been added with another device file.
[    34.074] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event9)
[    34.074] (II) No input driver specified, ignoring this device.
[    34.074] (II) This device may have been added with another device file.
[    34.074] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    34.074] (II) No input driver specified, ignoring this device.
[    34.074] (II) This device may have been added with another device file.
[    34.075] (II) config/udev: Adding input device Mantis VP-1041 IR receiver (/dev/input/event10)
[    34.075] (**) Mantis VP-1041 IR receiver: Applying InputClass "libinput keyboard catchall"
[    34.075] (II) Using input driver 'libinput' for 'Mantis VP-1041 IR receiver'
[    34.075] (**) Mantis VP-1041 IR receiver: always reports core events
[    34.075] (**) Option "Device" "/dev/input/event10"
[    34.075] (**) Option "_source" "server/udev"
[    34.075] (II) event10 - Mantis VP-1041 IR receiver: is tagged by udev as: Keyboard
[    34.075] (II) event10 - Mantis VP-1041 IR receiver: device is a keyboard
[    34.075] (II) event10 - Mantis VP-1041 IR receiver: device removed
[    34.240] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1e.0/0000:05:04.0/rc/rc0/input13/event10"
[    34.240] (II) XINPUT: Adding extended input device "Mantis VP-1041 IR receiver" (type: KEYBOARD, id 12)
[    34.240] (**) Option "xkb_model" "pc105"
[    34.240] (**) Option "xkb_layout" "us"
[    34.240] (II) event10 - Mantis VP-1041 IR receiver: is tagged by udev as: Keyboard
[    34.241] (II) event10 - Mantis VP-1041 IR receiver: device is a keyboard
[    34.249] (**) SEM USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    34.249] (II) Using input driver 'libinput' for 'SEM USB Keyboard'
[    34.249] (**) SEM USB Keyboard: always reports core events
[    34.249] (**) Option "Device" "/dev/input/event4"
[    34.249] (**) Option "_source" "_driver/libinput"
[    34.249] (II) libinput: SEM USB Keyboard: is a virtual subdevice
[    34.249] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/0003:1A2C:2124.0003/input/input7/event4"
[    34.249] (II) XINPUT: Adding extended input device "SEM USB Keyboard" (type: KEYBOARD, id 13)
[    34.249] (**) Option "xkb_model" "pc105"
[    34.249] (**) Option "xkb_layout" "us"


---

### Post by Yellow Pasque on 2018-10-01
Have you tried adding/setting your own modeline: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---


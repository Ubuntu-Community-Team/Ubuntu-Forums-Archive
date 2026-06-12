---
title: "Unity takes too long to load after release upgrade to Oneiric"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by vajorie on 2012-03-27
I upgraded from 11.04 to 11.10. I had to halt the upgrade mid-process (disk full) but was able to finish it afterwards using apt-get -f and so on. I had to install "lightdm-gtk-greeter" myself for X to come up, but no problems otherwise. 

I have an ATI graphics card, not using fglrx:
```

02:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500/5100 Series]

```

When I boot (or start lightdm otherwise), unity takes a very long time to launch. Usually, my desktop background comes up, and I end up having to wait for everything to come back on. Can someone help? 

My Xorg.0.log:
```

.Org X Server 1.10.4
Release Date: 2011-08-19
[  8934.227] X Protocol Version 11, Revision 0
[  8934.227] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  8934.227] Current Operating System: Linux system76 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64
[  8934.228] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-17-generic root=UUID=75f3819b-9e31-4269-8e13-9f9627cb91e5 ro quiet splash vt.handoff=7
[  8934.228] Build Date: 19 October 2011  05:21:26AM
[  8934.228] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  8934.228] Current version of pixman: 0.22.2
[  8934.228] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  8934.228] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  8934.228] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 27 21:30:52 2012
[  8934.228] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  8934.228] (==) No Layout section.  Using the first Screen section.
[  8934.228] (==) No screen section available. Using defaults.
[  8934.228] (**) |-->Screen "Default Screen Section" (0)
[  8934.228] (**) |   |-->Monitor "<default monitor>"
[  8934.229] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  8934.229] (==) Automatically adding devices
[  8934.229] (==) Automatically enabling devices
[  8934.229] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  8934.229] 	Entry deleted from font path.
[  8934.229] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  8934.229] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  8934.229] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  8934.229] (II) Loader magic: 0x7e0220
[  8934.229] (II) Module ABI versions:
[  8934.229] 	X.Org ANSI C Emulation: 0.4
[  8934.229] 	X.Org Video Driver: 10.0
[  8934.229] 	X.Org XInput driver : 12.3
[  8934.229] 	X.Org Server Extension : 5.0
[  8934.230] (--) PCI:*(0:2:0:0) 1002:9553:1558:0770 rev 0, Mem @ 0xd0000000/268435456, 0xcfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[  8934.230] (II) Open ACPI successful (/var/run/acpid.socket)
[  8934.230] (II) LoadModule: "extmod"
[  8934.231] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  8934.231] (II) Module extmod: vendor="X.Org Foundation"
[  8934.231] 	compiled for 1.10.4, module version = 1.0.0
[  8934.231] 	Module class: X.Org Server Extension
[  8934.231] 	ABI class: X.Org Server Extension, version 5.0
[  8934.231] (II) Loading extension MIT-SCREEN-SAVER
[  8934.231] (II) Loading extension XFree86-VidModeExtension
[  8934.231] (II) Loading extension XFree86-DGA
[  8934.231] (II) Loading extension DPMS
[  8934.231] (II) Loading extension XVideo
[  8934.231] (II) Loading extension XVideo-MotionCompensation
[  8934.231] (II) Loading extension X-Resource
[  8934.231] (II) LoadModule: "dbe"
[  8934.231] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  8934.231] (II) Module dbe: vendor="X.Org Foundation"
[  8934.231] 	compiled for 1.10.4, module version = 1.0.0
[  8934.232] 	Module class: X.Org Server Extension
[  8934.232] 	ABI class: X.Org Server Extension, version 5.0
[  8934.232] (II) Loading extension DOUBLE-BUFFER
[  8934.232] (II) LoadModule: "glx"
[  8934.232] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  8934.232] (II) Module glx: vendor="X.Org Foundation"
[  8934.232] 	compiled for 1.10.4, module version = 1.0.0
[  8934.232] 	ABI class: X.Org Server Extension, version 5.0
[  8934.232] (==) AIGLX enabled
[  8934.232] (II) Loading extension GLX
[  8934.232] (II) LoadModule: "record"
[  8934.232] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  8934.232] (II) Module record: vendor="X.Org Foundation"
[  8934.233] 	compiled for 1.10.4, module version = 1.13.0
[  8934.233] 	Module class: X.Org Server Extension
[  8934.233] 	ABI class: X.Org Server Extension, version 5.0
[  8934.233] (II) Loading extension RECORD
[  8934.233] (II) LoadModule: "dri"
[  8934.233] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  8934.233] (II) Module dri: vendor="X.Org Foundation"
[  8934.233] 	compiled for 1.10.4, module version = 1.0.0
[  8934.233] 	ABI class: X.Org Server Extension, version 5.0
[  8934.233] (II) Loading extension XFree86-DRI
[  8934.233] (II) LoadModule: "dri2"
[  8934.233] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  8934.233] (II) Module dri2: vendor="X.Org Foundation"
[  8934.234] 	compiled for 1.10.4, module version = 1.2.0
[  8934.234] 	ABI class: X.Org Server Extension, version 5.0
[  8934.234] (II) Loading extension DRI2
[  8934.234] (==) Matched fglrx as autoconfigured driver 0
[  8934.234] (==) Matched ati as autoconfigured driver 1
[  8934.234] (==) Matched vesa as autoconfigured driver 2
[  8934.234] (==) Matched fbdev as autoconfigured driver 3
[  8934.234] (==) Assigned the driver to the xf86ConfigLayout
[  8934.234] (II) LoadModule: "fglrx"
[  8934.234] (WW) Warning, couldn't open module fglrx
[  8934.234] (II) UnloadModule: "fglrx"
[  8934.234] (II) Unloading fglrx
[  8934.234] (EE) Failed to load module "fglrx" (module does not exist, 0)
[  8934.234] (II) LoadModule: "ati"
[  8934.235] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[  8934.235] (II) Module ati: vendor="X.Org Foundation"
[  8934.235] 	compiled for 1.10.2.902, module version = 6.14.99
[  8934.235] 	Module class: X.Org Video Driver
[  8934.235] 	ABI class: X.Org Video Driver, version 10.0
[  8934.235] (II) LoadModule: "radeon"
[  8934.235] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  8934.236] (II) Module radeon: vendor="X.Org Foundation"
[  8934.236] 	compiled for 1.10.2.902, module version = 6.14.99
[  8934.236] 	Module class: X.Org Video Driver
[  8934.236] 	ABI class: X.Org Video Driver, version 10.0
[  8934.236] (II) LoadModule: "vesa"
[  8934.236] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  8934.236] (II) Module vesa: vendor="X.Org Foundation"
[  8934.236] 	compiled for 1.10.2, module version = 2.3.0
[  8934.236] 	Module class: X.Org Video Driver
[  8934.236] 	ABI class: X.Org Video Driver, version 10.0
[  8934.236] (II) LoadModule: "fbdev"
[  8934.237] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  8934.237] (II) Module fbdev: vendor="X.Org Foundation"
[  8934.237] 	compiled for 1.10.0, module version = 0.4.2
[  8934.237] 	ABI class: X.Org Video Driver, version 10.0
[  8934.237] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS
[  8934.240] (II) VESA: driver for VESA chipsets: vesa
[  8934.240] (II) FBDEV: driver for framebuffer: fbdev
[  8934.240] (++) using VT number 7

[  8934.241] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[  8934.241] (II) [KMS] Kernel modesetting enabled.
[  8934.241] (WW) Falling back to old probe method for vesa
[  8934.241] (WW) Falling back to old probe method for fbdev
[  8934.241] (II) Loading sub module "fbdevhw"
[  8934.241] (II) LoadModule: "fbdevhw"
[  8934.241] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  8934.241] (II) Module fbdevhw: vendor="X.Org Foundation"
[  8934.241] 	compiled for 1.10.4, module version = 0.0.2
[  8934.241] 	ABI class: X.Org Video Driver, version 10.0
[  8934.241] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  8934.241] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[  8934.241] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  8934.241] (==) RADEON(0): Default visual is TrueColor
[  8934.241] (==) RADEON(0): RGB weight 888
[  8934.241] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[  8934.241] (--) RADEON(0): Chipset: "ATI Mobility Radeon 4500 Series" (ChipID = 0x9553)
[  8934.241] (II) RADEON(0): PCIE card detected
[  8934.241] drmOpenDevice: node name is /dev/dri/card0
[  8934.241] drmOpenDevice: open result is 9, (OK)
[  8934.241] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[  8934.241] drmOpenDevice: node name is /dev/dri/card0
[  8934.241] drmOpenDevice: open result is 9, (OK)
[  8934.241] drmOpenByBusid: drmOpenMinor returns 9
[  8934.241] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[  8934.241] (II) Loading sub module "exa"
[  8934.241] (II) LoadModule: "exa"
[  8934.241] (II) Loading /usr/lib/xorg/modules/libexa.so
[  8934.241] (II) Module exa: vendor="X.Org Foundation"
[  8934.241] 	compiled for 1.10.4, module version = 2.5.0
[  8934.241] 	ABI class: X.Org Video Driver, version 10.0
[  8934.241] (II) RADEON(0): KMS Color Tiling: enabled
[  8934.241] (II) RADEON(0): KMS Pageflipping: enabled
[  8934.241] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[  8934.264] (II) RADEON(0): Output VGA-0 has no monitor section
[  8934.264] (II) RADEON(0): Output LVDS has no monitor section
[  8934.268] (II) RADEON(0): Output HDMI-0 has no monitor section
[  8934.296] (II) RADEON(0): EDID for output VGA-0
[  8934.296] (II) RADEON(0): EDID for output LVDS
[  8934.296] (II) RADEON(0): Manufacturer: LGD  Model: 20c  Serial#: 0
[  8934.296] (II) RADEON(0): Year: 2009  Week: 0
[  8934.296] (II) RADEON(0): EDID Version: 1.3
[  8934.296] (II) RADEON(0): Digital Display Input
[  8934.296] (II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[  8934.296] (II) RADEON(0): Gamma: 2.20
[  8934.296] (II) RADEON(0): No DPMS capabilities specified
[  8934.296] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  8934.296] (II) RADEON(0): First detailed timing is preferred mode
[  8934.296] (II) RADEON(0): redX: 0.617 redY: 0.349   greenX: 0.314 greenY: 0.597
[  8934.296] (II) RADEON(0): blueX: 0.151 blueY: 0.057   whiteX: 0.313 whiteY: 0.329
[  8934.296] (II) RADEON(0): Manufacturer's mask: 0
[  8934.296] (II) RADEON(0): Supported detailed timing:
[  8934.296] (II) RADEON(0): clock: 97.8 MHz   Image Size:  345 x 194 mm
[  8934.296] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[  8934.296] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
[  8934.296] (II) RADEON(0): Supported detailed timing:
[  8934.296] (II) RADEON(0): clock: 97.8 MHz   Image Size:  345 x 194 mm
[  8934.296] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[  8934.296] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
[  8934.296] (II) RADEON(0):  MT6KG&#65533;156WD1
[  8934.296] (II) RADEON(0): Unknown vendor-specific block 0
[  8934.296] (II) RADEON(0): EDID (in hex):
[  8934.296] (II) RADEON(0): 	00ffffffffffff0030e40c0200000000
[  8934.296] (II) RADEON(0): 	00130103902313780a1be59e59509826
[  8934.296] (II) RADEON(0): 	0e505400000001010101010101010101
[  8934.296] (II) RADEON(0): 	0101010101012f2640a060841a303020
[  8934.296] (II) RADEON(0): 	350059c21000001b2f2640a060841a30
[  8934.296] (II) RADEON(0): 	3020350059c21000001b000000fe004d
[  8934.296] (II) RADEON(0): 	54364b47803135365744310a00000000
[  8934.296] (II) RADEON(0): 	00000000000000000002010a202000bc
[  8934.296] (II) RADEON(0): Printing probed modes for output LVDS
[  8934.296] (II) RADEON(0): Modeline "1600x900"x60.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)
[  8934.296] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  8934.296] (II) RADEON(0): Modeline "1280x854"x59.9   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync (53.1 kHz)
[  8934.296] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[  8934.297] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[  8934.297] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[  8934.297] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[  8934.297] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[  8934.297] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[  8934.297] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[  8934.297] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[  8934.301] (II) RADEON(0): EDID for output HDMI-0
[  8934.301] (II) RADEON(0): Output VGA-0 disconnected
[  8934.301] (II) RADEON(0): Output LVDS connected
[  8934.301] (II) RADEON(0): Output HDMI-0 disconnected
[  8934.301] (II) RADEON(0): Using exact sizes for initial modes
[  8934.301] (II) RADEON(0): Output LVDS using initial mode 1600x900
[  8934.301] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  8934.301] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:20000000 visible:fa3b000
[  8934.301] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[  8934.301] (==) RADEON(0): DPI set to (96, 96)
[  8934.301] (II) Loading sub module "fb"
[  8934.301] (II) LoadModule: "fb"
[  8934.301] (II) Loading /usr/lib/xorg/modules/libfb.so
[  8934.301] (II) Module fb: vendor="X.Org Foundation"
[  8934.301] 	compiled for 1.10.4, module version = 1.0.0
[  8934.301] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  8934.301] (II) Loading sub module "ramdac"
[  8934.301] (II) LoadModule: "ramdac"
[  8934.301] (II) Module "ramdac" already built-in
[  8934.301] (II) UnloadModule: "vesa"
[  8934.301] (II) Unloading vesa
[  8934.301] (II) UnloadModule: "fbdev"
[  8934.301] (II) Unloading fbdev
[  8934.301] (II) UnloadModule: "fbdevhw"
[  8934.301] (II) Unloading fbdevhw
[  8934.301] (--) Depth 24 pixmap format is 32 bpp
[  8934.301] (II) RADEON(0): [DRI2] Setup complete
[  8934.302] (II) RADEON(0): [DRI2]   DRI driver: r600
[  8934.302] (II) RADEON(0): Front buffer size: 5876K
[  8934.302] (II) RADEON(0): VRAM usage limit set to 225324K
[  8934.302] (==) RADEON(0): Backing store disabled
[  8934.302] (II) RADEON(0): Direct rendering enabled
[  8934.302] (II) RADEON(0): Setting EXA maxPitchBytes
[  8934.302] (II) EXA(0): Driver allocated offscreen pixmaps
[  8934.302] (II) EXA(0): Driver registered support for the following operations:
[  8934.302] (II)         Solid
[  8934.302] (II)         Copy
[  8934.302] (II)         Composite (RENDER acceleration)
[  8934.302] (II)         UploadToScreen
[  8934.302] (II)         DownloadFromScreen
[  8934.302] (II) RADEON(0): Acceleration enabled
[  8934.302] (==) RADEON(0): DPMS enabled
[  8934.302] (==) RADEON(0): Silken mouse enabled
[  8934.302] (II) RADEON(0): Set up textured video
[  8934.302] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[  8934.302] (II) RADEON(0): [XvMC] Extension initialized.
[  8934.302] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  8934.302] (--) RandR disabled
[  8934.302] (II) Initializing built-in extension Generic Event Extension
[  8934.302] (II) Initializing built-in extension SHAPE
[  8934.302] (II) Initializing built-in extension MIT-SHM
[  8934.302] (II) Initializing built-in extension XInputExtension
[  8934.302] (II) Initializing built-in extension XTEST
[  8934.302] (II) Initializing built-in extension BIG-REQUESTS
[  8934.302] (II) Initializing built-in extension SYNC
[  8934.302] (II) Initializing built-in extension XKEYBOARD
[  8934.303] (II) Initializing built-in extension XC-MISC
[  8934.303] (II) Initializing built-in extension SECURITY
[  8934.303] (II) Initializing built-in extension XINERAMA
[  8934.303] (II) Initializing built-in extension XFIXES
[  8934.303] (II) Initializing built-in extension RENDER
[  8934.303] (II) Initializing built-in extension RANDR
[  8934.303] (II) Initializing built-in extension COMPOSITE
[  8934.303] (II) Initializing built-in extension DAMAGE
[  8934.303] (II) Initializing built-in extension GESTURE
[  8934.312] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/r600_dri.so
[  8934.319] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  8934.319] (II) AIGLX: enabled GLX_INTEL_swap_event
[  8934.319] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  8934.319] (II) AIGLX: enabled GLX_SGI_make_current_read
[  8934.319] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  8934.320] (II) AIGLX: Loaded and initialized r600
[  8934.320] (II) GLX: Initialized DRI2 GL provider for screen 0
[  8934.320] (II) RADEON(0): Setting screen physical size to 423 x 238
[  8934.330] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  8934.336] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[  8934.336] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  8934.336] (II) LoadModule: "evdev"
[  8934.336] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.337] (II) Module evdev: vendor="X.Org Foundation"
[  8934.337] 	compiled for 1.10.2, module version = 2.6.0
[  8934.337] 	Module class: X.Org XInput Driver
[  8934.337] 	ABI class: X.Org XInput driver, version 12.3
[  8934.337] (II) Using input driver 'evdev' for 'Power Button'
[  8934.337] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.337] (**) Power Button: always reports core events
[  8934.337] (**) Power Button: Device: "/dev/input/event3"
[  8934.337] (--) Power Button: Found keys
[  8934.337] (II) Power Button: Configuring as keyboard
[  8934.337] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[  8934.337] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  8934.337] (**) Option "xkb_rules" "evdev"
[  8934.337] (**) Option "xkb_model" "pc105"
[  8934.337] (**) Option "xkb_layout" "tr"
[  8934.337] (**) Option "xkb_variant" "alt"
[  8934.338] (II) XKB: reuse xkmfile /var/lib/xkb/server-6A5361FC91CB054C1D90C9C236E5262A348BE03B.xkm
[  8934.354] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[  8934.354] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  8934.354] (II) Using input driver 'evdev' for 'Video Bus'
[  8934.354] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.354] (**) Video Bus: always reports core events
[  8934.354] (**) Video Bus: Device: "/dev/input/event6"
[  8934.354] (--) Video Bus: Found keys
[  8934.354] (II) Video Bus: Configuring as keyboard
[  8934.354] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6/event6"
[  8934.354] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  8934.354] (**) Option "xkb_rules" "evdev"
[  8934.354] (**) Option "xkb_model" "pc105"
[  8934.354] (**) Option "xkb_layout" "tr"
[  8934.354] (**) Option "xkb_variant" "alt"
[  8934.363] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  8934.363] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  8934.363] (II) Using input driver 'evdev' for 'Power Button'
[  8934.363] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.363] (**) Power Button: always reports core events
[  8934.363] (**) Power Button: Device: "/dev/input/event1"
[  8934.363] (--) Power Button: Found keys
[  8934.363] (II) Power Button: Configuring as keyboard
[  8934.363] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[  8934.364] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  8934.364] (**) Option "xkb_rules" "evdev"
[  8934.364] (**) Option "xkb_model" "pc105"
[  8934.364] (**) Option "xkb_layout" "tr"
[  8934.364] (**) Option "xkb_variant" "alt"
[  8934.364] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  8934.364] (II) No input driver/identifier specified (ignoring)
[  8934.365] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  8934.365] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  8934.365] (II) Using input driver 'evdev' for 'Sleep Button'
[  8934.365] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.365] (**) Sleep Button: always reports core events
[  8934.365] (**) Sleep Button: Device: "/dev/input/event2"
[  8934.365] (--) Sleep Button: Found keys
[  8934.365] (II) Sleep Button: Configuring as keyboard
[  8934.365] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[  8934.365] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  8934.365] (**) Option "xkb_rules" "evdev"
[  8934.365] (**) Option "xkb_model" "pc105"
[  8934.365] (**) Option "xkb_layout" "tr"
[  8934.365] (**) Option "xkb_variant" "alt"
[  8934.368] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event11)
[  8934.368] (II) No input driver/identifier specified (ignoring)
[  8934.369] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[  8934.370] (II) No input driver/identifier specified (ignoring)
[  8934.370] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[  8934.370] (II) No input driver/identifier specified (ignoring)
[  8934.373] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event5)
[  8934.373] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[  8934.373] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse'
[  8934.373] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.373] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[  8934.373] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event5"
[  8934.373] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[  8934.373] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[  8934.373] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[  8934.373] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[  8934.373] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[  8934.373] (II) Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support
[  8934.373] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[  8934.373] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  8934.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5/event5"
[  8934.373] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[  8934.374] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[  8934.374] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[  8934.374] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[  8934.374] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[  8934.374] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[  8934.374] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[  8934.374] (II) No input driver/identifier specified (ignoring)
[  8934.375] (II) config/udev: Adding input device SMP WebCam (/dev/input/event7)
[  8934.375] (**) SMP WebCam: Applying InputClass "evdev keyboard catchall"
[  8934.375] (II) Using input driver 'evdev' for 'SMP WebCam'
[  8934.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.375] (**) SMP WebCam: always reports core events
[  8934.375] (**) SMP WebCam: Device: "/dev/input/event7"
[  8934.376] (--) SMP WebCam: Found keys
[  8934.376] (II) SMP WebCam: Configuring as keyboard
[  8934.376] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7/event7"
[  8934.376] (II) XINPUT: Adding extended input device "SMP WebCam" (type: KEYBOARD)
[  8934.376] (**) Option "xkb_rules" "evdev"
[  8934.376] (**) Option "xkb_model" "pc105"
[  8934.376] (**) Option "xkb_layout" "tr"
[  8934.376] (**) Option "xkb_variant" "alt"
[  8934.380] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[  8934.380] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  8934.380] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  8934.380] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  8934.380] (**) AT Translated Set 2 keyboard: always reports core events
[  8934.380] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[  8934.380] (--) AT Translated Set 2 keyboard: Found keys
[  8934.380] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  8934.380] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[  8934.380] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  8934.380] (**) Option "xkb_rules" "evdev"
[  8934.380] (**) Option "xkb_model" "pc105"
[  8934.380] (**) Option "xkb_layout" "tr"
[  8934.380] (**) Option "xkb_variant" "alt"
[  8934.381] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[  8934.381] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  8934.381] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  8934.381] (II) LoadModule: "synaptics"
[  8934.381] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  8934.381] (II) Module synaptics: vendor="X.Org Foundation"
[  8934.381] 	compiled for 1.10.4, module version = 1.4.1
[  8934.381] 	Module class: X.Org XInput Driver
[  8934.381] 	ABI class: X.Org XInput driver, version 12.3
[  8934.381] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  8934.381] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  8934.381] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  8934.381] (**) Option "Device" "/dev/input/event10"
[  8934.381] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5378
[  8934.381] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4546
[  8934.381] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  8934.381] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  8934.381] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[  8934.384] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  8934.384] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  8934.388] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event10"
[  8934.388] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  8934.388] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  8934.388] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  8934.388] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  8934.388] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  8934.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  8934.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  8934.388] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  8934.388] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  8934.388] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  8934.388] (II) No input driver/identifier specified (ignoring)
[  8934.744] (II) RADEON(0): EDID vendor "LGD", prod id 524
[  8934.744] (II) RADEON(0): Printing DDC gathered Modelines:
[  8934.744] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)
[  8935.148] (II) RADEON(0): EDID vendor "LGD", prod id 524
[  8935.148] (II) RADEON(0): Printing DDC gathered Modelines:
[  8935.148] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)
[  8944.977] (II) AIGLX: Suspending AIGLX clients for VT switch
[  8945.711] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  8951.686] (II) Open ACPI successful (/var/run/acpid.socket)
[  8951.686] (II) AIGLX: Resuming AIGLX clients after VT switch
[  8951.716] (II) RADEON(0): EDID vendor "LGD", prod id 524
[  8951.716] (II) RADEON(0): Printing DDC gathered Modelines:
[  8951.716] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)
[  8951.722] [dix] couldn't enable device 13
[  8970.724] (II) RADEON(0): EDID vendor "LGD", prod id 524
[  8970.724] (II) RADEON(0): Printing DDC gathered Modelines:
[  8970.724] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)
[  8971.810] (II) XKB: reuse xkmfile /var/lib/xkb/server-FD28454494EF1FB891D0BC0906C979FF571CFAD9.xkm
[ 10139.200] (II) RADEON(0): EDID vendor "LGD", prod id 524
[ 10139.200] (II) RADEON(0): Printing DDC gathered Modelines:
[ 10139.200] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz)

```

My lightdm.log:
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.0.6, UID=0 PID=13880
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user mehmet
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: Activating VT 7
[+0.00s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.01s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 13885: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.19s] DEBUG: Got signal 10 from process 13885
[+0.19s] DEBUG: Got signal from X server :0
[+0.19s] DEBUG: Connecting to XServer :0
[+0.19s] DEBUG: Automatically logging in user mehmet
[+0.20s] DEBUG: pam_start("lightdm-autologin", "mehmet") -> (0x17edd00, 0)
[+0.20s] DEBUG: pam_authenticate(0x17edd00, 0) -> 0 (Success)
[+0.20s] DEBUG: pam_acct_mgmt(0x17edd00, 0) -> 0 (Success)
[+0.20s] DEBUG: User mehmet authorized
[+0.21s] DEBUG: Using session ubuntu
[+0.21s] DEBUG: Starting user session
[+0.22s] DEBUG: Dropping privileges to uid 1000
[+0.22s] DEBUG: Restoring privileges
[+0.23s] DEBUG: Dropping privileges to uid 1000
[+0.23s] DEBUG: Writing /home/mehmet/.dmrc
[+0.23s] DEBUG: Restoring privileges
[+0.24s] DEBUG: Starting session ubuntu as user mehmet
[+0.24s] DEBUG: Logging to /home/mehmet/.xsession-errors
[+0.24s] DEBUG: Launching session
[+0.24s] DEBUG: pam_set_item(0x17edd00, 3, ":0") -> 0 (Success)
[+0.24s] DEBUG: pam_open_session(0x17edd00, 0) -> 0 (Success)
[+0.27s] DEBUG: Opened ConsoleKit session 267043fc83e172caaafd56e70000000d-1332898252.394994-1757891176
[+0.27s] DEBUG: Dropping privileges to uid 1000
[+0.27s] DEBUG: Adding session authority to /home/mehmet/.Xauthority
[+0.27s] DEBUG: Restoring privileges
[+0.27s] DEBUG: Launching process 13898: /usr/sbin/lightdm-session '/usr/bin/gnome-session --session=ubuntu'
[+0.27s] DEBUG: New display ready, switching to it
[+0.27s] DEBUG: Activating VT 7
[+0.27s] DEBUG: pam_setcred(0x17edd00, PAM_ESTABLISH_CRED) -> 0 (Success)
[+0.27s] DEBUG: PAM returns environment 'PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games LANG=en_US.UTF-8'
[+0.27s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0

```

---

### Post by Mark Phelps on 2012-03-28
If the log time is correct, and that looks like 27 seconds, that is not a LONG time for Unity to load -- that is about right.

The move to the Unity desktop has slowed down loading in general.

If you want to get away from that, you should look into switching to the Classic Desktop -- but then, you would lose Unity.

---

### Post by vajorie on 2012-03-28
> **Mark Phelps said:**
> If the log time is correct, and that looks like 27 seconds, that is not a LONG time for Unity to load -- that is about right.
...

Thanks for your response :)

I think it takes about a minute or so. It surely feels like it could be faster, as what happens is: 

1. load my desktop wallpaper
2. wait and wait (on first boot, I thought it just froze there; I see no disk activity and I couldn't find what it is waiting for)
3. load everything (instantly)

It feels like the release upgrade did something wrong but I don't know what that could be... 

(and the laptop is supposed to be fast with an i7 @ 2.80GHz and a 7200rpm hard disk, and a capable graphics card.) Unity used to load pretty much instantly in 11.04 once the laptop booted. 

PS. So far, I tried reinstalling xserver-xorg-ati, reconfigure xserver-xorg, do a X -configure (which failed), reset unity (unity --reset), turn off vblank thru ccsm... Can anyone think of anything else?

---

### Post by Mark Phelps on 2012-03-28
I've got a six-core 3.2GHz 64-bit processor on my desktop, and it still takes nearly a minute from boot to working desktop.  So, sorry, don't have any tips to drastically reduce the startup time -- other than switching OUT of the Unity desktop.

---


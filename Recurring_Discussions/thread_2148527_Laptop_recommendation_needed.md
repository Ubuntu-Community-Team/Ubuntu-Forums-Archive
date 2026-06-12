---
title: "Laptop recommendation needed"
date: 2013-05-25
forum: Recurring Discussions
---

### Post by duncan12 on 2013-05-25
Hi all,

Currently I have an Acer Aspire 5534 — it's just over 3 years old now and it has the following problems:


[LIST]
[*]The microphone doesn't work with Linux
[*]The battery now lasts only 5 minutes, but it never did last more than 2 hours
[*]It overheats frequently — the idle temperature is about 70°C and it overheats when it exceeds 90°C. It tends to have a fairly cheap feel.
[*]It has only a 1.2 GHz processor and it's a grind to boot it up
[/LIST]

I'm looking at getting a new laptop. I want one that fulfills the following requirements:


[LIST]
[*]Compatibility with Linux
[*]Reasonable battery life
[*]Doesn't overheat — general good quality feel
[*]Processor: good enough that Ubuntu boots in less than a minute. Probably Intel i5 or i7. (RAM: don't really care. They all have > 4Gb nowadays).
[/LIST]

And on top of that, of course, I want it to be relatively cheap.

Are my needs too demanding or can someone recommend their laptop? :)

---

### Post by Yellow Pasque on 2013-05-25
I would wait for Haswell to be released and get something with a CPU based on that: [http://en.wikipedia.org/wiki/Intel_Haswell](http://en.wikipedia.org/wiki/Intel_Haswell)

In the meantime, you should figure out what's overheating the system. If the graphics driver got borked and you're running a 3D desktop (like Unity or Gnome-shell), then that can eat the battery quickly. Post your /var/log/Xorg.0.log

---

### Post by duncan12 on 2013-05-25
It's not so much of a problem now that I take care: I always have it propped up on a piece of wood when I use it and that helps. But it would be nice to fix it.

Here's /var/log/Xorg.0.log:

```

[    30.344] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    30.344] X Protocol Version 11, Revision 0
[    30.344] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    30.344] Current Operating System: Linux Duncan-Linux 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686
[    30.344] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=36e50d75-3842-43fe-8d54-f00023023655 ro quiet splash vt.handoff=7
[    30.344] Build Date: 04 August 2012  01:51:24AM
[    30.344] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 
[    30.344] Current version of pixman: 0.24.4
[    30.344] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    30.344] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    30.345] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May 26 06:00:17 2013
[    30.360] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    30.361] (==) No Layout section.  Using the first Screen section.
[    30.361] (==) No screen section available. Using defaults.
[    30.361] (**) |-->Screen "Default Screen Section" (0)
[    30.361] (**) |   |-->Monitor "<default monitor>"
[    30.361] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    30.361] (==) Automatically adding devices
[    30.361] (==) Automatically enabling devices
[    30.361] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    30.361] 	Entry deleted from font path.
[    30.362] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    30.362] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    30.362] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    30.362] (II) Loader magic: 0xb774c5a0
[    30.362] (II) Module ABI versions:
[    30.362] 	X.Org ANSI C Emulation: 0.4
[    30.362] 	X.Org Video Driver: 11.0
[    30.362] 	X.Org XInput driver : 16.0
[    30.362] 	X.Org Server Extension : 6.0
[    30.372] (--) PCI:*(0:1:5:0) 1002:9612:1025:031e rev 0, Mem @ 0xe0000000/268435456, 0xf2200000/65536, 0xf2100000/1048576, I/O @ 0x00007000/256
[    30.375] (II) Open ACPI successful (/var/run/acpid.socket)
[    30.375] (II) LoadModule: "extmod"
[    30.430] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    30.431] (II) Module extmod: vendor="X.Org Foundation"
[    30.431] 	compiled for 1.11.3, module version = 1.0.0
[    30.431] 	Module class: X.Org Server Extension
[    30.431] 	ABI class: X.Org Server Extension, version 6.0
[    30.431] (II) Loading extension MIT-SCREEN-SAVER
[    30.431] (II) Loading extension XFree86-VidModeExtension
[    30.431] (II) Loading extension XFree86-DGA
[    30.431] (II) Loading extension DPMS
[    30.431] (II) Loading extension XVideo
[    30.431] (II) Loading extension XVideo-MotionCompensation
[    30.431] (II) Loading extension X-Resource
[    30.431] (II) LoadModule: "dbe"
[    30.431] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    30.432] (II) Module dbe: vendor="X.Org Foundation"
[    30.432] 	compiled for 1.11.3, module version = 1.0.0
[    30.432] 	Module class: X.Org Server Extension
[    30.432] 	ABI class: X.Org Server Extension, version 6.0
[    30.432] (II) Loading extension DOUBLE-BUFFER
[    30.432] (II) LoadModule: "glx"
[    30.433] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    30.433] (II) Module glx: vendor="X.Org Foundation"
[    30.433] 	compiled for 1.11.3, module version = 1.0.0
[    30.433] 	ABI class: X.Org Server Extension, version 6.0
[    30.433] (==) AIGLX enabled
[    30.433] (II) Loading extension GLX
[    30.433] (II) LoadModule: "record"
[    30.434] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    30.434] (II) Module record: vendor="X.Org Foundation"
[    30.434] 	compiled for 1.11.3, module version = 1.13.0
[    30.434] 	Module class: X.Org Server Extension
[    30.434] 	ABI class: X.Org Server Extension, version 6.0
[    30.434] (II) Loading extension RECORD
[    30.434] (II) LoadModule: "dri"
[    30.435] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    30.435] (II) Module dri: vendor="X.Org Foundation"
[    30.435] 	compiled for 1.11.3, module version = 1.0.0
[    30.435] 	ABI class: X.Org Server Extension, version 6.0
[    30.435] (II) Loading extension XFree86-DRI
[    30.435] (II) LoadModule: "dri2"
[    30.436] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    30.436] (II) Module dri2: vendor="X.Org Foundation"
[    30.436] 	compiled for 1.11.3, module version = 1.2.0
[    30.436] 	ABI class: X.Org Server Extension, version 6.0
[    30.436] (II) Loading extension DRI2
[    30.436] (==) Matched fglrx as autoconfigured driver 0
[    30.436] (==) Matched ati as autoconfigured driver 1
[    30.436] (==) Matched vesa as autoconfigured driver 2
[    30.436] (==) Matched fbdev as autoconfigured driver 3
[    30.436] (==) Assigned the driver to the xf86ConfigLayout
[    30.436] (II) LoadModule: "fglrx"
[    30.437] (WW) Warning, couldn't open module fglrx
[    30.437] (II) UnloadModule: "fglrx"
[    30.437] (II) Unloading fglrx
[    30.437] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    30.437] (II) LoadModule: "ati"
[    30.438] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.438] (II) Module ati: vendor="X.Org Foundation"
[    30.438] 	compiled for 1.11.3, module version = 6.14.99
[    30.438] 	Module class: X.Org Video Driver
[    30.438] 	ABI class: X.Org Video Driver, version 11.0
[    30.438] (II) LoadModule: "radeon"
[    30.439] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.439] (II) Module radeon: vendor="X.Org Foundation"
[    30.439] 	compiled for 1.11.3, module version = 6.14.99
[    30.439] 	Module class: X.Org Video Driver
[    30.439] 	ABI class: X.Org Video Driver, version 11.0
[    30.439] (II) LoadModule: "vesa"
[    30.440] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.440] (II) Module vesa: vendor="X.Org Foundation"
[    30.440] 	compiled for 1.11.3, module version = 2.3.0
[    30.440] 	Module class: X.Org Video Driver
[    30.440] 	ABI class: X.Org Video Driver, version 11.0
[    30.440] (II) LoadModule: "fbdev"
[    30.441] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.441] (II) Module fbdev: vendor="X.Org Foundation"
[    30.441] 	compiled for 1.11.3, module version = 0.4.2
[    30.441] 	ABI class: X.Org Video Driver, version 11.0
[    30.441] (==) Matched fglrx as autoconfigured driver 0
[    30.441] (==) Matched ati as autoconfigured driver 1
[    30.441] (==) Matched vesa as autoconfigured driver 2
[    30.441] (==) Matched fbdev as autoconfigured driver 3
[    30.441] (==) Assigned the driver to the xf86ConfigLayout
[    30.441] (II) LoadModule: "fglrx"
[    30.442] (WW) Warning, couldn't open module fglrx
[    30.442] (II) UnloadModule: "fglrx"
[    30.442] (II) Unloading fglrx
[    30.442] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    30.442] (II) LoadModule: "ati"
[    30.443] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    30.443] (II) Module ati: vendor="X.Org Foundation"
[    30.443] 	compiled for 1.11.3, module version = 6.14.99
[    30.443] 	Module class: X.Org Video Driver
[    30.443] 	ABI class: X.Org Video Driver, version 11.0
[    30.443] (II) LoadModule: "vesa"
[    30.444] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.444] (II) Module vesa: vendor="X.Org Foundation"
[    30.444] 	compiled for 1.11.3, module version = 2.3.0
[    30.444] 	Module class: X.Org Video Driver
[    30.444] 	ABI class: X.Org Video Driver, version 11.0
[    30.444] (II) UnloadModule: "vesa"
[    30.444] (II) Unloading vesa
[    30.444] (II) Failed to load module "vesa" (already loaded, 0)
[    30.444] (II) LoadModule: "fbdev"
[    30.444] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.444] (II) Module fbdev: vendor="X.Org Foundation"
[    30.444] 	compiled for 1.11.3, module version = 0.4.2
[    30.444] 	ABI class: X.Org Video Driver, version 11.0
[    30.444] (II) UnloadModule: "fbdev"
[    30.444] (II) Unloading fbdev
[    30.444] (II) Failed to load module "fbdev" (already loaded, 0)
[    30.444] (II) RADEON: Driver for ATI Radeon chipsets:
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
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
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
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    30.454] (II) VESA: driver for VESA chipsets: vesa
[    30.454] (II) FBDEV: driver for framebuffer: fbdev
[    30.454] (++) using VT number 7


[    30.454] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    30.454] (II) [KMS] Kernel modesetting enabled.
[    30.454] (WW) Falling back to old probe method for vesa
[    30.454] (WW) Falling back to old probe method for fbdev
[    30.454] (II) Loading sub module "fbdevhw"
[    30.454] (II) LoadModule: "fbdevhw"
[    30.455] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.455] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.455] 	compiled for 1.11.3, module version = 0.0.2
[    30.455] 	ABI class: X.Org Video Driver, version 11.0
[    30.455] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    30.455] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    30.455] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.455] (==) RADEON(0): Default visual is TrueColor
[    30.455] (==) RADEON(0): RGB weight 888
[    30.455] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    30.455] (--) RADEON(0): Chipset: "ATI Radeon HD 3200 Graphics" (ChipID = 0x9612)
[    30.456] (II) RADEON(0): PCI card detected
[    30.456] drmOpenDevice: node name is /dev/dri/card0
[    30.456] drmOpenDevice: open result is 9, (OK)
[    30.456] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    30.456] drmOpenDevice: node name is /dev/dri/card0
[    30.456] drmOpenDevice: open result is 9, (OK)
[    30.456] drmOpenByBusid: drmOpenMinor returns 9
[    30.456] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    30.456] (II) Loading sub module "exa"
[    30.456] (II) LoadModule: "exa"
[    30.457] (II) Loading /usr/lib/xorg/modules/libexa.so
[    30.457] (II) Module exa: vendor="X.Org Foundation"
[    30.457] 	compiled for 1.11.3, module version = 2.5.0
[    30.457] 	ABI class: X.Org Video Driver, version 11.0
[    30.457] (II) RADEON(0): KMS Color Tiling: enabled
[    30.457] (II) RADEON(0): KMS Pageflipping: enabled
[    30.457] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    30.457] (II) RADEON(0): Output LVDS has no monitor section
[    30.485] (II) RADEON(0): Output VGA-0 has no monitor section
[    30.485] (II) RADEON(0): EDID for output LVDS
[    30.485] (II) RADEON(0): Manufacturer: LGD  Model: 210  Serial#: 0
[    30.485] (II) RADEON(0): Year: 2009  Week: 0
[    30.485] (II) RADEON(0): EDID Version: 1.3
[    30.485] (II) RADEON(0): Digital Display Input
[    30.485] (II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    30.485] (II) RADEON(0): Gamma: 2.20
[    30.485] (II) RADEON(0): No DPMS capabilities specified
[    30.486] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.486] (II) RADEON(0): First detailed timing is preferred mode
[    30.486] (II) RADEON(0): redX: 0.590 redY: 0.350   greenX: 0.330 greenY: 0.555
[    30.486] (II) RADEON(0): blueX: 0.153 blueY: 0.119   whiteX: 0.313 whiteY: 0.329
[    30.486] (II) RADEON(0): Manufacturer's mask: 0
[    30.486] (II) RADEON(0): Supported detailed timing:
[    30.486] (II) RADEON(0): clock: 75.1 MHz   Image Size:  345 x 194 mm
[    30.486] (II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1564 h_border: 0
[    30.486] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 800 v_border: 0
[    30.486] (II) RADEON(0):  LG Display
[    30.486] (II) RADEON(0): Monitor name: LP156WH3-TLA2
[    30.486] (II) RADEON(0): EDID (in hex):
[    30.486] (II) RADEON(0): 	00ffffffffffff0030e4100200000000
[    30.486] (II) RADEON(0): 	00130103802313780a28659759548e27
[    30.486] (II) RADEON(0): 	1e505400000001010101010101010101
[    30.486] (II) RADEON(0): 	010101010101561d56c6500020303020
[    30.486] (II) RADEON(0): 	350059c2100000190000000000000000
[    30.486] (II) RADEON(0): 	00000000000000000000000000fe004c
[    30.486] (II) RADEON(0): 	4720446973706c61790a2020000000fc
[    30.486] (II) RADEON(0): 	004c503135365748332d544c4132002a
[    30.486] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    30.486] (II) RADEON(0): Printing DDC gathered Modelines:
[    30.486] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    30.486] (II) RADEON(0): Printing probed modes for output LVDS
[    30.486] (II) RADEON(0): Modeline "1366x768"x60.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    30.486] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    30.486] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    30.486] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    30.486] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    30.486] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    30.486] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    30.486] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    30.516] (II) RADEON(0): EDID for output VGA-0
[    30.516] (II) RADEON(0): Output LVDS connected
[    30.516] (II) RADEON(0): Output VGA-0 disconnected
[    30.516] (II) RADEON(0): Using exact sizes for initial modes
[    30.516] (II) RADEON(0): Output LVDS using initial mode 1366x768
[    30.516] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    30.516] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fba0000
[    30.516] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    30.516] (**) RADEON(0): Display dimensions: (350, 190) mm
[    30.516] (**) RADEON(0): DPI set to (99, 102)
[    30.516] (II) Loading sub module "fb"
[    30.516] (II) LoadModule: "fb"
[    30.517] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.517] (II) Module fb: vendor="X.Org Foundation"
[    30.518] 	compiled for 1.11.3, module version = 1.0.0
[    30.518] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    30.518] (II) Loading sub module "ramdac"
[    30.518] (II) LoadModule: "ramdac"
[    30.518] (II) Module "ramdac" already built-in
[    30.518] (II) UnloadModule: "vesa"
[    30.518] (II) Unloading vesa
[    30.518] (II) UnloadModule: "fbdev"
[    30.518] (II) Unloading fbdev
[    30.518] (II) UnloadModule: "fbdevhw"
[    30.518] (II) Unloading fbdevhw
[    30.518] (--) Depth 24 pixmap format is 32 bpp
[    30.518] (II) RADEON(0): [DRI2] Setup complete
[    30.518] (II) RADEON(0): [DRI2]   DRI driver: r600
[    30.518] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    30.518] (II) RADEON(0): Front buffer size: 4224K
[    30.518] (II) RADEON(0): VRAM usage limit set to 228096K
[    30.518] (==) RADEON(0): Backing store disabled
[    30.518] (II) RADEON(0): Direct rendering enabled
[    30.518] (II) RADEON(0): Setting EXA maxPitchBytes
[    30.519] (II) EXA(0): Driver allocated offscreen pixmaps
[    30.519] (II) EXA(0): Driver registered support for the following operations:
[    30.519] (II)         Solid
[    30.519] (II)         Copy
[    30.519] (II)         Composite (RENDER acceleration)
[    30.519] (II)         UploadToScreen
[    30.519] (II)         DownloadFromScreen
[    30.519] (II) RADEON(0): Acceleration enabled
[    30.519] (==) RADEON(0): DPMS enabled
[    30.519] (==) RADEON(0): Silken mouse enabled
[    30.519] (II) RADEON(0): Set up textured video
[    30.519] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    30.519] (II) RADEON(0): [XvMC] Extension initialized.
[    30.519] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.520] (--) RandR disabled
[    30.520] (II) Initializing built-in extension Generic Event Extension
[    30.520] (II) Initializing built-in extension SHAPE
[    30.520] (II) Initializing built-in extension MIT-SHM
[    30.520] (II) Initializing built-in extension XInputExtension
[    30.520] (II) Initializing built-in extension XTEST
[    30.520] (II) Initializing built-in extension BIG-REQUESTS
[    30.520] (II) Initializing built-in extension SYNC
[    30.520] (II) Initializing built-in extension XKEYBOARD
[    30.520] (II) Initializing built-in extension XC-MISC
[    30.520] (II) Initializing built-in extension SECURITY
[    30.520] (II) Initializing built-in extension XINERAMA
[    30.520] (II) Initializing built-in extension XFIXES
[    30.520] (II) Initializing built-in extension RENDER
[    30.520] (II) Initializing built-in extension RANDR
[    30.520] (II) Initializing built-in extension COMPOSITE
[    30.520] (II) Initializing built-in extension DAMAGE
[    30.722] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.722] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.722] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.722] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.723] (II) AIGLX: Loaded and initialized r600
[    30.723] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.725] (II) RADEON(0): Setting screen physical size to 361 x 203
[    30.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.798] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    30.798] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.798] (II) LoadModule: "evdev"
[    30.798] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.799] (II) Module evdev: vendor="X.Org Foundation"
[    30.799] 	compiled for 1.11.3, module version = 2.7.0
[    30.799] 	Module class: X.Org XInput Driver
[    30.799] 	ABI class: X.Org XInput driver, version 16.0
[    30.799] (II) Using input driver 'evdev' for 'Power Button'
[    30.799] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.799] (**) Power Button: always reports core events
[    30.799] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.799] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.799] (--) evdev: Power Button: Found keys
[    30.799] (II) evdev: Power Button: Configuring as keyboard
[    30.799] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.799] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.799] (**) Option "xkb_rules" "evdev"
[    30.799] (**) Option "xkb_model" "pc105"
[    30.799] (**) Option "xkb_layout" "us"
[    30.801] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    30.801] (II) No input driver specified, ignoring this device.
[    30.801] (II) This device may have been added with another device file.
[    30.802] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    30.802] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.802] (II) Using input driver 'evdev' for 'Video Bus'
[    30.802] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.802] (**) Video Bus: always reports core events
[    30.802] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    30.802] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.802] (--) evdev: Video Bus: Found keys
[    30.802] (II) evdev: Video Bus: Configuring as keyboard
[    30.802] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input5/event5"
[    30.802] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.802] (**) Option "xkb_rules" "evdev"
[    30.802] (**) Option "xkb_model" "pc105"
[    30.802] (**) Option "xkb_layout" "us"
[    30.804] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.804] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.804] (II) Using input driver 'evdev' for 'Power Button'
[    30.804] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.804] (**) Power Button: always reports core events
[    30.804] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.804] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.804] (--) evdev: Power Button: Found keys
[    30.804] (II) evdev: Power Button: Configuring as keyboard
[    30.804] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    30.804] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    30.804] (**) Option "xkb_rules" "evdev"
[    30.804] (**) Option "xkb_model" "pc105"
[    30.804] (**) Option "xkb_layout" "us"
[    30.805] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    30.805] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.806] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.806] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.806] (**) Sleep Button: always reports core events
[    30.806] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    30.806] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.806] (--) evdev: Sleep Button: Found keys
[    30.806] (II) evdev: Sleep Button: Configuring as keyboard
[    30.806] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    30.806] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    30.806] (**) Option "xkb_rules" "evdev"
[    30.806] (**) Option "xkb_model" "pc105"
[    30.806] (**) Option "xkb_layout" "us"
[    30.807] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/event7)
[    30.807] (**) Logitech Unifying Device. Wireless PID:400a: Applying InputClass "evdev pointer catchall"
[    30.808] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400a'
[    30.808] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.808] (**) Logitech Unifying Device. Wireless PID:400a: always reports core events
[    30.808] (**) evdev: Logitech Unifying Device. Wireless PID:400a: Device: "/dev/input/event7"
[    30.808] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Vendor 0x46d Product 0xc52b
[    30.808] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found 20 mouse buttons
[    30.808] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found scroll wheel(s)
[    30.808] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found relative axes
[    30.808] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found x and y relative axes
[    30.808] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Configuring as mouse
[    30.808] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Adding scrollwheel support
[    30.808] (**) evdev: Logitech Unifying Device. Wireless PID:400a: YAxisMapping: buttons 4 and 5
[    30.808] (**) evdev: Logitech Unifying Device. Wireless PID:400a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.808] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/0003:046D:C52B.0003/input/input7/event7"
[    30.808] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400a" (type: MOUSE, id 10)
[    30.808] (II) evdev: Logitech Unifying Device. Wireless PID:400a: initialized for relative axes.
[    30.809] (**) Logitech Unifying Device. Wireless PID:400a: (accel) keeping acceleration scheme 1
[    30.809] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration profile 0
[    30.809] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration factor: 2.000
[    30.809] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration threshold: 4
[    30.810] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/mouse0)
[    30.810] (II) No input driver specified, ignoring this device.
[    30.810] (II) This device may have been added with another device file.
[    30.810] (II) config/udev: Adding input device CNF9011 (/dev/input/event6)
[    30.810] (**) CNF9011: Applying InputClass "evdev keyboard catchall"
[    30.810] (II) Using input driver 'evdev' for 'CNF9011'
[    30.810] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.811] (**) CNF9011: always reports core events
[    30.811] (**) evdev: CNF9011: Device: "/dev/input/event6"
[    30.811] (--) evdev: CNF9011: Vendor 0x4f2 Product 0xb175
[    30.811] (--) evdev: CNF9011: Found keys
[    30.811] (II) evdev: CNF9011: Configuring as keyboard
[    30.811] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input6/event6"
[    30.811] (II) XINPUT: Adding extended input device "CNF9011" (type: KEYBOARD, id 11)
[    30.811] (**) Option "xkb_rules" "evdev"
[    30.811] (**) Option "xkb_model" "pc105"
[    30.811] (**) Option "xkb_layout" "us"
[    30.812] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event8)
[    30.812] (II) No input driver specified, ignoring this device.
[    30.812] (II) This device may have been added with another device file.
[    30.813] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event9)
[    30.813] (II) No input driver specified, ignoring this device.
[    30.813] (II) This device may have been added with another device file.
[    30.814] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.814] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.814] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.814] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.814] (**) AT Translated Set 2 keyboard: always reports core events
[    30.814] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.814] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.814] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.814] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.814] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.814] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    30.814] (**) Option "xkb_rules" "evdev"
[    30.814] (**) Option "xkb_model" "pc105"
[    30.814] (**) Option "xkb_layout" "us"
[    30.815] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event10)
[    30.816] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.816] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.816] (II) LoadModule: "synaptics"
[    30.816] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.816] (II) Module synaptics: vendor="X.Org Foundation"
[    30.816] 	compiled for 1.11.3, module version = 1.6.2
[    30.816] 	Module class: X.Org XInput Driver
[    30.816] 	ABI class: X.Org XInput driver, version 16.0
[    30.816] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.816] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.817] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.817] (**) Option "Device" "/dev/input/event10"
[    30.868] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.868] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.868] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.874] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input10/event10"
[    30.874] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    30.874] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    30.874] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    30.874] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[    30.874] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.874] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    30.874] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.874] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.875] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.875] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    30.875] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.978] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    32.978] (II) RADEON(0): Printing DDC gathered Modelines:
[    32.978] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    33.964] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    33.964] (II) RADEON(0): Printing DDC gathered Modelines:
[    33.964] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    60.588] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    60.589] (II) RADEON(0): Printing DDC gathered Modelines:
[    60.589] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    62.794] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    62.794] (II) RADEON(0): Printing DDC gathered Modelines:
[    62.794] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    73.623] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    73.624] (II) RADEON(0): Printing DDC gathered Modelines:
[    73.624] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[    84.220] (II) RADEON(0): EDID vendor "LGD", prod id 528
[    84.220] (II) RADEON(0): Printing DDC gathered Modelines:
[    84.221] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[   120.145] (II) XKB: reuse xkmfile /var/lib/xkb/server-49D6BC4AFC8E1F4442B1D428615373BFBB28EC6C.xkm
[ 12059.996] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 12071.710] (II) Open ACPI successful (/var/run/acpid.socket)
[ 12071.710] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 12071.710] (II) RADEON(0): EDID vendor "LGD", prod id 528
[ 12071.710] (II) RADEON(0): Printing DDC gathered Modelines:
[ 12071.710] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[ 12071.756] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[ 12694.332] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 12705.998] (II) Open ACPI successful (/var/run/acpid.socket)
[ 12705.998] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 12705.999] (II) RADEON(0): EDID vendor "LGD", prod id 528
[ 12705.999] (II) RADEON(0): Printing DDC gathered Modelines:
[ 12705.999] (II) RADEON(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
[ 12706.054] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

```

Thanks

---

### Post by DJWYMAN on 2013-05-25
[http://www.dell.com/us/business/p/xps-13-linux/pd](http://www.dell.com/us/business/p/xps-13-linux/pd)  this one meats all of your demands except for the cheap part.  It comes with ubuntu installed so you know it is built for it.

---

### Post by DJWYMAN on 2013-05-25
[https://www.system76.com/laptops/model/lemu4](https://www.system76.com/laptops/model/lemu4)  heres another one though I cant speak on the quality of it but it is on the cheaper side price tag wise.

---

### Post by duncan12 on 2013-05-25
Thanks, the Dell one is simply too expensive, but System76 sounds like a good idea, and a good company to support :)

---

### Post by mörgæs on 2013-05-25
Before investing money into something new: Have you tried the classic low-tech solutions? 
a) install the Lubuntu desktop and 
b) take the CPU cooling unit apart and clean it from dust.

---

### Post by duncan12 on 2013-07-03
To update this old thread, I ended up getting the Lenovo E531. It has a 15.6" screen, Intel i5 3.2GHz processor, 4GB RAM, 500GB HD, and Lenovo seems to get a pretty good reputation. It is listed on [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/). It comes with Windows 8 but I will be sure to remove that!

When it arrives I will update this post with my experience.

---

### Post by operative-terminus on 2013-09-27
> **duncan12 said:**
> To update this old thread, I ended up getting the Lenovo E531. It has a 15.6" screen, Intel i5 3.2GHz processor, 4GB RAM, 500GB HD, and Lenovo seems to get a pretty good reputation. It is listed on [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/). It comes with Windows 8 but I will be sure to remove that!

When it arrives I will update this post with my experience.

That's the laptop I just got. Everything works fine except wireless, which doesn't work at all (I have tried with both Network Manager and Wicd). Has that been your experience as well?

---

### Post by duncan12 on 2013-09-27
> **operative-terminus said:**
> That's the laptop I just got. Everything works fine except wireless, which doesn't work at all (I have tried with both Network Manager and Wicd). Has that been your experience as well?

It depends on your kernel version, at first I was only kernel 3.8 because that is the latest that Linux Mint 15 supports. Wireless "just worked" but it would randomly lock up sometimes, which was a major problem. I upgraded to 3.9 using the "mainline kernels". Kernel 3.9 fixed the locking up but stopped the wireless working. I eventually found the fix.

[LIST=1]
[*]Check that you are indeed already on a kernel version greater than 3.9 using the "uname -r" command. Those are the only kernels where these steps apply.
[*]Run "sudo apt-get remove bcmwl-kernel-source". (Why? Broadcom had updated the bcmwl-kernel-source package to work on kernel 3.9+ but the latest version was not yet in the repos and therefore it would fail to install on kernel 3.9+.)
[*]Download the latest actual version as a .deb from [http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source) and install it.
[*]Ensure the bcmwl-kernel-source package is actually in use by your computer by opening something like "proprietary drivers" or "hardware drivers" in the control panel, and ticking the box next to bcmwl-kernel-source.
[*]You may need to reboot and then your wireless should work! :D
[/LIST]
Further troubleshooting:

[LIST]
[*]Ensure that all wireless related packages other than bcmwl-kernel-source are gone, eg things like b43-fwcutter, just search in synaptic and mark them for uninstall.
[/LIST]

Hope this helps, it's my experience anyway. Please let me know how you go.

By the way, this laptop is really great, after getting the few Linux hiccups out the way!

---

### Post by mörgæs on 2013-09-28
Thanks for your advice on the Lenovo. 

If you have the time please add a post to the [laptop compatibility list]("http://ubuntuforums.org/showthread.php?t=1543006") about how to get it running.

---

### Post by duncan12 on 2013-09-28
> **mörgæs said:**
> Thanks for your advice on the Lenovo. 

If you have the time please add a post to the [laptop compatibility list]("http://ubuntuforums.org/showthread.php?t=1543006") about how to get it running.

Done thanks.

---

### Post by Bucky Ball on 2013-09-28
*Thread moved to **Recurring Discussions**.*

---

### Post by operative-terminus on 2013-09-30
> **duncan12 said:**
> It depends on your kernel version, at first I was only kernel 3.8 because that is the latest that Linux Mint 15 supports. Wireless "just worked" but it would randomly lock up sometimes, which was a major problem. I upgraded to 3.9 using the "mainline kernels". Kernel 3.9 fixed the locking up but stopped the wireless working. I eventually found the fix.

[LIST=1]
[*]Check that you are indeed already on a kernel version greater than 3.9 using the "uname -r" command. Those are the only kernels where these steps apply.
[*]Run "sudo apt-get remove bcmwl-kernel-source". (Why? Broadcom had updated the bcmwl-kernel-source package to work on kernel 3.9+ but the latest version was not yet in the repos and therefore it would fail to install on kernel 3.9+.)
[*]Download the latest actual version as a .deb from [http://packages.ubuntu.com/raring/bcmwl-kernel-source](http://packages.ubuntu.com/raring/bcmwl-kernel-source) and install it.
[*]Ensure the bcmwl-kernel-source package is actually in use by your computer by opening something like "proprietary drivers" or "hardware drivers" in the control panel, and ticking the box next to bcmwl-kernel-source.
[*]You may need to reboot and then your wireless should work! :D
[/LIST]
Further troubleshooting:

[LIST]
[*]Ensure that all wireless related packages other than bcmwl-kernel-source are gone, eg things like b43-fwcutter, just search in synaptic and mark them for uninstall.
[/LIST]

Hope this helps, it's my experience anyway. Please let me know how you go.

By the way, this laptop is really great, after getting the few Linux hiccups out the way!


Thanks so much for taking the time to explain your workaround. I was going to try it, but prior to that I upgraded to the 13.10 Beta and the wireless works now! I'm having some other issues now, but at least the wireless works, and that's what I was really after :). If I end up having to go back down to 13.04 I will definitely try your workaround and let you know how it goes.

---


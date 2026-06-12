---
title: "Hanging on _ after boot, no virtual console"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2015-02-26
Hi everyone, 

What happened to *Absolute Beginner Talk*? :cry:


Anyhow, I've recently come crawling back to Ubuntu, and installed the pre-packaged Gnome version two days ago. This morning I went to boot and was met with a solid black screen (GUI boot, and no virtual console). Tried booting with an older kernel to no avail. Went into recovery options and hit 'resume' to force a verbose boot a few times - system was hanging after the message 'saned disabled; edit /etc/default/saned' (no virtual console).

Thinking this odd, I booted into a live environment and enabled it in the file listed, just to see what would happen. System just hung on the message that was prior to the above. 

Booted back into the live environment, changed to a permanent verbose boot and to the 'console' GRUB2 menu etc. I also chroot-ed into my install and ran apt-get update, apt-get upgrade (and apt-get autoremove). I then ran update-grub (to complete the changes affected), and the output looked like it ran twice - and in the middle contained something about the FGLRX_core package (I have an AMD graphics card, and use the latest drivers from AMD's site). I wish I'd recorded the output, but alas I did not; is it stored in a log file anywhere? The system had been restarted multiple times without issue using the currently installed FGLRX packages.

Now when I boot, I get through the verbose stage and onto the "computername login:" screen, but that disappears after a second or less and is replaced by a '_' cursor (probably blinking, but my memory fails me). I still do not have access to a virtual console - which is peculiar, as it's already shown me the login prompt. 

Anybody have any ideas? I suppose I should try purging all fglrx-related packages...

---

### Post by Jakey_TheSnake on 2015-02-26
Update: apt-get remove --purge fglrx* && apt-get autoremove has got me back into my install. It appears the proprietary AMD drivers are buggered somehow, which is odd; as I mentioned before they were working fine previously. The only thing I changed was installing the Catalyst Control Centre package, and using it to enable Tear Free Desktop and disable VSync. 

In the interests of science (and me, as I'd like to use fglrx), I reinstalled the necessary packages and was met with the same blinking _ after boot as before. Will settings be left over in configuration files even after a purge?

---

### Post by sandyd on 2015-03-10
Check the XOrg log (/var/log/Xorg.0.log) after the blinking cursor occurs to see if there are any errors.

If you find it more convineant than having to reboot constantly, install a SSH server on the computer and log in remotely to check the logs when you are at the blinking cursor.

---

### Post by Jakey_TheSnake on 2015-03-10
Cheers for the reply. 

I can SSH into my computer out-of-the-box, is this different from installing an (other?) SSH server?

---

### Post by sandyd on 2015-03-10
> **Jakey_TheSnake said:**
> Cheers for the reply. 

I can SSH into my computer out-of-the-box, is this different from installing an (other?) SSH server?

Nope, if you can do that, you have a ssh server installed.

Any ssh server is fine.

---

### Post by Jakey_TheSnake on 2015-03-11
There's quite a lot of stuff printed in relation to AMD/fglrx, including a "No valid AMD display adapters found" line. 

```
[     2.469] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[     2.469] X Protocol Version 11, Revision 0
[     2.469] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[     2.469] Current Operating System: Linux janux 3.16.0-31-generic #41-Ubuntu SMP Tue Feb 10 15:24:04 UTC 2015 x86_64
[     2.469] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic root=UUID=e1a540ac-4feb-4339-a888-4f62473b7148 ro quiet splash vt.handoff=7
[     2.469] Build Date: 12 February 2015  02:46:23PM
[     2.469] xorg-server 2:1.16.0-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[     2.469] Current version of pixman: 0.32.4
[     2.469] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     2.469] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.469] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 17:13:36 2015
[     2.470] (==) Using config file: "/etc/X11/xorg.conf"
[     2.470] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.471] (==) ServerLayout "aticonfig Layout"
[     2.471] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[     2.471] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[     2.472] (**) |   |-->Device "aticonfig-Device[0]-0"
[     2.472] (==) Automatically adding devices
[     2.472] (==) Automatically enabling devices
[     2.472] (==) Automatically adding GPU devices
[     2.473] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.473] 	Entry deleted from font path.
[     2.473] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.473] 	Entry deleted from font path.
[     2.473] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.473] 	Entry deleted from font path.
[     2.473] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.473] 	Entry deleted from font path.
[     2.473] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.473] 	Entry deleted from font path.
[     2.473] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     2.473] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.473] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.473] (II) Loader magic: 0x7f67b8a07d80
[     2.473] (II) Module ABI versions:
[     2.473] 	X.Org ANSI C Emulation: 0.4
[     2.473] 	X.Org Video Driver: 18.0
[     2.473] 	X.Org XInput driver : 21.0
[     2.473] 	X.Org Server Extension : 8.0
[     2.474] (--) PCI:*(0:1:0:0) 1002:679a:1682:3221 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[     2.474] (II) "glx" will be loaded by default.
[     2.474] (WW) "xmir" is not to be loaded by default. Skipping.
[     2.474] (II) LoadModule: "glx"
[     2.474] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[     2.476] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[     2.476] 	compiled for 6.9.0, module version = 1.0.0
[     2.476] (II) LoadModule: "fglrx"
[     2.476] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[     2.506] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     2.506] 	compiled for 1.4.99.906, module version = 14.50.2
[     2.506] 	Module class: X.Org Video Driver
[     2.507] (II) Loading sub module "fglrxdrm"
[     2.507] (II) LoadModule: "fglrxdrm"
[     2.507] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[     2.508] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[     2.508] 	compiled for 1.4.99.906, module version = 14.50.2
[     2.508] (II) AMD Proprietary Linux Driver Version Identifier:14.50.2
[     2.508] (II) AMD Proprietary Linux Driver Release Identifier: 14.501.1003                          
[     2.508] (II) AMD Proprietary Linux Driver Build Date: Nov 20 2014 21:22:54
[     2.508] (++) using VT number 7

[     2.508] (WW) Falling back to old probe method for fglrx
[     2.514] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     2.516] ukiDynamicMajor: found major device number 251
[     2.516] ukiDynamicMajor: found major device number 251
[     2.516] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     2.516] ukiOpenDevice: node name is /dev/ati/card0
[     2.516] ukiOpenDevice: open result is 9, (OK)
[     2.732] ukiOpenByBusid: ukiOpenMinor returns 9
[     2.732] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     2.735] (EE) No supported AMD display adapters were found
[     2.735] (EE) No devices detected.
[     2.735] (==) Matched fglrx as autoconfigured driver 0
[     2.735] (==) Matched ati as autoconfigured driver 1
[     2.735] (==) Matched modesetting as autoconfigured driver 2
[     2.735] (==) Matched fbdev as autoconfigured driver 3
[     2.735] (==) Matched vesa as autoconfigured driver 4
[     2.735] (==) Assigned the driver to the xf86ConfigLayout
[     2.735] (II) LoadModule: "fglrx"
[     2.735] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[     2.735] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[     2.735] 	compiled for 1.4.99.906, module version = 14.50.2
[     2.735] 	Module class: X.Org Video Driver
[     2.735] (II) LoadModule: "ati"
[     2.735] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     2.736] (II) Module ati: vendor="X.Org Foundation"
[     2.736] 	compiled for 1.16.0, module version = 7.4.0
[     2.736] 	Module class: X.Org Video Driver
[     2.736] 	ABI class: X.Org Video Driver, version 18.0
[     2.736] (II) LoadModule: "radeon"
[     2.736] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     2.738] (II) Module radeon: vendor="X.Org Foundation"
[     2.738] 	compiled for 1.16.0, module version = 7.4.0
[     2.738] 	Module class: X.Org Video Driver
[     2.738] 	ABI class: X.Org Video Driver, version 18.0
[     2.738] (II) LoadModule: "modesetting"
[     2.738] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.738] (II) Module modesetting: vendor="X.Org Foundation"
[     2.738] 	compiled for 1.16.0, module version = 0.9.0
[     2.738] 	Module class: X.Org Video Driver
[     2.738] 	ABI class: X.Org Video Driver, version 18.0
[     2.738] (II) LoadModule: "fbdev"
[     2.739] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.739] (II) Module fbdev: vendor="X.Org Foundation"
[     2.739] 	compiled for 1.16.0, module version = 0.4.4
[     2.739] 	Module class: X.Org Video Driver
[     2.739] 	ABI class: X.Org Video Driver, version 18.0
[     2.739] (II) LoadModule: "vesa"
[     2.739] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.739] (II) Module vesa: vendor="X.Org Foundation"
[     2.739] 	compiled for 1.16.0, module version = 2.3.3
[     2.739] 	Module class: X.Org Video Driver
[     2.739] 	ABI class: X.Org Video Driver, version 18.0
[     2.739] (II) AMD Proprietary Linux Driver Version Identifier:14.50.2
[     2.739] (II) AMD Proprietary Linux Driver Release Identifier: 14.501.1003                          
[     2.739] (II) AMD Proprietary Linux Driver Build Date: Nov 20 2014 21:22:54
[     2.739] (II) RADEON: Driver for ATI Radeon chipsets:
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
	SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
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
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
	OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
	HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
	BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
	KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
	MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
	KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
	HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[     2.744] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.744] (II) FBDEV: driver for framebuffer: fbdev
[     2.744] (II) VESA: driver for VESA chipsets: vesa
[     2.744] (++) using VT number 7

[     2.744] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     2.744] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     2.744] (WW) Falling back to old probe method for fglrx
[     2.744] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[     2.745] ukiDynamicMajor: found major device number 251
[     2.745] ukiDynamicMajor: found major device number 251
[     2.745] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     2.745] ukiOpenDevice: node name is /dev/ati/card0
[     2.745] ukiOpenDevice: open result is 11, (OK)
[     2.745] ukiOpenByBusid: ukiOpenMinor returns 11
[     2.745] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     2.745] (EE) No supported AMD display adapters were found
[     2.746] (II) [KMS] drm report modesetting isn't supported.
[     2.746] (EE) open /dev/dri/card0: No such file or directory
[     2.746] (WW) Falling back to old probe method for modesetting
[     2.746] (EE) open /dev/dri/card0: No such file or directory
[     2.746] (II) Loading sub module "fbdevhw"
[     2.746] (II) LoadModule: "fbdevhw"
[     2.746] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.746] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.746] 	compiled for 1.16.0, module version = 0.0.2
[     2.746] 	ABI class: X.Org Video Driver, version 18.0
[     2.746] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[     2.746] (II) FBDEV(2): using default device
[     2.746] (WW) Falling back to old probe method for vesa
[     2.746] (EE) Screen 0 deleted because of no matching config section.
[     2.746] (II) UnloadModule: "radeon"
[     2.746] (EE) Screen 0 deleted because of no matching config section.
[     2.746] (II) UnloadModule: "modesetting"
[     2.746] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[     2.746] (==) FBDEV(0): RGB weight 888
[     2.746] (==) FBDEV(0): Default visual is TrueColor
[     2.746] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     2.746] (II) FBDEV(0): hardware: VESA VGA (video memory: 8128kB)
[     2.746] (II) FBDEV(0): checking modes against framebuffer device...
[     2.746] (II) FBDEV(0): checking modes against monitor...
[     2.746] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[     2.746] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[     2.746] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[     2.746] (==) FBDEV(0): DPI set to (96, 96)
[     2.746] (II) Loading sub module "fb"
[     2.746] (II) LoadModule: "fb"
[     2.747] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.747] (II) Module fb: vendor="X.Org Foundation"
[     2.747] 	compiled for 1.16.0, module version = 1.0.0
[     2.747] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     2.747] (**) FBDEV(0): using shadow framebuffer
[     2.747] (II) Loading sub module "shadow"
[     2.747] (II) LoadModule: "shadow"
[     2.747] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     2.748] (II) Module shadow: vendor="X.Org Foundation"
[     2.748] 	compiled for 1.16.0, module version = 1.1.0
[     2.748] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     2.748] (II) UnloadModule: "fglrx"
[     2.748] (II) Unloading fglrx
[     2.748] (II) UnloadSubModule: "fglrxdrm"
[     2.748] (II) Unloading fglrxdrm
[     2.748] (II) UnloadModule: "vesa"
[     2.748] (II) Unloading vesa
[     2.748] (==) Depth 24 pixmap format is 32 bpp
[     2.748] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     2.749] (==) FBDEV(0): Backing store enabled
[     2.750] (**) FBDEV(0): DPMS enabled
[     2.750] (==) RandR enabled
[     2.753] (II) SELinux: Disabled on system
[     2.754] (EE) GLX error: Can not get required symbols.
[     2.760] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     2.762] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     2.762] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.762] (II) LoadModule: "evdev"
[     2.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     2.763] (II) Module evdev: vendor="X.Org Foundation"
[     2.763] 	compiled for 1.16.0, module version = 2.9.0
[     2.763] 	Module class: X.Org XInput Driver
[     2.763] 	ABI class: X.Org XInput driver, version 21.0
[     2.763] (II) Using input driver 'evdev' for 'Power Button'
[     2.763] (**) Power Button: always reports core events
[     2.763] (**) evdev: Power Button: Device: "/dev/input/event1"
[     2.764] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.764] (--) evdev: Power Button: Found keys
[     2.764] (II) evdev: Power Button: Configuring as keyboard
[     2.764] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     2.764] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     2.764] (**) Option "xkb_rules" "evdev"
[     2.764] (**) Option "xkb_model" "pc105"
[     2.764] (**) Option "xkb_layout" "gb"
[     2.765] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[     2.765] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     2.765] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.765] (II) Using input driver 'evdev' for 'Power Button'
[     2.765] (**) Power Button: always reports core events
[     2.765] (**) evdev: Power Button: Device: "/dev/input/event0"
[     2.765] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.765] (--) evdev: Power Button: Found keys
[     2.765] (II) evdev: Power Button: Configuring as keyboard
[     2.765] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     2.765] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     2.765] (**) Option "xkb_rules" "evdev"
[     2.765] (**) Option "xkb_model" "pc105"
[     2.765] (**) Option "xkb_layout" "gb"
[     2.765] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event7)
[     2.765] (II) No input driver specified, ignoring this device.
[     2.765] (II) This device may have been added with another device file.
[     2.765] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event8)
[     2.765] (II) No input driver specified, ignoring this device.
[     2.765] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event3)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event4)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event5)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event6)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event9)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event10)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event11)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.766] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event12)
[     2.766] (II) No input driver specified, ignoring this device.
[     2.766] (II) This device may have been added with another device file.
[     2.767] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event13)
[     2.767] (II) No input driver specified, ignoring this device.
[     2.767] (II) This device may have been added with another device file.
[     2.767] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/event14)
[     2.767] (**) Razer Razer Mamba: Applying InputClass "evdev pointer catchall"
[     2.767] (II) Using input driver 'evdev' for 'Razer Razer Mamba'
[     2.767] (**) Razer Razer Mamba: always reports core events
[     2.767] (**) evdev: Razer Razer Mamba: Device: "/dev/input/event14"
[     2.767] (--) evdev: Razer Razer Mamba: Vendor 0x1532 Product 0x24
[     2.767] (--) evdev: Razer Razer Mamba: Found 9 mouse buttons
[     2.767] (--) evdev: Razer Razer Mamba: Found scroll wheel(s)
[     2.767] (--) evdev: Razer Razer Mamba: Found relative axes
[     2.767] (--) evdev: Razer Razer Mamba: Found x and y relative axes
[     2.767] (II) evdev: Razer Razer Mamba: Configuring as mouse
[     2.767] (II) evdev: Razer Razer Mamba: Adding scrollwheel support
[     2.767] (**) evdev: Razer Razer Mamba: YAxisMapping: buttons 4 and 5
[     2.767] (**) evdev: Razer Razer Mamba: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     2.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/0003:1532:0024.0001/input/input17/event14"
[     2.767] (II) XINPUT: Adding extended input device "Razer Razer Mamba" (type: MOUSE, id 8)
[     2.767] (II) evdev: Razer Razer Mamba: initialized for relative axes.
[     2.767] (**) Razer Razer Mamba: (accel) keeping acceleration scheme 1
[     2.767] (**) Razer Razer Mamba: (accel) acceleration profile 0
[     2.767] (**) Razer Razer Mamba: (accel) acceleration factor: 2.000
[     2.767] (**) Razer Razer Mamba: (accel) acceleration threshold: 4
[     2.767] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/mouse0)
[     2.767] (II) No input driver specified, ignoring this device.
[     2.767] (II) This device may have been added with another device file.
[     2.767] (II) config/udev: Adding input device Razer Razer Mamba (/dev/input/event15)
[     2.767] (**) Razer Razer Mamba: Applying InputClass "evdev keyboard catchall"
[     2.767] (II) Using input driver 'evdev' for 'Razer Razer Mamba'
[     2.767] (**) Razer Razer Mamba: always reports core events
[     2.767] (**) evdev: Razer Razer Mamba: Device: "/dev/input/event15"
[     2.767] (--) evdev: Razer Razer Mamba: Vendor 0x1532 Product 0x24
[     2.767] (--) evdev: Razer Razer Mamba: Found 1 mouse buttons
[     2.767] (--) evdev: Razer Razer Mamba: Found scroll wheel(s)
[     2.767] (--) evdev: Razer Razer Mamba: Found relative axes
[     2.767] (II) evdev: Razer Razer Mamba: Forcing relative x/y axes to exist.
[     2.767] (--) evdev: Razer Razer Mamba: Found absolute axes
[     2.767] (II) evdev: Razer Razer Mamba: Forcing absolute x/y axes to exist.
[     2.767] (--) evdev: Razer Razer Mamba: Found keys
[     2.767] (II) evdev: Razer Razer Mamba: Configuring as mouse
[     2.767] (II) evdev: Razer Razer Mamba: Configuring as keyboard
[     2.767] (II) evdev: Razer Razer Mamba: Adding scrollwheel support
[     2.767] (**) evdev: Razer Razer Mamba: YAxisMapping: buttons 4 and 5
[     2.767] (**) evdev: Razer Razer Mamba: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     2.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/0003:1532:0024.0002/input/input18/event15"
[     2.767] (II) XINPUT: Adding extended input device "Razer Razer Mamba" (type: KEYBOARD, id 9)
[     2.767] (**) Option "xkb_rules" "evdev"
[     2.767] (**) Option "xkb_model" "pc105"
[     2.767] (**) Option "xkb_layout" "gb"
[     2.768] (II) evdev: Razer Razer Mamba: initialized for relative axes.
[     2.768] (WW) evdev: Razer Razer Mamba: ignoring absolute axes.
[     2.768] (**) Razer Razer Mamba: (accel) keeping acceleration scheme 1
[     2.768] (**) Razer Razer Mamba: (accel) acceleration profile 0
[     2.768] (**) Razer Razer Mamba: (accel) acceleration factor: 2.000
[     2.768] (**) Razer Razer Mamba: (accel) acceleration threshold: 4
[     2.768] (II) config/udev: Adding input device Logitech Gaming Keyboard G105 (/dev/input/event16)
[     2.768] (**) Logitech Gaming Keyboard G105: Applying InputClass "evdev keyboard catchall"
[     2.768] (II) Using input driver 'evdev' for 'Logitech Gaming Keyboard G105'
[     2.768] (**) Logitech Gaming Keyboard G105: always reports core events
[     2.768] (**) evdev: Logitech Gaming Keyboard G105: Device: "/dev/input/event16"
[     2.768] (--) evdev: Logitech Gaming Keyboard G105: Vendor 0x46d Product 0xc248
[     2.768] (--) evdev: Logitech Gaming Keyboard G105: Found keys
[     2.768] (II) evdev: Logitech Gaming Keyboard G105: Configuring as keyboard
[     2.768] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/0003:046D:C248.0003/input/input19/event16"
[     2.768] (II) XINPUT: Adding extended input device "Logitech Gaming Keyboard G105" (type: KEYBOARD, id 10)
[     2.768] (**) Option "xkb_rules" "evdev"
[     2.768] (**) Option "xkb_model" "pc105"
[     2.768] (**) Option "xkb_layout" "gb"
[     2.768] (II) config/udev: Adding input device Logitech Gaming Keyboard G105 (/dev/input/event17)
[     2.768] (**) Logitech Gaming Keyboard G105: Applying InputClass "evdev keyboard catchall"
[     2.768] (II) Using input driver 'evdev' for 'Logitech Gaming Keyboard G105'
[     2.768] (**) Logitech Gaming Keyboard G105: always reports core events
[     2.768] (**) evdev: Logitech Gaming Keyboard G105: Device: "/dev/input/event17"
[     2.768] (--) evdev: Logitech Gaming Keyboard G105: Vendor 0x46d Product 0xc248
[     2.768] (--) evdev: Logitech Gaming Keyboard G105: Found keys
[     2.768] (II) evdev: Logitech Gaming Keyboard G105: Configuring as keyboard
[     2.768] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.1/0003:046D:C248.0004/input/input20/event17"
[     2.768] (II) XINPUT: Adding extended input device "Logitech Gaming Keyboard G105" (type: KEYBOARD, id 11)
[     2.768] (**) Option "xkb_rules" "evdev"
[     2.768] (**) Option "xkb_model" "pc105"
[     2.768] (**) Option "xkb_layout" "gb"
[     2.769] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event2)
[     2.769] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     2.769] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     2.769] (**) Eee PC WMI hotkeys: always reports core events
[     2.769] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event2"
[     2.769] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     2.769] (--) evdev: Eee PC WMI hotkeys: Found keys
[     2.769] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     2.769] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input5/event2"
[     2.769] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[     2.769] (**) Option "xkb_rules" "evdev"
[     2.769] (**) Option "xkb_model" "pc105"
[     2.769] (**) Option "xkb_layout" "gb"
[     2.771] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     3.228] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.866] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BB54422A303CE4DB23D02C1BF81235398E5836A.xkm
[     3.871] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BB54422A303CE4DB23D02C1BF81235398E5836A.xkm
[   602.904] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   602.904] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   602.905] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

---

### Post by sandyd on 2015-03-12
Seems like your Video card isn't supported by the driver
Whats the output of
```

lspci
```

---


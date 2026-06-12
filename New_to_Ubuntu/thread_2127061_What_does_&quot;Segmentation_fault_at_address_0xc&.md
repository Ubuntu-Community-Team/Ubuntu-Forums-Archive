---
title: "What does &quot;Segmentation fault at address 0xc&quot; mean?"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by Acharn on 2013-03-19
I've installed a HIS AMD Radeon HD 6670 graphics card in my Ubuntu 12.04 Acer Aspire M-1610 desktop. It runs OK with the OpenGL drivers, and I would really prefer not to bother with the proprietary fglrx driver, but I can't run some Windows games in Wine and I was hoping they would run with the AMD drivers. Trouble is, when I install the driver and reboot the X server does not start. I saved the /var/log/Xorg.0.log file into a text file in my home directory. Here it is:
```
[    12.069] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    12.069] X Protocol Version 11, Revision 0
[    12.069] Build Operating System: Linux 2.6.24-31-xen i686 Ubuntu
[    12.069] Current Operating System: Linux roger-Aspire-M1610 3.5.0-10-generic #10-Ubuntu SMP Mon Aug 13 16:35:16 UTC 2012 i686
[    12.069] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-10-generic root=UUID=aa930990-0b62-4bea-971b-6fb5332311cd ro quiet splash vt.handoff=7
[    12.069] Build Date: 09 July 2012  05:18:23PM
[    12.069] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support) 
[    12.070] Current version of pixman: 0.26.0
[    12.070] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.070] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.070] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 19 10:44:19 2013
[    12.070] (==) Using config file: "/etc/X11/xorg.conf"
[    12.070] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.070] (==) ServerLayout "aticonfig Layout"
[    12.070] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    12.070] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    12.071] (**) |   |-->Device "aticonfig-Device[0]-0"
[    12.071] (==) Automatically adding devices
[    12.071] (==) Automatically enabling devices
[    12.131] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.131] 	Entry deleted from font path.
[    12.166] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    12.166] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.166] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.166] (II) Loader magic: 0xb77155a0
[    12.166] (II) Module ABI versions:
[    12.166] 	X.Org ANSI C Emulation: 0.4
[    12.166] 	X.Org Video Driver: 12.0
[    12.166] 	X.Org XInput driver : 16.0
[    12.166] 	X.Org Server Extension : 6.0
[    12.167] (--) PCI:*(0:1:0:0) 1002:6758:1787:2012 rev 0, Mem @ 0xd0000000/268435456, 0xfdcc0000/131072, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    12.167] (II) Open ACPI successful (/var/run/acpid.socket)
[    12.167] (II) "extmod" will be loaded by default.
[    12.167] (II) "dbe" will be loaded by default.
[    12.167] (II) "glx" will be loaded by default.
[    12.167] (II) "record" will be loaded by default.
[    12.167] (II) "dri" will be loaded by default.
[    12.167] (II) "dri2" will be loaded by default.
[    12.167] (II) LoadModule: "extmod"
[    12.224] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    12.224] (II) Module extmod: vendor="X.Org Foundation"
[    12.224] 	compiled for 1.12.3, module version = 1.0.0
[    12.224] 	Module class: X.Org Server Extension
[    12.224] 	ABI class: X.Org Server Extension, version 6.0
[    12.224] (II) Loading extension MIT-SCREEN-SAVER
[    12.224] (II) Loading extension XFree86-VidModeExtension
[    12.224] (II) Loading extension XFree86-DGA
[    12.224] (II) Loading extension DPMS
[    12.224] (II) Loading extension XVideo
[    12.224] (II) Loading extension XVideo-MotionCompensation
[    12.224] (II) Loading extension X-Resource
[    12.224] (II) LoadModule: "dbe"
[    12.225] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    12.225] (II) Module dbe: vendor="X.Org Foundation"
[    12.225] 	compiled for 1.12.3, module version = 1.0.0
[    12.225] 	Module class: X.Org Server Extension
[    12.225] 	ABI class: X.Org Server Extension, version 6.0
[    12.225] (II) Loading extension DOUBLE-BUFFER
[    12.225] (II) LoadModule: "glx"
[    12.225] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    12.226] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    12.226] 	compiled for 6.9.0, module version = 1.0.0
[    12.226] (II) Loading extension GLX
[    12.226] (II) LoadModule: "record"
[    12.226] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    12.227] (II) Module record: vendor="X.Org Foundation"
[    12.227] 	compiled for 1.12.3, module version = 1.13.0
[    12.227] 	Module class: X.Org Server Extension
[    12.227] 	ABI class: X.Org Server Extension, version 6.0
[    12.227] (II) Loading extension RECORD
[    12.227] (II) LoadModule: "dri"
[    12.227] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    12.227] (II) Module dri: vendor="X.Org Foundation"
[    12.227] 	compiled for 1.12.3, module version = 1.0.0
[    12.227] 	ABI class: X.Org Server Extension, version 6.0
[    12.227] (II) Loading extension XFree86-DRI
[    12.227] (II) LoadModule: "dri2"
[    12.228] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    12.228] (II) Module dri2: vendor="X.Org Foundation"
[    12.228] 	compiled for 1.12.3, module version = 1.2.0
[    12.228] 	ABI class: X.Org Server Extension, version 6.0
[    12.228] (II) Loading extension DRI2
[    12.228] (II) LoadModule: "fglrx"
[    12.228] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    12.257] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    12.257] 	compiled for 1.4.99.906, module version = 8.96.4
[    12.257] 	Module class: X.Org Video Driver
[    12.257] (II) Loading sub module "fglrxdrm"
[    12.257] (II) LoadModule: "fglrxdrm"
[    12.258] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    12.258] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    12.258] 	compiled for 1.4.99.906, module version = 8.96.4
[    12.258] (II) ATI Proprietary Linux Driver Version Identifier:8.96.4
[    12.258] (II) ATI Proprietary Linux Driver Release Identifier: 8.96.7                               
[    12.258] (II) ATI Proprietary Linux Driver Build Date: Mar 12 2012 13:06:47
[    12.258] (++) using VT number 7

[    12.258] (WW) Falling back to old probe method for fglrx
[    12.266] (II) Loading PCS database from /etc/ati/amdpcsdb
[    12.267] (--) Chipset Supported AMD Graphics Processor (0x6758) found
[    12.267] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    12.268] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    12.268] (II) AMD Video driver is signed
[    12.268] (II) fglrx(0): pEnt->device->identifier=0xb8af8d20
[    12.268] (II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
[    12.268] 
[    12.268] Backtrace:
[    12.268] 0: /usr/bin/X (xorg_backtrace+0x49) [0xb76a82c9]
[    12.269] 1: /usr/bin/X (0xb7522000+0x189fba) [0xb76abfba]
[    12.269] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb74ff40c]
[    12.269] 3: /usr/lib/i386-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs111_atiddxLeaveVT+0x4a) [0xb64d0e5a]
[    12.269] 4: /usr/bin/X (xf86DeleteScreen+0x6d) [0xb75a696d]
[    12.269] 
[    12.269] Segmentation fault at address 0xc
[    12.269] 
Caught signal 11 (Segmentation fault). Server aborting
[    12.269] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    12.269] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.269] 
[    12.271]  ddxSigGiveUp: Closing log
[    12.271] Server terminated with error (1). Closing log file.

```
I have a vague memory of what "segmentation fault" meant when the CPU was an 80286 or 80386, but am not clear what it means with an Intel duo-core chip. Or is this an indication of something else? I'm really lost here.

---

### Post by CSNate on 2013-03-19
Even for an Intel Core series chip it means the same as it did with i386 or i486.  You've essentially tried to access memory that does not exist.  In this case, it seems to me that the cause is either from a bug or incompatibility with the drivers.  How did you install your drivers?

---

### Post by Impavidus on 2013-03-19
Have you checked your windows games with the [wine application database]("http://appdb.winehq.org/")?  If they are listed as garbage new drivers won't help.

---

### Post by Acharn on 2013-03-19
> **Impavidus said:**
> Have you checked your windows games with the [wine application database]("http://appdb.winehq.org/")?  If they are listed as garbage new drivers won't help.

Ah, thanks for the reminder. I'll do that. I've got one which seems to work fine, Codename Panzers Phase 1, so that may be the problem. I'd still like to find out what the problem is with the drivers, though.

---

### Post by Acharn on 2013-03-19
> **CSNate said:**
> Even for an Intel Core series chip it means the same as it did with i386 or i486.  You've essentially tried to access memory that does not exist.  In this case, it seems to me that the cause is either from a bug or incompatibility with the drivers.  How did you install your drivers?

I used the terminal, command: 'sudo apt-get install fglrx fglrx-amdcccle'. To get back to the OpenGL drivers I used the command: 'sudo apt-get remove --purge fglrx fglrx-amdcccle'. Oh, after I installed them  but before rebooting, I ran 'sudo aticonfig --initial'. I tried to run the Catalyst Control Center, but it reported that it did not find an AMD driver, which I thought was kind of ominous but attributed to not having rebooted yet. I've tried several times to install the drivers, but this is the first time I saved a copy of the /var/log/Xorg.0.log file.

---


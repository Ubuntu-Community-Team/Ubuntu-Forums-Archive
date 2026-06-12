---
title: "[SOLVED] Intel Graphics Controller is Killing Me!!!"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by dr.silly on 2008-11-08
I am installing ubuntu on a machine with a Intel 82915G/GV/910GL Express Chipset Controller. Everything works great except about every five minutes my screen gets pretty little lines and dots and then reboots. It will happen with compiz on and off. and happens usually when I try to do something that requires more graphics power like opening a maximized window.

Any help?

---

### Post by Peter09 on 2008-11-09
First check which driver you are actually using

Can you Post the output of

```
lshw -C display
```

---

### Post by dr.silly on 2008-11-09
the output of lshw -C display looks something like this:

```
*-display:0 UNCLAIMED
	description: VGA compatible controller
	product: 82915G/GV/910GL Integrated Graphics Controller
	vendor: Intel Corporation
	physical id: 2
	bus info: pci@0000:00:02.0
	version: 04
	width: 32 bits
	clock: 33MHz
	capabilities: pm bus_master cap_list
	configuration: latency=0
*-display:1 UNCLAIMED
	description: Display Controller
	product: 82915G Integrated Graphics Controller
	vendor: Intel Corporation
	physical id: 2.1
	bus info: pci@0000:00:02.1
	version: 04
	width: 32 bits
	clock: 33MHz
	capabilities: pm bus_master cap_list
	configuration: latency=0

```

---

### Post by phidia on 2008-11-09
I assume your video card was automatically detected and set up-intel usually is.

I think you need to look in your log files and look at the time stamps in the logs to find what's happening. You can view log files from System > Admin > System Log or /var/log.

---

### Post by dr.silly on 2008-11-09
Alright this is pathetic. System Log is crashing my computer

---

### Post by dr.silly on 2008-11-09
I've got the logs in the terminal but I'm not finding anything. What exactly am I looking for?

---

### Post by dr.silly on 2008-11-09
I'm getting something that says unregistered pardevice before the reboots if that means anything.

---

### Post by phidia on 2008-11-09
> **dr.silly said:**
> I've got the logs in the terminal but I'm not finding anything. What exactly am I looking for?

Look at /var/log/messages; dmesg; xorg.log maybe fail.log?

It is a lot of work to wade through those but if you know the time of the crash you should see something related to it there. 

If you want you can attach dmesg and/or messages here-not copy/paste but attach as a file.

---

### Post by PmDematagoda on 2008-11-09
dr.silly, could you just post the log files? More specifically:-
/var/log/Xorg.0.log
and
/var/log/messages

---

### Post by dr.silly on 2008-11-09
I set the driver in xorg.conf to vesa and now it's not crashing but still no xgl or anything.

In response to PmDematagoda: Firefox would crash my computer. But I'll do it now that i can.

---

### Post by PmDematagoda on 2008-11-09
> **dr.silly said:**
> I set the driver in xorg.conf to vesa and now it's not crashing but still no xgl or anything.

In response to PmDematagoda: Firefox would crash my computer. But I'll do it now that i can.

If you face difficulty in obtaining the outputs, you can redirect the output to a file elsewhere with:-
```
cat /var/log/messages > file-to-send-output-to
```
and
```
cat /var/log/Xorg.0.log > file-to-send-output-to
```
and then access the files via a different install or live cd.

---

### Post by dr.silly on 2008-11-09
Ok these files are too big to upload.

---

### Post by PmDematagoda on 2008-11-09
> **dr.silly said:**
> Ok these files are to upload.

The Xorg log doesn't seem to be too big so you can upload it or just post it completely, but for the messages log, can you just post the last 25 lines atleast using:-
```
dmesg | tail -25
```

---

### Post by dr.silly on 2008-11-09
I've been looking through these files for a while and I really don't think there's anything there

---

### Post by dr.silly on 2008-11-09
ok here's that output

```
sam@sam-desktop:~$ dmesg | tail -25
[  143.333240] type=1503 audit(1226240965.270:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=5679 profile="/usr/sbin/cupsd"
[  143.412144] ppdev0: registered pardevice
[  143.460033] ppdev0: unregistered pardevice
[  145.156660] ppdev0: registered pardevice
[  145.204216] ppdev0: unregistered pardevice
[  322.696477] __ratelimit: 3 callbacks suppressed
[  322.696489] gnome-system-lo[5644]: segfault at ebfe8132 ip b7858486 sp bfdd2430 error 7 in libcairo.so.2.10800.0[b7836000+70000]
[  356.415899] gnome-system-lo[5739]: segfault at 31800 ip b7622a12 sp bfdda320 error 4 in libgobject-2.0.so.0.1800.2[b7601000+3c000]
[  552.213759] compiz.real[5515]: segfault at 4b20022 ip 08055c8c sp bfaf8f50 error 4 in compiz.real[8048000+34000]
[ 1510.243390] mtrr: base(0xc0000000) is not aligned on a size(0x7b0000) boundary
[ 1590.236303] ppdev0: registered pardevice
[ 1590.284325] ppdev0: unregistered pardevice
[ 1590.314200] type=1503 audit(1226242412.250:16): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6742/net/" pid=6742 profile="/usr/sbin/cupsd"
[ 1591.334944] type=1503 audit(1226242413.270:17): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6749/net/" pid=6749 profile="/usr/sbin/cupsd"
[ 1591.337474] type=1503 audit(1226242413.274:18): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.339631] type=1503 audit(1226242413.274:19): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.343558] type=1503 audit(1226242413.278:20): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.345568] type=1503 audit(1226242413.282:21): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.347553] type=1503 audit(1226242413.282:22): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.349662] type=1503 audit(1226242413.286:23): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.351670] type=1503 audit(1226242413.286:24): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6749 profile="/usr/sbin/cupsd"
[ 1591.424136] ppdev0: registered pardevice
[ 1591.472064] ppdev0: unregistered pardevice
[ 1592.876341] ppdev0: registered pardevice
[ 1592.924193] ppdev0: unregistered pardevice
```

---

### Post by dr.silly on 2008-11-09
Xorg.0.log is different now that I changed to vesa to post here do want to still try and get some of it?

---

### Post by PmDematagoda on 2008-11-09
About the Xorg log, try and get the one with the greatest number appended to it. That is, a number greater than 0.

About the dmesg log, these lines look very suspicious:-
```
[  322.696489] gnome-system-lo[5644]: segfault at ebfe8132 ip b7858486 sp bfdd2430 error 7 in libcairo.so.2.10800.0[b7836000+70000]
[  356.415899] gnome-system-lo[5739]: segfault at 31800 ip b7622a12 sp bfdda320 error 4 in libgobject-2.0.so.0.1800.2[b7601000+3c000]
[  552.213759] compiz.real[5515]: segfault at 4b20022 ip 08055c8c sp bfaf8f50 error 4 in compiz.real[8048000+34000]
```

---

### Post by dr.silly on 2008-11-09
ah ha! I didn't notice those.

Heres Xorg.99.log:

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux sam-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.99.log", Time: Sun Nov  9 09:21:44 2008
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0@0:2:0) Intel Corporation 82915G/GV/910GL Integrated Graphics Controller rev 4, Mem @ 0xdff00000/0, 0xc0000000/0, 0xdfec0000/0, I/O @ 0x0000e898/0
(--) PCI: (0@0:2:1) Intel Corporation 82915G Integrated Graphics Controller rev 4, Mem @ 0xdff80000/0
List of video drivers:
	i128
	ark
	neomagic
	mach64
	sis
	rendition
	voodoo
	i810
	ati
	radeon
	geode
	vmware
	cirrus
	tdfx
	r128
	intel
	tseng
	trident
	i740
	s3
	s3virge
	chips
	mga
	siliconmotion
	v4l
	ztv
	savage
	openchrome
	apm
	sisusb
	nv
	fbdev
	vesa
(II) LoadModule: "i128"

(II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
(II) Module i128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ark"

(II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
(II) Module ark: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.7.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "neomagic"

(II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
(II) Module neomagic: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mach64"

(II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
(II) Module mach64: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "sis"

(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.10.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "rendition"

(II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
(II) Module rendition: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 4.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "voodoo"

(II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
(II) Module voodoo: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i810"

(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ati"

(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "geode"

(II) Loading /usr/lib/xorg/modules/drivers//geode_drv.so
(II) Module geode: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vmware"

(II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
(II) Module vmware: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 10.16.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "cirrus"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "tdfx"

(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
(II) Module tdfx: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "r128"

(II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Failed to load module "intel" (already loaded, -1074349404)
(II) LoadModule: "tseng"

(II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
(II) Module tseng: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.1.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "trident"

(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "i740"

(II) Loading /usr/lib/xorg/modules/drivers//i740_drv.so
(II) Module i740: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3"

(II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
(II) Module s3: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "s3virge"

(II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
(II) Module s3virge: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.10.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "chips"

(II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
(II) Module chips: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "mga"

(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.4.9
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "siliconmotion"

(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.6.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "v4l"

(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "ztv"

(II) Loading /usr/lib/xorg/modules/drivers//ztv_drv.so
(II) Module ztv: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 0.0.1
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "savage"

(II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
(II) Module savage: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "openchrome"

(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.1, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "apm"

(II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
(II) Module apm: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "sisusb"

(II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
(II) Module sisusb: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.1.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "fbdev"

(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for i128
(WW) Falling back to old probe method for ark
(WW) Falling back to old probe method for neomagic
(WW) Falling back to old probe method for sis
(WW) Falling back to old probe method for voodoo
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(WW) Falling back to old probe method for cirrus
(II) Loading sub module "cirrus_laguna"
(II) LoadModule: "cirrus_laguna"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
(II) Module cirrus_laguna: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "cirrus_alpine"
(II) LoadModule: "cirrus_alpine"

(II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
(II) Module cirrus_alpine: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(WW) Falling back to old probe method for tseng
(WW) Falling back to old probe method for trident
(WW) Falling back to old probe method for i740
(WW) Falling back to old probe method for s3
(WW) Falling back to old probe method for s3virge
(WW) Falling back to old probe method for siliconmotion
(WW) Falling back to old probe method for v4l
(II) v4l driver for Video4Linux
(WW) Falling back to old probe method for z4l
(II) z4l driver for Video4Linux
(WW) Falling back to old probe method for apm
(WW) Falling back to old probe method for sisusb
(II) FBDEV: driver for framebuffer: fbdev
(II) VESA: driver for VESA chipsets: vesa
(++) Using config file: "//xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(**) ModulePath set to "/usr/lib/xorg/modules"
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7872 kB
(II) intel(0): VESA VBE OEM: Intel(r)915G/915GV/910GL Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)915G/915GV/910GL Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level 2
(II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
(II) intel(0): VESA VBE DDC read successfully


Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is //xorg.conf.new

To test the server, run 'X -config //xorg.conf.new'

```

I see in the list of drivers it says i810 and that's what I thought mine was so I'll to try it.

---

### Post by dr.silly on 2008-11-09
it also list the driver intel is that it maybe?

---

### Post by dr.silly on 2008-11-09
Ok i810 driver flat out doesn't work (no gdm) and the intel driver gives me the same problems that I get if i don't set a driver.

---

### Post by dr.silly on 2008-11-09
just being curious I tried i740 no luck same problems as with i810

---

### Post by dr.silly on 2008-11-09
Am I stuck with vesa?

---

### Post by dr.silly on 2008-11-09
OK I finally figured this out. Here's what I did:

1. uninstalled xserver-xorg-video-intel
2. installed xserver-xorg-video-i810
3. set driver to "i810"

And fully functional finally!

---


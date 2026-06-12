---
title: "Games Not Working, Were Working Before"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by davethebrave on 2013-02-03
My netbook's hardware is, with the right drivers, capable of running the games I've been trying to run. I know this because only a few days ago, all of them were working under Ubuntu. I've since installed lubuntu, and I'm not 100% sure what's wrong because I'm not 100% sure what my drivers were before. I thought they were the current Mesa OpenGL drivers, but those seem to be installed from what I can see. I'm a bit of a newb though, and I don't really trust my own assessments of this stuff. 

The error that happens is that nothing happens. I try to open the game, and it's as if I did nothing. I've tried three games so far, and for each one the shell script brings me to the option to execute, and I click it, and then nothing happens. It doesn't hang or freeze or lag or anything, it just doesn't execute. When I looked up this error, I found people mostly suggesting driver updates, but I think (not sure, but *I think*) that they're fine? I wish I'd kept track of what was current, re: drivers, before I did this wipe and reinstall.

---

### Post by davethebrave on 2013-02-03
Just in case it helps, here's what lspci -k spit out: 

```
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: ASUSTeK Computer Inc. Device 83ac
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: ASUSTeK Computer Inc. Device 83ac
```

And here's what hwinfo spit out: 

```
12: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _Znp.Opejx8JdAT0
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Model: "Intel VGA compatible controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa011 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x83ac 
  Driver: "i915"
  Driver Modules: "drm"
  Memory Range: 0xf7e00000-0xf7e7ffff (rw,non-prefetchable)
  I/O Ports: 0xdc00-0xdc07 (rw)
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xf7d00000-0xf7dfffff (rw,non-prefetchable)
  IRQ: 44 (46252 events)
  Module Alias: "pci:v00008086d0000A011sv00001043sd000083ACbc03sc00i00"
  Driver Info #0:
    Driver Status: i915 is active
    Driver Activation Cmd: "modprobe i915"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 02.1: 0380 Display controller
  [Created at pci.318]
  Unique ID: ruGf.vF0Mr_bHS46
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: graphics card
  Model: "Intel Display controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa012 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x83ac 
  Memory Range: 0xf7e80000-0xf7efffff (rw,non-prefetchable)
  Module Alias: "pci:v00008086d0000A012sv00001043sd000083ACbc03sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

---

### Post by davethebrave on 2013-02-08
Disregard this, I've uninstalled lubuntu and reinstalled ubuntu.

---


---
title: "internal dvd writer sata (lite-on) issues"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by binsiram on 2008-04-22
any help is appreciated...
wasted 4 dvd's

Burning with growisofs 7.0.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/dvdrw -dvd-video -V "DVD-ABC" "/home/xyz/dvd-abc"
=========================================================
Executing 'genisoimage -dvd-video -V DVD-ABC /home/xyz/dvd-abc | builtin_dd of=/dev/dvdrw obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.41% done, estimate finish Tue Apr 22 19:57:30 2008
  0.83% done, estimate finish Tue Apr 22 19:57:30 2008
  1.24% done, estimate finish Tue Apr 22 19:58:50 2008
/dev/dvdrw: engaging DVD-R DAO upon user request...
/dev/dvdrw: reserving 1207115 blocks
/dev/dvdrw: "Current Write Speed" is 3.3x1352KBps.
  1.66% done, estimate finish Tue Apr 22 20:53:49 2008
  2.07% done, estimate finish Tue Apr 22 20:43:20 2008
  2.49% done, estimate finish Tue Apr 22 20:37:03 2008
  2.90% done, estimate finish Tue Apr 22 20:31:58 2008
....
.........
..............
 99.00% done, estimate finish Tue Apr 22 20:02:25 2008
 99.41% done, estimate finish Tue Apr 22 20:02:25 2008
 99.83% done, estimate finish Tue Apr 22 20:02:25 2008
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4248
Path table size(bytes): 42
Max brk space used 0
1207115 extents written (2357 MB)
:-[ WRITE@LBA=126b40h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/dvdrw: flushing cache
:-[ FLUSH CACHE failed with SK=2h/ASC=04h/ACQ=01h]: Resource temporarily unavailable
=========================================================
Done. You should now have a working DVD. Please visit
the tovid homepage: [http://www.tovid.org](http://www.tovid.org)

---

### Post by binsiram on 2008-04-22
bump!!

---

### Post by warp99 on 2008-04-23
> **binsiram said:**
> any help is appreciated...
wasted 4 dvd's

Burning with growisofs 7.0.1 using the following command:
growisofs -use-the-force-luke=dao -dvd-compat  -Z /dev/dvdrw -dvd-video -V "DVD-ABC" "/home/xyz/dvd-abc"
=========================================================
Executing 'genisoimage -dvd-video -V DVD-ABC /home/xyz/dvd-abc | builtin_dd of=/dev/dvdrw obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.41% done, estimate finish Tue Apr 22 19:57:30 2008
  0.83% done, estimate finish Tue Apr 22 19:57:30 2008
  1.24% done, estimate finish Tue Apr 22 19:58:50 2008
/dev/dvdrw: engaging DVD-R DAO upon user request...
/dev/dvdrw: reserving 1207115 blocks
/dev/dvdrw: "Current Write Speed" is 3.3x1352KBps.
  1.66% done, estimate finish Tue Apr 22 20:53:49 2008
  2.07% done, estimate finish Tue Apr 22 20:43:20 2008
  2.49% done, estimate finish Tue Apr 22 20:37:03 2008
  2.90% done, estimate finish Tue Apr 22 20:31:58 2008
....
.........
..............
 99.00% done, estimate finish Tue Apr 22 20:02:25 2008
 99.41% done, estimate finish Tue Apr 22 20:02:25 2008
 99.83% done, estimate finish Tue Apr 22 20:02:25 2008
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4248
Path table size(bytes): 42
Max brk space used 0
1207115 extents written (2357 MB)
:-[ WRITE@LBA=126b40h failed with SK=0h/ASC=00h/ACQ=03h]: Input/output error
:-( write failed: Input/output error
/dev/dvdrw: flushing cache
:-[ FLUSH CACHE failed with SK=2h/ASC=04h/ACQ=01h]: Resource temporarily unavailable
=========================================================
Done. You should now have a working DVD. Please visit
the tovid homepage: [http://www.tovid.org](http://www.tovid.org)

Is your sata controller a software raid controller? Linux doesn't have code for the ATAPI interface for certain sata controllers, such as VIA VT6420, since the specification for ATAPI was never implemented by the manufacturer so proprietary software runs the ATAPI interface for DVD/CD-Rom.

Run the following command:
```
lspci -v 
```
then scroll down the list until you get to the controller. If it says this:
```
IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
```
then your sata DVD will not burn properly because the software to run it is proprietary and out of reach from the kernel developers.

---

### Post by binsiram on 2008-04-23
> **warp99 said:**
> Is your sata controller a software raid controller? Linux doesn't have code for the ATAPI interface for certain sata controllers, such as VIA VT6420, since the specification for ATAPI was never implemented by the manufacturer so proprietary software runs the ATAPI interface for DVD/CD-Rom.

Run the following command:
```
lspci -v 
```
then scroll down the list until you get to the controller. If it says this:
```
IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
```
then your sata DVD will not burn properly because the software to run it is proprietary and out of reach from the kernel developers.

Thanks for the response. This is what I have for the IDE interface.

00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Micro-Star International Co., Ltd. Unknown device 366f
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>


Let me know if you need any more datails.

---

### Post by binsiram on 2008-04-23
bump!!

---


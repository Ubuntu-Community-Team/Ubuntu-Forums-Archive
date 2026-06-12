---
title: "Ubuntu 18.04 does not mount 1TB NTFS drive"
date: 2019-04-03
forum: New to Ubuntu
---

### Post by lasloureiro on 2019-04-03
Hello,

I just installed Ubuntu 18.04 and the external HDD (NTFS) i have for storage, it's not working.
The disk is detected but i can't find any files in it, and as i'm a new at this i can't understand why this is happening. I previously had installed Linux Mint and it worked perfectly.

lsusb:
Bus 002 Device 005: ID 1058:10b8 Western Digital Technologies, Inc. Elements Portable (WDBU6Y, WDBUZG)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b217 Chicony Electronics Co., Ltd Lenovo Integrated Camera (0.3MP)
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo fdisk -l:

Disk /dev/sdc: 1,4 TiB, 1500267937792 bytes, 2930210816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xcaa54367


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1        2048 2930210815 2930208768  1,4T  7 HPFS/NTFS/exFAT

Can someone help me with this?

Thank you,

LL

---

### Post by oldfred on 2019-04-03
If Windows 10 or 8, it has fast start up which sets hibernation flag. It does not fully unmount other partitions.
The Linux NTFS driver will not mount hibernated NTFS partitions to prevent damage.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---


---
title: "MAC on Ubuntu?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-31
Hi,

I would like to connect my friends MAC formatted external hard drive to my Ubuntu system so I can copy some of his stuff. Is it possible to be done? If so, how?

Thanks

---

### Post by TheLions on 2008-10-31
it should work with these:

[http://ubuntuforums.org/showthread.php?t=646975](http://ubuntuforums.org/showthread.php?t=646975)

---

### Post by phidia on 2008-10-31
You should be able to read HFS+ without any additional configuration.
You said copy so that should be no problem-you won't be able to write to an HFS+ drive.

---

### Post by phidia on 2008-10-31
You should be able to read HFS+ without any additional configuration.
You said copy so that should be no problem-you won't be able to write to an HFS+ drive.

---

### Post by Konstabel on 2008-10-31
How do I mount the device?

---

### Post by phidia on 2008-10-31
> **Konstabel said:**
> How do I mount the device?

How are you connecting this (it's a hard drive correct?) 

My hfs+ drive automounts but after you plug your drive in open a terminal and enter "dmesg" you should see some output related to the drive there.

If you have the drive mounted in some external device that's not supported by linux that could be the problem.

---

### Post by Konstabel on 2008-10-31
It is a usb external harddrive.

I only have an ssh connection to my system. It serves as a file backup server

---

### Post by Konstabel on 2008-10-31
With the fdisk -l command I get the following:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5d268a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156290903+  ee  EFI GPT

---

### Post by phidia on 2008-10-31
I'm not sure-and I'm not sure what you're up to either but perhaps [this link]("http://www.command-tab.com/2008/02/08/gpt-protective-partitions-and-windows-xp/") will help.

---

### Post by Konstabel on 2008-10-31
I have a home network Windows PC and Ubuntu file backup system. Now I am borrowing an external hard drive which has a MAC file system. I would like to connect this external hard drive to my Ubuntu machine to copy some stuff. Since the Ubuntu machine is a backup, I only have ssh control over it.

---

### Post by cariboo on 2008-10-31
Plug the device in and check dmesg like this:

```
tail -n 10 /var/log/dmesg
```

This will print out the last 10 lines of dmesg, you should see a device label like sdb sdb1 if the device is recognized. then just manually mount the drive:

```
mount /dev/sdbx /mnt
```

where /dev/sdbx /is the device number of your external hard drive that was assigned when it was plugged in.

Jim

---

### Post by Konstabel on 2008-10-31
The last few lines just running dmesg gives:
[ 1766.314284] hfs: can't find a HFS filesystem on dev sdb.
[ 2173.323441] autofs: called with bogus options
[ 3206.312779] hfs: can't find a HFS filesystem on dev sdb1.
[ 4627.132437] usb 2-1: USB disconnect, address 2
[ 4757.505121] usb 2-1: new full speed USB device using ohci_hcd and address 3
[ 4757.721028] usb 2-1: configuration #1 chosen from 1 choice
[ 4757.741046] scsi3 : SCSI emulation for USB Mass Storage devices
[ 4757.741585] usb-storage: device found at 3
[ 4757.741588] usb-storage: waiting for device to settle before scanning
[ 4762.741019] usb-storage: device scan complete
[ 4762.813968] scsi 3:0:0:0: Direct-Access     FUJITSU  MHW2160BHPL           PQ: 0 ANSI: 2 CCS
[ 4762.824958] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 4762.831952] sd 3:0:0:0: [sdb] Write Protect is off
[ 4762.831955] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 4762.831957] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4762.842938] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[ 4762.849933] sd 3:0:0:0: [sdb] Write Protect is off
[ 4762.849936] sd 3:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 4762.849937] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 4762.849941]  sdb: sdb1 sdb2
[ 4762.993968] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 4762.994002] sd 3:0:0:0: Attached scsi generic sg1 type 0

running the command "tail -n 10 /var/log/dmesg" gives 
[  118.391991] input: Power Button (FF) as /devices/virtual/input/input1
[  118.402264] ACPI: Power Button (FF) [PWRF]
[  118.402328] input: Power Button (CM) as /devices/virtual/input/input2
[  118.418246] ACPI: Power Button (CM) [PWRB]
[  118.871863] AMD768 RNG detected
[  119.705567] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  121.589433] lp: driver loaded but no devices found
[  121.747242] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[  122.311895] EXT3 FS on sda1, internal journal
[  123.486615] ip_tables: (C) 2000-2006 Netfilter Core Team


Don't really know what to make of this.

---

### Post by phidia on 2008-10-31
It looks like there are two partitons (sdb1; sdb2) you can attempt to mount those with > sudo mount -t hfsplus /dev/sdb1 /mnt/sdb1 

You need to create the mountpoint prior to doing the mount command. 

To create the mountpoint enter > sudo mkdir /mnt/sdb1

---


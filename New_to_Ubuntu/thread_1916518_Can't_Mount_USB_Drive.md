---
title: "Can't Mount USB Drive"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by talisman.26 on 2012-01-28
I've been through many threads, and my situation hasn't been posted that I can see.  The hard drive is a new Seagate 1.5 TB USB 3.0 (backwards compatible).  I formatted it with Windows 7 to get rid of the software that autoloads and used the NTFS option.  It will mount just fine in Windows 7 and my netbook Lubuntu 11.10, but not on this machine, Lubuntu 10.04.  It will show up under lsusb but not fdisk -l, and dmesg gives a funny output.


```
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 002 Device 005: ID 0bc2:2332 Seagate RSS LL[/COLOR]C 
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 104: ID 413c:2100 Dell Computer Corp. SK-3106 Keyboard
Bus 001 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17b88b82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1568    12594928+  83  Linux
/dev/sda2            1569        9730    65555665+   5  Extended
/dev/sda5            1569        2077     4088511   82  Linux swap / Solaris
/dev/sda6            2078        5869    30452369   83  Linux
/dev/sda7            5869        9565    29689856   83  Linux
/dev/sda8            9565        9730     1323008   82  Linux swap / Solaris

```

```
~$ dmesg | tail
[ 2599.483682] sd 26:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 2599.483690] sd 26:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 3f 00 00 08 00
[ 2599.483710] end_request: I/O error, dev sdb, sector 63
[ 2599.483723] Buffer I/O error on device sdb1, logical block 0
[ 2599.483732] Buffer I/O error on device sdb1, logical block 1
[ 2599.656053] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 2599.972057] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 2600.288062] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 2600.608051] usb 2-2: reset full speed USB device using uhci_hcd and address 5
[ 2600.984050] usb 2-2: reset full speed USB device using uhci_hcd and address 5

```

Can anyone assist?

**EDIT**  I should probably mention I can mount other external hard drives without any issues.

---

### Post by ajgreeny on 2012-01-28
Does the disk show up if you use parted instead of fdisk?  ```
sudo parted -l
```I wonder if it has been partitioned using something other than a standard ms-dos partition table, eg GPT.

---

### Post by talisman.26 on 2012-01-28
Thanks for the quick reply, but no, it doesn't:


```
~$ sudo parted -l
[sudo] password for talis: 
Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  12.9GB  12.9GB  primary   ext4            boot
 2      12.9GB  80.0GB  67.1GB  extended
 5      12.9GB  17.1GB  4187MB  logical   linux-swap(v1)
 6      17.1GB  48.3GB  31.2GB  logical   ext4
 7      48.3GB  78.7GB  30.4GB  logical   ext4
 8      78.7GB  80.0GB  1355MB  logical   linux-swap(v1)



Error: /dev/sdb: unrecognised disk label
```

Tell me I can't use the label name in 10.04...
I used Ally's Monster Drive

**EDIT**  Going to try and rename it "External"

---

### Post by talisman.26 on 2012-01-28
Didn't work... Still gives Error: /dev/sdb: unrecognised disk label

---

### Post by ajgreeny on 2012-01-28
Remove the apostrophe in the disk label and try again.

---

### Post by talisman.26 on 2012-01-28
I did...it's named External now.

---

### Post by ajgreeny on 2012-01-28
Are there files on it that you need?  If there are, can you see if it will mount in windows, and backup the files that way, then boot to ubuntu and format the disk again with gparted.  If the disk is empty just format it with gparted and see if that works.

---

### Post by talisman.26 on 2012-01-29
gParted won't see it.  I'm just going to upgrade the O/S.  It is an empty drive, but I was going to move stuff to it.  Thanks for your help though!

---


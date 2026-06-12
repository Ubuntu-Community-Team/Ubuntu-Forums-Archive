---
title: "External USB hard drive not detected. Previously working"
date: 2015-11-12
forum: New to Ubuntu
---

### Post by Jack_Dickerson on 2015-11-12
Hello, 
I have a previously working external USB hard drive no longer being detected.  It's where I save all my data.  
I really need some info on it. (of course no backup).

I've been using it.  It worked perfectly yesterday. Today not even detected.  
     However GPARTED still detects it:
TOSHIBA MK4026GAX    37.26 GiB    /dev/sdb
Partition Table: msdos   Heads: 255   Sectors/track: 63  total sectors: 78140160  Sector size: 512
Format: Fat32
But file manager (PCManFM) no longer detects it.  -- NO error messages.

The USB port is tested and working with other devices. Also tested it in other USB ports, not detected.
I have tested it with both a _known good_ adapter cable, and the USB hdd external case it was in when it quit. 
I'm running LXLE, (based on Ubuntu 14.04.3 LTS).   I've searched similar problems not finding the answer.
I have included  printouts from  "lsusb",  "fdisk" and "dmesg". Let me know if you need anything else.
Here they are: 

lsusb
```
jack@jack-OptiPlex-GX280:~$ lsusb
Bus 001 Device 006: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 004: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

fdisk 
```
jack@jack-OptiPlex-GX280:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cdc91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   152074239    76036096   83  Linux
/dev/sda2       152076286   156248063     2085889    5  Extended
/dev/sda5       152076288   156248063     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b523e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    78139391    39068672    b  W95 FAT32
jack@jack-OptiPlex-GX280:~$ 

```

dmesg
```
jack@jack-OptiPlex-GX280:~$ dmesg | tail -n 20
[  260.245810] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[  260.245815] usb 1-4: Product: USB to ATA/ATAPI Bridge
[  260.245819] usb 1-4: Manufacturer: JMicron
[  260.245822] usb 1-4: SerialNumber: 222048C51604
[  260.247982] usb-storage 1-4:1.0: USB Mass Storage device detected
[  260.248442] scsi5 : usb-storage 1-4:1.0
[  261.248945] scsi 5:0:0:0: Direct-Access     TOSHIBA  MK4026GAX        2D   PQ: 0 ANSI: 2 CCS
[  261.249334] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  261.249919] sd 5:0:0:0: [sdb] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[  261.250791] sd 5:0:0:0: [sdb] Write Protect is off
[  261.250797] sd 5:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  261.252553] sd 5:0:0:0: [sdb] Asking for cache data failed
[  261.252560] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  261.256218] sd 5:0:0:0: [sdb] Asking for cache data failed
[  261.256224] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  261.266978]  sdb: sdb1
[  261.270028] sd 5:0:0:0: [sdb] Asking for cache data failed
[  261.270036] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  261.270042] sd 5:0:0:0: [sdb] Attached SCSI disk
[  554.944892] systemd-hostnamed[3721]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
jack@jack-OptiPlex-GX280:~$ 
```

I really hope someone can help. And thank you in advance.
Jack

---

### Post by rdb3 on 2015-11-12
Do you have another pc you can test it on...... just to verify that it works?

---

### Post by yancek on 2015-11-12
Because it worked yesterday, doesn't mean it will work today.  Drives just fail and though often signs are seen when you have problems with a drive, sometimes they just fail.  The fact that fdisk and GParted see it is a good sign.  You are talking about the 40GB drive?  Does it show in the BIOS?  Were any changes made to your system just prior to this happening?

---

### Post by sudodus on 2015-11-13
Welcome to the Ubuntu Forums :-)

Like yancek wrote, if it is the 40 GB drive, fdisk and gparted see it, and it is good.

You can try to mount it manually via the command line (the partition sdb1)

```
sudo mount /dev/sdb1 /mnt
```

and then browse to **/mnt** with your file browser. Then you should be able to see your files in the directory tree under **/mnt**

Edit: Otherwise you might need to repair the file system. A FAT32 file system should be repaired by Windows.

```
format /f X:
```

or the corresponding GUI tool, where X: is the volume ID as seen by Windows.

---

### Post by Jack_Dickerson on 2015-11-13
Hi,
Thanks to you all, especially yancek and sudodus.  
Yancek- no I had not made any changes.
Sudodus-  sudo mount /dev/sdb1 /mnt returned "No such file or directory".   
As you said, the file system needed to be repaired.  I forget which diagnostic I ran- showed not properly unmounted, and a "dirty bit" set. 
So I ran: sudo dosfsck -t -a /dev/sdb1  to see if it would repair it and it did.  
(BTW, It stopped after the line "Auto-correcting it". I thought it was froze but I let it run, took around 30 minutes to do, but it worked).
Here are the results if it will help anyone else: [INDENT]:~$ sudo dosfsck -t -a /dev/sdb1
 fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
FSINFO sector has bad magic number(s):
  Offset 0: 0x43425355 != expected 0x41615252
  Offset 484: 0x00000000 != expected 0x61417272
  Offset 510: 0x0000 != expected 0xaa55
  Auto-correcting it.

Free cluster summary uninitialized (should be 422566)
  Auto-setting.
Performing changes.
/dev/sdb1: 15087 files, 798031/1220597 clusters
jack@jack-OptiPlex-GX280:~$ 
[/INDENT]

Then it detected perfectly. 
P.S. Now for sure I back-up everything.

---

### Post by sudodus on 2015-11-13
Congratulations :KS

Good luck with your backup routine, and thanks for sharing your solution :-)

---


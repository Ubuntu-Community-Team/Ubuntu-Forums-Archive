---
title: "USB external drive fails to mount after upgrade"
date: 2016-09-04
forum: New to Ubuntu
---

### Post by cardinal548 on 2016-09-04
Upgraded from 14.04 to 16.04 after which my external USB drive fails to mount. What commands are helpful in accessing the problem and how can I save the data?

---

### Post by TheFu on 2016-09-05
Did you try to mount the external disk using the '**mount**' command?  Sorry to ask, but it isn't clear from the post above.  Is the USB device seen by the kernel at all? Is there a device for it in /dev/?  Are there any messages related in the log files or **dmesg**?

---

### Post by cardinal548 on 2016-09-05
sdc is the problem drive
dmesg 

[   48.397325] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[   48.397331] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[   52.912587] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
 
I have tried to mount it but no mount point. Create mount point fail says it already is there.

what is mount command pls

---

### Post by TheFu on 2016-09-05
Those dmesg outputs look bad. Do you have a backup and another disk to restore onto?  

There are lots of different ways to mount storage. Need to know the device, UUID, Label, file system(s), partitions, and that the disk (or cable or controller) isn't failing.

Does [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) have commands that will help?

---

### Post by cardinal548 on 2016-09-05
The problem drive is sdc, I have some space on sdb that I could put most of it, if I am able to select what transfers and what does not.

```
jucick@Home:~$ sudo blkid
/dev/sda1: UUID="d2165b35-009f-454c-87c3-9587c62b6a9f" TYPE="ext4" PARTUUID="00049b98-01"
/dev/sda2: UUID="7b8eea06-fec0-4047-9e0c-7741be004718" TYPE="swap" PARTUUID="00049b98-02"
/dev/sda3: UUID="cde4346b-22e5-4b20-a236-dc100f48497d" TYPE="ext4" PARTUUID="00049b98-03"
/dev/sdb1: LABEL="Secondary" UUID="401183b3-1ff3-4dbc-8952-8668809dba36" TYPE="ext4" PARTUUID="3cf24fc8-d146-466a-a901-870d220b102b"
/dev/sdc1: UUID="2016-07-19-21-27-51-00" LABEL="Ubuntu 16.04.1 LTS amd64" TYPE="iso9660" PTUUID="40a863e7" PTTYPE="dos" PARTUUID="40a863e7-01"
/dev/sdc2: PARTUUID="40a863e7-02"

The Label is not the original, the "Ubuntu 16.04.1 LTS amd64" came after the upgrade. The original label was "ARK". As far as the file system I can't tell for certain, I don't know a command to get it. I was trying different commands days earlier and I believe it said FAT but I can't recall the command I used.
I'm sure the cable is good, it does show the drive in the launch bar. Controller is another thing I have no way to know how to check that.


jucick@Home:~$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0  37.3G  0 part /
&#9500;&#9472;sda2   8:2    0   4.7G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 181.7G  0 part /home
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/jucick/Secondary
sdc      8:32   0   2.7T  0 disk 
&#9500;&#9472;sdc1   8:33   0  11.3G  0 part 
&#9492;&#9472;sdc2   8:34   0  18.5M  0 part 

This is interesting

jucick@Home:~$ sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: present
  GPT: not present


*******************************************************************
This disk appears to contain an Apple-format (APM) partition table!
*******************************************************************


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdc: 732566646 sectors, 2.7 TiB
Logical sector size: 4096 bytes
Disk identifier (GUID): E1627DAF-5889-4132-A58E-A424B0FBC762
Partition table holds up to 128 entries
First usable sector is 6, last usable sector is 732566640
Partitions will be aligned on 16-sector boundaries
Total free space is 732561899 sectors (2.7 TiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2         2927216         2931951   18.5 MiB    EF00  EFI System
```

---

### Post by cardinal548 on 2016-09-05
Ah found it (I think)


```
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00049b98

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048  78125055  78123008  37.3G 83 Linux
/dev/sda2       78125056  87889919   9764864   4.7G 82 Linux swap / Solaris
/dev/sda3       87889920 468860927 380971008 181.7G 83 Linux


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DD6EE98C-D880-423C-B417-563BAE071901

Device     Start        End    Sectors   Size Type
/dev/sdb1     34 1953525134 1953525101 931.5G Linux filesystem

Partition 1 does not start on physical sector boundary.


Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 732566646 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x40a863e7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 2955679 2955680 11.3G  0 Empty
/dev/sdc2       2927216 2931951    4736 18.5M ef EFI (FAT-12/16/32)
```

---

### Post by cardinal548 on 2016-09-05
This is after disconnecting the drive and reconnecting it.```


[CODE][ 9802.143864] usb 2-1.8: new high-speed USB device number 6 using ehci-pci
[ 9802.298043] usb 2-1.8: New USB device found, idVendor=0480, idProduct=d000
[ 9802.298049] usb 2-1.8: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 9802.298052] usb 2-1.8: Product: External USB 3.0
[ 9802.298054] usb 2-1.8: Manufacturer: TOSHIBA
[ 9802.298056] usb 2-1.8: SerialNumber: 20140301015024
[ 9802.298512] usb-storage 2-1.8:1.0: USB Mass Storage device detected
[ 9802.298690] scsi host7: usb-storage 2-1.8:1.0
[ 9802.389172] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:5604:a6ff:febf:1b11 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=929830 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9802.389192] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:5604:a6ff:febf:1b11 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=647735 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9802.389207] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:94fb:ba27:539b:6ab3 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=6273 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9802.389221] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:94fb:ba27:539b:6ab3 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=288368 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9802.389234] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:fb73:fb21:24f7:388e DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=853003 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9802.389247] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:fb73:fb21:24f7:388e DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=386391 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9802.389261] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:6577:4c88:ced4:4920 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=188159 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9802.389275] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=fe80:0000:0000:0000:6577:4c88:ced4:4920 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=915612 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9802.399438] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:5604:a6ff:febf:1b11 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=929830 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[ 9802.399454] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=2601:0442:0101:0880:5604:a6ff:febf:1b11 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=647735 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[ 9803.297010] scsi 7:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0    PQ: 0 ANSI: 6
[ 9803.297583] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 9811.821317] sd 7:0:0:0: [sdc] 732566646 4096-byte logical blocks: (3.00 TB/2.73 TiB)
[ 9811.822440] sd 7:0:0:0: [sdc] Write Protect is off
[ 9811.822444] sd 7:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 9811.823567] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 9811.853501]  sdc: sdc1 sdc2
[ 9811.857193] sd 7:0:0:0: [sdc] Attached SCSI disk
[ 9813.061205] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[ 9813.061208] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
[ 9813.062699] grow_buffers: requested out-of-range block 18446744071562067968 for device sdc1
[ 9813.062702] isofs_fill_super: bread failed, dev=sdc1, iso_blknum=17, block=-2147483648
```

---

### Post by wildmanne39 on 2016-09-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by TheFu on 2016-09-07
WildMan - thanks for adding the code tags. Too hard to read otherwise. We are all volunteers, after all.

The way I'd try to solve this is to gather as much info as possible, then try to mount each partition. If I had backups, a new disk would have been swapped in and the backups restored already. For me, once a disk shows **any** issues, it is pulled from daily use and relegated to secondary use until it fails. All HDDs fail.

So ... looking over the data above, sdc appears to be about a 3TB disk with broken GPT formatting.  gdisk does have a history of altering disk partitions in a bad way back when it was first released. **gparted** and **parted** are the tools these says ... and if I need to clone GPT partition tables (just the table), then **sgdisk** is my tool of choice. 

What the data says. 
[LIST]
[*]sdc1 is formatted like a DVD would be, ISO9660. That is a read-only, optical, format. The contents are probably a copy of an Ubuntu DVD. Don't know why this would be here. It isn't something that happens through any installer I know. Very much a manual thing happened. Know idea why it is label'd that way either. I've never seen that.
[*]sdc2 is formatted FAT - looks like a UEFI partition. That is used for booting.
[*] The rest of the disk is unknown. Nothing to mount. Recovery of that data will be non-trivial, if it is even possible.
[/LIST]

What is the partition history for this disk? Do you remember having just a few, relatively small, partitions on it?  What was on most of the 3TB disk? OS, apps, data, games, media?

First, before anything else, try using a different interface to access the storage - USB or SATA. Try a different USB plug and port.  It might just be the USB controller, not the disk at all. If not, assume the data is gone and hope we can get some of it back. It will be painful, long, manual, process on a disk that size even if it is only 10% full.

Recovery attempt ... 
There is a suite of tools called "[testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")."  Before starting with it, make a bit-for-bit clone of the bad disk and only work on the new storage. Use **ddrescue** to clone it. ddrescue is like dd, but tries very hard to get all the bits by retrying over and over and over. Plus the cmd doesn't just stop when an error happens, like dd does.  Be very careful with dd/ddrescue tools. They do what you say, not necessarily what you intend/mean.  **Don't get the parameters backwards, that could leave 2 empty disks.** The target disk must be at least as large as the source disk.  Plus if everything does work as we hope, you'll have some backup storage (the old disk) for future needs. I've only used testdisk for play stuff, once, a few years ago. It was impressive what it could restore. The manpage for ddrescue is pretty easy to understand. Be sure to review it.

Try USB first for the recovery stuff. If it mostly works, great! Otherwise use eSATA or SATA connections.  The commands supported by SATA have more control than simple USB storage access commands. When it comes to data recovery, this can be important. 

Anyway, hope this isn't confusing and can be of some small help. Wish there was better news.

---


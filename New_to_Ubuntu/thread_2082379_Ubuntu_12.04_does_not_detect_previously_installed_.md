---
title: "Ubuntu 12.04 does not detect previously installed XP"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by maruf7 on 2012-11-09
Hello,
I've been trying to install Ubuntu 12.4 in my pc where Windows XP installed earlier. But after booting from live cd and starting installation wizard, Ubuntu neither recognizes existing XP (message like shown: No Previously installed os detected in your computer...) nor my 60 gigabyte unpartitioned space is shown in the partitioning window. Please help with this issue. 

Thanks
Maruf

---

### Post by newb85 on 2012-11-09
First, welcome to the forums and Ubuntu.

Determining the reason XP isn't recognized will require some investigation outside the install wizard (i.e., the "Try Ubuntu" option).

Once you're in a live session, open a terminal (Ctrl+Alt+T) and run the following two commands, copying and pasting their results into a new post surrounded by code tags.

```
sudo lshw -C disk
sudo lshw -C volume
```

Code tags like this
[noparse]```
Results
Here
```[/noparse]

---

### Post by maruf7 on 2012-11-09
new85-thanks for yor response. Following are the results:

[sudo lshw –C disk]
```
*-disk
description: ATA Disk
product: Hitachi HDS72105
vendor: Hitachi
physical id: 0.0.0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: JP2O
serial: JP8521HR27GGKV
size: 465GiB (500GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=5806c6ed
*-cdrom
description: DVD-RAM writer
product: CDDVDW SH-222AB
vendor: TSSTcorp
physical id: 0.0.0
bus info: scsi@3:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/sr0
logical name: /cdrom
version: SB01
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted
status=ready
*-medium
physical id: 0
logical name: /dev/cdrom
logical name: /cdrom
capabilities: partitioned partitioned:dos
configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=66b94095
state=mounted
[/sudo lshw –C disk]
```


[sudo lshw -C volume]
```
*-volume:0
description: Windows NTFS volume
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
version: 3.1
serial: 406fcd74-9f52-984d-b0d0-10809a0bb380
size: 49GiB
capacity: 49GiB
capabilities: primary bootable ntfs initialized
configuration: clustersize=4096 created=2011-08-17 14:02:45 filesystem=ntfs label=XP
state=clean
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
size: 415GiB
capacity: 415GiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume:0
description: HPFS/NTFS partition
physical id: 5
logical name: /dev/sda5
logical name: /media/New Volume
capacity: 48GiB
configuration: mount.fstype=fuseblk
mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,bl
ksize=4096 state=mounted
*-logicalvolume:1
description: HPFS/NTFS partition
physical id: 6
logical name: /dev/sda6
capacity: 99GiB
*-logicalvolume:2
description: HPFS/NTFS partition
physical id: 7
logical name: /dev/sda7
capacity: 99GiB
*-logicalvolume:3
description: HPFS/NTFS partition
physical id: 8
logical name: /dev/sda8
capacity: 100GiB
*-volume:2
description: Windows NTFS volume
physical id: 3
bus info: scsi@0:0.0.0,3
logical name: /dev/sda3
version: 3.1
serial: fc9c1c3e-5ca4-7940-bb9c-1898d63720ab
size: 64GiB
capacity: 64GiB
capabilities: primary ntfs initialized
configuration: clustersize=4096 created=2011-08-11 09:14:36 filesystem=ntfs label=Local Disk
state=clean
*-volume UNCLAIMED
description: Hidden HPFS/NTFS partition
physical id: 1
capacity: 701MiB
capabilities: primary bootable hidden
[/sudo lshw –C volume]
```

---

### Post by newb85 on 2012-11-09
Formatting: Sorry I didn't make this clear enough.  [noparse]```
 and 
```[/noparse] are formatting tags.  You shouldn't replace the word *CODE* with anything.

The unallocated space you're looking for is within the Extended partition.  (Extended partitions are basically containers for more partitions.)  If you select the "Something Else" install option, you can select the Extended partition and add another partition within it.

---

### Post by oldfred on 2012-11-09
Added code tags.

I have had gparted not even show my entire sda drive when chkdsk was required. My XP booted, but once I ran chkdsk then gparted showed sda. I think now the NTFS driver or gparted will show NTFS partition but show a little icon for warning that there is some issue with the partition. If you click on icon it tells you what the issue may be.

Post screenshot from gparted.

---

### Post by maruf7 on 2012-11-09
Thank you neb85 & oldfred.
As I selected 'Something Else' installation option, /dev/sda was showing under device. The following options were also displayed:
New Partition Table, Add, Change, Delete,Revert.

But only 'New Partition Table' and 'Revert' were usable, others were disabled. Now which should I select to proceed the installation in a new partition without messing the existing NTFS partitions?

---

### Post by oldfred on 2012-11-09
If you go into Ubuntu liveCD's live mode and open gparted what does it show?

And have you tried chkdsk on our Windows partition from an XP disk?

---

### Post by maruf7 on 2012-11-10
Well I can't run gparted from live mode because it says 'I don't have privilige', but after running chkdsk and booting from Ubuntu CD, XP is detected by Ubuntu and ''Install Ubuntu alongside XP' is available and now I'm able to install Ubuntu. Thanks a lot newb85 and oldfred for your sincere help.

---

### Post by Calinou on 2012-11-10
You can run gparted with this command in a terminal:
```
sudo gparted
```

---


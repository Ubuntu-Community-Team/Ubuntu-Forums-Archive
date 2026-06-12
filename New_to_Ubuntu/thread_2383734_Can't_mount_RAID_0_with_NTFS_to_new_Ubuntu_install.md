---
title: "Can't mount RAID 0 with NTFS to new Ubuntu install"
date: 2018-01-29
forum: New to Ubuntu
---

### Post by benh0882 on 2018-01-29
Hey guys,

I have a server that has Windows 10 installed on an SSD and all of my movies etc. are on a separate two-hard drive 4TB RAID 0. I shrank the Windows 10 NTFS partitions and installed Ubuntu 16.04.3 LTS on my newly acquired free space. I've been having a hard time trying to mount my RAID drive in Ubuntu.

I tried to mount my RAID using "sudo mount -t ntfs-3g /dev/mapper/pdc_chbiehecf", but I'm getting the following error:

Failed to mount '/dev/mapper/pdc_chbiehecf': Invalid argument
The device '/dev/mapper/pdc_chbiehecf' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

This hard drive is working perfectly in Windows 10. I ran chkdsk just in case. Any ideas as to what I can do to get this hard drive mounted?

Thanks for any help!

---

### Post by TheFu on 2018-01-29
"Any ideas?"

How was the RAID setup?  Is it a Windows thing?  A motherboard thing?

In Linux, RAID is one of these types:
* HW-RAID - the card does all the work and specific drivers are required. Seldom do the drivers work the same between Windows and Linux. These are fast, but tied to the specific release of the card, which makes it highly recommended that 2 cards be purchased.
* Fake-RAID - Motherboard RAID.  This ties you to the MB and it is slow.
* SW-RAID - Linux used mdadm to manage SW RAID.  On a modern system, it is fast, convenient, and flexible.

There are other sorts of SW-RAID in Linux too - ZFS, LVM both have modes.  I've not used them on Linux.

So, the first question stands. What sort of RAID-0 is being used?  Is this compatible with Linux?

Welcome to the forums.

---

### Post by oldfred on 2018-01-29
Is Windows fast start up which is just hibernation off?

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 


 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04 and later.

---

### Post by tps-mail on 2018-01-29
from a command prompt, try

```
sfdisk -l [COLOR=#000000]/dev/mapper/pdc_chbiehecf
```


and see what it tells you.

[/COLOR]

---

### Post by benh0882 on 2018-01-30
> **tps-mail said:**
> from a command prompt, try

```
sfdisk -l [COLOR=#000000]/dev/mapper/pdc_chbiehecf[/COLOR]
```[COLOR=#000000]


and see what it tells you.

[/COLOR]

Here's the output I get:

Disk /dev/mapper/pdc_chbiehecf: 1.7 TiB, 1800976728064 bytes, 3517532672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device                          Boot Start        End    Sectors Size Id Type
/dev/mapper/pdc_chbiehecf-part1          1 4294967295 4294967295   2T ee GPT


Partition 1 does not start on physical sector boundary.

---

### Post by benh0882 on 2018-01-30
> **TheFu said:**
> "Any ideas?"

How was the RAID setup?  Is it a Windows thing?  A motherboard thing?

In Linux, RAID is one of these types:
* HW-RAID - the card does all the work and specific drivers are required. Seldom do the drivers work the same between Windows and Linux. These are fast, but tied to the specific release of the card, which makes it highly recommended that 2 cards be purchased.
* Fake-RAID - Motherboard RAID.  This ties you to the MB and it is slow.
* SW-RAID - Linux used mdadm to manage SW RAID.  On a modern system, it is fast, convenient, and flexible.

There are other sorts of SW-RAID in Linux too - ZFS, LVM both have modes.  I've not used them on Linux.

So, the first question stands. What sort of RAID-0 is being used?  Is this compatible with Linux?

Welcome to the forums.

The RAID was set-up with my MSI motherboard's BIOS. I guess that makes it a Fake-RAID. I actually meant to include it in my original post. Thank you for the information though, very informative!

---

### Post by benh0882 on 2018-01-30
Guys, some additional information. I just ran a blkid command. The two members of my fake-RAID are /dev/sdb and /dev/sdc. It says they're "promise_fasttrack_raid_member". I also see /dev/mapper/pdc_chbiehecf listed as "PMBR".

---

### Post by tps-mail on 2018-01-30
I believe that  [COLOR=#000000]/dev/mapper/pdc_chbiehecf-part1 is what you should be trying to mount... the partition, not the device[/COLOR]

---


---
title: "Mounting a new 3TB HDD in 12.04 Server"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by chris193 on 2014-03-17
Hello!

Complete noob here, I apologise in advance. I'm running Ubuntu 12.04 on an old dell PC with 2 HDDs, one 80GB with the OS on and a second 3TB I'm trying to mount. This will be used primarily as a file sharer for Windows PCs. 

I've been following a few tutorials and I don't seem to be getting far. I've formatted the 3TB HDD (I have no intentions of putting anything else on the 80GB other than the OS) in Windows as GPT NTFS then put it in the server. 

I've tried following the basic tutorial, but since putting it in windows to partition it, it appears I need to use 'GNU Parted' I tried following [this]("http://microdevsys.com/wp/linux-unix-adding-a-new-sata-harddrive-using-parted-instead-of-fdisk/"), without step 3 and 4, as I thought I'd already partitioned it. For step 5 I was told i needed to specify file type (presumably NTFS) I'd appreciate any links to tutorials or suggestions, Cheers, Chris.

fdisk -l gives me this:

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00051fda


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156248063    77873153    5  Extended
/dev/sda5          501760   156248063    77873152   83  Linux


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x041a2d94


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/mapper/sda5_crypt: 79.7 GB, 79740010496 bytes
255 heads, 63 sectors/track, 9694 cylinders, total 155742208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table


Disk /dev/mapper/EMU--Events--vg-root: 48.7 GB, 48658120704 bytes
255 heads, 63 sectors/track, 5915 cylinders, total 95035392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/EMU--Events--vg-root doesn't contain a valid partition table


Disk /dev/mapper/EMU--Events--vg-swap_1: 1337 MB, 1337982976 bytes
255 heads, 63 sectors/track, 162 cylinders, total 2613248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/EMU--Events--vg-swap_1 doesn't contain a valid partition table


Disk /dev/mapper/cryptswap1: 1337 MB, 1337982976 bytes
255 heads, 63 sectors/track, 162 cylinders, total 2613248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8878a68c


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
```

---

### Post by TheFu on 2014-03-17
Don't use fdisk on HDDs over 2TB in size or if GPT formating is used. Use **parted** or **gparted** always.

Please post the output of **sudo parted -l** and **sudo blkid**.

Mounting guide: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)
Ubuntu samba guide. [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

BTW, you should be using ext4, not NTFS for this data drive - probably,
If you get stuck making samba permissions work the way you need, please run **testparm** and post the output.

**Consistent Help/Guides:**
It is important to get consistent help/guidance from trusted sources, not random blogs. Often, the random blog post gets made by someone who just got X working for the first time as a way to remind that person of their steps.  Sometimes they do not have a complete understanding of what they did or which parts were necessary. I did NOT look at the blog link you provided in detail, so this isn't saying anything about it. I did skim it and saw a few things that did not follow best practices, however. I always start by looking for official ubuntu guides, then move to the partnered ubuntu websites and forums. There are many how-tos available in those, which describe things in the most straight forward way, not for a specific need.

Good luck.

---

### Post by JKyleOKC on 2014-03-17
> **TheFu said:**
> BTW, you should be using ext4, not NTFS for this data drive - probably.I disagree **strongly** with this suggestion, since the OP said he intends to use the 3 TB drive primarily for exchanging files with Windows. Out-of-the-box Windows systems don't recognize ext4 partitions **at all**, although third-party drivers for them that **DO** recognize ext4 are available. I used one of those drivers on an XP installation to restore backups from an external disk that was EXT4; I don't know if any such driver is yet available for Win8 or later...

---

### Post by TheFu on 2014-03-17
> **JKyleOKC said:**
> I disagree **strongly** with this suggestion, since the OP said he intends to use the 3 TB drive primarily for exchanging files with Windows. Out-of-the-box Windows systems don't recognize ext4 partitions **at all**, although third-party drivers for them that **DO** recognize ext4 are available. I used one of those drivers on an XP installation to restore backups from an external disk that was EXT4; I don't know if any such driver is yet available for Win8 or later...

I think we are coming at the question from 2 different views.
a) Permanently mounted inside a Linux Samba server - EXT4.
b) Temporarily mounted to either Linux or Windows machines - NTFS.

The OP did not say which was planned.

If the drive will be physically moved between the systems, then NTFS **is** the better choice.  If not, then EXT4 is definitely what OP needs.

---

### Post by JKyleOKC on 2014-03-18
With that explanation I agree fully. The Samba server will take care of making the data available to Windows users, so long as the files are dealt with only through that server. Thanks for the clarification!

---


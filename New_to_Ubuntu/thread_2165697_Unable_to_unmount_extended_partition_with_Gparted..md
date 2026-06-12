---
title: "Unable to unmount extended partition with Gparted."
date: 2013-08-05
forum: New to Ubuntu
---

### Post by Telephonoscope on 2013-08-05
Hello, I've been working on this issue most of the day but I just don't know enough about Ubuntu/Linux as I only installed it a few days ago. I've read many posts in the forums with similar issues and done Google searches ... close, but no cigar.

[ATTACH=CONFIG]245113[/ATTACH]

As you can see I have several partitions. Part of that is because I installed Uberstudent through a live disk that I created but then switched to Ubuntu 13.04 x64 which I also installed through a live disk I created - that then popped up with wubi. When installing Ubuntu I decided to just shrink the Uberstudent partition until I had more time to get rid of it because I was informed it wasn't the easiest process. These actions were approved by my friend who is sorta-kinda teaching me how to use Ubuntu. He's been trying to help me figure this out throughout the day and he's stumped.

When I try to delete sda5
[ATTACH=CONFIG]245114[/ATTACH]

When I try to unmount sda4 the unmount option is grayed out.


Currently I'm booted into 13.04 from the same live disk I used to install two or three days ago. My end goal is to delete sda5 and expand sda4/sda7 into my unallocated space.

sda4 is shown as mounted in Gparted, but is not mounted according to the terminal.
```
root@ubuntu:~# umount /dev/sda4
umount: /dev/sda4: not mounted
root@ubuntu:~# umount -f /dev/sda4
umount2: Invalid argument
umount: /dev/sda4: not mounted
```

Don't know if this is important but I saw it asked for a lot.
```
root@ubuntu:~# fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffa8d7ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   121313279    60553216    7  HPFS/NTFS/exFAT
/dev/sda3       951980032   976771071    12395520    7  HPFS/NTFS/exFAT
/dev/sda4       455499774   951980031   248240129    5  Extended
/dev/sda5       515330048   548962303    16816128   83  Linux
/dev/sda6       935731200   951980031     8124416   82  Linux swap / Solaris
/dev/sda7       455499776   515330047    29915136   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 999.7 GB, 999732936704 bytes
255 heads, 63 sectors/track, 121543 cylinders, total 1952603392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fb76df6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1952588294   976294116    c  W95 FAT32 (LBA)

Disk /dev/sdc: 4072 MB, 4072669184 bytes
53 heads, 52 sectors/track, 2886 cylinders, total 7954432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8192     7954431     3973120    b  W95 FAT32

```

Thought I'd get the UUID of the partition so I could maybe do something through fstab. sd4 isn't listed?
```
root@ubuntu:~# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="36164E8A164E4B57" TYPE="ntfs" 
/dev/sda2: LABEL="OS" UUID="36D64FB6D64F74E1" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="F48081B380817D3C" TYPE="ntfs" 
/dev/sda5: UUID="e61c01a3-0569-46bc-90e7-ebda10a7090d" TYPE="ext4" LABEL="Uberstudent" 
/dev/sda6: UUID="bd618173-0e95-433e-85e2-d1409a127ef4" TYPE="swap" 
/dev/sda7: UUID="afe74fa5-c67f-4a7c-a632-2d6555f3a0aa" TYPE="ext4" LABEL="Ubuntu" 
/dev/sr0: LABEL="Ubuntu 13.04 amd64" TYPE="iso9660" 
/dev/sdb1: LABEL="LIFESTUDIO" UUID="1A08-1C58" TYPE="vfat" 
/dev/sdc1: LABEL="MYKEY" UUID="5D18-F276" TYPE="vfat" 

```

It's not in fstab either
```
root@ubuntu:~# cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

```

Thank you, and if I need to expand my Windows partitions for some reason please let me know. I save almost everything to my external harddrive except for programs.

---

### Post by deadflowr on 2013-08-05
Not sure, but I think you need to turn swap off.
Right click on the linux-swap partition and find swapoff(swapon?)
See what that does.

---

### Post by fantab on 2013-08-05
What happens when UNMOUNT partitions, /dev/sda6 and /dev/sda7? Since one partition has Ubuntu and other is SWAP, Gparted should be used with from Ubuntu Live DVD/USB.
You CANNOT unmount the Extended Partition (It just serves as container for Logical Partitions) without unmounting all the Logical Partitions 'contained' in it. So before deleting /dev/sda5, you have to unmount /dev/sda6 and /dev/sda7. From Ubuntu Live DVD/USB use the utility called 'DISKS' to double check if sda6 and sda7 are unmounted. AFAIK they are not mounted by default. /dev/sda6 is the SWAP partition, using Gparted right click on the Swap partitions and select 'Swapoff', then perhaps you can unmount it.

Always BACK UP your Important DATA before you fiddle with any Disk or Partition manager.

Post the output of:
```
sudo parted -l
```

---

### Post by Telephonoscope on 2013-08-06
Turning swap off worked. I was able to delete the Uberstudent partition. Now I'm having difficulties expanding into the unallocated space, but I think I'll do some research on my own before I ask for any information. Thanks for your help!

---

### Post by carl4926 on 2013-08-06
FYI and future ref
The extended partition is just a container for logical partitions
Ask what you need and supply a screen of what you now have... and we can advise

---

### Post by Telephonoscope on 2013-08-06
Turning swap off fixed the problem I had, but I'm going to go ahead and run the code just in case anything shows up that I need to fix. Thanks!

```
root@ubuntu:~# parted -l
Model: ATA WDC WD5000AAKS-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   62.1GB  62.0GB  primary   ntfs
 4      233GB   487GB   254GB   extended
 6      233GB   264GB   30.6GB  logical   ext4
 5      479GB   487GB   8319MB  logical   linux-swap(v1)
 3      487GB   500GB   12.7GB  primary   ntfs


Model: Hitachi HDS721010CLA332 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  fat32        lba


Model: Generic STORAGE DEVICE (scsi)
Disk /dev/sdc: 4073MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  4073MB  4068MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!        

```

---

### Post by BlinkinCat on 2013-08-06
Hi,

Here's how to mark your thread as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :p


Sorry if I posted this too soon!

---

### Post by oldfred on 2013-08-06
If the issue is your first unallocated you may have to expand extended partition left to include that unallocated space. Or you can create unallocated as a partition and move /home into it. Or make it a data partition and mount that and link folders into /home to in effect make /home larger.

But you may have made Windows a bit small. Windows works best with 30% free, and it looks like you left about 20%. If Windows gets down to 10% free it just about becomes unusably slow. Or houseclean more old files out of Windows.

---

### Post by Telephonoscope on 2013-08-06
> Ask what you need and supply a screen of what you now have... and we can advise

Here you go. I wasn't sure if I should continue in this thread since it's a new question in a way.

[ATTACH=CONFIG]245117[/ATTACH]
[ATTACH=CONFIG]245118[/ATTACH]
[ATTACH=CONFIG]245119[/ATTACH]

```
GParted 0.12.1 --enable-libparted-dmraid
 Libparted 2.3
  [TABLE]
[TR]
[TD="colspan: 2"] **Move /dev/sda4 to the left and grow it from 236.74 GiB to 390.55 GiB**  00:00:01    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sda4  00:00:01    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sda4
start: 455,499,774
end: 951,980,031
size: 496,480,258 (236.74 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] move partition to the left and grow it from 236.74 GiB to 390.55 GiB  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 455,499,774
old end: 951,980,031
old size: 496,480,258 (236.74 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]requested start: 132,941,824
requested end: 951,977,983
requested size: 819,036,160 (390.55 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *Unable to satisfy all constraints on the partition.*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

---

### Post by fantab on 2013-08-06
Instead of merging the 'unallocated space' you can create a new partition from the space and format it with EXT4 and use it as a simple linux partition where you can save your personal data. 

If I am correct the 'unallocated space' is after the SWAP partition, (if this is true) then it won't be easy for you to merge the space with /dev/sda5. You may have to delete the SWAP as well and then merge the space with /dev/sda5 and recreate the SWAP partition. If this works then you will have to edit /etc/fstab and change the UUID of SWAP partition to reflect the present UUID.

If I were you I would just create a new partition from the 'unallocated space' and use it to save the data partition. You can choose to later either automount it with Ubuntu start or do it manually whenever you need to mount it from the 'file browser', Nautilus.

---

### Post by Telephonoscope on 2013-08-06
I really appreciate all of the helpful suggestions I got on my post. Early this morning in a fit of pique I took the plunge and installed Uuntu on the entirety of my hard drive. I'm going to mark this thread as solved since I can't get any more help out of it.

---


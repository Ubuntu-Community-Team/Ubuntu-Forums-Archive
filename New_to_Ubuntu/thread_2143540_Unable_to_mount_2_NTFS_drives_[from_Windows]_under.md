---
title: "Unable to mount 2 NTFS drives [from Windows] under Ubuntu 13.04"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by dejavue on 2013-05-09
Hi guys,

this is my first post here and I consider myself an Ubuntu noob. I could not find anything similar to my problem really, so I hope I am not double-posting this.

I am currently trying to slowly move away from using Windows (7) towards using Ubuntu as my main OS (the only thing stopping me from uninstalling Windows altogether is that I am gaming and WINE is not as good as native support on Windows).

However I want to go there and for that I also need my drives to be shared to my WDTV Live Streaming (3rd Gen.) for watching movies that are on my HDD(s) via network share.
However, I am stumped early on, because I cannot even mount two of the main drives that contain video files on my PC 

[ATTACH=CONFIG]242377[/ATTACH][ATTACH=CONFIG]242378[/ATTACH]

These are the two error messages I am getting when trying to mount the two drives. And since I am a linux newbie, I don't really get the supposed solutions when I simply enter these error messages into google. As I don't want to nuke my system right away, I thought I might ask you nice guys first :) 

Additional info: These drives are internal storage drives (SATA) that have been set up and formatted under Windows 7 x64 Ultimate Edition using NTFS (--> Windows Disk Management, no 3rd party tool used).

I hope you can help me (this problem is probably really easy to solve and I am just too stupid to do so on my own).


Greetz,
dejavue

---

### Post by dino99 on 2013-05-09
as your screenshots errors asked: are those drives "single" or used as "raid" ? If the raid is used, it seems having trouble.

boot with windows and check for hdd errors (with the formatting tool); clean your install (chkdsk or like) and also defrag.

then test again to know if the previous errors still exist.

---

### Post by oldfred on 2013-05-09
+1 on dino99's suggestions.

Post this from your Ubuntu install.

sudo parted -l
sudo fdisk -lu

---

### Post by dejavue on 2013-05-09
First of all, no there is no raid. However, I found this:
[ATTACH=CONFIG]242392[/ATTACH]
The partitions that are giving me trouble are inexplicably split for no apparent reason (I am 100% sure that I have never resized these partitions or done anything to them but simply set them up in the beginning).
When I do chkdsk /R it starts at 10% of files processed and gives me no estimate as to how long it will take to finish, but by the time it took to reach 11% (2 hours at least) I would still wait for that a month later.

Result from sudo parted -l:

> Model: ATA OCZ-VERTEX3 (scsi)Disk /dev/sda: 60,0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   60,0GB  59,9GB  primary  ntfs




Model: ATA OCZ-VERTEX3 MI (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type     File system  Flags
 1      1049kB  180GB  180GB   primary  ntfs
 2      180GB   240GB  60,0GB  primary  ext4




Model: ATA SAMSUNG HD502IJ (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type     File system  Flags
 1      32,3kB  500GB  500GB  primary




Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdd: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32,3kB  10,7GB  10,7GB  primary  ntfs
 2      10,7GB  118GB   107GB   primary  ntfs         boot
 3      118GB   500GB   382GB   primary  ntfs




Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32,3kB  1000GB  1000GB  primary  ntfs

sudo fdisk -lu result:
> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0cbda773


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   117227519    58510336    7  HPFS/NTFS/exFAT


Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3e289cfe


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   351670016   175833984+   7  HPFS/NTFS/exFAT
/dev/sdb2       351670272   468860927    58595328   83  Linux


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b60d902


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976771119   488385528+  42  SFS


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfca7fca7


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63    20964824    10482381   42  SFS
/dev/sdd2   *    20964825   230677334   104856255   42  SFS
/dev/sdd3       230677335   976771119   373046892+  42  SFS


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf9905369


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953523119   976761528+  42  SFS


Hope this helps

---

### Post by Cheesemill on 2013-05-09
Unfortunately I don't think you are going to be able to mount those drives using Ubuntu in their current state. As you can see from your screenshot Windows has converted them into dynamic drives, this is a proprietary Microsoft technology which can't be read by Linux systems. It is possible to convert them back into basic drives, but like any partitioning operation you should make sure you have a full backup before attempting it in case anything goes wrong. I've never done this myself but a quick Google led me to this page...

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by dejavue on 2013-05-09
> **Cheesemill said:**
> Unfortunately I don't think you are going to be able to mount those drives using Ubuntu in their current state. As you can see from your screenshot Windows has converted them into dynamic drives, this is a proprietary Microsoft technology which can't be read by Linux systems. It is possible to convert them back into basic drives, but like any partitioning operation you should make sure you have a full backup before attempting it in case anything goes wrong. I've never done this myself but a quick Google led me to this page...

[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)


Thank you Cheesemill for your quick answer.
That is too bad, because as you may tell, I don't have near enough free space to backup all those files.
Maybe I'll save up for a rather big (>3TB) external drive and save all to that (then I can just plug that into the WD TV Live directly) and then completely reformat using windows.

Thank you all for your very quick help. 

Best regards,
dejavue

---

### Post by oldfred on 2013-05-09
If you get a 3TB drive do not format with Windows.

Several users have just formatted drives without partitioning creating huge issues,  and some have used Windows and not gotten correct gpt structures. 
A 3TB drive must be gpt not MBR(msdos). You can use gparted for gdisk from most Linux live disks to partition and format.

---

### Post by dejavue on 2013-05-10
> **oldfred said:**
> If you get a 3TB drive do not format with Windows.

Several users have just formatted drives without partitioning creating huge issues,  and some have used Windows and not gotten correct gpt structures. 
A 3TB drive must be gpt not MBR(msdos). You can use gparted for gdisk from most Linux live disks to partition and format.


Thanks for the advice, I was not going to do this now anyway (gotta take something away from this whole experience, right? ;))

---


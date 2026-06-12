---
title: "Partitioning, dual boot"
date: 2014-01-19
forum: New to Ubuntu
---

### Post by sooraj2 on 2014-01-19
i tried to install ubuntu 13.10 ie i tried for dual boot with my win 7 but could not

i hav 2 hdds
1 80 gb
2 250 g 

i hav partitioned them in such a way that nw i  hav 5 local disc 
1 localdisc C - 74gb 
2 local disc E - 48gb
3 localdisc F - 48gb
4 localdisc G - 48gb
5 localdisc H - 86gb (full empty kept for ubuntu)

then i deleted the partition 86gb and it showed unallocated space then boot into live usb i tried to 
see if ter was any partition i can select but there aren't any i saw this 
only this 
[IMG]https://drive.google.com/file/d/0B1WuJuN7p2ihQ29vMzV3V05ja0E/edit?usp=sharing[/IMG]
and this
[IMG]https://drive.google.com/file/d/0B1WuJuN7p2ihZVBxR2R2c3NDTUk/edit?usp=sharing[/IMG]

i dont see my 86 gb  unallocated space 
then i tried this [IMG]https://drive.google.com/file/d/0B1WuJuN7p2ihZHJyMXlqOFhscVU/edit?usp=sharing[/IMG]
then this [IMG]https://drive.google.com/file/d/0B1WuJuN7p2iha0ZwbXk1cXM2SzA/edit?usp=sharing[/IMG]

pls help me

---

### Post by Bashing-om on 2014-01-19
sooraj2; Hi !

We are here to help !
Your imaging did not take, however, as we prefer to look at things from ubuntu's point of view;
Boot the InstallMedium -> try ubuntu and activate a terminal:
Post back the out puts of terminal codes: -between code tags -
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
"fdisk" is applicable to the leagacy partitioning schemes, else use "gdisk" to see GPT partitioning.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-01-19
> **Bashing-om said:**
> sooraj2; Hi !

We are here to help !
Your imaging did not take, however, as we prefer to look at things from ubuntu's point of view;
Boot the InstallMedium -> try ubuntu and activate a terminal:
Post back the out puts of terminal codes: -between code tags -
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
"fdisk" is applicable to the leagacy partitioning schemes, else use "gdisk" to see GPT partitioning.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[INDENT][INDENT]a tale will be told
[/INDENT]
[/INDENT]


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcc29cc29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   156299263    78148608    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8d5afae6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488395119   244197528+  42  SFS

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a9da53a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 



```


```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST380211AS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  80.0GB  80.0GB  primary  ntfs         boot


Model: ATA ST3250318AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary


Model: SanDisk Cruzer Pop (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ 


```

```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST380211AS (scsi)
Disk /dev/sda: 156301488s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      2048s  156299263s  156297216s  primary  ntfs         boot

ubuntu@ubuntu:~$ 


```

```

ubuntu@ubuntu:~$ lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9492;&#9472;sda1              
sdb                 
&#9500;&#9472;sdb1              
&#9500;&#9472;sdb2              
&#9500;&#9472;sdb3              
&#9500;&#9472;sdb4              
&#9492;&#9472;sdb5              
sdc                 
&#9492;&#9472;sdc1              /cdrom
sr0                 
loop0               /rofs
loop1               
ubuntu@ubuntu:~$ lsblk -f


```

and this time i used mini partition tool to partion my 86gb to fat32 stiill wont wrk :(

---

### Post by Bashing-om on 2014-01-19
sooraj2; Not good for the home team.

> 
/dev/sda1   *        2048   156299263    78148608    7  HPFS/NTFS/exFAT

Houston, we have a problem.
The formatting on the hard disk is HPFS, that is proprietary to Windows. Ubuntu will not touch it.

There is a means to convert HPFS back to basic, and that process is risky to data loss to the extreme.
That process is above my pay grade, others will have to advise as  Window's is not my thing.

The good thing is ->
[INDENT][INDENT][INDENT]there are solutions
[/INDENT][/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-01-19
> **Bashing-om said:**
> sooraj2; Not good for the home team.


Houston, we have a problem.
The formatting on the hard disk is HPFS, that is proprietary to Windows. Ubuntu will not touch it.

There is a means to convert HPFS back to basic, and that process is risky to data loss to the extreme.
That process is above my pay grade, others will have to advise as  Window's is not my thing.

The good thing is ->[INDENT][INDENT][INDENT]there are solutions
[/INDENT]
[/INDENT]
[/INDENT]

wow tats a very quick reply 
ok Bashing-om i really dont ant to loose my data so is ter any way without loosing data

---

### Post by sooraj2 on 2014-01-19
ok ill revert back to ntfs then ...........?????
wat to do

---

### Post by Bashing-om on 2014-01-19
sooraj2; Hey !

I wish it were that simple. Like I say that formatting will have to be changed to "basic" . It is doable and I think I have seen the procedure to do so on this forum.
May I suggest ya search this forum for Mark Phelps and/or grahammechanical -they are the gurus - for their threads in this respect.
Else; await others to pick up this thread and offer much better advise.

I am totally not qualified to assist you in this matter.

[INDENT][INDENT]some things I just do not want to know
[/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-01-19
ok
but is ter any way i can change my partition from ntfs to ext4
if yes can u pls tell me ???? if its done will it detect in ubuntu ???

---

### Post by Bashing-om on 2014-01-19
sooraj2; Well,

What might be a viable solution is to back up the files on sdb (2nd hard drive), and install ubuntu onto that 2nd hard drive.
SFS == A shared-disk filesystem, I would not expect any difficulties in reformatting the drive, but if it is a shared drive, a lot of reconfiguration would be in the prospect.
In addition, One would have to pay close attention to how/where Windows is booting and how you would want to boot the respective operating systems.

If you so choose to install ubuntu onto the 2nd hard drive would not effect Window's in the least - if you are happy to select the 2nd drive at boot (bios), will not even have to touch Window's boot code. Just Make double sure that grub (ubuntu's boot loader code) is installed onto the 2nd hard drive's Master Boot Record sector.

The safe way to insure all this takes place correctly is just to remove the drive that Windows is installed on.

There are options and
[INDENT][INDENT][INDENT]the choosing is yours
[/INDENT][/INDENT][/INDENT]

---

### Post by sooraj2 on 2014-01-19
but i dont wand to loose my data on 2nd hdd 250gb  i hav a lot o imp personal info in it
and i hav made a local disc seperately for installing ubuntu but i thing ter is no way i can get ubuntu in my second hdd 86 gb partition

---

### Post by Bashing-om on 2014-01-19
sooraj2;
Then like I have repeatedly advised, if you are to install ubuntu onto that 1st hard drive (sda) you must reformat it away from Window's proprietary format HPFS, Any Time one reformats in any environment all data on that disk is lost, there is a "risky" means to change that HPFS format back to basic - and perhaps retain all the data -, But I am not going there as I am not qualified in that respect to advise you.

Search the forum for others advise in your similar situation.

(Purchase a 3rd Hard drive and install ubuntu onto the 3rd Hard Drive ??)

[INDENT][INDENT]when you are willing and want to
[INDENT][INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Sef on 2014-01-19
[COLOR=#000000](Purchase a 3rd Hard drive and install ubuntu onto the 3rd Hard Drive ??)

Or buy an external HD and back up your data to it. (Unplug it after verifying that all the data you want saved, has been saved[/COLOR]

---

### Post by Mark Phelps on 2014-01-20
There is simply NO WAY to reformat an existing parition into another filesystem format without losing data.  Each filesystem format has a different partition table scheme and they are not compatible with one another.

The ONLY way to retain data and reformat a partition is the following:
1) Copy the data to another partition
2) Reformat the partition
3) Copy the data the newly formatted partition.

I strongly suggest "copy" not "move" because if anything goes wrong, you still have the original copy of the data.

Sorry, but there's no such thing as an in-place reformat that retains the old data.

---

### Post by mörgæs on 2014-01-20
Please use a more informative thread title.
Changed.

---

### Post by oldfred on 2014-01-20
The real issue is this which is how Linux sees Windows dynamic partitions:
>     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488395119   244197528+  42  SFS



And if you have created all those logical partitions inside one physical partition you may need to use the Microsoft recommended solution of full backup erase drive and create new basic partitions. Some third party tools may work but that is usually where there is a one to one relationship still between dynamic and physical partitions (or you have not more than the 4 primary partitions). 
Whatever you do good backups are vital.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---


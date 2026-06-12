---
title: "[SOLVED] flash drive needs force formatting"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-11
hi
I've done a search on this but not managed to come up with anything
I have a usb flash drice that is recognised as being unallocated by gparted
I am therefore unable to reformat the drive
It is also not listed under places where flash drives usually show up as "disk" or in the usual place on the desktop
Is there any way of force formatting a drive in ubuntu?

---

### Post by Stunts on 2008-08-11
I suppose you can try to manually mount it from the CLI and then reformat it using the CLI too.
There is a wiki on how to mount devices, but I seem to have lost the link. I can search if you fail to find it though.
As for CLI formatting use the command "mkfs".
Beware - this can be dangerous if not used properly!
Make sure you read trough the man pages. (man mkfs).
Hope this give you a hand!

---

### Post by ajgreeny on 2008-08-11
Surely you can click on the unallocated space in gparted and make a new partition and then format it to the file system you want.  You can not format empty space if there is no partition there to format, if I remember correctly.

---

### Post by ukripper on 2008-08-11
Can you post output of the following commands:
```
sudo fdisk -l
```

and 

```
sudo mount
```

---

### Post by LTFC2020 on 2008-08-11
I tried following instructions I found here:

[http://ubuntuforums.org/archive/index.php/t-520821.html](http://ubuntuforums.org/archive/index.php/t-520821.html)

and did the following in the terminal
any ideas?
the drive is currently listed as being maximum size 3mb but is actually 1 g

richard@richard-laptop:~$ sudo unmount /dev/sdb
[sudo] password for richard:
sudo: unmount: command not found
richard@richard-laptop:~$ sudo mkfs.ext3 /dev/sdb
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
384 inodes, 3068 blocks
153 blocks (4.99%) reserved for the super user
First data block=1
Maximum filesystem blocks=3145728
1 block group
8192 blocks per group, 8192 fragments per group
384 inodes per group

Writing inode tables: done                            
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 39 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
richard@richard-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd9aed9ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3742    30057583+   7  HPFS/NTFS
/dev/sda2           11628       12161     4289355   1c  Hidden W95 FAT32 (LBA)
/dev/sda3            3743       11442    61850250   83  Linux
/dev/sda4           11443       11627     1486012+   5  Extended
/dev/sda5           11443       11627     1485981   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3 MB, 3145216 bytes
1 heads, 6 sectors/track, 1023 cylinders
Units = cylinders of 6 * 512 = 3072 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
richard@richard-laptop:~$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x95bbc6b5.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the DOS compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
No partition is defined yet!

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot   
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data    
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access     
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor      
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT        
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux RAID auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep        
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT            
1c  Hidden W95 FAT3 75  PC/IX          

Command (m for help):

---

### Post by coffeecat on 2008-08-11
**LTFC2020**, did you read **ajgreeny**'s post? To repeat what he said. If Gparted is showing all the space as unallocated, simply create a partition in Gparted and format it with the filesystem of your choice. Also:

> richard@richard-laptop:~$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel

You need to make a disklabel before you partition. You can do that in Gparted. Just hunt around in the Gparted menu.

---

### Post by LTFC2020 on 2008-08-11
hi
I set a new disk label and went to create new partition and the maximum size allowed is 0 mb - so no joy there
What I still need to do is force format the whole drive and start afresh - I think

---

### Post by LTFC2020 on 2008-08-11
I took a screeshot

---

### Post by unutbu on 2008-08-11
How big is this drive supposed to be? "sudo fdisk -l"   is reporting it to be 3MB:
```

Disk /dev/sdb: 3 MB, 3145216 bytes
1 heads, 6 sectors/track, 1023 cylinders
Units = cylinders of 6 * 512 = 3072 bytes
Disk identifier: 0x00000000
```

---

### Post by coffeecat on 2008-08-11
I've never seen unallocated space as a negative quantity before. :( I reckon you've got a dead flash drive there. Possibly the sector that holds the partition table has failed, and it's confusing Gparted. And fdisk too. I just noticed this:

> Disk /dev/sdb: 3 MB, 3145216 bytes
1 heads, 6 sectors/track, 1023 cylinders
Units = cylinders of 6 * 512 = 3072 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table3 megabytes? I don't think so.

One last throw, although I don't hold out much hope. Randomise the whole drive with shred. Plug it in and make sure it's sdb and from a terminal:

> sudo shred -vn 1 /dev/sdbDid I say to make sure it's sdb? You don't want to shred the wrong drive. :? That will take quite a while, and afterwards you could try Gparted again.

---

### Post by LTFC2020 on 2008-08-11
I tried shred and it didnt take a while - it took a couple of seconds
however no difference
this is strange as the drive was originally password protected but gparted caused the problem when I tried to format it to remove the password protected partition
looks like its not going to work though and windows will also not format it so in the bin it goes
thanks to everyone for trying to sort it out

---

### Post by niteshifter on 2008-08-11
Hi,

This USB flash wouldn't be a U3 "smart" type, would it? If so, that could be your problem. You need to "un-U3" it.

For generic devices [go here]("http://www.u3.com/uninstall/final.aspx") to get a removal tool.

For SanDisk devices [use this tool.]("http://www.sandisk.com/Assets/u3/launchpadremoval.exe")

You'll need a Windows XP / Vista machine to use these tools.

---

### Post by alecz20 on 2011-06-26
I know the thread is old, but I have a very similar problem.

Essentially fdisk does not write anything on the partition, nor does GParted.

To remove doubt of a bad SD card, this card works well in the NIKON Photo Camera, which formats it then it can use it fine.

I can see the pictures on the card using the camera (Windows only though), but when I put the card directly in the reader, the system says it's unformatted.

Other cards work fine.

One more thing: the card is 32 GB.

Any ideas?

---


---
title: "3TB WD WD30EZRX couldn't be used under ubuntu 10.04"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by hth0923 on 2012-02-23
Hi All,

I have been searching around for this topic, found quite number sources from forum; website etc.... I have tried every single method that each source suggested. But it's been a week, my drive is still not working. I hope someone could really give me a hand on it and get the ball rolling.

OS: Ubuntu 10.04 ( 2.6.32.38 )

Target:

Partition: 2 x 1.5TB
Table: GPT
File system: ext4
Purpose: Storage & file server

Program used: Gparted GUI & Commend line

Gparted GUI:

1, Device > Create Partition Table > select GTP under Advanced>press apply
2, Partition > New > 
-- Free space preceding (Mib): 2 (Tried 1 as well, no luck)
-- New Size (Mib): 1430792
-- Free space following (MiB):1430792
-- Create as: Primary Partition
-- File system: ext4
-- unchecked Round to cylinders
3, Partition > New >
-- Free space preceding (Mib): 0
-- New Size (Mib): 1430792
-- Free space following (MiB): 0
-- Create as: Primary Partition
-- File system: ext4
-- unchecked Round to cylinders

After a while error occur, and the whole system very slow, it took 10 minutes to restart the system. I have saved the details below:

[PHP]GParted 0.5.1

Libparted 2.2

Create Primary Partition #1 (ext4, 1.36 TiB) on /dev/sdf  00:02:47    ( ERROR )
    	
create empty partition  00:00:01    ( SUCCESS )
    	
path: /dev/sdf1
start: 4096
end: 2930266111
size: 2930262016 (1.36 TiB)
set partition type on /dev/sdf1  00:00:00    ( SUCCESS )
    	
new partition type: ext4
create new ext4 file system  00:02:46    ( ERROR )
    	
mkfs.ext4 -j -O extent -L "" /dev/sdf1
    	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=1 blocks, Stripe width=0 blocks
91578368 inodes, 366282752 blocks
18314137 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
11179 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
102400000, 214990848

Writing inode tables: done 
mke2fs 1.41.11 (14-Mar-2010)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir 
========================================

Create Primary Partition #2 (ext4, 1.36 TiB) on /dev/sdf    ( ERROR )
========================================[/PHP]

Gparted Commend line:

[PHP]root@huan-linux:~# parted /dev/sdf
GNU Parted 2.2
Using /dev/sdf
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdf will be destroyed and all data on
this disk will be lost. Do you want to continue?
Yes/No? Yes                                                               
(parted) print
Model: ATA WDC WD30EZRX-00M (scsi)
Disk /dev/sdf: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

(parted) mkpart primary 1MB 1500GB                                        
(parted) mkpart primary 1500GB 3001GB
(parted) print                                                            
Model: ATA WDC WD30EZRX-00M (scsi)
Disk /dev/sdf: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1500GB  1500GB               primary
 2      1500GB  3001GB  1501GB               primary

(parted) q                                                                
Information: You may need to update /etc/fstab.                           

root@huan-linux:~# mkfs.ext4 /dev/sdf1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=1 blocks, Stripe width=0 blocks
91553792 inodes, 366210560 blocks
18310528 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
11176 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
root@huan-linux:~# mkfs.ext4 /dev/sdf2
mke2fs 1.41.11 (14-Mar-2010)
Warning: could not erase sector 2: Attempt to write block from filesystem resulted in short write
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=1 blocks, Stripe width=0 blocks
91594752 inodes, 366355712 blocks
18317785 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
11181 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Warning: could not erase sector 0: Attempt to write block from filesystem resulted in short write
Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir[/PHP]

Above seems working nicely, and ready to roll. Unfortunately, the OS become very slow again. restarted the system, there is no partitions being created.

Could anyone give me a warm hand here :confused::confused: .

Many thanks
hth0923

---

### Post by hth0923 on 2012-02-24
Anyone has such situation? could you please give me a help?

Thanks a lot. 

Regards,
hth0923

---

### Post by oldfred on 2012-02-24
I think I used the gparted from 10.04 when I created my first gpt drive to experiment. It was not a large drive.

Is your drive one of the new 4K drives?

Have you tried downloading the newest gparted liveCD. 

Or have you tried gdisk?

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

With gpt and BIOS you need a bios_grub partition or if using UEFI your very first partition has to be efi. All new drives I am formating with both efi and bios_grub since I am still BIOS but may get a new UEFI computer this years. 

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

---

### Post by hth0923 on 2012-02-27
Hi oldfred,

Million thanks for your informative and quick answer.

-- Is your drive one of the new 4K drives?

Yes the drive on 4k.

-- Have you tried downloading the newest gparted liveCD. 

Yes i have done it and runs it over 2 computers. gparted-live-0.11.0-10.iso (121.1 MB), I have also tried gdisk, parted, disk utility, no luck at all. 

I have also tried to format the drive in Windows 7. 1.5TB each on 2 partitions. The 1st 1.5TB NTFS took 10 minutes on quick format, sounds really strange for me, as it should take about 10 seconds rather that such long time. I would like to ask, is that windows is realigning the drive and writing GPT table and system files to the 1st partitions? Furthermore, 2nd partition 1.5Tb takes normal 10 seconds to complete the process. 

**[COLOR="Red"]*Finally*[/COLOR]**, I have checked the disk health, it has 65533 bad sectors, and straight away returned the disk and getting the replacement soon.

I think when i received the new drive, I will try use various methods provided by you and do it under the ubuntu 10.04, if i couldn't manage to get it because my limited knowledge on linux, then I will try below method, could you let me know if it is practical.

1, 3 partitions on windows 7
2, 200mb hidden NTFS on 1st partition (I think the GPT table and system files is set in the 1st partition about 136mb), 1.5TB on 2nd and 3rd partition
3, set the drive in Linux and use native Gparted convert the 2nd and 3rd partition to ext4 and secure and leave the hidden 1st 200mb partition. 

As i am using the 3TB drive as storage addon, do you think this method is ok?

> With gpt and BIOS you need a bios_grub partition or if using UEFI your very first partition has to be efi. All new drives I am formating with both efi and bios_grub since I am still BIOS but may get a new UEFI computer this years. 

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

As i am still a beginner in Linux world, could you guide me through the above process? do i need to adjust anything from the Bios such as change IDE to AHCI or i just need to do few commends in the terminal?

Many Thanks and I am appreciate you answers.

Regards,
hth0923

---

### Post by oldfred on 2012-02-27
I think all new drives should use ACHI in BIOS, and definitely not IDE. At least Large or LBA settings in BIOS. But ACHI may make Windows not work. I know it it a PITA in XP and I boot XP so little now that on the rare occasion I just set BIOS back from ACHI. With Windows 7 you can change it to ACHI while in whatever mode you are in and then it should work.

I have seen some posts from users  with very large drives that had very strange results from some Windows program's formating. It only formated to the 2.2GB that MBR allows but wrapped around somehow and made weird results. Check drive size in gparted and several tools to make sure drive is seen correctly, if you do anything in Windows.

---

### Post by spandey on 2012-02-27
Do you have UEFI motherboard, if not please don't use Windows to Format hard drive larger than 2.2 TB, it's real pain. 

Please try to have Ubuntu and GRUB within first 500GB of your disk. The speed will be great, that's what is my experience.

---

### Post by hth0923 on 2012-02-27
> **oldfred said:**
> I think all new drives should use ACHI in BIOS, and definitely not IDE. At least Large or LBA settings in BIOS. But ACHI may make Windows not work. I know it it a PITA in XP and I boot XP so little now that on the rare occasion I just set BIOS back from ACHI. With Windows 7 you can change it to ACHI while in whatever mode you are in and then it should work.

I have seen some posts from users  with very large drives that had very strange results from some Windows program's formating. It only formated to the 2.2GB that MBR allows but wrapped around somehow and made weird results. Check drive size in gparted and several tools to make sure drive is seen correctly, if you do anything in Windows.

Many thanks for your confirmation. I will turn it on over the bios after i got the new drive in hand. As i am having this storage on Ubuntu 10.04, therefore it wouldn't be any problems if i turn it to AHCI. 

I will let you know the outcome when i set it on.

Thanks again.

Regards,
hth0923

---

### Post by hth0923 on 2012-02-27
> **spandey said:**
> Do you have UEFI motherboard, if not please don't use Windows to Format hard drive larger than 2.2 TB, it's real pain. 

Please try to have Ubuntu and GRUB within first 500GB of your disk. The speed will be great, that's what is my experience.

I have checked on the net, it said both of my motherboards P5Q & P6T V1 Deluxe are on EFI. is that a difference between UEFI and EFI?

Linux on P5Q and WIndows 7 on P6T V1 Deluxe. both of them recognised the drive correctly at 2.73TiB and Windows 7 could partition the drive into 2 parts at 1.5TB each on NTFS. Linux set the GPT table quickly and correctly, but couldn't partition the drive at all, and stuck the system.

-- Please try to have Ubuntu and GRUB within first 500GB of your disk. The speed will be great, that's what is my experience.

As my linux knowledge is pretty limited, what do you mean for above?

Thanks for your help.

Regards,
hth0923

---

### Post by oldfred on 2012-02-27
If just a data drive with NTFS you do not need the boot partition(s).

Grub2 has a bug on very large / (root) or /boot partitions. I normally suggest only 25GB for / (root)  even with a drive as large as yours, if you have separate data or /home partition(s).

Because the partitions are NTFS, you will need to manually run chkdsk periodically. Ubuntu runs fsck every 40 to 60 boots, but I do not think Windows does even on its system partition. Be sure to have a good Windows repairCd or USB.

A little food for thought on large drives.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive with data on several drives also.

UEFI is the update/replacement for BIOS. Most boot in BIOS mode from MBR if an efi partition is not found. Windows requires UEFI to boot from a gpt drive. Ubuntu works with gpt for either BIOS (I use it now) and UEFI. Since I may buy a new UEFI system this year, I format new drives (or when totally reformatting) with both an efi partition at the beginning of the drive for future UEFI booting and a bios_grub partition to let grub2 work with current  BIOS booting and gpt drives.

---

### Post by hth0923 on 2012-07-06
My final solution, return the drive and get a 2TB drive sadly.

Many thanks for all your support!

Regards,
hth0923

---


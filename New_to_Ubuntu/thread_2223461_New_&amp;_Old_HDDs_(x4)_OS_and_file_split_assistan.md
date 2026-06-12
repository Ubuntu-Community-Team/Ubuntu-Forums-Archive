---
title: "New &amp; Old HDDs (x4) OS and file split assistance request"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by Drowz0r on 2014-05-11
Hello all

I am upgrading and adding to my current HDD arrangement. Currently I have two HDDs, SATA, one with Windows on and one with Ubuntu on (to keep things simple).

I wish to load Ubuntu onto a SSD HDD and then run two SATAs for everything else on my Ubuntu OS; one being the SATA I already have with Ubuntu on it and the other an additional SATA drive I will purchase.

I would like to use the two discs in tandom, but I'm not sure what RAID set up I would need (I hear it's RAID0 but unconfirmed).

The Windows SATA disk would remain untouched. Totalling to x1 SSD with Ubuntu OS on it, x2 SATAs working together for Ubuntu games, music, etc... and x1 SATA for Windows.

I have some questions:

      1) Is this difficult to set up? Seems relatively easy reading up on it online.

      2) Can I just move my files from my existing Ubuntu SATA HDD, or would I have to do a fresh install?

      3) My SATA discs can take 6GB (SATA 3) transfer rates it seems. Is it worth getting SATA 3 cabling, as the drives can't write the information that fast anyway...?   (Currently I have SATA 2 cabling, 3GB rate)

      4) Is it worth having a different file system to EXT for my OS and then EXT for the other discs?

      5) Always end a list on odd numbers

Thanks in advance all :)

---

### Post by oldfred on 2014-05-11
I am not a fan of RAID on desktops. For servers with many drives and daily backups to tape then it does make sense.

       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I suggest a full new install to SSD. You need different configuration anyway.

I would stay with ext4.
[http://www.phoronix.com/scan.php?page=article&item=linux_315_hddfs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_315_hddfs&num=1)

And if not using Windows on a drive to boot, then use gpt partitioning. Windows only boots from gpt with UEFI, but will read data from NTFS partitions on a gpt drive when booted in BIOS with MBR on another drive. 
Ubuntu will boot from gpt with UEFI or BIOS. But if you have the 35-40 year old MBR(msdos) partitioning you can only boot with BIOS.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Drowz0r on 2014-05-12
Awesome.

SDD for OS and x2 SATA for files then.

EXT4 it is, makes things easier anyway.

Is it difficult to install files when using multiple partitions? For instance if I'm installing something from the terminal, do I get prompted for which partition to install it to or would I have to specify from now on? I'm trying to reserve my SDD for OS stuff and maybe one or two other things, like the browser etc... things used the most. I'd like games, documents and all that other junk on the SATA HDDs.

Thanks for the help

---

### Post by oldfred on 2014-05-12
Programs from repository are always installed in / (root). I think some games can be elsewhere.
If you put /home on the hard drive all data automatically goes into /home.

But a bit more advanced is separate data partition. But then you have to set ownership, permissions and mount it to make it easy to use.

I have lots of programs, but no games and use 11GB of my 28GB / partition. That does include my /home, but the only thing in /home is wine for Picasa and the hidden user settings. And larger hidden folders with data like Firefox & Thunderbird profiles are also moved to my data partition. My /home inside my / is about 2GB and most of that is the wine folder.

---

### Post by Drowz0r on 2014-05-14
Alright, so I've installed Ubuntu 14.04 LTS onto the SSD drive. The other two drives weren't formatted with the installation though (not sure why) and are mounted. One is my old Ubuntu disc, and I can see all my old files on it and stuff.

How do I format these other two HDDs and make them a seemless part of my OS? Atm they just seem to be disks I can drop files in and out of.

I have something like 300GB of games, so I need to be able to install games and have them "spill over" into other HDDs or specify which HDDs to install them into. I can't just drag and drop them like a video file.

This is why I think I need something like RAID but I could be wrong.

---

### Post by oldfred on 2014-05-14
Specific examples here for both NTFS and ext4.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

You do need to partition drives and format the partition(s).

If you add to fstab then they will always be mounted under the mount point or name you give partition. Better than just d: or e: that Windows uses. I also label partitions with gparted when I create them or disks or Disk utility if I forget or change partition. Then for those partitions I do not mount automatically I have a name I recognize. But I have labeled a partition Data and mounted it data in fstab and gotten confused. :)

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

If Linux formatted you have to set ownership & permissions for each mount point.

 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Drowz0r on 2014-05-14
It's not actually allowing me to format the drive even when I put in the fresh DVD to format everything. I've connected the three discs. SSD x1 and HDD (regular SATA) x2 and it will not let me delete the partitions and only installs Ubuntu to the first disk.

I continued as normal thinking maybe gpartition could do it or something but it also will not let me format the old HDD and use it for space.

So I carried on setting up Ubuntu and for some unknown reason it decided to no longer allow me to boot into my desktop properly. I get a cursor and nothing else. Recovery mode didn't fix it so I decided to just do a format again.

Now after suppisidly wiping the disk it tells me there is already a grub boot loader present. I don't get how as the disk is meant to be blank... So co ringing without one (It is detecting the OS on the HDD I can't wipe as an alternative OS so it wants grub).

---

### Post by Drowz0r on 2014-05-14
Okay, unplugged all except the SDD and still couldn't boot.

Formatted the drive again and not loaded in any other drives. All is working.

I've plugged in one of the regular SATA HDDs.

Drive opens fine. I have the option to "Unmount" it, so I suspect it's mounted already? It just opens like any other media.

---

### Post by Drowz0r on 2014-05-14
I did this to check:

```
drowz0r@Prime:/dev$ ls s*
sda   sda2  sdb   sg0  sg2  snapshot  sr1     stdin
sda1  sda5  sdb1  sg1  sg3  sr0       stderr  stdout
```

SDA is my SSD HDD, SDB is the 2nd disk, the regular HDD (500GB).

So it seems to mount by itself, simply by being plugged in?

---

### Post by Drowz0r on 2014-05-14
Right looking into it, it seems I had to unmount the disks, format them, partition them.

Seems to be working fine now. Not sure if they should be primary or extended partitions. I think primary...

---

### Post by Drowz0r on 2014-05-15
Sigh. I can't help but think this has become wildly more complicated than it needs to be.

I just need to mount 3 hard disks and it's not working. I've formatted the disks but regardless of what method I use to mount them, command line or gpart or whatever they only display as read only disks. I've even tried manually changing the permissions but that only seems to half work.

fstab shows my disks as:

```
drowz0r@Prime:~$ sudo fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b53ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   116660223    58329088   83  Linux
/dev/sda2       116662270   125044735     4191233    5  Extended
/dev/sda5       116662272   125044735     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00058939

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x299b299a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976773119   488385536   83  Linux
```

So why can't I actually use the disks?

---

### Post by oldfred on 2014-05-15
You have to give yourself ownership & permissions. 
And clicking on a partition will mount it automatically but not with your ownership & permissions. 

Re-review post #6

I do prefer to label partitions that I do not auto mount with fstab so I have a better idea of what they are. But that is because I have lot of partitions. 

If not mounted with Nautilus. Or you can just run the chmod & chown commands on the location already mounted. This will show mount points if mounted already:
mount

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by Drowz0r on 2014-05-16
Yeah I tried the chmod permissions thing but it didn't seem to work. Remounted everything and did chmod again and it worked... so perhaps I missed a step or something? I even tried setting chmod to 777 but didn't get anywhere.

Oh well, at least it's clicked into place now :)

Thanks

---


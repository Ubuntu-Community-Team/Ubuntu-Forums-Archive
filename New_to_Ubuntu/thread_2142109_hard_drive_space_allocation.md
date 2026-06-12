---
title: "hard drive space allocation"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Cu Rua on 2013-05-04
I've got an 80 gb hard drive, but my file system containing all my photos, docs, music, etc. lives on just 26.9 gb, and yesterday I ran into that limit. 
How do I give my file system more space?

---

### Post by Cheesemill on 2013-05-04
We need more information please. Is this a dual boot or do you just have Ubuntu installed? How is your drive partitioned?

Can you post the output of the following commands...
```
df -h
sudo parted -l
```

---

### Post by woxuxow on 2013-05-04
the best graphical way to solve your problem is "gparted"
gparted can edit - remove - resize - create and ... your partitions
sudo apt-get install gparted

---

### Post by Paqman on 2013-05-04
Did you install using Wubi? If you're not sure, look for a location in your filesystem called /host. If that's there then it's a Wubi install and you've hit a hard limit in Wubi installs. You may need to reinstall into a partition with more space.

---

### Post by Mark Phelps on 2013-05-04
> **MustafaJF said:**
> the best graphical way to solve your problem is "gparted"... 
NOT .. if the OP installed using Wubi -- which typically has a 30GB "limit".  

It's important to find out HOW they installed Ubuntu BEFORE telling them to use a partitioning tool.

---

### Post by woxuxow on 2013-05-05
> **Mark Phelps said:**
> NOT .. if the OP installed using Wubi -- which typically has a 30GB "limit".  

It's important to find out HOW they installed Ubuntu BEFORE telling them to use a partitioning tool.

yeah, you are right.

---

### Post by Cu Rua on 2013-05-14
```
 rachael@rachael-desktop:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              27G   25G  1.2G  96% /
none                  497M  312K  497M   1% /dev
none                  501M  368K  501M   1% /dev/shm
none                  501M   88K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
rachael@rachael-desktop:~$ sudo parted -l
[sudo] password for rachael: 
Model: ATA WDC WD800BB-00JH (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   16.5GB  16.4GB  primary   ntfs
 3      16.5GB  80.0GB  63.5GB  extended
 7      16.5GB  45.5GB  29.0GB  logical   ext3
 8      45.5GB  46.8GB  1291MB  logical   linux-swap(v1)
 5      46.8GB  78.6GB  31.8GB  logical   ext4
 6      78.6GB  80.0GB  1416MB  logical   linux-swap(v1)


Model: ATA ST340016A (scsi)
Disk /dev/sdb: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  ext3


rachael@rachael-desktop:~$ 


``` 

what does this tell you?

---

### Post by Impavidus on 2013-05-14
To make a code box, use [/code] instead of [code] for that closing tag.

I see you have been messing around a bit when installing. You have two swap partitions where one should be sufficient and you have two linux partitions, one ext3 and one ext4 (sda7 and sda5). Do you have two linux installs on this computer? That wouldn't make you an absolute beginner, so I assume you don't.

Your root partition is sda7 now. If sda5 is not used at the moment the easiest way to solve this is to move a large directory (I propose /home) to sda5. You may also want to delete one of the swap partitions and expand sda5 to fill its space. Maybe some other resizing. Alternatively, you can delete sda8 and sda5 and expand sda7 to take up the freed space. This is somewhat more flexible, as you don't have to get the relative sizes of the root and /home partitions correct, but separate root and /home has some advantages too.

Partitioning can be done using gparted from a live medium. Always make backups on external drives before changing partitions. Wait for a moment for other replies, as others may have different suggestions.

Edit: Now I see there is also an sdb drive, completely formatted as ext3. It this used for something? If not, you may be able to move part of your data there.

---

### Post by Cu Rua on 2013-05-14
As far as Linux is concerned, I mostly mess in the GUI, and barely literate in computer terms. 

I have two swap partitions because this computer originally came with Windows 7, and my at-home tech support begged on bended knee to dual-boot it instead of wiping it out when I installed Ubuntu. Deleting the extra would probably cripple Windows, wouldn't it? (More than Windows is already crippled, that is.) 

I have gparted because that second drive is a royal pain-- it's convinced that I don't have permission to access it until I use some magic word in the terminal (that I've since forgotten)-- and I spent a long afternoon reformatting it over and over trying to make it behave. If there were a way to exorcise the demons from that drive, I'd use it to back up my stuff before reformatting my main drive. I'd really like to take full advantage of my giant main drive-- it's hard to believe that it needs 50 gb for temp and program files.

---

### Post by Impavidus on 2013-05-14
Windows doesn't use partitions of the type linux-swap. It has its own swap file, located in the windows partition. Only Linux uses that swap partition, and if you have enough RAM it's more of a convenience than a necessity.

Instructions on moving your home directory to a different partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Information on fstab, for easy mounting of partitions: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I'm going to sleep now, but someone else in a timezone closer to you may answer more questions.

---

### Post by Cu Rua on 2013-05-16
Alrighty, thanks for the links. 

Since you pointed out that they're linux swaps, I realized that I may still have Ubuntu 8.04. I thought it got squashed when I upgraded to 10.04. 

I've got a gb of ram, between facebook, deviantart, and hi-res images, my computer slows to a crawl. Would a bigger swap partition speed things up a hair? 

Also, is there anything you can think of to beat my second drive into submission besides reformatting? I can mount it and pull things off it, but I can't put things in it.

---

### Post by d0006 on 2013-05-16
Please understand that GNU/Linux is a very different mindset than windows.  The people who develop Linux believe in freedom.  This means they provide a framework that has many options for different configurations.  This means that users have to know what options they want to create a useful system.  This means that users have to do a lot more learning to use Linux effectively than windows users.  Ubuntu does a pretty good job of offering a "plug and play" OS but when you get "creative" things get complicated fast.  I'm saying all this because when you dual boot, have a system with multiple drives, etc., you will have to spend some time learning Linux and the command line.

Anyway, if you only have 1GB of RAM you should consider a "midweight" distro.  I installed Ubuntu 13.04 on a 1GB laptop and it is a slug!  Some suggestions:

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php) (KDE version)
[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) (go with 12.04 LTS)

If I had your setup I would backup the data I wanted to save and repartition and reformat both drives. You can backup the data from the 40GB drive to the 80GB drive first and repartition/reformat the 40GB  (use the ext4 filesystem) and then backup the 80GB drive to the 40GB drive and fix the 80GB drive. You can leave the NTFS partitions alone and keep your windows installation.  I would dual boot the 80GB drive and use the 40GB drive for backup/data storage.

---

### Post by Cu Rua on 2013-05-16
Yup, the freedom and control was the reason why I decided to convert to Linux. Also, having a research and development team numbering in the hundreds of thousands appeals immensely <3 Learning command line on my list of things to do, in between finding a few decent game emus and learning graphics programs.

Thanks, I think I'll stick to this distro and buy some more ram. Seems simpler. 

Thanks for the ext4 tip, suddenly I have permission to mess with the 40 gb drive ^.^ Methinks I'll do your data flipping idea and repartition the 80 gb drive with gparted, see whether my tower explodes. The second drive was always intended as a backup, particularly as it's always been a pain >.< I'll let you know how it goes.

---

### Post by Cu Rua on 2013-05-16
Well, I backed up my stuff on the 40 gb drive, but haven't been able to repartition the 80gb drive without error messages and gparted threatening to delete the whole thing. 

I started out in the disk utility and had it delete the extra swap partition and the empty file system, but left the NTFS section alone. When I tried to repartition the drive, "drive is busy" popped up; when I tried to unmount the partition, it said the same thing. I tried to create a partition in the empty space and got this:

 ```
 Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sda, start=46777167360, size=33249104384, type=0x83
Entering MS-DOS parser (offset=0, size=80026361856)
MSDOS_MAGIC found
looking at part 0 (offset 1048576, size 104857600, type 0x07)
new part entry
looking at part 1 (offset 105906176, size 16393000448, type 0x07)
new part entry
looking at part 2 (offset 16499942912, size 63526328832, type 0x05)
Entering MS-DOS extended parser (offset=16499942912, size=63526328832)
readfrom = 16499942912
MSDOS_MAGIC found
readfrom = 45485798400
MSDOS_MAGIC found
readfrom = 46777199104
MSDOS_MAGIC found
readfrom = 46777167360
MSDOS_MAGIC found
Exiting MS-DOS extended parser
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 1
got it
got disk
new partition
Error: Can't have overlapping partitions.
ped_disk_add_partition() failed


``` 

I brought up gparted and found I couldn't do anything except format and wipe the entire drive. 

Help!!

---

### Post by Cu Rua on 2013-05-17
:? The end of this sad sad tale: I shut down my computer for a few hours, and then it wouldn't boot back up again. "Error 17" right after post. I booted it up through my 8.04 installer disk and spent many many hours updating and upgrading it back to 10.04, and incidentally decided I was sick of Windows and squashed it. Now I have a 77 gb primary partition formatted to ext 3. 

Problem agonizingly solved!

---


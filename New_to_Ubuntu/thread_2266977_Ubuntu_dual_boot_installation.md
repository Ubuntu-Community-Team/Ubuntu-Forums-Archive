---
title: "Ubuntu dual boot installation"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by Ridhz on 2015-02-26
Hi everyone,
I am a beginner at Ubuntu and I have a few queries regarding installtion. I would be really thankful if you could help me out. My laptop has 500gb HDD and it's currently running win 7 32-bit. I have partitoned my HDD into C : (OS) about 100 GB and D : (empty drive). I have backed up all important data to a 500gb external HDD.I want to install Ubuntu 14.04 without uninstalling windows. 
My queries are:-
1. Is a separate partition recommended ?
If yes (a) Should I partition D drive before installation using disk management or during installation ?
2. How much space does Ubuntu require ? (what would you recommend)
Thanks in advance!

---

### Post by sandyd on 2015-02-26
> **Ridhz said:**
> Hi everyone,
I am a beginner at Ubuntu and I have a few queries regarding installtion. I would be really thankful if you could help me out. My laptop has 500gb HDD and it's currently running win 7 32-bit. I have partitoned my HDD into C : (OS) about 100 GB and D : (empty drive). I have backed up all important data to a 500gb external HDD.I want to install Ubuntu 14.04 without uninstalling windows. 
My queries are:-
1. Is a separate partition recommended ?
If yes (a) Should I partition D drive before installation using disk management or during installation ?
2. How much space does Ubuntu require ? (what would you recommend)
Thanks in advance!

1. It is not only required, but recommended. Ubuntu cannot be installed onto a NTFS filesystem. It is best to let windows fiddle with the partitions. During installation, click "something else" during partitioning, and create the following
a) Root partition (Click New -> set mount to '/', filesystem to ext4). The root partition is the highest level directory there is in the linux filesystem and stores all files in the OS.
b) Swap partition, used similar to a windows paging file (Click New -> set filesystem to swap).

If you want, you can create a separate partition for /home . Most user defined settings, and all their files are generally stored inside /home. As a result, if you need to do a reinstallation, you will not be wiping out your files and settings as you can just delete the root partition and leave the home partition be. However, you may be limited to 4 partitions per drive if you are using MBR

If you want to hibernate, Swap partition must be larger than your RAM.

If you have multiple physical disks, make sure that the the drive specified for your bootloader is correct (generally /dev/sda if you only have one drive in your system)


2. around 5G Minimum, but you would not really be able to do anything without running out of space. The amount you choose to let Ubuntu use is your own choosing.

If you are unsure about partitioning, boot up using a Ubuntu LiveCD, and run the following commands in a terminal:
```

wget http://softlayer-dal.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
sudo bash bootinfoscript
```

The commands will generate a file which you can attach or post the contents of here :)

---

### Post by Bashing-om on 2015-02-26
Ridhz; Hi ! Welcome to the forum.

The quick way to get your feet wet easiest.
Boot the install media, select the "unallocated" space, and let the install wizard install ubuntu to ALL of that space.
Bear in mind can only have a maximum of 4 primary partitions in the legacy partitioning scheme .. to get around that limitation is the 'extended' partition as a container for 'logical' partition ( ubuntu is happy to install to 'logical' partitions)
Now that said, if you desire to set up partitions before hand for the installer to set up on:
I see 30 Gigs as recommended for a starter for the '/' (operating system at large);
Maybe consider setting up a separate /home partition of say 20 Gigs, that will lessen the amount of space required for '/' ;
As you are dual booting with Windows, you might consider a shared NTFS partition to share files between Windows and ubuntu ;
IF you have less than 4 Gigs of ram, and you do intend to hibernate the system, then a "swap" partition is required - slightly larger then the amount of ram installed.

All that above said, IF you keep good backups of your personal files, once you are comfortable with ubuntu - at that time is no big deal to re-partition to accommodate your experienced use case.

Oh, as an aside, Hard disk nomenclature:
Where Windows designates C: of D: as a Hard drive, in actuality these are partitions.
linux (ubuntu) does a hard disk identification:
sda -> serial drive 1
sdb -> serial drive 2
sdc -> serial drive 3
sda1 is serial drive 1, and the 1st partition on that hard drive
sda2 is the 2nd partition of 1st hard drive
sdb5 is the 5th partition of 2nd hard drive
sdc8 is the 8th partition  on 3rd hard drive. 

[INDENT][INDENT]get your feet wet
[INDENT][INDENT][INDENT]dive in
[INDENT][INDENT][INDENT][INDENT]the water is fine
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gmulak on 2015-02-27
Ridhz, you have some great help in these comments.  I was not sure what you meant about "backup" as in what format that was in.  When I do this in the computer lab at Surf City Church in Huntington Beach I usually clone the HDD so that I can "go back" if something goes really wrong.  Clontining is like taking a picture image of the HDD where it is in that point of time.  There are different software for this.  One free one is Clonezilla, here: [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php)  You can also search the internet.

---


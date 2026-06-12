---
title: "Installing Kubuntu 7.10 on Software RAID5"
date: 2008-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by LNK on 2008-02-17
[size=+2]**Introduction**[/size]

This is a step-by-step tutorial/guide for setting up a complete Kubuntu 7.10 (Gutsy Gibbon) system on RAID5. By this I mean that the root partition (and other system partitions) are on RAID5. If you plan to install your system on RAID1 and only use RAID5 for data, you may find this guide helpful. But it's focus is installing the **system** on RAID5.

I've installed Kubuntu because I prefer the KDE desktop. But this should work just as well for Ubuntu or one of the other Ubuntu-derived variants. I have **not** installed anything other than Kubuntu as described here. So be forewarned. But I can think of no reason why it shouldn't work.

I did a lot of research on exactly how to install to RAID5. Here are a few sources that I bookmarked and found particularly useful. I want to thank the authors for their assistance!
[list]
[*]_[FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)_, How to install Ubuntu onto a ***fakeRAID*** system
[*]_[HOWTO Install on Software RAID](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID)_
[*]Forum thread: _[HOWTO: Linux Software Raid using mdadm](http://ubuntuforums.org/showthread.php?t=408461)_
[/list]
These sources where very useful, particularly because they showed me the basics and provided ideas. But I never found a source to do specifically what I wanted: system installation to RAID5. So I decided to jump in head first and learn it.

I believe I installed from scratch a half dozen times. At least once, leftover partition information on my hard drives prevented me from getting the installer to do what I needed. So I zeroed all my hard drives to remove anything left over and started again. I kept a lot of notes and when I had it all working, I zeroed the drives and started again, following my notes to the letter to be sure I had it right. I've now written this guide directly from my notes.

I've tried to write this guide for someone with limited Linux experience. For experience users, it will probably seem too detailed. The RAID support in Linux is solid and stable. But as some of us have found, the installation isn't so easy. So I've tried to focus on detailed step-by-step instructions. The guide is a bit long. But if you have average experience with Linux, you should be able to complete the installation in a couple hours. It may take longer if you have very large partitions for your RAID arrays. It does take some time for the system to build the arrays. But you can take a break while it's doing that.

If you don't know much about RAID, you should do a little self-education. It will help if you know some of the basics, like the difference between RAID0, RAID1 and RAID5. If you know how RAID5 works then you'll understand why you need at least three drives and why in any RAID5 array you can have one drive fail but not two. And you'll understand why some partitions, like **[font=courier]/boot[/font]**, can't reside on RAID5.

[size=+2]**Prerequisites**[/size]

The prerequisite list is pretty short. Here's what you'll need:
[list]
[*]An Intel- or AMD-based PC.
[*]At least 3 hard drives of reasonable size.
[*]A CDROM drive.
[*]Connected monitor, keyboard and mouse.
[*]The Kubuntu 7.10 Alternate Install CD which you can _[download](http://www.kubuntu.com/download.php)_ and burn.
[/list]
Also recommended:
[list]
[*]A companion working system so you can consult the Internet if you have issues.
[*]The Kubuntu 7.10 Desktop CD which you can _[download](http://www.kubuntu.com/download.php)_ and burn.
[/list]
A working system connected to the Internet is highly recommended and almost a must have. You probably won't need the Desktop CD. It's nice to have if you run into issues because you can boot a working Kubuntu system in memory and use it to troubleshoot.

[size=+2]**Important Learning Experiences**[/size]

There are a few things I learned while going through this process. I'll point those out up front and then expand on them later.
[list]
[*]The installer will not install to a RAID5 partition. RAID5 is available in the partitioning menus, but it doesn't work. RAID1 seems to work very well. I'm not certain of the reason for this. But I suspect it is due to limited RAID support in the installer for actually **running** RAID, as opposed to configuring RAID. The process presented here works around this issue by installing the system to a non-RAID partition and then moving it to RAID5 partitions created later.
[*]The default **[font=courier]init[/font]** process doesn't support putting **[font=courier]/var[/font]** or **[font=courier]/tmp[/font]** in partitions separate from the root partition. The issue is in the sequence services are started. The RAID daemon is not started soon enough. I will show you how to change things so it will work.
[*]If you don't install the root partition as a RAID partition, the installer will not include RAID support when it builds the kernel. I will show you how to fix this as well. It adds an extra step or two.
[/list]

[size=+2]**My Hardware ... For the Curious**[/size]

I'm building a medium to high-end server system. I have three desktops and a laptop at home, plus the laptop owned by my employer that I carry between home and work. These are all individual systems, three of the four running Windoze and the other running Kubuntu. I don't have much of a network, just a couple of Windoze shares and printer sharing. I want to set up a good network with a central server. I've recently had a couple of disk failures. Although I didn't lose any data, one was a close call. I've gotten lax about backups and I want to correct that. I have a lot of data and would like to centralize some of it and then also do daily backups from all the desktops and laptops to the server. I kicked the idea around a while and finally decided to do RAID5. The choice of Linux was a no-brainer for me. The thing I like about RAID5 is that once the initial installation is done, if I add another like-size disk I increase the amount of storage by the size of the disk (roughly). This isn't true of RAID1; I'd have to add two disks to double the size.

My priority when choosing hardware was to find a motherboard that supported a high number of SATA drives. Given that I also needed a case with ample space and cooling for the drives and a big power supply. But since it's a server, I don't need a high-end video card. I could have saved a few dollars on memory, but I got a great deal so I filled it up. Here's what I have for hardware:
[list]
[*]Antec P182 Mid-Tower case
[*]CoolerMaster Real Power Pro 1000W power supply
[*]Gigabyte GA-P35-DS3P Rev 2 motherboard
[*]Intel Core 2 Duo E6750 2.66Ghz CPU
[*]8 GB Patriot 800Mhz PC6400 (4x2GB) memory
[*]5 Seagate ST3500320AS 500GB, 7200rpm, 32MB cache, hard drives
[*]Samsung SH-S202G DVD burner
[*]EVGA e-GeForce 6200LE PCI-E graphics card
[*]Sony MPF920 1.44MB floppy drive
[/list]
The BIOS supports AHCI (Advanced Host Controller Interface) for SATA. The Linux kernel has excellent support for AHCI. So I enabled it in the BIOS. It wasn't enabled by default. I've seen no issues with it so far.

[size=+2]**Decide on Partition Scheme**[/size]

There are a lot of different ideas about how to partition your system. It really comes down to a matter of personal preference. I am from the "old school" on this one and I like separate partitions for **[font=courier]/var[/font]** and **[font=courier]/tmp[/font]**. The reason is simple: These two directories are used by programs for temporary output files which may be very large. For example, the print spooler uses temp space under **[font=courier]/var/spool[/font]**. If someone prints a very large file, the spooled output could be enormous. If **[font=courier]/var[/font]** is in the root filesystem, its default location, and the spooled output fills the filesystem, the system will crash. If **[font=courier]/var[/font]** is in a different filesystem and the same thing happens, the system does not crash and you can fix the issue. As I said before, this is a personal preference. It does make things more complicated.

As I mentioned above, putting **[font=courier]/var[/font]** and/or **[font=courier]/tmp[/font]** in separate partitions complicates the installation process. If you keep them in the root partition, where they are by default, there are a number of steps in this guide that you can skip. I will point these out. But you may want to think about that ahead of time while you're deciding on how you will set up your partitions.

A RAID5 installation requires at least two partitions, one for **[font=courier]/boot[/font]** and one for the root partition. You **cannot** put **[font=courier]/boot[/font]** on a RAID5 partition. The reason is quite simple. The boot loader has no built-in RAID support. It expects to find the kernel in a partition on a **single** disk. RAID5 uses striping. So any particular file is spread across all the disks of the array. You have two choices here: 1) you can create identical non-RAID partitions on each disk for **[font=courier]/boot[/font]** and manually keep them in sync, or 2) you can use a RAID1 partition; the RAID software will keep them in sync for you. The latter is really the way to go. Note that I didn't list a third option which is to put **[font=courier]/boot[/font]** on only one disk. This really isn't an option in my opinion. Why do RAID and then leave this as a single point of failure?

Root will be on a RAID5 partition when we're all done. If you don't want to use RAID5 for your system installation, then this guide isn't for you. You may find it useful. But there are other sources that are more specific to your situation.

Once you decide on what your partitions will be, you need to decide what size to make them. Opinions vary on this as well. There is general agreement that **[font=courier]/boot[/font]** can be realtively small. A hundred megabytes is enough to hold three or four versions of the kernel. I've observed that the base system requires approximately 2.25GB. So if you put it all in the root partition, you need at least that. But, of course, you'll want some room for growth.

Here are my partitions and their sizes:
[list]
[*]/boot (128 MB)
[*]/ (10 GB)
[*]/usr (20 GB)
[*]/var (20 GB)
[*]/tmp (10 GB)
[*]swap (16 GB)
[*]/home (what's left)
[/list]
Here are some of my thoughts on the decisions I made:
[list]
[*]I have five 500 GB disk drives. So, on average, none of the system partitions are large. But they are definitely large enough for growth.
[*]Most add-on software will be installed in **[font=courier]/usr[/font]**, so it should be larger than the root.
[*]I wanted to provide ample room for system temporary storage, so I decided to make **[font=courier]/var[/font]** larger than perhaps it really needs to be.
[*]There are some heated arguments about how large swap should be. Many will argue that a GB is more than enough. I simply used the old rule of thumb that says it should be twice the size of your RAM. It could easily be with 8 GB of RAM, mine will never get used!
[/list]
There is an argument for leaving a little unused space on each drive, maybe about 5% of the drive, to account for slightly smaller drives added to the array at a later time. For example, let's say you start with some 500GB drives which are actually 502GB (manufacturers round the numbers). You set up your partitions to consume the entire disk. Then in a couple of years you decide to expand your array. The exact drives you previously purchased are no longer available, so you buy a different model advertised as 500GB, but it's actual size is 497GB. You can't make the partitions exactly the same on the new drive; it's not big enough. If you'd left 5% (10GB) unused, then you could. I agree with this reasoning. But there are other factors. In my case, I have a 16GB swap partition that I would not need to create on the new drive. There is really no need to have another spare. Also, I wouldn't have to include space to expand any of my system partitions. Having them on five drives is enough. So it all depends. You should think through these issues as you decide how to set up your partitions.

A little more discussion on swap. Some will argue that you don't need to put swap on a RAID partition. The basis for the argument is that it's the most transient of all your data. But the other side of the argument is that if you don't put swap on RAID and you lose the disk where swap is, or one of multiple disks when swap is on multiple disks, your system will crash. So again, to me it doesn't make sense to have this single point of failure. My swap is on a RAID1 partition. Why RAID1? Why not RAID5? Overall, performance for swap is a little better with RAID1. (I actually, set up the partition as RAID1 on two drives with the other three drives as spares.) The point about performance is open to debate. But I believe that the read:write ratio is closer to 1:1 for swap than most other types of data. For example, if you have a media server, you'd typically write a media file once, but then read it many times. For swap, it's only used when RAM is full. So it seems logical if the system finds it needs to read something from swap, it probably also needs to write something out to swap to make room in RAM. Write performance is better with RAID1 than with RAID5. So the closer the read:write ratio gets to 1:1, the better RAID1 will perform compared to RAID5.

Before leaving this discussion about partitioning, I need to point out another very important aspect that should enter into your decisions. The effective size of a RAID1 partition is equal to the size of a single component partition that makes up the RAID array. If you have a 1 GB partition on two disks or on 10 disks and you create a RAID1 array will all the partitions, you have 1 GB of usable space. But this isn't the case with RAID5. Since RAID5 includes striping the effective size of the array is equal to the size of the smallest component partition times one less than the total number of component partitions. So in my case, assuming all 5 disks are in my RAID5 array, the effective size of a RAID5 partition is the size of a component partition on a single disk times 4 (5 - 1). This means in my case that when I create the partitions that will make up a RAID5 array I want to make each one-fourth the effective size of the full RAID5 partition. For example, my 10 GB root partition will be composed of five 2.5 GB partitions.

[size=+2]**Installation From CD**[/size]

With all the decisions made on partitions, it's time to start the installation of the system. The only thing you'll need is the bootable Kubuntu 7.10 alternate installation CD and a network connection.

[size=+1]***Start the installation.***[/size]
[list=1]
[*]Boot from the installation CD. You may need to change your EPROM settings to enable booting from the CD-ROM drive.
[*]Select ***Install in text mode*** when the menu comes up.
[*]Proceed with installation until you reach the partitioning menu.
[/list]
NOTE: When I say "select" in these instructions, that means use the arrow keys to move to that entry and the press ENTER.

NOTE: The steps I outline here are based on my partitioning decisions. If you're setting up different partitions, you'll need to make adjustments. If your partitions are different sizes, then adjust the sizes. If you have fewer partitions or more partitions, then adjust the names of the devices accordingly.

[size=+1]***Configure partitions.***[/size]
[list=1]
[*]Select ***Manual partioning*** at the partitioning menu. The screen will show some instructions at the top and display your drives. The drive display should be similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS

```
[*]Select ***SCSI1*** in the list of drives.
[*]It will ask if you want to create a new empty partition table on the device. Select ***Yes***. It will return you to the menu and the drive display should be similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
        pri/log  500.1 GB       FREE SPACE
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS

```
[*]Select the line that begins ***pri/log ...*** to start creating the **[font=courier]/boot[/font]** partition.
[*]It will ask if you want to create a new partition. Select ***Yes***.
[*]It will ask for the size of the partition. Enter ***128mb***.
[*]It will ask for the type for the new partition. Select ***Primary***.
[*]It will ask for the location for the new partition. Select ***Beginning***.
[*]It will present default settings for the partition. Select the ***Use as*** line.
[*]It will present a list of partition types. Select ***physical volume for RAID***.
[*]It will return to the previous menu. Select ***Bootable flag***. This will set the bootable flag to ***on***.
[*]Select ***Done setting up the partition***. It will return to the list of drives and it should now be similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
        pri/log  500.1 GB       FREE SPACE
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS

```
[*]Select the line that begins ***pri/log ...*** again to start creating what will eventually be the root partition.
[*]It will ask if you want to create a new partition. Select ***Yes***.
[*]It will ask for the size of the partition. Enter ***2.5gb***.
[*]It will ask for the type for the new partition. Select ***Logical***.
[*]It will ask for the location for the new partition. Select ***Beginning***.
[*]It will present default settings for the partition. Select the ***Use as*** line.
[*]It will present a list of partition types. Select ***physical volume for RAID***.
[*]It will return to the previous menu. Select ***Done setting up the partition***. It will return to the list of drives and it should now be similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
        pri/log  500.1 GB       FREE SPACE
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS

```
[*]Now that you've created a couple partitions, you should know how to do it. Create four more **logical** partitions in the same manner. The sizes are 5GB, 5GB, 2.5GB and 16GB in that order. These will become the **[font=courier]/usr[/font]**, **[font=courier]/var[/font]**, **[font=courier]/tmp[/font]** and **[font=courier]swap[/font]** partitions, respectively.
[*]Now create the last partition. This will eventually be the **[font=courier]/home[/font]** partition. But right now it will be used as a temporary root partition. Select the line that begins ***pri/log ...*** to start.
[*]It will ask if you want to create a new partition. Select ***Yes***.
[*]It will present all the remaining free space as the size for the partition. Press ENTER to use that size.
[*]It will ask for the type for the new partition. Select ***Logical***.
[*]It will ask for the location for the new partition. Select ***Beginning***.
[*]Set ***Use as*** to ***Ext3***.
[*]Set ***Mount point*** to **[font=courier]/[/font]**.
[*]Select ***Done setting up the partition***. It will return to the list of drives and it should now be similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   f ext3       /
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS

```
[*]Now repeat this entire process for each of the remaining drives with the following exception: Make the last (very large) partition on each drive a ***physical volume for RAID*** partition. This will set the type correctly for later on when the RAID array is created. All the other partitions should be set up identically to the first drive. When you are done the list of drives and partitions should look similar to this:
```

SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   f ext3       /
SCSI2 (0,0,0) (sdb) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   K raid
SCSI3 (0,0,0) (sdc) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   K raid
SCSI4 (0,0,0) (sdd) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   K raid
SCSI5 (0,0,0) (sde) - 500.1 GB ATA ST3500320AS
     #1 primary  131.6 MB B K raid
     #5 logical    2.5 GB   K raid
     #6 logical    5.0 GB   K raid
     #7 logical    5.0 GB   K raid
     #8 logical    2.5 GB   K raid
     #9 logical   16.0 GB   K raid
    #10 logical  469.0 GB   K raid

```
[*]Review the partition configuration to this point and be sure it is as you want.
[*]Now it's time to configure the RAID1 partitions for **[font=courier]/boot[/font]** and **[font=courier]swap[/font]**. Select ***Configure software RAID***. The menu selection is above the list of drives and partitions.
[*]It will ask if you want to write the changes to the devices and configure software RAID. Select ***Yes***. It will create the Ext3 filesystem for the root partition. This may take a minute or so because the partition is large.
[*]When it's done it will present the menu for configuring RAID. Select ***Create MD device***.
[*]Select ***RAID1*** as the multidisk device type.
[*]Set the number of active devices for the RAID1 array to ***5***.
[*]Set the number of spare devices for the RAID1 array to ***0***.
[*]It will now present a list of all the mapped devices for the partitions you created and ask which ones you want to be the active devices in the RAID array. Select ***/dev/sda1***, ***/dev/sdb1***, ***/dev/sdc1***, ***/dev/sdd1*** and ***/dev/sde1***. Use the arrow keys to move in the list. Use the space bar to select a list entry.
[*]When you've selected the correct devices, press ENTER.
[*]It will return to the menu for configuring RAID. Select ***Create MD device***.
[*]Select ***RAID1*** as the multidisk device type.
[*]Set the number of active devices for the RAID1 array to ***2***.
[*]Set the number of spare devices for the RAID1 array to ***3***.
[*]It will now present a list of the mapped devices for the partitions you created and ask which ones you want to be the active devices in the RAID array. (NOTE: I found that some of the devices I put in the first array were not in the list, but others were. Don't be concerned about that.) Select ***/dev/sda9*** and ***/dev/sdb9*** and press ENTER.
[*]It will present the list again and ask which ones you want to be the spare devices in the RAID array. Select ***/dev/sdc9***, ***/dev/sdd9*** and ***/dev/sde9***.
[*]It will return to the menu for configuring RAID. Select ***Finish***.
[*]It will return to the partitioning menu and the list of drives and partitions should look similar to this:
```

RAID1 device #0 - 131.5 MB Software RAID device
      #1 131.5 MB
RAID1 device #1 - 16.0 GB Software RAID device
      #1  16.0 GB
SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
... << the rest of the list of drives and partitions will follow >>

```
[*]Select the line that reads ***#1 131.5 MB***.
[*]Set ***Use as*** to ***Ext3 journaling file system*** and ***Mount point*** to **[font=courier]/boot[/font]**. Leave the rest of the settings on default values. Select ***Done setting up the partition***.
[*]It will return to the list of drives and partitions. Select the line that reads ***#1 16.0 GB*** (the line under RAID device #1).
[*]Set ***Use as*** to ***swap area***.
[*]Select ***Done setting up the partition***.
[*]It will return to the list of drives and partitions. It should now look similar to this:
```

RAID1 device #0 - 131.5 MB Software RAID device
      #1 131.5 MB   F ext3       /boot
RAID1 device #1 - 16.0 GB Software RAID device
      #1  16.0 GB   f swap       swap
SCSI1 (0,0,0) (sda) - 500.1 GB ATA ST3500320AS
... << the rest of the list of drives and partitions will follow >>

```
[*]Partitioning is now done! Select ***Finish partitioning and write changes to disk***.
[*]It will ask if you want to write the changes to disk. Select ***Yes***.
[*]It will format the RAID partitions and then the installation will continue.
[/list]

[size=+1]***Finish the installation.***[/size]

Follow the prompts and complete the remainder of the installation. When it reaches the end, it will eject the CD. Remove the CD, close the tray, and reboot. It should boot into the OS. At this point, you've installed GRUB, the boot loader, and the kernel on the very small RAID1 array at the beginning of the disk and everything else temporarily on the large partition on the first disk. **[font=courier]swap[/font]** is on the other RAID1 array that was configured. You have a working system!

[size=+2]**Reconfiguration for RAID5**[/size]

Now that the initial installation is complete and you have a complete system installed, it can be reconfigured to put the system on RAID5 arrays. This process involves setting up the arrays, copying system files into place, and doing some reconfiguration of the startup process.

[size=+1]***Log in and look around.***[/size]

You can now log in as the user you set up during the installation process. Besides root, that is the only user. And by default, root isn't allowed to log in. So start by logging in and bringing up the desktop. First, get familiar with the initial configuration.

[list=1]
[*]Open a *Konsole* window. Click the icon in the lower left corner of the screen. Go to ***System*** --> ***Konsole***. You can resize the *Konsole* window by dragging the edges with a mouse. All the commands in this guide are entered in a *Konsole* window.
[*]In the *Konsole* window, enter ***cat /proc/mdstat***. This will show you the status of the current RAID arrays. Remember this command. You'll use it quite a bit. The output should be similar to this:
```

root@ubuntu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda9[0] sde9[4](S) sdd9[3](S) sdc9[2](S) sdb9[1]
      15623104 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sde1[4] sdd1[3] sdc1[2] sdb1[1]
      128384 blocks [5/5] [UUUUU]

unused devices: <none>
root@ubuntu:~# 

```
The *U* letters at the end of the second line of each array indicate how many component partitions are up and running. The *S* in parens indicates a spare.
[*]Enter ***mount***. This will show you the file systems which are mounted. You should see something like this:
```

root@ubuntu:~# mount
/dev/sda10 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/md0 on /boot type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
root@ubuntu:~# 

```
The **[font=courier]swap[/font]** partition isn't in the above list because it isn't a mounted file system. You can take a look at **[font=courier]swap[/font]** by entering ***cat /proc/swaps***. You'll see something like this:
```

root@ubuntu:~# cat /proc/swaps
Filename                    Type            Size      Used    Priority
/dev/md1                    partition       15623096     0      -1
root@ubuntu:~# 

```
[/list]

[size=+1]***Create the RAID5 partitions.***[/size]

The first step to reconfigure the system for RAID5 is to create the RAID partitions that will hold the system files.

NOTE: All the commands I present here need to be run as root. You will need to preface each one with ***sudo*** ("switch user and do") to run it as root. Personally, I think it gets to be a real pain using ***sudo*** and needing to enter a password occasionally. I prefer to simply switch user to root. Yes, it may be a little more dangerous. But it has never been an issue for me. I don't normally do work as root, just system admin work and then I exit the root shell. If you want to be able to switch user to root, you need to give the root account a password. You can do this with the command ***sudo passwd***. It will prompt you for the password to set. Once you've set the password you can become root any time with ***su -*** and entering the root password. This will open a new shell. You can exit the shell by entering the ***exit*** command.

[list=1]
[*]Create the RAID5 array for the **[font=courier]root[/font]** partition with the following command:
```

root@ubuntu:~# mdadm --create --verbose /dev/md2 --level=5 --raid-devices=5 /dev/sda5 /dev/sdb5 /dev/sdc5 /dev/sdd5 /dev/sde5
mdadm: layout details to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 2441728K
mdadm: array /dev/md2 started
root@ubuntu:~# 

```
[*]Create three more RAID5 arrays for **[font=courier]/usr[/font]**, **[font=courier]/var[/font]** and **[font=courier]/tmp[/font]**.
```

root@ubuntu:~# mdadm --create --verbose /dev/md3 --level=5 --raid-devices=5 /dev/sda6 /dev/sdb6 /dev/sdc6 /dev/sdd6 /dev/sde6
...

root@ubuntu:~# mdadm --create --verbose /dev/md4 --level=5 --raid-devices=5 /dev/sda7 /dev/sdb7 /dev/sdc7 /dev/sdd7 /dev/sde7
...

root@ubuntu:~# mdadm --create --verbose /dev/md5 --level=5 --raid-devices=5 /dev/sda8 /dev/sdb8 /dev/sdc8 /dev/sdd8 /dev/sde8
...


```
[*]Wait until the arrays are completely built before creating the file systems. You can watch the progress with the command ***cat /proc/mdstat***. There will be a progress meter and percentage to indicate how far along it is. I don't have a specific example to show. But it is easily discerned from the display.
[*]When all the "recovery" is complete, it is time to create the file systems on the RAID partitions.
```

root@ubuntu:~# mkfs -t ext3 /dev/md2
<< usual output from mkfs >>

root@ubuntu:~# 

```
I don't have example output from **[font=courier]mkfs[/font]**.
[*]Repeat the command for ***/dev/md3***, ***/dev/md4*** and ***/dev/md5***.
[*]Now update **[font=courier]mdadm.conf[/font]** to retain the RAID configuration when the system restarts. Be sure you are in a non-system directory (root's home directory is fine) and run this command:
```

root@ubuntu:~# mdadm --detail --scan > mdadm.new
root@ubuntu:~# 

```
[*]Open **[font=courier]/etc/mdadm/mdadm.conf[/font]** in your chosen text editor. Find the lines that begin with "ARRAY" and comment them out. NOTE: In my version, the definition for the md1 array was on two lines.
[*]Open the **[font=courier]mdadm.new[/font]** file you just created and copy all the lines from that file into **[font=courier]/etc/mdadm/mdadm.conf[/font]** immediately after the lines you commented out. After the changes, it should look similar to this:
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid1 num-devices=5 UUID=4af98750:2c546770:e0a38126:d70ed490
#ARRAY /dev/md1 level=raid1 num-devices=2 UUID=17f37a2d:96cbe834:401bc8f3:e3b6fa3e
#   spares=3
ARRAY /dev/md0 level=raid1 num-devices=5 UUID=4af98750:2c546770:e0a38126:d70ed490
ARRAY /dev/md1 level=raid1 num-devices=2 spares=3 UUID=17f37a2d:96cbe834:401bc8f3:e3b6fa3e
ARRAY /dev/md2 level=raid5 num-devices=5 UUID=e22c986f:e0013765:f9935161:a927a204
ARRAY /dev/md3 level=raid5 num-devices=5 UUID=26600050:a9781133:f9935161:a927a204
ARRAY /dev/md4 level=raid5 num-devices=5 UUID=05d53ed8:1c2918a8:f9935161:a927a204
ARRAY /dev/md5 level=raid5 num-devices=5 UUID=f359ace2:fd8582ba:f9935161:a927a204

# This file was auto-generated on Mon, 04 Feb 2008 01:55:40 +0000
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $

```
[*]Save the changes to **[font=courier]/etc/mdadm/mdadm.conf[/font]**.
[*]At this point I suggest you reboot. This isn't necessary. But I like to reboot occaisionally to be sure that changes I've made work as expected. If you wait too long before a reboot and things don't work as you expect, you have a lot more changes to investigate.
[*]After you reboot, log in, and check **[font=courier]/proc/mdstat[/font]**. You should see all the RAID arrays as active.
[/list]

[size=+1]***Restructure the installed OS.***[/size]

Now that the RAID5 arrays for the system are configured and active it is time to move the different parts of the system to the arrays. Actually, we're going to copy them. The currently booted system will remain until we know the system will boot and run from the RAID arrays.

[list=1]
[*]Copy the root file system to it's new home. Mount the md2 array. Enter:
```

root@ubuntu:~# mount /dev/md2 /mnt
root@ubuntu:~# 

```
[*]Use **[font=courier]rsync[/font]** to copy all the files. Enter:
```

root@ubuntu:~# rsync -daHv --exclude=proc/* --exclude=sys/* --exclude=boot/* --exclude=usr/* --exclude=var/* --exclude=tmp/* --exclude=mnt/* / /mnt
<< list of files copied >>

root@ubuntu:~# 

```
It will list the files as they are copied. The **[font=courier]proc[/font]** and **[font=courier]sys[/font]** directory are in-memory file systems created by the kernel; they don't need to be copied; in fact, they can't be copied. The **[font=courier]boot[/font]**, **[font=courier]usr[/font]**, **[font=courier]var[/font]** and **[font=courier]tmp[/font]** directories will each be their on own file systems (we'll do those next). We can't recursively copy the **[font=courier]mnt[/font]** directory (it's the destination); so it is excluded. NOTE: If you want to see what it will copy without actually doing the copy, include the "-n" option.
[*]When **[font=courier]rsync[/font]** is done, unmount the file system. Enter:
```

root@ubuntu:~# umount /mnt
root@ubuntu:~# 

```
[*]Next we'll copy the **[font=courier]/usr[/font]** directory to its own file system. Mount the md3 array. Enter:
```

root@ubuntu:~# mount /dev/md3 /mnt
root@ubuntu:~# 

```
[*]Copy it. Enter:
```
root@ubuntu:~# rsync -daHv /usr/ /mnt
<< list of files copied >>

root@ubuntu:~# 

```
NOTE: Do **NOT** forget the trailing slash after **[font=courier]/usr[/font]**! This tells **[font=courier]rsync[/font]** to copy all files and directories **under** **[font=courier]/usr[/font]**, not **[font=courier]/usr[/font]** itself. If you leave off the trailing slash it will create a **[font=courier]usr[/font]** directory in **[font=courier]/mnt[/font]** and you don't want that.
[*]When **[font=courier]rsync[/font]** is done, unmount the file system. Enter:
```

root@ubuntu:~# umount /mnt
root@ubuntu:~# 

```
[*]Next we'll copy the **[font=courier]/var[/font]** directory to its own file system. Mount the md4 array. Enter:
```

root@ubuntu:~# mount /dev/md4 /mnt
root@ubuntu:~# 

```
[*]Copy it. Enter:
```

root@ubuntu:~# rsync -daHv /var/ /mnt
<< list of files copied >>

root@ubuntu:~# 

```
[*]When **[font=courier]rsync[/font]** is done, unmount the file system. Enter:
```

root@ubuntu:~# umount /mnt
root@ubuntu:~# 

```
[*]The **[font=courier]/tmp[/font]** directory does not need to be copied since it contains only transient files. But the permissions on the mount point must be set correctly. To do that, enter the following commands:
```

root@ubuntu:~# mount /dev/md2 /mnt
root@ubuntu:~# mount /dev/md5 /mnt/tmp
root@ubuntu:~# chmod 01777 /mnt/tmp
root@ubuntu:~# umount /mnt/tmp
root@ubuntu:~# 

```
Note that we left **[font=courier]/dev/md2[/font]** mounted. We're going to make some changes to it.
[*]The last thing to do in the restructuring part is to update **[font=courier]/etc/fstab[/font]** so the new file systems are automatically mounted. We'll do this to the mounted **[font=courier]/dev/md2[/font]** file system and leave the original installed version alone.
[list=a]
[*]Edit **[font=courier]/mnt/etc/fstab[/font]**.
[*]Find the line where **[font=courier]/dev/sda10[/font]** is mounted.
[*]Copy that line and paste the copy right below it.
[*]Comment out the original.
[*]In the pasted line change the string **[font=courier]UUID=[long alphanumeric string][/font]** with **[font=courier]/dev/md2[/font]**.
[*]Make a copy of the line you just changed.
[*]Paste the copy under the line where **[font=courier]/boot[/font]** is mounted.
[*]In the pasted line change **[font=courier]/dev/md2[/font]** to **[font=courier]/dev/md3[/font]** and the mount point from **[font=courier]/[/font]** to **[font=courier]/usr[/font]**.
[*]Make a copy of the line you just changed and paste it right below that line.
[*]In the pasted line change **[font=courier]/dev/md3[/font]** to **[font=courier]/dev/md4[/font]** and the mount point from **[font=courier]/usr[/font]** to **[font=courier]/var[/font]**.
[*]Make a copy of the line you just changed and paste it right below that line.
[*]In the pasted line change **[font=courier]/dev/md4[/font]** to **[font=courier]/dev/md5[/font]** and the mount point from **[font=courier]/var[/font]** to **[font=courier]/tmp[/font]**.
[*]Save the changes. The new version should look similar to this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda10
#UUID=2420f84c-8f9e-4021-a0e8-f02ee91b2853 /               ext3    defaults,errors=remount-ro 0       1
/dev/md2        /               ext3    defaults,errors=remount-ro 0       1
# /dev/md0
UUID=929843f5-3001-4b78-bf87-28ae3636d4b5 /boot           ext3    defaults        0       2
/dev/md3        /usr            ext3    defaults,errors=remount-ro 0       1
/dev/md4        /var            ext3    defaults,errors=remount-ro 0       1
/dev/md5        /tmp            ext3    defaults,errors=remount-ro 0       1
# /dev/md1
UUID=275a7465-da22-4a0e-be3d-785bbeb7f51f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
[/list]
[/list]

[size=+1]***Update GRUB to boot from RAID.***[/size]

Because we installed the root file system on a non-RAID partition, the kernel that is booted doesn't have RAID support. The RAID support is a module that must be included in the **[font=courier]initrd.img[/font]** file in **[font=courier]/boot[/font]** to allow the root partition to reside on a RAID array. The **[font=courier]initrd.img[/font]** is built by the installer. And if the root partition isn't on a RAID array, the installer doesn't include the module. So we need to add the module now.

The **[font=courier]update-initramfs[/font]** command is used to do the work. It uses **[font=courier]/etc/fstab[/font]** to determine if RAID support is needed. So we need to put the new **[font=courier]fstab[/font]** in place to run the command. Here is the procedure:
[list=1]
[*]Change directory. Enter:
```

root@ubuntu:~# cd /etc
root@ubuntu:/etc# 

```
[*]Save the current file. Enter:
```

root@ubuntu:/etc# mv fstab fstab.save
root@ubuntu:/etc# 

```
[*]Put the modified file in place. Enter:
```

root@ubuntu:/etc# cp /mnt/etc/fstab .
root@ubuntu:/etc# 

```
That dot at the end is part of the command!
[*]Update **[font=courier]initrd.img[/font]**. Enter:
```

root@ubuntu:/etc# update-initramfs -u
root@ubuntu:/etc# 

```
[*]Restore the original **[font=courier]fstab[/font]**. Enter:
```

root@ubuntu:/etc# mv fstab.save fstab
root@ubuntu:/etc# 

```
[/list]
Now we need to update the GRUB menu so it will know how to load the root file system from the RAID array.
[list=1]
[*]Open **[font=courier]/boot/grub/menu.lst[/font]** in your editor.
[*]Find the menu at the end of the file.
[*]Copy the first two menu entries; the first one is 5 lines, the second is 4 lines.
[*]Paste the copy right before its current location.
[*]In the **[font=courier]kernel[/font]** line of each of the first two entries (the ones you just created), replace the string **[font=courier]UUID=[long alphanumeric string][/font]** with **[font=courier]/dev/md2[/font]**. This tells GRUB that the root partion is on md2.
[*]On the two original entries (now the third and fourth entries), append "(non-RAID)" to the title line. When the menu displays, you'll be able to tell which ones will boot from original installation.
[*]While you're editing this file, find the line near the top that begins **[font=courier]# kopt=root[/font]**. Change the string **[font=courier]UUID=[long alphanumeric string][/font]** to **[font=courier]/dev/md2[/font]**. This line, which is commented out with just a single sharp, defines the options to put on the kernel line in the menu when the menu is updated. If you don't change it and then later apply an update that needs to update the GRUB menu, your system won't boot anymore! I was bitten by this one and it took a while to determine what happened.
[*]Save the changes. The menu should look similar to this:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/md2 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/md2 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (non-RAID)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=2420f84c-8f9e-4021-a0e8-f02ee91b2853 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (non-RAID)
root            (hd0,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=2420f84c-8f9e-4021-a0e8-f02ee91b2853 ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
quiet

```
[/list]
Note that we have left the existing installation in place. The only changes we've made to it's original pristine condition is we configured the RAID arrays and changed **[font=courier]mdadm.conf[/font]** to start them. And if you rebooted after those changes, then you know it will still boot.

Why is this important? If you have a typo or other mistake in the restructuring of the OS, it may not boot. If this is the case, then you can still boot the original installation and use it to troubleshoot the problem. We'll remove it later when we are more confident that the RAID installation is working.

[size=+1]***Reconfigure when the RAID daemon is started.***[/size]

By default, when the system starts up, it doesn't start the **[font=courier]mdadm[/font]** daemon until it goes into its final run level. If you don't know about run levels and want to learn, you can find plenty of sources on the web. Here's one  _[explanation](http://www.linux.com/articles/114107)_.

I don't want to attempt to explain the entire start up process here. But here's a quick overview:
[list]
[*]After the system boots, and near the end of the startup process, it runs the scripts in the **[font=courier]/etc/rcS.d[/font]** directory.
[*]Then it runs the scripts in the **[font=courier]/etc/rcX.d[/font]** directory, where X is the run level. For example, if it's going to run level 5, it runs the scripts in **[font=courier]/etc/rc5.d[/font]**.
[*]The scripts in these directories begin with either a K or an S. K means "kill". S mean "start". After the K or S is a two-digit number. The number determines the order for the scripts to run.
[*]When a run level is entered, the kill scripts for that level are run and then the start scripts for that level are run.
[/list]
If you look at your system, you'll see that there is a **[font=courier]/etc/rc1.d/K25mdadm[/font]** script. This means **[font=courier]mdadm[/font]** will be killed when entering run level 1 (single-user mode). There is an **[font=courier]S25mdadm[/font]** script for run levels 2 thru 5. This means **[font=courier]mdadm[/font]** will be started when each of those run levels is entered. The problem is that is too late. By then the system has mounted the file systems in **[font=couriermdadm]fstab[/font]** and it can't mount the file systems on RAID arrays if the arrays aren't active!

We need to change the scripts so the **[font=courier]mdadm[/font]** daemon is started earlier and is always running no matter what run level we're in. This isn't difficult to do. We just need to remove the **[font=courier]mdadm[/font]** related scripts from all the **[font=courier]rcX.d[/font]** directories, where X is 1 thru 5, and add a script to **[font=courier]rcS.d[/font]**. Here are the commands:
```

root@ubuntu:~# cd /mnt/etc/rcS.d
root@ubuntu:/mnt/etc/rcS.d# ln -s ../init.d/mdadm S25mdadm
root@ubuntu:/mnt/etc/rcS.d# cd ..
root@ubuntu:/mnt/etc# rm rc1.d/K25mdadm
root@ubuntu:/mnt/etc# rm rc2.d/S25mdadm
root@ubuntu:/mnt/etc# rm rc3.d/S25mdadm
root@ubuntu:/mnt/etc# rm rc4.d/S25mdadm
root@ubuntu:/mnt/etc# rm rc5.d/S25mdadm

```

One final thing on the startup of the **[font=courier]mdadm[/font]** daemon. The script that starts the daemon stores its process ID in a file under **[font=courier]/var[/font]**. But the way we have things configured, **[font=courier]/var[/font]** is on its own RAID array and is not mounted when the **[font=courier]mdadm[/font]** daemon starts! So we'll change it so the file with the process ID is in **[font=courier]/etc[/font]**. This isn't ideal, but it will work.

Edit **[font=courier]/mnt/etc/init.d/mdadm[/font]**. Find the definition for **[font=courier]RUNDIR[/font]** and change it to **[font=courier]/etc/mdadm[/font]**. That is the directory where **[font=courier]mdadm.conf[/font]** is located. Save the changes.

NOTE: If you have **[font=courier]/var[/font]**, **[font=courier]/tmp[/font]** and **[font=courier]/usr[/font]** on your root partition, you can skip this whole section. It should work with the default configuration.

[size=+1]***Reboot to the RAID5 system!***[/size]

Unmount the file system from **[font=courier]/mnt[/font]** and reboot. Enter:
```

root@ubuntu:/mnt/etc# cd
root@ubuntu:~# umount /mnt
root@ubuntu:~# reboot

```
When it comes back up you'll be running Kubuntu from the RAID5 arrays!

[size=+2]**Move [font=courier]/home[/font] to RAID5 and Clean Up**[/size]

Almost done! The last major step is to create the final RAID5 partition for the **[font=courier]/home[/font]** file system. This will destroy the original system installation.

[size=+1]***Change the partition type.***[/size]

The first step is to change the type of the partition to "Linux raid autodetect". This is only necessary on the partition where the original installation was placed. The corresponding partitions on the other disks were set to the correct type during installation.

[list=1]
[*]Use **[font=courier]fdisk[/font]** to change the partition type. Enter ***fdisk /dev/sda***
[*]It will probably warn that your disk is rather large and then prompt **[font=courier]Command (m for help): [/font]** Enter ***t***
[*]It will prompt **[font=courier]Partition number (1-10): [/font]** Enter ***10***. Depending on how you partitioned your disks during installation, you may have a different number of partitions. You need to enter the number of the partition where the original root partition was installed.
[*]It will prompt **[font=courier]Hex code (type L to list codes): [/font]** Enter ***fd***
[*]It will prompt **[font=courier]Command (m for help): [/font]** Enter ***w***. It will save the changes and exit. Here's what it should all look like:
```

root@ubuntu:~# fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Partition number (1-10): 10
Hex code (type L to list codes): fd
Command (m for help): w
root@ubuntu:~# 

```
[*]Reboot the system so the kernel will load the new partition table from the disk.
[/list]

[size=+1]***Create the RAID array.***[/size]

Now it's time to create the final RAID5 array and its file system.
[list=1]
[*]Create the RAID5 array for **[font=courier]/home[/font]** with the following command:
```

root@ubuntu:~# mdadm --create --verbose /dev/md6 --level=5 --raid-devices=5 /dev/sda10 /dev/sdb10 /dev/sdc10 /dev/sdd10 /dev/sde10
mdadm: /dev/sda10 appears to contain an ext2fs file system ...
Continue creating array? yes<ENTER>
mdadm: layout details to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 45798086K
mdadm: array /dev/md6 started
root@ubuntu:~# 

```
You need to enter "yes" at the prompt to continue.
[*]Check **[font=courier]/proc/mdstat[/font]** occasionally to check on the progress building the array. This will take a while. For my 469GB partitions, it took almost 3 hours!
[*]When all the "recovery" is complete, create the file system. Enter:
```

root@ubuntu:~# mkfs -t ext3 /dev/md6
<< usual output from mkfs >>

root@ubuntu:~# 

```
[/list]

[size=+1]***Copy the files.***[/size]

We need to copy the files from the existing **[font=courier]/home[/font]** directory to the new file system.
```

root@ubuntu:~# mount /dev/md6 /mnt
root@ubuntu:~# rsync -daHv /home/ /mnt
<< list of files copied >>

root@ubuntu:~# umount /mnt
root@ubuntu:~# 

```

[size=+1]***Update configuration.***[/size]

Now we'll update the configuration so the array is started and the file system mounted when rebooting.
[list=1]
[*]Be sure you're in a safe directory, e.g. root's home. Enter:
```

root@ubuntu:~# mdadm --detail --scan > mdadm.new
root@ubuntu:~# 

```
[*]Edit **[font=courier]/etc/mdadm/mdadm.conf[/font]**.
[*]Get the line for **[font=courier]/dev/md6[/font]** from **[font=courier]mdadm.new[/font]** and paste it at the end of **[font=courier]/etc/mdadm/mdadm.conf[/font]**.
[*]Save the changes.
[*]Edit **[font=courier]/etc/fstab[/font]**.
[*]Find the line for **[font=courier]/dev/md5[/font]**. Copy it.
[*]Paste the copy right below the original.
[*]In the copy change **[font=courier]/dev/md5[/font]** to **[font=courier]/dev/md6[/font]** and **[font=courier]/tmp[/font]** to **[font=courier]/home[/font]**.
[*]Save the changes.
[/list]

[size=+1]***Clean up.***[/size]

There are a few things to clean up now that the installation is complete. Remove a few files that have been copied and clean up configuration files. We'll do some of it from single-user mode.
[list=1]
[*]Reboot the system. When the message **[font=courier]GRUB loading, please wait[/font]** comes up, hit ***ESC*** to get the boot menu.
[*]Select the second entry for "recovery mode", and press ENTER to boot.
[*]When it prompts for the root password for mainenance, enter it.
[*]Enter the following commands:
```

root@ubuntu:~# umount /tmp
root@ubuntu:~# rm -rf /tmp/*
root@ubuntu:~# mount /tmp
root@ubuntu:~# umount /home
root@ubuntu:~# rm -rf /home/*
root@ubuntu:~# mount /home
root@ubuntu:~# init 5

```
These command remove all the files in the **[font=courier]/tmp[/font]** and **[font=courier]/home[/font]** directories in the root file system. They are no longer needed; they are on the mounted file systems. The last command will continue booting to the GUI.
[*]Edit **[font=courier]/etc/fstab[/font]** and remove the original commented out entry for **[font=courier]/dev/sda10[/font]**. It is no longer valid. I also suggest changing the entries for **[font=courier]/dev/md0[/font]** and **[font=courier]/dev/md1[/font]** to use the device names instead of the UUIDs. But this is up to you. Here's what my final **[font=courier]/etc/fstab[/font]** looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md2        /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /boot           ext3    defaults        0       2
/dev/md3        /usr            ext3    defaults,errors=remount-ro 0       1
/dev/md4        /var            ext3    defaults,errors=remount-ro 0       1
/dev/md5        /tmp            ext3    defaults,errors=remount-ro 0       1
/dev/md6        /home           ext3    defaults,errors=remount-ro 0       1
/dev/md1        none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```
[*]Edit **[font=courier]/etc/mdadm/mdadm.conf[/font]** and remove the commented out array defintions.
[*]Edit **[font=courier]/boot/grub/menu.lst[/font]** and remove the menu entries for the non-raid boot options. These are no longer valid.
[/list]

[size=+2]***What's Left?***[/size]

That's it, The installation is complete. However, at this point you should do some testing of your RAID arrays. You can fail different partitions and insure that the arrays continue to function in degraded mode. Then you can bring the partitions back and insure they are recovered. Also, you should set up **[font=courier]mdadm[/font]** to report status. You need to be aware if you have a failure. One failure on a RAID5 array is recoverable. But two simultaneously is not!

I hope you've found this guide to be helpful. If your configuration isn't exactly like mine, at least this may get you started on your way to a successful RAID5 installation.

---

### Post by SloYerRoll on 2008-03-08
Hey LNK. I came here from TOTW just to check out your writeup. I want to say you did a superb job! 

Keep up the great work!

All the best,

---

### Post by kevdog on 2008-03-09
That might be the most thorough tutorial Ive ever skimmed -- it started getting long.

This is for a RAID5 software RAID setup, not hardware -- I noticed no RAID5 controller setup in your hardware statement.

I would recommend making the size of your /boot partition bigger.  If you ever manually compile a vanilla kernel and install it, it might not fit.  Ive run into problems with this before.  With all the space you have, I wouldn't hesitate about quadrupling the size of the /boot partition. -- Just my opinion.

Stellar writeup

---

### Post by LNK on 2008-03-25
Thanks for the comments!

Yes, this is definitely for software RAID. On the size of the boot partition, I agree that it could easily be larger. In my case, my server should be very stable and I won't need too many kernel versions. But it's excellent advice to others who may be setting up a system. There isn't any good reason to be too frugal about space when you have plenty to use. If you're going to be doing anything that might require you to have several versions of the kernel leave yourself plenty of space.

I hope the tutorial has been helpful!

--Lloyd

---

### Post by maino82 on 2008-03-30
Great tutorial, and I just have one question. If something ever did happen to the array or your boot sector somehow got corrupted, how would you recover your data? I'm assuming it's not as simple as putting a liveCD in and recovering that way. I'm not very familiar with RAID, but I want to try it out and I'm just worried that if I jump into this and something goes wrong I'll have no idea where to go from there.

Thanks!

---

### Post by LNK on 2008-04-14
maino,

I must apologize for being slow to respond. I thought I was subscribed to this thread, but I wasn't. I've been busy like everyone else and didn't check back here often enough.

I think the short answer to you question is that corrupting a RAID partition is no different from corrupting a non-RAID partition. If you ask Linux to write corrupted data, it will happily do so. What I'm saying is that corruption generally occurs because of user error or an application that does something wrong. Linux won't know whether it is a bad write or not.

One of the main reasons for using multiple partitions is to prevent data corruption from spreading to your entire disk (or disk array). Generally, corruption should be confined to a single partition.

The key with RAID is monitoring the health of your array so if you have a disk exhibiting signs of failure, or an actual failure, you can replace it before you lose another. A RAID5 array will continue to operate with a single faulty drive. But losing a second one before you get the first fixed will take all your data with it.

Probably the most important thing you can do to guard against corruption is put in place a consistent backup procedure. Then when you have a corruption issue, you should only lose data back to when the corruption started, worst case. Of course, this assumes you find the corruption issue before all your backups are corrupted. People often get a sense of false security from RAID. They think because they have RAID they don't need backups. Nothing could be further from the truth. Many things can happen where you lose all the data on an array. Corruption is one of them. Natural disasters are another. If your server room, or your house, burns down around your computer, your data will most likely be gone. Do backups and store them at another location!

If you do need to deal with a corruption issue, you'll probably want to consult the forums with specifics about the issue. Many are solvable without too much effort. If you keep your OS on a partition, or partitions, separate from all your data, you can reinstall the OS without affecting your other partitions. I usually advise people to at least do that: partition the OS separate from their "user data".

Hope this helps!

--Lloyd

---

### Post by rgotten on 2008-04-19
I am trying to instal the ubuntu server edition, i am new to all this...I am using 3 500 gb hd, i am a docotr and trying to create a file server . On the cd of the server edition i create a partition for the raid 1 and another for the raid 5,why you did not create all RAID 1 and 5  at the beguining and then install the software. Sorry I am new to this and trying to learn..Thanks

Rgotten

---

### Post by LNK on 2008-04-21
Rgotten,

A very quick primer on RAID1 and RAID5, because it's essential to understand how the data is laid out on the disk drives. RAID1 is simply mirroring. It's very simple. Every partition in the RAID array is a mirror of every other partition. When a byte is written to one of the partitions, it is written to every partition. If you lose one, then all your data is on at least one other.

RAID5 is striping, for performance, plus redundancy for backup. It's much more complicated. Here's a very basic example with 3 drives, each with a partition in the array. Call the drives A, B and C. When a file is saved the first block will be written to A, the second block written to B, and then a checksum from those blocks calculated and written to C. Then the third block of the file will be written to B, the fourth block to C and the checksum of those two blocks to A, Then the fifth block will be written to C, the sixth block written to A, and the checksum of those two blocks written to B. And so on. No one drive contains all the checksum blocks. So let's say drive B goes down. When the file is read, the first block will be read from A. B isn't there so the block stored on B will be calculated on the fly using the block on A and the checksum block on C. So whenever a block needs to be read from B it is reconstructed using the corresponding blocks on A and C, one of which is the checksum.

So why do the installation like I did? The boot PROM on your computer knows nothing about RAID. All files that it needs to read to load the Linux kernel MUST be on the same drive. So it simply can't work with RAID5 where the files are striped across more than one drive. But it can work with RAID1 because each drive is an exact mirror of the others. This is why you MUST install the boot partition as either an ordinary non-RAID partition or as a RAID1 partition.

The second part of the answer is about RAID5. The installer does not adequately support RAID5. (Note: This is an educated assumption on my part which hasn't been disputed and therefore appears to be confirmed.) Thus, the installer cannot install correctly to a RAID5 partition. It appears to ignore the fact that the partition is RAID and installs to only one of the partitions that make up the RAID array. The array is never properly set up and so when the system boots and assumes it's a RAID5 array, it can't read the data. It then bombs very badly.

If all you want is redundancy for crash protection, then you can do it all as RAID1. This should work just fine. There are several guides about installing RAID1 on the Internet. The installer appears to support this just fine. I believe what it actually does is install everything to a single partition in the RAID1 array and then when the Linux kernel comes up the first time, the kernel actually constructs the mirror(s).

But if you want RAID5, then you need a way to create your RAID5 array AFTER your system is up and running so you can use the RAID5 support in the kernel. I don't see any way around this.

You can also do a hybrid where you install the entire Linux OS on RAID1 (a single array or multiple) and then use RAID5 only for your data files. This would be a simple installation.

I hope this answers you questions. If not, then ask some more and I'll try and answer them.

--Lloyd

---

### Post by rgotten on 2008-04-22
Thanks for your reply and offer to help. Your explanation has being spectacular but like i mention i am completely new into Linux, i am a doctor who is trying to build a file server to start with. At the beguining i follow multiples instructions found on the forum with Ubuntu server edition, what i did was create a raid 1 for boot with 100 mb, swap of 2gb on raid 1,  and the rest on raid 5. Like i mention all of this was done from the cd and the partitions and raid were created when the partition area came up during instalation. The system boots well, and when i did the command cat /proc/mdstat i see the 2 raid 1 and the raid 5, then i install the grub also on the second disk's (/dev/sdb) master boot record (MBR), and the third, following instructions found on this forum. everything boots well, but when i remove a hard drive to test the raid the system boots and show a busy box  that ends on initrmfs and stays there. 

Then i decided to reinstall everything and follow your instructions and make them with 3 hd that i have instead of 5. Everything went well untill "reestructure the installed os", specially when the commands "rsync -daHv /usr/ /mnt", "rsync -daHv /var/ /mnt", I receive a bunch of error and then when i did "
root@ubuntu:~# mount /dev/md2 /mnt
root@ubuntu:~# mount /dev/md5 /mnt/tmp
root@ubuntu:~# chmod 01777 /mnt/tmp
root@ubuntu:~# umount /mnt/tmp
root@ubuntu:~#
it says that is busy. I continue your instructions up to "Reconfigure when the RAID daemon is started." it boots but there appear to be a lot of errors while is butting but the it give me the option to login and password and the command prompt looks fine. Can you tell me what i am doing wrong, and if i have to start the whole procees again. Also let me ask you why did you use kubuntu instead of ubuntu server. From what i can read from your post what you are doing could be similar for what i want and trying to build (evidently, i am 100% new to linux, and cannot compare to your expertice, and has being very interesting starting to use nano or vi for editiong your instructions on how to do this...but your help will be greatly apreviated

Thanks and hope you understand my primitive understanding of linux ?(but willing to learn)
rgotten

---

### Post by LNK on 2008-04-22
Rgotten,

Let me be sure I understand something. From your explanation, my understanding is that you tried some other guides you found on the Internet before you tried the one I created. That is what I understand from the first paragraph of your reply. If this is not correct, please tell me. If I'm correct, then that part of your experience is the same as mine. The problem is that even though the installer appears to support RAID5, it doesn't really support it. The files are installed on a standard non-RAID partition. So it will boot. But if that partition goes away, like when you removed a drive, it will no longer boot.

I must say that I never tried to install the "server" version. It's possible that something is different and my guide cannot be followed exactly. But I wouldn't know what that is. I believe the server version is a subset of the desktop version, without all the GUI support primarily.

I will need to know the specific errors you received when running rsync in order to help you. It is probably something simple. But it could be any of a large number possibilities. Do you remember the errors? Are you running all the commands as "root"? If not, you'll get all kinds of "permission denied" errors.

The fact that you could not unmount /mnt/tmp at that particular point is not a major issue. I don't understand why that would be the case unless you did something extra not in the guide. Something as simple as doing a "cd" into the mounted area and leaving a shell sitting there would cause it to be busy. But if you did nothing more that what's in the guide, I don't know why it would be busy. But if you can't unmount it, just leave it mounted. The next time you reboot, it will all be take care of.

If you tried a different technique for the installation (as I assumed and explained above), you may have some issue with leftover partition tables from that previous attempt. When you start the installation over, you MUST clear out the existing partition table before reinstalling. Now, I forget exactly how to do that using the installer. But I recall at one of the menus for setting up partitions, there is a way to remove partitions. You can try that and see if it works. I know that at least once when I was rerunning the installation, I could not get it to work completely and had to wipe my disk drives to remove the partition table. This could be part of your issues, although I can't say for certain.

Wiping a disk, or zeroing a disk, isn't hard to do. But you must have a bootable system on another media, e.g. a CD. This is because you can't zero out the drive you are booted from. You must boot from a CD (or floppy, or flash drive, etc.) and then zero the hard drives. The Ubuntu "desktop" version is a bootable version. It's a completely working Linux system, GUI and all. That would be my choice.

After you've booted from a CD, you can zero the disk with this command: "dd if=/dev/zero of=/dev/hda bs=1M". After this is done, do the same for hdb and hdc. If you need more info, do an Internet search for something like "linux zero disk". After that is done, start the installation from scratch.

To answer another question, I'm running Kubuntu because I prefer the KDE desktop. No other reason. That's all that makes Kubuntu different from Ubuntu.

--Lloyd

---

### Post by rgotten on 2008-04-22
> **LNK said:**
> Rgotten,

Let me be sure I understand something. From your explanation, my understanding is that you tried some other guides you found on the Internet before you tried the one I created. That is what I understand from the first paragraph of your reply. If this is not correct, please tell me. If I'm correct, then that part of your experience is the same as mine. The problem is that even though the installer appears to support RAID5, it doesn't really support it. The files are installed on a standard non-RAID partition. So it will boot. But if that partition goes away, like when you removed a drive, it will no longer boot.

You are correct, i try other guides with no succes, and tehn i follow your instructions

> **LNK said:**
> I will need to know the specific errors you received when running rsync in order to help you. It is probably something simple. But it could be any of a large number possibilities. Do you remember the errors? Are you running all the commands as "root"? If not, you'll get all kinds of "permission denied" errors.

Well like i mention, i am comletely new to all this and doing my best, I believe i am running all the commands as a root since I am doing the following: "sudo cat/ proc/mdstat", with the sudo command on the fornt. At this point i do not recall the erros, but i am happy to write them back if i get them again

> **LNK said:**
> To answer another question, I'm running Kubuntu because I prefer the KDE desktop. No other reason. That's all that makes Kubuntu different from Ubuntu.

--Lloyd


Well i have read on the forum and came to the conclusion of using the ubuntu server, one of my plans was to then probably install the GUI with kubuntu. what are your thougths in relation ot this. I just want something ligth and stable

Thanks

rgotten

---

### Post by LNK on 2008-04-22
Rgotten,

Yes, if your are prefacing each command with "sudo", then you are running the commands as root. If you happen to forget it on a command, you will likely get some errors.

If you try the installation again and get some errors, post them back here and I'll see if I can deduce what is happening.

If you think you will want the KDE GUI, my advice is to simply install that from the start. I think it will be more work later to install it on the server version. If you install it and then decide you don't want the GUI running, I'm sure you can change the startup process so it doesn't start the GUI. I believe that is simply a matter of specifying a different init level for the startup process. This is just my opinion. Others might disagree. If you do want Kubuntu, just be sure you use the "alternate" version which contains RAID support.

--Lloyd

---

### Post by rgotten on 2008-04-24
> **LNK said:**
> Create the RAID array.

Now it's time to create the final RAID5 array and its file system.
Create the RAID5 array for /home with the following command:

Code:
root@ubuntu:~# mdadm --create --verbose /dev/md6 --level=5 --raid-devices=5 /dev/sda10 /dev/sdb10 /dev/sdc10 /dev/sdd10 /dev/sde10
mdadm: /dev/sda10 appears to contain an ext2fs file system ...
Continue creating array? yes<ENTER>
mdadm: layout details to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 45798086K
mdadm: array /dev/md2 started
root@ubuntu:~#

.


So far so good. I am in the process of reconfiguring the raid 5 and waiting for it to finish to install the /home. During the above part of the installation i just want to be sure if this is a typo error or I have an error on my side, if you see above you are creating this command for md6, and at the end i got a message"
"mdadm: array /dev/md6 started" when you posted "mdadm: array /dev/md2 started" 

Thanks
rgotten

---

### Post by LNK on 2008-04-24
Rgotten,

Yes! That's a typo. Nice catch! I edited the original and corrected it.

--Lloyd

---

### Post by rgotten on 2008-04-24
> **LNK said:**
> 
Edit /etc/mdadm/mdadm.conf and remove the commented out array defintions. 
Edit /boot/grub/menu.lst and remove the menu entries for the non-raid boot options. These are no longer valid. 


So far everything is well, and i am at the last part, since i am so new, i do not want to screw it up, can you be more specific in this last 2 steps. In teh fist one what exactly i have to remove? and in the second part do you refer to the parragraph that you mention before: "On the two original entries (now the third and fourth entries), append "(non-RAID)" to the title line. When the menu displays, you'll be able to tell which ones will boot from original installation"...I should remove the 3rd and 4th parragraph?

Thanks

rgotten

---

### Post by rgotten on 2008-04-24
.

---

### Post by rgotten on 2008-04-24
While waiting to do the last 2 steps( see my next question) , i decided to disconect one of the hard drives trying to simulate a failure and when i boot it, this is what i got:

Loading, please wait...
stdin: error 0
kinit: name_to_dev_t(/dev/md1) = md1(9,1)
kinit: trying to resume from /dev/md1
[ 237.474863] Read-error on swap-device (9:1:
kinit: No resume image, doing normal boot...
Usage modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modeprobe -r [-n] [-i] [-v] <modulename> ...
modeprobe -l -t <dirname> [ -a <modulename> ...]
mount: Cannot read /etc/fstab: No such file or directory
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help'for a list of build-in commands

(initramfs)


After this if i turn of the computer and reconect the hard drive it turns on normally...Any idea???

rgotten

---

### Post by LNK on 2008-04-24
Rgotten,

First, your questions about cleaning up. In the section "Reconfiguration for RAID5", subsection "Create the RAID5 partitions", step 7, I said to comment out the current ARRAY definitions in the mdadm.conf file and paste the new definitions into the file. You should remove the ARRAY definitions you commented out at that point. On the second question, yes remove the 3rd and 4th menu entries that were tagged "non-RAID".

On the errors you get when disconnecting a drive, it could be several things. First, did you check mdstat before doing this to be sure the that all the arrays were completely built? If it's still in the process of syncing data to all the drives, you'd have a big problem if one of them went away!

It is sometimes difficult to determine which drive is zero, one, or two, i.e. hd0, hd1 or hd2. If you disconnected hd0, then it will not boot with the default menu entry, because hd0 isn't present. You have to tell it to boot from one of the other drives. I'm not in front of my system, so I can't be specific. But when your system starts up, you will see an opportunity to interrupt the boot process to bring up the boot menu. Do that. It will present a menu of what it can boot. Select the primary menu entry, and "edit" it. Tell it to boot from hd(1,0) instead of hd(0,0). Then continue booting. I think this is probably your problem. But I can't be sure because I haven't seen that specific error.

--Lloyd

---

### Post by rgotten on 2008-04-24
> **LNK said:**
> Rgotten,

First, your questions about cleaning up. In the section "Reconfiguration for RAID5", subsection "Create the RAID5 partitions", step 7, I said to comment out the current ARRAY definitions in the mdadm.conf file and paste the new definitions into the file. You should remove the ARRAY definitions you commented out at that point. On the second question, yes remove the 3rd and 4th menu entries that were tagged "non-RAID".

Well i just realize one problem here, i just learn that comment out means to place a # before a definition instead i deleted what you mention to comment out...Di i have to do the whole process again ( i follow all you steps but instead of commente out i delete what was suppose to be comment out. If i have to redo this do i have to do the complte process from scratch (including partition and RAID???

> **LNK said:**
> On the errors you get when disconnecting a drive, it could be several things. First, did you check mdstat before doing this to be sure the that all the arrays were completely built? If it's still in the process of syncing data to all the drives, you'd have a big problem if one of them went away!

Yes i checked and all the RAID's were built...

> **LNK said:**
> It is sometimes difficult to determine which drive is zero, one, or two, i.e. hd0, hd1 or hd2. If you disconnected hd0, then it will not boot with the default menu entry, because hd0 isn't present. You have to tell it to boot from one of the other drives. I'm not in front of my system, so I can't be specific. But when your system starts up, you will see an opportunity to interrupt the boot process to bring up the boot menu. Do that. It will present a menu of what it can boot. Select the primary menu entry, and "edit" it. Tell it to boot from hd(1,0) instead of hd(0,0). Then continue booting. I think this is probably your problem. But I can't be sure because I haven't seen that specific error.

I will check that tomorrow also, but if the boot area is in RAID 1 isn't suppose to boot from the mirror area??, and if i keep on having problems how ligth is kubuntu to worl as a server???..Thanks

---

### Post by LNK on 2008-04-25
Rgotten,

You do not need to redo the installation. It is okay that you deleted those lines from mdadm.conf. The only reason to comment things out as you go is so you don't lose any previous configuration. But it sounds like you made it through okay and there's no need for those lines at this point. So you are okay.

The boot partition is RAID1. But that is simply to keep all the disks in sync. Remember, the boot PROM knows nothing about RAID. It simply assumes the individual partition on the boot drive contains what it needs to boot. And it reads that. The RAID software doesn't run until AFTER the kernel is up. You could have set up identical partitions for /boot on each drive and not put them in a RAID array. That would work too. But you'd have to keep them in sync manually (make a change to one, then sync the others). With RAID1 you can let the RAID implementation do that work for you. But it still boots without RAID. And that's why you have to change the boot parameters in the menu if the boot drive is the one that fails. Once your failed boot drive is replaced and the /boot RAID array is in sync again, you can boot with the default parameters again.

--Lloyd

---

### Post by rgotten on 2008-04-25
I try to change the boot sequence, and it does not work, i also try disconecting a diferent hard drive at tha same time (always two connected) and the same thing happen. Any other ideas??

rgotten

---

### Post by LNK on 2008-04-25
Rgotten,

I'm afraid I'm out of great ideas. I tested my system to see that I could boot for other drives by changing the drive in the boot menu. I don't think I tried all five of my drives, but I did boot from at least three with no problems at all. But that was done with all five running. I never tried to disconnect one and then boot. I also did RAID testing by "failing" drives with the mdadm command. Everything worked fine doing that.

It appears from the error output you posted that it is actually finding and loading the kernel but then doesn't correctly mount the root filesystem. That's why it can't find /etc/fstab and it can't mount the in-memory filesystems like /proc (the root filesystem isn't there).

When you get the busybox prompt, run dmesg and look at the output to see where the initial error is. I suspect that there is an error that has scrolled off the screen and you're just seeing the end result.

When you boot, bring up the boot menu and check what the "root" filesystem is. There should be a line similar to "kernel /vmlinuz-2.6.22-14-generic root=/dev/md2 ro quiet splash". What is "root=???"? Is it the root RAID partition, or something else?

These are some things to check. I'll see if I come up with more. Basically, we need to determine where it is failing first.

--Lloyd

---

### Post by rgotten on 2008-04-25
root file system is /dev/md2. root is (hd0,0). Also when i was trying to change (hd0,0) to (hd1,0), i click on "e" and was able to change it but how do i save it, when i go out, it stays as (hd0,0). 
In the past when i  was researching before i came to your thread, i look at this [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html), there is a warning at the end with some bugs reported for version 7.10 like this one: [https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375) and this one: [https://bugs.launchpad.net/ubuntu/+bug/157648](https://bugs.launchpad.net/ubuntu/+bug/157648), what do you think about this, and do you think this could be the problem?

Also how do i run dmesg on the busybox??

Evidently, i removed a hard drive, since in my opinion if one of them fails wound't this be a similar situation for a hard drive failure and that is when you want the system to work until you replace the hard drive?

Also, what do you think about version 8.04 should i try that, do you think that this can make a difference??

---

### Post by LNK on 2008-04-25
Rgotten,

This ([https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)) looks like it is exactly the problem you are having. At the end of this very long thread are some workarounds that show a lot of promise. But I'd guess you'll need to read the entire thread to understand all of it. Now you have me thinking that I have a vulnerability to address! Yes, a disconnected drive definitely simulates one potential error situation. And I should probably try that myself and work through this issue.

I could be wrong, but I thought dmesg was included in the busybox command set. If so, you can just enter dmesg and hit ENTER. Of course, there will be lots of stuff that scrolls by. You might need to redirect output to a file and then look at the file in an editor.

I have no opinion on using 8.04, except if I were installing today that's what I'd use. You should look at the change logs and see if the bug has been addressed. If you want to restart from scratch with 8.04, you could give it a try. I did find that after I'd run the installation a few times, I could do the whole thing fairly quickly, other than waiting for it to sync large RAID arrays.

I am going to take a look at this issue with my own system and implement the work around if I need to. But I don't know when I'll get to it.

--Lloyd

---

### Post by rgotten on 2008-04-25
Let me ask you another  question, i learned how to check the partitions and found the following with the fdsik -l command: each one of the disk says: Dsik /dev/md6 doesn't coantain a valid partition table...the same thing with 1 or 2 or 3 or 4 or 5..Why

Thanks one more time for your help

---

### Post by LNK on 2008-04-25
Rgotten,

When you "partition" a drive, you slice up the drive into different segments/partitions. For example, when you partition /dev/hda, you end up with /dev/hda1, /dev/hda2, /dev/hda3, and so on. The partition table is stored on /dev/hda, the base "drive", not on each partition. When you run "fdisk -l /dev/hda2", for example, it actually reads the partition table from /dev/hda. Make sense? At least that is my understanding.

So, where is /dev/md? Well, there isn't one. So when you run "fdisk -l /dev/md2", it can't find /dev/md and thus can't find the partition table. The raid devices are "software devices" and the actual configuration is in mdadm.conf, not on the drives themselves. The drives themselves have the "hard" partitions, like hda1, hda2, etc.

Generally, the primary reason for the partition table is so various tools can read it and use it to manage partition sizes. Since the actual size of the RAID array is based on the size of the constituent partitions on the drives, it really can't be "managed", i.e. grown, shrunken, etc. To do that, you have to actually manage the size of the constituent partitions. Thus, having a partition table for the RAID device isn't particularly useful.

I don't know of any issue with not having a partition table for the RAID devices.

--Lloyd

---

### Post by rgotten on 2008-04-25
how do i check then were  / /var /usr and home are located..let say i want to go to my root or my home folder

rgotten

---

### Post by LNK on 2008-04-25
I'm not sure I understand your question. But I think this is pretty simple, basic Linux/Unix stuff. The root filesystem is mounted as "/". So if you want to go to the root, cd to /. The root filesystem has empty directories for usr, tmp, var and home (and potentially others). These are the mount points for those filesystems. The usr filesystem is mounted on /usr, the var filesystem on /var, etc. If you want to go to the usr filesystem, you simple cd to somewhere in /usr. Once a filesystem is mounted, the mount point will no longer appear to be empty. For example, if you look at /usr before it is mounted it will be empty. After it's mounted, it will appear full of lots of things, like /usr/bin, /usr/local, etc. All this is a little difficult to see because all these filesystems need to be mounted for a working system. But if you put a CD in your CD drive it should mount on /media/cdrom0 (I believe). If you look at /media/cdrom0 before putting the CD in, it will be empty. After you put the CD in, it will show all the files on the CD.

You can see all the mounted devices by simply enter the "mount" command (no parameters) at a command prompt. If you're not the superuser, you'll only see the ones accessible to you. To see everything, do "sudo mount". An entry will look something like "/dev/md6 on /home type ext3 (rw)", which tells you /dev/md6 is mounted on the mount point /home, it has an ext3 filesystem and it's mounted read-write (rw). Using the mount command is the quick way to see all that's mounted.

Being new to all this, you might want to pick up a basic Linux book. There are some specific to Ubuntu. Play around a bit with basic commands to learn. The GUI is always nice, but to do many admin tasks on any Linux distro you have to get comfortable with the shell and a text editor. You will frequently need to use those for admin work.

--Lloyd

---

### Post by rgotten on 2008-04-29
When install version 8.04, and i disconect either of the hard drive it appears to boot and i get a message that says: start the raid in degrade (or somethng similar), with the command mdadm -R /dev/mdx ( in version 7.10, i have to install the boot insruction in each one of the hard drive). Since i am getting this message, does this mean that the newer version has the bug fixed in regards to the instruction on how to boot in each one of the hard drive??

How can i check each hard drive to be sure they have this instruction and that i have installed grub also on the second disk's (/dev/sdb) master boot record (MBR), as well as the third. ??

thanks one more time

rgotten

---

### Post by LNK on 2008-04-30
Rgotten,

I don't think I can help you with this latest question. There were some hints in this: [https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375). But I didn't read it well enough to be able to tell you where to look for changes. You may want to post your question in the Installation & Upgrades forum. There should be some experts in the community watching that forum and perhaps they can answer your question. You should refer to the URL above and ask specifically about that bug.

Sorry I can't be of more help on this one. I'd have to reinstall and play with it to be able to answer your question.

--Lloyd

---

### Post by Bill Roberts on 2008-05-01
Fabulous post!  I've been trying to solve this puzzle myself for a couple of weeks and now it's all laid out for me.:KS

---

### Post by slvrmoontiger on 2008-06-22
Hi,

  Just tried doing this and everything seemed to work out pretty well with the following exception.  On my md0 1 of the drives is not syncd up how do I force a sync on that drive:


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md6 : active raid5 sdd9[3] sdc9[2] sdb9[1] sda9[0]
      20506560 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md5 : active raid5 sdd8[3] sdc8[2] sdb8[1] sda8[0]
      14650944 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md4 : active raid5 sdd7[3] sdc7[2] sdb7[1] sda7[0]
      20506560 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md3 : active raid5 sdd6[3] sdc6[2] sdb6[1] sda6[0]
      20506560 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md2 : active raid5 sdd5[3] sdc5[2] sdb5[1] sda5[0]
      14650944 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

md1 : active raid1 sda10[0] sdc10[3](S) sdb10[1]
      4883648 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdd1[3] sdb1[1]
      128384 blocks [4/3] [UU_U]

unused devices: <none>

---

### Post by kb-linux-2 on 2008-10-30
Lloyd,

Thanks for all of the time and effort that you have expended in writing this “How To”.  It is very detailed and easy to understand.

I have only had one problem, I got all of the expected results until I got to the reboot step in the “Reboot to the RAID5 system!” section.  The reboot worked up through and including my entering my userID and password.  Then I got a dialog box that said “The following installation problem was detected while trying to start KDE.  No write access to $HOME directory.  KDE is unable to start.”

After rebooting into my original installation partition I have looked at the permissions for both the non RAID home directory and the RAID home directory and found them to be identical.  I have redone the installation two more times being very careful to follow the instructions correctly and still have the same results. 

Any pointers on where I should look for possible things that I may have done wrong?

My installation is the same as yours except that I only have 3 drives in my array rather than the 5 drives that you used.

Thanks again!

kb-linux

---

### Post by LNK on 2008-10-31
kb-linux,

First, I have to ask if you are installing 7.10. If you're installing 8.X, it could be different. I know there were some changes made to the RAID support in version 8. I haven't upgraded and so I haven't investigated how the changes affect my procedure.

Assuming you're installing 7.10, then let me be sure I know just where you're experiencing the issue. You're at the point just before "Move /home to RAID5 and Clean Up". Correct? Assuming that is correct ...

I'm not certain what is happening, since /home hasn't yet changed. It's still on the original installation partition. Check the /etc/fstab file that is used when booting from RAID and be sure that it doesn't have a /home mount point that isn't available after the boot. At this point you shouldn't have a separate mount point for /home. It should still be in / (root) and that would be the one it's using.

Also check to see that the home directory is set correctly in the /etc/passwd file. Be sure you're checking the passwd file in the root RAID partition, not the original installed root. It's possible that $HOME is getting changed somewhere in a shell configuration file, e.g. .profile or .bashrc. But this is doubtful if you're doing a fresh installation.

Those are some suggestions to try and track down the issue. I don't recall seeing your particular issue when I was doing the installation. So I'm not sure what the root issue is.

Post back here with further questions, or the solution when you find it so others will know.

--Lloyd

---

### Post by Trollgaard on 2009-05-03
Thanks alot for this! Great work LNK! I am currently waiting for the building of the /home array to finish after a succesful install of Ubuntu 8.04 LTS Server 64bit. Everything has gone perfectly well until now, and I hope the little remaining work will too. I have followed the instructions as close as possible and had no problems or error messages except for a typo here and there which of course is my own bad. The raid consists of 6x750GB with: 128MB /boot, 18GB /, 50GB /usr, 20GB /var, 10GB /tmp and 2GB swap. The rest is for the /home partition and consists of partitions with 720GB on each disk. I will test the raid when it's done building and the final steps are done. If anything shows up, I'll post it here.
 
-Troll

---

### Post by kevinguillorytraining on 2009-10-09
Keep up the great work!

---


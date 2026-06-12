---
title: "Transferring 40GB HDD w/ Xubuntu from non-UEFI Motherboard to a UEFI Board"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by dannyboy79 on 2013-11-15
Hi everyone, 
I just picked up a new tower which has an AsRock Extreme6 motherboard, an A8-3870k APU, 8GB of DDR3 2133Mhz Patriot RAM and an XFX HD5750. It came with a OCZ Synapse 64GB Cache Drive (only 32GB is usable) but I am not sure what I am doing with that yet.
Anyway, my question is will I be able to just put in a PCI IDE card and my IDE 40GB HDD into this tower and boot it OR will I have to do anything special. I have already tested this tower with Ubuntu 13.04 from a flash drive and I had to choose USB boot, I didn't choose UEFI USB Boot.

---

### Post by oldfred on 2013-11-15
UEFI systems will usually work with old BIOS.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

But if an add in card that may be a question. Most new motherboard have one IDE connector although they are doing away with that now also. Few old IDE drives left that are not beyond warranty anyway.

Someone posted this, do not know if it would also apply to yours or not.

>  So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!



       UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)

    
It may just be time to convert to new drives with gpt partitioning and UEFI.

---

### Post by dannyboy79 on 2013-11-15
the AsRock A75 Extreme6 does NOT have an IDE port. I guess all I can do is try it out and see.

If I did have to move my current 40GB HDD Xubuntu installation onto a SATA drive, whats the best method to achieve this. My current HDD is setup using msdos partition table with a logical partition 14GB /, then an extended partition with 22GB /Home and the remaining is SWAP space.

---

### Post by oldfred on 2013-11-15
I believe in new installs.
I would partition new drive in advance, copy /home to new drive new /home with rsync or cp, but be sure to include parameters to preserver ownership & permissions. And then use Something Else or manual install to choose existing /home but DO NOT check the format box or else it will be reformatted.

I suggest gpt for all new systems. You can from Ubuntu boot in BIOS or UEFI mode from gpt partitioned drives. If if installing Windows you can only boot from gpt with UEFI.

If going from MBR to gpt do not use dd as gpt has additional internal differences.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

My backup procedure assumes I will reinstall, so I try to backup what I need to make it the way it was.
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by dannyboy79 on 2013-11-16
so you're saying that Clonezilla would not be an option then because it may use dd? I was just going to use clonezille to clone my / partition to an image as well as my /home to an image. then i will partition my new 160 SATA drive using GPT and create 3 patitions, 1 for /, 1 for /home, and 1 for swap. then I was going to use clonezilla to restore the images of my / and /home onto my new drive. Will that not work?

Id rather not have to perform a new installation, i have a ton custimized and just the way I like it. Any more suggestions would be much appreciated.

---

### Post by oldfred on 2013-11-16
I have not used Clonezilla, but it says it only uses dd on unsupported file systems, so it may work. As long as you just use a copy you can go from MBR to gpt as it is data, but image type copies will not work.

All your user settings are in /home. Only hardware type settings are in /etc. But a list of installed applications is always good to have anyway. I make that part of my rsync backup of /home.

---

### Post by dannyboy79 on 2013-11-16
well, i've decided to just stick with msdos style partitioning (MBR) since my disk is only 160GB, i don't see a real need to go to gpt at this time. I have restored the images of my partitions onto the new 160GB disk but of course it doesn't boot, it sits there at a blinking cursor so I am now downloading the linux-secure-remix and will try boot-repair. Hopefully that fixes it.

UPDATE: yes, using linux-secure-remix_64bit version and using the recommended fix made it so my machine boots now and all is well. I successfully moved my Xubuntu installation from a 40GB IDE HDD to a 160GB SATA HDD using clonezilla by imaging each partition individually and then formatting my new hard drive with the same partition scheme (MBR) (msdos style partition table) and then used clonezilla to restore the images to the new hard drives partitions. YIPPIE!!!

I made a blog post about the whole process if interested, find it in my signature


The next thing to figure out is how to best use this 32GB Cache SSD drive, it advertized as 64GB but only 32GB is used (not sure why). Most likely either as an external journaling drive for my / and /home partitions OR try to setup flashcache. That thread is here if you have any feedback regrading best use of a 32GB cache ssd drive. [http://ubuntuforums.org/showthread.php?t=2187970](http://ubuntuforums.org/showthread.php?t=2187970)

---


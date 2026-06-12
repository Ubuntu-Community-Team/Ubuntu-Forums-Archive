---
title: "Oh dear, 2 hours in..."
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Zeromute on 2013-05-09
Hi all,

Another fresh user with a problem! 

Ive been trying for the last 2 hours to install 12.04 from both a CD and a USB, but to no avail.

Sadly each time I try something different seems to go wrong so it's kind of hard tracking the problem down. Essentially it just crashes once I press the "Install alongside Windows 7" button, the screen blacks, then displays an array of messages regarding processes shutting down. If I press enter at this point then it restarts and just loads windows. It's really rather frustrating! 

Comp is a Acer X3400, 3gb, GeForce 9200, AMD 2.9ghz

Thanks

Nick

---

### Post by TheFu on 2013-05-09
Can you run fine from the CD without installing? Is all your hardware well supported?  That is the first test.  Check the log files for "warning" and "error."  I think there is a log file browser in the menu somewhere or do it this way: [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

---

### Post by Zeromute on 2013-05-09
It worked absolutely fine from the CD, just the installation that goes wrong.

I can't seem to find the logs though.

just tried again, all good up to choosing the install options, then it goes to the splash screen, ejects the disk, restarts and boots straight into windows.

---

### Post by TheFu on 2013-05-09
I can only suggest that we gather information about your system for now. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) explains.  There is lots of new hardware these days, so knowing exactly what you have relative to BIOS and disks will be necessary.

---

### Post by Cheesemill on 2013-05-09
Have you checked the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso file you downloaded? A corrupt download can cause the sort of problems you're describing.

---

### Post by Zeromute on 2013-05-09
[Http://paste.ubuntu.com/5649136](Http://paste.ubuntu.com/5649136)

theres the boot repair log. Checking the MD5SUM now

---

### Post by Zeromute on 2013-05-09
> **Cheesemill said:**
> Have you checked the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso file you downloaded? A corrupt download can cause the sort of problems you're describing.

Checked ok. It matched the hashes on the the ubuntu hashes page.

---

### Post by Zeromute on 2013-05-09
Bah, still nothing.

Tried various different versions but always the same thing. Ejects installation media and restarts...

---

### Post by oldfred on 2013-05-09
You have run into the 4 primary partition limit with 30 year old MBR(msdos) partitioning scheme.

 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

We normally suggest deleting one primary like a vendor tools partition, but you have used all 4 as required partitions. You might be able to remove the pqservice which is probably your recovery partition.

But you can convert primary partitions to logical inside one extended partition. That may be a better way, then you can shrink your NTFS partitions to make room for Ubuntu partition(s). Always run chkdsk after any resize of NTFS partitions.

You can download fixparts into your liveCD/flash installer and run it in terminal from that.
      
 To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Zeromute on 2013-05-10
Crikey, that looks fairly complex. I had a go at shrinking one of the partitions to make some space, but it came back as "Unusable" on the installation. It also turned the 4 primary partitions into 1 primary (recovery) and 3 (4 after the shrink) simple.

---

### Post by black veils on 2013-05-10
> **Zeromute said:**
> Crikey, that looks fairly complex. I had a go at shrinking one of the partitions to make some space, but it came back as "Unusable" on the installation. It also turned the 4 primary partitions into 1 primary (recovery) and 3 (4 after the shrink) simple.

firstly, you need to shrink your main Windows system or Windows data partition, using the Windows disk management tool.

then delete a partition, you cannot install anything unless you delete one. you must decide what can be removed.

create an extended, which will be your final primary, make sure it fills the rest of your drive.

now can add more partitions, of the logical kind, within the extended.


when you say all the primary's have been changed, do you mean the hard drive is now dynamic? that is not good, linux is not compatible with it.

there is a way to change back to basic, but you risk wrecking Windows and your data. the official way is to remove everything from the hard drive, and then install Windows from fresh (probably from an installation disc). which is of course a lot of hassle.
**EASEUS partition tool**:
[http://www.nextofwindows.com/how-to-convert-a-dynamic-disk-storage-back-to-basic-without-losing-any-data-in-windows-7/](http://www.nextofwindows.com/how-to-convert-a-dynamic-disk-storage-back-to-basic-without-losing-any-data-in-windows-7/)

---

### Post by TheFu on 2013-05-10
> **Zeromute said:**
> [Http://paste.ubuntu.com/5649136](Http://paste.ubuntu.com/5649136)

theres the boot repair log. Checking the MD5SUM now

You are screwed.  The maker used all 4 primary partitions that MSDOS MBR partition tables support. You need one or two more and the partition table is already "full."  You'll need to perform some disk partition surgery to resolve the problem.

The tools that I would use are:
* backups
* partimage - clone Windows tool partition, Acer tool partition and recovery partition to some other disk
* another HDD - a place for the cloned partitions to move AND a place for the backups
* gparted - boot off a liveCD to make these changes easier. You might be able to change some partitions without doing this, but you can't touch actively used partitions at all.

Depending on the OSes you want/need to run, I'd try to use a GPT partition table instead of the MBR partition table. It is much more flexible if you can use it.  OSes since Vista work with GPT. WinXP does not.  Older Linux distros will also have issues, but anything from 2010 and later should be fine.  Use wikipedia to see why GPT is much more capable AND safer than MBR partitioning.  The main things GPT supports are huge numbers of primary partitions - over 100 and HDDs over 2TB in size. MBR doesn't.

Switching from MBR to GPT means wiping the entire disk. That might not be possible. The next option is to move as much data from the HDD and delete at least 1 primary partition at the end of the disk so you can create an "extended partition", then place a few "logical partitions inside it."  Logical partitions work just fine for Linux and linux-swap. Also, over 100 logical partitions are supported in MBR. It comes down to making all those logical partitions fit inside the extended partition.  Some OSes cannot boot from Logical partitions - usually those are old MS-DOS hardware tool partitions and older Windows-OS partitions.  Screwing around with the number of partitions on Wnidows is dangerous. You can end up with a non-booting system, so definitely have a backup and have the recovery partition ready to work. It is 50/50 that all this partition work will cause your system to be non-bootable. Be prepared.

Unless something has changed, using fdisk, sfdisk and cfdisk should probably be avoided. Those older tools don't **automatically do the right things** that we need for newer HDD layouts.  **gparted** and **parted** are the replacement tools which know about new disks AND old disks. These newer tools "do the right thing" automatically related to sector alignments so we don't need to manually handle it.  I've stopped using the old tools completely. It just isn't worth the hassle to me to wonder if they do what I need or not.

Try to use Windows tools for Windows partition management and Linux tools for Linux management. If the Wnidows tools don't do it, only then should you drop back to the Linux tools.

You know, at this point, I'd probably spend $50 and buy a new HDD, install it, partition it as GPT and use the partimage copy of the Widows recovery partition to reinstall Windows on the new HDD. Then I'd install Ubuntu.  With GPT, you get all sorts of flexibility. The main key is to have the MS-DOS tools in one of the first 4 primary partitions, then put Windows and/or Linux after that.  Here's the partitioning scheme that I would use:
* Partition 1 - Acer HW tools  (small partition - 500M?)
* Partition 2 - Windows Recovery (small partition - 2G-5G?)
* Partition 3 - Win7 OS  (40G-60G partition)
* Partition 4 - NTFS Data (all remaining storage for "data" only - not programs)
* Partition 5 - Linux OS/Apps (20G) 
* Partition 6 - Linux HOME (depends, 5-10G)
* Partition 7 - Linux Swap (2G max)

The other advice is solid.  I trust Oldfred.  Good luck!

---

### Post by oldfred on 2013-05-10
I like gpt partitioning, but Windows only boots in UEFI mode from gpt partitioned drives. I did have XP on a MBR drive and Ubuntu on a gpt drive without issue with my BIOS system. Windows 7 would see a NTFS partition on a gpt drive, but my XP could not.

Did you try to create partitions in Windows? Then you may have converted to dynamic from basic partitions. Dynamic does not work with Linux and even some Windows repair tools. Third party partition tools can be used to unconvert dynamic, but Microsoft official policy is backup, erase drive and reinstall & restore data.

Only use Windows partition tools to shrink a NTFS partition never to create new partitions.

---


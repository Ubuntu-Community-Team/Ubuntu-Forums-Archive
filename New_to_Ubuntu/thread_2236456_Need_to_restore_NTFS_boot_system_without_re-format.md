---
title: "Need to restore NTFS boot system without re-format"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by BrioHondo on 2014-07-26
Hey everyone! I'm getting back into linux after a long time, and think I royally screwed up my wife's laptop (an ASUS X200CA) when trying to dual-boot Ubuntu from a USB stick. I NEED to maintain the windows environment, preferably with the original data.

I made a series of mistakes.

First, I did NOT change the size of the partition in Windows. I tried to do that inside the Ubuntu partition manager during installation. That screwed up the drive/partition her windows machine was on. I do not think that I formatted the drive - I just changed to file system type.

I tried restoring things from the windows command line tool (CMD). I was able to change the file type back to NTFS, but somehow I did something that made things MUCH worse. Before I could get into the advanced boot-up options screen for windows, but that won't even load any more. If I boot up the machine without the USB drive in, the computer gets no further than BIOS.

Finally, I tried boot-repair, but whatever auto-fixes it tried did not work.

The website boot-repair gave me is below. Please help! And thanks in advance...
[http://paste.ubuntu.com/7871140/](http://paste.ubuntu.com/7871140/)

---

### Post by mooreted on 2014-07-26
First of all, you don't use Linux tools to repair Windows partitions; you're just asking for trouble. You say you just changed the file system type without formatting. There's a good chance that was enough to wipe out that partition.

A very important thing to remember about working on computers: before you do any major work you must back up your data first. It doesn't take much to wipe out a hard drive. One little mistake and it's all gone.

If you boot to the USB and run Ubuntu from it, can you see the Windows partition? If you can, mount it from the Ubuntu live session and copy the data on that partition - whatever you want to keep - to an external hard drive.

Once your data is backed up, boot up to the Windows DVD and see if you can do startup repair.

---

### Post by oldfred on 2014-07-26
You are the first I have seen with LDM partitions. 
Supposedly Windows even converts gpt partitioned drives which have an unlimited (really 128) number of partitions to dynamic partitions which Linux sees as LDM in gpt partitioned drives.
(With MBR or msdos partitioning dynamic is seen as SFS).

You also are showing two efi partitions. Drive can only have one per hard drive. So use gparted and remove boot flag from sda10.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM

DO NOT reinstall Ubuntu using any auto options. Only Something Else. All the auto options erase entire drive.

Third party Windows partition tools may do some repairs, but I have never used them.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

Basically you want to use Windows tools on Windows and Linux tools on Linux. But occassionly Linux tools may work to do some repairs on Windows.

Windows with UEFI also needs or expects extra partitions over the old style BIOS/MBR type installs.
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---


---
title: "Boot partition very far away from begining of disk"
date: 2015-09-29
forum: New to Ubuntu
---

### Post by diego50 on 2015-09-29
Hi everybody! I am having trouble since I recently installed UBUNTU and it does not boot properly. I run boot repair and everything's ok except that the boot partition is near the end of the disc, and the program warns me that probably I would experience boot failure.

And I do. Hopefully I can run UBUNTU in repair mode.

The situation goes like this. I have an HP Pavillion, that has 4 partiotions. The first 3 are reserved for Windows, although I freed some space to set a boot partition for UBUNTU. Now my scheme is:

- /dev/sda1   ntfs   System   200 MB
- unallocated                        1.98 GB (this where I wold like to set /boot, so it is at the begining of the disc and hence I'll be avoiding boot problems)
- /dev/sda2   ntfs                 500 GB (Windows partition. It has a boot flag)
- unallocated                        1 MB
- /dev/sda3   ntfs  Recovery 14.97 GB (This is from HP and I read it is recommended to leave it as it is)
- /devsda4/   extended
   -/dev/sda  linux-swap
   -/dev/sda  ext4     /(Root)
   -/dev/sda  ext4     /home
   -/dev/sda  ext4     /boot (this is the one I want to move upper in the disk)
- unallocated

How can I move the boot partition to the free space (1.98GB) I left unallocated near the start of the disc?  I can't simply create a primary partition there, since I already have 3 primary and one extended partitions.

Hope you can help me!!!

Cheers,
              
     
Diego

            &nbsp;):P

---

### Post by oldfred on 2015-09-29
You cannot.

All logical partitions must be together to be "inside" the extended partition.
And you can only have 4 primary partitions.

If a newer system you probably do not need to worry about the far from start of drive issue.
It still seems to be an issue with external drives, and with very old BIOS. 
I would have /boot first in extened partition & swap last on drive.

Make sure BIOS is up to date.

If it does not work, then only recourse is to make the DVD set or flash drive recovery. Which is probably a good idea anyway. When hard drive fails it is a bit difficult to use the recovery on the failed drive to restore to a new drive. 
Some just make a full backup of Windows. The main reason for the recovery is if later you want to sell system with working Windows you can do the vendor restore to have it "like" new.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Lyta on 2015-10-01
I have the same problem in a computer with no partitions, with only Ubuntu installed. I can't seem to find a way to fix it and have to keep doing hard shutdowns through the power button. Boot repair doesn't help besides record the problem and create an info html file, and I haven't found a definitive way to solve it anywhere in the forums.

---

### Post by oldfred on 2015-10-01
@lyta
Please start your own thread. Post summary report from Boot-Repair and system specs.

---


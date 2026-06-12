---
title: "gparted help"
date: 2013-11-29
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-11-29
okay i have /dev/sda1 ext 4 flagged boot at 16.66 gig for my linux
and            /dev/sda2   ntfs     for windows   54.92

this morning i used a live cd because i wanted to decrease sda2 to 40 and use the unallocated space to increase sda1
i shrunk sda2 and then had some unallocated spaced 15 gigs
so far fine
however when i tried to increase sda1 i couldnt 
only had the option to re-increase sda 2 to the size i shrunk it
any ideas   
tks

---

### Post by rburkartjo on 2013-11-29
wonder if this would work i could back up my windows data delete the /dev/sda2 ntfs partition. change to ext and then increase /dev/sda1. and then re-install windows on the remaining space. would only like to do this if no other options are presented.

---

### Post by grahammechanical on 2013-11-29
Is Windows still loading? I have read posts that advise using Windows tools to resize Windows partitions. Is Gparted showing unallocated space? Will it allow you to turn that unallocated space into a partition (Ext4)? Which you can then delete and then expand sda1 into its unallocated space?

Regards.

---

### Post by rburkartjo on 2013-11-29
gra yes both are stilling booting. so bare with me you are saying shrink sda2 then reformat the unallocated space to ext4 then delete. then i should be able to increase the size of sda1.

---

### Post by grahammechanical on 2013-11-29
I am thinking.

If the resize of sda2 has been successful, then use the unallocated space to create an Ext4 partition. If Gparted does not refuse to do that, then delete the newly created partition and may be Gparted will allow you to expand sda1 into the unallocated space that it has just created?

When messing around with partitions I like to run each Gparted operation at a time. I get nervous with the long wait as Gparted works its way through a list of operations. This is just my personal preference. I also like to shut down the live session and start again. I am suspicious that data from failed actions is still remembered by Gparted.

Regards.

---

### Post by ajgreeny on 2013-11-29
Just to check!

When you shrunk sda2 did you do so by grabbing the left hand edge so the the free space was adjacent to the sda1 partition?  Assuming your partitions are in numerical order on the disk (not always the case) if you shrunk sda2 by grabbing the right hand edge it will have given you free space but in the wrong place on disk, so impossible to expand sda1 into that space.  You can move partitions but it's not a good idea to do so with an OS partition, particularly windows, as it is probably not going to boot again once the start of the partition has been moved.  If the ntfs partition is just for data with no OS system files on it you may get away with moving it safely, but backup everything just in case.

---

### Post by oldfred on 2013-11-29
If moving NTFS partitions make sure you have your Windows repairCD or flash drive handy. You will need to run chkdsk after a move or resize. If bootable it may auto run on an external resize when rebooted, but if moved you need external Windows repairCD to run chkdsk.
NTFS partitions have start & size info in the NTFS PBR or partition boot sector. That must match partition table or Windows will not boot. And chkdsk fixes that issue among others.

Boot flag also need to be on the NTFS partition. Grub does not use boot flag, but Windows has to have it to directly boot, or repair the NTFS partition.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by rburkartjo on 2013-11-29
tks ya'll .will let you know how i fare.

---

### Post by rburkartjo on 2013-12-02
after i backed up my linux and win system with redo. had problem reinstalling so booted live cd ,deleted sda2 increased sda to full disk and then i had to use an older redo backup; one that just had linux on it to reinstall. that went fine(maybe i have to use the win recovery disk also when i reinstall a redo backup). then using gparted shrunk hard drive to the size i wanted and formated to ntfs. had no problem installing windows but of course i had to use root-repair disk to reinstall grub. again tks all

---


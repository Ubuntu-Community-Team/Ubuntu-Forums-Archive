---
title: "Adding Second Disk Drive to Install Ubuntu"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by KAWill70 on 2008-09-05
[B]Yesterday I downloaded Ubuntu 8.04.1, created a CD, and successfully ran the Live version on my WinXP system.

I intend to add a second disk drive to my system for Linux and WinXP backup.  It would have two partitions.

What is the proper sequence of things I need to do to accomplish this?

I would like a dual boot system.

I assume I will need to format and partition the new drive and want to be 100% certain that I will not disturb the existing operating system.

Also, am I correct that boot.ini on my existing drive will be modified during the above process to handle the second drive and dual boot?[/B]

---

### Post by kalesh7 on 2008-09-05
Put the jumper on the windows drive to slave and the new drive to master and put them on the same cable
doing this will cause the windows boot manager to be preserved so if you were to remove the second drive or reverse the slave and master config sometime in the future your windows will stay as it is.

boot using Live cd go through install till the partitioning phase
select manual partitioning and make sure to select your NEW disk.
create a partition with mount point as / formatted as ext3 make this bootable (I think theres a checkbox to do so) this is for linux system

create a partition as swap the size should be about 2x your RAM

create a partition without a mount point formatted as NTFS for windows backup 

write changes to disk and proceed with install
once done reboot enjoy


Now that will work but I'm just putting in this incase someone wants to do something like it? or if one is totally paranoid 
step 1 Remove the windows drive and stick in new
follow the rest of above procedure except the jumper part
once install is done stick in windows drive as well
in order to boot a particular system you will need to get into bios and change your boot options to boot from the particular hd
so if you want to boot into linux change it to boot into the new hd(and it will then continue to do so) and later you want to boot into windows change the bios to boot from windows drive

---

### Post by KAWill70 on 2008-09-05
Thanks very much for the help.

I had considered something similar where I would initially connect only the new drive and install Ubuntu.  To boot WinXP I would move the IDE ribbon cable to the WinXP drive.  Both drives would be jumpered as Master.

I suspect there is a way to dual boot either Linux or WinXP.  My current WinXP system is actually dual boot in a sense as I can boot WinXP or the WinXP Recovery Console.  I am given a choice after Power-on.

I think this is handled in the boot.ini file as I can see the information for the two cases.

I think if things are done correctly the boot.ini file would be updated for two disks with pointers to all bootable programs.  There would be three if I retain the WinXP Recovery Console.

---

### Post by tahina on 2008-09-05
You might also want to dedicate a partition for /home, so that a possible future clean install with preserved settings and media will be easier. (If the disk is small, it could be hard to decide how much to give the system and how much for /home, though.)

---

### Post by anjilslaire on 2008-09-05
If you install Windows, then install Ubuntu on a separate partition or drive to dual boot, then during the Ubuntu install, it will detect the persence of Windows and create & adjust the Grub Bootloader that will allow dual-booting of both OSes.
When you select Windows, then you'll have your normal Windows choices..

---


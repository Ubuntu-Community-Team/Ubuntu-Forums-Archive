---
title: "overlapped partition 32bit"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by dkim53 on 2013-10-19
Hello,
I recently installed windows xp pro as a 3rd os on this older single core computer. Originally started with windows home, then added ubuntu 11.10 and upgraded to 12.4LTS. I learned how to use Clonezilla and Gparted. I used Gparted to create and format the partition I installed xp pro on. Now Grub is gone and I can only boot to the two windows os, pro and home. I have use the ubuntu live cd to get to this. It seems the /dev/sda2 is overlapped to /dve/sda3 which is the Linux swap partition. How can  I manually change the ending of dev/sda2 in the terminal? Here is the output of sudo fdisk -l -u.

ubuntu@ubuntu:~$ sudo fdisk -l -u
omitting empty partition (5)

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x414c936c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   143362047    71680992+   7  HPFS/NTFS/exFAT
/dev/sda2       143380478   781422591   319021057    5  Extended
/dev/sda3       779853824   781422591      784384   82  Linux swap / Solaris
/dev/sda5       143382528   290838527    73728000    7  HPFS/NTFS/exFAT
/dev/sda6       681791488   778280959    48244736   83  Linux
/dev/sda7       778283008   779843583      780288   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by fantab on 2013-10-19
You have to re-install GRUB using Live Ubuntu DVD/USB. Read [HERE]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2") and [HERE]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")

---

### Post by oldfred on 2013-10-19
You cannot have a primary partition sda3 inside the extended partition which is sda2.
since it is just swap I would delete it. If it is the swap you are using, you then would have to edit fstab with the UUID of your other swap.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

This may just let you reorganize partitions.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by dkim53 on 2013-10-19
> **fantab said:**
> You have to re-install GRUB using Live Ubuntu DVD/USB. Read [HERE]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2") and [HERE]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")
Thanks fantab! I used the second (HERE) solution [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UmMC6HBvPk8](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UmMC6HBvPk8)
That worked perfectly for reinstalling GRUB to my Ubuntu 12.4LTS. Now I can boot to any of the OS's.

---

### Post by dkim53 on 2013-10-19
> **oldfred said:**
> You cannot have a primary partition sda3 inside the extended partition which is sda2.
since it is just swap I would delete it. If it is the swap you are using, you then would have to edit fstab with the UUID of your other swap.

       First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

This may just let you reorganize partitions.

 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
Hi oldfred. Can you help me with the terminal commands? I think all I need to do in sfdisk is manually change the end of the extended partition to end before /dev/sda3. Your thoughts...

---

### Post by oldfred on 2013-10-19
If you want to manually edit partition table that can be done. It might just be easier to change sda3 to sda8 so it then is logical. Fixparts makes that easier to do.

You can export text file with sfdisk and edit partition numbers or start and size of partition manually, but need to be sure to follow details. Some math also as sfdisk uses start & size where most outputs are start & end sectors.

You may just be able to use fdisk to reunmber disks also as it rewrites partition table. But if you have any place not using UUID, but using device that may then need editing.

 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> If you want to manually edit partition table that can be done. It might just be easier to change sda3 to sda8 so it then is logical. Fixparts makes that easier to do.

You can export text file with sfdisk and edit partition numbers or start and size of partition manually, but need to be sure to follow details. Some math also as sfdisk uses start & size where most outputs are start & end sectors.

You may just be able to use fdisk to reunmber disks also as it rewrites partition table. But if you have any place not using UUID, but using device that may then need editing.

 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)
Another observation with this overlapped extend partition is Gparted sees the drive as unallocated. This seems to be be consistant with many other of the forum threads. Do you think that moving /dev/sda3 to /dev/sda8 will help remedy the Gparted as well? I'm game with giving this a go. Can you help with the terminal commands?

---

### Post by oldfred on 2013-10-20
I really suggest fixparts as the easiest way. 

I have never directly edited a partition table but have the old links above where those who knew a lot did export data, edit it and reimport it. But that is almost never required now with fixparts.

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> I really suggest fixparts as the easiest way. 

I have never directly edited a partition table but have the old links above where those who knew a lot did export data, edit it and reimport it. But that is almost never required now with fixparts.
Ok oldfred, let's give fixparts a go. Please walk me through the the commands from downloading to finish. I am not an accomplished Linux user. The computer that I'm doing this to is not my main computer, it's like a test one to learn Ubuntu. If all fails, I'll wipe the drive and start from scratch. This will be a learning experience for me.

---

### Post by oldfred on 2013-10-20
Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).
oldfred YOU ARE THE MAN!!! Worked like a charm. Once installed in the terminal, typed p to see the fix part changes. Then typed w to save and exit from the terminal. Then rebooted and it did the trick. Now even Gparted sees all the partitions again. So I will make this solved thanks to you...

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).
oldfred, YOU ARE THE MAN!! Fixparts worked like a champ. After launching fixparts from within the terminal, typed p to let show the changes. Then typed w to save and exit from the terminal. Rebooted and all is well thanks to you. Now Gparted sees the partitions again. I will make this post solved. THANKS!!

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).
oldfred, YOU ARE THE MAN!! Fixparts worked like a champ. After launching  fixparts from within the terminal, typed p to let show the changes.  Then typed w to save and exit from the terminal. Rebooted and all is  well thanks to you. Now Gparted sees the partitions again. I will make  this post solved. THANKS!!

---

### Post by dkim53 on 2013-10-20
oldfred, YOU ARE THE MAN!! Fixparts worked like a champ. After launching  fixparts from within the terminal, typed p to let show the changes.  Then typed w to save and exit from the terminal. Rebooted and all is  well thanks to you. Now Gparted sees the partitions again. I will make  this post solved. THANKS!!

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).
old fred, YOU ARE THE MAN!! Fixparts worked like a champ. After launching fixparts from within the terminal, typed p to let it show the changes. Then typed w to save and exit the terminal. Upon rebooting all is well. Now Gparted sees all the partitions again. I will make this post solved thanks to you.THANKS!!

---

### Post by dkim53 on 2013-10-20
> **oldfred said:**
> Click on this link.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Read the instructions and follow the link to download the 32bit .deb file. You should be able to double click on it and it will install. It is a command line program so from a terminal just run
fixparts /dev/sdX where the X is the drive with your issue.

If instructions are not clear post back terminal output using advanced edit include in code tags (# after highlighting).
old fred, YOU ARE THE MAN!! Fixparts worked like a champ. After launching fixparts from within the terminal, typed p to let it show the changes. Then typed w to save and exit the terminal. Upon rebooting all is well. Now Gparted sees all the partitions again. I will make this post solved thanks to you.THANKS!!

---


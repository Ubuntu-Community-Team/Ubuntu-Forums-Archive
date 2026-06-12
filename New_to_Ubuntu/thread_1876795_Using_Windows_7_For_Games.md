---
title: "Using Windows 7 For Games"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by JoeAdamsIV on 2011-11-06
Hi. I have 1 500GB HDD, and 1 160GB HDD. Both are perfectly healthy. I am currently using Windows 7 Ultimate x64, however I am currently downloading Ubuntu 11.10. I plan on using Ubuntu for everything, and having it on the 500GB HDD. And then I am planning on putting two partitions on the 160GB, both 80GB, one for Windows 7 to play games, and one for backups. What do you think of this? Do you guys think there is a better way to do this?

---

### Post by corrytonapple on 2011-11-06
Just choose dual boot when you install.  Also, install Windows FIRST and then put Ubuntu on there.
BTW, what is the 500GB for?

---

### Post by JoeAdamsIV on 2011-11-06
Well can I dual boot with Ubuntu on one drive, and Win7 on the other?
I would prefer not to put them on the same HDD
And if you are asking what the 500GB will be used for, well mostly movies, music, and some other stuff. I have 280GB free on my Win7 partition, and that is with lots of games. I do not need it all, but I still would prefer to use the entire drive for Ubuntu

---

### Post by JoeAdamsIV on 2011-11-06
EDIT: double post

---

### Post by corrytonapple on 2011-11-06
Yes, you can dual boot with one OS on one drive and the other OS on the other drive.
Okay, I just saw you put you had a 500GB HDD and you didn't say if it was for Data or if it was for an install.
If you put the OS on one drive and the other OS on the other drive, make sure Windows is still installed first on the one drive.  Then when in the installer, choose to install to the other drive.  Once it is done downloading, put it on a USB of CD like it says on the download page and boot up (after changing the boot order in the BIOS of course).
You'll see what I mean.  You'll like it :D

---

### Post by JoeAdamsIV on 2011-11-06
Okay. In that case I am going to do a fresh install of Win7 on the 160GB drive, and then install Ubuntu on the 500GB.

---

### Post by corrytonapple on 2011-11-06
Is there data already on the 500GB drive?  How much are you giving to Ubuntu?

---

### Post by Ricx94 on 2011-11-06
when you install windows on the 160 drive, and you don't want it to take the whole drive, make sure it only partitions as much as you want (about 80gb?). when that is done, slip in your ubuntu 11.10 install disc, and you can install that on the 500 drive no problem.

All in all, you will have ubuntu on a 500gb drive, and windows 7 on half a 160gb drive, with the other half free to be formatted as NTFS or FAT32 so it can be used for data storage.

---

### Post by JoeAdamsIV on 2011-11-06
Yes there is data on the 500GB, my Windows 7. I am currently backing up everything to the 160GB drive, and when it is done I will shrink the partition giving room to install Windows 7. Once windows 7 is installed, I will be formatting all of the 500GB drive, and installing Ubuntu 11.10. After Ubuntu is installed, I will copy everything from the backup onto the 500GB drive, and then resize the Windows 7 partition to 160GB.
This will mean
Ubuntu: 500GB
Windows 7: 160GB
If I need to back anything up I will probably buy another HDD

---

### Post by corrytonapple on 2011-11-06
When you put the data back on the 500GB drive, make sure that your Data Partition is formatted NTFS so that Windows can see it and Ubuntu can see it.
You say:
> 
If I need to back anything up I will probably buy another HDD

But aren't you backing up everything already?

---

### Post by Ricx94 on 2011-11-07
> **JoeAdamsIV said:**
> Yes there is data on the 500GB, my Windows 7. I am currently backing up everything to the 160GB drive, and when it is done I will shrink the partition giving room to install Windows 7. Once windows 7 is installed, I will be formatting all of the 500GB drive, and installing Ubuntu 11.10. After Ubuntu is installed, I will copy everything from the backup onto the 500GB drive, and then resize the Windows 7 partition to 160GB.
This will mean
Ubuntu: 500GB
Windows 7: 160GB
If I need to back anything up I will probably buy another HDD

oh...you are using half of the 160gb drive for backup, and then installing windows 7 on the other half? i would suggest instead backing up to the 500gb drive, installing windows 7 on entire 160 drive, and copying everything over from 500 to 160, then installing ubuntu on 500gb drive.

---

### Post by Mark Phelps on 2011-11-07
Whatever you do, do NOT use the Win7 OS partition as a shared DATA partition.  You will probably want to write to such a partition from inside Ubuntu, and doing that to an win7 OS partition is asking for problems.

It's OK to share an NTFS data partition, but do not share the OS partition.

When you go to install, I've found the best solution in the long run, when you have multiple physical drives, is to put Windows on one drive and Ubuntu on the other -- having only ONE drive connected during the installations.  Not only does that make each drive then bootable on its own, it also prevent the problems where one or the others boot loaders is overwritten during install.

Then, when you're done, connect both drives, boot from the Ubuntu drive, open a terminal, and enter "sudo update-grub".  That will generate a new GRUB menu and when you then reboot, you will be presented with that menu and the option of choosing which OS to use.

---


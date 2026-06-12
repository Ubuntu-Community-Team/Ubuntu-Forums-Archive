---
title: "how to format a &quot;locked&quot; hard-disk (expansion bay)"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by philippsmueller on 2008-09-30
I have a thinkpad that has an expansion bay for a second hard-drive. I use ubuntu 8.04 and wanted to format the hard-disk in the second expansion bay (it had my old ubuntu from my other computer on it). After backing up the data from it, I installed gparted (using the graphical interface, as I really don't understand the command line stuff) and formated it, with the ext3 file-system (my other hard disk uses the same file system). 

I re-started the computer and can see the hard disk. It has one folder on it, that I cannot access called lost+found. I cannot transfer files to the hard drive.  I have no rights to write to it. Going back into Gparted I cannot re-format it. 

I feel at this point the only solution is to take out the hard-drive, put it into a case, connect it to a windows computer and then format it, but I feel it cannot be so hard to format a hard drive under linux (maybe I am just too stupid).

---

### Post by bsharp on 2008-09-30
[https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20at%20Boot](https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20at%20Boot)

That will show you how to partition, format, and have it automatically mounted at boot.

---

### Post by Gannon8 on 2008-09-30
Some expansion bays have a switch that prevents writing to the disk. If yours has one, make sure it is off.

If that still does not work, post the output of this command:
```
sudo fdisk -l
```

---

### Post by philippsmueller on 2008-09-30
Thank you, bsharp! - great page. I tried it, but it does not work. The strange thing is that if I go into the disk on my computer, right-click and go to properties, it tells me that I am not the owner and therefore am not allowed to access it.

---

### Post by Gannon8 on 2008-09-30
Yes, root "owns" the disk. That's why you need to be root to mount it (though gnome runs the mount command as root if you want to access it.)

---

### Post by philippsmueller on 2008-09-30
> **Gannon8 said:**
> Some expansion bays have a switch that prevents writing to the disk. If yours has one, make sure it is off.

If that still does not work, post the output of this command:
```
sudo fdisk -l
```
Here is the output, it is the 250 giga disk (sda) that I want to format...
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac4bac4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76df9909

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
philipp@Mexico:~$

---

### Post by philippsmueller on 2008-09-30
> **Gannon8 said:**
> Some expansion bays have a switch that prevents writing to the disk. If yours has one, make sure it is off.

If that still does not work, post the output of this command:
```
sudo fdisk -l
```
Here is the output, it is the 250 giga disk (sda) that I want to format...
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac4bac4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76df9909

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris
philipp@Mexico:~$

---

### Post by philippsmueller on 2008-09-30
> **Gannon8 said:**
> Yes, root "owns" the disk. That's why you need to be root to mount it (though gnome runs the mount command as root if you want to access it.)
---yikes, I know this must be the most stupid question, how do I become root?

---

### Post by bwang on 2008-09-30
Put sudo in front of the command to run it as root. 
```
sudo su
```
gives you a root terminal.

---

### Post by Gannon8 on 2008-09-30
> **bwang said:**
> Put sudo in front of the command to run it as root. 
```
sudo su
```
gives you a root terminal.

Don't do that.

To run a command as root, use "sudo"
For example:
```
sudo apt-get install package
```
installs a package named "package"
```
sudo mount /dev/sdb1 /mnt/somewhere
```
Mounts partition 1 of the second hard disk to the directory /mnt/somewhere

---

### Post by Zzl1xndd on 2008-09-30
You say you have opened the disk and can see the contents, but when you go to gparted you aren't able to format it cause it is locked (has a picture of a lock next to it?). If that is in fact the case simple unmount the drive, right click on it and select unmount and then you should be able to format it with Gparted. 


A mounted drive can't be altered.

---

### Post by philippsmueller on 2008-10-01
> **Gannon8 said:**
> Don't do that.

To run a command as root, use "sudo"
For example:
```
sudo apt-get install package
```
installs a package named "package"
```
sudo mount /dev/sdb1 /mnt/somewhere
```
Mounts partition 1 of the second hard disk to the directory /mnt/somewhere
sorry, ... it is not a mounting problem, I can unmount it (graphically) and remount it. I tried your command, but it did not recognize it... I will try to format it as a fat32 in windows and then re-insert it into the expansion bay. I just do not understand, how if I partition something and it looks perfectly fine, I have no way of accessing it or even just over-writing/partitioning it. By the way, you guys are amazing, this is the first time I am using a forum! Thank you!!!

---

### Post by philippsmueller on 2008-10-01
> **tweakedenigma said:**
> You say you have opened the disk and can see the contents, but when you go to gparted you aren't able to format it cause it is locked (has a picture of a lock next to it?). If that is in fact the case simple unmount the drive, right click on it and select unmount and then you should be able to format it with Gparted. 


A mounted drive can't be altered.
fantastic! this really helped. I then re-formatted it as a fat32 and now can access it. Not sure why it was locked and where I could have unlocked it before. Also my main drive is also locked, but I can write to it. Thanks again! This is a fantastic resource for the newbie like me.

---


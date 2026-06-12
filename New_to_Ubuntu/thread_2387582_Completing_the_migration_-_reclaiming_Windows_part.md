---
title: "Completing the migration - reclaiming Windows partitions"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by chaoticbob on 2018-03-20
I've recently installed 16.04 on a desktop which was previously running Windows 7. I went for dual boot because I wasn't sure if Linux was going to work with my hardware and my personal way of working and wanted to keep my options open. It's all gone well and I no longer need MS Windows on this machine. So my question - is it possible to expunge Widows and reclaim the whole disk for Ubuntu without a complete reinstall? I could do that (there's no data in the Windows space which I need to keep), but I've configured Ubuntu to some extent and would like to preserve my efforts if possible.
Robin

---

### Post by captionopen2 on 2018-03-20
I don't believe there is a way. I would backup anything you want to keep and then re-install using the whole disk space - if thats what you're looking to do. I think even if their partitioned in the same file format, you can't combine them.

That's from my understanding at-least.

Glad to see another switching from windows!

---

### Post by chaoticbob on 2018-03-20
Thanks. Probably best to go for a clean install then - there's nothing I need to keep on this machine,
Probably not the place to  discuss relative merits of different operating systems, but for me it's a liberation - Windows works fine for many people, but not for me.
Robin

---

### Post by monkeybrain20122 on 2018-03-20
There are ways. There are always ways. :)

If Windows is to the right of Ubuntu, then just boot from a live usb, use gparted to delete the Windows partition and expand the Ubuntu partition to the right. But this is probably not the case since you probably installed Windows first (expanding partition to the left is risky so that is a problem)  so there is a second method

Use fsarchiver to make a clone of your Ubuntu partition, then boot to a live usb to wipe and reformat the whole disk, then use the same live usb to restore your Ubuntu system. That is basically it If you want to go that route I can give you more details. To do this you need an external hard drive to save your image to when your hd is being reformatted of course.

---

### Post by Impavidus on 2018-03-21
There is a way. Depending on the exact layout of the partitions on your hard drive it may be a better option to delete the Windows partition, format the space as Linux partition and mount it somewhere to use as storage space. If you installed Ubuntu in a small partition it may be a good idea to convert the old Windows space into a /home partition. Changing partitions is usually done from a live disk, although as long as it doesn't involve the partition on which your system is installed, it can be done from the installed system.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Most Win7 systems are bios, but if yours is uefi I think you have to clean Windows from the EFI partition too. I'm still on an old bios laptop, so I don't know the details.

---

### Post by oldfred on 2018-03-21
Since Windows is probably the first two partitions, the data partition is a good choice.

But you backup procedure should include all of /home which includes all your user settings, files from /etc or all of /etc if you changed system settings, and a list of installed applications. There are many ways to backup, I prefer rsync.

 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636) 

      
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by yancek on 2018-03-21
Doing a backup is always a good idea but particularly so when modifying partitions.  There is no reason to delete the windows partition, simply format it with a Linux filesystem, create a mount point for it as suggested above and an entry in the /etc/fstab file to mount it as a data partition from Ubuntu.

---

### Post by chaoticbob on 2018-03-22
Thanks. Sounds like the way forward is to reformat and mount the Windows filespace which was preserved by the Ubuntu install as a Linux data partition. I'm afraid I shall need some guidance on how to do that though...

As far as I can make out the machine has a 240GB HD and the install left 160GB for Windows 7, so is running Ubuntu in 80GB. On the left of the (Unity?) Desktop is an icon labelled 160 GB Volume; clicking on that reveals what looks like a Windows filesystem. **lsblk** gives:

```
robin@robin-OptiPlex-780:~$ lsblk -a
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0         0 loop 
sdb      8:16   0 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   0 107.1G  0 part /media/robin/SWISNIFE1
loop6    7:6    0         0 loop 
loop4    7:4    0         0 loop 
sr0     11:0    1  1024M  0 rom  
loop2    7:2    0         0 loop 
loop0    7:0    0         0 loop 
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda2   8:2    0 148.9G  0 part /media/robin/228A133C8A130C43
&#9500;&#9472;sda5   8:5    0    80G  0 part /
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9492;&#9472;sda6   8:6    0   3.9G  0 part [SWAP]
loop7    7:7    0         0 loop 
loop5    7:5    0         0 loop 
loop3    7:3    0         0 loop 
```

**sdb1  **is an external USB drive which happened to be mounted at the time.
Any more detailed advice on how better to interpret the above and progress would be great.
Robin

---

### Post by oldfred on 2018-03-22
Run this, but more for documentation than anything.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Windows typically has a 100MB boot partition (probably your sda1) and main install probably sda2.
You need to make sure you have backed up all your data. 
Many later come back and have one program or game that only works in Windows, so may be best to do a full Windows backup.

Then you can use gparted to delete sda1 & sda2, and create new partition in that space.
Then post this in code tags to preserve format:

To see UUID for mounting new partition into fstab.

 sudo blkid -c /dev/null -o list 
cat /etc/fstab

The fstab and current UUID will be in Summary report also.

If you want to read ahead or do it yourself.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by chaoticbob on 2018-03-22
Thanks! Quite a lot of output:I'll work my way through it and try to understand what it all means. It's all quite fascinating for me - I suppose I must have geek gene somewhere.
Rob.

---

### Post by oldfred on 2018-03-23
Report just is actually running a set of terminal commands. First part is the old bootinfoscript which I still use as it is a command line script. Boot-Repair adds info & can then run some fixes, updates.

You can move /home or just use partition as data or move some folders and link those back into /home. Lots of options.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

      
 [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---


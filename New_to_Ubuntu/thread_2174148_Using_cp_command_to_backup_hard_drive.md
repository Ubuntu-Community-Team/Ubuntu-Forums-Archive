---
title: "Using cp command to backup hard drive?"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by solouko on 2013-09-13
Hello Ubuntu forum,
I'm having a few problems with my hard drives, I thought it would be a good idea to run a bunch of SSDDs in a RAID 0 array, now, it's really fast but my data's not very secure so I have to keep making regular backups.
So far i've been cloning the SSDD array to a standard single HDD with partitions the same size but, now, when i want to update the backup I dont really want to copy the entire disk image again, so my question is:

Q. Can I use the cp (Copy) command to copy an entire drive (eg. /dev/sda) to another drive (eg. /dev/sdb) but use modifiers so that it will only copy the files that are different? 

Different as in, not present on the destination drive, are an older version on the destination drive etc... 

I really could do with the drive being like this so I can access it easily, this is why it's not compressed and because I'm still a recovering windows user it's got to be in an NTFS file system for compatibility with my other machines in the event of an emergencey.  

Please help, thank you.
Any links to tutorials or information would be greatly appreciated.

Regards Carl.

---

### Post by sudodus on 2013-09-13
You can use ***cp*** to copy the content of a partition. But ***rsync*** is a better and more advanced tool for that purpose. See the manual pages

```
man cp
``` and ```
man rsync
```

If you want to copy a whole drive with boot sector and all partitions, to clone it, you can use ***dd*** or ***Clonezilla***. And you should boot from another drive for example your Ubuntu install CD/DVD/USB drive.

dd is nick-named 'disk destroyer' because it does what you tell it to do, not what you intend to do, and it asks no questions, so it is easy to overwrite what you have not yet backed up. But used in the correct way, it is a very good and powerful tool.

I would recommend Clonezilla, that you find easily on the internet.

---

### Post by solouko on 2013-09-13
Thanks for the quick response, i'm actually booted from the live CD at the moment while I copy my ubuntu boot disk to another drive with dd as I need to update the firmware on the boot drive.  
My plan though, Is to eventually copy the boot disk to a RAID 1 array insted, but I will have to free up one of the partitions on my backup drive first which is why I'm trying to update it now.  

I will have a look through the rsync manual and return if i have any questions about it.

---

### Post by CatKiller on 2013-09-13
Don't use NTFS for the target drive; it doesn't understand UNIX permissions. You don't want to have already had the pain that means you need to restore from backup followed by the pain that all your permissions are broken when you do.

---

### Post by |{urse on 2013-09-13
With a dual boot system I usually just pull an image with clonezilla, because I'm lazy, lol

---

### Post by oldfred on 2013-09-13
I use rsync to backup /home and data partitions, but would just reinstall Ubuntu and restore data. Then backups do not include system.

But everyone has different strategies and needs.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

      
 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)


 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

My command:
rsync -aruvlP /mnt/data/Documents /mnt/backup

      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---


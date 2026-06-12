---
title: "Backing up for beginners"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by J Swarthout on 2013-03-31
Hey Everyone


Could you guys suggest the best way/app to back up my Ubuntu system?  I was also wondering if there was any way of backing up applications as well.

---

### Post by black veils on 2013-03-31
to backup settings for your applications, you go into the relevant /home/username folder, show hidden files by pressing **Ctrl + H**, copy-paste all the stuff you want/need. they will be in the main folder, .config, and .kde

best to ignore .cache and .local

there are backup applications available, but as i have never used them, i cannot really say.

---

### Post by oldfred on 2013-03-31
discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

It almost is too many choices and methods. 
Some like full images using clonezilla or similar applications.
Others prefer incremental backups.
And many combine them.

I use rsync and backup /home and some other settings and a list of installed apps. I assume I will just do a new clean install and restore data, so I do not need a full image backup.


 Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)

      
 [URL="https://help.ubuntu.com/community/rsync#Grsync"]https://help.ubuntu.com/community/rsync#Grsync

[/URL]
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
     
[URL="https://help.ubuntu.com/community/rsync#Grsync"]
[/URL]

---

### Post by cmcanulty on 2013-03-31
i love grsync, very fast and easy to use try a dry run first just so you don't erase anything vital. any help needed contact me

---

### Post by ally_uk on 2013-03-31
Easier option mount a external hard disk and transfer your data to it or drop box :)

---

### Post by cmcanulty on 2013-04-01
If you just transfer it every time you back up everything gets copied again. With grsync it is incremental, you only copy new or changed files. I do 230GB so means I back up in a few mins if it was all copied each time it would take forever.

---

### Post by cortman on 2013-04-01
Or just good old rsync:

```
rsync -az /home/cortman/mystuff /media/my_backup_drive
```

for example.

---

### Post by bashhimup on 2013-04-01
You can also go to System Settings, and choose Backup.

---

### Post by bro on 2013-04-01
I like back in time. It makes incremental backups, so after the first time it is quite fast and it remains easy to browse through the past as it shows you all of your files as they were at a given date. Very friendly. 

Besides browser favorites I don't backup any applications. Not sure if it would be easy or good to install from backup since apt keeps track of your installs and versions too. Linux programs are usually spread through the file system and many share libraries. You can backup their settings but the entire app is probably not very workable.

---


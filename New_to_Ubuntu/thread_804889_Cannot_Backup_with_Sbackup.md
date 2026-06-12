---
title: "Cannot Backup with Sbackup"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by lakelovers on 2008-05-23
I'm backing up on a second drive (8-gib) with sbackup. The drive is full and, of course, won't take anymore files. The purge option on sbackup doesn't work or I don't know how to properly configure the purge . I've tried several configurations. No soap. So, I tried to manually delete old files on sdb1 but I don't have permission. I've tried it as root but that doesn't work. When I go to properties on the drive (sdb1), the permissions tab says "The permissions on sdb1 could not be determined."

Any ideas how I could solve this problem?

---

### Post by abhiroopb on 2008-05-23
What exactly do you want to do?

a) to clean out the backed up directory you can do the following in the terminal:
sudo rm -rf <type in wherever the directory is mounted and the folders you want to delete e.g. /media/sdb1/backup>

b) Set purge options: Change logarithmic purging to deleting everything 10 days old (you can set the number of days depending on how much space you have).

Hope this helps. Next time please provide following info: size of eternal hard drive, settings for sbackup (i.e. how frequent you backup).

---

### Post by lakelovers on 2008-05-23
Thanks for your help. That fixed my problem; I should have recalled the "rm" command. When a person knows what he/she is doing it's a snap to get around Ubuntu and Linux. I have a number of linux command index bookmarks but usually I don't know what I'm looking for. I would like to see a reference index where you could state what you want to do (e.g., remove files) and that would take you to the command(s) along with the actions of those commands. I guess that could be called a reverse index. :)

**Edit** Rats. . . I still have a problem. I emptied the sdb1, then re-configured Sbackup and did a manual backup. The backup shows in the /media/sdb1/lost+found but when I go to "backup restore" an error message says "no backups found in target directory." The correct directory shows on the "default" option, though nothing shows in "Available backups." That suggests that the backups went into the wrong directory but the path in Sbackup matches the path in the /media/sdb1 directory tree. I can't figure it out.

---

### Post by abhiroopb on 2008-05-23
Check this for a quick guide: [http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/](http://fosswire.com/2007/08/02/unixlinux-command-cheat-sheet/). Also you could do gksudo nautilus in the terminal which would allow you to browse the files as root (handy in some cases).

Anyway glad to have helped!

---

### Post by lakelovers on 2008-05-23
The fosswire.com is great. Thanks. What I discovered regarding the recover of files, is that if I use the custom option and type in "/media/sdb1/" and apply I get the backed up files. I wonder why the default "/media/sdb1/lost+found" does not return the backup files even though that is the default destination I use in Sbackup configuration..

---

### Post by abhiroopb on 2008-05-24
Sorry I'm a bit confused could you clarify?

(FYI: lost+found: [http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143))

---


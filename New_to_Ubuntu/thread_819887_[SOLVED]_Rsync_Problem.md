---
title: "[SOLVED] Rsync Problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-05
I am using rsync to backup to THREE locations.

**1. NTFS External Harddrive**
```
sudo rsync -rltDvu --progress --delete --exclude-from=/home/abhiroop/Computers/Bash/BackupBigExclude.txt / /media/Applications,\ Games,\ TV/BackUp
```
Here I'm backing up my root directory and excluding some files.

**2. Ext3 External Harddrive**
```
sudo rsync -avu --progress --delete --delete-excluded --exclude-from=/home/abhiroop/Computers/Bash/BackupSmallExclude.txt / /media/sbackup/BackUp
```

Here I'm backing up my root directory (while keeping permissions) and excluding some files.

[B]3. NTFS USB pendrive
[/B]
```
sudo rsync -rltDvu --progress --delete --delete-excluded --exclude-from=/home/abhiroop/Computers/Bash/BackupUSBExclude.txt /home/abhiroop/ /media/disk/BackUp
```

Here I am backing up my home folder while excluding some folders (listed in a separate file). The problem is the first time it backed up everything fine. However, to test I ran the script again and it tried to backup EVERY single file again, with this final error: 
```

UbuntuGuides/About:config.html
      242714 100%  420.26kB/s    0:00:00 (xfer#1158, to-check=56/4822)
rsync: mkstemp "/media/disk/BackUp/UbuntuGuides/.About:config.html.65Ownm" failed: Invalid argument (22)

sent 309259715 bytes  received 25760 bytes  1915080.34 bytes/sec
total size is 1442256901  speedup is 4.66
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

```
Then it stopped. Now each time I run it, it backs up everything, instead of doing (what I thought) rsync should do, which is check for any changes and backup only the changed files. What could the problem be?

This error happens for number 3. Number 1 and 2 are still backing up. But what could the problem be for number 3?

UPDATE:

Problem Solved: just add --modify-window=1. Basically windows uses a different time format and this allows it to accommodate that. The only other issue apparently occurs during daylight savings time :P!

---


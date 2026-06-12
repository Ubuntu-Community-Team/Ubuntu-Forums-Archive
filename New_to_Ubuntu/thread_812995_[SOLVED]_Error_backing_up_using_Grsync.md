---
title: "[SOLVED] Error backing up using Grsync"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by swarup on 2008-05-30
I recently installed Ubuntu Hardy 8.04, and today installed Grsync to backup certain folders in my /Home, to an external HD. I have used Grsync many times in the past, and have never had a problem with it. But today I've tried backing up several different folders, and each time get the same error with nothing getting backed up. 

As an example, here is the report of what happened in Grsync when I issued the backup command for a folder "/home/swarup/Health":

```
*** Launching RSYNC command:
rsync -r -t -v --progress /home/swarup/Health/ /media/disk/Health (Backup)/

building file list ... 
rsync: failed to set times on "/media/disk/Health (Backup)/.": Operation not permitted (1)
 0 files...
4 files to consider
rsync: mkstemp "/media/disk/Health (Backup)/.hand summary B.odt.TOjKd7" failed: Permission denied (13)
./
rsync: mkstemp "/media/disk/Health (Backup)/.hand summary.odt.OsQebg" failed: Permission denied (13)
hand summary 2.odt
rsync: failed to set times on "/media/disk/Health (Backup)/.": Operation not permitted (1)
       13302 100%    0.00kB/s    0:00:00
       13302 100%    0.00kB/s    0:00:00 (xfer#1, to-check=2/4)
hand summary B.odt
       10410 100%    4.96MB/s    0:00:00 (xfer#2, to-check=1/4)
hand summary.odt
       11031 100%    2.10MB/s    0:00:00 (xfer#3, to-check=0/4)

sent 34983 bytes  received 92 bytes  70150.00 bytes/sec
total size is 34743  speedup is 0.99
```



Here is the list of errors reported by Grsync:

```
rsync: failed to set times on "/media/disk/Health (Backup)/.": Operation not permitted (1)
rsync: mkstemp "/media/disk/Health (Backup)/.hand summary 2.odt.mT3jgY" failed: Permission denied (13)
rsync: mkstemp "/media/disk/Health (Backup)/.hand summary B.odt.TOjKd7" failed: Permission denied (13)
rsync: mkstemp "/media/disk/Health (Backup)/.hand summary.odt.OsQebg" failed: Permission denied (13)
rsync: failed to set times on "/media/disk/Health (Backup)/.": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
```

What do I need to do to correct this problem?

---

### Post by swarup on 2008-05-30
I figured out why it wasn't working. It required this terminal command:

```
sudo su -c 'chown -R swarup:swarup /media/disk-2'
```

Now it's working fine.

---


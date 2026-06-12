---
title: "Create a daily backup of my samba shared folder - unbuntu server"
date: 2017-01-10
forum: New to Ubuntu
---

### Post by docked2 on 2017-01-10
Hi,

I installed unbuntu server 16.04.1 LTS, then Samba and succesfully configured it by following a tutorial online. 

I have 2 internal drives in my machine. The first one is the one were my samba shared folder is installed. The second one is unmonted for right now and empty.

Could you please tell me, how I can create an automatic daily save of my samba shared folder to the second hard drive.

1. If i need to mount the second hard drive first, how can I do it ?
2. How can I create this automatic daily backup ?

Thank you su much for your help !

docked

---

### Post by TheFu on 2017-01-10
Welcome to the forums.

Seems you are really, really, new to Linux/Unix.  Not a problem, just important to know.  
To mount a partition or logical volume, there are many different ways.  
1) manually, using the **mount** command.
2) automatic at boot, using the /etc/**fstab** config file.
3) automatic as needed, using **autofs** and the config files that make it work.
None of these things have anything to do with Samba.  So do a little research for how to use those things.  Most people would use the fstab.  
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/) covers these things.

For backups, there are 50 different tools.  Generally, it is done like this:
a) use LVM for the base storage. This means you can freeze a version of the file system, called "taking a snapshot", then mount that to an empty area and backup all the files, settings, installed packages, configuration, without any risk of the files changing in the middle.
b) Use any backup tool you like; using a versioned, automatic, scheduled, tool is smart. I use rdiff-backup, but there are others like duplicity, rsnapshot, rbackup, and 50 others.
c) After the backup finishes, delete the snapshot, so it doesn't suck up space forever.  For a week, this doesn't matter usually 1-2% of total storage used, but leaving snapshots around for a long time can suck up lots of storage.
d) Once your script is working for backups, it is time to automate it via **cron**.  See the server-guide for use of cron.

There are lots and lots and lots of discussions about backups in these forums.  Just be aware that GUI backup tools generally cannot be automated. GUI tools don't run from cron.

Or you can start out really simple and just add a simple mirror to the crontab using rsync.
```
$ sudo rsync -avz SOURCE TARGET

``` It really is that simple when no devices or other "special files" are involved.  Tar and similar tools aren't good for backing up systems or anything over 5G of data.  Too inefficient.  Almost anything based on librsync will be efficient on storage and networking and if you need to do remote backups, they will use ssh automatically.

My signature has other links for this stuff.

---


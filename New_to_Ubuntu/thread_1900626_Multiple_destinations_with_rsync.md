---
title: "Multiple destinations with rsync"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by Sempa on 2011-12-26
**Background**
I've just recently installed Ubuntu 11.10 and I thought the first thing I'd do was figure out how to back up everything. I'll be using an external hard drive for the backup.

It seems as if using *tar* is an easy way to make non-incremental backups and using *rsync* is an equally easy way to make incremental backups. Seeing as a full backup might take some time to make, I was thinking of backing up with *rsync* once a day and making full backups a little less often.

After having tinkered a little, I came to realize that it took two and a half minutes to synchronize my SSD with the external hard drive with *rsync*, while it took half a minute **less** to make a tar archive of the same files and move the archive to the external hard drive! And this was after having run *rsync* once already. In other words, making an incremental backup with virtually no changes made took longer than making a full backup!

Not giving up on *rsync* quite yet, I tried using it on the same files but with a destination on the SSD instead of on the external hard drive, and this took less than a second after having run *rsync* the first time.

[B]Question
[/B]I'm wondering if there's any way to specify multiple destinations for *rsync* so that it uses the first destination to check which files to update and updates the files on all destinations. If so, I'd be able to keep a "backup" on the SSD that I'd use to speed the incremental backup to the external hard drive up.


Now that I think of it, it doesn't seem like a very efficient solution to essentially have a copy of each file on the SSD ... suggestions on a better way to make incremental backups are welcome!

---

### Post by Dennis N on 2011-12-26
Is the external hard drive formatted with a FAT file system? If so, that is why your 'incremental' backup is slow. 

You need to use the option

```
--modify-window=1
```

to get fast incremental backups. Example:

```
rsync -rt --modify-window=1 <source> <destination>
```

I has to do with accuracy of the time stamps. The rsync man page explains why: 

> When  comparing  two  timestamps, rsync treats the timestamps as    being equal if they differ by no  more  than  the  modify-window      value.   This  is  normally  0 (for an exact match), but you may       find it useful to set this to a larger value in some situations.       In  particular,  when  transferring to or from an MS Windows FAT       filesystem (which represents times with a 2-second  resolution),        --modify-window=1 is useful (allowing times to differ by up to 1       second).

So, files in you source directory can get copied again even if they are really unchanged from the last sync because the time stamps are slightly different at the destination.

---

### Post by Sempa on 2011-12-26
The external hard drive is formatted with an NTFS file system.

The precise command I'm using is

```
sudo rsync -az / --exclude=/backup --exclude=/cdrom --exclude=/dev/*  --exclude=/lost+found/*
--exclude=/media/* --exclude=/mnt/* --exclude=/proc/* --exclude=/sys/* --exclude=/tmp/*
--exclude=/var/cache/apt/* /media/LaCie/ubuntu
```For some reason, it seems to take only about one minute to run the command now; earlier it took two minutes every time I ran it ...!

I tried using the --modify-window option but it doesn't seem to make any difference, regardless of window size.
I also tried using only the *r* and *t* flags and that takes roughly half a minute, if that's of any importance.

When I time the commands, I typically get results like those below (with -rt and -az respectively)

```
real    0m32.481s
user    0m2.232s
sys    0m10.261s

real    1m0.692s
user    0m2.240s
sys    0m17.789s
```

---

### Post by Dennis N on 2011-12-26
Well, the man page only mentions FAT, so no information whether NTFS behaves the same. I don't know.

FYI:

I only back up folders under home to an FAT external drive, so only ordinary files are involved. 

Using:

 ```
rsync -rti --modify-window=1 <source dirs> <destination> 
```

-i option gives a list of changes.

You can also use the --stats option to get info on what and how much is transferred. 

Good Luck.

---

### Post by oldfred on 2011-12-27
You do know when you back up Linux partitions to a Windows formatted partition, you lose permissions & ownership. You then cannot easily recover system files. Data files can be easily reset to your owner & typical permissions. 

The tar backup can be copied and recovered since it is compressed and will maintain permissions & ownership.

I like rsync so I can easily see a file and do incremental backups & I find from Linux to Linux partition to be very quick.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Sempa on 2011-12-27
All right, I've got it working properly now!

When I ran *rsync* with the i flag, it'd say that all files were being updated, so I decided to format the drive with the ext4 system. After having run the *rsync* command once, each subsequent run was lightning fast (less than a second)!

And seeing as ext4 is not really a Windows format, I guess I won't have any problem with lost permissions and ownerships when I try to restore things either.


Thanks a lot for the help and input, Dennis and Fred! :)

I'll mark this as solved even though the original "question" wasn't really answered, as the actual issue I was having has been solved.

---


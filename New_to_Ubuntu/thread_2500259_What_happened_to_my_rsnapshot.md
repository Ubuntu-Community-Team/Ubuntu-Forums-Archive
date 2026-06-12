---
title: "What happened to my rsnapshot?"
date: 2024-08-28
forum: New to Ubuntu
---

### Post by xboomz on 2024-08-28
Hello,

I am using Ubuntu 24.04 LTS and trying to backup the system using rsnapshot.

I have installed rsnapshot and configured it to backup selected directories to the remote disk(btrfs, nfs4) mounted to /mnt/sys-backup/. md1 on the Ubuntu system is xfs, raid 1.

The issue is that it seems like each backup snapshot has similar size although I expected minimal increase between the snapshots. Below is the result from my terminal:

root@dalegal-server-w:/mnt/sys-backup/dalegal-server-w/snapshots
# du -sh --count-links */
7.0G    basic_setting_after_install/
42G    daily.0/
41G    hourly.0/
37G    hourly.1/
37G    hourly.10/
43G    hourly.11/
37G    hourly.2/
37G    hourly.3/
37G    hourly.4/
37G    hourly.5/
37G    hourly.6/
37G    hourly.7/
37G    hourly.8/
37G    hourly.9/
root@dalegal-server-w:/mnt/sys-backup/dalegal-server-w/snapshots
# du -sh */
7.0G    basic_setting_after_install/
42G    daily.0/
34G    hourly.0/
29G    hourly.1/
29G    hourly.10/
29G    hourly.11/
29G    hourly.2/
29G    hourly.3/
29G    hourly.4/
29G    hourly.5/
29G    hourly.6/
29G    hourly.7/
29G    hourly.8/
29G    hourly.9/


I suspect rsnapshot isn't functioning properly. Isn't rsnapshot supposed to compare the system and backup only differences using hard links?

Please help me.

---

### Post by ajgreeny on 2024-08-28
I may be misunderstanding you but surely when **du** is showing sizes of 29G without any obvious changes it may simply be the result of your choice of ** du -sh** not giving sufficient size detail.

If you run **du** without the **-h** option you may find that the sizes really are slightly different.

How much size difference are you anticipating?

---

### Post by xboomz on 2024-08-28
Thank you for reply, ajgreeny. Doesn't the size of each snapshot mean there was disk usage increment of the said size? As far as I know rsnapshot provides incremental backup of snapshots, which means it only adds new data to the previous version and avoid redundancy. There had been no activity for hours when those snapshots were made, so ideally subsequent snapshots should be close to zero or minimal value like several KB.

---

### Post by TheFu on 2024-08-28
I haven't used **rsnapshot** in about 20 yrs.  It doesn't do intra-file incremental changes.  When any byte of the file changes, a complete, new, copy, gets put in the the last version directory structure. If you want intra-file incremental changes, you need a different tool, like **rdiff-backup**.  Both methods greatly reduce storage used. There are times when hardlinked versioning uses less storage and there are times when reverse-differental versioning uses less storage.

If I had to guess, between hour 1 and 0, about 5GB of changed files happened.

Btrfs and zfs will both lie about disk used.  Hardlinked files use an inode, but not more space.  Inodes are pre-allocated when the file system is created (for most file systems), so that doesn't impact storage used whether there are 1 link to the actual file data or 50.  

I won't use BTRFS - not a good choice for my needs, but I use ext4.  I created a file inside V1/ and made a hardlink inside V2/ of the ../V1/file.
```
$ tree V[12]
V1
&#9492;&#9472;&#9472; file1.mkv
V2
&#9492;&#9472;&#9472; file2.mkv
```
So you understand the directory structure for my test.

```
$ ls -Rfl V[12]
V1:
total 1255280
drwxrwxr-x 10 tf tf      20480 Aug 28 10:57 ../
-rw-rw-r--  2 tf tf **1285374974** Aug 28 10:57 file1.mkv
drwxrwxr-x  2 tf tf       4096 Aug 28 11:00 ./

V2:
total 1255280
drwxrwxr-x 10 tf tf      20480 Aug 28 10:57 ../
drwxrwxr-x  2 tf tf       4096 Aug 28 11:00 ./
-rw-rw-r--  2 tf tf **1285374974** Aug 28 10:57 file2.mkv
```
file1 and file2 are exactly the same size because they are pointing at the same data storage on disk.  However, 
```
$ du -shc V[12]
1.2G    V1
4.0K    V2
1.2G    total
```
So, V2 even with a 1.2GB file inside is only using 4Kb.  That's what a hardlink does.  If we use the 'stat' command, we will see that the head inode to each data storage file is identical.
```
$ stat V1/file1.mkv V2/file2.mkv
_  File: V1/file1.mkv_
  Size: 1285374974      Blocks: 2510512    IO Block: 4096   regular file
Device: fd0dh/64781d    Inode: **4325378**     [COLOR="#FF0000"]Links: 2
[/COLOR]Access: (0664/-rw-rw-r--)  Uid: ( 1000/      tf)   Gid: ( 1000/      tf)
Access: 2024-08-28 10:57:16.042152945 -0400
Modify: 2024-08-28 10:57:24.802090904 -0400
Change: 2024-08-28 11:00:27.272787335 -0400
 Birth: -
_  File: V2/file2.mkv_
  Size: 1285374974      Blocks: 2510512    IO Block: 4096   regular file
Device: fd0dh/64781d    Inode: **4325378**     [COLOR="#FF0000"]Links: 2[/COLOR]
Access: (0664/-rw-rw-r--)  Uid: ( 1000/      tf)   Gid: ( 1000/      tf)
Access: 2024-08-28 10:57:16.042152945 -0400
Modify: 2024-08-28 10:57:24.802090904 -0400
Change: 2024-08-28 11:00:27.272787335 -0400
 Birth: -
```
We can also see there are 2 links to the same data.

```
$ du -sh --count-links  V[12] 
1.2G    V1
1.2G    V2
```
Shows a different, bogus, size used.

If you need a GUI tool that works with hardlinked version files, check out Back-in-Time.  [https://github.com/bit-team/backintime](https://github.com/bit-team/backintime)  I think it is in the repos.  I set it up for my Mom's PC and she was able to find files in the different versions.  

There are a few limitations for all hardlink-based backup tools, some can be very, very, important.
[LIST]
[*]File owner, group, permissions, ACLs and xattrs aren't also versioned. Only the last copy of the file will have the correct file metadata, unless something inside the file forced the file to change too.
[*]Hardlinks only work within the same file system.  Just be certain that the source and destination file systems are different, but that all backup versions fit into a single file system.  That isn't hard these days.
[/LIST]

I've been using **rdiff-backup** since around 2010.  The most recent version of the backups still looks like an rsync mirror.  Older versions are diffs. Also, rdiff-backup stores any owner, group, ACL, permission changes along the way too.  Since about 2020, rdiff-backup has handled sparse files as expected too, but it didn't always.

---


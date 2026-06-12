---
title: "Scheduled Backup Program For 18.04 64 Bit"
date: 2018-05-29
forum: New to Ubuntu
---

### Post by jerryz2 on 2018-05-29
Hello,

New to Ubuntu and looking for the following:

A program that can provide a scheduled backup from one USB drive to another. Running 18.04 64 bit in a VM and want to schedule a nightly clone of some data.

Thanks
Jerry

---

### Post by TheFu on 2018-05-29
Welcome to the forums.

Unix systems, including  Linux and Ubuntu have tools that we put together to automate things in the way we like.  But it is differnent from most desktop-centric operating systems, so some of the ideas may seem odd.

One of those things is **cron**.  Cron is how we schedule things to happen periodically.  Cron runs regardless of whether any user is logged in or not.  It doesn't do any error checking, so that it up to the person who creates the script to be run by cron.  Also, it doesn't support GUI programs, so whatever program you want to use shouldn't have a GUI.

As for programs to copy data between 2 different storage devices, there are 500 of those each with a slightly different purpose.  If you want a mirror copy, I'd use **rsync**. If you want versioned backups and both disks are running Linux file systems (not NTFS or vfat/fat32), then I'd use **rdiff-backup**.  If the source runs a Linux file system but the target does not and versioned backups are desired, I'd use duplicity.  All of these tools have to be run with elevated permissions (i.e. root) so file and directory permissions are maintained.  You can run them without root, but the owner and group would be lost. This makes it data, not a backup.  For large media files or a single userid's HOME, that probably doesn't matter, but for program and OS files, it would make restoring useless.

A mirror really isn't the best sort of backup since malware can corrupt files, which would be cloned with the corruption. Versioned backups really are very important these days.

If you provide a little more data about the file types and file systems involved and how they are mounted, then we can provide more complete answers.

Some light reading:
* fstab mounting [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
* [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) - I'd probably setup **autofs** myself
* cron [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
* rsync [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

As for accessing USB devices from inside virtual machines, that is something you'll need to figure out based on the hypervisor being used.

---

### Post by jerryz2 on 2018-05-29
Thank you for your reply. Looks like rsync would be the way to go. If I wanted to perform a daily backup of the two drives, would I need the trailing forward slash?

What would a cron look like for a daily backup?

i.e.

rsync -ruv --delete /media/myname/driveA/ /media/myname/driveB/

---

### Post by TheFu on 2018-05-29
```
#!/bin/bash 
EXCLUDES="--exclude .Trash-1000 --exclude lost+found"
ionice rsync -av --stats --progress $EXCLUDES --delete-after /D/ /misc/b-D/
```

is how I do a media rsync between 2 ext4 file systems.  The file system type matters.
Both storage locations mount via autofs, so they aren't always mounted, unless a request is made.

There are different versions of a crontab with slightly different formats.

---

### Post by jerryz2 on 2018-05-30
Thank you. This looks great. How do I schedule this to run every day?

---

### Post by TheFu on 2018-05-30
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) has examples.

---


---
title: "How to Determine Full Path to Second Drive"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by decatur-linux on 2013-04-18
I have a desktop with three drives in it.  They display as "320Gb Hard Disk/21Gb Filesystem", "320Gb Hard Disk/297Gb Filesystem", and "File System".  I am aware that I booting Ubuntu from the drive "File System" and that the other two are auxiliary storage.

I want to setup a backup process using **rsync** to backup my home directory to the "297Gb Filesystem", but I don't know how to express the destination drive in "full directory path" terms, i.e., sda/sdb or whatever.  What is a CLI command that I can use to make this determination? [I presume that rsync doesn't have a GUI and will be run from the command line].

Thanks.

---

### Post by Cheesemill on 2013-04-18
If you are using your file manager to mount the drives when you click on them then they could be in a couple of places...

If they are removable drives you'll probably find them in /media/<USERNAME>/
If they are permanently connected they will be in /run/user/<USERNAME>/gvfs (for Ubuntu 12.10 and later) or in /home/<USERNAME>/.gvfs/ (for 12.04 and earlier).

You can find out the full paths of all of your currently mounted drives by running the 'mount' command.

> I presume that rsync doesn't have a GUI and will be run from the command line
There is a GUI that you can install called [grsync]("apt://grsync"), although I don't use it myself.

---

### Post by decatur-linux on 2013-04-18
Thank you, Cheesemill.  The command **mount** is the quickest and obvious one.  I'm running Ubuntu 10.04 and don't mount the drives manually, so I didn't think of that.  I eventually found out what I need to know by the more complicated command **sudo parted -l**.

One more question concerning **rsync**:
I've never used **rsync**, and I don't even know what format the output will be in;  **mount** identifies the destination drive as "/dev/sdb3 on /media/ad0f009f-xxxx-xxxx-xxxxxxxxxxxx type ext3 (rw,nosuid,nodev,uhelper=udisks)"
My question is this: do I define the destination disk in the **rsync** command as "/dev/sdb3", or as "/media/ad0f009f-xxx-xxx-xxxxxxxxxxxx"?

Thanks again.

---

### Post by Dennis N on 2013-04-19
> **decatur-linux said:**
> 
My question is this: do I define the destination disk in the **rsync** command as "/dev/sdb3", or as "/media/ad0f009f-xxx-xxx-xxxxxxxxxxxx"?

Thanks again.

The path to the target is through the mount point, so would begin with /media/ad0f009f-xxx-xxx-xxxxxxxxxxxx. This gets you to the root of the filesystem on the backup drive. You can add any folder or path to this.

**Tip**: You can label the partitions (filesystems) on a drive, and the label can be used in the path. this makes it easier to identify. Do some reading and learning about labels, and tools to create them. One such tool is e2label, a command line tool.

For example, the target filesystem might be labeled 'backups' then the path can begin with:

/media/backups/...

---

### Post by oldfred on 2013-04-19
I like labels and label every partition. But I labeled my backup partition Backup but created a mount of backup and now get confused as my rsync mounts as backup, but Nautilus may see it as Backup. And I cannot have it mounted as both.

I added this to my rsync script.

> # ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup


       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh


 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

      
 Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---


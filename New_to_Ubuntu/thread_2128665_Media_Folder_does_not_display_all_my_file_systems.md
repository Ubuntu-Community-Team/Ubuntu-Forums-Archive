---
title: "Media Folder does not display all my file systems"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by ozark_hillbilly on 2013-03-23
After changing Fstab file and getting my /home partition properly linked to 12.04 when i look at folders, and in particular my file subsystems for devices and computer, it does not list all of them. See attachments of screenshots. Is this a mounting issue or what?
GParted shows SDB1 to not be mounted. ????

Media folder does not list all the existing file subsystems (partitions).....

The reason I am trying to "find" these devices/file systems is that I did in fact have backups made regularly to my other hard drive. I looked at them under Lucid Lynx install before upgrading to 12.04. If I re-install apps like Google Chrome and Evolution I DO NOT want to overwrite my Bookmarks or Address Book and lose the data unless I know I have it saved in my backup archive. I am very leery right now to do any app installs for fear of losing or having existing data files in my \home partition overwritten. Verifying my backup would be reassuring but I cannot see it listed in Devices or in the Media folder.

---

### Post by NimalNet on 2013-03-23
Hi Ed

It seems that your NTFS partition is not mounted

Try
$mkdir ~/ntfs
$mount -t ntfs /dev/sda1 ~/ntfs

---

### Post by ozark_hillbilly on 2013-03-23
I have SDB1 not mounted as well. What file do you modify to have these automatically mounted on boot up?

---

### Post by Bashing-om on 2013-03-23
ozark_hillbilly     ;
Still hanging with you. You are looking good !
sdb drive: I am a strong advocate of only mounting my backup data drive as on demand - thereby minimizing any adverse effects from any cause. That entails manually mounting the drive and REMEMBER to (un-)mount the drive prior to logging off or shutting down . Failure to (un-)mount the device may result in filesystem corruption.

Here are the tutorials on fstab and mounting that I expect will set your mind at ease (looks like all your files are intact) to access them.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) 

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

On going Compilation of all things ubuntu:
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)[INDENT=4]
just try'n to help

[/INDENT]

---

### Post by ozark_hillbilly on 2013-03-23
Hey Bashing-om,

I was wondering if I manually mount my backupdrive would that be a problem for auto backup routines? Or do they mount the drive themselves when the archive is made?

Ed

---

### Post by Bashing-om on 2013-03-23
ozark_hillbilly;

Well, if it were me I would write a script to mount the drive in the backup routine. To be honest, I do all my backing up manually, If something were to go wrong I want to be there immediately to take command of that slopyation ! Like you My backups are important and I take undue care that I have my data, That, That I am not going to do without -  I have also duplicates out side of my computer.

Like you I live in these hills of Arkansas, power fluctuations and outages at any time have plagued me in the past, several times I have had to resort to a (re-)install of my system (or my wife's !). Practice, I can now (re-)install in 20 minutes and within an hour all my data is restored (scripts) and I am fully back up.[INDENT=2]
just my thoughts 
[/INDENT]

---

### Post by Bashing-om on 2013-03-23
ozark_hillbilly;

Not to leave you high and dry //but, I was up at 4:00 this am and the hours are telling now. I will check your status in the A.M.
[INDENT=2]
learning may be obtained by effort but sleep when one can

[/INDENT]

---

### Post by ozark_hillbilly on 2013-03-23
@ Bashing-om

I am absolutely puzzled as to why my Backupdrive does not show my archives. There are old ones (.ful) but not the latest ones I looked at through 
root/media/Backupdrive prior to doing a clean install of 12.04. Even if the clean install overwrote the /media folder it should not have had any effect on the hard drive physical data itself. It showed, when still using Lucid Lynx, the .inc files from a scheduled backup a couple days ago but they're not there now. I am bamboozled now. If the google browser and evolution installs don't link to my pre-existing separate /Home partition then I am screwed royally on Bookmarks and Contacts.

---

### Post by Bashing-om on 2013-03-24
ozark_hillbilly 	;

What pops to mind is that the respective partitions containing your data are not mounted. Bear in mind it is partitions not devices that are mounted.
I think best from a CLI environment. Let's take a look at all the partitions on your system, compare that to what you presently have mounted (available).
To look at the partitions -> terminal code:
```
sudo fdisk -lu
```
To see what is mounted:
```
mount
``` compare that to :```
cat /etc/mtab
``` just to make sure nothing dorky is going on.
Though mount points can be established in any directory, it is recommended to make the mount points in either "/mnt or /media" depending on how one wants the file manager to relate.
Look to see what mount points have been established there:
```
 ls -la /mnt
ls -la /media
```

[INDENT=3]
tells the tale

[/INDENT]

---

### Post by ozark_hillbilly on 2013-03-26
Bashing-om,

Here is my terminal results:

root@ed-Desktop:/home/ed# sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00460046

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       160992122   488396799   163702339    5  Extended
/dev/sda5       161003493   283884614    61440561   83  Linux
/dev/sda6       160992124   161003429        5653   82  Linux swap / Solaris
/dev/sda7       283885568   488396799   102255616   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36de36de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   152253022    76126480   83  Linux
/dev/sdb2       152254462   312580095    80162817    5  Extended
/dev/sdb5       214048768   308457471    47204352   83  Linux

***********************************************************************
show what is currently mounted:

root@ed-Desktop:/home/ed# mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /home type ext3 (rw,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ed)


*********************************************************************
compare to mtab:

root@ed-Desktop:/home/ed# cat /etc/mtab
/dev/sda7 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda5 /home ext3 rw,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ed/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ed 0 0
root@ed-Desktop:/home/ed# 


********************************************************************


root@ed-Desktop:/home/ed# ls -la /mnt
total 8
drwxr-xr-x  2 root root 4096 Apr 19  2012 .
drwxr-xr-x 23 root root 4096 Mar 24 15:42 ..



root@ed-Desktop:/home/ed# ls -la /media
total 20
drwxr-xr-x  5 root root 4096 Mar 24 22:26 .
drwxr-xr-x 23 root root 4096 Mar 24 15:42 ..
drwxr-xr-x  2 root root 4096 Mar 23 20:20 Backupdrive
lrwxrwxrwx  1 root root    7 Mar 22 21:45 floppy -> floppy0
drwxr-xr-x  2 root root 4096 Mar 22 21:45 floppy0
drwxr-xr-x  2 root root 4096 Mar 23 21:06 sdb5
root@ed-Desktop:/home/ed# 

What do I need to do to make a task to mount my Backupdrive?

Ed

---

### Post by Bashing-om on 2013-03-26
ozark_hillbilly;

Setting up to mount your Backupdrive should be straight forward. I have this line in my routine that works great.
> 
     mount /dev/sdb1 /mnt/backup
sleep 2 where my "backup" drive is sdb1 and the name in my mount point is "backup" and the sleep command just to make sure that things do not happen so quickly the partition is not mounted yet.

Again, make sure the partition is unmounted prior to logging off/out, at some point when all done run
```
 umount /mnt/backup
``` with the elevated privileges at some point.

I also do not see that you have set up a means - at this time - to access your Windows stuff or other ubuntu partitions( maybe you have set it up in /etc/fstab) ..
[INDENT=4]it's all good

[/INDENT]

---

### Post by Bashing-om on 2013-03-26
ozark_hillbilly;

As an afterthought; Would you like a copy of my routine (bash script). It is crude but it serves my purposes admirably and I know explicitly what I am backing up and where these files are located. I also have written a corresponding script to restore these files to my operating system. Been there - done that - and I learned the hard way! I will not loose my data (files) again.
[INDENT=3]
it's all in knowing how 

[/INDENT]

---


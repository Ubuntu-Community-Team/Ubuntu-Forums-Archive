---
title: "Adding a SATA drive"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by wbrokow1 on 2008-08-01
I have my 8.04 system up and running, everything seems to be ok.
I have one sata drive on an onboard sil3112 chip. It has been low level formatted and appears within ubuntu bu I can't access it.
Do I have to put a filesystem on it like I did in gentoo?
Also, I can't get su privileges.

Any help is appreciated.
THanks

---

### Post by collinp on 2008-08-02
Yes, you have to have a filesystem on it to mount the drive. And, in Ubuntu we use sudo instead of su for many reasons. To use sudo run:

```
sudo whksdisoeisjo
```

Replace all the gibberish with a command you need to run as su. After that it will ask you for your password, then it will run the command.

---

### Post by Rocket2DMn on 2008-08-02
If you need to format the drive, I suggest using GParted, it is available in the repositories
```
sudo apt-get install gparted
```
You can then access it from System->Administration->Partition Editor.  Remember you cannot fiddle with partitions that are mounted.  If you need help setting up an fstab entry after you format it, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
after you do the formatting and partitioning.

---

### Post by wbrokow1 on 2008-08-02
ok thanks, here is th output:

[code]
woody@woody-desktop:~$ sudo fdisk -l
[sudo] password for woody: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x476c476b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e6a1

   Device Boot      Start         End      Blocks   Id  System
woody@woody-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b212fd87-9d61-4fc4-a07b-c82cac4701bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7dea1d9a-7d5c-4a9f-9b4d-c74c179341b9 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
woody@woody-desktop:~$ sudo blkid
/dev/sda1: UUID="b212fd87-9d61-4fc4-a07b-c82cac4701bb" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7dea1d9a-7d5c-4a9f-9b4d-c74c179341b9" 
/dev/sdb1: UUID="d5a80aee-3040-43c5-a1fe-89a3e4d740e0" TYPE="ext2" 
woody@woody-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/woody/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=woody)
/dev/scd1 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=woody)
woody@woody-desktop:~$ 

[code]
the 160 gig drive is the one I have added.
What next?
I know I have to add a line the the fstab.
THanks so much for your help.

---

### Post by ConMan318 on 2008-08-02
[http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System](http://www.techotopia.com/index.php/Adding_a_New_Disk_Drive_to_an_Ubuntu_Linux_System)

I followed that to add my slave drive and it's a great tutorial.

---

### Post by Rocket2DMn on 2008-08-02
It appears that the sdc drive (the one in question) does not have a partition on it yet (it is unformatted).  You need to open GParted like I said in my previous post, and from there select the sdc drive from the drop down box at the upper right corner.  You can then add a partition to the drive (most likely ext3 filesystem).  You will probably just want one partition to cover the entire drive.

That needs to be done before we can proceed with adding an fstab entry.  Then can you please repost
```
sudo fdisk -l
sudo blkid
```
and I will help you to add the correct fstab line.

---

### Post by wbrokow1 on 2008-08-02
ok thanks, this is what i got:

woody@woody-desktop:~$ sudo fdisk -l
[sudo] password for woody: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x476c476b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e6a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux
woody@woody-desktop:~$ sudo blkid
/dev/sda1: UUID="b212fd87-9d61-4fc4-a07b-c82cac4701bb" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="7dea1d9a-7d5c-4a9f-9b4d-c74c179341b9" 
/dev/sdb1: UUID="d5a80aee-3040-43c5-a1fe-89a3e4d740e0" TYPE="ext2" 
/dev/sdc1: UUID="f59c410c-52b2-4c9b-a761-83f65558f23f" SEC_TYPE="ext2" TYPE="ext3" 
woody@woody-desktop:~$

---

### Post by Rocket2DMn on 2008-08-02
Alright, let's open fstab for editing:
```
gksudo gedit /etc/fstab
```
Now add this line to the bottom:
```
UUID=f59c410c-52b2-4c9b-a761-83f65558f23f /media/sdc1 ext3 defaults 0 2
```
Save and close.  You can use whatever mount point you want, I simply chose /media/sdc1 - if you decide on something else, just make sure it doesn't have spaces in it, and change it appropriately in the next command.
Now create the mount point:
```
sudo mkdir /media/sdc1
```
Now tell it to mount:
```
sudo mount -a
```
If it complains, post the output back here, otherwise it is mounted!

---

### Post by wbrokow1 on 2008-08-02
ok thanks it's mounted now.
It did give an error but on reboot it mounted.

DO you think you could help me out with dar.
I can't seem  to get it to extract from my cdrom to any directory.


I get:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             229G  2.8G  214G   2% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   64K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sdc1             148G  188M  141G   1% /media/sdc1
gvfs-fuse-daemon      229G  2.8G  214G   2% /home/woody/.gvfs
/dev/scd1             4.0G  4.0G     0 100% /media/cdrom0
woody@woody-desktop:~$ dar -x /media/cdrom/FMUSIC /media/sdc1
Parse error on command line (or included files): Unknown argument : /media/sdc1
woody@woody-desktop:~$ 


Thanks for any help.
I'll take this up in the morning.

---

### Post by Rocket2DMn on 2008-08-02
Sorry, you need to start a new thread for that.

---

### Post by wbrokow1 on 2008-08-02
how do I put an an official "thank you" into your tally?

---

### Post by Rocket2DMn on 2008-08-02
There is a little blue and gold ribbon in the bottom right corner of posts.  This is typically used for responses that you find to be very helpful.  Use sparingly, otherwise it loses its significance :)

---


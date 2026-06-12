---
title: "Problems moving Home Directory?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by mapes12 on 2008-05-30
I have created 2 new partitions on my HDD one of which I am trying to move my Home directory across to. I am following this guide:

[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Everything goes OK until I get to the bit where I need to edit my /etc/fstab

The guide says it should look like this:

> #-------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hda5 /home ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /mnt/sys2 ext3 defaults,errors=remount-ro 0 1
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/.iso/ubuntu-5.04-install-i386.iso /mnt/iso iso9660 ro,loop,auto 0 0
#---------------------------------------------------------------------------------------------------------
But mine look like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=271f9285-7831-4c20-aeb8-98534c6e28d8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=ebb5eb7e-aedf-4bae-9ba9-4bd193eff076 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

As you can see sda1 (main partition) and sda5 (swap) are commented out. I tried adding the line per the guide

> /dev/sda3 /home ext3 defaults,errors=remount-ro 0 1
after the entry to sda1 and before sda 5 but on restarting my machine the is no sign of my home partiton appearing on the new partition which BTW is sda3. The other new partion which I haven't done anything with yet is sda4.

If I restart the machine then Places>Computer I can see one of the new partions mounted (don't know if its sda3 or sda4, whereas before I started this exercise I could see icons for both new partitions, unmounted) but there is no sign of the moved home directory on it.

If I use sfdisk to query my drives I get:

> mark@ubuntu-desktop:~$ sudo sfdisk -l

Disk /dev/sda: 2491 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    818     819-   6578586   83  Linux
/dev/sda2       2382    2490     109     875542+   5  Extended
/dev/sda3        819    1600-    782-   6277120+  83  Linux
/dev/sda4       1601    2381     781    6273382+  83  Linux
/dev/sda5       2382+   2490     109-    875511   82  Linux swap / Solaris
mark@ubuntu-desktop:~$

Can anybody help me out here please?

---

### Post by Duck2006 on 2008-05-30
This may help.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by cmnorton on 2008-05-30
I suggest you mount the whole drive in /media, and you'll need to create a directory there; suggest the device name of the drive.

This following is some output from a Fedora 6 system, but the analogy should be close.

LABEL=/1                /                       ext3    defaults        1 1
LABEL=/boot1            /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
LABEL=SWAP-sda2         swap                    swap    defaults        0 0
/dev/sdb1         /mnt/sdb1         ext3     defaults,errors=remount-ro 0 1

/dev/sdb1 is being mounted in /mnt/sdb1.

Here is what's under /mnt/sdb1

cd /[dbadmin@steamboy ~]$ cd /mnt
[dbadmin@steamboy mnt]$ ls -l
total 20
drwxr-xr-x 2 root root 4096 Mar 31  2007 cdrom
drwxr-xr-x 2 root root 4096 Jun 13  2007 floppy
drwxr-xr-x 4 root root 4096 Dec 20 11:03 sdb1
drwxr-xr-x 2 root root 4096 Feb 20 11:26 sdc1
drwxr-xr-x 2 root root 4096 Aug 20  2007 usb
[dbadmin@steamboy mnt]$ cd sdb1
[dbadmin@steamboy sdb1]$ ls -l
total 20
drwxr-xr-x 34 root root  4096 May  8 08:19 home
drwx------  2 root root 16384 Dec 20 10:57 lost+found

Here is the link to home in /

lrwxrwxrwx   1 root root    14 Dec 20 11:02 home -> /mnt/sdb1/home

The Ubuntu fstab is using labels instead of hardware notation, but you should be able to put in a conventional line in fstab. My guess is you have something else not set up, like the soft link to home, the mount directory, or something like that.

---

### Post by mapes12 on 2008-05-30
UPDATE:

I think something worked because if I edit /etc/fstab back to its original state then restart the machine I get an error message telling me the system can't find my home directory. So I put the /dev/sda3............. line back in /etc/fstab and I can long in normally.

Also, I have attached a gparted screen shot of the system current state if that helps.................

---

### Post by sisco311 on 2008-05-30
> **mapes12 said:**
> UPDATE:

I think something worked because if I edit /etc/fstab back to its original state then restart the machine I get an error message telling me the system can't find my home directory. So I put the /dev/sda3............. line back in /etc/fstab and I can long in normally.

Also, I have attached a gparted screen shot of the system current state if that helps.................

Your /home partition is mounted. Now you need to mount the other one.Edit yout fstab and add this line:
> /dev/sda4 **/media/data** ext3 defaults 0 2Change the /media/data to the directory where you want to mount the partition.

Create the directory:
```
sudo mkdir /media/data
```Mount the partition:
```
sudo mount -a
```To get write permission on the partition you need to change the owner:
```
sudo chown -R $USERNAME\: /media/data
```

---


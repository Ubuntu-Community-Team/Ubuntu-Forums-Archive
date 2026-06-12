---
title: "[SOLVED] gconf error after update or hard drive full?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by waydownsouth on 2008-08-03
Ok,
So I ran update manager, it installed 33 updates, all went well until I got this:
```
Setting up ufw (0.16.2.3) ...
/usr/bin/ucf: line 181: cannot create temp file for here document: No space left on device
dpkg: error processing ufw (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ufw
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now when i try to run synaptic I get this:
```
therapy@BOB:~$ gksudo synaptic
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory)

(gksudo:6802): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory 2: IOR file '/tmp/gconfd-therapy/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Error copying '/home/therapy/.Xauthority' to '/tmp/libgksu-40sv1n': No space lef
```


My hard disk reports that it has no free space,
I have two partitions:
20Gb   /
300Gb /home

Whether or not my 20Gb is actually full or whether its a prob with gconf, I have no idea and am unsure of where to begin...

So heres hoping someone can help?

---

### Post by bpowell2005 on 2008-08-04
Open up a terminal window and post the output of:

df -h

(disk file usage...I always think of it as "disk free") the -h switch just makes the output easier for humans to understand.

---

### Post by waydownsouth on 2008-08-04
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G   18G     0 100% /
varrun                378M  252K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   40K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
lrm                   378M   39M  339M  11% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb3             278G  111G  154G  42% /home
overflow              1.0M  1.0M     0 100% /tmp

```

Right, so that's pretty straightforward... full disk

---

### Post by bpowell2005 on 2008-08-04
> **waydownsouth said:**
> ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              18G   18G     0 100% /
varrun                378M  252K  378M   1% /var/run
varlock               378M     0  378M   0% /var/lock
udev                  378M   40K  378M   1% /dev
devshm                378M     0  378M   0% /dev/shm
lrm                   378M   39M  339M  11% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb3             278G  111G  154G  42% /home
overflow              1.0M  1.0M     0 100% /tmp

```

Right, so that's pretty straightforward... full disk


Yup, that's a full root partition! I've done this before, so you're not alone. The good news is it's easy to fix! You will just need to burn yourself a "Gparted" CD, boot into that, and add some space do your /dev/sdb1 partition by taking space from your /dev/sdb3 (home) partition...looks like you have 154 Gig to spare there, so add another 20 Gig to your root and you should be in great shape.

---

### Post by bpowell2005 on 2008-08-04
Waydownsouth,

Also, you may want to look into what's consuming all the space on your root partition...I've been running Ubuntu Hardy for a while now with all the upgrades, and adding software like crazy, and haven't hit 18 gig...so I have a feeling you have some music or videos or something big getting stored on your root rather than your /home partition.

Try this: go to your root directory (cd /) then type: du -h --max-depth=1

This command is: Disk Usage; the -h provides a "human" output (like df) and the max-depth=1 just tells the program to give us the 30,000 foot view of your file system...which directory from root is eating the most space? You can then cd into that directory, and run the same command, and see what sub-directory is eating space...etc. etc.

---

### Post by waydownsouth on 2008-08-04
:oops:

I found my problem, I use an external drive for backup, and at one point last week I took the drive away to copy some files from a friends machine.

When I replugged the drive it can't have mounted properly and instead of sbackup saving to /media/my_external_drive it did a full backup to /media which is where I found a 12Gb tar of backed up files...

My bad

Thanks for steering me in the right direction. 

root is at a much better size now: 3Gb

---

### Post by bpowell2005 on 2008-08-04
No worries man! Hit me up with a "Thanks" if you don't mind...and don't forget to change this thread to "Solved".

---

### Post by n3rxs on 2008-11-02
ok I have the same error and no full disks I even get the error when trying to do any gediting.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              33G  3.3G   28G  11% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  108K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1005M   1% /dev
tmpfs                1008M   48K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             117G   47G   71G  40% /media/Temp
/dev/sdb2             117G  265M  117G   1% /media/Projects
/dev/sdd1             150G   16G  134G  11% /media/Storage
/dev/sdc1              75G   13G   63G  17% /media/Data

---

### Post by n3rxs on 2008-11-02
I get the error when say using gedit /etc/fstab as root but if I use gedit as my regular user, no error. This error is after going to clean install og Ubuntu 8.10 from the final version cd

---

### Post by OVERK|LL on 2008-11-22
> **n3rxs said:**
> I get the error when say using gedit /etc/fstab as root but if I use gedit as my regular user, no error. This error is after going to clean install og Ubuntu 8.10 from the final version cd

Same issue on my Gentoo box. Though it doesn't seem to affect functionality.....

---


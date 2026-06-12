---
title: "[SOLVED] Where Is /home"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by mapes12 on 2008-06-04
> mark@laptop-ubuntu:~$ sudo sfdisk -l
[sudo] password for mark:

Disk /dev/sda: 2432 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    636     637-   5116671   83  Linux
/dev/sda2       2325    2431     107     859477+   5  Extended
/dev/sda3        637    2324    1688   13558860   83  Linux
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       2325+   2431     107-    859446   82  Linux swap / Solaris
mark@laptop-ubuntu:~$ 

I had to reinstall Ubuntu 7.10. The previous configuration is for /home to be located on sda3. During the fresh installation i preserved sda3 thinking that /home would be mounted there. But following the install I find that /home appears to be on sda1 with a duplicate on sda3. When I boot sda3 is mounted by default but if I umount it then my /home files still apppear on my desktop? 

1. How has this happened?
2. What can I do to correct it please?  :confused:

---

### Post by sisco311 on 2008-06-04
post the output from:
```
mount
```
and
```
cat /etc/fstab
```

---

### Post by hyper_ch on 2008-06-04
To see what is currently mounted where run:

```

df -l

```

---

### Post by indytim on 2008-06-04
> 
I had to reinstall Ubuntu 7.10. The previous configuration is for /home to be located on sda3. During the fresh installation i preserved sda3 thinking that /home would be mounted there. But following the install I find that /home appears to be on sda1 with a duplicate on sda3. When I boot sda3 is mounted by default but if I umount it then my /home files still apppear on my desktop?

1. How has this happened?
2. What can I do to correct it please? 


To answer your questions directly.

1.  When you re-installed your ops, at the "Manual Partition" section, you did not specify /sda3 as the location of your /home.  So, having no other directives, the installation installed /home on the same partition as "/" (sda1).  As part of the installation process, all ext3 partitions are mounted.  That explains why you are able to see the old /home and your current /home.  Your active /home is in sda1.

2.  You will need to edit your fstab file and point the /home to sda3 rather than sda1.  Re-boot and all should be happy.

IndyTim

---

### Post by hyper_ch on 2008-06-04
reboot is not necessary, everything can be remounted with
```

sudo mount -a

```

---

### Post by mapes12 on 2008-06-04
Here's the output to those commands. I can't figure out why fstab comments out sda1, 3 and5?

> mark@laptop-ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/sda3 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
mark@laptop-ubuntu:~$ 


mark@laptop-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2491dcf0-31e3-481d-86e5-ad984967254e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=e07e3890-1419-40a4-aa57-938eded8b93c /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=5e862daa-8e62-436b-8791-0bf4a72f20c6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
mark@laptop-ubuntu:~$ 


mark@laptop-ubuntu:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              5036284   3350280   1430172  71% /
varrun                  517528        92    517436   1% /var/run
varlock                 517528         0    517528   0% /var/lock
udev                    517528        60    517468   1% /dev
devshm                  517528         0    517528   0% /dev/shm
lrm                     517528     34696    482832   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3             13345372    203836  12599184   2% /media/sda3
mark@laptop-ubuntu:~$ 


---

### Post by soxs on 2008-06-04
sda1 and other stuff are not required, as it uses uuids to allocated the right partition, the sdax stuff is only for a better reading/understanding experience.

If sda3 was your old home partition you need to alter that line:

```
# /dev/sda3
UUID=e07e3890-1419-40a4-aa57-938eded8b93c /media/sda3     ext3    defaults        0       2

```to
```

# /dev/sda3
UUID=e07e3890-1419-40a4-aa57-938eded8b93c /home     ext3    defaults        0       2
```but to be able to mount sda3 successfully to /home you need to make sure that your /home directory is empty (log in as root (make this possible goto System -> System.. -> login -> allow local root login) an remove anything within &home via ```
sudo rm -Rvf /home/*
``` NOTE:You will loose all your done settings/data and get instead your ones from your old home partition)
EDIT:
[COLOR=DarkRed]NOTE: pruging home dir is not a required step, but I suggest it anyone, as any data you have in /home will be unreadable while you home partition is mounted to /home dir.[/COLOR]

---

### Post by mapes12 on 2008-06-04
Thank you! :)

It worked.

The commands Soxs provided solved the problem. Gold stars clicked for all that posted to help me out.

Thanks again.

:lolflag:

---

### Post by hyper_ch on 2008-06-04
a directory does not need to be empty in order to mount anything in it... at least that's what I think.

---

### Post by soxs on 2008-06-04
You're right, but he won't be able to access his old data anyways, so it saves him some MiBs.

---


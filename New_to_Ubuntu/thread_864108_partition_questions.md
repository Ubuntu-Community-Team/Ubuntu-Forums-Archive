---
title: "partition questions"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by pgte3 on 2008-07-19
I believe this is a complete list of all partitions on my hard drive:

pgte3@pgte3-laptop:~$ sudo fdisk -l
[sudo] password for pgte3: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed8eed8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       11316    89358398+   7  HPFS/NTFS
/dev/sda3           11317       19457    65392582+   5  Extended
/dev/sda5           14047       19229    41632416   83  Linux
/dev/sda6           19230       19457     1831378+  82  Linux swap / Solaris
/dev/sda7           11317       13927    20972794+  83  Linux
/dev/sda8           13928       14046      955836   82  Linux swap / Solaris

Partition table entries are not in disk order

I thinks this is what is currently mounted and in use:

pgte3@pgte3-laptop:~$ df -a -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda7     ext3    20807152   2635660  17122856  14% /
proc          proc           0         0         0   -  /proc
/sys         sysfs           0         0         0   -  /sys
varrun       tmpfs      972052       104    971948   1% /var/run
varlock      tmpfs      972052         0    972052   0% /var/lock
udev         tmpfs      972052        60    971992   1% /dev
devshm       tmpfs      972052        12    972040   1% /dev/shm
devpts      devpts           0         0         0   -  /dev/pts
lrm          tmpfs      972052     39760    932292   5% /lib/modules/2.6.24-19-generic/volatile
securityfs
        securityfs           0         0         0   -  /sys/kernel/security
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon    20807152   2635660  17122856  14% /home/pgte3/.gvfs


Questions:

How do I determine what swap file is in use?

What is /dev/sda1 and /dev/sda3?

---

### Post by spiderbatdad on 2008-07-19
sda3 is an extended partition. Extended partitions were created as a means of subdividing the primary partition, to allow you to have a greater number of partitions. Before the creation of extended partitions, a disk could only be divided into 4 partitions.

sda1: I have no idea what you have there.

---

### Post by Vivaldi Gloria on 2008-07-19
> **pgte3 said:**
> How do I determine what swap file is in use?

Try

```
cat /proc/swaps
```

---

### Post by logos34 on 2008-07-19
> **pgte3 said:**
> How do I determine what swap file is in use?

What is /dev/sda1 and /dev/sda3?

cat /proc/swaps [Edit: looks like vivaldi beat me to that one]
swapon -s

cat /etc/fstab (one of the two will be listed)

sda1 is probably a manufacturer recovery partition (~1.8 GB)


Have a nice day.

---

### Post by pgte3 on 2008-07-19
Thanks for the post. So /dev/sda3 does not contain data, but is needed for partition 5 - 8. Maybe /dev/sda1 is used by Vista which came shipped with my machine.

---

### Post by logos34 on 2008-07-19
> **pgte3 said:**
> Thanks for the post. So /dev/sda3 does not contain data, but is needed for partition 5 - 8. Maybe /dev/sda1 is used by Vista which came shipped with my machine.

exactly.  An extended partition is just a container or shell for logical partitions--by itself it doesn't take up any disk space.

---


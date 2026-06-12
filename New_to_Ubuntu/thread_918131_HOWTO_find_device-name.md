---
title: "HOWTO find device-name"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-12
Hellow,

how can I find the real name of my external hard disk
i need it because my ubuntu doesn't reconice it (mounting problem)
so i thought of using 'nfts-3g -o force /dev/device_name /mnt/ntfs'

mvg,
Dadsgé

---

### Post by bobnutfield on 2008-09-12
With the drive plugged in:

> sudo fdisk -l

---

### Post by Dadsgé on 2008-09-12
tried it, but
'command not found...'

---

### Post by bobnutfield on 2008-09-12
> **Dadsgé said:**
> tried it, but
'command not found...'

Quite unusual.  fdisk is a legitimate app and the -l lists all disk devices.

The swith is a small "L" (-l)

---

### Post by Dadsgé on 2008-09-12
well that's what I tried, but it's still givin' me no names...

---

### Post by bobnutfield on 2008-09-12
You are getting no output, other than "command not found"?  You should have gotten something like this:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003415c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+  83  Linux
/dev/sda2            3825        6374    20482875   83  Linux
/dev/sda3            6375        6629     2048287+  82  Linux swap / Solaris
/dev/sda4            6630       19457   103040910    5  Extended
/dev/sda5            6630       13156    52428096   83  Linux
/dev/sda6           13157       15068    15358108+  83  Linux
/dev/sda7           15069       19457    35254611   83  Linux


---

### Post by WRDN on 2008-09-12
If "fdisk" doesn't work, try:

```
sudo blkid
```

---

### Post by Dadsgé on 2008-09-12
now it's working
still dont quiet now what i was doing wrong, but it's okey now :)

thanx ;)

---

### Post by Dadsgé on 2008-09-12
hmm
ntfs not working...
> hannes@hannes-laptop:~$ ntfs-3g /dev/sdb /mnt/ntfs
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

what should I do now?

---

### Post by bobnutfield on 2008-09-12
If you are trying to mount your Windows partition, and it is located on /dev/sdb1, try this:

> sudo mount -t ntfs /dev/sdb1 /mnt/ntfs

assuming the mount point exists, i.e. the directory /mnt/ntfs exists. Or, use "sudo" in front of your command.

---

### Post by Dadsgé on 2008-09-12
now it is giving me this:
> hannes@hannes-laptop:~$ sudo mount /dev/sdb1 ntfs /mnt/ntfs
[sudo] password for hannes: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

i dont think this solved my problem did it?

---

### Post by bobnutfield on 2008-09-12
Sorry, I edited after I noticed neglected to include the -t switch:

> sudo mount -t ntfs /dev/sdb1 /mnt/ntfs

---

### Post by Dadsgé on 2008-09-12
yes, it worked

thanx bobnutfield

---


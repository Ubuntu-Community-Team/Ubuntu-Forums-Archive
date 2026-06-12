---
title: "Mounting harddrives, letter changes"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by datatek on 2008-11-26
Hello,

as part of a backup system, I use 2 very simple scripts to mount and unmount a harddrive;


To mount;
#!/bin/sh
#/sbin/backup-mount
echo " /dev/sda5 mounted at /mnt/backup" >>/var/log/messages
mount /dev/sda5 /mnt/backup >>/var/log/messages
echo " /dev/sda5 mounted at /mnt/backup"

To unmount;

#!/bin/sh
#/sbin/backup-unmount
sync
echo "/mnt/backup now offline" >>/var/log/messages
umount /dev/sda5 >>/var/log/messages
echo "/mnt/backup now offline"


The problem is that when devices get (often) inserted in a haphazard manner, the drive isn't sda5 anymore, but sometimes sdb5, sdc5, sdd5 etc, and then the script doesn't work anymore.

How can I alter the script so that it picks up sd*5?

---

### Post by Titan8990 on 2008-11-26
Best way to go about this is to use the UUID of the drive in /etc/fstab so that it will automount.


Other than that you would have to set up udev rules to ensure that your drive gets assigned the same logical name every time.

---

### Post by bodhi.zazen on 2008-11-26
You can list your partitions by UUID with ```
sudo blkid
```

See [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by datatek on 2008-12-06
The problem has expanded: several different harddrives (with differing UUIDS etc, of course) will be used, and each of these needs to be mounted to /dev/sda5 when it's connected. How can this be done?

---

### Post by bodhi.zazen on 2008-12-06
Not a problem.

You can mount two file systems to the same mount point at the same time (not that I would advise it), but you can only access one at a time. You will have access to the last one mounted.

For example

mount /dev/sda1 to /mnt

ls /mnt => see content of sda1

mount /dev/sda2 /mnt

ls /mnt => see content of sda2

umount /dev/sda2

ls /mnt => see content of sda1 again.

===========

At any rate, you can mount by UUID or by label, or any way you wish., You can recycle the same mount point if you wish, you may wish to write a wrapper script to see if any partition is mounted at the mount point before you mount a second partition to the same place.

Is there some reason you are making this more complicated then 1 mount point per partition ?

---

### Post by datatek on 2008-12-11
> **bodhi.zazen said:**
> 

Is there some reason you are making this more complicated then 1 mount point per partition ?

The backups are created from one specific location.

---


---
title: "Second HDD"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by CorneliusSneed on 2014-04-28
Ubuntu 12.04LTS.  Two HDD installed in machine, one with OS, second for storage. When I try to move files to the second one, I get the error "The folder "My Folder" cannot be copied because you do not have permissions to create it in the destination."

A check of the perms on the drive says owner and group are root, and I am not the owner so I can't change permissions.

What is the best way to fix this?

---

### Post by 3rdalbum on 2014-04-28
Whatever the mount point is of this drive, you need to change its ownership to your user account.

For instance, if the drive is mounted at /media/christopher/mydisk:

```
sudo chown christopher /media/christopher/mydisk
```

---

### Post by CorneliusSneed on 2014-04-28
Thanks, 3rdalbum. When I right click and check properties, it says this:  "Location:   /media"  and "Volume: 196 GB Filesystem"
So I tried "sudo chown kelly /media / 196 GB Filesystem" and got this: 

chown: cannot access `196': No such file or directory
chown: cannot access `GB': No such file or directory
chown: cannot access `Filesystem': No such file or directory
kelly@kelly-desktop:/media$ 

It seems there must be something simple I am missing, like what the HDD is actually called by the OS? I also tried the UUID, with the same result.

---

### Post by oldfred on 2014-04-28
Spaces create issues with Linux. 
I try to avoid spaces by using CamelCase, under_score, or justalabel for mount points or labels.
If you label partitions then a default mount using Nautilus will use the label.
I try to remember to add labels when I create partitions with gparted, but if I forget I often use Disks or Disk Utility just to add labels.

If you change to use labels, you can use that mount point. 
Or unmount with Nautilus and manually mount with a simple mount. Cannot have same partition mounted twice.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data


But if you have a permanent second drive you may want to have it mount on reboot. Then you need to add it to fstab. Again do not use a mount with spaces to make it easier, but you can use any name/label/mount you like. And it does not have to be the same as the label. I have labelled a partition data and mounted it Data and gotten confused on which it is as Linux case sensitive.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by CorneliusSneed on 2014-04-28
The command that worked was "sudo chown kelly /media/88951161-91e7-4795-87be-c53dc14dc6e2"

---


---
title: "Mounting multiple drives command line"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-05-29
cant seem to mount more than one usb hard drive with command line, I've been mounting one using this command:

mount -t ntfs-3g /dev/sdb1 /mounting/path

do i need to change sdb1 to sdb2 or look in the dev directory to see what the other hd's partition id's are? or how is it done? been goin round in circles on this one....

would:
mount /dev/sdb1 /mounting/path

be enough rather than the -t ntfs-3g?

---

### Post by strask on 2012-05-29
The 1 at the end of /dev/sdb1 is the partition identifier, it points to a particular partition on the /dev/sdb disk drive. If you have an entirely separate disk drive to mount, it is likely something like /dev/sdc or /dev/sdd or whatever. Once you figure out the right letter, you need to add the correct partition number to the end of the disk identifier so something like /dev/sdc1 might be right.

You can get a clue about what drive devices to check by typing ```
cat /proc/partitions
```
There will be entries in that list that you should ignore, but pay attention to the ones that start with sd.

Then when you think you have the right disk, you can check the partition table with ```
sudo fdisk -l /dev/sdx
```
This will help you choose the correct partition to mount.

---

### Post by dniMretsaM on 2012-05-29
> **bikefreakvinnie said:**
> cant seem to mount more than one usb hard drive with command line, I've been mounting one using this command:

mount -t ntfs-3g /dev/sdb1 /mounting/path

do i need to change sdb1 to sdb2 or look in the dev directory to see what the other hd's partition id's are? or how is it done? been goin round in circles on this one....

Use this command to find the device names for various drives:
```
sudo fdisk -l
```
Then run:
```
sudo mount /dev/<xxx#> <path to mount device to>
```

> **bikefreakvinnie said:**
> would:
mount /dev/sdb1 /mounting/path

be enough rather than the -t ntfs-3g?

I believe so, yes.

---

### Post by bikefreakvinnie on 2012-05-29
thanks for that!

---


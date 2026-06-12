---
title: "filesystem is NOT clean"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by BetterSense on 2008-04-30
I have an ext3 / and a reiserFS /home, iirc. I suffered a power failure; now when I boot it seems to be checking the rieserFS, and the boot screen tells me 'the filesystem is NOT clean'.

I tried to run fsck, but it said running it on a  mounted filesystem would cause severe filesystem damage. I tried using grub to log into a recovery shell as root and run fsck, but it said the same thing.

Everything seems to work, but I don't like how it tells me I'm unclean.

---

### Post by TeoBigusGeekus on 2008-04-30
Boot up with the live cd and run fsck.

---

### Post by otrojake on 2008-04-30
Once you got to the recovery shell, did you unmount your home drive?

---

### Post by BetterSense on 2008-04-30
should I just run unmount /home, or do I have to find the official name for my home filesystem?

---

### Post by otrojake on 2008-05-01
I'd run 
```
sudo fdisk -l
``` at the recovery shell to figure out what the device name is (/dev/?).  The size in blocks should give you a hint as to what drive is which, taking for granted the partitions are different sizes.  Or you could also check out the fstab with ```
sudo vim /etc/fstab
``` and see which device name is mounted for home.  After you've figured out what the device name is for your /home partition.  Run this code ```
sudo umount /dev/?
``` replacing the question mark with whatever the partition's name is (hda2, or sda3, for example).  Then you should be able fsck it.

---


---
title: "Restored partitions not working"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by t-molli on 2008-05-05
hola,

I made a copy of my partitions using partition image (partimage), but have not had any success with restore.

I've restored my hda1 partition to hda1 and the hda2 partition to hda2. I even restored the master boot record (mbr), but when I reboot the computer - it pops up Grub at the top and then stops booting.

I made the original images while in the Live CD. After restoring the partitions (I formatted the two partitions) I checked the HD's and saw all the typical files/folders present.

I've checked the drives and hda1 does show the boot flag, so it's right - but there seems to be some hang-up with the Grub I think (see above).

Have I forgotten something to make this work? The back-up and restore actually look very good while in progress and appear to work perfectly. However, we know that's not the case or I wouldn't be posting. :)

Any ideas of what I may have overlooked?



Commands used:

Create:

sudo partimage -z1 -d -f3 -b save hda1 /home/tom/Desktop/partition_image_hda1.gz

sudo partimage -z1 -d -f3 -b save hda1 /home/tom/Desktop/partition_image_hda2.gz

Restore:

sudo partimage restore -f3 -b hda1 partition_image_hda1.gz

sudo partimage restore -f3 -b hda2 partition_image_hda2.gz


Thanks in advance...

---

### Post by Oldsoldier2003 on 2008-05-05
> **t-molli said:**
> hola,

I made a copy of my partitions using partition image (partimage), but have not had any success with restore.

I've restored my hda1 partition to hda1 and the hda2 partition to hda2. I even restored the master boot record (mbr), but when I reboot the computer - it pops up Grub at the top and then stops booting.

I made the original images while in the Live CD. After restoring the partitions (I formatted the two partitions) I checked the HD's and saw all the typical files/folders present.

I've checked the drives and hda1 does show the boot flag, so it's right - but there seems to be some hang-up with the Grub I think (see above).

Have I forgotten something to make this work? The back-up and restore actually look very good while in progress and appear to work perfectly. However, we know that's not the case or I wouldn't be posting. :)

Any ideas of what I may have overlooked?



Commands used:

Create:

sudo partimage -z1 -d -f3 -b save hda1 /home/tom/Desktop/partition_image_hda1.gz

sudo partimage -z1 -d -f3 -b save hda1 /home/tom/Desktop/partition_image_hda2.gz

Restore:

sudo partimage restore -f3 -b hda1 partition_image_hda1.gz

sudo partimage restore -f3 -b hda2 partition_image_hda2.gz


Thanks in advance...

can you post a copy of /boot/grub/menu.lst and the return from:
```
ls /dev/disk/by-uuid -alh
```

---

### Post by t-molli on 2008-05-05
Thanks for your help. I'm thinking there's got to be something with the "hd0,0" My OS is on hda1 and hda2, but I can't remember how the hd0,0 works again. Isn't it 0 for the first hard drive and second 0 is partition, but seems like it should be hd1,1?? Don't know without testing, but will wait to hear from you or someone else. Thanks again...

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c72259d1-cc3e-490c-a614-a11852040b46 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c72259d1-cc3e-490c-a614-a11852040b46 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


ls command follows:

lrwxrwxrwx 1 root root  10 2008-05-06 00:38 4accf0ed-e342-4115-a8b4-1f5652449a0c -> ../../hda3

lrwxrwxrwx 1 root root  10 2008-05-06 00:38 6745ed60-597e-43f0-a4fa-090c9ca57b53 -> ../../hda2

lrwxrwxrwx 1 root root  10 2008-05-06 00:41 c72259d1-cc3e-490c-a614-a11852040b46 -> ../../hda1

---

### Post by t-molli on 2008-05-06
bump

---


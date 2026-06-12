---
title: "Attempting to access data folder from a failed Seagate Central drive"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by tony58 on 2014-08-12
Hey Folks,

I received persmission from Seagate to remove the 4TB hard drive from the external Seagate Central unit. One of the Seagate techs suggested I try Linux to recover the the data from the hard drive. When I try to access the data volume I get the following message:

Unable to access “Data”

Error mounting /dev/dm-0 at /media/ubuntu/Data: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/ubuntu/Data"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



Any ideas or suggestions?

Thanks

---

### Post by Jonathan Precise on 2014-08-12
Looks like you will need to run fsck:

```
fsck /dev/dm-0
```

---

### Post by SeijiSensei on 2014-08-12
Is the drive really formatted with ext4?  You would have had to do that yourself, since the factory default is usually FAT32 or NTFS.

---

### Post by tony58 on 2014-08-13
I do not recall formating the drive to use ext4. It was used in a Win 8.1 so it was one those default formats FAT32 or NTFS.
I will try the fsck /dev/dm-0  command. 

Thanks so much.

---


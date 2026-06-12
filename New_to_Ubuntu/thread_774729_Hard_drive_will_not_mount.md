---
title: "Hard drive will not mount"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Benbow on 2008-04-29
I have a separate HD in a case which I use frequently.I think that I may have turned off Ubuntu without unmounting it and it will not now mount. Is there any way I can overcome this problem, I use the drive very often.

---

### Post by quirks on 2008-04-29
Check the filesystem on the hard disk for inconsistencies:
```
sudo fsck -f /dev/*xxxx*
```
where *xxxx *is the device file of the filesystem that won't mount (e.g., *sdb1*).

You can find out what the device is with this command:
```
sudo fdisk -l
```
The command lists all partitions on your local hard disks. Probably, you can infer the proper device file from the sizes of the partitions.

If you have trouble with this, just ask.

If the filesystem is NTFS, you should not use fsck. Better check it in Windows.

---


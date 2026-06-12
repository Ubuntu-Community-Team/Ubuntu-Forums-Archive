---
title: "Help! No boot"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by stubblepoo on 2008-08-25
well now i have your attention.
i managed to fill my xp partition with such crap/virus's that i decided it was time fro a clean install, thats all went fine except that i doont have my wireless card driver so that didnt work, but no worries i thought i'll just use ubuntu for online stuff but since my reinstallation of windows my ubuntu grub menu doesnt show at bootup. in oreder to get around this i installed GAG bootloader. but this see's my ubuntu partition, reconises that it is an ntfs formated drive and all but when it is selected says: sector boot not found or 'invalid'
dunno what to do next, sort of have to get everything working before uni in a couple of weeks!

---

### Post by OffAxis on 2008-08-25
I've never used that bootloader, but what about super grub disk?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Otherwise, you could boot off a live cd and reinstall grub.

---

### Post by stubblepoo on 2008-08-25
how from the live cd would i reinstall grub?
edit: worked out how, how do i find out which hd#,# to input?

---

### Post by WRDN on 2008-08-25
> **stubblepoo said:**
> how from the live cd would i reinstall grub?
edit: worked out how, how do i find out which hd#,# to input?

There is a guide [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for reinstalling GRUB from the LiveCD.

To find out the drive and partition (the first and second number in (hd0,0) respectively), boot Ubuntu and in the Terminal, type:

```
sudo fdisk -l
```

The output format will look like this:

> Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93109310

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13212   106125358+   7  HPFS/NTFS
/dev/sda3           13213       14946    13928355    5  Extended
/dev/sda5           13213       14791    12683254+  83  Linux
/dev/sda6           14792       14855      514048+  82  Linux swap / Solaris
/dev/sda7           14856       14946      730926   83  Linux


Now, find the root partition (in this case, it is /dev/sda5). Your output will either show "sdaN" or "hdaN" under the Device column, where N represents the number. The 3rd letter tells you the HDD you will boot from (the a in sda tells you its the first HDD, while a b would refer to a second drive etc) and the number is the partition. If you only have 1 HDD, it will be "(hd0,N)", where N refers to the partition number.

---


---
title: "automounting usb hard drive"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by theRightNee on 2008-05-21
hey all,
i know this topic comes up a lot, but after trying every method that has worked for me before i cannot successfully automount

this is my /etc/fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=65a40680-e4d5-427a-ac53-1d7f504bcfed /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=776bac0f-5715-4311-b249-a0afe75abf43 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


#Added by diskmounter utility
/dev/sdb1 /media/sdb1 ntfs user,fmask=0111,dmask=0000 0 0

```

---

### Post by EXCiD3 on 2008-05-22
do you get any errors when you try to mount it? Sometimes ntfs cant be mounted if it wasnt safely removed last time you used it in windows. this happens to mine alot.

you can also try doing a "sudo mount -t ntfs-3g /media/sdb1" and seeing what errors you get from that.

---

### Post by vanadium on 2008-05-22
A removable USB drive indeed should not be mounted using /etc/fstab. If the volume is OK, the drive will mount automatically. As EXCiD3 already mentionned, an USB drive must be properly disconnected from windows. In practice this means that when using Windows, either

* you completely shut down Windows (no hibernation!)
or
* you use the tray icon to safely disconnect the drive

(same goes for Ubuntu!)

---

### Post by theRightNee on 2008-05-22
ah...thank you! i have never used this hard drive with windows, but perhaps it was because i did not safely disconnect. i'll remeove the /etc/fstab entry =]

---


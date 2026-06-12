---
title: "Change install location (ie, to flash drive?)"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by sjandrew on 2012-12-28
Hello,

Say I want to install some software (maybe VirtualBox), but I don't have enough disk space (because I do not, in fact, have a hard disk) and want to install this software to a peripheral device (such as a hard drive connected via USB). How do I do that? I'm a former Windows user, and accustomed to being able to tell the system, during the install process, where to install a given piece of software. 

Thanks much

---

### Post by BBQdave on 2012-12-28
> **sjandrew said:**
> Say I want to install some software (maybe VirtualBox), but I don't have enough disk space (because I do not, in fact, have a hard disk)...

If you are running an Ubuntu Live CD session, then you would need a disk to save your work on. If you wish to install applications beyond the Live CD session, the most straight forward method would be to install Ubuntu. A full Ubuntu install with added applications - you will need at least 10GB of disk.

You could install Ubuntu to an USB stick and then select USB boot up on your hardware's bios. If you are looking for something leaner than Ubuntu, and want Linux computing on a stick, check out [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm") :)

---

### Post by C.S.Cameron on 2012-12-28
If using a Live CD or Live USB, you should be able to make a ext2 partition on the USB hard drive and label it casper-rw.

If booting from Live CD press F6 and type <space>persistent.

```
 persistent
```

If booting from Live USB, (made using Startup Disk Creator), you can edit the text.cfg, (or txt.cfg depending on Ubuntu version), thus:
```

append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
```

If the Live USB was made using UNetbootin, the file to edit is syslinux.cfg.

Things change from version to version so please let me know if this does not work for you.

---


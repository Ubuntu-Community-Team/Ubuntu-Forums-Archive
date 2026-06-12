---
title: "How to differentiate between USB and non-USB mounts"
date: 2008-07-21
forum: Programming Talk
---

### Post by pcman312 on 2008-07-21
I'm gathering system information, part of if being information regarding the file system. Is there a way of determining what mount points are disks and what ones are not disks (namely USB)?  I can gather the information I need from *df* however I cannot tell what is USB and what isn't.

---

### Post by kidders on 2008-07-22
Hi there,

Your post is a little confusing, because there's nothing stopping something being a disk *and* a USB device. One way of finding out whether something is a USB device is to look in /sys. For the sake of example ...```
#!/bin/sh

for DEVICE in /dev/[hs][rd]?; do
        for INFO in `udevinfo --query=env --name=$DEVICE`; do eval $INFO; done
        echo $DEVICE is a $ID_BUS $ID_TYPE
done
```Executing that should give you something like ...```
/dev/sda is a scsi disk
/dev/sdb is a scsi disk
/dev/sdc is a scsi disk
/dev/sdd is a usb disk
/dev/sr0 is a scsi cd
```

As far as determining whether something is a disk or not is concerned, where would you like to draw the distinction? For instance, is an optical drive or a ramdisk a "disk"? Depending on your point of view, one way of creating at least a partial list of mounts that aren't disks would be ...```
mount | grep -v "^/dev"
```That would show up files (eg disk images), virtual filesystems (eg sysfs), NFS shares, and so on.

Being able to pick these out is important, I suppose, because running **df** on things like /proc or a remote filesystem can have unpleasant side-effects.

I hope that helps.

---

### Post by Can+~ on 2008-07-22
How about [FONT="Courier New"]lsusb[/FONT]?

---

### Post by pcman312 on 2008-07-28
Actually, udevinfo works perfectly for what I need. Thanks.

The idea is to detect what USB devices are connected vs non-usb and then act accordingly.

---


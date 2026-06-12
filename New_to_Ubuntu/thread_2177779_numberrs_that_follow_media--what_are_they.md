---
title: "numberrs that follow /media--what are they?"
date: 2013-09-30
forum: New to Ubuntu
---

### Post by mark allyn on 2013-09-30
Hello everyone,

I know this is a silly question.  I know many of you will consider it even frivolous.  Yet, I can't help myself (as an aviid Ubuntuer):

When I insert a flash drive in my 12.04 system, it automounts to /mediia/xxxx-xxxx.  What the heck is xxxx-xxxx?  Does it bear any particular relationship to the UUID, or some other physical characteristic of the drive, or the filesystem, or the pci?

Thanks for your patience.

Mark Allyn

---

### Post by deadflowr on 2013-09-30
If a device or partition mounted doesn't have a label, then yes it'll show the UUID.
Which is what that is.

---

### Post by mark allyn on 2013-09-30
Deadflowr-

Thanks for your very quick response.  Let me make sure I understand what you're saying.  If I label /dev/sdc1 as "jack" then when I automount to /media/jack.  If I do not assign a label, then it mounts to /media/uuid?

I have one more question (at least), but first I have to do some research so I don't waste your time -- or anyone else's.

Cheers,
Mark

---

### Post by deadflowr on 2013-09-30
> **mark allyn said:**
> Deadflowr-

Thanks for your very quick response.  Let me make sure I understand what you're saying.  If I label /dev/sdc1 as "jack" then when I automount to /media/jack.  If I do not assign a label, then it mounts to /media/uuid?

I have one more question (at least), but first I have to do some research so I don't waste your time -- or anyone else's.

Cheers,
Mark

Pretty much so.
Except you won't automount the device to /media/jack, the device will be automounted as /media/jack.
If no label is found then it'll fallback to the UUID.
Of course if you manually mount it, using mount command in terminal, it'll be mounted as whatever directory name you mount it in.
Example
```
mount /dev/sda1 /mnt/googlyeyes.
```
The device will show up in /mnt/googlyeyes.
More, maybe
[https://help.ubuntu.com/community/MountDevicesTroubleshooting](https://help.ubuntu.com/community/MountDevicesTroubleshooting)
other more, maybe
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by mark allyn on 2013-09-30
Hi Deadflowr-

I think I "get" your distinction between "to" and "as"....perhaps not.  Anyway, 

In the present instance, the flash has a vfat32 partition.  The device is mounting as /media/80C2-1B31 and this is in fact the UUID as discovered by ls -l /dev/disk/by-uuid.  So that takes care of that.  Moreover, gparted shows that the partition is not labeled.

My remaining question is this: BLKID command does not show the flash drive (when it is mounted), but LSBLK command does.  Can you explain why the two commands do not produce equivalent results?

Thanks,
Mark 

Actually, there might be one remaining question...

---

### Post by deadflowr on 2013-09-30
No clue on either blkid or lsblk differences.
However, you can look at the man for both.
man blkid
man lsblk

Maybe you can find the reason they each post results differently.

---

### Post by mark allyn on 2013-09-30
Hi Deadflowr,

Consulting man pages for lsblk and blkid reveals not a whole lot.  blkid reads from the libblkid library and lsblk reads from sysfs.  The remainder of the man pages don't show any other obvious differences, at least to my untutored eye.

You're more than welcome to reply, but I think I will mark this thread SOLVED.

Cheers,
Mark

---


---
title: "fstab for removable device"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by victorbrca on 2008-08-14
Hi all,

I've just set two removable devices (actually 1x with 2x partitions) on my fstab, and I was wondering if I did it correct.

This is what it looks like:

```
/dev/disk/by-label/bute    /media/bute    ext3    noauto    0    0
/dev/disk/by-label/BUTE-DOCS    /media/bute-docs    vfat    auto,exec,rw,user,sync    0    0    
```

  I want bute not to be mounted and bute-docs to be mounted automatically (just like it always does). My doubts are:

1- Do I have all the proper settings for options, dump and fsck selected? Do I need "utf8"?
2- As I want to have bute-docs to mount automatically, should I make it easy and just add bute to fstab so it does not automount.


Thanks,

Vic.

---

### Post by Lord Xeb on 2008-08-14
I know it can be done, but why do you want to do that?

---

### Post by victorbrca on 2008-08-14
> **Lord Xeb said:**
> I know it can be done, but why do you want to do that?

  That partition is of no use to me. It's the root folder for a bootable image that I have on that hard drive. The other partition however holds a lot data that I'm constantly using.

  The other reason would be because I can!!!  :lolflag:


Vic.

---


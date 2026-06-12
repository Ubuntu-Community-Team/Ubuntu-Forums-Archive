---
title: "Boot Off USB Without Initrd"
date: 2008-07-27
forum: Programming Talk
---

### Post by solarwind on 2008-07-27
Hey all, I'm sorry if I posted in the wrong section but I really couldn't find another section to post this in.

I'm just making a very simple Linux "distribution" which only boots the kernel and busybox. I have prepared a rootfs with everything and made an ext2 image to use as a "ramdisk".

Currently, booting using extlinux (syslinux for ext2/3 fs) works. I write a simple configuration file to boot my kernel bzImage using my rootfs ramdisk and it boots.

However, I have two questions:

Is it possible to ditch the ramfs completely? I do NOT want to use an initrd or any other ramfs. I want to simply copy the rootfs onto the USB stick and boot into it directly. I have compiled in support for ext2/3 directly into the kernel (no modules are used at all).

Also, can I use GRUB instead of extlinux o boot this way? If so, what root parameter would I pass in the kernel line?

For example root=/dev/something. What would "something" be? I have no idea what my device is called at boot time... And I DO NOT want to use an initrd/ramfs.

---

### Post by rjack on 2008-07-30
You can boot a USB disk with GRUB.

If you have one IDE disk only, your USB disk will likely be named hd1

So try to give this to GRUB:

```
root (hd1,$BOOT_PARTITION_NUMBER)
kernel=/boot/$KERNEL_IMAGE root=/dev/sdb$ROOT_PARTITION_NUMBER rootdelay=$SOME_SECONDS
```

The $ROOT_PARTITION_NUMBER is not the number assigned by GRUB, but the number assigned by mount.

An example from my system:
```
title Gentoo USB
root (hd1,0)
kernel /boot/safe-kernel root=/dev/sdb3 rootdelay=8
```

I have a IDE disk (hd0) so the GRUB id of the USB disk is hd1.
I have a separate boot partition on that disk (sdb1), so GRUB calls it (hd1,0).

The real root is sdb3 (sdb2 is another partition): you can give the sd**b** because the kernel probes the IDE disks before the USB ones.

rootdelay is needed because USB devices need a couple of seconds, and if the kernel tries to mount the root before the USB subsystem is ready, all you get is a panic.

---

### Post by solarwind on 2008-07-30
> **rjack said:**
> You can boot a USB disk with GRUB.

If you have one IDE disk only, your USB disk will likely be named hd1

So try to give this to GRUB:

```
root (hd1,$BOOT_PARTITION_NUMBER)
kernel=/boot/$KERNEL_IMAGE root=/dev/sdb$ROOT_PARTITION_NUMBER rootdelay=$SOME_SECONDS
```

The $ROOT_PARTITION_NUMBER is not the number assigned by GRUB, but the number assigned by mount.

An example from my system:
```
title Gentoo USB
root (hd1,0)
kernel /boot/safe-kernel root=/dev/sdb3 rootdelay=8
```

I have a IDE disk (hd0) so the GRUB id of the USB disk is hd1.
I have a separate boot partition on that disk (sdb1), so GRUB calls it (hd1,0).

The real root is sdb3 (sdb2 is another partition): you can give the sd**b** because the kernel probes the IDE disks before the USB ones.

rootdelay is needed because USB devices need a couple of seconds, and if the kernel tries to mount the root before the USB subsystem is ready, all you get is a panic.

And I wont need an initrd for this as long as I have all the fs drivers compiled into the kernel, right?

---

### Post by rjack on 2008-07-31
> **solarwind said:**
> And I wont need an initrd for this as long as I have all the fs drivers compiled into the kernel, right?

Yes, you won't need a initrd, but be sure to compile in all the needed stuff (i.e. usb, usb-storage and friends).

---

### Post by solarwind on 2008-07-31
Awesome thanks!

---


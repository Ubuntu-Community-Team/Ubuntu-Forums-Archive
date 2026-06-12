---
title: "[SOLVED] dash: Is a fs mounted?"
date: 2009-01-03
forum: Programming Talk
---

### Post by x1a4 on 2009-01-03
Hi,
What do I need to test for to find out if a filesystem is mounted or not?
I need to modify the update-initramfs script to check if /boot/ is mounted and mount it if it's not, then umount it when done.

Thank you.

---

### Post by stroyan on 2009-01-03
You can search for the mount point in /etc/mtab or /proc/mounts.

---

### Post by snova on 2009-01-03
Something like:

```

if [[ `mount | grep /boot` -eq '' ]]; then
    # Not mounted, mount it.
    mount /boot
fi

# Stuff to do

umount /boot

```

Probably not the best way to do it...

---

### Post by x1a4 on 2009-01-03
> **stroyan said:**
> You can search for the mount point in /etc/mtab or /proc/mounts.

Silly me, I totally forgot about these.  I've gone for such a very long time without any major problems I forgot about many things I've learned about Linux and *buntu.  :)

---


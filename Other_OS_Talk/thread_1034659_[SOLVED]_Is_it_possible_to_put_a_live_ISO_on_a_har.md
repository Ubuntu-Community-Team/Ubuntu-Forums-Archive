---
title: "[SOLVED] Is it possible to put a live ISO on a hard drive partition?"
date: 2009-01-08
forum: Other OS Talk
---

### Post by MaxIBoy on 2009-01-08
Basically, I want to create a SquashFS partition on my hard drive, sized at exactly 700 Mb (the size of a CD,) so I can install distros from the LiveCD image without the slowness of the optical drive. Is it possible?

---

### Post by x22 on 2009-01-09
well, let's call the new partition /dev/sdb3--whatever
let's call the unmounted CD /dev/sdc--w'r

in a root terminal (or "sudo")

"dd if=/dev/sdc of=/dev/sdb3"

---

### Post by MaxIBoy on 2009-01-09
That is easy! And I'm guessing this works just as well for disk images (so I don't have to waste the CD.) But how would I go about editing grub's menu.lst file to boot this? As in, do I have to do anything special for squashFS partitions?

---

### Post by Sorivenul on 2009-01-09
> **MaxIBoy said:**
> That is easy! And I'm guessing this works just as well for disk images (so I don't have to waste the CD.) But how would I go about editing grub's menu.lst file to boot this? As in, do I have to do anything special for squashFS partitions?

You may want to take a look at [this post]("http://ubuntuforums.org/showpost.php?p=5711022&postcount=23") by kagashe regarding LiveCDs on partitions and GRUB entries.

---

### Post by MaxIBoy on 2009-01-09
Thanks, that's exactly what I was looking for.

---


---
title: "HOW-TO: Add Windows back to Grub after fixing boot"
date: 2006-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by [S|G] on 2006-07-16
I noticed that recently people have been asking how to boot into their Windows installation after they fix their Grub boot. Although I personally didn't experience this (Grub always detected my Windows correctly) there is an easy way to fix this, which is to edit your Grub boot menu list:
```

sudo nano /boot/grub/menu.lst

```

Then add the following piece of code at the end of the file:
```

title           Microsoft Windows XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

The only thing you might need to change is where root is located. On this example, Windows was installed on /dev/hda1 - (hd0,0). Here is a quick reference table to help you determining what to place in your configuration:

--------------------------------------------------------------------------
Place                                   |  Linux Name       |  Grub Name
--------------------------------------------------------------------------
1st partition on primary master disk    |   /dev/hda1       |    (hd0,0)
2nd partition on primary master disk    |   /dev/hda2       |    (hd0,1)
--------------------------------------------------------------------------
1st partition on primary slave disk     |   /dev/hdb1       |    (hd1,0)
2nd partition on primary slave disk     |   /dev/hdb2       |    (hd1,1)
--------------------------------------------------------------------------
1st partition on secondary master disk  |   /dev/hdc1       |    (hd2,0)
2nd partition on secondary master disk  |   /dev/hdc2       |    (hd2,1)
--------------------------------------------------------------------------
1st partition on secondary slave disk   |   /dev/hdd1       |    (hd3,0)
2nd partition on secondary slave disk   |   /dev/hdd2       |    (hd3,1)
--------------------------------------------------------------------------

---


---
title: "Error 13 when booting to XP"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by TideMan on 2008-10-17
I've installed Ubuntu 7.10 on an old machine.  It's for me to explore and learn Linux.  I don't really want XP, but I tried following the instructions in another post to get a dual boot.

fdisk -l gives this:
```
Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x943a943a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4866     1646662+   5  Extended
/dev/hda5            4662        4866     1646631   82  Linux swap / Solaris

```

And I've installed this in /boot/grub/menu.lst:
```
title Windows XP
root (hd0,1)
makeactive
chainloader +1
```

Now, when I reboot and hit ESC, I get a list of Ubuntus and a Windows XP option, but if I hit Windows XP, I get this message
```
Error 13: Invalid or unsupported executable format
```

I don't fully understand the hd0,1 business, so I tried hd0,0 but got the same message.

If the answer is: "You're screwed.  You can't get XP."  then that's fine.  I don't really want it anyway, but this is part of my learning to play with Linux.

---

### Post by kansasnoob on 2008-10-17
There is no XP here:

> /dev/hda1   *           1        4661    37439451   83  Linux
/dev/hda2            4662        4866     1646662+   5  Extended
/dev/hda5            4662        4866     1646631   82  Linux swap / Solaris

You installed over XP!

You wiped it!

---

### Post by TideMan on 2008-10-17
> You installed over XP!

You wiped it!

Oh dear, what a shame.  But it was circa 2001 (i.e., even before SP1).
I guess I'm committed to Linux on this machine now.
That's good!!

---


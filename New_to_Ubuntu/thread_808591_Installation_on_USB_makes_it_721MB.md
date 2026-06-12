---
title: "Installation on USB makes it 721MB"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Tal Ormanda on 2008-05-26
After I tried making a bootable USB it makes the flashdrive 721MB instead of the 1GB it originally was. How do I make it go back to 1GB?

---

### Post by Zacariaz on 2008-05-26
I would think that a swap partition (extra memory on disk or whatever) is taking up the rest of the space on your usb.

you could try (in console):
```
sudo fdisk -l
```
to see if it all adds up.

---

### Post by BlackDragonBE on 2008-05-26
It's probably still 1GB, but in several partitions.
Start up gparted and take a look at it.

Cheers

---


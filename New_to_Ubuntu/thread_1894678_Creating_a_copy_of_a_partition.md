---
title: "Creating a copy of a partition"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by ampoland on 2011-12-13
I'm reading about copying my Ubuntu partition here ([https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)) and I'm a little confused on one point.

Once the partition is copied, both the old and the new partiion have the same UUID -- I get that. What I don't understand is why the UUID of the new partition needs to be changed if the old partiion is removed from the computer. (And from that, why grub.cfg and fstab need to be updated.) I'm sure there's a reason, but it seems to me that if you're just switching hard drives the boot information and whatnot would be fine.

I don't suppose someone can fill in the missing piecefor me? Thanks!

---

### Post by coffeecat on 2011-12-13
The way I read that page is that it is assuming that the cloned (moved to) partition will be in the same machine as the original, whether on the original hard drive or another one. In which case the UUID will have to be changed, with a need then to amend /etc/fstab and grub. If you intend to use the cloned/moved partition in another machine, then you don't need to do anything about the UUID - I agree.

The page could do with a clarification, imo, in the first paragraph.

---

### Post by ampoland on 2011-12-13
Thank you. That makes sense to me. :D I'm still just getting a handle on how things work below the surface, so to speak.

---


---
title: "Partioning an external hard drive?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by dowell22 on 2008-11-23
is it possible to partion an external hard drive?

i'm getting a laptop next month, and instead of dual booting on my computer's hard drive, i would like to put ubuntu on only part of my external hard drive, and save the rest for storage. and leave my laptop's internal hard drive alone.

---

### Post by pdwerryhouse on 2008-11-23
There's no reason why you can't do that, although it's likely you'll still have to install grub on your internal drive to boot it.

---

### Post by jimreynold2nd on 2008-11-23
Sure you can. If you know how to partition an internal hdd, partitioning an external hdd is exactly the same. Just need to select the correct HDD in your partitioning program.

Btw, which partitioning program do you use? I can help you with gparted, paragon partition manager, partition magic and Ubuntu installation's partition wizard if you need.

Good luck, and gratz for the new laptop! :D I just got myself a T61 too.

---

### Post by jimreynold2nd on 2008-11-23
Oh MB, remember to click "Advance" on the summary page and tell it to put the bootloader on the external drive! This step is easy to miss and after you missed it you can't go back (I missed it a couple of times).

This is an absolute plus: Windows, Mac OSX and Solaris cannot be booted from an external drive (unless with some hacks) but Ubuntu can

---


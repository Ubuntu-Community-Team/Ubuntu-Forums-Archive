---
title: "why is my usb key not waking up from standby"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by edjoh on 2012-11-28
i have install Ubuntu 12.O4 on my usb key (intenso 16G) because my HDD is dead. it has been working for almost a week when i decided to put my computer on standby, since then any computer on which i plug in my usb key is not more recognizing it! Is there any way to wake up my usb from standby or to format it so that any other computer can see it? I am using a dell latitude D420

---

### Post by DuckHook on 2012-11-28
I'm assuming that you did a dynamic install to your USB key rather than a "Live-CD"-type install using something like UNetbootin. You should be aware that a USB key uses EEPROM memory, which only sustains a limited number of writes before it dies from write fatigue. I used to counsel against installing any dynamic system on a USB key until *oldfred* set me straight. It is apparently doable so long as you disable the write-intensive features of modern filesystems like atime, journaling and any sort of swap. I suspect that you did not, and your USB stick now has died of write fatigue.

I don't know of any way to access a USB key dead from write fatigue, but perhaps others on this forum do. It is also possible that your USB stick is still alive and has some other problem, but the fact that no other computer recognizes it also points to the fact that the key is dead. Does partitioning software like parted or gparted see it? If not, then it is probably unusable.

If you want to continue using your laptop, it really ought to be based on a HDD and not something as fragile as a USB stick.

---

### Post by benbrockn on 2012-11-28
Use a Live CD -> GParted -> format the USB stick (Make sure you pick the correct drive!) -> Delete Partition -> Format to FAT 32 (it's what Ubuntu reads when using a USB live version, that or FAT).

You may have to add a new partition table by doing this:

Device -> new partition table -> MSDOS

and then format to FAT 32 (or FAT)

**EDIT: How did your HDD die? Is there any way to fix it? (Maybe with GParted or Disk Utility?)**

---


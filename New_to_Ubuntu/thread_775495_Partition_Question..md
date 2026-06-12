---
title: "Partition Question."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by benc123 on 2008-04-30
I have been running both windows and ubuntu 7.10 on my laptop for some time now. I have just got VMWare so no longer need my windows partition. How do i delete it? Will i have to re-install ubuntu? 

Any help appreciated. 

Benc123.

---

### Post by warbread on 2008-04-30
**Back up all data you want saved!!**

```
:-$ sudo apt-get install gparted
```

You can delete your NTFS partition here and then resize your EXT3 to fill the gap.  The program can be found in System -> Administration.

---

### Post by aeiah on 2008-04-30
depending on how your system is set up this may take a long time to shift the data or expand the partition. if you havent got a seperate home partition already, you might want to consider creating a new ext3 partition over your windows ntfs and migrating your home folder to its own partition. there's a howto on this on the site. or you may want to consider changing your windows partition into just a data storage partition, so you can easily reinstall ubuntu without touching your data if something goes wrong.

---

### Post by park8b156 on 2008-04-30
Also look in to Partition Magic its seams to be faster.

---

### Post by Paqman on 2008-04-30
You might want to use the Ubuntu LiveCD to do the partitioning warbread described. The LiveCD already has Gparted installed, and you can't make any changes to a partition while it's mounted, so you need to be running from a disk anyway.

Once you've deleted the Win partition you'll still see Windows as an option in the Grub bootloader (even though it's gone)

To sort that out you want to edit the Grub file:
```

gksudo gedit /boot/grub/menu.lst

```
And comment out the five lines relating to Windows by putting a # at the start. You might also want to change the timer, since you don't need time to pick an option any more.

---

### Post by Sef on 2008-04-30
> Also look in to Partition Magic its seams to be faster.

Don't use Partition Magic.  It and GNU/Linux don't always get along.  GParted will work just fine.

---

### Post by benc123 on 2008-04-30
Thanks very much. I have just got Gparted. After i have re-sized my partitions, what will happen to the GRUB screen/Menu? Could Grub cause any problems?

---

### Post by Paqman on 2008-05-01
> **benc123 said:**
> Thanks very much. I have just got Gparted. After i have re-sized my partitions, what will happen to the GRUB screen/Menu? Could Grub cause any problems?

Nope, Grub will be fine if you've just resized things. All Grub does is tell the system which partition to look at to boot.

---


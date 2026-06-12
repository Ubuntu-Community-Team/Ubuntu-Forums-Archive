---
title: "[SOLVED] Help can I mount / to c"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Uhuabin on 2008-08-25
Hi all. here's my question. my disk was partitioned into c d e and f. and Ubuntu was settled after that. Now I've erased xp but c d e and f drives remain. could anyone pls tell me if I can find a way to merge those parts and move my / to c, or by now it should be /dev/sda1? by that I mean I want Ubuntu to be settled in my disk as if xp were never there. well that may not be necessary but I just want to see if I can do that. thank you very much. :p

---

### Post by Thelasko on 2008-08-25
Let me see if I understand.  You want to repartition your drive so Ubuntu takes up the whole thing now that Windows is gone?  For drive partitioning, I recommend GParted.  The LiveCD is very nice.

You basically want to delete the NTFS partition of the drive and expand the Linux partition (usually ext3) to fill the space.  If you have a separate /home partition, I would make that the largest part of your hard drive.

Note: by deleting the NTFS partition, any data stored there will be lost!
P.S. Back up your data!  Put it on an external drive, CDs, DVDs, just not on that drive your partitioning!

---

### Post by Uhuabin on 2008-08-25
hi thanks. yes i want to repartition it. and i've formated the partitions into ext3. but when i tried delete a partition and merge them, GParted tells me i can not delete it before i unmount all the logical patitions with higher ids.

---

### Post by Thelasko on 2008-08-25
> **Uhuabin said:**
> GParted tells me i can not delete it before i unmount all the logical patitions with higher ids.

Did you run GParted from your installed Ubuntu or from the LiveCD?  If you tried it from Ubuntu, try the LiveCD.  You won't have to worry about any partitions being mounted.

---

### Post by Uhuabin on 2008-08-25
Got it. Thank you very much. btw, is it possible to move / to another partition?

---

### Post by Thelasko on 2008-08-26
> **Uhuabin said:**
>  btw, is it possible to move / to another partition?
That I don't know.  It might be easier to reinstall Ubuntu.

Glad I could help.

---

### Post by coffeecat on 2008-08-26
> **Uhuabin said:**
> Got it. Thank you very much. btw, is it possible to move / to another partition?

Yes, but I wouldn't recommend it to a newcomer to Linux. You have to copy everything, making sure you have preserved permissions of all files and folders, then edit /etc/fstab and /boot/grub/menu.lst with the UUIDs of the new partition and finally reinstall grub.

If you want to do that, someone can guide you through because there are some intermediate steps as well, but I agree with Thelasko; it might be easier and quicker simply to reinstall.

---

### Post by Uhuabin on 2008-08-27
Thanks a lot, you've been of great help.

---


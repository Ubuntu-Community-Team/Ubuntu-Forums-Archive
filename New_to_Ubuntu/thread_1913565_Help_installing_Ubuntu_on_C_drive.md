---
title: "Help installing Ubuntu on C: drive"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by kudey on 2012-01-22
how to install ubuntu in c drive and keep d drive safe...i have all media in d drive

---

### Post by kudey on 2012-01-22
how to install ubuntu in c drive and keep d drive safe...i have all media in d drive

---

### Post by MG&amp;TL on 2012-01-22
You tagged your thread wubi...does that mean you're using wubi?

In which case, wubi does not partition, so you have no reason to worry about you drives/partitioning.

---

### Post by jockyburns on 2012-01-22
> **kudey said:**
> how to install ubuntu in c drive and keep d drive safe...i have all media in d drive

All depends whether you have a physical D drive or it's just a partitioned C drive. On my old computer I thought it had 2 HDD's but sadly it was just the one drive partitioned, one labelled C and the other labelled D.

---

### Post by Nixarter on 2012-01-22
If it is a separate hard drive, I recommend just unplugging it, to be absolutely sure you don't accidentally delete or damage anything.

---

### Post by oldos2er on 2012-01-22
Please don't multi-post on the same issue, stick to one thread.

---

### Post by Choragos on 2012-01-22
I know this isn't that helpful, but please please make a backup of your D: drive before installing.  It's pretty difficult to unintentionally overwrite your stuff when installing with the newer installers, but not impossible.

---

### Post by Mark Phelps on 2012-01-22
In standard Windows PCs, the "C" drive is the partition containing the OS and apps, and since the XP days, this has been formatted as NTFS.

The ONLY way you can install Ubuntu to a "C" drive, formatted like this, is using Wubi.

---

### Post by 3rdalbum on 2012-01-22
Boot up your computer from the Ubuntu CD and click on "Install Ubuntu" when the window appears.

The installer lists the partitions and disks on the system and asks if you want to erase any of these and install Ubuntu over the top. It also gives the option of installing "side by side" which resizes an existing partition downwards and installs Ubuntu into the new empty space - this wont destroy any data. But it might take a long time to do this - DO NOT interrupt it!

The installer takes care of you, just read what it is saying carefully. And make sure all your data is backed up first before installing any new operating system.

---


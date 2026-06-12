---
title: "help understanding how to backup with ext drive"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by irishbreakfast on 2008-06-13
I want to purchase an external drive to use a backup for three machines (two are XP only, 1 is dual book Vista/ubuntu with a shared ntfs data partition). I would like to split the drive into two partitions, ntfs and ext3 (as I plan to shift away from the shared ntfs partition most because the trash doesn't work).

So, can the ext drives be partitioned like this? Use Gpart?

The local computer shop recommended that I use FAT32, should I?

I am also unsure of what devices will actually work with ubuntu. I have learned that Seagate, particularly FreeAgent is not recommended. And looking at the website for Western Digital I found nothing that supported linux, including the download pages for various drives.

So, what about drivers?

---

### Post by Happy_Man on 2008-06-13
Any external HDD will work with any OS. Though any software that comes with the drive probably won't.

Please never use FAT32. It's old, and doesn't support files over 4 GB (which is a mark of how old it is, at the time it was created a 4 GB file was unheard of ;) )

There are windows drivers for ext3 available at [http://fs-drivers.org](http://fs-drivers.org) if you need them.

---

### Post by irishbreakfast on 2008-06-14
Yes, thank you. I thought this as well, at least until, I stopped and got the special Seagate FreeAgent 500GB on my way home. Then I searched the web for info on it and Linux. I will be returning the drive asap.

I was hoping to avoid this by finding out what manufactures products actually are working for folks out there. (As well as the driver advice)

Cheers

---


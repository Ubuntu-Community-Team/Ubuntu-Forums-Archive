---
title: "The Best format for my External HD?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by falkTX on 2008-05-17
Hi there again guys.

I TOTALLY changed to Ubuntu this week, so I started to delete some Programs and files I had on my external USB Hard Disk.
I also wanted to change the HD filesystem (now is NTFS). I've already copied all the files for my main HD, and... I just don't know one thing - Wich format should I use for a 1TeraByte USB2/SATA2 external hard disk?

**NTFS** doesn't seem (to me) to be the best option (I only use Linux for now, and I'm not planning to use Windows ever again).
Maybe **XFS**?

**What do you recommend for me?**
(Like I said, it's a **1TB drive**, connected only to Linux OSes, and I use a lot of big files (I have almost all Ubuntu versions on it).

Thanks for your time.

---

### Post by Joeb454 on 2008-05-17
I don't think NTFS would cause a problem, as you can read/write NTFS partitions by default now :)

Though if you want you could use ext3, you'll have to look into the benefits of each :)

---

### Post by falkTX on 2008-05-17
Sometimes I got the problem when it was unproperly shutdown.
But I also don't want NTFS cause Windows users can acess it and modified it.

If possible I would like to encrypt my whole external disk (like I did with the default one, in this laptop).
Is that possible?
I mean, only I can write to the disk. Other users can only see the files, or maybe not at all.

---

### Post by Tom--d on 2008-05-17
I don't like NTFS because it reminds me of Windows..

---

### Post by sasek118 on 2008-05-18
> **Joeb454 said:**
> I don't think NTFS would cause a problem, as you can read/write NTFS partitions by default now :)

Apparently after switch to 8.04 my USB NTFS drive mount ro :( Does anyone know how can I fix this?

*===edit===*
Solved. FS was broken. I've fixed it under XP. Do you know how can I fix NTFS with Linux?

---


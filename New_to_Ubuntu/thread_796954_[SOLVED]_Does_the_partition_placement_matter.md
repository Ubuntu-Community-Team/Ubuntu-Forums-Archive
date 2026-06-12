---
title: "[SOLVED] Does the partition placement matter?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-16
I'm making a new partition so that I may put my /home on it.

I'm running a LiveCD session. The attached screen shot shows what' going on. I tried this exact same thing earlier today and got some error message about an installation problem. So I decided it was easier to re-install the OS.

This disk has it's / on sda1, I'm adding (probably) /dev/sda3. Does OS care whether the sda1 sits on the disk before sda3, or is it smart?

Also, while I would like to make the /sda3 not the primary partition, but is there something better?

---

### Post by Oldsoldier2003 on 2008-05-16
> **Mark_in_Hollywood said:**
> I'm making a new partition so that I may put my /home on it.

I'm running a LiveCD session. The attached screen shot shows what' going on. I tried this exact same thing earlier today and got some error message about an installation problem. So I decided it was easier to re-install the OS.

This disk has it's / on sda1, I'm adding (probably) /dev/sda3. Does OS care whether the sda1 sits on the disk before sda3, or is it smart?

Also, while I would like to make the /sda3 not the primary partition, but is there something better?

The os doesn't care about what disk your partitions sit on. I've got root and data partitions strewn across a couple hard drives.

---

### Post by rlcomstock3 on 2008-05-16
The OS might not care, but for the best performance you might care.  Typically it is suggested if you have multiple hard drives that you take the first section of each of them and make it swap except for your first hard drive make the first section of that /boot.  I don't know that it will affect it enough to matter unless you are doing hard drive intensive computing. It is the suggested method, and for me it has worked well am my linuxing years.

---

### Post by Oldsoldier2003 on 2008-05-16
> **rlcomstock3 said:**
> The OS might not care, but for the best performance you might care.  Typically it is suggested if you have multiple hard drives that you take the first section of each of them and make it swap except for your first hard drive make the first section of that /boot.  I don't know that it will affect it enough to matter unless you are doing hard drive intensive computing. It is the suggested method, and for me it has worked well am my linuxing years.

I've seen and used this conventional wisdom as well. Personally I don't think it makes much difference except for database and mail servers.

---


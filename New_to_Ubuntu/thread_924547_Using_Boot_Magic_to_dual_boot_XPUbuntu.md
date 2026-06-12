---
title: "Using Boot Magic to dual boot XP/Ubuntu"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by TheIllustriousPotentate on 2008-09-19
Ok, I posted a thread a while back about installing Ubuntu as a dual boot with XP "without installing Grub".

I want to use Boot Magic, and Partition Magic to do all the work, and just simply install Ubuntu on the second partition created by Partition Magic, and have Boot Magic (not Grub) control the boot up.

Everyone says that at the end of the Ubuntu setup, you can uncheck the box to use the Grub boot loader. That should work for me if I'm using Boot Magic.

However, It seems that durring the installation, Ubuntu wants to partition the drive. If I already partitioned the drive, I don't want Ubuntu to partition the 2nd partition, or the first (XP) partition; I just want it to install into the already created second partition. How do I do that?

On a second note. I can't seem to find my Partition Magic disc, only my Boot Magic disc. If I can't find my Partition Magic disc, can I go ahead and let Ubuntu partition the drive, and still get Boot Magic to recognize the second partition with Ubuntu on it?

Thanks.

---

### Post by angelsguitar on 2008-09-20
> **TheIllustriousPotentate said:**
> Ok, I posted a thread a while back about installing Ubuntu as a dual boot with XP "without installing Grub".

I want to use Boot Magic, and Partition Magic to do all the work, and just simply install Ubuntu on the second partition created by Partition Magic, and have Boot Magic (not Grub) control the boot up.

Everyone says that at the end of the Ubuntu setup, you can uncheck the box to use the Grub boot loader. That should work for me if I'm using Boot Magic.

However, It seems that durring the installation, Ubuntu wants to partition the drive. If I already partitioned the drive, I don't want Ubuntu to partition the 2nd partition, or the first (XP) partition; I just want it to install into the already created second partition. How do I do that?

On a second note. I can't seem to find my Partition Magic disc, only my Boot Magic disc. If I can't find my Partition Magic disc, can I go ahead and let Ubuntu partition the drive, and still get Boot Magic to recognize the second partition with Ubuntu on it?

Thanks.

To have better control of Ubuntu's partitioning during installation, you should choose a Manual instead of the Guided partitioning methods (Manual is usually the last option on the screen when you get to the partition step during install).  That way you may be able to do what you want.

I've never used Boot Magic, but may I respectfully ask: Why would you want to use Boot Magic instead of Grub?  I too have a dual boot configuration; well, in fact, right now I have a triple boot configuration (Ubuntu - 64Studio - XP Home) using Grub and never had any problems.

---


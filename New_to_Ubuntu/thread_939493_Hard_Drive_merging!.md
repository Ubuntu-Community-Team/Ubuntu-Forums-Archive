---
title: "Hard Drive merging!?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Nider on 2008-10-06
Hi... I would try to explain as good as I can but english is not my main language.

I have my hard drive divide in two parts. I was for Win and the other for Ubuntu. But my win got a nasty virus and I stop using it. I noticed that I can access all my win's files by mounting the part of my hard drive that belonged to win, part that Ubuntu recognizes as "37.1 GB Volume: disk". I saved all that was important and erased everything else.

Now my question is. Is there any way that I can make Ubuntu "assimilate" that part of the hard drive, so the part that is the main hard drive of Ubuntu becomes bigger. I don't want them been two separate units.

Or in the other hand, is there any way to hide the icon of that "unit" from my desktop, because I like my desktop clean, if there is a way to do this, I wouldn't mind having the H.D. separate in two parts.

---

### Post by dhughes on 2008-10-06
> **Nider said:**
> ...Now my question is. Is there any way that I can make Ubuntu "assimilate" that part of the hard drive, so the part that is the main hard drive of Ubuntu becomes bigger. I don't want them been two separate units.

 Yes, as far as I know you can use the partition Windows was on but since you were dual booting you'll have to do something with the bootloader since Windows will be gone. I don't know where GRUB would be, probably on or near the Windows partition and if wiping that will wipe GRUB. I'm sure someone with some experience will help you with some more detailed information.

> **Nider said:**
> Or in the other hand, is there any way to hide the icon of that "unit" from my desktop, because I like my desktop clean, if there is a way to do this, I wouldn't mind having the H.D. separate in two parts.

 Yes. [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by DGortze380 on 2008-10-06
> **Nider said:**
> 
Now my question is. Is there any way that I can make Ubuntu "assimilate" that part of the hard drive, so the part that is the main hard drive of Ubuntu becomes bigger. I don't want them been two separate units.


Yes, you can use gParted 
```

sudo apt-get install gparted

```

to delete your old windows partition and expand your ubuntu partition. back up all important files on both partitions first, and never perform these opperations on a mounted drive.

---

### Post by mister_pink on 2008-10-06
> **DGortze380 said:**
> and never perform these opperations on a mounted drive.
Which essentially means the easiest way is to use the live CD, which already has the partition manager in the menu. Make sure you back up first.

As someone else mentioned, your computer may not boot afterwards. You'll have to use the live CD again to access your disk and edit /boot/grub/menu.lst and probably change references to things like "(hd0,1) to (hd0,0) or similar.

---

### Post by vanadium on 2008-10-06
The safest approach will be to reformat your Windows partition to an ext3 partition that you can use for data storage. You can mount it in /etc/fstab under /mnt instead of /media to keep your desktop clean, and link it to a convenient location in your home directory.

Moving your partition is quite tricky for the following reasons: 1) moving a partition is a very slow process (count overnight) that not always succeeds successfully 2) as pointed out, you need to "repair" the boot system "grub" after that. If you want a single partition, you would proceed far quicker, easier and safer with a reinstall.

---


---
title: "how to do Partition for Windows In Ubuntu."
date: 2012-06-07
forum: New to Ubuntu
---

### Post by sandip144 on 2012-06-07
Hi,

I have Ubuntu in my Laptop with 80GB Sata HDD.
Now when i install Windows it says there is no disk Available.
I tried Gparted for partition but the "Resize" icon is hidden.
Now Please help me to boot Windows XP in my Laptop.

---

### Post by carl4926 on 2012-06-07
Windows will need most of the 80GB HD :D

Post the output of

```
sudo fdisk -l
```

---

### Post by fantab on 2012-06-07
Windows :C should be a minimum 30GB for it work. If you can then go for bigger Hard disk.

---

### Post by Mark Phelps on 2012-06-07
First of all, you can't modify a partition while it's in use.  So, you can't resize the Ubuntu partition while you're running Ubuntu from your hard drive.

You will need to boot from an Ubuntu LiveCD or LiveUSB and use GParted from there.

Second, even Win7 does not need 80GB!  For an XP installation, 30GB will give you plenty of room.

---

### Post by sandip144 on 2012-06-08
Hi,

Thanks a Lot. I have Installed Windows 7.

---

### Post by Mark Phelps on 2012-06-08
OK, then if it's working for you, please use the Thread Tools to mark this thread a SOLVED.  thanks

---


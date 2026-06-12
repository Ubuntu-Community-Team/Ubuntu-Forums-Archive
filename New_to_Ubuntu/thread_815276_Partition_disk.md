---
title: "Partition disk"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by link- on 2008-06-01
Hi, 

Yesterday I installed sucessfully ubuntu HH with the help of Logos34 on an external HDD. 
When I installed the OS on my external HDD at the partition menu I selected use entire disk, the problem is that now a 250GB external HDD is only for the linux OS and there's no way that I could use it to store anything from W. Vista in it. There's a way that I could store other things from windows in it?

Thanks

-link

---

### Post by omi291 on 2008-06-01
You could create a new partition to hold whatever it is you want to...but could you elaborate on what it is exactly that you want to do?

---

### Post by link- on 2008-06-01
> **omi291 said:**
> You could create a new partition to hold whatever it is you want to...but could you elaborate on what it is exactly that you want to do?

What I want to do is to use my external HDD as a portable device where I can store any kind of data, programs from linux and windows and to have installed ubuntu on other partition

---

### Post by link- on 2008-06-01
How do I create another partition and resize the ubuntu partition?

---

### Post by Nevis on 2008-06-01
> **link- said:**
> How do I create another partition and resize the ubuntu partition?
I would use gParted, it's agreat tool for working with partitions. Format the partition as NTFS and you'll be fine. Ubuntu can even read those partitions if need be.

Try this how-to to give you an idea of how to begin. Make sure you're working with the right disk though!

---

### Post by link- on 2008-06-01
> **Nevis said:**
> I would use gParted, it's agreat tool for working with partitions. Format the partition as NTFS and you'll be fine. Ubuntu can even read those partitions if need be.

Try this how-to to give you an idea of how to begin. Make sure you're working with the right disk though!

:confused: I wonder where's the How to?

---

### Post by Nevis on 2008-06-01
Duh, sorry about that. Often my fingers are faster than my brain :-(

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by link- on 2008-06-02
I tried to run the gparted live-cd but for some reason the live-cd couldn't boot. I also tried the gparted program from ubuntu but I can't unmount anything. There is any other program that could help?

---

### Post by Nevis on 2008-06-02
> **link- said:**
> I tried to run the gparted live-cd but for some reason the live-cd couldn't boot. I also tried the gparted program from ubuntu but I can't unmount anything. There is any other program that could help?
I would be questioning why you can't get the boot CD to run but if you really want to try other utilities check here;

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

I can't offer much more advice as I've always used GParted.

---

### Post by Victormd on 2008-06-02
> **link- said:**
> How do I create another partition and resize the ubuntu partition?

Try gparted. Open a terminal and type:
```
sudo apt-get install gparted
```
and you'll have a GUI that allows you to "see" your HD and do whatever you want to... (you might have to format the newly created partition using Windows though...)

Sorry, just saw your last post...
It's odd that you can't boot from the Gparted liveCD, I would probably look into that before doing anything else. If you want, Windows Vista has a partition manager that you could use. I'm not sure how it will deal with ext2 or ext3 and you might have to format the whole thing, partition from windows, and re-install ubuntu...

---

### Post by Victormd on 2008-06-02
> **link- said:**
> I also tried the gparted program from ubuntu but I can't unmount anything. There is any other program that could help?

You won't be able to unmount because you're trying to unmount the HD that's running gparted, that's why you would need to try run it from the live CD.

---

### Post by Golem XIV on 2008-06-03
Instead of partitioning the external disk, how about enabling Windows to read/write the ext3 file system?  Here's a newbie-friendly way of doing it:

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Good luck.

---

### Post by Victormd on 2008-06-03
I personally prefer Golem XIV's suggestion (I prefer ext3 over ntfs). The only downside is that this is a removable drive and if you connect it to another computer, you'll have to install the ext3 reader on it as well...

---


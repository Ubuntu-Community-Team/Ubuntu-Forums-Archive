---
title: "Ubuntu auto mounts all my drives at boot"
date: 2015-09-16
forum: New to Ubuntu
---

### Post by johan28 on 2015-09-16
Hello,

My computer have several hardrives and some are NTFS-drives for my windows installation. 
The problem is that they automounts during boot even if they're not added in /etc/fstab

This driving me insanse since I can't find the solution.

What to do? Where to start to look? :)

---

### Post by jim_deadlock on 2015-09-16
First of all, how are you checking to see if they are mounted? If You see them showing in your GUI file manager it doesn't necessarily mean they are mounted, they will be displayed but you have to click them to actually mount them.

If this doesn't solve the problem, please post the contents of /etc/fstab and also the output of:

```
sudo blkid
```

---

### Post by johan28 on 2015-09-16
You're right. It happens when I click. My bad! :)

Thanks for spending you time on this one! :)

---

### Post by Bucky Ball on 2015-09-16
Welcome and please mark the thread as solved to help others. See the first link in my signature. 

Enjoy the ride. :)

(PS: You can right click them instead of left click and you should see that you have the option to mount partition.)

---

### Post by johan28 on 2015-09-16
> **Bucky Ball said:**
> Welcome and please mark the thread as solved to help others. See the first link in my signature. 

Enjoy the ride. :)

(PS: You can right click them instead of left click and you should see that you have the option to mount partition.)

Done! Should I also add how 'removed' them from sidebar in nautilus?

---

### Post by Bucky Ball on 2015-09-16
> **johan28 said:**
> Done! Should I also add how 'removed' them from sidebar in nautilus?

Why the heck not? Thanks for sharing and enjoy the ride. :)

PS: You probably don't intend to, but good idea not to mount the Windows partition itself from within Ubuntu. Messing with files in the Win OS from Ubuntu can screw things up when you boot Win.

---

### Post by johan28 on 2015-09-16
> **Bucky Ball said:**
> Why the heck not? Thanks for sharing and enjoy the ride. :)

PS: You probably don't intend to, but good idea not to mount the Windows partition itself from within Ubuntu. Messing with files in the Win OS from Ubuntu can screw things up when you boot Win.

That's because I didn't want to have them clickable in my sidebar :) I don't know the state know but when i used Linux about 10 years ago it wasn't recommended to mount/use your NTFS-partitions.

---

### Post by johan28 on 2015-09-16
I followed this guide: [http://askubuntu.com/questions/124094/how-to-hide-an-ntfs-partition-from-ubuntu](http://askubuntu.com/questions/124094/how-to-hide-an-ntfs-partition-from-ubuntu)

A bit down they explain how to create a rules-file in /etc/udev/rules.d

---

### Post by Bucky Ball on 2015-09-17
Using NTFS is fine, in fact, advised if you are sharing data between the two OSs. Accessing the partition where you have Windows installed and messing with operating system files in there while booted into Ubuntu is not.

Ubuntu should, in fact, now read/write NTFS partitions 'out of the box'. A lot changes in 10 years in techno-world. I'd say disregard much of your Ubuntu experience from that long ago. I think the first Ubuntu popped up around 2005-6 and that is just 10 years. :)

---


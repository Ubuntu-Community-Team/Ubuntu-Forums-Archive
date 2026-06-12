---
title: "Create partition while running 12.04"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2012-06-14
I would like to create a partition to install XP on.  I am already using 12.04, the only tutorials I can find are if you have windows and you want to dual boot ubuntu.

---

### Post by wilee-nilee on 2012-06-14
> **DarrenMR415 said:**
> I would like to create a partition to install XP on.  I am already using 12.04, the only tutorials I can find are if you have windows and you want to dual boot ubuntu.
 
If you have an unallocated space you can, use gparted,  if not, you have to use a live cd to make one, if you are using a single HD.

---

### Post by DarrenMR415 on 2012-06-14
I have gparted but it wont let me do anything because it says the drive is mounted.

---

### Post by wilee-nilee on 2012-06-14
> **DarrenMR415 said:**
> I have gparted but it wont let me do anything because it says the drive is mounted.

If you are trying to resize the partition you're using, that wont work, ubuntu does not due live resizes. Take a screenshot of gparted and post it, it will be easier to see what is up, unless this last post covers the problem.

If there is a reason why you would not just default to a live cd, then please share.

---

### Post by DarrenMR415 on 2012-06-14
I dont really know what creating a live cd entails.

---

### Post by wilee-nilee on 2012-06-14
> **DarrenMR415 said:**
> I dont really know what creating a live cd entails.

You can't resize a partition you're using, so a live cd or thumb is needed, here is a link.
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

I believe a dvd is now needed as the ISO is a little oversized, not sure though.

Or you can use a app like unetbootin to load a usb flash drive.

Gparted in on the live cd environment.

You are not really in the best of circumstances here in that windows is best being the first partition.

---

### Post by DarrenMR415 on 2012-06-14
> **wilee-nilee said:**
> You can't resize a partition you're using, so a live cd or thumb is needed, here is a link.
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

So basicly I need to go back through like I am going to reinstall ubuntu and change the partition?

---

### Post by Shadius on 2012-06-14
> **DarrenMR415 said:**
> So basicly I need to go back through like I am going to reinstall ubuntu and change the partition?

Ideally, you should install Windows first, then Ubuntu.

---

### Post by DarrenMR415 on 2012-06-14
> **Shadius said:**
> Ideally, you should install Windows first, then Ubuntu.

I have files that I would like to keep.  While AFAIK I wouldnt be able to keep by going in that direction.

---

### Post by Shadius on 2012-06-14
> **DarrenMR415 said:**
> I have files that I would like to keep.  While AFAIK I wouldnt be able to keep by going in that direction.

You can perform a backup, then reinstall Ubuntu after you've installed Windows first.

---

### Post by Hasan55 on 2012-06-14
> **DarrenMR415 said:**
> I would like to create a partition to install XP on.  I am already using 12.04, the only tutorials I can find are if you have windows and you want to dual boot ubuntu.
if you have free space in you hard drive so it is easy to install just run the xp  **** by booting and creat a nfst formate in your hard drive and just install it then automatically it will grub your previous system and dual boottig will be started. if your hard drive don't have the free space the make it by using windows 7 disk.........good luck

---

### Post by DarrenMR415 on 2012-06-14
> **Hasan55 said:**
> if you have free space in you hard drive so it is easy to install just run the xp  **** by booting and creat a nfst formate in your hard drive and just install it then automatically it will grub your previous system and dual boottig will be started. if your hard drive don't have the free space the make it by using windows 7 disk.........good luck

I have just over 100gbs free, I can partition by attempting to install xp overtop of ubuntu?

---

### Post by wilee-nilee on 2012-06-15
> **DarrenMR415 said:**
> I have just over 100gbs free, I can partition by attempting to install xp overtop of ubuntu?

No you have to resize the ubuntu leaving a unallocated for the ntfs for XP, which has its own problems with partition numbers being in order.

I would also just clone the ubuntu to a external, then install correctly with XP in a sda1 partition, rather than ubuntu.

Or just put the XP in a virtual like virtualbox.

---

### Post by DarrenMR415 on 2012-06-15
I like the cloning option.  That sounds like the best way to get this done.

---


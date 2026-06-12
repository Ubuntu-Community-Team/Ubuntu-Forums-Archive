---
title: "Grub mess needs cleaning up.Error 15"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by yogo on 2008-06-01
I installed gOS using the persistent method at pendrivelinux but after two failures, decided to install it on the same partition as Gutsy.

I decided I did not want it and so decided to delete the partition that had gOS on it. Then I got the error 15. I had taken a look at my menu lst and it looked ok but I had problems so I used SGD to try to repair grub but was not successful so I removed grub from the MBR and can not boot XP.

Can I use the XP boot to add Ubuntu? Or do I have to re-install grub? What program is used to view Linux from Windows?

One of the things I did not like about gOS was I could not mount my Gutsy or windows partitions.

TIA

---

### Post by Daveth on 2008-06-01
one of the easiest ways for you to sort out this dog's dinner might be to burn Super_grub onto a cd and use that to restore the various MBR/Grub settings so far trashed. It will also stand you in good stead for the future. This at

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The reason for you binning GOS in the first place might have been alleviated by reference to this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

with a bit of GOS-specific tweaking, of course. I'm sure a number of folk will suggest other solutions. Hope the re-build goes well.

---

### Post by yogo on 2008-06-01
[quote=Daveth;5093415]one of the easiest ways for you to sort out this dog's dinner might be to burn Super_grub onto a cd and use that to restore the various MBR/Grub settings so far trashed. It will also stand you in good stead for the future. This at

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The reason for you binning GOS in the first place might have been alleviated by reference to this:



I have been using the Super grub disk but running into troubles, I remember using it before ans was simple to fix. I did get my Windows ok as I used it to remove grub from the boot.ini.


I think I will have to do more reading at Bigpond, excellent for learning, well written

Thanks for the link on psychocats.

---


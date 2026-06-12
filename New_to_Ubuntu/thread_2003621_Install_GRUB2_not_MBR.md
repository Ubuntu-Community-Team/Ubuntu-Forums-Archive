---
title: "Install GRUB2 not MBR"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Grem41 on 2012-06-14
Hi all,

Hope you guys can help. After much deliberation I have just decided to do a HDD install on an ancient laptop.
The aim is to have 3 operating systems plus a swap partition. These will partitioned in this order as follows:  

1.  Microsoft Windows XP
2.  Puppy Linux Lucid 5.25
3.  Linux Swap
4.  Lubuntu 12.04 "Precise Pangolin" - Release i386

My problem is that I believe whilst installing Lubuntu GRUB2 overwrites the MBR - This where my Boot Manager is located so I can boot off the USB as my bios does have that option.
 I think I therefore need to have GRUB2 installed in same partition as Lubuntu installs its (4th partition) in. how do I go about it ? Any ideas

---

### Post by Cheesemill on 2012-06-14
You can choose where you want to install GRUB2 during the Lubuntu installation process.

---

### Post by Grem41 on 2012-06-15
Thanks Cheesemill,

Now installed into own partition with GRUB2.

Thanks again

---


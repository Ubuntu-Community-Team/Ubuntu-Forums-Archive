---
title: "[SOLVED] How does the installer partition drives?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-06
I wanted to know how Ubuntu partitions hard drives. When I have done it myself in the past I have three, boot, swap, root. But when the installer does it, it only has two.

---

### Post by bluefrog on 2008-05-06
by default the partitioner will create 2 drives indeed, / and swap. If you use the default LVM, you will have /boot and 2 LVM volumes (/ and swap).

It would be a good idea to create / swap and /home but it is not the default right now. 
Nothing prevents you from doing so by partitioning manually.

---

### Post by tjwoosta on 2008-05-06
yes the defualt install of ubuntu will only make two partitions the / partition and the swap partition

(if you manually set things up it is a good idea to create a seperate /home partition)
just so you can always upgrade ubuntu or whatever you want without touching any of your personal data and files 

or if something happens to ubutnu you can reinstall only the / partition and still have all of your data stored on the /home partition

---

### Post by slughappy1 on 2008-05-06
How about not having a /boot partition? How does that work? I thought you needed a /boot partition?

---

### Post by tjwoosta on 2008-05-06
/boot partition?   i dont have one

im pretty sure that grub installs to the MBR (master boot record)  rather than to a partition of its own

---

### Post by Oldsoldier2003 on 2008-05-06
> **tjwoosta said:**
> /boot partition?   i dont have one

im pretty sure that grub installs to the MBR (master boot record)  rather than to a partition of its own

sure you do. its in the root. just not a partition hehe

as for grub... you can install grub in the mbr or you can install it in the boot partition. that would be / if you don't have a separate /boot

the reason you would want to do this is to ease maintenance of multiple distros by chainloading

---


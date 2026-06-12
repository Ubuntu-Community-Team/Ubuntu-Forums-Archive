---
title: "Re: Problems booting into Ubuntu (Dual Boot)"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by rexracer86 on 2008-08-24
helloo..im using ubuntu 8.04 nw..im using it along with windows xp..i hav no problem in booting ubuntu in grub os menu..but whenever i choose windows xp,,xp boots..but after xp shut down or restart..no grub menu shows..the system directly enters XP..to regain or get into ubuntu i use ubuntu installation cd & enter rescue mode & type the following commands in shell( the command usage is given by my cousin who is a system adminstrator.)..the command is

fdisk /dev/sda..it gives another for disks..

then i use 'a' to toggle between partitions..after saving..rebootin systm shows menu again ..
how can i fix this???..that s to use both windows & ubuntu ..plzzz help..

---

### Post by caljohnsmith on 2008-08-24
Using "a" with that fdisk command toggles which partition has the boot flag set. Therefore your Grub is probably set up to boot off of the active partition (the partition with the boot flag set) by default.

Please boot up your Live CD, and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition in the form /dev/sdaX where X is the partition number; your Ubuntu partition should be type "linux" under "system". 

Next mount it and print Grub's menu.lst:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
Please post the results of all the above commands.

---


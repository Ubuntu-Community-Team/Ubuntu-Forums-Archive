---
title: "Partition Resizing"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by afkaos on 2008-05-14
Hello there!
I recently upgraded to 8.04 and have decided that I no longer need my Windows Partition. I currently have a Dual boot, but would like to get rid of the windows partition to give room to Ubuntu. What is the easiest/safest method of doing this? 

Thanks!

---

### Post by PartisanEntity on 2008-05-14
1. Backup all data both in your windows and ubuntu partitions

2. Boot your computer from the ubuntu live cd

3. Under System > Preferences or Administration is a partitioning tool that is easy to use.

Good luck :)

---

### Post by Dani Filth on 2008-05-14
> **PartisanEntity said:**
> 1. Backup all data both in your windows and ubuntu partitions

2. Boot your computer from the ubuntu live cd

3. Under System > Preferences or Administration is a partitioning tool that is easy to use.

Good luck :)

That is called "Partition Editor" in System > Administration.
It can also be executed by typing "gparted" in the Terminal, I reckon.

---

### Post by Stefan Stryjecki on 2008-05-14
The easiest and safest way to do it would be to just reformat you Windows partition using ext3, reiserfs or whatever you like and then use it as an additional data partition. If it is big enough you might move your home directory there. Just don't forget to update /etc/fstab if you do so.

---

### Post by coolen on 2008-05-14
There's a GParted LiveCD which has saved me a few times. Handy tool to have in your collection.

I think it comes with a file manager if you need to do some backup.

---

### Post by django0909 on 2008-05-14
I'd say use gparted.

```
sudo apt-get install gparted
```

---

### Post by indytim on 2008-05-14
Don't forget to adjust your menu.lst also :)

IndyTim

---


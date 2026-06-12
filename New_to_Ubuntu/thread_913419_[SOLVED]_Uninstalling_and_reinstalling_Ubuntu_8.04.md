---
title: "[SOLVED] Uninstalling and reinstalling Ubuntu 8.04"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by will_s54 on 2008-09-07
My main computer has Vista and Ununtu on seperate drives with the Ubuntu drive been the number one hard drive boot . Now I want to completely eradicate the Ubuntu drive and its contents and try again from start.

So what is the easiest way to do this ?

---

### Post by hyper_ch on 2008-09-07
just overwrite the ubuntu partitions upon reinstalling

---

### Post by will_s54 on 2008-09-07
I thought it may be that simple but didnt want to actually somehow overwrite my Vista installation.

I assume overwrite does a format and sets up a new Grub boot manager ?

---

### Post by Tatty on 2008-09-07
yes, it will sort out grub for you as before. just make sure you select the correct partition to install to.  

If you are unsure of manual partitioning in the ubuntu installer (it worried me the first few times) then you could try deleting the ubuntu partition via gparted, then when installing tell the partitioner to use the free space.  But obviously this is a long way round, so use it as a fallback if unsure.

---

### Post by will_s54 on 2008-09-09
well I blew it

To many hard drives and not checking them before

oh well, needed a cleanout and 99% of stuff backed up on other drives

Anyway Vista reinstalled and Ubuntu now on the hard drive I want it on

---


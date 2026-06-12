---
title: "[SOLVED] how to install to a specific partition"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-22
I just booted up with a minimal CD. I already have Xubuntu running on that machine and I want a dual boot of Xubuntu with a minimal + IceWM.

But I don't see any options for installing the minimal into a specific partition. How would I tell it to install into my sda6? I already have the partitions created when I installed Xubuntu.

Does the minimal CD even have that option?

---

### Post by rockerphil on 2008-05-22
i don't think the minimal CD has a partitioner, so what i'd do is just use the full blown server CD and just install a command line interface before building from the command line up. the only drawback of that is a bit longer download time

---

### Post by Inxsible on 2008-05-22
> **rockerphil said:**
> i don't think the minimal CD has a partitioner, so what i'd do is just use the full blown server CD and just install a command line interface before building from the command line up. the only drawback of that is a bit longer download timeWell I don't need the partitioner. I already have the partitions set up.

Is there an option to install into a specific partition?

If not, I think i just wasted a CD on 9.5 mb ;-)

---

### Post by Drakkor on 2008-05-22
Use re-writeables ! (CDRW) :)

---

### Post by LeoSolaris on 2008-05-22
If you mean option on your grub menu, you need to manually alter your grub's menu.lst in your original Xubuntu. 

[This might be helpful]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

---


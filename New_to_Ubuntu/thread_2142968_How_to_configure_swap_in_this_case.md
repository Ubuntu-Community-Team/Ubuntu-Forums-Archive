---
title: "How to configure swap in this case?"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by abexman on 2013-05-07
OK, so I have Windows 7 and Ubuntu 12.04 on dual boot. I think Windows 7 is on on sda2 shown below. I then have some separate partitions for my Ubuntu install but I just realized I have no swap! What would you suggest my best configuration would be going forward to allocate swap? Just make that unallocated  ~4gb linux-swap? This machine has 3.7 GB RAM. 

[IMG]http://s5.postimg.org/ii6gz7cg6/Screenshot_from_2013_05_07_09_41_05.jpg[/IMG]

---

### Post by ibjsb4 on 2013-05-07
If your doing ok without swap, why bother?

---

### Post by Drenriza on 2013-05-07
A swap partition is something of the past. Since 4GB ram was available, normal users dont use the swap space.
And if they do, they got a problem in their system if it's that memory hungry.

So dont bother using swap in Ubuntu or Windows.

---

### Post by Cheesemill on 2013-05-07
> **Drenriza said:**
> A swap partition is something of the past. Since 4GB ram was available, normal users dont use the swap space.
And if they do, they got a problem in their system if it's that memory hungry.

So dont bother using swap in Ubuntu or Windows.

Unless you want to be able to hibernate your machine, in which case your swap needs to be equal or larger than the size of your RAM.

---

### Post by abexman on 2013-05-08
Well, I would not do anything with swap but I was trying to get VMWare Player up and running to run some Windows only programs - and it seems to need some swap  I think. The VMware Player was erroring because I had no swap, then I added a swap and now the player launches OK. I guess I could use shared RAM for the VMware player but I was not able to figure out how to do that.

---


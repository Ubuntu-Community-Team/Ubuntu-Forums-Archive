---
title: "My Ububtu is taking soo long to boot up please help"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by appoloin on 2008-06-03
All of a sudden it take over 2 min for ubuntu to bootup from pressing the power button to the main log in screen. any way i can speed things up? clean thing?

i have 3 gig ram and duel core cpu should not really be this long to boot up right?

---

### Post by dranockcir on 2008-06-03
Hi,

I haven't really tried any of these tips but after reading through them it's where I would start if I was gonna try to speed things up. Can't hurt to have a look. :) [http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

Rick

---

### Post by philinux on 2008-06-03
Press esc. edit the kernel line to remove quiet then press b to boot.

Read the text during boot and look where the process hangs.

Definitly fixable.

Mine takes 15 seconds from grub to login screen.

You could also install bootchart from the repo.

---

### Post by K.Mandla on 2008-06-04
> **philinux said:**
> Press esc. edit the kernel line to remove quiet then press b to boot.

Read the text during boot and look where the process hangs.

Definitly fixable.

Mine takes 15 seconds from grub to login screen.

You could also install bootchart from the repo.
+1. Find out where the system is hanging, and that will give you a clue how to fix it. 

Bootchart will also help, if the problem isn't obvious.

---


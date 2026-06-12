---
title: "[SOLVED] Increasing Hard Drive Space"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Kavkaz86 on 2008-06-21
Hi Members, 

I have a problem. I currently have Ubuntu installed on my machine along with windows in a dual boot method. When I installed ubuntu I chose the minimum space requirement which is 5 GB. I would like to increase this space and make half available for windows and half available for linux. is there a way of doing that? 

**PS- Would be very helpful if you could explain this in a step by step method. 

Thank you,

kavkaza

---

### Post by geo909 on 2008-06-21
Well, you could always use gparted that exists in your ubuntu livecd.
There will be somewhere in system->administration I think.
It's quite safe and easy, though i would advise to back up your important files from both xp and ubuntu..

EDIT: What you do is that you run gparted, unmount any mounted drives/partitions that you need to resize. Then you will have the option by right-clicking to resize a partition. Click on your ubuntu partition bar and resize it to the left until you reach the desired size...

---

### Post by hyper_ch on 2008-06-21
you used wubi install, right?

---

### Post by Kavkaz86 on 2008-06-21
> **hyper_ch said:**
> you used wubi install, right?

If wubi means I have installed it in a windows session first then my answer is yes.

---

### Post by hyper_ch on 2008-06-21
> **Kavkaz86 said:**
> If wubi means I have installed it in a windows session first then my answer is yes.

yes, so you can forget about all the other things geo909 said

---

### Post by Kavkaz86 on 2008-06-21
> **hyper_ch said:**
> yes, so you can forget about all the other things geo909 said

That's what I thought ... ! Do I need to reinstall for a new copy?

---

### Post by hyper_ch on 2008-06-21
why not do a proper install in an own partition? would also be better for performance...

---


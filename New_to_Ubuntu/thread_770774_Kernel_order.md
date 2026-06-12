---
title: "Kernel order"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by cmuluna on 2008-04-27
I performed a clean install of 8.04 on Thursday, and for two days, the only boot-up options for operating systems were "Ubuntu 8.04, Kernel 2.6.24-16-generic" (and "Recovery Mode" and "memtest 86+") as well as Longhorn. This worked great since I could boot up my laptop, walk away, and then come back a few minutes later to the Ubuntu log in screen. 

However, as of yesterday, there is another option, specifically "Ubuntu 8.04, Kernel 2.6.24-16-386" (and "Recovery Mode"). This appeared after I was installing "VirtualBox" (I believe that's when it appeared. Not 100% sure.) Anyway, 24.16.386 is now at the top of the order, and when it boots, it says that it has to use graphics safe mode, and so I restart, select 24-16-generic, and I have no problems. 

So, my question is this: can I either delete the 24-16-386 option or place the 24-16-generic option above the rest? If so, how would I do this?

Optional questions to answer (for my own expanding knowledge of Ubuntu): What am I looking at? Is this the GRUB menu? Is there is any reason why I SHOULD be using 24-16-386? Just curious.

Thanks.

cmuluna

---

### Post by rubicon on 2008-04-27
> **cmuluna said:**
> 
So, my question is this: can I either delete the 24-16-386 optionJust delete unneeded kernel from synaptic, that's it. And yes, that's grub menu, /boot/grub/menu.lst.

> **cmuluna said:**
> Is there is any reason why I SHOULD be using 24-16-386? Just curious.Honestly — no. Unless you run Pentium I machine :D

---

### Post by cmuluna on 2008-04-27
Outstanding. That got it.

---


---
title: "Fresh Install, how-to?"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by KingTermite on 2008-05-30
Ok...I've been running Ubuntu 8.04 for about 2 or 3 weeks now. I'm happy with it and wanting to keep it. Through my learning process so far, I've installed a lot of "crap" and want to start fresh now.


1) If I delete partition and reinstall, will it screw up GRUB and my dual boot with XP?

2) Once I start fresh, is there any tool/utility that can help me keep track of what I've installed/changed since the fresh install?

3) If I upgrade at some point in time, can I just install over what's there? I want to upgrade without having to reconfigure everything the way I've tweaked it.

4) If I install two partitions with Ubuntu, how will GRUB handle that? Which menu.lst file will be the one used? I'd like one for "real" and one that is a "test playground".


Thanks in advance.

---

### Post by drs305 on 2008-05-30
> **KingTermite said:**
> 
3) If I upgrade at some point in time, can I just install over what's there? I want to upgrade without having to reconfigure everything the way I've tweaked it.


One thing you can do is to create a separate home partition when you reinstall. You will create (a minimum of) a / (root), /home and swap partition. Having a separate home partition of about 5GB will allow all of your settings to be retained if you have to reinstall the system.

---

### Post by housam on 2008-05-30
1) No.
2) add / remove programs can help 
3) yes , upgrading will keep your settings as it is
4) it will give you a grub menu to choose which system to boot.and you can always make a backup before you change any thing

---

### Post by KingTermite on 2008-05-30
> **housam said:**
> 1) No.
2) add / remove programs can help 
3) yes , upgrading will keep your settings as it is
4) it will give you a grub menu to choose which system to boot.and you can always make a backup before you change any thing

Thanks for the reply, but.....I still have questions on 2 and 4.

How will add/remove programs help me keep track. Can you be more specific? I'd like to know exactly which things *I* installed.


And on 4, I think you missed the point of the question. I know how GRUB gives you a menu, I have a dual boot now. But that menu comes from the menu.lst file.

If I installed a second Ubuntu, then each installation will have a GRUB menu.lst file, will it not? Which one is used? How do I know WHICH menu.lst file to updated if I want to tweak it?

---

### Post by indytim on 2008-05-30
> 
If I installed a second Ubuntu, then each installation will have a GRUB menu.lst file, will it not? Which one is used? How do I know WHICH menu.lst file to updated if I want to tweak it?


By default, you will be using the menu.lst from your **last** install.  The others will exist but will no longer be active.  See my sig if you want to have a stable Grub covering multiple Lxs.

IndyTim

---

### Post by KingTermite on 2008-05-30
> **indytim said:**
> By default, you will be using the menu.lst from your **last** install.  The others will exist but will no longer be active.  See my sig if you want to have a stable Grub covering multiple Lxs.

IndyTim

Thanks for the info. 

I'm also looking at your article now. :)

---


---
title: "Dual Boot Help"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by eightphases on 2008-04-24
I followed instructions I'd found elsewhere on these forums that explained how to dual boot XP with Ubuntu 7.10. It all seemed to be going perfectly: I selected "Guided - Resize" and it installed without any problems. 

But when I reset my machine, it just loaded back up into windows, instead of getting the grub boot loader. I was just wondering if anyone knows what I should try next?

---

### Post by phidia on 2008-04-24
The install may have worked but grub didn't install properly.
I'm not sure which cd image you used but one of the iso's lets you re-install grub-that's what you need to do. You can also use the [super grub disk]("http://www.supergrubdisk.org/") to boot your system

---

### Post by eightphases on 2008-04-24
I used super grub loader and tried to boot ubuntu.
I got a list to choose from something like:

Ubuntu 7.10
Ubuntu 7.10(recovery mode)
Ubuntu, memtest+86
and Windows Pro

So I chose the first one, and I get a message saying the partition doesn't exist :/ 

I think this might be related, but a while back, when I reformatted and tried to install Ubuntu fresh on this hdd (no dual boot), the installation apparently completed, but I got a message saying no OS could be found (and I know it's not the disc I'm using, because it works perfectly fine on my laptops).

---

### Post by zvacet on 2008-04-24
Is it HDD related then? Can you install any other OS on that HDD?

---


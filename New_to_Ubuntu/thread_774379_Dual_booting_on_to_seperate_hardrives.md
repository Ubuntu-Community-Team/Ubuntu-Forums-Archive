---
title: "Dual booting on to seperate hardrives"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-04-29
Can i dual boot on to seperate hardrives, 1 with ubuntu 7.10 (soon to be hardy) and windoze xp?
i would like ubuntu as the main operating system then xp as a backup till my girlfriends parents want to fully move over to ubuntu!

---

### Post by crjackson on 2008-04-29
> **ibizatunes said:**
> Can i dual boot on to seperate hardrives, 1 with ubuntu 7.10 (soon to be hardy) and windoze xp?
i would like ubuntu as the main operating system then xp as a backup till my girlfriends parents want to fully move over to ubuntu!

Yes, that's exactly what I do...

---

### Post by ibizatunes on 2008-04-29
how did you do it?

---

### Post by lemming465 on 2008-04-29
More specifically, the easiest path is

1. install xp on the first hard drive
2. install ubuntu on the second one, letting ubuntu take control of the MBR (grub boots windows easier than windows boots grub).

It's also OK if they share a hard drive, just give them separate partitions.  Ubuntu probably wants at least 2, root and swap.  The can be logical partitions; they don't have to be primary, though with 2 disks they can all be primary.

---

### Post by ibizatunes on 2008-04-29
i have xp already installed on disk 1 
and ubuntu already install on disk 2
is there anyway of doing it without reinstalling ubuntu on disk 2?
like manually editing the mbr?

---

### Post by wolfen69 on 2008-04-29
or you could unplug the xp drive before installing ubuntu and choose the quick boot option at start up to pick which drive to boot to.

EDIT:i just saw your last post and feel that re-installing would be the quickest way at this point. by the time you figure out how to edit GRUB, you could have re-installed in 20 minutes. it's not the techie-hardcore way, but it works.

---

### Post by ibizatunes on 2008-04-29
well i was going too upgrade from 7.10 to 8.04 so maybe doing a "clean" install will be a the idea i will go with!!
thanks!!

---

### Post by yamawho on 2008-04-29
I installed 8.04 on my kid's system which is running XP.

I was testing 8.04 and she saw me playing with aMSN and said it was so cool.

I installed using the entire 2nd hdd and used advanced to install Grub to the MBR of the 2nd hdd.  

I had Grub issues and was getting error 17 Cannot mount partition.

I tried to figure out what was going on but being more of a hardware guy, I started playing around with the sata cables to see if I could get it to actually boot.

I unplugged the windows hdd and restarted the system, then replugged the 2nd hdd ... same thing.

I decided to reinstall and noticed that the order of the hdd's had changed because of my tinkering. So I installed 8.04 again as above and it works  :)

I can booth directly to XP by f11 to access the boot menu.
I can access XP from grub doing a normal boot.
I can boot into ubuntu doing a normal boot.

I know my changing the order in which the system see the hdd's was the key to solving this.

In time I hope to be able to fix things by editing menu.list or fstab files. I keep trying but I still don't know what I'm doing  :lolflag:

---


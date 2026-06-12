---
title: "Remove grub without windows cd???"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Valon22 on 2008-06-08
Recently i set up to dual boot ubuntu and XP. I wanted to see if there was a way to make my sound card work and i couldn't. I went back to xp and deleted the partitions i had made for ubuntu. I restarted and i got a grub error 22 not letting me boot in to windows and not letting my partition manager put the unallocated space back to my main partition. I dont have my windows cd.

Is there anyway for me to remove grub without doing the fixboot/fixmbr throguh recovery console. Or maybe a way to modify my boot files manually?

Thanks

---

### Post by Oldsoldier2003 on 2008-06-08
> **Valon22 said:**
> Recently i set up to dual boot ubuntu and XP. I wanted to see if there was a way to make my sound card work and i couldn't. I went back to xp and deleted the partitions i had made for ubuntu. I restarted and i got a grub error 22 not letting me boot in to windows and not letting my partition manager put the unallocated space back to my main partition. I dont have my windows cd.

Is there anyway for me to remove grub without doing the fixboot/fixmbr throguh recovery console. Or maybe a way to modify my boot files manually?

Thanks

you can use the super grub live cd to do this or the Ubuntu live cd. If you opt to use the ubuntu live cd install the ms-sys package from Debian. I recommend using the super grub cd, its a lot easier.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by housam on 2008-06-08
try to use the [[COLOR="Red"]_super grub disk_[/COLOR]]("http://www.supergrubdisk.org/index.php?pid=12") , it can help booting windows

---

### Post by shailendra on 2008-06-08
Hi,

When Ubuntu is installed it also updates the MBR of Windows so that it can support dual boot. Since, you have deleted Ubuntu, the MBR is no more able to locate Ubuntu. The Windows MBR is now not good. You will have to fix the Windows MBR.

You can either use "FixMBR" or "ms-sys".

For "ms-sys" please read the "HOW TO" at the following link, which I had written for a similar issue;
"http://ph.ubuntuforums.com/showthread.php?p=5143390#post5143390"

Hope it works for you.

---


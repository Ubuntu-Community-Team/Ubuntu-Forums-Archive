---
title: "Uninstalling ubuntu"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by bigdawgdesigns on 2008-08-20
Hey everybody
I was wondering if anyone know how to uninstall UBUNTU in a dual boot machine.
I am going to make some videos on how to install Ubuntu onto a computer but i want to do it with a computer with only windows and nothing else.
All help is appreciated

---

### Post by iaculallad on 2008-08-20
> **bigdawgdesigns said:**
> Hey everybody
I was wondering if anyone know how to uninstall UBUNTU in a dual boot machine.
I am going to make some videos on how to install Ubuntu onto a computer but i want to do it with a computer with only windows and nothing else.
All help is appreciated

Boot from your LiveCD and use it's GParted utility to delete and format the partitions used by your Ubuntu OS. You might need to restore your windoze boot record afterward.

---

### Post by bigdawgdesigns on 2008-08-20
how would i restore my windows boot record

---

### Post by kspncr on 2008-08-20
You boot from the windows disc and use the recovery tools, then use the command "fixmbr"

If you bought your computer with windows preinstalls and don't have the disc, the super grub disc will work too [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) just navigate "fix boot of windows"

---


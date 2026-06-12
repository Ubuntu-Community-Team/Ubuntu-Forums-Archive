---
title: "Installation issues--help please!"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by superspork7 on 2008-10-17
ok, i've got two HDD: an 80G slaved to a 5G.  the 5 has Ubuntu, and i recently wiped the 80.  I'm trying to install winXP on the 80 through Ubuntu using Wine.  it seems that the winXP install process is failing to initialize.  any suggestions?

---

### Post by AndyCooll on 2008-10-17
You can't install WinXP using Wine. Wine runs Windows _apps_ not windows itself.

To install WinXP you essentially have two choices. You can dual-boot (see link in my signature) or you can virtualise. For the latter you'd need to install something like VirtualBox or VMware. There are plenty of threads on these boards regarding running XP under Virtualbox for instance (just do a search for Virtualbox and XP).

In fact there's a whole forum on the subject: [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308")

:cool:

---

### Post by penguin17 on 2008-10-17
I'd just switch to boot from cd in your bios and then pick the 80gb hard drive when prompted to.

---

### Post by superspork7 on 2008-10-17
thanks for the quick replies!  is there any way to start a winxp install from ubuntu to a slaved drive?

---

### Post by LowSky on 2008-10-17
> **superspork7 said:**
> thanks for the quick replies!  is there any way to start a winxp install from ubuntu to a slaved drive?

Yeah like AndyCooll said, use VMware, otherwise install it from startup, but then you will need to fix the grub menu

---

### Post by jbrevik on 2008-10-17
If you want to use ubuntu as your daily driver, you could use virtubox to install windows xp.

---


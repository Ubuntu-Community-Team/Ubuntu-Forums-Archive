---
title: "Uninstall Ubuntu, RePartition,Install XP"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Takido on 2008-09-26
I am a new college student, and i have this old laptop which i had installed ubuntu on. I seem to have a problem considering the fact that when i reinstalled windows, it gets to the grub menu and will not finish the installation for XP. Basically i want to re partition my drive to the way it was (two 25gb sizes) and just have XP installed. Is there anyway i can do this from ubuntu, because windows will no longer work. Or simpler still, can i turn off grub?

-Thanks

---

### Post by Tatty on 2008-09-26
If it will not boot from your windows install CD then it is probably because your CD drive comes after your hard drive in the boot order.

The easiest way to do what you want to do is with gparted.  Just boot a ubuntu liveCD and then go to System->Adminsitration->Partition Editor.

From here you can simply delete your ubuntu install and then partition your drives however you want.

---


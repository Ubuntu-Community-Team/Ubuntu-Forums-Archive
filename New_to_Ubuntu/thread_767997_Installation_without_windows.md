---
title: "Installation without windows"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by nirakarsethy on 2008-04-26
How can I have only Ubuntu on my machine ? no windows dual partition

---

### Post by frup on 2008-04-26
Do you mean how can you manage or how is it actually possible?

If you want just Ubuntu (as plenty of have and everyone should :P) Just pop in the live CD, click install and take over the entire drive.

If you mean how can you manage, Virtual Machines, Wine and checking carefully for alternatives all help.

---

### Post by ad_267 on 2008-04-26
What set up do you have at the moment? Do you have a dual boot and you want to remove windows? Or do you want to do a clean install?

If you are doing a new install you can just tell the installer to use an entire hard drive or use the manual option to set up your partitions.

If you are currently dual booting you can use the live cd to use gparted and delete your windows partition then resize your ubuntu partition. You can remove windows from your grub boot menu by editing /boot/grub/menu.lst

---

### Post by Dr.Gringo on 2008-04-26
If I'm not mistaken i believed you used wubi in this case just burn the iso to a cd and install; take the entire drive to eliminate windows.

---


---
title: "Newly built kernel not showing up in GRUB"
date: 2014-01-23
forum: Packaging and Compiling Programs
---

### Post by madhusudhan2 on 2014-01-23
Hi,

I have built a new kernel and ran update grub to include the newly built kernel into the grub. After this, I could see the change in /boot/grub/grub.cfg and in other locations. But, strangely, the GRUB that gets displayed during the boot time, does not show the newly built kernel. As a result, I am unable to boot this new kernel. 

Any idea, as to what exactly is the reason?


-Madhu

---

### Post by kajoky on 2014-01-27
Are you using multiple operating systems?  I have two linux operating systems and thus two /boot/grub/grub.cfg each on a different partition.  If this is the case, you can use grub-install to use the desired grub.cfg.

---


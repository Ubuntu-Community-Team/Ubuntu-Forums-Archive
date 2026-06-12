---
title: "Dual Boot with an existing install"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by Tim_OHagan on 2013-09-10
Hi

I have installed Ubuntu on my parents machine on a new SSD.  They now want access to certain windows software and i want set up to dual boot.   When I installed Ubuntu I left the existing XP install, which is on the original hdd in the machine but, without a sata cable connecting it to the mother board so, as far as Ubuntu knew when it was installed there was no other operating system.  This means that Grub does not offer the option to boot the XP drive now that i have connected it back to the motherboard.

Is there a quick fix for this by sorting grub out or is a fresh Ubuntu install a better bet?

Thanks in advance for any help.

Regards

Chris

---

### Post by westie457 on 2013-09-10
> **Tim_OHagan said:**
> Hi

I have installed Ubuntu on my parents machine on a new SSD.  They now want access to certain windows software and i want set up to dual boot.   When I installed Ubuntu I left the existing XP install, which is on the original hdd in the machine but, without a sata cable connecting it to the mother board so, as far as Ubuntu knew when it was installed there was no other operating system.  This means that Grub does not offer the option to boot the XP drive now that i have connected it back to the motherboard.

Is there a quick fix for this by sorting grub out or is a fresh Ubuntu install a better bet?

Thanks in advance for any help.

Regards

Chris


Welcome to UF.

Open a terminal (pressing Ctrl+Alt+T at the same time) and run ```
sudo update-grub
``` should fix it.

If that does not then there is always Boot Repair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Tim_OHagan on 2013-09-10
Sir you are a gent.  Many thanks indeed it worked a treat :D

Regards

Chris

---

### Post by newb85 on 2013-09-10
Please mark the thread as solved by clicking "Thread Tools" above ^^

---


---
title: "Is it possible to insert compile module after compiled &quot;make&quot; without installing"
date: 2012-07-26
forum: Programming Talk
---

### Post by jao_madn on 2012-07-26
Hi gud day,

I would like to ask if possible to load the driver i compiled module without installing it in the ubuntu-kernel-distro/updates* or simple not executing "make install". what i mean is i compile the compat wireless driver using make and i want to try to load 
on the system without installing "make install"

Is it possible, thanks in advance for the possible answer.

---

### Post by Bachstelze on 2012-07-26
Yes, see [font=monospace]man insmod[/font]. You still need to be root.

---


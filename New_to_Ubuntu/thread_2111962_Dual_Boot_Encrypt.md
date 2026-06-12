---
title: "Dual Boot Encrypt"
date: 2013-02-03
forum: New to Ubuntu
---

### Post by Dyronne on 2013-02-03
how do you encrypt a dual boot system with windows 8 that on start up allows you to select os through grub menu????(is the grub menu the purple window menu????)

---

### Post by Mark Phelps on 2013-02-03
Dual-boot can mean two VERY different things:
1) Ubuntu installed from INSIDE Windows, using Wubi, such that the Windows loader puts up an OS selection screen
2) Ubuntu installed from OUTSIDE Windows, from a CD/CDVD/USB such that GRUB puts up a selection screen.

IF you installed using WUBI and encrypt Win8, I'm pretty sure that will prevent access to Ubuntu -- since it is a virtual filesystem inside the Windows partition.

But ... since my personal perspective is that encryption is largely a waste of time that only causes trouble in the long run ... I'm probably not the best person to provide advice.

---


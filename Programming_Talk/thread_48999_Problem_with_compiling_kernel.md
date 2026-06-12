---
title: "Problem with compiling kernel"
date: 2005-07-14
forum: Programming Talk
---

### Post by satishc on 2005-07-14
Hi,

I recompiled the kernel with original configuration and tried booting it. But, I got the following error.

modprobe: FATAL: Could not load /lib/modules/2.6.12/modules.dep

I built ext3 into the kernel and not a module. But, the problem still exists.

Does anyone know why this problem is happening?

Thank you,

-Satish

---

### Post by ubuntp on 2005-07-14
Did you *make modules modules_install*?

---


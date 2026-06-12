---
title: "GRUB won't load straight from BIOS"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by powerpleb on 2008-06-11
I have a problem with GRUB. It won't load straight from the BIOS, but it will load if I put a live CD in a select Boot from Hard Disk.

I've fiddled with BIOS boot order.

I have run this...
```
sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,3)
grub> setup (hd0)
grub> quit
```

Then rebooted. Problem is still there.

Does anyone know what's going on?

---

### Post by sdennie on 2008-06-11
Is the partition that grub is on have the boot flag set?

---

### Post by powerpleb on 2008-06-12
> **vor said:**
> Is the partition that grub is on have the boot flag set?

Nope.
Thanks, that was the problem.

---


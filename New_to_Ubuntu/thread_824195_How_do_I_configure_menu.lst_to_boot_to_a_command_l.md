---
title: "How do I configure menu.lst to boot to a command line"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by william_lee on 2008-06-09
I'm looking to set up a grub menu item to boot directly to a command line (NOT recovery) in Ubuntu.

I don't want to remove GDM to do so.

Does anyone know how to set up menu.lst to accomplish this?

I want to boot directly to a command line similar to the server version of Ubuntu.  I currently have Gnome installed.

Thanks.

---

### Post by Oldsoldier2003 on 2008-06-09
> **william_lee said:**
> I'm looking to set up a grub menu item to boot directly to a command line (NOT recovery) in Ubuntu.

I don't want to remove GDM to do so.

Does anyone know how to set up menu.lst to accomplish this?

I want to boot directly to a command line similar to the server version of Ubuntu.  I currently have Gnome installed.

Thanks.
try adding these boot options to your kernel line.
```
textonly quiet
```

---


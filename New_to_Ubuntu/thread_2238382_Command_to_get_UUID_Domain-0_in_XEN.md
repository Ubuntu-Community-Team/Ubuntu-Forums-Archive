---
title: "Command to get UUID Domain-0 in XEN"
date: 2014-08-07
forum: New to Ubuntu
---

### Post by Veerabhadra_Kota on 2014-08-07
Hi,

Is there any command to get the UUID of Domain-0 in Xen?

Thanks,
Veerabhadra

---

### Post by TheFu on 2014-08-07
If you want the partition UUID, **blkid** is the command.  I don't know of any other UUID for a Linux system, KVM or Xen.
In what context is this UUID needed? It will help me learn.

---


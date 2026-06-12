---
title: "/boot partition almost full"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by kenweill on 2008-07-18
my /boot partition is almost full.
how do i safely remove the old kernels installed?

---

### Post by sharks on 2008-07-18
go to synaptic and type linux-headers and see and carefully remove it.

---

### Post by kenweill on 2008-07-18
How about the older linux-image-2.6.*, do i have to remove them as well?
or only the header files...

---

### Post by Bachstelze on 2008-07-18
> **kenweill said:**
> How about the older linux-image-2.6.*, do i have to remove them as well?

Yes, those are the ones you need to remove. The headers install into /usr, not /boot (though of course, you can remove them as well).

---


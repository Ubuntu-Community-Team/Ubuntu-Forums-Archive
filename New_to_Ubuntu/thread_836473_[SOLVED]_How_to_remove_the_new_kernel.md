---
title: "[SOLVED] How to remove the new kernel"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by amyst on 2008-06-21
I installed 2.6.22-15 linux kernel on my laptop. I want to remove it because my wireless does not work. The new kernel exists side-by-side with 2.6.22-14 kernel.

Is it safe to remove linux-image-2.6.22-15-generic, as well as 2.6.22-15 modules in Synaptics? This is my productivity machine so I really really don't want to change too many important settings. 

Thanks!

---

### Post by Joeb454 on 2008-06-21
I've removed kernels in synaptic before, and it didn't do any harm, though they were the older versions of the kernel :)

And 2.6.22 isn't that new ;)

---

### Post by PmDematagoda on 2008-06-21
By rights there shouldn't be any problem, just be careful not to remove the old kernel:).

---

### Post by amyst on 2008-06-21
Thanks everyone! I'm removing it with my breath held :)

---

### Post by fidamehran on 2008-07-06
> **amyst said:**
> Thanks everyone! I'm removing it with my breath held :)
And......
The result?

---

### Post by Locutus_of_Borg on 2008-07-06
lets hope he edited /boot/grub/menu.list to point to an existing kernel first...

---


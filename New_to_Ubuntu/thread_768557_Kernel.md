---
title: "Kernel"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by reyhan on 2008-04-26
hello i just finished upgrade my Ubuntu to Hardy 
but when i look the Grub boot list why the 2.6.22-14-generic is
still there? 
Do i need to remove it?

---

### Post by elmer_42 on 2008-04-26
I am also wondering about this. Why is it there? Did GRUB just "forget" to delete the entry?

---

### Post by Theo148 on 2008-04-26
Well for me running

```
sudo update-grub
```

solved the problem, although I'm not sure if that's really a proper fix in all cases.

---

### Post by SOULRiDER on 2008-04-26
Ubuntu does not remove old kernels, its always good to have an older kernel just in case the new one has any issues. If you want, you can use Synaptic to remove the older one, it will also be removed from grub. The package should be called either linux-image-<version> or kernel-image-<version> I cant remember which of the two.

---

### Post by reyhan on 2008-04-26
if i remove it can it damage my 
System?

---

### Post by SOULRiDER on 2008-04-26
No, dont worrry about that, it should happen, just make sure you dont remove all kernels, just the older one(s)

---

### Post by reyhan on 2008-04-26
Okay Thanks!!!

---


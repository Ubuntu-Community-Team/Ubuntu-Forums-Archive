---
title: "[SOLVED] Kernel upgrade did not load to menu.lst file"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-05-26
I just did an upgrade to the new 17-generic kernel and when I rebooted it only gave me the choice to us the 16-generic kernel.  How do I go about adding the 17-generic kernel to menu.lst....

---

### Post by zvacet on 2008-05-26
```
sudo update-grub
```

Question is how many kernels do you have installed?Go to the synaptic and type linux-image in search box.You will see all kernels and you can delete ones with lower number and leave just two Hardy kernels.

---


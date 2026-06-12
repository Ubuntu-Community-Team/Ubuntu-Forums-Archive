---
title: "Ecrypt/Private Volume"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Glurf on 2008-10-22
I installed Ecrypt not too long ago, and it mounted a volume "Private". I have no need for Ecrypt, so I removed it, however the mounted volume remains. When I select "Unmount" from the menu, it says "umount: /home/tyler/Private is not in the fstab (and you are not root)". So, I turn to the terminal, and use "sudo umount Private", but it can't find the volume. I don't know exactly what directory it's mounted under, so terminal doesn't seem like a viable option. Does anyone know how to fix this problem?

Btw, I'm using the Intrepid Ibex beta if that changes anything, shouldn't though.

---

### Post by hyper_ch on 2008-10-22
run
```

df -l

```

---


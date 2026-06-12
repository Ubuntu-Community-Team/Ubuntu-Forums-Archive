---
title: "Kernel upgrade won't update grub configuration"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Anakunda on 2012-03-28
Hello I upgraded kernel to 3.0.0-17 and grub boot config won't update so that Ubuntu still boots to 3.0.0-16, how do I involve bootfile update to correspond to current kernel?

---

### Post by garvinrick4 on 2012-03-28
Do you have more than one install? Remember the partition or OS that grub is in sda looks for grub files in that partition or operating system. Any which way always.
```
sudo update-grub
```

To make sure grub has new kernel updated.

You can use:
```
sudo grub-mkconfig
```

And can watch all the kernels update if you want to see them.

---

### Post by Anakunda on 2012-03-28
Thank you

---


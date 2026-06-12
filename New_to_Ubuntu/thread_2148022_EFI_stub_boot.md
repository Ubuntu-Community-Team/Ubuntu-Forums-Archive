---
title: "EFI stub boot"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by Kopkins on 2013-05-23
I'm trying to boot with EFI stub but it hangs halfway through boot each time. If I boot with irqpoll it hangs at about 15seconds when "Disabling IRQ #17" but discovers some additional hardware before hanging. If I boot without irqpoll it hangs at about 5seconds with "Disabling IRQ #17" I have the itnitrd-ubuntu.img and the vmlinuz-ubuntu.img in an ubuntu folder on my efi partition "/boot/efi/EFI/ubuntu/"

Does anoyone boot from EFI stub? I'm using refind.

Thanks,

Kopkins

---

### Post by Kopkins on 2013-05-26
Do I have to recompile the kernel?

---


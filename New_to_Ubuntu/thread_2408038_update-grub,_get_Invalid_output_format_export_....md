---
title: "update-grub, get Invalid output format export ..."
date: 2018-12-12
forum: New to Ubuntu
---

### Post by cwmoser on 2018-12-12
My kernel is stuck on 4.15.0-38
Under /boot have a new 4.15.0-42 but it does not appear in Grub.

Any ideas on how to fix this?

Thanks

-- Carl


When I run update-grub I get errors:
[B]$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-42-generic
Found initrd image: /boot/initrd.img-4.15.0-42-generic
Found linux image: /boot/vmlinuz-4.15.0-38-generic
Found initrd image: /boot/initrd.img-4.15.0-38-generic
Invalid output format export. Choose from value,
device, list, or full
Invalid output format export. Choose from value,
device, list, or full
Invalid output format export. Choose from value,
device, list, or full
Invalid output format export. Choose from value,
device, list, or full
Invalid output format export. Choose from value,
device, list, or full[/B]

---


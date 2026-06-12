---
title: "Alternate CD Won't Boot On Old Laptop"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by tdrusk on 2008-05-04
I have a very old laptop. I have used the CD to install on my new laptop, so that's not the problem.

Every time I try to boot I get the error
```
[    0.000000 ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
```

The thing is, at the end of the boot line I added
```
boot: /boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash acpi=off
```
The above line is purely an example that I copied off a guide, but as you can see, I just put a space then typed acpi=off.

Did I do something wrong? What do I need to do? Is there a way to tell what boot parameters your system needs?

---

### Post by alienexplorers on 2008-05-24
It should read:
> acpi=force
this allows the computer to shutdown when you click the shutdown button.  My computer is also an old work horse and I have to add the same line due to the fact my system bios is too old.

---


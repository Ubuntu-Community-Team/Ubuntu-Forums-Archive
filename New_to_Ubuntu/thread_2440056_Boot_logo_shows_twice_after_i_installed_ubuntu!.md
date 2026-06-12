---
title: "Boot logo shows twice after i installed ubuntu!"
date: 2020-04-05
forum: New to Ubuntu
---

### Post by arditprenga on 2020-04-05
Hi, after i installed ubuntu the logo shows twice before starting, anyone has information on this?

---

### Post by CelticWarrior on 2020-04-05
It's not any boot logo, it's the Lenovo splash screen and before there there's an error message about PXE boot (network boot). We know that because of your video: [https://www.dropbox.com/s/xd7qxeo8co6gt11/20200405_113833.mp4?dl=0](https://www.dropbox.com/s/xd7qxeo8co6gt11/20200405_113833.mp4?dl=0)

Open UEFI settings and check the boot order, boot options. Namely:


[LIST=1]
[*]disable PXE/network boot 
[*]In the drives priority setting make sure the first priority is given to the drive that contains the ESP (EFI Sustem Partition) 
[*](OPTIONAL) Disable Secure Boot. 
[/LIST]

---

### Post by arditprenga on 2020-04-05
- Disabled PXE and it doesnt show anymore.
- Disabled secure boot
- The EFI is first in order.

Still the lenovo logo shows twice.
Maybe did i do smth wrong during installation, swap, boot  partitions

---

### Post by CelticWarrior on 2020-04-05
> **arditprenga said:**
> Still the lenovo logo shows twice.

That's how it is then. An UEFI update may or may not change that behavior. Anyway, not a problem, it's how your Lenovo works. And it's just a splash screen. Avoiding the first PXE related error also was only to make it boot a fraction of a second faster.

> Maybe did i do smth wrong during installation, swap, boot  partitions

Maybe you did, maybe not, but in any case it has nothing to do with it. The boot process is like this:

UEFI does POST > reads the EFI partition > releases control to the OS selected to boot (only at this point the OS is involved).

In older systems the process is similar but instead of UEFI you would had BIOS and instead of reading the EFI partition it would read the MBR of the drive selected as bootable.

---

### Post by arditprenga on 2020-04-05
thanks for information

---


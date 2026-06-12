---
title: "how create the /boot and /boot/efi partition for centos and ubuntu on one system"
date: 2019-01-02
forum: New to Ubuntu
---

### Post by nks12layer on 2019-01-02
Hi,

I am trying to install ubuntu and Centos on my pc but i can't mount the same /boot partition and /boot/efi partition when installing the CentOS and Ubuntu.

It is possible to create the /boot and /boot/efi partition outside the /root partition when installing the Ubuntu.

Please provide the solution.

Thanks & Regards,
Nikhil

---

### Post by SeijiSensei on 2019-01-02
If you select the manual option during the disk partitioning step, you can create a separate boot partition.  I usually create a 512 MB partition formatted as ext2 these days as kernels and their associated files have gotten larger in size.

---

### Post by Dennis N on 2019-01-02
If installing in a computer using UEFI, they can both use the same EFI system partition, mounted at /boot/efi. Each OS has it's own grub files that it installs to a separate folder on that EFI system partition. You don't need a separate boot partition for these distros unless you intend to encrypt an OS.

---

### Post by oldfred on 2019-01-02
I prefer to use gparted but only slightly easier than creating partitions during install.
You can share an ESP - efi system partition with many installs. But if using /boot, it must be unique to every install. Better to not have /boot as Dennis N suggests.

Lots of detailed info & many links to more info in link in my signature for UEFI installs.

---


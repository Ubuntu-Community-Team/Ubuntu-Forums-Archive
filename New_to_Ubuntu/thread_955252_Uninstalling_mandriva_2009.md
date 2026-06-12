---
title: "Uninstalling mandriva 2009"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by ModdTaco on 2008-10-22
Hey does anyone know how to remove Mandriva 2009 so I can put Kubuntu 8.10 in its spot. I have Vista currently installed also and would hate to have to reinstall it again....

---

### Post by Hexagoon on 2008-10-22
Just choose to use and format the mandriva partitions when you install Kubuntu. Remember that 8.10 still is in beta state and may fail, possibly resulting in data loss. Backup before you begin :)

---

### Post by ModdTaco on 2008-10-22
Thanks for the prompt response. I was going to wait a few days until 8.10 was out of beta. Would doing what you suggested mess up my ability to boot properly into windows?

---

### Post by Hexagoon on 2008-10-22
I dont se any reason it would mess up the ability to boot up windows? If you only use the partitions used by mandriva today for the ubuntu installation, you cant destroy the win partition.

The problem that may appear is that grub(the bootloader) doesn't automatically add you windows installation to the boot menu. But that can be fixed post-install, no need to worry :)

Edit: Be sure to check the partitioning settings in the installer so that you not delete the win partition, i think there is an option like "Use all **_Linux partitions_** blablabla".

---


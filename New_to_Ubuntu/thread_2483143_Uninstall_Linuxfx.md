---
title: "Uninstall Linuxfx"
date: 2023-01-21
forum: New to Ubuntu
---

### Post by stevieonlinux on 2023-01-21
Hello


I have Linuxfx running on a partition of an SDD drive but I would like to replace it with Ubuntu and KDE plasma. (I have windows 10 running on a different partition of the SSD so I don't want to simply delete the partition where I have Linuxfx because I would lose my MBR for Windows 10.) How can I best proceed? Thanks if you have time to answer.


Stevie

---

### Post by Impavidus on 2023-01-21
Deleting partitions should be no issue as long as you don't touch the Windows partitions or the EFI partition. That's assuing you run in UEFI mode. For the rare cases of Windows 10 in legacy/bios mode (which would make dual booting fragile), the MBR will always be overwritten when installing Ubuntu on the same drive.

But there's no need to delete any partitions. Start the installer, for partitioning use manual partitioning/something else and reuse the existing partition. Tell the installer to format it.

---

### Post by grahammechanical on 2023-01-22
> I would like to replace it with Ubuntu and KDE plasma.

There is an official flavour of Ubuntu that comes with KDE Plasma by default. It is called Kubuntu.

[https://kubuntu.org/news/kubuntu-22-04-lts-released/](https://kubuntu.org/news/kubuntu-22-04-lts-released/)

Kubuntu 22.04.1 is supported up to April 2025. At which time you can upgrade to Kubuntu 24.04 LTS. Other release of Ubuntu/Kubuntu have a shorter support life and require more frequent upgrades to newer versions.

[https://kubuntu.org/getkubuntu/](https://kubuntu.org/getkubuntu/)

Regards

---


---
title: "HP laptop will not boot after Ubuntu installed only if flash drive is left in"
date: 2024-02-10
forum: New to Ubuntu
---

### Post by meping12 on 2024-02-10
It will try and boot but get a "non system disc" message

---

### Post by MAFoElffen on 2024-02-10
It's a fresh install right?

Reinstall it choosing erase. But insure when it displays what it is going to do with partitions and such, that it chooses to install (Grub boot) EFI partition to the disk you are installing to, not to your USB flash drive... If it is saying to the Flash drive then just stop and post back without installing.

But first, post which installer release version and flavor.

---

### Post by oldfred on 2024-02-13
Many with HP have reported that they have to go into HP's UEFI settings and change boot order there.

Screenshot of HP's UEFI settings change of boot order
[https://ubuntuforums.org/showthread.php?t=2490924&page=2](https://ubuntuforums.org/showthread.php?t=2490924&page=2)
[https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6](https://www.phoronix.com/news/HP-BIOSCFG-For-Linux-6.6)
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

---


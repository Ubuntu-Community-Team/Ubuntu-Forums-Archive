---
title: "Ubuntu Linux 19.0.4 Not able to Boot"
date: 2020-01-28
forum: New to Ubuntu
---

### Post by techub-2020 on 2020-01-28
Hp Pavilion All-in-one Desktop having Windows 10 Pre-Loaded not able to dual boot Ubuntu Desktop 64 bit 19.0.4 , not able to see the Hard Disk Partitions made in Windows . Can u suggest what to do next

---

### Post by Impavidus on 2020-01-28
First of all, Ubuntu 19.04 reached end of life last week, so don't install it. I suggest you use 19.10 instead. The release numbers are year and month of release, so the first number is as relevant as the second. You can also take the latest long term support (LTS) release, which is 18.04 and has longer support, but if you intend to upgrade to 20.04 soon after release there's no point in that.

But that won't solve you problem, although it will prevent other prblems.

Ubuntu has te be installed in a type of Linux partition, usually an ext4 partition. Windows doesn't know about Linux partitions, so you cannot install Ubuntu in any partition that Windows can make. If you just leave unallocated space on your hard drive, the Ubuntu installer will create partitions and format it for you.

Also make sure you disable FastStartup on Windows. With FastStartup enabled Ubuntu cannot see the Windows system. And have a read here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---


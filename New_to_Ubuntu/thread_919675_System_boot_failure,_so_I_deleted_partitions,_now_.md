---
title: "System boot failure, so I deleted partitions, now error 22?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Pascal11110 on 2008-09-14
I had a system boot failure on an IDE hard drive that Iw as using solely for Ubuntu, and I really need the computer up and running again,(I also tried booting from the disk and reinstalling, but it always got stuck at the partitioning thing) so I attached it to my laptop through an enclosure, and deleted the partitions. Then I hooked the hard drive back up to my computer and had the ubuntu live disk in. Now it just says error 22? WHat should I do?

---

### Post by 1/0 on 2008-09-14
Sounds like Grub can't find your kernel. I would reinstall grub and check my settings. To reinstall boot from a livecd. Open a terminal and enter the following:

```
sudo grub
```
```
find /boot/grub/stage1
```

Use this info (the hdX,Y) to install. If hd0,1 do this (otherwise adjust your numbers to what you got):
```
root (hd0,1)
```
```
setup (hd0)
```
```
quit
```

Then edit the grub settings:

```
gksu gedit /boot/grub/menu.lst
```

Set proper settings. You'll find lots of info from this command:

```
fdisk -l
```

You should have something like this:

```
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd1,1)
kernel          /vmlinuz-2.6.24-19-generic root=UUID=1234567890...
initrd          /initrd.img-2.6.24-19-generic
quiet
```

---


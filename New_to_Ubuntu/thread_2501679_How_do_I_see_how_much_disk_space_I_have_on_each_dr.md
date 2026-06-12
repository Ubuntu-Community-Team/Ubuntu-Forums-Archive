---
title: "How do I see how much disk space I have on each drive?"
date: 2024-10-17
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-17
[COLOR=#000000]How do I see how much disk space I have on each drive?  New to ubuntu.[/COLOR]

---

### Post by Rubi1200 on 2024-10-17
Easiest way is to open a terminal with Ctrl+Alt+T or search from the menu for Terminal and use this command:

```
df -hT
```

---

### Post by shadowtabby on 2024-10-17
Which is which?
[COLOR=#000000][INDENT]
Filesystem     Type      Size  Used Avail Use% Mounted on
tmpfs          tmpfs     3.2G  3.0M  3.2G   1% /run
/dev/sda2      ext4      218G   35G  173G  17% /
tmpfs          tmpfs      16G  152M   16G   1% /dev/shm
tmpfs          tmpfs     5.0M   16K  5.0M   1% /run/lock
efivarfs       efivarfs  256K   75K  177K  30% /sys/firmware/efi/efivars
/dev/sda1      vfat      1.1G  6.2M  1.1G   1% /boot/efi
tmpfs          tmpfs     3.2G   11M  3.2G   1% /run/user/1000


And my 2nd SSD?

[/INDENT]
[/COLOR]

---

### Post by ActionParsnip on 2024-10-17
That is only showing sda which is the first disk in the system. What is the output of:
```

sudo parted -l

```

---

### Post by shadowtabby on 2024-10-17
Thank you for you reply.  Amazing thank you so much.

---


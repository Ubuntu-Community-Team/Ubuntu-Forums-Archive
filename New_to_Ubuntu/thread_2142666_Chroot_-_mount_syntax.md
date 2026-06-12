---
title: "Chroot - mount syntax"
date: 2013-05-06
forum: New to Ubuntu
---

### Post by Patty X on 2013-05-06
What is the correct syntax for mount command in chroot scenario? I saw several:

```
mount -t proc none /mnt/xxx/proc
mount -t proc proc /mnt/xxx/proc
mount -o bind /proc /mnt/xxx/proc

``````

mount -o bind /dev /mnt/xxx/dev
mount --rbind /dev /mnt/xxx/dev
```
Is mounting /sys also necessary? Some people mount it while others not.

---

### Post by matt_symes on 2013-05-06
Hi

> **Patty X said:**
> What is the correct syntax for mount command in chroot scenario? I saw several:

```
mount -t proc none /mnt/xxx/proc
mount -t proc proc /mnt/xxx/proc
mount -o bind /proc /mnt/xxx/proc

``````

mount -o bind /dev /mnt/xxx/dev
mount --rbind /dev /mnt/xxx/dev
```

I am currently running, and have booted into, Arch Linux. I have a chroot into my Xubuntu install so i can offer help on the forums.

Chrooting into Xubuntu i used this syntax

[https://wiki.archlinux.org/index.php/Change_Root](https://wiki.archlinux.org/index.php/Change_Root)

However in the past i have also use this syntax
```

mount -o bind /proc /mnt_point/proc
mount -o bind /dev /mnt_point/dev
mount -o bind /sys /mnt_point/sys
```

So both should work.

> Is mounting /sys also necessary? Some people mount it while others not.

If you want to run commands like *lspci* then you will need sysfs mounted, otherwise not.

Kind regards

---


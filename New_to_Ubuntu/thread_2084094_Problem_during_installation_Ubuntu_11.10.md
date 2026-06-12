---
title: "Problem during installation Ubuntu 11.10"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by mancubas on 2012-11-14
The installation of Ubuntu 11.10 64bit completes correctly, when it reboots I am indefinatley stuck at a purple screen with no error message no nothing :( . I have tried the following without success:-

1. nomodeset when installer starts
2. unplugged the additonal 1tb disk
3. Setting SATA controller to IDE
4. ctrl+alt F1 (diff tty)

My setup is Asus P9X79, 3970k, 120Gb SSD & 16GB RAM

Any suggestions on where I am going wrong?

Oh I have to stick with 11.10 for various reasons I wont go into here.

Hope someone can help.

Thanks,
ManC

---

### Post by mancubas on 2012-11-14
My solution all be it uncomplete at this point and if it helps anyone else at any point was

Press ESC to interupt the bootloader and endup in the GRUB menu config, I replaced 'quiet splash vt.handoff=7' with "nomodeset, Pressed CTRL+x to save and exit I assume & the subsequent boot dropped me in the GUI.

I am going to be working on making this change permanent now, wish me luck :)

ManC

---

### Post by sandyd on 2012-11-14
try this
```

sudo nano /etc/default/grub
```
change
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```

Press control+x to save, and run
```

sudo update-grub
```
to update the grub bootloader

---

### Post by mancubas on 2012-11-14
Seems straight forward enough, will give it a go tomorrow and let you know if it works. 

Thx,
ManC

---

### Post by mancubas on 2012-11-15
> **sandyd said:**
> try this
```

sudo nano /etc/default/grub
```change
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```to
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```Press control+x to save, and run
```

sudo update-grub
```to update the grub bootloader

Those instructions worked a treat, thanks!

I wonder why choosing 'nomodeset' during the installation process didnt aid this problem? maybe it only influences the installation instance of Ubuntu and is lost when it completes...

---


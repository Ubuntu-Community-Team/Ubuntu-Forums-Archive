---
title: "Managing grub and multiple menu.lst files?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by bhold on 2008-05-26
I have 3 root (/) partitions for tri-booting Ubuntu, Debian, or Fedora. Each partition has its own /boot directory and menu.lst file. Several questions:
1. How does grub select which is the "real" menu.lst file?
2. How can I change which partition grub uses to get menu.lst?

Seems like every time I install a new distro, it takes over grub and that becomes the "real" menu.lst. At which point I use vi to merge the current information from all menu.lst files. There must be a better way, I would like to maintain only one menu.lst to control grub. Should I assign /boot its own unique partition?

---

### Post by bwhite82 on 2008-05-26
The grub command can accomplish this. Read up on the man page for the options.

---


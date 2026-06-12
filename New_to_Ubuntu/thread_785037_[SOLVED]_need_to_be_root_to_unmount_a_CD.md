---
title: "[SOLVED] need to be root to unmount a CD?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-07
Hardy Heron is telling me that I need to be root to unmount a DVD I just put into the computer.  It's also not letting me access my data ext2 filesystem.  Is there a way to change the permissions on those so that I can take the damn DVD out of the drive?

---

### Post by TeoBigusGeekus on 2008-05-07
Type 
```
sudo fdisk -l
```
to learn the names of your devices.

If the dvd is /dev/cdrom0 for example, then change its owner with
```
sudo chown -R yourusername /dev/cdrom0
```

---

### Post by imangh on 2008-05-07
Hello
Sudo is useful for Terminal commands, is there any way for running Items in menu as root?

---

### Post by kpkeerthi on 2008-05-07
> **imangh said:**
> Hello
Sudo is useful for Terminal commands, is there any way for running Items in menu as root?
For graphical applications, use
```
gksudo /command/to/run
```

---


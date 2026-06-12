---
title: "Daemon which mounts the Linux file system at start-up"
date: 2015-03-26
forum: New to Ubuntu
---

### Post by sylwek on 2015-03-26
Hi everyone.
As in the title, I need to find which daemon mounts Linux file system at start up.
Is it init?

Many thanks

---

### Post by dino99 on 2015-03-26
vivid have switched (recently) to 'systemd' but 'upstart' is still available if the user prefer to use it (one conflict with the other, so no drama)

---

### Post by SeijiSensei on 2015-03-26
I believe it happens via grub.  For instance, in /boot/grub/grub.cfg, I have:
```
linux   /boot/vmlinuz-3.16.0-33-generic root=UUID=d5b782fb-49d1-438c-b1e4-e521b571ef69 ro  quiet splash
```
The "root=" entry points to the filesystem to be mounted.

---


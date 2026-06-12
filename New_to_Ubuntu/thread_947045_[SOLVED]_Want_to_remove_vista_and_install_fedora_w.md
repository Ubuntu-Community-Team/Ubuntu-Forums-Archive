---
title: "[SOLVED] Want to remove vista and install fedora without disturbing ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by sonu 1807 on 2008-10-13
I want to remove vista completely. I do not want to reinstall ubuntu. Vista occupies 100 GB in my laptop. I want to allocate this space to fedora and have an option to boot into fedora like I do have with vista currently. I do not know how to edit grub. Please help! I have no knowledge of Computers.So please be elaborate.Thanks!

---

### Post by eternalnewbee on 2008-10-13
I would first backup my ubuntu data: See here **[http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html](http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html)**.
Then just useyour Fedora installation CD and install it on the Vista drive.
Make sure you know which drive that is so you don't mess up Ubuntu accidentally.
Good luck

---

### Post by sonu 1807 on 2008-10-23
I made a backup as suggested in the link.... I then used fedora installation DVD to delete all partitions and made a swap of 4 GB (is it too much?, I have 2 GB RAM)....and alloted fedora 70 GB.... then i used ubuntu CD to install it in the remaining free space.... ubuntu automatically recognised Fedora (didn't work the other way around)... now everything is perfect :)

---

### Post by alphaniner on 2008-10-23
> **sonu 1807 said:**
> I made a backup as suggested in the link.... I then used fedora installation DVD to delete all partitions and made a swap of 4 GB (is it too much?, I have 2 GB RAM)....and alloted fedora 70 GB.... then i used ubuntu CD to install it in the remaining free space.... ubuntu automatically recognised Fedora (didn't work the other way around)... now everything is perfect :)

I think maybe 4GB is a excessive for swap.  But I guess it depends on what you are going to do with the machine.  I have 1GB, and I've never seen it go past 10% use.

---

### Post by sonu 1807 on 2008-10-24
I read somewhere on the net that the swap should be of double size of computep's RAM. So I followed that.I am not planning to have any other distro. I too checked swap and found that most of its space is free. May be 1 GB or 2 GB was enough. But in any case, I have enough space on my laptop and is working fine... so I am not going to tweak it any further. Only one issue reamains that my touchpad seems to be oversensitive and creates trouble while typing. Though my computer has touchpad lock. but can I configure it to function properly ? Don't want to edit X11 without proper guidance. I am gong to search forum for that.

---


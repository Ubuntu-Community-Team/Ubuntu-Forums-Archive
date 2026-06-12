---
title: "Wants to disable All Mass Storage Device Drivers SCSI, IDE"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by psrdotcom on 2011-09-21
Hi experts,
I would to modify the kernel in such a way that, it will not contain any mass storage device drivers.

My aim is, when I boot from my own designed pendrive with my own drivers, then only it should boot. It should disable all the other storage devices.

Any suggestions please

---

### Post by psrdotcom on 2011-09-23
Since, no one replied to this thread. To make it active, I posting one of my suggestion.

Will it be good to edit the mountall.conf in /etc/init.d to disable the drives from user to use.

---

### Post by Lisiano on 2011-09-23
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
Your in for a lot of hair loss if you wish to modify the kernel and don't have any previous experience.

If you just don't want non-root/superuser users to mount anything, just delete fuse and gvfs (Gnome)/KIO (KDE). I think that would be enough to block any user-space mounting. Other DEs might have something else that works like gvfs and kio.

---

### Post by psrdotcom on 2012-06-01
If I have done that. Will it boot from my USB Pen Drive and able to detect partitions of the Pen Drive?

---


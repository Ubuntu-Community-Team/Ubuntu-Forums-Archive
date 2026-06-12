---
title: "2 part boot loader question"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by Kickinthedoor on 2012-08-17
Two days ago I re installed my dual boot win 7 and updated ubuntu 10.04 to 12.04. after everything was I done I restarted my computer and the boot loader popped up as usual, only now I have an extra option

Ubuntu with Linux 3.2.0-29 generic pae
Ubuntu with Linux 3.2.0-29 generic pae (recovery mode)
_Previous Linux Versions_
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)

The _previous Linux Versions_ wasn't in my boot loader before I did the update to 12.04, is this just something new with 12.04 or something left over from my last dual boot?

And I'm not entirely sure what some of the other options are/do. The first 2 and last option I know, but I would like to understand what the others are all about. If any one feels up to schooling me a little bit I would really appreciate it...

---

### Post by drs305 on 2012-08-17
The "Previous Linux versions" is a new feature of Grub 1.99 to reduce the size of the main menu. For the default Linux OS, when a new kernel is added it becomes the entry on the main menu. The previous version is moved to the new submenu and is still available by clicking on the submenu.

This prevents the main menu from growing very long as new kernels are introduced. If only one kernel is available the "Previous linux versions" submenu disappears.

Here is more information:
[https://help.ubuntu.com/community/Grub2/Submenus]("https://help.ubuntu.com/community/Grub2/Submenus")

---

### Post by Kickinthedoor on 2012-08-17
thank you for the link good sir, or madam

---


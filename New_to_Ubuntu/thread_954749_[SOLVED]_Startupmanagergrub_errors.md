---
title: "[SOLVED] Startupmanager/grub errors"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by phil66 on 2008-10-21
Installed startupmanager from apt-get in Hardy. The startupmanager is abreviated to show only usplash screen.

The following is the errors when running from terminal.

ray@phil66:~$ sudo startupmanager
Grub2 not detected
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd1,0) /boot/grub/splashimages/tux_tche.xpm.gz

Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Grub Legacy not detected
Usplash detected
Splashy not detected

How do I correct these.
Thanks

---

### Post by philinux on 2008-10-21
Those messages are perfectly normal, nothing to corrct, however you would only need to use 
```
sudo startupmanager 
```
for testing purposes/debug.

Use the menus.
System>Admin>Startup Manager

---

### Post by phil66 on 2008-10-22
> **philinux said:**
> Those messages are perfectly normal, nothing to corrct, however you would only need to use 
```
sudo startupmanager 
```
for testing purposes/debug.

Use the menus.
System>Admin>Startup Manager

Thanks for the reply

Used all avenue's available to start-up the manager with no success.
No clues as to why it would not detect legacy or splash

The fix was to use menu.lst and to configure legacy usplash and splash as desired.

I completely uninstalled startupmanager. This is the first time I have had problems with startupmanager.

---


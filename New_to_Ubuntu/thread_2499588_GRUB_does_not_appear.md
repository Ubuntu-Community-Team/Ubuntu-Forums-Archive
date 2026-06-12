---
title: "GRUB does not appear"
date: 2024-08-01
forum: New to Ubuntu
---

### Post by apgp on 2024-08-01
I just upgraded from Ubuntu 22.04 to 24.04. GRUB does not appear and when I try to recover it it does not let me delete the linux-image-5.15.0-117-generic package. When I try to delete it with dpkg or apt-get it returns error 127. I appreciate some help. Thank you.

---

### Post by oldfred on 2024-08-01
Grub does not normally appear unless you have multiple installs.
You should be able to press escape key just after UEFI/BIOS screen and before grub normally appears to get grub menu.
But if UEFI fast boot is on, you may not have time to press any key. Then try "cold" boot or full power down.

---

### Post by ajgreeny on 2024-08-01
I think it is easier to ensure that the grub menu appears at every boot but for only 2 or 3 seconds, not the default 10 seconds.

Use command ```
sudoedit /etc/default/grub
``` and edit the lines as shown below. All other lines in the menu can remain unchanged.
After these edits run command ***sudo update-grub***
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Ubuntu2404"  #this edit is not important so can be left unedited.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by apgp on 2024-08-02
The GRUB menu appears when I press escape. But when I run the sudo update-grub command, after editing /etc/default/grub, it returns: Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-39-generic
Found initrd image: /boot/initrd.img-6.8.0-39-generic
Found linux image: /boot/vmlinuz-6.5.0-45-generic
Found initrd image: /boot/initrd.img-6.5.0-45-generic
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

---

### Post by oldfred on 2024-08-02
Proxy files are from grub customizer. We have seen issues with it before.
You have to totally uninstall grub. Remove grub folders.
And totally reinstall grub.
You will lose any settings changes you made, but ajgreeny's suggestion above a just about as easy as using Customizer.
And if grub does not reinstall correctly you will not be able to boot, so be sure to have an Ubuntu live installer and know how to reinstall grub from it or add Boot-Repair to live installer with ppa and use advanced mode to reinstall grub.
Best to have good backups for any system change.

---

### Post by apgp on 2024-08-02
Thank you so much. I'll try.

---


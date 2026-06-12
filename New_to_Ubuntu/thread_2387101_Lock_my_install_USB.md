---
title: "Lock my install USB?"
date: 2018-03-14
forum: New to Ubuntu
---

### Post by tdk408 on 2018-03-14
Is is possible to lock my bootable Ubuntu install USB?

I am testing a software process, and after each test I have been wiping the disk and reinstalling a completely virgin copy of Ubuntu.

If I could lock the live boot USB so it never changes, then it seems like I could return to the original unchanged virgin installation by simply rebooting.

If this isn't possible, is there another alternative? Docker seems to containerize an application, but I don't know if it shields the OS from changes. I don't know a way of making a snapshot of the OS, but maybe that would work.

Thanks in advance!

Thomas

---

### Post by kerry_s on 2018-03-14
it already does that. nothing done in a live session is retained.

---

### Post by tdk408 on 2018-03-14
It seems to work that way, but I wanted to be sure nothing happens behind the scenes.  

Thanks!

---

### Post by kerry_s on 2018-03-14
there should be no write access to the drive while your using it.

---

### Post by C.S.Cameron on 2018-03-14
A persistent live USB depends on a file or partition named casper-rw, (or home-rw), plus the word "persistent" needs to be found in the boot process, ie in grub.cfg, txt.cfg or syslinux.cfg, etc.

---

### Post by sudodus on 2018-03-15
[SIZE=4]If your Ubuntu live drive is **cloned** from the iso file, you have 'double security'[/SIZE]

- The feature of the live (live-only) system to not save anything in a persistent way.

- The feature of the cloned ISO 9660 file system: It is a read-only file system.

[SIZE=3]Cloning tools in Ubuntu[/SIZE]

- The **Ubuntu Startup Disk Creator** alias usb-creator-gtk in Ubuntu 16.04 LTS and newer versions

- **Disks** alias gnome-disks

- **[mkusb](https://help.ubuntu.com/community/mkusb)**

[SIZE=3]Cloning tool in Windows[/SIZE]

- **[Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)**

---


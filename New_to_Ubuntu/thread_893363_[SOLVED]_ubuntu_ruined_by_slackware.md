---
title: "[SOLVED] ubuntu ruined by slackware?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-18
i installed slackware to my usb drive and it took over my mbr.
is there any way to rescue ubuntu,super grub didnt work.or
do i have to reinstall,i think i trashed grub,nothing works,can these two distros be run together?because slack uses lilo.i thought i could boot it from a usb stick.
Rick:(

---

### Post by kellemes on 2008-08-18
> **rixtr66 said:**
> i installed slackware to my usb drive and it took over my mbr.
is there any way to rescue ubuntu,super grub didnt work.or
do i have to reinstall,i think i trashed grub,nothing works,can these two distros be run together?because slack uses lilo.i thought i could boot it from a usb stick.
Rick:(

Super Grub Disk is made for "fixing" Grub.
Simply reinstall Grub based on the /boot/grub/menu.lst of your Ubuntu boot-partition and the Ubuntu bootlist will be back.

---

### Post by rixtr66 on 2008-08-18
thanks!!
Rick

---

### Post by oldos2er on 2008-08-18
> **rixtr66 said:**
> i installed slackware to my usb drive and it took over my mbr.
is there any way to rescue ubuntu,super grub didnt work.or
do i have to reinstall,i think i trashed grub,nothing works,can these two distros be run together?because slack uses lilo.i thought i could boot it from a usb stick.
Rick:(

 Of course you can have both distros. Edit your lilo.conf to include Ubuntu.

---

### Post by rixtr66 on 2008-08-18
when i edit lilo conf. what do i put in?/dev/sda5?ubuntu,im not familiar with lilo.
Rick

---

### Post by oldos2er on 2008-08-18
There's an example here: [https://help.ubuntu.com/7.04/installation-guide/i386/linux-upgrade.html](https://help.ubuntu.com/7.04/installation-guide/i386/linux-upgrade.html) toward the bottom of the page under 'Set up the Boot Loader'.

---

### Post by rixtr66 on 2008-08-18
ok thanks that clears things up a little.
Rick

---


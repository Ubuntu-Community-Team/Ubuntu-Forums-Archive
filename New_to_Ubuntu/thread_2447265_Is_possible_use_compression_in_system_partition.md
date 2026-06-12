---
title: "Is possible use compression in system partition ?"
date: 2020-07-16
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-16
Linux allow to use automatic file compression in system and user partitions thus how Windows does ?
Thanks for reply.

---

### Post by ActionParsnip on 2020-07-16
Why? The system data in Ubuntu is very small due to reused libraries. Are you low on space or are you just curious?

---

### Post by Holger_Gehrke on 2020-07-16
NTFS-3g driver for the Windows NTFS filesystem supports reading, writing and creating compressed files since around 2009. So if you have a filesystem created on Windows using that feature it can be used. Of the Linux-native filesystems ZFS can do complete compressed filesystems and btrfs supports transparently compressed files. There are also several solutions based around FUSE (filesystem in userspace).

But generally speaking storage is cheap while processing cycles are expensive. So it's not an option that is used by many people.

Holger

---

### Post by aug7744 on 2020-07-16
Thanks for your reply. ZFS not is automatic compression ? Is possible install Lubuntu in an BTRFS partition ? If not is possible install using BTRFS is possible convert the file system partition to BTRFS and use compression ?

---

### Post by Holger_Gehrke on 2020-07-16
I only know *about* these solutions, I don't know them in the sense of having used them. 

ZFS has volume-management similar to lvm and you can set a whole volume to be compressed. Obviously you'd need an uncompressed volume to boot from, unless grub knows how to uncompress ZFS-volumes (IDK ...). 

In btrfs you'd set the 'c'-attribute using chattr for a file to tell the system to store this file compressed. So in that way btrfs is closer to what windows does (IIRC you have to activate compression somewhere in the properties of a file or in the properties of a folder on windows). 

Both of these filesystems are more at home on servers than on the desktop, so AFAIK the tools to control them are command line only.

It's been a while since I last installed LUbuntu, but I dimly recall having the option to manually set up the partitions and filesystems during installation and having the option to use btrfs for them.

Holger

---

### Post by aug7744 on 2020-08-02
Thanks for reply :)

---


---
title: "External Hard Drive formatting"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Absolute-Zero on 2008-05-28
I bought external hard drive and it is NTFS and works well on windows with out any software.

However ubuntu does not recognise it, is there any way where you can reformat NTFS to some other that can work on ubuntu ?

---

### Post by quelx on 2008-05-28
Which version of Ubuntu are you using?  Do you have the **ntfs-3g** package installed?  You could probably get it working using NTFS, but you could reformat the drive FAT32 (vfat) so it could be used on Mac/Windows/*nix.  After you plug the drive in type ```
dmesg
``` in a terminal window and paste the code from the bottom (relevant to the drive, sd, EHCI, stuff) here.

---

### Post by gali98 on 2008-05-28
You could use gparted

sudo apt-get install gparted

but If you can just use the above posters suggestions it would probably be better.
Kory

---

### Post by Absolute-Zero on 2008-05-29
Thank you guys, and i am using ubunu 8.04 hardey heron

---


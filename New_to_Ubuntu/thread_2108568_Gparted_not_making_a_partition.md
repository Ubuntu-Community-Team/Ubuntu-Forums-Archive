---
title: "Gparted not making a partition"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by mike551345 on 2013-01-24
Hi so im kinda new to Ubuntu. i have just bought a new computer a dell insprion 5721 and i have been having some troubles cause of win8. This was probaly the wort thing i have ever messed around with. so i want to install windows 7 and have ubuntu as a dual-boot. right now i have ubuntu installed and etc. but when i go and try to use gparted to make a new partition so i can install win7 it wont let me resize. i know i have enoough room to do it cause i have a 1tb hard drive. plz plz let me know how to fix this cause i need to get win7 installed for school thanks

---

### Post by Bucky Ball on 2013-01-25
Partitions need to be unmounted to resize and you can't unmount the partition that is running Ubuntu. Boot from the LiveCD (Ubuntu install CD), get to a desktop, right click to make sure your partitions are unmounted and away you go ...

Don't bother creating a new partition for Win. Just leave free space as the Win install will take care of it and create a partition there during install.

---

### Post by mike551345 on 2013-01-25
Yeah but i need to create a partition cause the ubuntu partition is not a NTSF. Win7 needs a Ntsf partition.

---

### Post by Bucky Ball on 2013-01-25
Yes, and Win 7 will create its own NTFS partition when you install it. You don't need to do anything for Win7 in Gparted apart from leave free space for the Win7 install when you shrink your partition. ;)

---

### Post by furything on 2013-01-25
Can I just add that if you are installing to one hard drive windows will overwrite your master boot record (MBR) and you will only be able to boot windows 7.

You can (if you have the software) take an image of the hard drive MBR and restore it afterwords then get grub to rebuild the menu which will add the windows install to its menu.

Alternatively (and I found this a pain) boot from live cd and get it to access your hard drive and reinstall grub. Make sure you read and understand the documentation on ubuntu help for grub2 before your start this install

---

### Post by oldfred on 2013-01-25
Is drive MBR with the 4 primary partition limit or gpt.

 If you have Windows 8 pre-installed it is gpt and you have UEFI with secure boot. Windows 7 will not install on secure boot systems.

---


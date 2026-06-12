---
title: "External hard rive fails to appear after grub resuce issues"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by marinecomm on 2013-08-22
Updated some files last night and was prompted to reboot. when I rebooted the computer I was greeted with a black screen and a message stating:

error: file not found
grub rescue>

Did some research and got the grub2 loaded back up and working again. I can now log into my computer just fine now. Now the only problem is that my external hard drive is not showing up on the desktop when I plug it in.

Ran a disk utility and it shows up there.

Ran gparted and it shows up there. However, under the Mount Point column it's showing /boot/efi. Is that value supposed to be that?

Issued the command cat /proc/partitions: no error messages and the external shows up there.

Issued the command lssub: external hard drive shows up there.

For whatever reason the system isn't putting an icon on my desktop allowing me to mount and access the contents of my external hard drive.

Any thoughts or ideas? Thank you. I'm running Xubuntu 12.04 64-bit.

Update: Was using Thunar to search for some files on my computer. Was able to access my external's files under the folders /boot/efi/. I don't know what's going on.

---


---
title: "GRUB on thumbdrive"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by 001607 on 2012-11-14
guys.

i recently installed ubuntu 12.04 along with win7.
problem is when i boot there is no GRUB to select ubuntu.
GRUB only appears when i reboot with my thumbdrive mounted.

can anyone pls help?

---

### Post by oldfred on 2012-11-14
Welcome to the forums.

It seems like you installed grub to the USB flash drive? Grub normally defaults to install to sda's MBR. But a few computers promote flash drive to sda and then grub installs to wrong drive.

If you can boot from flash drive into Ubuntu run this to reset install drive. Be sure to choose the hard drive, not any partitions or the flash drive again.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Grub remembers where to reinstall on major updates, so you need the reconfigure to reset it, or else it may try to reinstall to flash drive later on.

---

### Post by 001607 on 2012-11-14
thanks a lot.that helps.

---


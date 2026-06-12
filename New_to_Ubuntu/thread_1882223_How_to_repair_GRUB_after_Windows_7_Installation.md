---
title: "How to repair GRUB after Windows 7 Installation"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by Othello75 on 2011-11-16
Hello Everyone,
I have a multi-boot PC with Windows XP, Windows 8 and Ubuntu. Since installing Windows 7, I am unable to boot Ubuntu.  Is it possible to use the Ubuntu LiveCD to repair GRUB?  I'd like to preserve my data. I'm concerned that LiveCD may overwrite it.

Any suggestions you can make would be helpful.

Othello75
-peace

---

### Post by hansdown on 2011-11-16
Welcome to the forum, Othello75.

This should help.

[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

---

### Post by oldfred on 2011-11-16
hansdown's method is fine, it is the full chroot which sometimes has to be done when the shorter method does not work.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
# Or If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by hansdown on 2011-11-17
Thanks, oldfred


I find myself trying to answer questions, that are, out of my depth.

Just trying to help.  :p

---


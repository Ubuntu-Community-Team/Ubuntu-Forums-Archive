---
title: "How to boot from USB"
date: 2018-10-25
forum: New to Ubuntu
---

### Post by nul2 on 2018-10-25
I have Ubuntu working fine, but I want to reinstall with the encryption process. I can't figure out how to boot from the USB. I keep getting a grub command line that I have no idea how to use. It there a command to restart and boot from the USB?

---

### Post by C.S.Cameron on 2018-10-25
Automated Full Disk Encryption is working with 18.04 as part of the install process to USB drives. 
Before proceeding disable the internal drive.
When you get to installation type, choose Encrypt the new Ubuntu installation for security, and Use LVM with the new Ubuntu installation.
[https://askubuntu.com/questions/1085982/does-the-full-disk-encryption-in-the-ubuntu-18-04-installer-encrypt-all-partitio/1086011#1086011](https://askubuntu.com/questions/1085982/does-the-full-disk-encryption-in-the-ubuntu-18-04-installer-encrypt-all-partitio/1086011#1086011)

Manual Full Disk Encryption is also working with 18.04.
It gives a few more options than automatic encryptions.
Paddy Landau has just finished updating the manual and it works great for me:
[https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

In either case the flash drive should be chosen as first HDD in BIOS/UEFI.

Alternately on most computers when booting there is an option to select drive to boot, With HP this is F9, other computers may use F10 or F12.

---

### Post by nul2 on 2018-10-29
Great stuff. Thanks for the post.

---


---
title: "Help with boot-repair"
date: 2018-05-20
forum: New to Ubuntu
---

### Post by frog-guys on 2018-05-20
Hi, I tried to restore/recover GRUB after installing Windows 10, but I ran into the following errors with boot-loader:
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
[URL="http://paste.ubuntu.com/p/k2TwQrhN2R/"]
Pastebin link[/URL]

Thanks for the help

---

### Post by yancek on 2018-05-20
You did a Legacy/MBR install of windows and you appear to have been trying to do an EFI install of Ubuntu.  Don't do that, it won't work the way you want.  Your problem is that you did not install the Ubuntu Grub bootloader to the MBR which would have created a boot entry for both Ubuntu and windows.  You don't have any boot files on the Ubuntu partition so I would suggest that you re-install and make sure you are booting in Legacy mode to match your windows install.  See the Ubuntu documentation on the subject at the link below as it tells you how you will know if you are booting to install in Legacy mode. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2018-05-22
> I might be wrong but I think you have 2 drives.

Based on the size of sdb, I would guess that it is the usb/flash drive he is using to install Ubuntu.

---


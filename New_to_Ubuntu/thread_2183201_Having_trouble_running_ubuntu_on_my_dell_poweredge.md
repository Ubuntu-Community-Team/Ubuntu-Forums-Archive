---
title: "Having trouble running ubuntu on my dell poweredge"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by jg808 on 2013-10-23
so i have a dell poweredge T105 with windows small business server on it and I'm trying to load ubuntu i put the program on a USB and made it bootable using unetbootin i loaded the program and the download went good but it still loads in windows and it dosn't give me the option to pick ubuntu i cant figure out how to uninstall the windows OS and i don't know what i should do. Please help

---

### Post by Impavidus on 2013-10-24
Did you use these instructions: [https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Windows)
Can you boot the live usb? You may have to change the boot order in the bios. You can install as dual boot, keeping Windows and installing Ubuntu on a separate partition of the hard drive, or delete Windows and use Ubuntu only. In this case the installer will simply overwrite Windows, including all files. If this is a production machine, be careful and make backups.

---


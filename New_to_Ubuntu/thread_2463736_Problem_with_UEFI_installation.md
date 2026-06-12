---
title: "Problem with UEFI installation"
date: 2021-06-17
forum: New to Ubuntu
---

### Post by etienne10 on 2021-06-17
Hello,

I am trying to install Ubuntu 20.04 in uefi mode in dual boot with Windows.

I can start the installation in legacy but it's not what I want. When I enter the bios, the usb key is detected but no boot file is detected. I manually entered /EFI/BOOT/BOOTx64 , /EFI/BOOT/grubx64 but neither of them succeeded in launching grub to install ubuntu. I have been trying for several hours now.

If someone has an idea ...

Thanks in advance

---

### Post by Impavidus on 2021-06-17
How have you created your live usb? Some tools create one that can boot only in legacy mode or only in eufi mode, other tools create one that can be booted in both modes.

Have you downloaded the .iso from the official site, ubuntu.com or anything linked from there?

Have you made sure the file was downloaded correctly and correctly copied to the usb drive? This is not likely to be the issue, as you can boot in legacy mode.

---

### Post by yancek on 2021-06-17
The site below is the official Ubuntu documentation on the subject so would be a good place to start.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---


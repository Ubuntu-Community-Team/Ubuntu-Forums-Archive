---
title: "Grub 2 cant detect windows"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by gauravmittal00 on 2012-03-29
i have windows 7 in c drive,
win 7 has reserved 100mb drive for itself as usual.

now i installed ubuntu(macbuntu) 10.10 on other drive
now when i start my laptop its does not show windows as an option

i have checked the boot flag and have repaired my windows with the installation setup(usb), but it didnt work

m copying the result-text which i obtained after boot infoscript

---

### Post by oldfred on 2012-03-29
Welcome to the forums.

Ubuntu is not on another drive, but in partition sda5. Your install looks ok. You do show some wubi files in your Windows partition and have moved the Windows boot flag from sda1 to sda2. If you tried booting with Windows it would not work as boot flag has to be on sda1 which is Windows boot partition.

It looks like you are able to boot Ubuntu. Have you tried this from a terminal. This should find your Windows install and add it to the menu.

```
sudo update-grub
```Grub does not use or need a boot flag and will chainload to the Windows partition correctly without boot flag in correct location. But I would still correct that so if you ever need repairs it is in the correct place. You can use disk utility in Ubuntu, gparted from liveCD or download gparted into your Ubuntu or from a Windows repairCD make the first partition "active" (not sure of details in Windows anymore :) ).

---


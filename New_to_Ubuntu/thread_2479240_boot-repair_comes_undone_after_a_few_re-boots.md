---
title: "boot-repair comes undone after a few re-boots"
date: 2022-09-19
forum: New to Ubuntu
---

### Post by thepolkhandyman on 2022-09-19
20.04.5 LTS on Toshiba Satellite C-55 Intel Celeron N2840 2.16 ghz speed 4096 mb mem  Secure boot disabled and  UEFI boot mode selected in bios
This computer was running Windows 10 without any problems prior to Ubuntu.

Did full install and disk wipe with only the 20.04.5 LTS on the system.
Installed and ran great, loaded a bunch of new software, rebooted and it passes bios and then freezes on Toshiba Welcome Screen
Ran boot-repair and made the recommended repair, worked great started booting from HDD into the newly installed 20.04.5 and working fine

Then same problem loaded a bunch of new software, rebooted and it passes bios and then freezes on Toshiba Leading Innovation Screen
Ran boot-repair again, worked great Ubuntu from HDD perfectly.

then a third time used my browser adding  browser extensions and passwords, then exact same thing freezes after re-boot.

I did not understand boot-repair instruction "Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.5 LTS entry (sda1/efi/ubuntu/grubx64.efi file)
so I did not do this. 

This time I DID NOT DO the repair, just loaded boot-repair and created a summary to the pastebin

[http://paste.ubuntu.com/p/bGhWsgyyf/](http://paste.ubuntu.com/p/bGhWsgyyf/)

Interesting point after running boot-repair and only creating a summary "Not Repairing" the computer was able to boot through the bios through the Toshiba Leading Innovation screen
right into Ubuntu 20.04.5 from HDD and run perfectly again.

Please HELP,
Thanks in advance
-Dave

---

### Post by oldfred on 2022-09-19
Pastebin says that link does not exist.

Grub normally makes the ubuntu entry as default. Normally using shimx64.efi which is for UEFI Secure boot, but works with Secure boot off.
But some systems, so not support change with efibootmgr that grub uses. You then have to go into UEFI settings, not UEFI boot menu & change boot order to Ubuntu.

You can see UEFI boot entries & boot order. This is also in the report.
sudo efibootmgr -v

Lenovo seems to have many models. And some have extra settings in UEFI.
But most require UEFI/BIOS update. And if SSD, SSD firmware updates.

Lenovo has also informed customers about Retbleed, a new speculative execution attack impacting devices with Intel and AMD processors.
[https://support.lenovo.com/us/en/product_security/LEN-91369](https://support.lenovo.com/us/en/product_security/LEN-91369)
The Device Guard BIOS setting locks down the boot order to internal HDD/SSD only.
Lenovo Thinkpad T495 Boot Order Lock
[https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots](https://askubuntu.com/questions/1404259/getting-grub-menu-to-work-on-dual-boot-ubuntu-22-04-windows-11-currently-boots)

---


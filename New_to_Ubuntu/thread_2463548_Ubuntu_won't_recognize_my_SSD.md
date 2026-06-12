---
title: "Ubuntu won't recognize my SSD"
date: 2021-06-13
forum: New to Ubuntu
---

### Post by gabrielabenke on 2021-06-13
Hi, I'm totally new to Ubuntu. I have a Windows 10 PC with 3 SSD and I wanted to install Ubuntu over Windows 10. I'm trying to install from the pendrive. The Ubuntu installer couldn't recognize the SSD where Windows 10 was installed, so I ended up installing in the wrong disk. When I restarted the PC, Windows opened instead of Ubuntu. I tried switching the disk setting in the BIOS from IDE to AHCI, but Unbutu Installer still won't recognize the SSD and now Windows won't boot. The PC says I don't have an OS, even though Ubuntu is installed in one of the SSD. What do I do? How to I totally remove Windows from my PC and make Ubuntu work?

---

### Post by oldfred on 2021-06-13
You have to first convert Windows to use AHCI.
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347) & 
[https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)

If UEFI installs, you should be able to directly boot Windows from UEFI boot menu.
See also link below in my signature for more UEFI info.

With multiple drives & multiple installs, safest way to install, is to unplug all other drives.
Or you can use Something Else but have to choose drive & partition.
If UEFI make sure drive is gpt partitioned.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2021-06-14
> **oldfred said:**
> With multiple drives & multiple installs, safest way to install, is to unplug all other drives.
Or you can use Something Else but have to choose drive & partition.
If UEFI make sure drive is gpt partitioned.

Yes, if you have the luxury of multiple drives, I agree that it is safer to only have the [COLOR="#0000FF"]target drive available[/COLOR].
Isolate, physically remove or de-activate the drives before installation (many PCs have these settings in the UEFI set-up)

---

### Post by oldfred on 2021-06-14
Many also need UEFI firmware update & SSD firmware update.

Just an example, have seen issue with many brands.
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
[https://ubuntuforums.org/showthread.php?t=2420860](https://ubuntuforums.org/showthread.php?t=2420860)

---


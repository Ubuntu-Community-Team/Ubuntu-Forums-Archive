---
title: "Error while booting with flashdisk"
date: 2023-06-02
forum: New to Ubuntu
---

### Post by alexbaqua on 2023-06-02
Hi all;
Today i tried to install Ubuntu 21.10 Imprish to my Asus Vivobook X1502ZA for testing. Just created a bootable flashdisk with Universal USB installer so far so good. When I boot from flashdisk taking this error:"Error verification failed (0x1A) security violation" But also tested with LTS bootable flashdisk this is not stopping the process and correctly booting. What would be this error mean. I would be much appreciated.
alex

---

### Post by oldfred on 2023-06-02
Please use a current version.
21.10  Impish Indri
Ubuntu 21.10 will be supported for 9 months until July 2022.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You also need to install a version that is newer (by months) than your system, so you have kernel & drivers that will support your hardware.
Linux often is not directly supported by vendors, only Windows, so Linux has to develop fixes & include those in kernel & drivers. Then those updates have to be included in a distribution. 
If most current LTS is new enough often better to use it for its 5 year support (3 years on flavors).
But if very new system, you may need the latest interim release which will need update every 9 months to new version.

Be sure to boot in UEFI mode, if your system still has the old BIOS mode. Many newer systems now are UEFI only (even if vendor calls it BIOS).
[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

Issues often common across multiple models of same brand. But different issues if AMD or Intel. And which video card/chip is used.
Asus Vivobook S14 Also Zenbook
[https://askubuntu.com/questions/1432177/issues-with-dual-booting-of-asus-vivobook-zenbook-series-laptops-with-ubuntu-22](https://askubuntu.com/questions/1432177/issues-with-dual-booting-of-asus-vivobook-zenbook-series-laptops-with-ubuntu-22)
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)

My newer Dell just installed with no UEFI settings changes, but I did have to turn off Windows fast start up & Windows bitlocker.

---


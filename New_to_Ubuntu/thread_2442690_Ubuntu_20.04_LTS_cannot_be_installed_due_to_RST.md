---
title: "Ubuntu 20.04 LTS cannot be installed due to RST"
date: 2020-05-06
forum: New to Ubuntu
---

### Post by dev30 on 2020-05-06
I tried installing ubuntu along with Windows 10 from a bootable USB drive on my internal hard drive. My device has Intel Optane memory i.e. it has Rapid Storage Technology. My device SATA configuration is RAID and not AHCI and now it says that I cannot install it and I have to change it. I cannot find a proper solution to it.

Please HELP!!!

---

### Post by CelticWarrior on 2020-05-06
Welcome.

The solution is the same already posted in hundreds of tutorials: Install AHCI support in Windows, change to AHCI, install Ubuntu.

---

### Post by dev30 on 2020-05-08
Okay Thanks!!

---

### Post by oldfred on 2020-05-09
Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571)
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)

---

### Post by VMC on 2020-05-10
oldfred. I tried most of those fixes yesterday. All to no avail. In the end I just re-installed Windows with AHCI active. It was easier and faster after spending hours(most of the day), inside "diskpart" windows repair then re-booting, only to find another "blue screen", then yet another hack, etc. The re-install took far less time than all the nonsense.

---


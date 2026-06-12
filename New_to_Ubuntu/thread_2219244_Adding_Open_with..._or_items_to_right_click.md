---
title: "Adding Open with... or items to right click"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by phazerxo09 on 2014-04-23
I'm new to Ubuntu and i'm running 10.04 due to the age of my laptop and needing the fglrx drivers to prevent heat issues, anyways i would like to know how i can add items to the right click menus for example:

[IMG]http://i.imgur.com/WvIx4iJ.png[/IMG]

Lets say i wanted to open that .desktop file in a text editor with root permission to edit it and save, how can i do that?

Thanks

---

### Post by mörgæs on 2014-04-23
Hi, welcome to the fora.
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by phazerxo09 on 2014-04-23
Nothing opens when I do

---

### Post by phazerxo09 on 2014-04-23
This is what sudo lshw -short brings up

```

H/W path         Device      Class       Description
====================================================
                             system      Presario CQ62 Notebook PC
/0                           bus         1444
/0/0                         memory      1MiB BIOS
/0/c                         processor   AMD Athlon(tm) II P320 Dual-Core Proces
/0/c/d                       memory      256KiB L1 cache
/0/c/e                       memory      1MiB L2 cache
/0/f                         memory      3GiB System Memory
/0/f/0                       memory      2GiB SODIMM Synchronous 1066 MHz (0.9 n
/0/f/1                       memory      1GiB SODIMM Synchronous 1066 MHz (0.9 n
/0/100                       bridge      RS780 Host Bridge Alternate
/0/100/1                     bridge      RS780 PCI to PCI bridge (int gfx)
/0/100/1/5                   display     M880G [Mobility Radeon HD 4200]
/0/100/5                     bridge      RS780 PCI to PCI bridge (PCIE port 1)
/0/100/5/0       eth1        network     Broadcom Corporation
/0/100/6                     bridge      RS780 PCI to PCI bridge (PCIE port 2)
/0/100/6/0       eth0        network     RTL8101E/RTL8102E PCI Express Fast Ethe
/0/100/11        scsi0       storage     SB700/SB800 SATA Controller [AHCI mode]
/0/100/11/0      /dev/sda    disk        160GB Hitachi HTS54501
/0/100/11/0/1    /dev/sda1   volume      100MiB Windows NTFS volume
/0/100/11/0/2    /dev/sda2   volume      109GiB Windows NTFS volume
/0/100/11/0/3    /dev/sda3   volume      39GiB Extended partition
/0/100/11/0/3/5  /dev/sda5   volume      37GiB Linux filesystem partition
/0/100/11/0/3/6  /dev/sda6   volume      1688MiB Linux swap / Solaris partition
/0/100/11/1      /dev/cdrom  disk        DVD A  DS8A4LH
/0/100/12                    bus         SB700/SB800 USB OHCI0 Controller
/0/100/12.2                  bus         SB700/SB800 USB EHCI Controller
/0/100/13                    bus         SB700/SB800 USB OHCI0 Controller
/0/100/13.2                  bus         SB700/SB800 USB EHCI Controller
/0/100/14                    bus         SBx00 SMBus Controller
/0/100/14.2                  multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                  bridge      SB700/SB800 LPC host controller
/0/100/14.4                  bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                  bus         SB700/SB800 USB OHCI2 Controller
/0/100/16                    bus         SB700/SB800 USB OHCI0 Controller
/0/100/16.2                  bus         SB700/SB800 USB EHCI Controller
/0/101                       bridge      K10 [Opteron, Athlon64, Sempron] HyperT
/0/102                       bridge      K10 [Opteron, Athlon64, Sempron] Addres
/0/103                       bridge      K10 [Opteron, Athlon64, Sempron] DRAM C
/0/104                       bridge      K10 [Opteron, Athlon64, Sempron] Miscel
/0/105                       bridge      K10 [Opteron, Athlon64, Sempron] Link C
/1                           power       MU06047
```

---

### Post by mörgæs on 2014-04-23
It's quite strong hardware. Does it also overheat running X/Lubuntu 14.04?

---


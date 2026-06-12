---
title: "Problems with grub2 when converting Windows 7 HP p2-1033w to Linux"
date: 2018-01-20
forum: New to Ubuntu
---

### Post by womanrising on 2018-01-20
Greetings,
For the past 5 days I have been trying to convert an old HP P2-1033w to Linux, preferably Ubuntu. The problems I have is when it gets to grub2 installation, it locks up and wont go any further. The first time I left it on overnite to see if it was just slow moving, the next morning it was still in the same place. I tried it again several times with ubuntu, then Debian 9, then Linux Mint, with each of these I still had the same issue, freezing at during the grub2 install. I am new to Linux so please help me with idiot proof instructions :redface:.  With the several attempts at the installation of Linux, I have atleast accomplished 1 goal, that is I no longer have windows 7 on the computer. The problem is I do not have a usable Linux desktop OS either.   Please Help ](*,)](*,)
The system information I was able to get is as follows:
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            20
Model:                 2
Model name:            AMD E-300 APU with Radeon(tm) HD Graphics
Stepping:              0
CPU MHz:               1114.000
CPU max MHz:           1300.0000
CPU min MHz:           780.0000
BogoMIPS:              2594.75
Virtualization:        AMD-V
L1d cache:             32K
L1i cache:             32K
L2 cache:              512K
NUMA node0 CPU(s):     0,1
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt hw_pstate vmmcall arat npt lbrv svm_lock nrip_save pausefilter

H/W path                 Device      Class       Description
============================================================
                                     system      p2-1033w (QP812AA#ABA)
/0                                   bus         2AD3
/0/0                                 memory      64KiB BIOS
/0/4                                 processor   AMD E-300 APU with Radeon(tm) H
/0/4/5                               memory      128KiB L1 cache
/0/4/6                               memory      1MiB L2 cache
/0/d                                 memory      16GiB System Memory
/0/d/0                               memory      8GiB DIMM DDR3 Synchronous 1600
/0/d/1                               memory      8GiB DIMM DDR3 Synchronous 1600
/0/100                               bridge      Family 14h Processor Root Compl
/0/100/1                             display     Wrestler [Radeon HD 6310]
/0/100/4                             bridge      Family 14h Processor Root Port
/0/100/11                            storage     SB7x0/SB8x0/SB9x0 SATA Controll
/0/100/12                            bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Con
/0/100/12/1              usb4        bus         OHCI PCI host controller
/0/100/12.2                          bus         SB7x0/SB8x0/SB9x0 USB EHCI Cont
/0/100/12.2/1            usb1        bus         EHCI Host Controller
/0/100/12.2/1/5          scsi6       storage     USB DISK 3.0
/0/100/12.2/1/5/0.0.0    /dev/sdb    disk        15GB SCSI Disk
/0/100/12.2/1/5/0.0.0/1  /dev/sdb1   volume      14GiB Windows FAT volume
/0/100/13                            bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Con
/0/100/13/1              usb5        bus         OHCI PCI host controller
/0/100/13/1/1                        input       2.4G RF Keyboard & Mouse
/0/100/13.2                          bus         SB7x0/SB8x0/SB9x0 USB EHCI Cont
/0/100/13.2/1            usb2        bus         EHCI Host Controller
/0/100/14                            bus         SBx00 SMBus Controller
/0/100/14.2                          multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                          bridge      SB7x0/SB8x0/SB9x0 LPC host cont
/0/100/14.4                          bridge      SBx00 PCI to PCI Bridge
/0/100/14.5                          bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Con
/0/100/14.5/1            usb6        bus         OHCI PCI host controller
/0/100/15                            bridge      SB700/SB800/SB900 PCI to PCI br
/0/100/15.1                          bridge      SB700/SB800/SB900 PCI to PCI br
/0/100/15.1/0            enp4s0      network     AR8152 v2.0 Fast Ethernet
/0/100/16                            bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Con
/0/100/16/1              usb7        bus         OHCI PCI host controller
/0/100/16.2                          bus         SB7x0/SB8x0/SB9x0 USB EHCI Cont
/0/100/16.2/1            usb3        bus         EHCI Host Controller
/0/101                               bridge      Family 12h/14h Processor Functi
/0/102                               bridge      Family 12h/14h Processor Functi
/0/103                               bridge      Family 12h/14h Processor Functi
/0/104                               bridge      Family 12h/14h Processor Functi
/0/105                               bridge      Family 12h/14h Processor Functi
/0/106                               bridge      Family 12h/14h Processor Functi
/0/107                               bridge      Family 12h/14h Processor Functi
/0/108                               bridge      Family 12h/14h Processor Functi
/0/1                     scsi0       storage     
/0/1/0.0.0               /dev/sda    disk        500GB Hitachi HDS72105
/0/1/0.0.0/1             /dev/sda1   volume      511MiB Windows FAT volume
/0/1/0.0.0/2             /dev/sda2   volume      488MiB EFI partition
/0/1/0.0.0/3             /dev/sda3   volume      464GiB EFI partition
/0/2                     scsi1       storage     
/0/2/0.0.0               /dev/cdrom  disk        DVD A  DH16ABLH
/1                                   power       Standard Efficiency
```

Finally the partition information

```
Disk /dev/loop0: 1.7 GiB, 1842749440 bytes, 3599120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 32476F0C-7A38-4418-8DFF-95DE5390E8E4

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624   2050047    999424   488M Linux filesystem
/dev/sda3  2050048 976771071 974721024 464.8G Linux filesystem

Disk /dev/sdb: 14.5 GiB, 15504900096 bytes, 30283008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x005d6e84

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 30283007 30280960 14.4G  c W95 FAT32 (LBA)
```

---

### Post by oldfred on 2018-01-20
Please use code tags on longer text or terminal output.

Do not know any issues related to AMD, but it looks like a typical UEFI install. So system not that old.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by womanrising on 2018-01-20
It was not code, it was the configuration for my computer. :(

---

### Post by coffeecat on 2018-01-20
@womanrising, I've done the best I can with your first post to remove spurious BBCode formatting and insert BBCode code tags. It doesn't matter whether it was code or not. Please use code tags for any terminal output, otherwise you lose column spacing.

---

### Post by cruzer001 on 2018-01-20
Hello

Dual core, plenty of ram.  I think your box should run Ubuntu just fine.

May want to try the mini.iso to install Ubuntu.  And I would suggest 16.04 to keep you on xorg instead of wayland.  The mini.iso requires an internet connection.  It has been know to work when the regular installer will not.  I think worth a try.

Download #3 under 64bit.  "Ubuntu 16.04 LTS "Xenial Xerus" 

[https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29_.28Recommended.29](https://help.ubuntu.com/community/Installation/MinimalCD#A64-bit_PC_.28amd64.2C_x86_64.29_.28Recommended.29)

I also had a look at your graphic processor and it seems to be supported.

[https://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](https://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)

---

### Post by womanrising on 2018-01-25
@cruzer001,
Thank you!! I installed the mini.iso and it worked nicely. I even went back and installed the full Ubunut distro and it took it with no problem after installing the mini.iso.

---

### Post by cruzer001 on 2018-01-25
Congratulations :)

I guess you can mark this thread solved (under thread tools).

):P

---

### Post by womanrising on 2018-01-25
):P \\:D/ =d>

Done.. thanks

---


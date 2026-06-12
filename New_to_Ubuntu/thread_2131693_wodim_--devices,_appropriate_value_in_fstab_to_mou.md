---
title: "wodim --devices, appropriate value in fstab to mount CD drive"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by deadlytackler on 2013-04-02
Hi friends,
struggling to mount my DVD drive, here is output of "$ wodim --devices"
```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'    rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H55N'
-------------------------------------------------------------------------
```

here is the output of "$ sudo fdisk -l"

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00095982

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      391167      194560   83  Linux
/dev/sda2          391168     4296703     1952768   82  Linux swap / Solaris
/dev/sda3         4296704    53125119    24414208   83  Linux
/dev/sda4        53127166   136769535    41821185    5  Extended
/dev/sda5        53127168   136769535    41821184   83  Linux
```

also the output of "$ lspci" is
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 0e)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)#
```



what should be the appropriate value for this particular DVD drive in fstab?

---

### Post by Bashing-om on 2013-04-02
deadlytackler;

DVD drive should be recognized by the operating system as soon as a disk is inserted and the tray closed. No intervention on your part should be required.
What are you trying to do, or what is specifically happening when you insert a disk ? 
Maybe (yeah, pointless to play guessing games), you do not have the required codecs , maybe doing a non-standard procedure ?[INDENT=2]more info = better help

[/INDENT]

---

### Post by deadlytackler on 2013-04-02
When I am inserting  dvd disc nothing is happening, though I just discovered that upon inserting audio cd it comes into life.
How to have codecs? might be you are pointing to right direction

---

### Post by Bashing-om on 2013-04-02
deadlytackler;
Not having the proper codec is a good possibility, as ubuntu is free and open source and  many DVD's require proprietary software; the 3rd party software must be installed. Most of the needed codes are available for installation in ubuntu's repositories. It is your decision if you want proprietary software on your system.

Insure you have  "independent - provided by third-party software developers" enabled in Software Sources -> other sources. In ubuntu Software Center, search for "ubuntu-restricted-extras" and install the package (lots of other addons too in this package)... or from the command line:
```
 sudo apt-get install ubuntu-restricted-extras
```

Install the package and advise.[INDENT=2]
hope this helps

[/INDENT]

---


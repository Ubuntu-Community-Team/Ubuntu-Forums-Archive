---
title: "Reltek Card Reader not working"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Kedster on 2013-02-19
Hello, and thank you all for giving time to try to help 

I have an internal card reader in my HP Pavilion DV6-6155ca and the card reader is a "multi-card media reader" (I know this means nothing but trying to be though) and the device is the RTS5209 PCI Express Card Reader.  I am running ubuntu 12.10 

When I insert a sd card nothing happens at all. The card is readable from other devices and I have used at one point in another version of ubuntu

 ```
uname -a
Linux Ketterer-Ubuntubook 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 01:50:30 UTC 2013        x86_64 x86_64 x86_64 GNU/Linux
```

The output of lspci

    ```
$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6400M/7400M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
19:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```



The outout of lspci -vmmnn | grep -A4 -B2 Realtek 
   
    ```
$ lspci -vmmnn | grep -A4 -B2 Realtek 
    Slot:	13:00.0
    Class:	Unassigned class [ff00]
    Vendor:	Realtek Semiconductor Co., Ltd. [10ec]
    Device:	RTS5209 PCI Express Card Reader [5209]
    SVendor:	Hewlett-Packard Company [103c]
    SDevice:	Device [1656]
    Rev:	01
```


Output of lsusb

```
$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 004: ID 5986:02ac Acer, Inc 
Bus 002 Device 004: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 8086:0189 Intel Corp.
``` 


Thank you for your help again

---

### Post by Kedster on 2013-02-20
Bump
I understand advice is a commodity and you all deserve a lot more for being on the forums, I hope that someone is able to help me

---

### Post by Mark Phelps on 2013-02-21
Sorry for the bad news, but I've had the same problem -- reader showing up in lspci but not in lsusb -- and the only solution I found to work was to get an external card reader that connected via USB.  Seems that Linux doesn't find drivers for internal card readers.

---


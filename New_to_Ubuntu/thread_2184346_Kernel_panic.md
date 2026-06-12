---
title: "Kernel panic?"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by ishana.rl on 2013-10-28
I been having this problem since yesterday but it was just being solved by a simple restart... but now a simple restart would just mess up things even more sometimes!
I am not sure what is causing this but I have only followed some instructions from a website called "noobslab" and since then this been happening!

[http://i.imgur.com/JiH5iJ6.jpg](http://i.imgur.com/JiH5iJ6.jpg)

It just happens all of a sudden sometimes and the worse part is when it keeps my caps lock blinking.
The only way to fix this "sometimes" is to to do a hard restart.

Link I followed everything even the hibernate
[http://www.noobslab.com/2013/04/tweaksthings-to-do-after-install-of.html](http://www.noobslab.com/2013/04/tweaksthings-to-do-after-install-of.html)

---

### Post by cdaver on 2013-10-28
When posting you should mention the Hardware you are using as well as Version of Ubuntu you are using.

---

### Post by buzzingrobot on 2013-10-28
Executing 'uname -a' in a terminal will provide the kernel version, plus other info that will be helpful here.

try backing out the hardware-related changes from Noobslab, one at a time, and rebooting.  I'd start with that hibernation tweak.

---

### Post by ishana.rl on 2013-10-28
Thank you that would make perfect sense ^_^

Ubuntu 13.04

Hardware
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
0b:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)


```

---


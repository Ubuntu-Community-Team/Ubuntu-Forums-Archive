---
title: "nvidia driver. two graphic cards ASUS laptop"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by sssuizaaa on 2011-10-15
Hello All,

I post this in case it is helpful for anyone.

ASUS U33jc. 2 Graphics card. One Intel one that is included in the motherboard (I guess) and an Nvidia one.
After installing Ubuntu 11.10 I had no 3D effects. The unity launcher was 2D, etc. looking at additional drivers, the NVIDIA accelerated graphics driver was installed. when hitting the NVIDIA X Server application a message appeared that the driver was apparently not working (it was a long message that I do not exactly recall).
Solution. I simply removed the nvidia accelerated graphics driver and restarted the computer. Everything seemed to work fine after that. I now have 3D effects.

What happened. I do not know, but if someone has the same problem, this seems to be the solution or at least one solution.

I wonder which card and which driver is running now?. Does anybody have an idea?
here's the result of lspci:

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
05:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

Regards,

sssuizaaa

---


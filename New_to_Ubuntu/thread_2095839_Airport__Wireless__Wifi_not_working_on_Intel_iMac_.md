---
title: "Airport / Wireless / Wifi not working on Intel iMac after last update of 12.10"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by seventhsamurai on 2012-12-18
Hi Guys

I am running 12.10 on an intel imac and it was running perfectly fine until the last update. Now suddenly, my airport / wireless networking doesn't work anymore since the update. In the networking menu, I don't even see an option to enable/disable wireless anymore, which leads me to believe the system isn't even detecting the hardware. I would appreciate any help.

Thanks.

---

### Post by seventhsamurai on 2012-12-18
The output of lspci -nn is as follows:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 03)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 04)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 04)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 04)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 04)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 04)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 04)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 04)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 04)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 04)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 04)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] [1002:9583]
03:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW643 [TrueFire] PCIe 1394b Controller [11c1:5901] (rev 06)
04:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
```

---

### Post by seventhsamurai on 2012-12-18
Ok I managed to solve it. Just need to uninstall bcmwl-kernel-source. Search for it in synaptic package manager and uninstall and REBOOT. The airport and wifi should start working again. 

In case after uninstalling, it still doesn't work, install the firmware manually. Instructions here: [http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work](http://askubuntu.com/questions/166504/macbook-pro-wifi-wont-work)

---


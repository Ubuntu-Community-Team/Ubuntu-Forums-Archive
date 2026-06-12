---
title: "All the sudden can't connect to 1 wireless network in particular"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by spumvis on 2013-01-28
First the story:

I am connected to the internet with a Belking 300N router. This worked fine until a couple of days ago.
I was connected all day, closed my netbook (didn't turned it off), went to my job with it, I used it there (though without connecting to the internet), came home and discovered than it had locked up.

So I rebooted and I can't connect to my network. It keeps trying and occasionally it asks my psk. 
I can connect to other networks without any real issues.

I can however connect with my phone (android 4.0), tablet (android 4.0) and desktop (Windows 7) to the troublesome network without any problems. Only with my netbook (Ubuntu 12.04)I can't connect to it.

What I've gathered from other threads is that you'll want this:

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ac
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=08 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 8446
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f7e00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc00 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at f7d00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 8446
    Flags: bus master, fast devsel, latency 0
    Memory at f7e80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 841c
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 7f900000-7fafffff
    Prefetchable memory behind bridge: 000000007fb00000-000000007fcfffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: f8000000-fbffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: f7f00000-f7ffffff
    Prefetchable memory behind bridge: 000000007f700000-000000007f8fffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [90] Subsystem: ASUSTeK Computer Inc. Device 83ad
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel
    Capabilities: [180] Root Complex Link
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f7cf7c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: [50] Subsystem: ASUSTeK Computer Inc. Device 83ad

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=0c <?>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
    I/O ports at d080 [size=8]
    I/O ports at d000 [size=4]
    I/O ports at cc00 [size=8]
    I/O ports at c880 [size=4]
    I/O ports at c800 [size=32]
    Memory at f7cf7800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [70] Power Management version 2
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 83ad
    Flags: medium devsel, IRQ 4
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
    Subsystem: ASUSTeK Computer Inc. Device 8468
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7fc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec00 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-1f-81-6c-bc-ae-c5-ff
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: AzureWave Device 2047
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fbffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [13c] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-60-ff-ff-a7-48-5d
    Capabilities: [16c] Power Budgeting <?>
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac
```

Some help would be greatly appreciated so I can stop mooching off my neighbour's internet.

---

### Post by frank604 on 2013-01-28
You have a BCM4313 wifi adapter.  [http://ubuntuforums.org/showthread.php?t=2067185](http://ubuntuforums.org/showthread.php?t=2067185) This guy does too, and his issue was solved.

First page of the thread = got wifi up but slow speeds (fix does not persist after reboot)
Second page of thread = got wifi up with fast speeds (fix does not persist after reboot)
Third page = got wifi up with fast speed and fix persists through reboot (magically it seems)

---

### Post by spumvis on 2013-01-28
> **frank604 said:**
> You have a BCM4313 wifi adapter.  [http://ubuntuforums.org/showthread.php?t=2067185](http://ubuntuforums.org/showthread.php?t=2067185) This guy does too, and his issue was solved.

First page of the thread = got wifi up but slow speeds (fix does not persist after reboot)
Second page of thread = got wifi up with fast speeds (fix does not persist after reboot)
Third page = got wifi up with fast speed and fix persists through reboot (magically it seems)

Thanks.

I tried the solution on page 1 and I was finally able to connect. Though it boosted the reception of 2 other networks, the connection remains very poorly despite sitting next to the router.
With the solution on page 3 it looks like I gained 1 bar (from 1 to 2) and it seems to persists after rebooting.

So that's a nice improvement.

Though when trying the solution on page 2, I got this error.

```
spumvis@eee:~$ sudo su
[sudo] password for spumvis:
root@eee:/home/spumvis# apt-get remove --purge brcmwl-kernel-source
Reading package lists... Done
Building dependency tree  	 
Reading state information... Done
E: Unable to locate package brcmwl-kernel-source
root@eee:/home/spumvis# echo brcmsmac >>/etc/modules
root@eee:/home/spumvis# exit
exit

```

---

### Post by frank604 on 2013-01-28
That error just means the brcmwl driver wasn't in your kernel source.  I would just ignore it as it isn't blocking you from getting online.  If you aren't happy with 2 bars of wifi signal, or you think the transfer speed is slow, perhaps testing it WITH the absent brcmwl driver would be possible.  But if you aren't too familiar with all of this or understand what the code does then I would stay with what you have?  Thoughts?

---

### Post by spumvis on 2013-01-28
I do have a Broadcom STA wireless driver listed under additional drivers. I don't know if that's part of the issue or not.

I mainly use the netbook to Skype or on travels... And to entertain me during graveyard shift at work. So it's not that big of an issue; just annoying.

Thanks a lot for helping me. I'm going to give it a few days to see  if the fix has permanently fixed it before I mark this as solved.

---


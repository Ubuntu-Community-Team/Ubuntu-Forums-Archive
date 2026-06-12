---
title: "No internet via wireless or Ethernet"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by Delta 397 on 2012-05-04
I installed Ubuntu 12.04 on my Macbook Pro 8,1 and I have no Ethernet connection to the internet or wireless for that matter.  Here is info on my PC.


```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)
```

---

### Post by jtarin on 2012-05-04
Tell us what you have done to try connecting.

---

### Post by Delta 397 on 2012-05-04
well when i was installing ubuntu the ethernet connection was established and the install went smoothly.  After i rebooted from the hd, I had no firmware for my wireless card and no connection via ethernet.  It tries to establish a connection to the network it used when it installed but it always fails eventually.

---

### Post by Hadaka on 2012-05-04
[http://ubuntuforums.org/showthread.php?t=1901839&highlight=b43](http://ubuntuforums.org/showthread.php?t=1901839&highlight=b43)

read post #10  it has the zip file you probably need and instructions to 
load it for the b43 drivers for broadcom

hope this helps.

---

### Post by Delta 397 on 2012-05-04
I tried all the steps to no avail.  Any other suggestions?

---

### Post by jtarin on 2012-05-05
Your hard wire connection is DSL I assume? Have you used Network Manager to setup your DSL connection?

---

### Post by carl4926 on 2012-05-05
I'll PM you a link, extract the folder and place it in
/lib/firmware

---

### Post by Delta 397 on 2012-05-05
I believe that it is dsl but im at a College so its hard to find out what exactly all the pieces of my internet connection are and where they are coming from.

---

### Post by carl4926 on 2012-05-05
For hardwire not to work OOTB is very odd

---

### Post by Delta 397 on 2012-05-05
Yeah I've had a tough time trying to find info on how to fix this problem without internet connection.

---

### Post by Senior_Buckethead on 2012-05-05
See if this is of any help.
[http://wiki.debian.org/Broadcom](http://wiki.debian.org/Broadcom)

---

### Post by Hadaka on 2012-05-05
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

This should help sort out your connection problem. Choose b-43 no internet on the right
side of the page.

hope this helps

---

### Post by Delta 397 on 2012-05-05
Unfortunately neither link offered a solution that helped.  I did notice that there was a list of supported wireless chips and that my b4331 was not there however in the list of unsupported chips, it wasn't listed there either.

---

### Post by carl4926 on 2012-05-05
> **Delta 397 said:**
> Unfortunately neither link offered a solution that helped.  I did notice that there was a list of supported wireless chips and that my b4331 was not there however in the list of unsupported chips, it wasn't listed there either.

To be sure I'd need to see the output of

```
lspci -nnk
```

[[IMG]http://thumbnails45.imagebam.com/18870/87be2b188698581.jpg[/IMG]](http://www.imagebam.com/image/87be2b188698581)

---

### Post by whistlerspa on 2012-05-06
I found that my desktop PC would not connect to the DSL router or the internet if both connections were simultaneously live. I removed the ethernet cable and wireless works fine now. Disconnecting wirelss did not enable the ethernet connection to work. This may not be the same for you but that's what I found.

---

### Post by Delta 397 on 2012-05-06
here is the output of "lspci -nnk".


```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
	Subsystem: Apple Inc. Device [106b:00db]
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:01.1 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0105] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
	Subsystem: Apple Inc. Device [106b:00db]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 [8086:1c2c] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 [8086:1c27] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Intel Corporation Device [8086:7270]
	Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
	Subsystem: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4]
	Kernel driver in use: tg3
	Kernel modules: tg3
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
	Subsystem: Broadcom Corporation Device [14e4:0000]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Apple Inc. AirPort Extreme [106b:00d6]
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma
04:00.0 FireWire (IEEE 1394) [0c00]: LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) [11c1:5901] (rev 08)
	Subsystem: LSI Corporation Device [11c1:5900]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
mitch@mitch-Ubuntu:~$ 

```

---

### Post by linuxmatt7 on 2012-05-06
I would recommend that you move this thread to the Mac section this way you will get more/better results than in this forum, but it is ok since you are a newbie. Have you tried the Live CD. Does the Live CD see your Wireless and Ethernet card. If it does than backup everything and install Ubuntu 12.04 LTS, I would recommend you test drive Xubuntu 12.04 LTS. Now if it doesn't see your Wireless and Ethernet cards you might try looking for drivers online.  ):P

---


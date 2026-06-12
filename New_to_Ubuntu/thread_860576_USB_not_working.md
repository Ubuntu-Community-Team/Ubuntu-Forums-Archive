---
title: "USB not working"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by RMorris78 on 2008-07-15
I installed Hardy on my desktop (Via PC 2500 Mobo -- Same thats in the everex PC that runs gOS...) and the USB doesnt work.  Here is my lspci output

```

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

Ive installed ubuntu before and am fairly confident with it, but ive never had a USB problem before so I do not no where to start.  Thanks for the help in advance.

---

### Post by benfindlay on 2008-07-15
just out of interest, what does lsusb output show?

---

### Post by RMorris78 on 2008-07-15
lsusb has no output at all

---

### Post by oldsoundguy on 2008-07-15
don't know if this applies in your case, but I attempted to install Hardy on an older PIII with a Via chipset and it installed .. except it saw the hard drives as SATA and was totally useless on the machine (since reverted back to Gutsy).  It still could be a Via chipset issue.

---

### Post by johnaaronrose on 2008-07-17
I had usb problem with Hardy. All usb devices worked except usb mouse & usb keyboard. PC is Dell Inspiron 1501 laptop. Solution for me was was to amend /boot/grub/menu.lst, adding "acpi=noirq pci=noacpi" to end of kernel line. Also, add this to defoptions line so that it holds after kernel upgrade."

---


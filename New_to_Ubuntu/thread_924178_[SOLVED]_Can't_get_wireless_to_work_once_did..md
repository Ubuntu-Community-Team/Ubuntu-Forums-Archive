---
title: "[SOLVED] Can't get wireless to work once did."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by misswham on 2008-09-19
hi there. my laptop all of a sudden stopped getting wireless. when i log on it automatically connects but now the 2 icons have an exclamation point and the other has a minus sign. I dont know why it stopped connecting but it did. also the negative sign error message says

Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device

and when i right click on the one with the exclamation point

enable network is checked

and edit wireless network is in bold and when i left click edit wireless network i see my router listed under networks.

can someone help?

---

### Post by Borusa on 2008-09-19
You don't say what Laptop you have, but can you check in the BIOS (press whatever key it asks for on startup to "Enter Setup") and check whether your Wireless card is Enabled (it's often in places called something like "Onboard Devices".)

---

### Post by Borusa on 2008-09-19
The "Edit Networks" thing basically allows you to edit networks that you have connected to in the past. It doesn't show ones that are currently available.

---

### Post by misswham on 2008-09-19
do u know how to make it available?

---

### Post by Borusa on 2008-09-19
Well, if it has been disabled in the BIOS, you can just change the BIOS to have it "Enabled" and save settings. If it hasn't been disabled, then there are some other options, but I'd need to know laptop make and model!

---

### Post by misswham on 2008-09-19
First when I try to hit f2 at start up it takes me straight to the grub menu to choose linux or windows.  For some reason I cant get to the BIOS screen to check if the wireless card is enabled.  I dont know why it would be disabled since I never disabled it.  I have a Toshiba Satellite laptop and here is the type of wireless card I have.

lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by misswham on 2008-09-19
Also I looked in hardware drivers and it says 

support for atheros 802.11 wireless LAN cards.    in use

is checked with a green check mark.

---

### Post by misswham on 2008-09-19
its working now.  I dont know what I did but it is working.  thanks

---


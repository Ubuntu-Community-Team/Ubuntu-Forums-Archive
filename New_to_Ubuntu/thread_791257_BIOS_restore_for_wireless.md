---
title: "BIOS restore for wireless"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by scholzilla on 2008-05-12
I've been having a really difficult time getting my wifi up and running despite days on end reading various posts. Because device manager does not show a wireless device and because of the output below, I decided to check my BIOS settings to see if there was a clue. NOTE: This is a laptop with an internal wifi card that I can't touch. 

I don't know if this is normal, but under the Advanced tab in the BIOS menu, the wireless option is "greyed out" with the word [Restore] written next to it instead of the [Enabled] setting next to other devices in the same menu. I can't scroll to the entry to manipulate this setting, and given my ignorance this is probably a good thing. Does this clue anyone in to why I'm not seeing my device? Please check the output below too. My chipset is realtek's 8187b (not listed below) and I've already seen every post you could link me to about reconfiguring/patching the driver. Thanks.
--------------------
matt@Darwin:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


matt@Darwin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by subzero316 on 2008-05-12
[QUOTE=scholzilla;4939020]I've been having a really difficult time getting my wifi up and running despite days on end reading various posts. Because device manager does not show a wireless device and because of the output below, I decided to check my BIOS settings to see if there was a clue. NOTE: This is a laptop with an internal wifi card that I can't touch. 

I don't know if this is normal, but under the Advanced tab in the BIOS menu, the wireless option is "greyed out" with the word [Restore] written next to it instead of the [Enabled] setting next to other devices in the same menu. I can't scroll to the entry to manipulate this setting, and given my ignorance this is probably a good thing. Does this clue anyone in to why I'm not seeing my device? Please check the output below too. My chipset is realtek's 8187b (not listed below) and I've already seen every post you could link me to about reconfiguring/patching the driver. Thanks.






What is your laptop model?
Try removing and inserting the wifi card and see if it changes in the BIOS.

---

### Post by scholzilla on 2008-05-12
Thanks.

The laptop model is gateway mt6452. The wifi card is internal, so I have no idea how to pull it out and reinsert.

---

### Post by Tomatz on 2008-05-12
You could just buy an inexpensive wireless usb adaptor that works out of the box. Like a cheap belkin one.

---

### Post by scholzilla on 2008-05-12
yeah, i think that's where this is heading...

---

### Post by shifty_powers on 2008-05-12
well your wireless card is definitely NOT listed in you pci list.

so tbh, try and restore it in the bios. I can pretty much guarantee you are not going to do anything irrecoverable to your laptop...

---

### Post by scholzilla on 2008-05-12
I don't know if this is normal, but under the Advanced tab in the BIOS menu, the wireless option is "greyed out" with the word [Restore] written next to it instead of the [Enabled] setting next to other devices in the same menu. I can't change it.

---

### Post by shifty_powers on 2008-05-12
then i guess tomatz has the right idea i'm afraid ;)

---


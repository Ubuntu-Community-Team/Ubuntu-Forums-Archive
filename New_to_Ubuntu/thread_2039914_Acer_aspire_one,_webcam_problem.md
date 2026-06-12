---
title: "Acer aspire one, webcam problem"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by stephenstephen on 2012-08-09
Hi all,

I am running Ubuntu 12.04 on my Acer aspire one, and the built-in webcam does not work. When I go into the skype options for video device, it tells me that there are no detectable webcams.

Is there anything I can do to fix this?

Thanks,
Stephen

p.s.
Before I started using Ubuntu, the webcam worked fine with windows.

---

### Post by stephenstephen on 2012-08-09
I have removed then reinstalled skype several times. 
I have looked through this forum and tried just about every terminal command people have put up.... nothing has worked. Skype opens, but the camera does not work.

Anyone know how to fix this?

Otherwise I am sadly going to remove ubuntu and go back to windows. 

Cheers.

---

### Post by Hadaka on 2012-08-09
Hi, try this

```
 gstreamer-properties 
```

choose the Video tab
then click TEST.....video

---

### Post by stephenstephen on 2012-08-10
Hi, thanks for responding.

I did as you suggested. 

Under DEFAULT OUTPUT DEVICE, it says; Unsupported

Under DEFAULT INPUT DEVICE, its says; None
(there are no other options to select to change these)

When I clicked TEST it says; Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'.

I installed cheese, and initially my webcam video was working. But it only worked the first time, now it says no device.

Any thoughts?

Thanks.

---

### Post by ajeannotte on 2012-08-12
this is the exact same problem i'm having with my lenovo sl500. cam works in windows, not even recognised in linux. 

i'm running the latest ubuntu, 12.04, but it hasn't worked in any of the previous versions either.

---

### Post by NikTh on 2012-08-13
Hi , 
please open a terminal(ctrl+alt+t) and give the results of these 2 commands

```
lspci -nnk 
lsusb
```
Put the results inside [CODE] tags , by highlighting the text and click the # symbol on top of message pane.

Another thing you must check , is a Function key (Fn) that turns on the camera. Some laptops (netbooks) has such key . e.g : Fn+F2 or another F . You can test it all. 

Thanks

---

### Post by ajeannotte on 2012-08-13
i had a look, there doesn't appear to be any function keys locking out the webcam. no issues in windows (i hate writing that, but it's true).

any help is VERY MUCH appreciated.



cheers

```
Laptop:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Lenovo Device [17aa:20e0]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Lenovo Device [17aa:20f1]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Lenovo Device [17aa:20f2]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Lenovo Device [17aa:20f0]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Lenovo Device [17aa:20f1]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Lenovo Device [17aa:20f6]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
	Subsystem: Lenovo Device [17aa:20f8]
	Kernel driver in use: ahci
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98 [GeForce 9300M GS] [10de:06e9] (rev a1)
	Subsystem: Lenovo Device [17aa:2107]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Lenovo Device [17aa:2108]
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
	Subsystem: Lenovo Device [17aa:2109]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
0d:00.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
	Subsystem: Lenovo Device [17aa:210a]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
0d:00.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
	Subsystem: Lenovo Device [17aa:210c]
	Kernel driver in use: r592
	Kernel modules: r592
0d:00.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
	Subsystem: Lenovo Device [17aa:210d]
	Kernel driver in use: r852
	Kernel modules: r852
Laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5c:2145 Broadcom Corp. Bluetooth with Enhanced Data Rate II
Bus 005 Device 003: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor


```

---

### Post by lincoln32 on 2012-08-13
not a lot of help But I did several acerones over the last few months
and had the same issue but I did trace it to a KeyBoard Switch 
(Fn + F4) Function and F4 at the same time as I recall but I do not have one in front of me but if you get us the model number we should be able to get a manual to verify how
:D

---

### Post by ajeannotte on 2012-08-13
> **ajeannotte said:**
> this is the exact same problem i'm having with my lenovo sl500. cam works in windows, not even recognised in linux. 

i'm running the latest ubuntu, 12.04, but it hasn't worked in any of the previous versions either.

as you can see, i said i had a problem with the exact same symptoms as the guy who originally posted this thread, but i am using a lenovo thinkpad, sl500 (that is now about 3 years old).

still no function key for the camera. Fn + F4 puts my computer to sleep.

---

### Post by NikTh on 2012-08-13
Hi , 
sorry but  i cannot handle 2 problems in one thread. Problem seems similar , but it is another Laptop , maybe different things applied. 
It will be nice to open your own thread @ajeannotte. 
I am waiting the OP to post the results of commands above , and see if Function Keys enable camera. 
Thanks

---


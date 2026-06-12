---
title: "Card reader not working"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by knightcoder on 2008-07-31
Hi all.
I have a HP Pavilion dv2000 laptop and I have a flash media card reader for SD and ProDuo cards. It worked in XP when I had dual boot. But about 6 months ago, I moved to Ubuntu and I've not been able to use it since.

I mostly use it to connect to pictures taken from my camera. I now have to connect my camera to the USB port. It'd be convenient to get it working again.

I'm using 8.04 and was thinking if there were any drivers out there to detect the card reader.

Thanks.

---

### Post by Atomic Dog on 2008-07-31
First things first.  Can you open a terminal and type: lspci and post the results?

---

### Post by knightcoder on 2008-07-31
Here it is : 

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

---

### Post by knightcoder on 2008-07-31
Oh yeah, I see the Ricoh Memory stick adapter.

So, now what, it recognizes the PCI device but it needs something else ???

---

### Post by Atomic Dog on 2008-07-31
I have the same card reader.  I can read/write to SD cards, but not XD or Memory stick.  

The bad news is the last time I looked xd was not supported, nor MS.  your searches should be aimed more at xd or whatever card you need supported on your system/laptop.  You might find a driver in development that will get it working.

A forum search might reveal something, but I found most all posts said "my SD card works but not (insert card type here)."

---

### Post by dima338 on 2008-07-31
I have the same laptop and the same problem...I tried sticking the MS Pro Duo by itself and then in a Memory Stick Duo adapter but it didn't work. SD cards work fine though as said earlier.

---

### Post by knightcoder on 2008-08-02
Hey, guys. Please, I still need help with my card reader.

---

### Post by aquamammal on 2008-11-23
Same Problem, 

Is there anyone that solved this?

Thanks~

---


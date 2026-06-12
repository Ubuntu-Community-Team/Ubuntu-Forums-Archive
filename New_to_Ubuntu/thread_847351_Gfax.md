---
title: "Gfax"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-02
I tried efax now I am trying Gfax and it says that it does not recognize the modem.

How can I get it to recognize the modem?

---

### Post by saskatchewan on 2008-07-02
After trying two faxes I got the messages that Modem not Responding and Fatal Error.

How can I get it to talk to the modem?

---

### Post by markjensen on 2008-07-02
I don't have *any* modem experience with Linux, but I think that if you post what model you have, it might help people.  Is it an internal card, or an external unit?  It might show up in an **lspci** command.  If it does, copy/paste that line here and others will know exactly what hardware you are dealing with.

---

### Post by saskatchewan on 2008-07-02
This is an ancient Dell Inspiron 7500 pentium 3.

---

### Post by saskatchewan on 2008-07-02
This is an ancient Dell Inspiron 7500 pentium 3.

---

### Post by markjensen on 2008-07-03
I was asking for the model of modem.   Since it is internal to your laptop, that is where the **lspci** command I mentioned earlier comes in.  ;)

It will tell you everything it sees for devices on its PCI bus.

---

### Post by saskatchewan on 2008-07-03
This is the result that I got from that commmand.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
00:10.0 Communication controller: Agere Systems WinModem 56k (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
02:00.0 Ethernet controller: Linksys 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

---

### Post by sicofante on 2008-08-12
I'm having the same problem. Mine is a Conexant based modem:

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
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
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
[B]02:07.0 Communication controller: Conexant Unknown device 10b4 (rev 89)
[/B]02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

I don't want to use efax-gtk (I find it plain horrible) and I've followed old threads about GFAX without success.

---


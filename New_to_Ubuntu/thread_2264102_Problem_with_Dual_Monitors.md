---
title: "Problem with Dual Monitors"
date: 2015-02-05
forum: New to Ubuntu
---

### Post by arjona.nicholas on 2015-02-05
Hello all,

I am very new to Ubuntu and Linux in general, so I apologize if what I'm asking is a dumb question. I did do research as to whether someone has had this problem before and none of their solutions worked. Anyways, I just set up my build with Ubuntu being the only OS on there. I used one monitor for the set up and all was groovy. Then I plugged in my 2nd monitor once I installed everything and it won't  come on. The Display settings does not even detect a 2nd monitor there. I installed ARandR and it does not detect a 2nd one either. I also checked for additional drivers and none showed up, is there another place to check for drivers to help? Any help would be very much appreciated.

Thanks

---

### Post by QIII on 2015-02-05
Hello!

It would be very helpful if we knew which release of Ubuntu you are using, as well as the OEM and model of your graphics adapter.

Cheers!

---

### Post by arjona.nicholas on 2015-02-05
I am using Ubuntu 14.04. I am not sure what you mean by OEM? And the graphics adapter is: **&#8203;**[Gigabyte GeForce GTX 750 2GB]("http://pcpartpicker.com/part/gigabyte-video-card-gvn750oc2gi")

---

### Post by sandyd on 2015-02-05
That card has been reported to have issues with nouveau - the default open source graphics driver due to its new maxwell arch. See [http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ](http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ) for details.

What you want is to install the latest propreitary drivers, those have been reported to work.

Go to the Unity Dash, type in 'drivers', and choose the first thing that comes up. - it should be named 'Additional Drivers'.

Install the latest proprietary drivers, and see if that improves things.

---

### Post by arjona.nicholas on 2015-02-05
> **sandyd said:**
> That card has been reported to have issues with nouveau - the default open source graphics driver due to its new maxwell arch. See [http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ](http://www.phoronix.com/scan.php?page=news_item&px=MTY0MzQ) for details.

What you want is to install the latest propreitary drivers, those have been reported to work.

Go to the Unity Dash, type in 'drivers', and choose the first thing that comes up. - it should be named 'Additional Drivers'.

Install the latest proprietary drivers, and see if that improves things.


When I go there, it states that there are no additional drivers available. Is there a way I can manually install the proprietary drivers?

---

### Post by sandyd on 2015-02-06
> **arjona.nicholas said:**
> When I go there, it states that there are no additional drivers available. Is there a way I can manually install the proprietary drivers?

Checked again - Seems like the newest drivers avaliable in Trusty are the 304 drivers - which don't seem to be new enough according to the nvidia site. The oldest drivers they have there are the 340 ones. Luckily, we can get newer ones in a PPA.

**Disclaimer:** The commands below add the xorg-edgers PPA to allow you to access updated drivers. However, packages in this PPA are not as well tested as those in the repositories and may make your system unstable.

See [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

Now, about installing the newer drivers...
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-346
sudo apt-get upgrade
```

Side note: Due to the nature of the terminal, please paste one line at a time - if you paste multiple, apt-get and add-apt-repository will interpret the additional lines as a input to any questions it may ask you.

---

### Post by taihsiangho on 2015-02-06
If you could not install a proprietary driver that is claimed to be supported by the graphic vendor, it is may be a bug of ubuntu-drivers.

Is it possible for you to provide your hardware information and let's see whether it is supported by the graphic vendor.
1. open the terminal by press (ctrl+t)
2. apply the command "lspci -nnvv"
3. paste the output of the above command to here.

---

### Post by arjona.nicholas on 2015-02-06
> **taihsiangho said:**
> If you could not install a proprietary driver that is claimed to be supported by the graphic vendor, it is may be a bug of ubuntu-drivers.

Is it possible for you to provide your hardware information and let's see whether it is supported by the graphic vendor.
1. open the terminal by press (ctrl+t)
2. apply the command "lspci -nnvv"
3. paste the output of the above command to here.


Here is the output:
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (external gfx0 port B) [1002:5a14] (rev 02)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:1709]
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Capabilities: <access denied>


00:04.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] RD890 PCI to PCI bridge (PCI express gpp port D) [1002:5a18] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fd000000-fe0fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000e1ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390] (rev 40) (prog-if 01 [AHCI 1.0])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:5503]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 19
	Region 0: I/O ports at f090 [size=8]
	Region 1: I/O ports at f080 [size=4]
	Region 2: I/O ports at f070 [size=8]
	Region 3: I/O ports at f060 [size=4]
	Region 4: I/O ports at f050 [size=16]
	Region 5: Memory at fe20b000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci


00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe20a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:12.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe209000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe208000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:13.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe207000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller [1002:4385] (rev 42)
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: piix4_smbus


00:14.1 IDE interface [0101]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c] (rev 40) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374
	Region 4: I/O ports at f000 [size=16]
	Kernel driver in use: pata_atiixp


00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:8228]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0


00:14.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge [1002:4384] (rev 40) (prog-if 01 [Subtractive decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-


00:14.5 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe206000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:15.0 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) [1002:43a0] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:15.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1) [1002:43a1] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: fe100000-fe1fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:15.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2) [1002:43a2] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Prefetchable memory behind bridge: 00000000e2100000-00000000e21fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport


00:16.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe205000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci-pci


00:16.2 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:3701]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe204000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci-pci


00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0 [1022:1600]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>


00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1 [1022:1601]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-


00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2 [1022:1602]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-


00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3 [1022:1603]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k10temp


00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4 [1022:1604]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: fam15h_power


00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5 [1022:1605]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750] [10de:1381] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:362e]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at e0000000 (64-bit, prefetchable) [size=32M]
	Region 5: I/O ports at e000 [size=128]
	Expansion ROM at fe000000 [disabled] [size=512K]
	Capabilities: <access denied>


01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device [1458:362e]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe080000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel


04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042] (prog-if 30 [XHCI])
	Subsystem: Biostar Microtech Int'l Corp Device [1565:6300]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe100000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:230e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 48
	Region 0: I/O ports at d000 [size=256]
	Region 2: Memory at e2104000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at e2100000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169

---

### Post by arjona.nicholas on 2015-02-06
> **sandyd said:**
> 
Now, about installing the newer drivers...
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers-346
sudo apt-get upgrade
```

Side note: Due to the nature of the terminal, please paste one line at a time - if you paste multiple, apt-get and add-apt-repository will interpret the additional lines as a input to any questions it may ask you.

Ok I ran this through the terminal and it seemed to run successfully, however, nothing happened afterward. I restarted my computer and looked in the Display options, but still no 2nd monitor appeared.

---

### Post by sandyd on 2015-02-06
> **arjona.nicholas said:**
> Ok I ran this through the terminal and it seemed to run successfully, however, nothing happened afterward. I restarted my computer and looked in the Display options, but still no 2nd monitor appeared.

Have you tried configuring it from the nvidia settings panel?
If you don't have it, run
```

sudo apt-get install nvidia-settings
```

to install.

---


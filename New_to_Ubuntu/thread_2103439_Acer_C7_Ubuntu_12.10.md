---
title: "Acer C7 Ubuntu 12.10"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by ToraxOutlaw on 2013-01-10
I'm having several issues with various things not working correctly in Ubuntu 12.10 on my Acer C710 Chromebook. I don't know whether this is the laptop or something that I have done myself. The internal microphone is muffled in Google+ and records static when using sound recorder. The other issue is that I have no sound at all when playing Minecraft. Any help would be appreciated.

---

### Post by Man OS on 2013-01-10
Hey !!

are u sure that your ubuntu gets correctly installed on chrome OS , actually there are some specific set of instructions which you should follow while installing ubuntu on chrome OS .

and 

also it can be some issues with compatibility also.

1) please report exactly what the error message was.

2) try out these commands like "dmesg", "lspci -vv" and "lsusb" and let me know what are the outputs.

3) is your webcam and sound are properly working ?

---

### Post by ToraxOutlaw on 2013-01-10
I used this guide to install Ubuntu 12.04 to my Acer C710 [Installing Ubuntu on Acer C7 Chromebook]("http://liliputing.com/2012/11/how-to-install-ubuntu-12-04-on-the-199-acer-c7-chromebook.html"). After this was completed I ran the Software Updater and updated it to Ubuntu 12.10. The Webcam and Sound work perfectly when I use Google+, Lovefilm after installing Moonlight and Youtube, so I can watch videos and stream videos to  it no problem. I get no error messages on the screen. In regards to Minecraft, I had to google to get a solution to fix the blackscreen, and I had to google an Alsa fix to get the microphone working at all. Even though I used the Alsa patch, my mic is muffled in Google+ and Sound Recorder just records static.


Outcome of lspci -vv command:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Intel Corporation 2nd Generation Core Processor Family DRAM Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 42
	Region 0: Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at e0705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 44
	Region 0: Memory at e0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e0400000-e04fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: e0600000-e06fffff
	Prefetchable memory behind bridge: 00000000e0500000-00000000e05fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e0705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
	Subsystem: Intel Corporation 7 Series Chipset Family LPC Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: nm10_gpio
	Kernel modules: nm10_gpio

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 43
	Region 0: I/O ports at 1060 [size=8]
	Region 1: I/O ports at 1070 [size=4]
	Region 2: I/O ports at 1068 [size=8]
	Region 3: I/O ports at 1074 [size=4]
	Region 4: I/O ports at 1040 [size=32]
	Region 5: Memory at e0705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at e0706000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0400 [size=32]
	Kernel driver in use: i801_smbus

00:1f.6 Signal processing controller: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller (rev 04)
	Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 139
	Region 0: Memory at e0704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
	Subsystem: Foxconn International, Inc. Device e052
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e0400000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at e0480000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 0742
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at e0500000 (64-bit, prefetchable) [size=64K]
	Region 2: Memory at e0510000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at e0600000 [disabled] [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0742
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at e0520000 (64-bit, prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci


Outcome of lsusb command:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0489:e04e Foxconn / Hon Hai 
Bus 001 Device 004: ID 064e:d251 Suyin Corp.

---

### Post by ToraxOutlaw on 2013-01-10
I can't get all the output from the dmesg command as there's too much information and the beginning/start is missing.

---

### Post by jacs102 on 2013-02-04
her is a work around for the mic issue . dont forget to click on speacker icon in upper right corner and turn input up to 100%
open a terminal and copy and paste one line at a time and enterget [http://www.cisgendered.com/~keyvin/mic-fix.deb](http://www.cisgendered.com/~keyvin/mic-fix.deb)
sudo dpkg -i mic-fix.deb
sudo shutdown -r now

---

### Post by jacs102 on 2013-02-04
sorry here it is again

wget [http://www.cisgendered.com/~keyvin/mic-fix.deb](http://www.cisgendered.com/~keyvin/mic-fix.deb)
sudo dpkg -i mic-fix.deb
sudo shutdown -r now

---

### Post by wlraider70 on 2013-02-04
Try this 

lspci -vv > verbose.txt

the ">" will put the output into that file.

---

### Post by ToraxOutlaw on 2013-02-05
lspci -vv > verbose.txt <----- what will this command do? And I will try the mic fix and see what happens.

EDIT: Tried the mic workaround and it works. Thanks guys for your help. I just help fixing all my Chromebook shortcut keys from F1 to F5. I've fixed the brightness keys and the volume keys work automatically, any suggestions on how to get the other shortcut keys working again?

---

### Post by ToraxOutlaw on 2013-02-06
Also how would I install Linux Mint on the Acer C7?

---

### Post by linux_author on 2013-02-16
install Linux Mint? if it's just to use the Mint desktop, simply install cinnamon, log out of your session, then choose cinnamon before logging back in - cinnamon will then become the defalut desktop manager

hth!

---

### Post by ToraxOutlaw on 2013-02-20
I've tried the cinnamon desktop it looks ok, I'm more interested to see if I can install Linux Mint on it.

---

### Post by ToraxOutlaw on 2013-04-19
Ok I have everything working now, I have the cinnamon desktop all good and running perfectly. But my bluetooth hasn't and doesn't work. How can I fix this?

---

### Post by avion540 on 2013-04-20
> **ToraxOutlaw said:**
> Ok I have everything working now, I have the cinnamon desktop all good and running perfectly. But my bluetooth hasn't and doesn't work. How can I fix this?

Would you mind sharing how you got all the shortcut keys working? Thanks!

---

### Post by ToraxOutlaw on 2013-04-20
I've only managed get the brightness shortcut keys to work. I just want to get the bluetooth to work, anyone have any ideas.

---

### Post by avion540 on 2013-04-20
How did you get the brightness shortcut keys to work? What happens when you try to pair your Chromebook with a bluetooth device?

---

### Post by ToraxOutlaw on 2013-04-20
I want send files via bluetooth to and from my phone. My phones bluetooth isn't finding any devices and the Ubuntu Bluetooth Setup just scans forever without finding anything.

In relation to the brightness settings just create 2 custom shortcuts within your keyboard settings.
First shortcut is to increase brightness. write in the command box xbacklight -inc 20% and set the key as F7
Second shortcut is to decrease brightness. write in the command command box xbacklight -dec 20% and set the key as F6

---

### Post by ToraxOutlaw on 2013-04-26
I've now updated to 13.04 and my bluetooth still is not working. Any ideas for me guys?

---

### Post by ToraxOutlaw on 2013-05-15
I've been googling this problem for a few weeks now to no avail. Does anyone have any ideas on how I can get the bluetooth to work on my Acer C7?

---


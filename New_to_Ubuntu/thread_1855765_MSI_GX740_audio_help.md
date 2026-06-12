---
title: "MSI GX740 audio help?"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Nexus18 on 2011-10-06
Hello everyone! I have a little problem. My current laptop, an MSI GX740, has had the hard drive fail recently and I took it as an excuse to finally install Ubuntu instead of Win7. The thing is im still quite new to Linux-based OS so without further ado, heres the problem. My computer has 5 speakers, two below the screen, two on sides below mouse pad and one sub on the bottom. The problem is, Ubuntu only plays sound from the sub. Ive tried playing around with ALSA and made a few tweaks to the default number of channels, all to no avail. Hopefully someone knows how to help me :p

Cheers,
Nexus

---

### Post by wolfen69 on 2011-10-06
Post the output of
```
lspci
```

---

### Post by Nexus18 on 2011-10-06
Here it is:
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Broadway XT [Mobility Radeon HD 5800 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
06:00.0 Network controller: Intel Corporation WiFi Link 5100
07:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
07:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

---

### Post by wolfen69 on 2011-10-06
See if [this]("https://help.ubuntu.com/community/SurroundSound") helps.

---

### Post by Nexus18 on 2011-10-06
Nothing, sub still only thing playing. I noticed in the preferences for hardware, the only options were:
Analog stereo input
Digital stereo duplex
Digital stereo output
Analog stereo output
Analog stereo duplex

No surround sound or anything else. :-k

---

### Post by wolfen69 on 2011-10-06
Do:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
then add the following (on it's own line)
*options snd-hda-intel index=0 model=acer-aspire-7730g*
close and save, then reboot.

---

### Post by Nexus18 on 2011-10-06
Yep, that did the trick. Thank you very much for your help! :D

---


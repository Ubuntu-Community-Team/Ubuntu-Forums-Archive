---
title: "Graphics Driver Problem"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by omgakos17 on 2013-05-12
I have changed graphics driver and then restarted for the changes to take effect but when my computer opened the display was of and it opened only with commands like terminal. I read a thread in this forum for it's solution that was saying to type "sudo rmmod nvidia" and another option to change Driver from "nvidia" to "nv" twice and when i restarted my computer it stucked on openning logo "ubuntu". Is there any solution for my problem or I 'll have to format my computer?

---

### Post by CatKiller on 2013-05-12
I don't know why you think formatting is an acceptable solution.

Some details about your hardware and what you actually did would help.

---

### Post by omgakos17 on 2013-05-19
i have an HP Pavilion dv8000  [Processor: Genuine Intel® CPU T2300 @ 1.66GHz × 2, Os typw : 32 bit, Graphics : still unknown but the type of the card is "nvidia geforce go 7400 and 7600", running on ubuntu 12.04 lts]. I hope those information helps you. I just changed the installation of graphics driver to one option of those that system let's me to choose and after i restarted my pc it started without display. Just terminal. I typed some commands and it sayd that there is a problem with display. I tried to unistall driver istallation so i can open display with some other commands I just read on the forum but none helped me. One the other side there has been a bigger disaster. The computer after restart was crashing on ubuntu logo when openning and the only thing that was working was the alt ctrl del combination for restart. I opened computer with recovery (safe mode) and i fixed the last problem but the graphics was the same. I had no problem to format it but there was some files i needed so i installed ubuntu again  without erasing the last installation i took the files and then format again by erasing everything. I still have problem with graphics driver because i have not find the driver that suits to ubuntu software.. Anyway my first problem solved but i would apreceate if you could inform me about the graphics problem. On additional drivers there are 3 options:  NVIDIA accelerated graphics driver (post-release updates)(version 173-updates), NVIDIA accelerated graphics driver (version current)[Recommended] and NVIDIA accelerated graphics driver (post-release updates)(version current-updates). I just use the recomended.

Sorry if my english are bad.

---

### Post by mastablasta on 2013-05-19
what CPU is that? does the laptop use Nvidia optimus technology? if so, you need bumblebee.

```
lshw 
```

to get the list of hardware in terminal. copy the result and post it here.

also copy and post result here from command 
```
lspci
```

---

### Post by CatKiller on 2013-05-19
Saying that you read something on a website somewhere and did something isn't terribly helpful unless you actually tell us what you did.

The GeForce Go 7300 is apparently supported by the 304 line of drivers, and earlier presumably, but discontinued later. I don't know how that lines up with the release of Ubuntu 12.04.

It's not clear from your messages so far whether you ever had your graphics working OK before you started fiddling.

---

### Post by omgakos17 on 2013-05-19
> **CatKiller said:**
> Saying that you read something on a website somewhere and did something isn't terribly helpful unless you actually tell us what you did.

The GeForce Go 7300 is apparently supported by the 304 line of drivers, and earlier presumably, but discontinued later. I don't know how that lines up with the release of Ubuntu 12.04.

It's not clear from your messages so far whether you ever had your graphics working OK before you started fiddling.

I know that this way of answer doesent helps you and I am realy sorry about it but i did my try to fix this some weeks ago and i dont remember clearly what i did or the commands I used. I could search to find the links from the posts that i read and act if this will help you. I used the 304 line too and I think that there was the problem. Now i do not have the 304 as an option on additional drivers. I am gonna search for the links and then post them here but I may be a little late because I  don't have much time. So I ask for you to be patient. Enyway thanks for trying to help.

---

### Post by omgakos17 on 2013-05-19
> **mastablasta said:**
> what CPU is that? does the laptop use Nvidia optimus technology? if so, you need bumblebee.

```
lshw 
```

to get the list of hardware in terminal. copy the result and post it here.

also copy and post result here from command 
```
lspci
```

I dont really know if it's using Nvidia optimus technology but i know that my graphics card is Nvidia GeForce go 7400 or 7600 they use the same driver on windows i had before.
**So the result of the first command is: **
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1508MiB
     *-cpu
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm dtherm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:d0000000-d1ffffff ioport:c0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72M [GeForce Go 7400]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:d1000000-d1ffffff memory:c0000000-cfffffff memory:d0000000-d0ffffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:d2400000-d2403fff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:64000000-641fffff ioport:64200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:64400000-645fffff ioport:64600000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:64800000-64afffff ioport:64b00000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 02
                serial: 00:13:02:34:84:6c
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.5.0-30-generic firmware=15.32.2.9 ip=192.168.1.5 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:45 memory:64800000-64800fff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1800(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1820(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1840(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1860(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d2404000-d24043ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d2000000-d20fffff ioport:60000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCIxx12 Cardbus Controller
                vendor: Texas Instruments
                physical id: 6
                bus info: pci@0000:08:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:18 memory:d2004000-d2004fff ioport:2400(size=256) ioport:2800(size=256) memory:60000000-63ffffff memory:68000000-6bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCIxx12 OHCI Compliant IEEE 1394 Host Controller
                vendor: Texas Instruments
                physical id: 6.1
                bus info: pci@0000:08:06.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:19 memory:d2007000-d20077ff memory:d2000000-d2003fff
           *-storage
                description: Mass storage controller
                product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
                vendor: Texas Instruments
                physical id: 6.2
                bus info: pci@0000:08:06.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: driver=tifm_7xx1 latency=64 maxlatency=4 mingnt=7
                resources: irq:22 memory:d2005000-d2005fff
           *-generic
                description: SD Host controller
                product: PCIxx12 SDA Standard Compliant SD Host Controller
                vendor: Texas Instruments
                physical id: 6.3
                bus info: pci@0000:08:06.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64 maxlatency=4 mingnt=7
                resources: irq:20 memory:d2007800-d20078ff
           *-network
                description: Ethernet interface
                product: PRO/100 VE Network Connection
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:08:08.0
                logical name: eth0
                version: 01
                serial: 00:16:d4:01:27:5f
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=66 maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:d2006000-d2006fff ioport:2000(size=64)
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1880(size=16)
        *-storage
             description: SATA controller
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:18c8(size=8) ioport:18ac(size=4) ioport:18c0(size=8) ioport:18a8(size=4) ioport:18b0(size=16) memory:d2404400-d24047ff
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4082N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: CQ04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage

**And from the second command: **

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

I hope that information helps you.

---

### Post by CatKiller on 2013-05-19
If the 304 caused you problems it's probably not worth hunting them down.

What state is your computer in at the moment?

---

### Post by omgakos17 on 2013-05-19
Now it works normaly. I have only two issues. One with the cursor, I have made a new thread and the other is that the graphics driver isn't displayed on details and i cannot change display analysis on Desktop neither on the game that i have downloaded by steam "Counter Strike". On the game there is only an option of graphics "Opengl" and only 1440X900.

---

### Post by CatKiller on 2013-05-20
That sounds fairly standard to me.

---

### Post by omgakos17 on 2013-05-21
ok so i should leave it as well.! Thank you very much for your help. i will post here the information you asked me yesterday as soon as i get them! Thank you again!

---


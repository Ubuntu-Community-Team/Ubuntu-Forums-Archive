---
title: "Problems with Presario v3000 on 11.04"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by rbales427 on 2012-01-07
I recently inherited this computer. The problem is since I installed Ubuntu, the computer will randomly freeze and runs very slow. I have a feeling it has to do with the age of the computer, ir it is overheating. But the person I recieved it from said that they recently changed the fan so I dont think that is the issue. Would anyone suggest something I could do to fix this? Is there a way to downgrade to a version that is comperable? And how would I go about doing that? Thanks in advance.

---

### Post by wildmanne39 on 2012-01-07
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
sudo lshw
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by rbales427 on 2012-01-07
[QUOTE=wildmanne39] ```
  *-core
       description: Motherboard
       product: 30B5
       vendor: Wistron
       physical id: 0
       version: 62.61
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.39
          date: 11/22/2007
          size: 96KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.8.2
          slot: U1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 256KiB
             capacity: 2MiB
             capabilities: synchronous external write-back
     *-memory:0
          description: System Memory
          physical id: 1
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: M2
             size: 512MiB
             width: 32 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 6
          bus info: cpu@1
          version: 15.8.2
          size: 1600MHz
          capacity: 1600MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 memory:b3000000-b30fffff
        *-network
             description: Network controller
             product: BCM4311 802.11b/g WLAN
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=b43-pci-bridge latency=0
             resources: irq:19 memory:b3000000-b3003fff
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 ioport:4000(size=4096) memory:b4000000-b7ffffff ioport:d0000000(size=2097152)
     *-display
          description: VGA compatible controller
          product: C51 [GeForce Go 6150]
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:21 memory:b2000000-b2ffffff memory:c0000000-cfffffff memory:b1000000-b1ffffff memory:40000000-4001ffff
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3040(size=64) ioport:3000(size=64)
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP51 PMU
          vendor: nVidia Corporation
          physical id: a.3
          bus info: pci@0000:00:0a.3
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:b0040000-b007ffff
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:18 memory:b0004000-b0004fff
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:b0005000-b00050ff
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi1
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:3080(size=16)
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GMA-4082N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: HQ04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          logical name: scsi2
          version: f1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30b0(size=8) ioport:30a4(size=4) ioport:30a8(size=8) ioport:30a0(size=4) ioport:3090(size=16) memory:b0006000-b0006fff
        *-disk
             description: ATA Disk
             product: FUJITSU MHV2100B
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 892C
             serial: NW12T662BK38
             size: 93GiB (100GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0001904d
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: b8cc4ce2-7382-43db-836d-7ec30e4daf0f
                size: 92GiB
                capacity: 92GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2004-07-19 11:22:41 filesystem=ext4 lastmountpoint=/ modified=2012-01-06 19:28:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,commit=600,barrier=1,data=ordered mounted=2012-01-07 14:21:07 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 957MiB
                capacity: 957MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 957MiB
                   capabilities: nofs
     *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: memory:b8000000-b80fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 9
             bus info: pci@0000:05:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:16 memory:b8000000-b80007ff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.1
             bus info: pci@0000:05:09.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64
             resources: irq:23 memory:b8000800-b80008ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.2
             bus info: pci@0000:05:09.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r592 latency=0
             resources: irq:23 memory:b8000c00-b8000cff
        *-generic:2
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 9.3
             bus info: pci@0000:05:09.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=r852 latency=0
             resources: irq:23 memory:b8001000-b80010ff
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corporation
          physical id: 10.1
          bus info: pci@0000:00:10.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:b0000000-b0003fff
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:d3:05:31:23
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.15 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:17 memory:b0007000-b0007fff ioport:30b8(size=8)
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:ad:10:61
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-14-generic firmware=508.1084 link=no multicast=yes wireless=IEEE 802.11bg
```[/QUOTE]
Here you are.

---

### Post by wildmanne39 on 2012-01-07
Hi, I have a computer like that it has the same cpu in a laptop, mine likes to run warm so I have a cooling pad with fans that I use at all times.

The computer does not have much memory that could be causing the slowness, but it depends on what version of ubuntu you are using.
Please show:
```
cat /etc/lsb-release; uname -a
```
```
lspci | grep VGA
```
Thanks

---

### Post by rbales427 on 2012-01-07
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ryan-Presario-V3000-EZ675UA-ABA 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux
```

```
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)

```

---

### Post by rbales427 on 2012-01-07
[QUOTE=wildmanne39][/QUOTE]Anything? I also have some other questions for you if you could help.

---

### Post by wildmanne39 on 2012-01-07
Hi, for slowness do what this link says and it should take care of the problem as much as it can running unity on your older system.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Also you could log out and click on your user name then go to the bottom of the screen and chose classic no effects and you should have much improved performance.
Thanks

---

### Post by rbales427 on 2012-01-07
> **wildmanne39 said:**
> Hi, for slowness do what this link says and it should take care of the problem as much as it can running unity on your older system.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Also you could log out and click on your user name then go to the bottom of the screen and chose classic no effects and you should have much improved performance.
Thanks
Awesome! Thanks for the assistance. I truly appreciate it. I also have another question for you if you can help. I had the Broadcom 43xx issue which I had to resolve with this setup:

[http://ubuntuforums.org/showthread.php?t=1905753](http://ubuntuforums.org/showthread.php?t=1905753)

```
sudo modprobe b43
```

Every time I turn the computer on, I have to input the code again. I want to know if there is a permanent fix for this so I don't have to do it every time. I tried blacklisting like he said. Thanks for the help again!!

---

### Post by wildmanne39 on 2012-01-07
Hi, yes here it is:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
When your original question is resolved please use thread tools to mark the thread solved.

Also you should use a descriptive title for your thread and only one issue per thread please, it helps other people looking for the same answer as you find it easier.
Thanks

---

### Post by rbales427 on 2012-01-07
> **wildmanne39 said:**
> Hi, yes here it is:
```
sudo su 
echo b43 >> /etc/modules 
exit
```When your original question is resolved please use thread tools to mark the thread solved.

Also you should use a descriptive title for your thread and only one issue per thread please, it helps other people looking for the same answer as you find it easier.
Thanks
Will do. Thanks again for the help.

---


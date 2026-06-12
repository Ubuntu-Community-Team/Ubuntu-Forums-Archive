---
title: "Ubuntu 11.10"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by priority on 2012-01-05
Hi,

I d like to use the latest version but I didn't like it's look and its performance.. I installed and it slowed down my laptop. Also gnome 3 was not good for me. After some hours I installed 11.04 .. 11.04 is good. 

Is there anyone had problems with 11.10  like me ? It s really slow to open programs, documents, folders.. Also it freezes sometimes.. It has lag to open anything . It takes time to respond apps.. Etc. Even after installed updates it keeps giving problems as I said..

Also 11.04 has some performance problems, it slows sometimes and lagging while opening apps, folders, docs.. Is there way to speed up it ?

Another q. Is there any way to turn it to look exactly like 11.04 Ubuntu classic with no effects ? 
 
- both panel same color, no transparent in middle
- date and time on left up panel not in middle 
- and direct restart tab. when press on power icon
...etc

I was a windows user for years, I like Ubuntu too but sometimes it makes me feel it has many bugs inside and doesn't make me feel secure.. Free and open source shouldn't mean to be cheap and not useless.. I d like to see more powerful Ubuntu as an OS.

---

### Post by grahammechanical on 2012-01-05
If you do not like cheap, then you should send a $300 to .....

---

### Post by Basher101 on 2012-01-05
have you even considered that your laptop is not 100% perfectly supported by ubuntu? also some of the newer kernels have some bugs. That is why ppl who want stability use the Ubuntu 10.04 LTS (Long Term Support) version as it has only a few changes to ensure maximum stability. Also what are your system specs? you laptop may not handle the 3D Desktop Environments..

---

### Post by collisionystm on 2012-01-05
your computer is probably old and slow.

What are the specs? Make model?

---

### Post by Alphamonkey on 2012-01-05
I am running ubuntu 11.10 on my Eee PC. I had to switch to it because windows 7 ran so slowly on it. I do have some of there errors and glitches but that is because it is not the (LTS) version. You can switch to the "Classic" view of gnome 2. I currently have KDE plasma, Gnome 3, and classic gnome interfaces installed. Thats one of the things I love about ubuntu. I can freely switch between user interfaces.

---

### Post by chipbuster on 2012-01-05
It's a sad fact that we often can't have both the latest technology and perfect stability.

Also, I can say that on the various systems I've tested Ubuntu on (in 2 months), I've found Ubuntu to have an equal number of bugs as Windows. Of course, some Ubuntu bugs are fatal, but the OS has such a hilariously fast boot time that I can reboot the computer in the time it'd take to open task manager in Win7.

---

### Post by sandyd on 2012-01-05
> **priority said:**
> Hi,

I d like to use the latest version but I didn't like it's look and its performance.. I installed and it slowed down my laptop. Also gnome 3 was not good for me. After some hours I installed 11.04 .. 11.04 is good. 

Is there anyone had problems with 11.10  like me ? It s really slow to open programs, documents, folders.. Also it freezes sometimes.. It has lag to open anything . It takes time to respond apps.. Etc. Even after installed updates it keeps giving problems as I said..

Also 11.04 has some performance problems, it slows sometimes and lagging while opening apps, folders, docs.. Is there way to speed up it ?

Another q. Is there any way to turn it to look exactly like 11.04 Ubuntu classic with no effects ? 
 
- both panel same color, no transparent in middle
- date and time on left up panel not in middle 
- and direct restart tab. when press on power icon
...etc

I was a windows user for years, I like Ubuntu too but sometimes it makes me feel it has many bugs inside and doesn't make me feel secure.. Free and open source shouldn't mean to be cheap and not useless.. I d like to see more powerful Ubuntu as an OS.
Whats your computer's specs?
You can dump it back to the 11.04 Classic look with [http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

---

### Post by wildmanne39 on 2012-01-05
Hi, please post the results of:
```
sudo lshw
```
Thanks

---

### Post by priority on 2012-01-06
> **grahammechanical said:**
> If you do not like cheap, then you should send a $300 to .....

heyy , by which organ are you reading my post ?

---

### Post by priority on 2012-01-06
System Specs :

Lenovo ThinkPad Edge 13" ( ubuntu certified computer )
[http://www.ubuntu.com/certification/hardware/201011-6824:201101-6964:201103-7450](http://www.ubuntu.com/certification/hardware/201011-6824:201101-6964:201103-7450)

Intel Core2Duo U7300 1.30 GHz
4GB DDR3 RAM
128MB Intel GMA


> **wildmanne39 said:**
> Hi, please post the results of:
```
sudo lshw
```
Thanks

here :

 description: Notebook
    product: 01962ZG ()
    vendor: LENOVO
    version: ThinkPad Edge
    serial: xxxx
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ThinkPad Edge frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled uuid=3B4CAE81-5009-11CB-8E49-B256A8E35ADA
  *-core
       description: Motherboard
       product: 01962ZG
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZGX201K15M
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 6YET36WW (1.19 )
          date: 06/15/2011
          size: 111KiB
          capacity: 1984KiB
          capabilities: pci pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Genuine Intel(R) CPU           U7300  @ 1.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: CPU Version
          slot: U2E1
          size: 1300MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 3MiB
             capacity: 4MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: EBJ21UE8BDS0-AE-F
             vendor: AMI
             physical id: 0
             serial: 2F8316D8
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: Micron Technology
             physical id: 1
             serial: DE4F8400
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f0000000-f03fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0400000-f04fffff
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f0804800-f0804bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f0800000-f0803fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:c0000000-c01fffff ioport:c0200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:f0500000-f05fffff ioport:c0400000(size=2097152)
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: 90:4c:e5:e0:f1:50
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.18 latency=0 link=yes multicast=yes wireless=802.11bgn
                resources: irq:17 ioport:2000(size=256) memory:f0500000-f0503fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=4096) memory:c0600000-c07fffff ioport:c0800000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=4096) memory:c0a00000-c0dfffff ioport:f0900000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 03
                serial: 00:26:9e:e4:40:a1
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:44 ioport:3000(size=256) memory:f0904000-f0904fff memory:f0900000-f0903fff memory:f0920000-f093ffff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0804c00-f0804fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:1818(size=8) ioport:180c(size=4) ioport:1810(size=8) ioport:1808(size=4) ioport:18e0(size=32) memory:f0804000-f08047ff
           *-disk
                description: ATA Disk
                product: HITACHI HTS54503
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: PB3Z
                serial: 091213PBNC041YG45G6R
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=252ee3dd
              *-volume
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 60066541-f396-489a-bed7-5a101e4650a6
                   size: 298GiB
                   capacity: 298GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-01-05 18:18:58 filesystem=ext4 lastmountpoint=/ modified=2012-01-05 18:25:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2012-01-06 13:39:40 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0e00000-c0e000ff ioport:1c00(size=32)
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi0
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sdb

---

### Post by priority on 2012-01-06
> **sandyd said:**
> Whats your computer's specs?
You can dump it back to the 11.04 Classic look with [http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/](http://www.omgubuntu.co.uk/2011/12/how-to-make-ubuntu-11-10-look-and-feel-like-gnome-2/)

thank you for gnome 2 info.

---

### Post by wildmanne39 on 2012-01-06
Hi, in my opinion with your system specs you should use classic or classic with no effects, or you can install lubuntu or xubuntu instead they both require less resources.
Thanks

---


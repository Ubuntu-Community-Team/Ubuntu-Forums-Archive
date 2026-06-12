---
title: "Hardy Heron and Toshiba Realtek networking woes"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by lrbradford on 2008-05-01
HI guys! Can I jump in here with my issues? I have tried some of these commands **(BOLD)**and saved my terminal's output. First, some background:

Toshiba A215 AMD 64 2x with a Realtek network onboard

snip 8<--------------------

lynn@lynn-laptop:~$ sudo **lshw -C network **
[sudo] password for lynn: 
*-network 
description: Ethernet interface 
product: RTL8101E PCI Express Fast Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:08:00.0 
logical name: eth0 
version: 01 
serial: 00:a0:d1:84:8a:26 
capacity: 1GB/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair 
lynn@lynn-laptop:~$ **iwconfig** 
lo no wireless extensions. 

eth0 no wireless extensions. 

lynn@lynn-laptop:~$ **ifconfig** 
eth0 Link encap:Ethernet HWaddr 00:a0:d1:84:8a:26 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:252 Base address:0x2000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:262 errors:0 dropped:0 overruns:0 frame:0 
TX packets:262 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:14300 (13.9 KB) TX bytes:14300 (13.9 KB) 
snip 8<-------------------------

Any ideas, please enlighten me. This is a dual boot with Vista and Ubuntu 8.04.  I am currently on the road, and won't be able to run these commands while wired to my router.  The output above was from sitting in my hotel room to the hotel wireless, which the Vista OS connects fine at home and at the hotel wirelessly.  I don't think I have ever tried wired to the router at home.  No need.

Thanks in advance for any help for this old newby!:guitar:
------------------------------------------------------------------------------------

chili555 responded with:

@Irbradford

I think you are better to start your own thread. When you do, post all you have here and try to get at least some information about your wireless card, with lspci or lsusb or, worst case, tell us whatever you can by looking at it: make, model, version, etc. 

It is your wireless you are trying to get going, isn't it?
__________________
Registered Linux User #374501

---

### Post by lrbradford on 2008-05-01
OK.  I ran the commands Chilli suggested - lspci and lsusb.  Those results are pasted below:

snip 8<---------------------------------------------

lynn@lynn-laptop:~$ **lspci**

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge

00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)

00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)

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

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

14:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

14:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

lynn@lynn-laptop:~$ **lsusb**

Bus 004 Device 001: ID 0000:0000  

Bus 005 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 006 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 

Bus 001 Device 001: ID 0000:0000  

snip 8<-----------------------------------------------------

Again folks, this is with wireless ONLY available right now.  When I get back home, I can run a cable to my router and re-run all of these commands to see if something different comes up.

Thanks in advance!

LB

---

### Post by tyroeternal on 2008-05-01
Okay, I've done a lot of digging around and its not sounding good for that laptop.

[This]("http://ubuntuforums.org/showthread.php?p=3816581&page=4") thread sounds like it is coming from your hardware and he was unable to get things working.  (Also take note that he bought a pcmcia card and found that his laptop didn't support that kind of card)

Hopefully you have the laptop that [this]("http://ph.ubuntuforums.com/showthread.php?t=715301") guy has, because it seems to be able to be poked into a working state.

I've had lots of trouble in the past with non-functional wireless cards, so for the time being going wired or getting another wireless card/usb solution may be the only option)

If a wireless card/usb solution is something you are interested in, make sure you check out the wiki's page for [wireless card compatability]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

In any case, best of luck!

---

### Post by lrbradford on 2008-05-01
Hmm...I found that my Toshiba Satellite A215-S7414 has a Realtek RTL8101E PCI Express Fast Ethernet controller, courtesy of the lshw -C network command.  I am bothered that the iwconfig command returned both lo and eth0 "no wireless extension".  What that means is still a mystery. 

I found in the link above to another thread that Realtek has drivers for there controllers, so I went to Realtek and found that drivers for my RTL8101E is "Linux driver (driver has built-in the kernel)".

SO does this mean I need to blacklist a default driver in Ubuntu like I had to when I had an old Dell with a PCMCIA card.  Wish I knew...a little help fellas!!

LB

---

### Post by tyroeternal on 2008-05-02
From what I've gathered about your hardware just in searching around...

Your wired network controller as found through lspci
> product: RTL8101E PCI Express Fast Ethernet controller 

Your wireless controller is actually a completely different entry as indicated by lsusb:
> Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

There does not seem to be anyone able to get drivers working for the 8197 at the moment, but I'll keep searching this weekend.

I could be very wrong about this being your wireless controller.  However, from all the different threads I've found this seems to be the general consensus.

---

### Post by lrbradford on 2008-05-02
Ok people.  I changed hotels, and they only have a wired network.  I plugged in, connected with my Vista first, restarted into Hardy.  I got on the NEt!!  What the heck?  What commands should I run now??  I did an update, and saw where lshw was one of the updates.  I ran that command as sudo, and got a heck of a listing.

lynn@lynn-laptop:~$ sudo lshw
[sudo] password for lynn: 
lynn-laptop               
    description: Computer
    product: Satellite A215
    vendor: TOSHIBA
    version: PSAFGU-01V015
    serial: XXXXXXXXXXXX
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
       description: Motherboard
       product: SB600
       vendor: ATI
       physical id: 0
       version: Rev 1
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.00 (08/27/2007)
          size: 112KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-55
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.8.1
          slot: Socket M2/S1G1
          size: 1800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: H0 L2 Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list
                configuration: latency=64
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 01
                serial: 00:a0:d1:84:8a:26
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.59.1.2 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: Hitachi HTS54168
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: SB2O
                serial: SB2241KGHD354S
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6be8f641
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 8cf5-1f7a
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2008-04-28 10:12:56 filesystem=ntfs label=TOSHIBA SYSTEM VOLUME state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 381d5eff-9858-bf44-a99f-d1fc848e4032
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-04-28 10:13:05 filesystem=ntfs label=SQ004513V03 modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 35GiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 1600MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ-850S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.21
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:14:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:14:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci latency=32 module=sdhci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:14:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:14:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:14:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
lynn@lynn-laptop:~$ 

I hope you gurus out there can make sense of it.  I'm baffled that the wired works here but not at my home when I hooked up a cablem unless that cable is bad that I used there?  I'll use this one when I get home.  But back to wireless:  why doesn't it work???

LB

---

### Post by kwacka on 2008-05-02
These should help:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)  (see Realtek 8187 comments)

---

### Post by chili555 on 2008-05-02
Before you do anything drastic, and since you know the wired works, I'd check at home first. If you can connect, let's mark it 'case closed' and move on to wireless. If not, we can troubleshoot.

---

### Post by tyroeternal on 2008-05-02
DOH! My bad, I completely pasted the wrong line for what I said your ethernet card was, IM SORRY!

I'm not sure why wired would not work at home, hopefully it magically works when you get back as well :D

Your problem with the wireless is that the 8197 Realtek card shown when you run **lsusb** is what controls your wireless, not the RTL8101E PCI Express Ethernet controller.  At this point its just a matter of finding the driver to make your 8197 card work.  I still haven't found a solution for that card but the search will continue.  Hopefully someone out there has found a way to make it work.

---

### Post by lrbradford on 2008-05-04
OK, I checked my hardware drivers while in Vista (DOH!) and it says I have a RTL8187B wireless.  I checked the Realtek website and fond a Linux driver for kernal 2.6.22 dated 12/27/2007.  I downloades it to my Vista hard drive, and noticed it saved it as a tar.gz.  Is that OK, or is it a way for Winders to mess things up?

I'm going to go to my Linux load and see what develops over there.

Wish me luck!

LB

---

### Post by tyroeternal on 2008-05-04
Very cool.  Hopefully it works!

.tar.gz is a typical compressed format that linux works with (just like .zip files)

---

### Post by lrbradford on 2008-05-05
Well, Tyro, I did get my wired connection to work from home.  As for the wireless, no such luck.  I used ndisgtk and the Windows .inf file to create a driver, but when I go into System > Administrator > Network, I only show wired and modem as an option.

I downloaded the Linux driver - the only one they showed - but I am not sure of the commands I need to use from terminal to get those unzipped to the correct location, and so forth.  I was hoping that when I clicked on the file, and unzip comes up, it would ask me to install, but I guess it is as dumb as me!  The file name is:

rtl8185_linux_26[1].1027.0823.2007.tar.gz

SO if you care to give me a hand on using these, I'll go back and uninstall the driver created my ndisgtk and see how this one flies!  My Ubuntu Linux Bible does not sound to encouraging.  It says that if my wireless doesn't show up in network, it may not be supported by the kernal.  DO I need to download the kernal headers?  Is that the term?  Or see if they exist on my laptop?

Thanks in advance,

LB

---

### Post by tyroeternal on 2008-05-06
Since your vista drivers said it was the RTL8187B card I just wanted to make sure that you tried the method for getting those drivers working that was mentioned earlier.

> **kwacka said:**
> [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)  (see Realtek 8187 comments)

Aside from that, the download that you have linked to appears to be the 8185 driver, not the 8187b driver.

Give that guide a try (you have to scroll a ways down the page to see the section for your card) and let me know how things turn out.  Hopefully in the next day or so here we can get it all figured out!

---

### Post by lrbradford on 2008-05-06
I'm back at the hotel in Toledo, OH.  They have wireless, so I am pretty much stuck on the Vista side of the laptop and bouncing back to Ubuntu to try stuff.

To recap, I was able to connect wired to my router with Ubuntu, but no luck on wireless.  I printed out the guide Tyro sent me pertaining to mods to get the included drivers for the 8185 1nd 8187 to work.  I'll play with it to see what happens.  My questions is, if I get it modified for Linux, will it be screwed up for Vista wireless or even the wired side??

---

### Post by tyroeternal on 2008-05-06
You will not hurt your vista install by trying to get your linux side up and running.

---

### Post by lrbradford on 2008-05-12
OK.  I'll give that a try.  I can't find my notes at the moment, but when I ran the lshw -C network command, something other than 8187 came up.  I'm thinking it was the 8101.

---

### Post by tyroeternal on 2008-05-13
Yes, it was 8101, but that was for your wired network controller.  When you ran lsusb it showed that your wireless network controller was the 8197 card.  I haven't been able to find a working driver for the 8197.  Since you said vista was using what appeared to be 8187b drivers for your wireless, I would follow the guide for that driver and see what happens :).

---

### Post by lrbradford on 2008-06-30
Hi Tyro,

I finally got a chance to try the kevdog procedure for getting my wireless interface to work on this Toshiba.  So far, not so good.

Right off: I typed in 
[B]sudo modprobe r818x
sudo modprobe r8187[/B]

What I got for each one was: **FATAL: Module r818x not found** The same message for the r8187.

NO mention in the steps as to what to do next in the case of this error.

Any suggestions?  I'll search around and see if there have been any new posts on how to get this thing working.  Ubuntu has had a few updates as well.

Thanks in advance,

LB

---

### Post by mbarvian on 2008-06-30
Hi, I have a similar laptop as you, and the same wireless chipset (RTL8187b).  As long as you don't have an encryption on the wireless, you can use the first section of this guide:

[http://ubuntuforums.org/showthread.php?t=839108&highlight=a215](http://ubuntuforums.org/showthread.php?t=839108&highlight=a215)

Hope this helps!

---

### Post by lrbradford on 2008-06-30
Well, I tried your suggestion and no wireless shown in Network Manager.  When I went to SYSTEM > ADMIN > WINDOWS WIRELESS DRIVERS, and it says: hardware present NO.

Now what, kind sir?

LB

---


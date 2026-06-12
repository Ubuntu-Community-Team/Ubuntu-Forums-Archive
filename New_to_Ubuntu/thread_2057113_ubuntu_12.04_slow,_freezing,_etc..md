---
title: "ubuntu 12.04 slow, freezing, etc."
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Velenjak on 2012-09-13
hello, i recently upgraded to 12.04 from an earlier version (8.10 or 9.10 i forgot) after doing a clean wipe and install. programs that i used previously are now performing very laggy, and when i multitask the computer will often totally freeze up. its not pleasant in its current state..

i was wondering if you guys know any way to "lighten" 12.04 so it works cleaner on my computer. thanks

---

### Post by shreepads on 2012-09-13
What's the machine spec?

---

### Post by Velenjak on 2012-09-13
3.2 gb ram
Intel pent 4 CPU 3.20ghz x 2
128 mb graphics card.

---

### Post by shreepads on 2012-09-13
Can you post the file created by:

sudo lshw -html -sanitize > hardwarespecs.html

---

### Post by Velenjak on 2012-09-13
the only message that comes up is 

PCI (sysfs)

---

### Post by shreepads on 2012-09-14
> **Velenjak said:**
> the only message that comes up is 

PCI (sysfs)

It should have created a file named hardwarespecs.html in the working folder where you were running the command from the terminal.

Actually wait, this forum doesn't allow upload of HTML format files, so could you please re-run as follows:

```
$ cd ~
$ sudo lshw -sanitize > hardwarespecs.txt
```

You should see a file named hardwarespecs.txt in your home directory, pls upload that file. (It contains the complete hardware specs, sanitized of information such as serial nos.)

---

### Post by Velenjak on 2012-09-14
Thanks for your help by the way,


computer
    description: Mini Tower Computer
    product: Dimension 8400
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0U7077
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A04
          date: 01/10/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.3
          serial: [REMOVED]
          slot: Microprocessor
          size: 3200MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 3584MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82925X/XE Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82925X/XE PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:dfd00000-dfefffff memory:d0000000-d7ffffff
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:43 memory:d0000000-d7ffffff ioport:dc00(size=256) memory:dfde0000-dfdeffff memory:dfe00000-dfe1ffff
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:dfdf0000-dfdfffff
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:dfc00000-dfcfffff ioport:d8200000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5751-v3.23a ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:16 memory:dfcf0000-dfcfffff
        *-pci:2
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:1000(size=4096) memory:dfb00000-dfbfffff ioport:d8000000(size=2097152)
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:dfa00000-dfafffff
           *-communication
                description: Modem
                product: FA82537EP 56K V.92 Data/Fax Modem PCI
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@0000:04:02.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:18 memory:dfaff000-dfafffff ioport:cc00(size=256)
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:23 ioport:ec00(size=256) ioport:e8c0(size=64) memory:dffffa00-dffffbff memory:dffff900-dffff9ff
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-storage
             description: SATA controller
             product: 82801FR/FRW (ICH6R/ICH6RW) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:dffffc00-dfffffff
           *-disk
                description: ATA Disk
                product: ST3160023AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 8.12
                serial: [REMOVED]
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=eb275b50
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: [REMOVED]
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-03-05 00:11:34 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: [REMOVED]
                   size: 84GiB
                   capacity: 84GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-03-05 00:11:38 filesystem=ntfs state=clean
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 64GiB
                   capacity: 64GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 6236MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 58GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH22NS50
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                logical name: /media/New
                version: TN03
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/New
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:e8a0(size=32)

---

### Post by shreepads on 2012-09-14
Can you edit that last post to put CODE tags around the output?

> [CO DE]
<output from lshw>
[/CO DE]

Pretty unreadable right now...

Also in your last post you had mentioned

Intel pent 4 CPU 3.20ghz **_x 2_**

Which is why I asked for this detail, can't see a 2nd CPU in there, just one single core one.

I don't think a Pentium 4 and a Radeon X300 will sustain Ubuntu 12.04...

You could try Lubuntu 12.04, but really if you want a modern OS that will be snappy on this hardware, you should go for Puppy Linux IMHO.

---

### Post by shreepads on 2012-09-14
Ahhh it has Hyper-Threading, so single core but probably appearing as 2 in the System Monitor?

Try Xubuntu/ Lubuntu 12.04...

---

### Post by black veils on 2012-09-14
try linux mint 13 xfce or xubuntu, you will have plenty of options, yet a system lighter on graphics!

---

### Post by didar90 on 2012-09-14
Hello,

i m new user of Ubuntu 12.04. Before that, i used to use Windows, still i have two OS in my laptop, Ubuntu and Windows 7. 

I m facing the same problem with Ubuntu, sometime it freezes up. Its slow. 

But, i m really liking the interface. I want to use Ubuntu as my main OS. 

My Laptop config is:

Acer Aspire E1-431
Processor: Intel B960 2nd Generation Dual Core (2.2 GHz, 2MB L3 Cache)
Intel HD Graphics
2GB DDR3 1333 Bus Ram
500GB HDD
14.1 inch LED.

How can i make my Ubuntu faster??

Pls help me out.

---

### Post by shreepads on 2012-09-17
> **didar90 said:**
> Hello,

i m new user of Ubuntu 12.04. Before that, i used to use Windows, still i have two OS in my laptop, Ubuntu and Windows 7. 

I m facing the same problem with Ubuntu, sometime it freezes up. Its slow. 

But, i m really liking the interface. I want to use Ubuntu as my main OS. 

My Laptop config is:

Acer Aspire E1-431
Processor: Intel B960 2nd Generation Dual Core (2.2 GHz, 2MB L3 Cache)
Intel HD Graphics
2GB DDR3 1333 Bus Ram
500GB HDD
14.1 inch LED.

How can i make my Ubuntu faster??

Pls help me out.

Try installing XFCE from Synaptic and at the login screen select XFCE session...

---


---
title: "[SOLVED] Network connection mauled by 8.10 upgrade"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by thornmastr on 2008-11-01
Greetings,

I have more than once dutifully upgraded from level to level and from version to version with little if any problems at all. 8.10 has more than made up for all that pleasant upward mobility. After the upgrade I was left with two problems; the first effectively killing a reasonable cure; to wit, 'No network connection.' The second involves no sound but I will deal with that when my network works again. As an aside, to communicate with the group I am using a Windows PC; so I am really an unhappy and frustrated camper.

I ran a number of relative (I hope) commands to shed some light on the situation, but in all truth I do not know how to apply that information to bring back my network connection. The file, t1.txt is attached. 

I would be most grateful if some network guru would look at the attachment, and offer some guidance and/or a resolution to the problem.

Since the text file did not properly upgrade, here it is:
Result of lspci | grep -i ethernet

bermanrl@bermanrl-desktop:~$ lspci | grep -i ethernet
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
bermanrl@bermanrl-desktop:~$ 
bermanrl@bermanrl-desktop:~$ 

Result of Sevices-Network Tools
Network device:	lo
Hardware address:	Loopback
IP address:	127.0.0.1
Netmask:	255.0.0.0
Broadcast:	 
Multicast:	Disabled
MTU:	16436
Link speed:	 
State:	Active
Transmitted packets:	10
Transmission errors:	0
Received packets:	10
Reception errors:	0
Collisions:	0

RESULT OF ifconfig:
bermanrl@bermanrl-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:660 (660.0 B)  TX bytes:660 (660.0 B)

RESULT OF lspci:
00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
03:00.0 SATA controller: Marvell Technology Group Ltd. 88SE6145 SATA II PCI-E controller (rev a1)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
bermanrl@bermanrl-desktop:~$ 

Result of lshw:

bermanrl-desktop          
    description: Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 uuid=AF0C4FDA-0DD9-11DC-8929-0007E9747DB3
  *-core
       description: Motherboard
       product: D975XBX2
       vendor: Intel Corporation
       physical id: 0
       version: AAD53350-507
       serial: BQB27220016G
       slot: Base Board Chassis Location
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: J3E1
          size: 2394MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Unknown
             size: 4MiB
             capacity: 4MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
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
     *-cache
          description: L1 cache
          physical id: 2
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 4
          version: BX97520J.86A.2674.2007.0315.1546 (03/15/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 0x414554373630554430302D33304458393758
             vendor: 0x7F7F7F7F7F570000
             physical id: 0
             serial: 0x11016794
             slot: J6H1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 1
             serial: NO DIMM
             slot: J6H2
        *-bank:2
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: 0x414554373630554430302D33304458393758
             vendor: 0x7F7F7F7F7F570000
             physical id: 2
             serial: 0x12016753
             slot: J6J1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM [empty]
             product: NO DIMM
             vendor: NO DIMM
             physical id: 3
             serial: NO DIMM
             slot: J6J2
     *-pci
          description: Host bridge
          product: 82975X Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82975X PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV535 [Radeon X1650 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV535 [Radeon X1650 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-multimedia UNCLAIMED
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage UNCLAIMED
                description: SATA controller
                product: 88SE6145 SATA II PCI-E controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list
                configuration: latency=0 mingnt=8
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: 82573L Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.27-7-server uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.27-7-server uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
              *-usb UNCLAIMED
                   description: Printer
                   product: deskjet 3600
                   vendor: hp
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   serial: TH3BM122ZD6B
                   capabilities: usb-2.00 bidirectional
                   configuration: maxpower=2mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.27-7-server uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.27-7-server uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.27-7-server ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub slots=8 speed=480.0MB/s
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-firewire UNCLAIMED
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=4 mingnt=2
        *-isa
             description: ISA bridge
             product: 82801GH (ICH7DH) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1P
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KL05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD5000AAKS-0
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/sda
                version: 12.0
                serial: WD-WCAPW1725099
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000a482
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.1.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 8ce73acc-b6ec-4452-9112-22db20fe00ac
                   size: 459GiB
                   capacity: 459GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2007-07-07 15:12:00 filesystem=ext3 modified=2008-11-01 09:07:23 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-10-31 19:48:25 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.1.0,2
                   logical name: /dev/sda2
                   size: 5930MiB
                   capacity: 5930MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5930MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
bermanrl@bermanrl-desktop:~$

Result of  dmesg | grep -i error
bermanrl@bermanrl-desktop:~$ dmesg | grep -i error
[    2.800113] usb 2-1: device not accepting address 2, error -71
bermanrl@bermanrl-desktop:~$ 





Thank you very much,


Robert

---

### Post by Mazza558 on 2008-11-01
What wireless card are you using?

(and you ought to attach that file ;))

---

### Post by thornmastr on 2008-11-01
Greetings Mazza,

I thought it did get uploaded. My apologies. I have now included it in the original post. Thanks for looking.

Robert

---

### Post by Mazza558 on 2008-11-01
What does 

> iwlist scanning

show?

---

### Post by thornmastr on 2008-11-01
> **Mazza558 said:**
> What does 



show?

iwlist scanning shows:

lo   Interface doesn't support scanning.


Argggggggggggggg!

Robert

---

### Post by dwende on 2008-11-02
Upgrade to 8.10 also clobbered my network. It was
working fine in 8.04.

It seems to be similar to this problem:

[http://ubuntuforums.org/showthread.php?p=6081405#post6081405](http://ubuntuforums.org/showthread.php?p=6081405#post6081405)

although the fix there did not solve my problem.

---

### Post by thornmastr on 2008-11-02
> **dwende said:**
> Upgrade to 8.10 also clobbered my network. It was
working fine in 8.04.

It seems to be similar to this problem:

[http://ubuntuforums.org/showthread.php?p=6081405#post6081405](http://ubuntuforums.org/showthread.php?p=6081405#post6081405)

although the fix there did not solve my problem.

Thanks for the reply. That solution did not work for me either.
Did you ever get the problem resolved?

At this point, if there is not another forthcoming idea that works, I think the best approach is to do a massive system save to keep my existing data and software, and then do a real install of 8.10 from a downloaded CD; doing a full system restore once that is done to get back all my data.:confused:

Hopefully, someone has dealt with this issue before and it will work for me also.

Robert

---

### Post by thornmastr on 2008-11-03
Finally, I solved the problem with some help from a network engineer who suggested i attempt to download the latest driver for my network card. The problem got much more interesting when downloading the driver led me to the inescapable fact that the driver was already happily living on my machine.

The solution was to edit /boot/grub/menu.lst and point grub to use the previous  kernel. Then edit /etc/network/interfaces and add auto eth0 and iface eth0 inet dhcp. Reboot, and the network worked quite nicely.

Hopefully this will help someone who has had a similar experience upgrading to 8.10.


Robert

---


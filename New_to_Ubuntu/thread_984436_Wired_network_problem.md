---
title: "Wired network problem"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Jappsta on 2008-11-16
Hello,

I've got a little problem with my wired network connection on my laptop running a fresh installation of 8.10. It doesn't seem to autodetect my network card. Wireless works fine but I don't want to use my neighbours connection all the time.

/etc/network/interfaces gives me:
auto lo
iface lo inet loopback

:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)
02:06.4 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by randy78 on 2008-11-16
post the output of: sudo lshw
and: ifconfig

---

### Post by Jappsta on 2008-11-17
sudo lshw
[sudo] password for hidde: 
hidde-laptop              
    description: Notebook
    product: HP Compaq 8510w
    vendor: Hewlett-Packard
    version: F.14
    serial: CNU83109TP
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook uuid=33D09A8B-3A15-E011-0984-6D99103D5D29
  *-core
       description: Motherboard
       product: 30C5
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 71.36
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MVD Ver. F.14 (08/19/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.6
          serial: 0001-0676-0000-0000-0000-0000
          slot: U10
          size: 2501MHz
          capacity: 2501MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: burst external write-back unified
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
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             product: NL8256421207F-D53M
             vendor: 7F7F7F1600000000
             physical id: 0
             serial: 00265276
             slot: DIMM #1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM Synchronous [empty]
             physical id: 1
             slot: DIMM #2
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Quadro FX 570M
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: Mobile PM965/GM965 MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
        *-ide:0 UNCLAIMED
             description: IDE interface
             product: Mobile PM965/GM965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi cap_list
             configuration: latency=0
        *-communication:1
             description: Serial controller
             product: Mobile PM965/GM965 KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=serial latency=0
        *-network UNCLAIMED
             description: Ethernet controller
             product: 82566DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wmaster0
                version: 61
                serial: 00:21:5c:0a:10:ed
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.4 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:02:06.0
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00303020-b0030301f
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:02:06.1
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128 module=yenta_socket
                resources: iomemory:b00704020-b0070401f
              *-pccard UNCLAIMED
                   description: RICOH
                   physical id: 0
                   version: Bay8Controller
                   slot: Socket 1
                   resources: irq:3
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-generic
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:02:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: driver=ricoh-mmc latency=255 maxlatency=255 mingnt=255 module=ricoh_mmc
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T40L
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KC07
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: ST9200420AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AH
                serial: 5SH0ER3A
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=2527a2c7
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 36a73eb1-b2cb-b24b-bad3-13054e4eea5e
                   size: 43GiB
                   capacity: 43GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2008-10-30 10:08:47 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 142GiB
                   capacity: 142GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 113GiB
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 27GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1247MiB
                      capabilities: nofs
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 07/23/2008
       serial: 08199
       slot: Primary
       capacity: 51000mWh
       configuration: voltage=14.4V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4a:03:4a:e3:a8:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

 ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:308 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20416 (20.4 KB)  TX bytes:20416 (20.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:0a:10:ed  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe0a:10ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20389321 (20.3 MB)  TX bytes:859968 (859.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-0A-10-ED-30-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Jappsta on 2008-11-17
I've tried installing wicd to see if the problem was in NetworkManager, ifconfig has now changed to:

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:278 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17976 (17.9 KB)  TX bytes:17976 (17.9 KB)

pan0      Link encap:Ethernet  HWaddr d6:24:cc:18:78:11  
          inet6 addr: fe80::d424:ccff:fe18:7811/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:2772 (2.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:5c:0a:10:ed  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5cff:fe0a:10ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35824838 (35.8 MB)  TX bytes:2780812 (2.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-5C-0A-10-ED-30-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Still no wired connection though, anyone have an idea what could be going wrong here? Thanks.

---

### Post by dren on 2008-11-19
I'd love to know if you figure out what's wrong.  I ran an update on 8.04 (didn't go to 8.10).  Now my network card and IDE Controller card don't load drivers or function.

I get similar output to you from running ```
sudo lshw -C network
```

*-network UNCLAIMED

I think the unclaimed means there's no driver/module loaded for my hardware but I haven't the foggiest what the name of the correct module to load is.  Heck, I don't even know how to find that out.

---

### Post by Jappsta on 2009-01-04
Sorry for digging up this old thread but I still have the same problem,
Anyone who can help me with this?

Thanks,
Hidde

---


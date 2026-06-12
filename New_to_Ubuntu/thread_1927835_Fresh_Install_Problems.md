---
title: "Fresh Install Problems"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by Lerik on 2012-02-18
Fried my old harddrive which had Vista on it, decided I would switch to Ubuntu to avoid the continue headache.

Installed Ubuntu 11.10 64 bit
Has HP DV2000 but terminal refers to the computer as DV2700
HD Scorpio Blue 320 harddrive 
Intel GM965/GL960 Integrated Graphics video card

I am experiencing minor problems though, the bootup takes forever.  Once I get to login, if I sign into Ubuntu, I get no icons or anything.  When I sign into Ubuntu 2d everything works, but it is still super slow. Any help would be appreciated. Thank you.

---

### Post by wildmanne39 on 2012-02-18
Hi, please post the output of:
```
sudo lshw
```
Thanks

---

### Post by Lerik on 2012-02-18
Going to have to go ahead and thank you for even looking at this next block of text.  If you can find something wrong, I will be eternally grateful.

```
micah-hp-pavilion-dv2700-notebook-pc
    description: Notebook
    product: HP Pavilion dv2700 Notebook PC (FE983UA#ABA)
    vendor: Hewlett-Packard
    version: F.2B
    serial: 2CE82352YV
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: administrator_password=enabled boot=oem-specific chassis=notebook family=103C_5335KV frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled sku=FE983UA#ABA uuid=6DBC1F20-3DB1-11DD-A5EE-AEAA1C6133D4
  *-core
       description: Motherboard
       product: 30CD
       vendor: Wistron
       physical id: 0
       version: 80.52
     *-firmware
          description: BIOS
          vendor: Phoenix
          physical id: 0
          version: F.2B
          date: 05/07/2008
          size: 102KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T5750
          slot: U2E1
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 667MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
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
             slot: L2 Cache
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM000
             vendor: Mfg 0
             physical id: 0
             serial: 1234-B0
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: SODIMM001
             vendor: Mfg 1
             physical id: 1
             serial: 1234-B1
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:f4000000-f40fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f4100000-f41fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1840(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1860(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f4705c00-f4705fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:48 memory:f4500000-f4503fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:f2000000-f3ffffff ioport:f0000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f4200000-f42fffff ioport:c0700000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8039 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 14
                serial: 00:1d:72:5f:17:73
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:f4200000-f4203fff ioport:3000(size=256)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=4096) memory:c0300000-c04fffff ioport:c0500000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:4000(size=4096) memory:f4300000-f43fffff ioport:c0100000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 61
                serial: 00:1f:3b:c5:37:fb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-12-generic firmware=228.61.2.24 ip=192.168.0.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:f4300000-f4301fff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:18a0(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18c0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f4706000-f47063ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f4400000-f44fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:08:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:16 memory:f4400000-f44007ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:08:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:18 memory:f4400800-f44008ff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:08:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
                resources: memory:f4401000-f44010ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:08:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=32
                resources: irq:18 memory:f4401400-f44014ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
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
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1830(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DS8A1H
                vendor: Slimtype
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WH66
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
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:18f8(size=8) ioport:18ec(size=4) ioport:18f0(size=8) ioport:18e8(size=4) ioport:1c00(size=32) memory:f4705000-f47057ff
           *-disk
                description: ATA Disk
                product: WDC WD3200BPVT-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX71E91FAMV6
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000aff80
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d7335553-4a27-4a9b-b99c-063e7bef539e
                   size: 294GiB
                   capacity: 294GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2012-02-18 14:45:51 filesystem=ext4 lastmountpoint=/ modified=2012-02-18 18:00:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,stripe=1,data=ordered mounted=2012-02-18 18:05:11 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4085MiB
                   capacity: 4085MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4085MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0000000-c00000ff ioport:1c20(size=32)
  *-battery
       description: Lithium Ion Battery
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1
       slot: Rear
       capacity: 1000mWh
       configuration: voltage=0.0V
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 2
       capabilities: inbound
micah@micah-HP-Pavilion-dv2700-Notebook-PC:~$ 
```

---

### Post by wildmanne39 on 2012-02-18
Hi, I recommend logging out and choosing ubuntu no effects and see if that helps the slowness problems.

Your computer would probably do a lot better with xubuntu or lubuntu that require less resources.

I have a laptop with the same specs as yours and I installed xubuntu 10.04 so I would not have any trouble because of lack of resources.
Thanks

---

### Post by Lerik on 2012-02-18
How do I do Ubuntu no effects?  I stumbled upon 2d mode.  Also, Why does my computer run Vista wonderfully and is terrible with Ubuntu?  Thank you again.

---

### Post by mastergkage on 2012-02-19
> **Lerik said:**
> How do I do Ubuntu no effects?  I stumbled upon 2d mode.  Also, Why does my computer run Vista wonderfully and is terrible with Ubuntu?  Thank you again.

on the log-in screen you can see a small gear choose the options with no effects then log in see if there is a difference or an improve in performance, I encounter this lag of pc even though I'm using core i3 which lack video card memory dedicated is only 64mb but shared memory is upto 2GB.

---

### Post by Lerik on 2012-02-19
I could not even get no effects mode to finish loading up, 2d mode takes me on average fifteen minutes to load up.  Opening firefox takes abut two.  I just feel like I am missing something rather simple.  This computer ran vista well, I find it hard to believe ubuntu would be using more resources.  Any ideas would be greatly appreciated.

---

### Post by Blueyak on 2012-02-19
Just a quick ps to wildmanne39's post:  I don't know why Ubuntu is consuming so much resources for you but I switched from Ubuntu 11.04 to Xubuntu 11.10 and have really found it snappy, easier to work with and much more intuitive (xfce is more like gnome 2) than Unity.

---

### Post by oldfred on 2012-02-19
My Toshiba is 5 or 6 years old with 1.5GB of RAM and runs 10.10 just fine. I can also boot a USB flash drive and run 12.04 and it seems ok, but both flash & USB speeds make it a bit slower.

What BIOS settings do you have. Laptops often do not have much in the way of BIOS settings, but you may want to review. Newer systems use ACHI, some have IDE mode which may be slow. Do not use RAID setting if you have it as it may write data to drive that will cause issues. Some comments by others with issues, mostly with grub being slow.

One user had this work but see notes:
BIOS should be set for IDE compatibility mode - May make system slower so use with caution.
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
'IDE DMA tansfer' is the newer system to access IDE discs. By 'newer' I mean 'anything newer than 1997/1998 or so'. Disabling this setting forces the IDE drive to use 'PIO' mode, which is super slow.
Running PIO mode for a DMA HDD is a major performance hit. Running SATA HDDs in 'compatibility' (or 'IDE') mode is less of a hit, but still a hit.

Slow boot with Blue Ray need AHCI, but Windows also need AHCI configuration:

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.

---


---
title: "How to confirm hardware is detected and working  11.10"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by lobos marinos on 2011-10-17
Hi,

Firstly, I am a total beginner - don't understand syntax but eager to learn

Secondly, any feedback is greatly appreciated.

Installed Ubuntu 11.10 x64 Unity dual-boot with Windows7 x64

I ran the command "sudo lshw" from terminal with the following output:

```
vic@vic-Dell-System-XPS-L502X:~$ sudo lshw
[sudo] password for vic: 
vic-dell-system-xps-l502x 
    description: Portable Computer
    product: Dell System XPS L502X (System SKUNumber)
    vendor: Winbond Electronics
    version: 0.1
    serial: GRR8TQ1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall64 vsyscall32
    configuration: administrator_password=unknown boot=normal chassis=portable family=HuronRiver System frontpanel_password=unknown keyboard_password=unknown power-on_password=unknown sku=System SKUNumber uuid=44454C4C-5200-1052-8038-C7C04F545131
  *-core
       description: Motherboard
       product: 0NJT03
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: .GRR8TQ1.CN4864319K1239.
       slot: Part Component
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A06
          date: 07/20/2011
          size: 128KiB
          capacity: 2496KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
          vendor: Intel Corp.
          physical id: 19
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
          serial: Not Supported by CPU
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=4 threads=8
        *-cache:0
             description: L1 cache
             physical id: 1a
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 1b
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 1c
             slot: L3-Cache
             size: 6MiB
             capacity: 6MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 0
             serial: 8C520B6F
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: NT2GC64B88B0NS-CG
             vendor: Nanya Technology
             physical id: 1
             serial: 15590B6F
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:f0000000-f10fffff ioport:c0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF106 [GeForce GT 555M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:51 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:16 memory:f2405000-f240500f
        *-usb:0
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f240a000-f240a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:53 memory:f2400000-f2403fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f1800000-f1ffffff
           *-multimedia UNCLAIMED
                description: Multimedia controller
                product: SAA7231
                vendor: Philips Semiconductors
                physical id: 0
                bus info: pci@0000:02:00.0
                version: ca
                width: 64 bits
                clock: 33MHz
                capabilities: msi pciexpress pm bus_master cap_list
                configuration: latency=0
                resources: memory:f1800000-f1bfffff memory:f1c00000-f1ffffff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f2300000-f23fffff
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 34
                serial: ac:72:89:97:95:3c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=17.168.5.1 build 33993 ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:52 memory:f2300000-f2301fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:f2200000-f22fffff
           *-usb
                description: USB Controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:f2200000-f2201fff
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f2100000-f21fffff
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) ioport:f2000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth0
                version: 06
                serial: 84:8f:69:ab:15:45
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:50 ioport:2000(size=256) memory:f2004000-f2004fff memory:f2000000-f2003fff
        *-usb:1
             description: USB Controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f2409000-f24093ff
        *-isa
             description: ISA bridge
             product: HM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:49 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4060(size=32) memory:f2408000-f24087ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BPKT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WX91A61R4261
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=07f2837e
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: c449-4b80
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-09-26 02:54:54 filesystem=ntfs label=System Reserved state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 9233cb36-c38b-f247-8144-dee53ea437ae
                   size: 452GiB
                   capacity: 452GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-09-26 02:54:56 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 9359MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,stripe=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3989MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-L633J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D500
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f2404000-f24040ff ioport:efa0(size=32)
  *-battery
       product: DELL
       vendor: SDI
       physical id: 1
       version: 2008
       serial: 1.0
       slot: Rear
       capacity: 57720mWh
       configuration: voltage=11.1V
vic@vic-Dell-System-XPS-L502X:~$ 

```How do I know what is working & configured properly please?

What does "Status=Dirty" or "Status=Clean" mean for the hard drives please?

What does is it mean if one of the hardware is classified as "UNCLAIMED"?  Maybe that is my TV Tuner?

I used GParted to change partition sizes. Windows NTFS Volume 1 is now shown as "modified_by_chkdsk=true".  Is that caused by something I may have done incorrectly whilst using GParted or is that normal?  Chkdsk never used to run at boot and I can force stop but would like to know if caused by installation is standard.  Thanks

What does "sudo" mean please?  I'm guessing "super user" something or other...

Does "lshw" stand for List Hardware?

Many thanks for any help provided :)

---

### Post by dFlyer on 2011-10-17
Open dash and under search type system testing. That should give you an icon to click to test your system.

---

### Post by mcduck on 2011-10-17
Dirty status would mean that the file system on the hard drive might have problems, usually a result from uncleanly turning off the power, or the OS crashing. 

If it's on a Windows partition, booting to Windows and then shutting down normally sets the file system status as clean again.

For Linux partitions fsck should automatically fix the issue on boot. If it doesn't you can run it manually.

"unclaimed" means that no driver has taken control of the device. The unclaimed Philips "multimedia device" could very
 well be your TV tuner, if the computer has one. What comes to the unclaimed SMbus device, I wouldn't worry about it, that's usually only used for reading various temperature and voltage sensors, and if it doesn't work the only effect is that you might not be able to get information about your processors temperature etc. information. (none of the built-in safety features for overheating protection and so on rely on this, so if it doesn't work you aren't missing anything important)

edit: Yes, "lshw" is short for "list hardware". That's what it says on lshw's manual page. :) There are also similar commands like "lspci" and "lsusb", which obviously list PCI devices and USB devices....

edit2: I made a quick search for the Philips SAA7231, and indeed that is the TV tuner. Sadly, it seems that there is no working Linux driver for it. Somebody was writing one, but never got it into a working state and the last update is from 2009 so it's definitely not looking like you could get that one working...

---

### Post by lobos marinos on 2011-10-17
> **dFlyer said:**
> Open dash and under search type system testing. That should give you an icon to click to test your system.Hi & thanks.  I already ran that about half hour before I posted.  It just comes up with everything ticked.  Not sure if the list is for all hardware installed or just hardware that has linux drivers.  IE is it a complete test of ALL hardware installed or just what Linux can successfully install from default setup?

> **mcduck said:**
> Dirty status would mean that the file system on the hard drive might have problems, usually a result from uncleanly turning off the power, or the OS crashing. 

If it's on a Windows partition, booting to Windows and then shutting down normally sets the file system status as clean again.

For Linux partitions fsck should automatically fix the issue on boot. If it doesn't you can run it manually.

"unclaimed" means that no driver has taken control of the device. The unclaimed Philips "multimedia device" could very
 well be your TV tuner, if the computer has one. What comes to the unclaimed SMbus device, I wouldn't worry about it, that's usually only used for reading various temperature and voltage sensors, and if it doesn't work the only effect is that you might not be able to get information about your processors temperature etc. information. (none of the built-in safety features for overheating protection and so on rely on this, so if it doesn't work you aren't missing anything important)

edit: Yes, "lshw" is short for "list hardware". That's what it says on lshw's manual page. :) There are also similar commands like "lspci" and "lsusb", which obviously list PCI devices and USB devices....Rebooted into both Linux and Windows several times yesterday without 'dirty status' changing.  Will run fsck manually for Linux and manually system file check for Windows too.

I do have a TV Tuner and I think it iss the unclaimed device on PCI 1.  It is an Avermedia card H339 Hybrid DVB-T (with Philips chipset I think.).  I'll see if there is a Linux driver but would not have clue how to install lol

Edit: thanks for mentioning about lshw manual page.  Did not think to google a manual that only lists commands.  Now know fsck stands for File System Consistency Check & repair.

Edit 2: Thanks for checking about Philips device.  I was typing my original reply while you were checking.  I knew it had to be TV-Card and also cross-referenced against Philips to confirm chipset.

---


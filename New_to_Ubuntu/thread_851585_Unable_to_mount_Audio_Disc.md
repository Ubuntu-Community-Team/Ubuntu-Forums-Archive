---
title: "Unable to mount Audio Disc"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by valke on 2008-07-06
I wanted to play a CD. CDs have been working fine ever since I bought my Dell 1420n with Ubuntu pre-installed in February this year. Now, I get this nasty pop-up window that says:

Unable to mount Audio Disc
cannot connect to System Bus

I have no idea what's wrong, and I need help.

please and thanks.

---

### Post by ChameleonDave on 2008-07-07
Try entering this into a terminal:

```

cat /etc/fstab

```

---

### Post by valke on 2008-07-07
here is the output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f1fc5579-34a1-4a51-9197-5f4fb1d474e2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e93e2dd1-db08-49f2-8fe3-1117420f95f2 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

---

### Post by ChameleonDave on 2008-07-07
Is the error the same both for audio CDs and for CD-ROMs?

---

### Post by valke on 2008-07-08
yes.

---

### Post by ChameleonDave on 2008-07-08
The line with "/dev/sda2" seems to me to be unlikely to be correct.  In fact, it would take some very weird BIOS settings for that to be correct.

How many optical (CD/DVD) drives do you have on the machine?

Try putting a CD into the drive and entering the following commands:

```

sudo mount -v /dev/sda2
ls -l /media/cdrom0      # *checks whether the mount worked*

sudo mount -v /dev/scd0
ls -l /media/cdrom1      # *checks whether the mount worked*

```

Please also post the output of:

```

sudo blkid
sudo lshw -sanitize -C disk

```

---

### Post by forger on 2008-07-08
That /dev/sda2 shouldn't be there..

also post the output of:
```
sudo fdisk -l
```

---

### Post by aviborse on 2008-07-09
Hi 

I m not able to mount DVD which i burned wen i was using vista.
Now i have comletely shifted to ubuntu 100%
dont wanna go back.........but my dvd collection of about 40 DVD's is of no use now since i cant access it on my Lappy.........please help!!!!!!!!

Same is the case with VCD's and Audio CD's

I have Compaq Presario V6000
AMD Turion 64x2
160 GB HDD
1 GB Ram

OUTPUT OF TERMINAL AS BELOW

avi@avi-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=665781b2-edb6-4f0e-8a68-ca0e500fda20 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=57a93e2b-0a7b-4434-b1b7-f23a0d27d0bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
avi@avi-laptop:~$ sudo mount -v dev/sda2
[sudo] password for avi: 
Gravi@avi-laptop:~$ 
avi@avi-laptop:~$ sudo mount -v dev/sda2
[sudo] password for avi: 
mount: can't find dev/sda2 in /etc/fstab or /etc/mtab
avi@avi-laptop:~$ sudo mount -v /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

avi@avi-laptop:~$ ls -l /media/cdrom1 
ls: cannot access /media/cdrom1: No such file or directory
avi@avi-laptop:~$ sudo blkid
/dev/sda1: UUID="665781b2-edb6-4f0e-8a68-ca0e500fda20" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="57a93e2b-0a7b-4434-b1b7-f23a0d27d0bf" 
avi@avi-laptop:~$ sudo lshw -sanitize
computer                  
    description: Notebook
    product: Presario V6500 Notebook PC
    vendor: Hewlett-Packard
    version: Rev 1
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=2 uuid=434E4637-3335-344D-5A4B-001B2486DBC0
  *-core
       description: Motherboard
       product: 30CF
       vendor: Quanta
       physical id: 0
       version: 85.17
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.06 (07/23/2007)
          size: 109KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery
     *-cpu:0
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-58
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.8.1
          slot: Socket S1
          size: 800MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
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
             size: 512KiB
             capacity: 1MiB
             capabilities: synchronous internal write-through unified
     *-memory:0
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.8.1
          size: 800MHz
          capacity: 800MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP67 Co-processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8A1P
             vendor: Slimtype
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: CH71
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 5
             bus info: pci@0000:02:05.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-system:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.1
             bus info: pci@0000:02:05.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci latency=64 module=sdhci
        *-system:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 5.2
             bus info: pci@0000:02:05.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
        *-system:2 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 5.3
             bus info: pci@0000:02:05.3
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
        *-generic UNCLAIMED
             product: Illegal Vendor ID
             vendor: Illegal Vendor ID
             physical id: 5.4
             bus info: pci@0000:02:05.4
             version: ff
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master vga_palette cap_list
             configuration: latency=255 maxlatency=255 mingnt=255
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 04.0
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0b925cb5
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: [REMOVED]
                size: 146GiB
                capacity: 146GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-06-19 19:06:06 filesystem=ext3 modified=2008-07-09 00:27:43 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-08 22:28:06 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 2769MiB
                capacity: 2769MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2768MiB
                   capabilities: nofs
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          capacity: 100MB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-network
             description: Wireless interface
             product: BCM94311MCG wlan mini-PCI
             vendor: Broadcom Corporation
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: wlan1
             version: 02
             serial: [REMOVED]
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=[REMOVED] latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
     *-display
          description: VGA compatible controller
          product: GeForce 7150M
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
avi@avi-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b925cb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19104   153452848+  83  Linux
/dev/sda2           19105       19457     2835472+   5  Extended
/dev/sda5           19105       19457     2835441   82  Linux swap / Solaris

---

### Post by brian_p on 2008-07-09
> **valke said:**
> I wanted to play a CD. CDs have been working fine ever since I bought my Dell 1420n with Ubuntu pre-installed in February this year. Now, I get this nasty pop-up window that says:

Unable to mount Audio Disc
cannot connect to System Bus

Audio cds do not have a file system on them so cannot be mounted. The question would be why a mount is being attempted.

---

### Post by ChameleonDave on 2008-07-09
> **aviborse said:**
> Hi 

I m not able to mount DVD which i burned wen i was using vista.
Now i have comletely shifted to ubuntu 100%
dont wanna go back.........but my dvd collection of about 40 DVD's is of no use now since i cant access it on my Lappy.........please help!!!!!!!!


Hey, aren't you someone else anyway?

Your post is a bit hard to read.  Perhaps you could be so kind as to put the output of each command in a block quotation using the "#" button.  Click on the Edit button on your post to make the change.

---

### Post by ChameleonDave on 2008-07-09
[This bug report]("https://bugs.launchpad.net/ubuntu/+bug/193017") seems to indicate that Vista has adopted a non-standard version of the UDF file system.  This means that discs burnt using the default Vista burner (not third-party apps) are likely to be unmountable on other operating systems.

If you were paranoid, you'd almost think they wanted to sabotage Linux.

---


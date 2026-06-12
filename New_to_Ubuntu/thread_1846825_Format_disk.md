---
title: "Format disk"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by isato on 2011-09-19
Hi 

I was installing Ubuntu 11.04 64. When I was installing I didn't get pass "Installing language packages". I had to restart the computer. The disk is new so am not afraid of losing anything. How can I restore my disk to fabric.  

I have tried 

dd if=/dev/zero of=/dev/sda bs=64K     

and

sudo mkfs -t ext4 /dev/sda


Edit: Screen from disk utilty

 [http://img684.imageshack.us/content_round.php?page=done&l=img684/5986/screenshoteo.png](http://img684.imageshack.us/content_round.php?page=done&l=img684/5986/screenshoteo.png)

This is my disk

[http://www.komplett.no/k/ki.aspx?sku=641086](http://www.komplett.no/k/ki.aspx?sku=641086)


What can I do? I really wont to install Ubuntu 11.04 on it. 
Windows 7 worked just fine when i tried that. 


Thank you.

---

### Post by pytheas22 on 2011-09-19
If you restart the Ubuntu installer again from the beginning, choose the advanced partitioning option when you get to that step and you can easily tell the installer to format any existing partitions before installing your new Ubuntu system.

If the installer is crashing every time while it is installing language packages, then you will need to figure out that issue before going further.  I would check to make sure your installation CD is not corrupted, and google the model of your computer + ubuntu to see if there are known issues installing Ubuntu on that model.  If after research you remain stuck let me know.

---

### Post by isato on 2011-09-19
> **pytheas22 said:**
> If you restart the Ubuntu installer again from the beginning, choose the advanced partitioning option when you get to that step and you can easily tell the installer to format any existing partitions before installing your new Ubuntu system.

If the installer is crashing every time while it is installing language packages, then you will need to figure out that issue before going further.  I would check to make sure your installation CD is not corrupted, and google the model of your computer + ubuntu to see if there are known issues installing Ubuntu on that model.  If after research you remain stuck let me know.

When trying to format from Disk Utility (ext4) I get the error message

```
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.14 (22-Dec-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to reboot
	to re-read your partition table.
```


Edit: reeboting does not help.


Thanks


Trying to create partion table
```

Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sda, scheme=0
ped_device_get() failed
```

---

### Post by westie457 on 2011-09-19
Try it this way.

Boot your pc into the Live Desktop using your LiveCD/USB and start Gparted. When that is open ensure that your HD is not mounted, go to Device in the Menu Bar and select Create New Partition Table. This should effectively wipe the drive of all information.
Then select the unallocated space and create a new partition. make this about 20-25 GiB, this will be your '/'root partition. Next create another one about the same size as the amount of RAM, this will be your Swap partition. Then use the rest as your Home partition.

Partitions 1 and 3 should be formatted as EXT4 and there is no need to format the Swap as this is done during the install process.

Once this work has been completed close Gparted and click the INSTALL icon on the Desktop and follow the prompts as they come up.

Good luck.

---

### Post by isato on 2011-09-20
> **westie457 said:**
> Try it this way.

Boot your pc into the Live Desktop using your LiveCD/USB and start Gparted. When that is open ensure that your HD is not mounted, go to Device in the Menu Bar and select Create New Partition Table. This should effectively wipe the drive of all information.
Then select the unallocated space and create a new partition. make this about 20-25 GiB, this will be your '/'root partition. Next create another one about the same size as the amount of RAM, this will be your Swap partition. Then use the rest as your Home partition.

Partitions 1 and 3 should be formatted as EXT4 and there is no need to format the Swap as this is done during the install process.

Once this work has been completed close Gparted and click the INSTALL icon on the Desktop and follow the prompts as they come up.

Good luck.


Thanks

I have tried this but gparted does not find my SSD. I actually just installed Windows on it. I thought my disk would be found then. So strange becuase my disk was found the first time. 

I am out of ideas.

---

### Post by westie457 on 2011-09-20
Very weird and strange. Just looked at the link you posted for the drive, should have looked at it earlier. Is the SSD connected to a SATA 3 port. If it is that is probably why it is being recognised in Windows but not in Ubuntu. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1644278"). While not exactly describing your situation it does have a workable solution. Should be no harm in trying and might even work. 

Good luck.

---

### Post by isato on 2011-09-21
I don't believe that I am using SATA 3. 
```

description: Motherboard
       product: M4N68T
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MT7005036407605
       slot: To Be Filled By O.E.M.


  *-disk
             description: ATA Disk
             product: KINGSTON SH100S3
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 320A
             serial: 50026B7218240700
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=ccaa73dc
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 6015-8c47
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-09-20 20:57:03 filesystem=ntfs label=Reserverad av systemet state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 6604f8e8-03c3-9544-baac-3c66274091fe
                size: 111GiB
                capacity: 111GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-09-20 20:57:04 filesystem=ntfs state=clean
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=16) memory:deeef000-deeeffff


```

The whole ting
```
peter-system-product-name 
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=4 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=80F12677-8DFE-D511-AC70-485B39E9C2C5
  *-core
       description: Motherboard
       product: M4N68T
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MT7005036407605
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0706
          date: 04/09/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) II X4 635 Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.5.2
          serial: To Be Filled By O.E.M.
          slot: AM3
          size: 800MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt npt lbrv svm_lock nrip_save cpufreq
          configuration: cores=4 enabledcores=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 2f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.5.2
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
     *-cpu:2
          physical id: a
          bus info: cpu@2
          version: 15.5.2
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
     *-cpu:3
          physical id: d
          bus info: cpu@3
          version: 15.5.2
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
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:900(size=256)
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:e00(size=64) ioport:600(size=64) ioport:700(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:deefb000-deefbfff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:deefac00-deefacff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:deef4000-deef7fff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 48:5b:39:e9:c2:c5
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=10.0.0.6 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:43 memory:deef9000-deef9fff ioport:d480(size=8)
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=8) ioport:cc00(size=4) ioport:c880(size=16) memory:deef8000-deef8fff
        *-disk
             description: ATA Disk
             product: KINGSTON SH100S3
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sda
             version: 320A
             serial: 50026B7218240700
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=ccaa73dc
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@3:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 6015-8c47
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-09-20 20:57:03 filesystem=ntfs label=Reserverad av systemet state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@3:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: 6604f8e8-03c3-9544-baac-3c66274091fe
                size: 111GiB
                capacity: 111GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2011-09-20 20:57:04 filesystem=ntfs state=clean
     *-ide:2
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          logical name: scsi4
          logical name: scsi5
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:22 ioport:c800(size=8) ioport:c480(size=4) ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=16) memory:deeef000-deeeffff
        *-disk
             description: ATA Disk
             product: SAMSUNG HD322HJ
             physical id: 0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1AC0
             serial: S17AJ90Z336616
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000eb061
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /
                version: 1.0
                serial: 5139ef7b-2e69-421a-9d22-028e5f5a726a
                size: 294GiB
                capacity: 294GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2011-09-17 09:01:11 filesystem=ext4 lastmountpoint=/ modified=2011-09-17 09:16:42 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-09-21 18:24:00 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdb2
                size: 4095MiB
                capacity: 4095MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sdb5
                   capacity: 4095MiB
                   capabilities: nofs
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223L
             vendor: TSSTcorp
             physical id: 1
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:e000(size=4096) memory:def00000-dfffffff ioport:c0000000(size=503316480)
        *-display
             description: VGA compatible controller
             product: GT216 [GeForce GT 220]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a2
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:19 memory:df000000-dfffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:ec00(size=128) memory:def80000-deffffff
        *-multimedia
             description: Audio device
             product: High Definition Audio Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:def7c000-def7ffff
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz

```

---

### Post by pytheas22 on 2011-09-21
From the output you just posted, it looks like the system definitely detects a 120 gigabyte disk.  Is this the disk you're trying to format?  If so I don't know why gparted can't see it.

You could try using gparted's command-line equivalent, parted (just type "sudo parted" to start it).  It not as easy as pointing and clicking but if you type "help" in its shell figuring out how to use it is pretty straightforward.  You can use parted to erase your Windows partitions and replace them with a Linux one.

If you continue to have problems, it would also be useful to see what the output of "sudo fdisk -l" is.

---

### Post by westie457 on 2011-09-21
Kingston HyperX SSD 120GB 2.5"
[COLOR="Red"]SATA 6 Gb/s (SATA3.0)[/COLOR], 555MB/510MB/s read/write, SandForce®


1.895,-

Lagerstatus:  100+ stk. på lager.
Finansieringspris: kr 174,-/md. (12 md.)
Se alle terminbeløp

Ved finansiering kommer det i tillegg kr 45 i termingebyr og kr 295 i etableringsgebyr pr kunde. Kredittkjøpspris: kr 2.920. Fullstendige kjøpsbetingelser og effektiv rente. Ved kjøp av flere produkter vil kredittkjøpsprisen bli lavere.

Hello, The above was copied from the link you posted, see the part highlighted in red that says it is a SATA 3 Drive.

Try connecting it to an ordinary SATA 2 port and check if it is now recognised. If so,go ahead and format it and install 11.04 or any other OS that you want.

Good luck.

---

### Post by isato on 2011-09-23
> **westie457 said:**
> Kingston HyperX SSD 120GB 2.5"
[COLOR="Red"]SATA 6 Gb/s (SATA3.0)[/COLOR], 555MB/510MB/s read/write, SandForce®


1.895,-

Lagerstatus:  100+ stk. på lager.
Finansieringspris: kr 174,-/md. (12 md.)
Se alle terminbeløp

Ved finansiering kommer det i tillegg kr 45 i termingebyr og kr 295 i etableringsgebyr pr kunde. Kredittkjøpspris: kr 2.920. Fullstendige kjøpsbetingelser og effektiv rente. Ved kjøp av flere produkter vil kredittkjøpsprisen bli lavere.

Hello, The above was copied from the link you posted, see the part highlighted in red that says it is a SATA 3 Drive.

Try connecting it to an ordinary SATA 2 port and check if it is now recognised. If so,go ahead and format it and install 11.04 or any other OS that you want.

Good luck.

Sorry did not mean do be rude. Thanks for your help. 


"Try connecting it to an ordinary SATA 2 port and check if it is now recognised"

Thats what I think I am already doing. My motherboard only support Sata 2 I think. I this what you mean?

---

### Post by isato on 2011-09-23
> **pytheas22 said:**
> From the output you just posted, it looks like the system definitely detects a 120 gigabyte disk.  Is this the disk you're trying to format?  If so I don't know why gparted can't see it.

You could try using gparted's command-line equivalent, parted (just type "sudo parted" to start it).  It not as easy as pointing and clicking but if you type "help" in its shell figuring out how to use it is pretty straightforward.  You can use parted to erase your Windows partitions and replace them with a Linux one.

If you continue to have problems, it would also be useful to see what the output of "sudo fdisk -l" is.

"sudo parted" was I pain. Dont realy know what should be done. This my output from "sudo fdisk -l". Cant see my disk anywhere. 

```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb061

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38392   308375552   83  Linux
/dev/sdb2           38392       38914     4193281    5  Extended
/dev/sdb5           38392       38914     4193280   82  Linux swap / Solaris
peter@peter-System-Product-Name:~$ 

```

---

### Post by westie457 on 2011-09-23
> **isato said:**
> Sorry did not mean do be rude. Thanks for your help. 


"Try connecting it to an ordinary SATA 2 port and check if it is now recognised"

Thats what I think I am already doing. My motherboard only support Sata 2 I think. I this what you mean?

Did not think you were being rude, so no apology necessary.
The little knowledge I have about SSDs is only what I have read in the Forum.
At the moment the only thing I can suggest you do is give the drive a thorough check using Disk Utility and SMART Status, that is if a SSD has SMART built in. Another thing you could do is to contact the drive manufacturer's technical support department to find out if they have any idea why it cannot be partitioned or formatted.

I am completely out of ideas on how to fix this now. Sorry, I cannot help you further with this.

May be some others on the Forum might be able to help.

Good luck.

---

### Post by westie457 on 2011-09-24
Hello me again.

have been doing some research and have found this that might help you. [http://ubuntuforums.org/showthread.php?t=1456238](http://ubuntuforums.org/showthread.php?t=1456238)

---

### Post by pytheas22 on 2011-09-24
Thanks for the fdisk output.  It's certainly true that the device is not present there, but it's strange that the drive that is showing is sdb.  I would expect it to be sda if it's the only device that the system is recognizing.  This suggests that the system might be trying to do something with the SSD, and if it is running into a problem it will probably be mentioned in dmesg our your system log.  What output do get from:
```

dmesg | grep sda
grep sda /var/log/syslog
```

You may also want to experiment with any BIOS settings you have available regarding the drive bus to see if they make a difference.

---

### Post by isato on 2011-09-24
> **pytheas22 said:**
> Thanks for the fdisk output.  It's certainly true that the device is not present there, but it's strange that the drive that is showing is sdb.  I would expect it to be sda if it's the only device that the system is recognizing.  This suggests that the system might be trying to do something with the SSD, and if it is running into a problem it will probably be mentioned in dmesg our your system log.  What output do get from:
```

dmesg | grep sda
grep sda /var/log/syslog
```

You may also want to experiment with any BIOS settings you have available regarding the drive bus to see if they make a difference.

This is the output. 

```
peter@peter-System-Product-Name:~$ dmesg | grep sda 
[    8.096461] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    8.096514] sd 3:0:0:0: [sda] Write Protect is off
[    8.096517] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.096596] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.097011]  sda: sda1 sda2
[    8.097282] sd 3:0:0:0: [sda] Attached SCSI disk
peter@peter-System-Product-Name:~$ 

``````
peter@peter-System-Product-Name:~$ grep sda /var/log/syslog
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.004457] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.004503] sd 3:0:0:0: [sda] Write Protect is off
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.004505] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.004521] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.004888]  sda: sda1 sda2
Sep 24 14:45:19 peter-System-Product-Name kernel: [    8.005133] sd 3:0:0:0: [sda] Attached SCSI disk
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.036465] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.036530] sd 3:0:0:0: [sda] Write Protect is off
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.036534] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.036578] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.036944]  sda: sda1 sda2
Sep 24 20:19:55 peter-System-Product-Name kernel: [    8.037148] sd 3:0:0:0: [sda] Attached SCSI disk
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.960436] sd 1:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.960499] sd 1:0:0:0: [sda] Write Protect is off
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.960504] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.960533] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.960872]  sda: sda1 sda2
Sep 24 23:17:26 peter-System-Product-Name kernel: [    7.961108] sd 1:0:0:0: [sda] Attached SCSI disk
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.004457] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.004536] sd 3:0:0:0: [sda] Write Protect is off
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.004540] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.004581] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.004961]  sda: sda1 sda2
Sep 25 00:22:02 peter-System-Product-Name kernel: [    8.005276] sd 3:0:0:0: [sda] Attached SCSI disk
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.936470] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.936529] sd 3:0:0:0: [sda] Write Protect is off
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.936531] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.936588] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.937032]  sda: sda1 sda2
Sep 25 00:23:54 peter-System-Product-Name kernel: [    7.937296] sd 3:0:0:0: [sda] Attached SCSI disk
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.096461] sd 3:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.096514] sd 3:0:0:0: [sda] Write Protect is off
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.096517] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.096596] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.097011]  sda: sda1 sda2
Sep 25 00:25:26 peter-System-Product-Name kernel: [    8.097282] sd 3:0:0:0: [sda] Attached SCSI disk
peter@peter-System-Product-Name:~$ 

```

---

### Post by bodhi.zazen on 2011-09-24
> **isato said:**
> "sudo parted" was I pain. Dont realy know what should be done. This my output from "sudo fdisk -l". Cant see my disk anywhere. 

Next time use gparted =)

You need to understand the difference between /dev/sda and dev/sda1

See :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Also, you should reboot after changing the partition table with either parted or gparted.

---

### Post by isato on 2011-09-25
> **bodhi.zazen said:**
> Next time use gparted =)

You need to understand the difference between /dev/sda and dev/sda1

See :

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Also, you should reboot after changing the partition table with either parted or gparted.

Thanks for replay. I will read you tutorial but trying gparted was one of the first thing we did in this thread :).

---

### Post by isato on 2011-09-25
Trying some more. Normal output? I dont need to think about sdaX right know right? I only need one partion and the installer will take care of the rest?

```
peter@peter-System-Product-Name:~$ sudo mkfs.ext4 -L Kingston /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=Kingston
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
7331840 inodes, 29305206 blocks
1465260 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
895 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 38 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
peter@peter-System-Product-Name:~$ 

```


Edit: Made no difference.

---

### Post by WasMeHere on 2011-09-25
> **isato said:**
> Trying some more. Normal output? I dont need to think about sdaX right know right? I only need one partion and the installer will take care of the rest?

```
peter@peter-System-Product-Name:~$ sudo mkfs.ext4 -L Kingston /dev/sda
mke2fs 1.41.14 (22-Dec-2010)
/dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
```


Well, I think you need to think about sdaX right know. Please make a partition '/dev/sda1' on the '/dev/sda' disk! It may fill the disk, but should still be a partition. This action should be straight-forward with gparted, where you can also format it.

---

### Post by isato on 2011-09-25
> **Olle Wiklund said:**
> Well, I think you need to think about sdaX right know. Please make a partition '/dev/sda1' on the '/dev/sda' disk! It may fill the disk, but should still be a partition. This action should be straight-forward with gparted, where you can also format it.

Well this is my gparted at the moment. Cant choose sda. 

[http://imageshack.us/photo/my-images/402/screenshot1rdk.png/](http://imageshack.us/photo/my-images/402/screenshot1rdk.png/)

---

### Post by WasMeHere on 2011-09-25
> **isato said:**
> Well this is my gparted at the moment. Cant choose sda. 

So you cannot click on the button at the top right corner and select sda?! OK, I see. Your problem is not that easy. But I think that the following text from your earlier attempt is a warning:
> /dev/sda is entire device, not just one partition!
Proceed anyway? (y,n) y
Try again make the disk clean using **dd** (again). *Warning!!!* Make sure that sda is the disk you want to clean:
```
sudo dd if=/dev/zero of=/dev/sda bs=64K 
```
After that **gparted** maybe will not be confused by your file system without a partition. Otherwise you can try the following commands in **sudo parted**:
'print'
'select _device_'
'mkpart'
according to 'man parted':
> mkpart _part-type_ _[fs-type]_ _start_ _end_
       Make a part-type partition with  filesystem fs-type
       (if specified),  beginning  at  start  and  ending at end
       (by default in megabytes).  fs-type can be  one  of  "fat16",
       "fat32", "ext2", "HFS", "linux-swap", "NTFS", "reiserfs",
       or "ufs".  part-type should be one of  "primary",  "logi&#8208;
       cal", or "extended".
If you don't like parted, maybe the following command will work for you to make a partition:
```
sudo cfdisk /dev/sda
```
You do not have to make a filesystem (format the partition) at this moment. This will be done during the installation of Ubuntu. Just make a partition!****

---

### Post by isato on 2011-09-25
> **Olle Wiklund said:**
> So you cannot click on the button at the top right corner and select sda?! OK, I see. Your problem is not that easy. But I think that the following text from your earlier attempt is a warning:

Try again make the disk clean using **dd** (again). *Warning!!!* Make sure that sda is the disk you want to clean:
```
sudo dd if=/dev/zero of=/dev/sda bs=64K 
```
After that **gparted** maybe will not be confused by your file system without a partition. Otherwise you can try the following commands in **sudo parted**:
'print'
'select _device_'
'mkpart'
according to 'man parted':

If you don't like parted, maybe the following command will work for you to make a partition:
```
sudo cfdisk /dev/sda
```
You do not have to make a filesystem (format the partition) at this moment. This will be done during the installation of Ubuntu. Just make a partition!****


I tried this 

peter@peter-System-Product-Name:~$ sudo dd if=/dev/zero of=/dev/sda bs=64K
[sudo] password for peter: 
dd: writing `/dev/sda': No space left on device
1831576+0 records in
1831575+0 records out
120034123776 bytes (120 GB) copied, 573.087 s, 209 MB/s
peter@peter-System-Product-Name:~$ sudo cfdisk /dev/sda


The result :) 

[http://imageshack.us/photo/my-images/15/screenshot2npm.png/](http://imageshack.us/photo/my-images/15/screenshot2npm.png/)

---

### Post by bodhi.zazen on 2011-09-25
Now make a partition with fdisk or gparted.

Then reboot afte writing a partition table (with either fdisk of gparted).

---

### Post by WasMeHere on 2011-09-25
> **isato said:**
> I tried this 

peter@peter-System-Product-Name:~$ sudo dd if=/dev/zero of=/dev/sda bs=64K
[sudo] password for peter: 
dd: writing `/dev/sda': No space left on device
1831576+0 records in
1831575+0 records out
120034123776 bytes (120 GB) copied, 573.087 s, 209 MB/s
peter@peter-System-Product-Name:~$ sudo cfdisk /dev/sda

The dd output indicates that it could write onto /dev/sda as it should. And fast too! So far so good. But how come the SSD disk is so unwilling to be recognized by any partitioning tool? What is the output of the following command:```
sudo fdisk -lu
``` I think fdisk is less fuzzy about strange configurations which may seem to be errors to other partitioning software. It is quite good at reading but fdisk is considered old and rather bad at writing.

See 'man fdisk': @BUGS near the end

If you have another computer and/or a sata to usb adapter, you can try to make a partition that way. It could be some lack of hand-shaking between the sata interface of the computer and the SSD disk.

Finally, I call for help from someone else: We need more ideas how to solve this problem!

---

### Post by WasMeHere on 2011-09-25
If fdisk is recognizing the disk, maybe you dare use fdisk to create a partition. But be ***sure*** that you are writing onto the SSD disk!!!
```
sudo fdisk /dev/sda
``` Type 'm' for help and use the one-key commands to make a partition and save a partition table.

Good luck :-)

---

### Post by isato on 2011-09-25
> **Olle Wiklund said:**
> If fdisk is recognizing the disk, maybe you dare use fdisk to create a partition. But be ***sure*** that you are writing onto the SSD disk!!!
```
sudo fdisk /dev/sda
``` Type 'm' for help and use the one-key commands to make a partition and save a partition table.

Good luck :-)
```
peter@peter-System-Product-Name:~$ sudo fdisk -lu
[sudo] password for peter: 

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb061

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   616753151   308375552   83  Linux
/dev/sdb2       616755198   625141759     4193281    5  Extended
/dev/sdb5       616755200   625141759     4193280   82  Linux swap / Solaris

```



```

peter@peter-System-Product-Name:~$ sudo fdisk /dev/sda

Unable to read /dev/sda
peter@peter-System-Product-Name:~$ 
```

---

### Post by WasMeHere on 2011-09-25
well isato,

*Let us call for help from someone else*: We need more ideas how to solve this problem! My final(?) suggestions:

1. Have you tried to reboot your computer and retried partitioning?

2. If you have another computer and/or a sata to usb adapter, you can try to make a partition that way. It could be some lack of hand-shaking between the sata interface of the computer and the SSD disk.

3. Or try it on a friend's computer. (Is the SSD hardware OK?)

---

### Post by isato on 2011-09-25
> **Olle Wiklund said:**
> well isato,

*Let us call for help from someone else*: We need more ideas how to solve this problem! My final(?) suggestions:

1. Have you tried to reboot your computer and retried partitioning?

2. If you have another computer and/or a sata to usb adapter, you can try to make a partition that way. It could be some lack of hand-shaking between the sata interface of the computer and the SSD disk.

3. Or try it on a friend's computer. (Is the SSD hardware OK?)

Hold on! My laptop finds it :) 

Hope it works all the way.

---

### Post by isato on 2011-09-25
Well thank you all. It works but I have to install the OS on my laptop and then plug it into my other computer.

Edit: That did not work. Installing on my laptop and plug in to the other computer. I guess I need a new mother board (CPU or RAM can't have any effect). Any recommendations ([http://www.komplett.no/k/kc.aspx?bn=10111)?](http://www.komplett.no/k/kc.aspx?bn=10111)?)
I got 8GB ram and a CPU (quad core) that I think will be enough for me right know. It will be good if the mother board will allow me to upgrade in the future.

Edit2: This computer will used mainly for programming. No gaming.
My current CPU: [http://www.komplett.no/k/ki.aspx?sku=586161](http://www.komplett.no/k/ki.aspx?sku=586161)
Memory: DDR3

---

### Post by WasMeHere on 2011-09-26
I'm glad you have found that the SSD is working, and I agree that it is your computer that does not recognize it. Getting a suitable motherboard would certainly solve it. I have no specific advice about mobos, maybe you ask a local vendor if you can test that your SSD disk is recognized and can be partitioned.

But I wonder if there is some setting in the *bios menu*, that could make a difference. In one of my computers, an hp xw8400, I can change several settings for disk interfaces: ide, sata, scsi etc. That way I can make it recognize only one or many sata devices.

So it might save you the cost of a mobo if you search and test the bios menu.

*Edit: You cannot expect that it works to install on your laptop and plug in to the other computer because the installer will 'taylor-make' the operating system to fit the current hardware during installation. What I meant was that you make a partition on the other computer. Anyway, is the SSD disk visible in your target computer? If visible, then you might have it ready for installation.```
sudo fdisk -lu
```*

---

### Post by isato on 2011-09-26
> **Olle Wiklund said:**
> I'm glad you have found that the SSD is working, and I agree that it is your computer that does not recognize it. Getting a suitable motherboard would certainly solve it. I have no specific advice about mobos, maybe you ask a local vendor if you can test that your SSD disk is recognized and can be partitioned.

But I wonder if there is some setting in the *bios menu*, that could make a difference. In one of my computers, an hp xw8400, I can change several settings for disk interfaces: ide, sata, scsi etc. That way I can make it recognize only one or many sata devices.

So it might save you the cost of a mobo if you search and test the bios menu.

*Edit: You cannot expect that it works to install on your laptop and plug in to the other computer because the installer will 'taylor-make' the operating system to fit the current hardware during installation. What I meant was that you make a partition on the other computer. Anyway, is the SSD disk visible in your target computer? If visible, then you might have it ready for installation.```
sudo fdisk -lu
```*
I have already ordered a new mother board. 

Thank you anyway for your time.

---


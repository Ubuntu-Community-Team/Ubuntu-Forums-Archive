---
title: "Audio on HP Compaq dc7100"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by Gashog on 2011-12-04
I'm setting up my "new" workstation and am having trouble with the audio settings.
The sound card and internal speaker work under 9.04 and with Windows but when I try anything newer then 9.04, the sound doesn't work anymore. I've tried editing some file in /etc/modprobe.something and I've tried messing with ALSA mixer. I couldn't get audio.
I have no idea what I'm doing but I thought I might save the audio settings from 9.04.
I'm sure there are may ways to fix this.
Since the sound is working now, would it be easy to just save the settings, upgrade and apply the old settings again?
I am assuming that the sound configuration is all in one file. Is that right?

---

### Post by Gashog on 2011-12-05
Can anyone tell me how to save my sound settings in 9.04 and apply them in 11.10?
```

description: Low Profile Desktop Computer
    product: HP Compaq dc7100 SFF(DX878AV)
    vendor: Hewlett-Packard
    serial: 2UA4480HZ3
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=low-profile cpus=1 uuid=79281118-F046-D911-BBDA-795E280B0012
  *-core
       description: Motherboard
       product: 097Ch
       vendor: Hewlett-Packard
       physical id: 0
       serial: 2UA4480HZ3
       slot: REAR LINE IN
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 1
          version: 786C1 v01.57 (09/13/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: XU1 PROCESSOR
          size: 2800MHz
          width: 32 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: Internal L1 Cache
             size: 28KiB
             capacity: 28KiB
             capabilities: burst internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: Cache L2
             size: 1MiB
             capacity: 4MiB
             capabilities: burst internal write-back data
     *-memory:0
          description: System Memory
          physical id: 33
          slot: System board or motherboard
        *-bank:0
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 0
             serial: 8F7D02F5
             slot: XMM1
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 1
             serial: 9A7D05F5
             slot: XMM2
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 2
             serial: 9C7C03F5
             slot: XMM3
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM DDR Synchronous 400 MHz (2.5 ns)
             product: M3 68L3223FTN-CCC
             vendor: JEDEC ID:CE 00 00 00 00 00 00 00
             physical id: 3
             serial: 7F7D06F5
             slot: XMM4
             size: 256MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-memory:1 UNCLAIMED
          description: Flash Memory
          physical id: 34
          slot: System board or motherboard
          capacity: 512KiB
        *-bank UNCLAIMED
             description: Chip FLASH Non-volatile
             physical id: 0
             slot: SYSTEM ROM
             size: 512KiB
             width: 4 bits
     *-memory:2 UNCLAIMED
          physical id: 0
     *-memory:3 UNCLAIMED
          physical id: 2
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth0
                version: 01
                serial: 00:12:79:5e:28:0b
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.29a ip=192.168.1.39 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
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
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
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
        *-ide:0
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
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
           *-disk
                description: ATA Disk
                product: ST380815AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AA
                serial: 5QZ523TB
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a56fa56f
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 400baec6-e83b-6048-b552-e03d26b7a078
                   size: 36GiB
                   capacity: 36GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-02-22 06:49:12 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: dc67422c-f94a-441a-b14e-daca24037a20
                   size: 2384MiB
                   capacity: 2384MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: b52ab66b-aff1-4585-9711-ecb1ab026f7f
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-12-03 21:12:58 filesystem=ext4 modified=2011-12-03 21:22:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-12-03 21:22:44 state=mounted
           *-cdrom
                description: DVD reader
                product: DVD D  DH16DYS
                vendor: ATAPI
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: XH31
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
     *-scsi
          physical id: 3
          bus info: usb@1:7
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Photosmart Plus
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             capabilities: removable
             configuration: ansiversion=5
           *-medium
                physical id: 0
                logical name: /dev/sdb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:93:f5:20:05:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ted@ted-desktop:~$ 
```

---

### Post by gordintoronto on 2011-12-05
> **Gashog said:**
> Can anyone tell me how to save my sound settings in 9.04 and apply them in 11.10?


Sorry, that's not an option. If you are not getting any sound, it is muted somewhere, or the wrong sound source is active. Does your computer have HDMI out?

---

### Post by Gashog on 2011-12-05
No. It's an antique workstation. No frills at all.
I'll do a clean install tomorrow and start again. It's running 9.04 now.

---

### Post by Gashog on 2011-12-06
I loaded my 11.04 live CD and the sound is gone. can anyone tell me where I should be looking, other then "sound preferences"?

---

### Post by Gashog on 2011-12-06
I have Lubuntu loaded and no sound.
It must be something to do with the Intel chipset right? Why can 9.04 recognize it no problem and every release from then on, have a problem plug and playing?
I need to set it up manually but I don't know how.

---

### Post by Gashog on 2011-12-06
Back to 9.04 and all is normal.
I don't get it.

---

### Post by Gashog on 2011-12-06
I installed Mint 9 LXDE and low and behold, there was a slider for IEC958 P (my sound card). It was all the way down and turning it up fixed everything, of course.
What I don't understand is why my device did not appear in the ALSA Mixer in any of the other distros or releases I tried.
I think that editing the modprobe file was supposed to add this device to the list but I don't know enough and couldn't get it to work.

I guess this is semi solved but I still don't know how I would have added my onboard sound card to ALSA.

---


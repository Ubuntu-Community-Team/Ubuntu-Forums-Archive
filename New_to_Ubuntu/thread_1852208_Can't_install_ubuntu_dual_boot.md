---
title: "Can't install ubuntu dual boot"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by benpearsonnelson on 2011-09-29
I just got a new laptop and I have tried to install ubuntu as a dual boot option several times from a CD.  Each time, things seem to run smoothly until the last step, when I need to restart.  At that point I get a screen with "Ubuntu" and the five dots, then the line "Please remove installation media and close the tray (if any) and then press ENTER:"
Once I do that, the dots freeze, and then nothing happens.  I checked the disk and it checks out fine (in fact I used it to install ubuntu on another laptop).  
If I do a hard reboot with the cd in, I get the same grub menu I had, as if ubuntu is not installed.
If I do a hard reboot without the cd, windows starts, but gives me a warning that indicates a problem (the same message I get on other computers when I dual boot and then open windows).  I am not sure how to diagnose and fix this issue.  Does anyone know how I can best proceed?  
Thanks,
Ben

---

### Post by TeoBigusGeekus on 2011-09-29
Can you boot up with a live cd, open a terminal, give
```
lshw
```
and post us the results?

---

### Post by benpearsonnelson on 2011-09-29
> **TeoBigusGeekus said:**
> Can you boot up with a live cd, open a terminal, give
```
lshw
```and post us the results?
  
When I boot up with the live cd, open a terminal, I can run lshw but, I cannot figure out how to copy the output or  even close the terminal.   If you can advise me on that, it would be great.  Otherwise is there some output I should look for that might be a red flag?

---

### Post by benpearsonnelson on 2011-09-29
> **benpearsonnelson said:**
> When I boot up with the live cd, open a terminal, I can run lshw but, I cannot figure out how to copy the output or  even close the terminal.   If you can advise me on that, it would be great.  Otherwise is there some output I should look for that might be a red flag?
 
I figured out how to copy and save the output:
```

                     p { margin-bottom: 0.08in; }            size: 128KiB  
           capacity: 1984KiB  
           capabilities: pci upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer int10video pc98 acpi usb biosbootspecification netboot  
      *-memory  
           description: System Memory  
           physical id: 2d  
           slot: System board or motherboard  
           size: 6GiB  
         *-bank:0  
              description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)  
              product: NT2GC64B88B0NS-CG 
              physical id: 0  
              serial: 9267F41B  
              slot: DIMM 0  
              size: 2GiB  
              width: 64 bits  
              clock: 1333MHz (0.8ns)  
         *-bank:1  
              description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)  
              product: NT4GC64B8HB0NS-CG 
              physical id: 1  
              serial: ED70227B  
              slot: DIMM 0  
              size: 4GiB  
              width: 64 bits  
              clock: 1333MHz (0.8ns)  
      *-cpu  
           description: CPU  
           product: AMD A6-3400M APU with Radeon(tm) HD Graphics  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 33  
           bus info: cpu@0  
           version: AMD A6-3400M APU with Radeon(tm) HD Graphics  
           slot: Socket FS1  
           size: 800MHz  
           capacity: 1400MHz  
           width: 64 bits  
           clock: 100MHz  
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter cpufreq  
           configuration: cores=4 enabledcores=4 threads=4  
         *-cache:0  
              description: L1 cache  
              physical id: 34  
              slot: L1 Cache  
              size: 512KiB  
              capacity: 512KiB  
              clock: 1GHz (1.0ns)  
              capabilities: pipeline-burst internal write-back unified  
         *-cache:1  
              description: L2 cache  
              physical id: 35  
              slot: L2 Cache  
              size: 4MiB  
              capacity: 4MiB  
              clock: 1GHz (1.0ns)  
              capabilities: pipeline-burst internal write-back unified  
      *-pci:0  
           description: Host bridge  
           product: Advanced Micro Devices [AMD]  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 00  
           width: 32 bits  
           clock: 66MHz  
           configuration: latency=64  
         *-display UNCLAIMED  
              description: VGA compatible controller  
              product: ATI Technologies Inc  
              vendor: ATI Technologies Inc  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm pciexpress msi vga_controller bus_master cap_list  
              configuration: latency=0  
              resources: memory:e0000000-efffffff ioport:2000(size=256) memory:f0200000-f023ffff  
         *-multimedia:0  
              description: Audio device  
              product: ATI Technologies Inc  
              vendor: ATI Technologies Inc  
              physical id: 1.1  
              bus info: pci@0000:00:01.1 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm pciexpress msi bus_master cap_list  
              configuration: driver=HDA Intel latency=0  
              resources: irq:46 memory:f0244000-f0247fff  
         *-pci:0  
              description: PCI bridge  
              product: Advanced Micro Devices [AMD]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 4  
              bus info: pci@0000:00:04.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:16 memory:f0300000-f03fffff ioport:f0000000(size=1048576)  
            *-network  
                 description: Ethernet interface  
                 product: NetLink BCM57785 Gigabit Ethernet PCIe  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:01:00.0  
                 logical name: eth0  
                 version: 10  
                 serial: 20:6a:8a:4c:f8:28  
                 capacity: 1Gbit/s  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
                 configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb latency=0 link=no multicast=yes port=twisted pair  
                 resources: irq:16 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:f0050000-f00507ff  
            *-generic:0  
                 description: SD Host controller  
                 product: NetXtreme BCM57765 Memory Card Reader  
                 vendor: Broadcom Corporation  
                 physical id: 0.1  
                 bus info: pci@0000:01:00.1  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress bus_master cap_list  
                 configuration: driver=sdhci-pci latency=0  
                 resources: irq:17 memory:f0020000-f002ffff  
            *-generic:1 UNCLAIMED  
                 description: System peripheral  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0.2  
                 bus info: pci@0000:01:00.2  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress cap_list  
                 configuration: latency=0  
                 resources: memory:f0030000-f003ffff  
            *-generic:2 UNCLAIMED  
                 description: System peripheral  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0.3  
                 bus info: pci@0000:01:00.3  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress cap_list  
                 configuration: latency=0  
                 resources: memory:f0040000-f004ffff  
         *-pci:1  
              description: PCI bridge  
              product: Advanced Micro Devices [AMD]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 6  
              bus info: pci@0000:00:06.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:18 memory:f0100000-f01fffff  
            *-network UNCLAIMED  
                 description: Network controller  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:02:00.0  
                 version: 00  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress cap_list  
                 configuration: latency=0  
                 resources: memory:f0100000-f0103fff  
         *-storage  
              description: SATA controller  
              product: Hudson SATA Controller [AHCI mode]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 11  
              bus info: pci@0000:00:11.0 
              logical name: scsi0  
              logical name: scsi1  
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: storage msi ahci_1.0 bus_master cap_list emulated  
              configuration: driver=ahci latency=64  
              resources: irq:40 ioport:2118(size=8) ioport:2124(size=4) ioport:2110(size=8) ioport:2120(size=4) ioport:2100(size=16) memory:f024b000-f024b7ff  
            *-disk  
                 description: ATA Disk  
                 product: WDC WD5000BPVT-2  
                 vendor: Western Digital 
                 physical id: 0  
                 bus info: scsi@0:0.0.0  
                 logical name: /dev/sda  
                 version: 01.0  
                 serial: WD-WXH1E31DPT32 
                 size: 465GiB (500GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=8db51a8d  
               *-volume:0  
                    description: Windows NTFS volume  
                    physical id: 1  
                    bus info: scsi@0:0.0.0,1  
                    logical name: /dev/sda1  
                    version: 3.1  
                    serial: 14f3-f4ce  
                    size: 14GiB  
                    capacity: 14GiB  
                    capabilities: primary ntfs initialized  
                    configuration: clustersize=4096 created=2011-01-24 07:26:01 filesystem=ntfs label=PQSERVICE state=clean  
               *-volume:1  
                    description: Windows NTFS volume  
                    physical id: 2  
                    bus info: scsi@0:0.0.0,2  
                    logical name: /dev/sda2  
                    version: 3.1  
                    serial: 16ff-cabb  
                    size: 94MiB  
                    capacity: 100MiB  
                    capabilities: primary bootable ntfs initialized  
                    configuration: clustersize=4096 created=2011-07-21 12:44:58 filesystem=ntfs label=SYSTEM RESERVED state=clean  
               *-volume:2  
                    description: Windows NTFS volume  
                    physical id: 3  
                    bus info: scsi@0:0.0.0,3  
                    logical name: /dev/sda3  
                    version: 3.1  
                    serial: a4d79531-2074-db44-aeae-fefd424373e5  
                    size: 241GiB  
                    capacity: 241GiB  
                    capabilities: primary ntfs initialized  
                    configuration: clustersize=4096 created=2011-07-21 12:45:09 filesystem=ntfs label=ACER modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true  
               *-volume:3  
                    description: Extended partition  
                    physical id: 4  
                    bus info: scsi@0:0.0.0,4  
                    logical name: /dev/sda4  
                    size: 210GiB  
                    capacity: 210GiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume:0  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 5605MiB 
                       capabilities: nofs  
                  *-logicalvolume:1  
                       description: Linux swap / Solaris partition  
                       physical id: 6  
                       logical name: /dev/sda6  
                       capacity: 5600MiB 
                       capabilities: nofs  
                  *-logicalvolume:2  
                       description: Linux swap / Solaris partition  
                       physical id: 7  
                       logical name: /dev/sda7  
                       capacity: 5604MiB 
                       capabilities: nofs  
                  *-logicalvolume:3  
                       description: Linux swap / Solaris partition  
                       physical id: 8  
                       logical name: /dev/sda8  
                       capacity: 5600MiB 
                       capabilities: nofs  
                  *-logicalvolume:4  
                       description: Linux filesystem partition  
                       physical id: 9  
                       logical name: /dev/sda9  
                       capacity: 183GiB  
                  *-logicalvolume:5  
                       description: Linux swap / Solaris partition  
                       physical id: a  
                       logical name: /dev/sda10  
                       capacity: 5605MiB 
                       capabilities: nofs  
            *-cdrom  
                 description: DVD-RAM writer  
                 product: DVDRAM GT32N  
                 vendor: HL-DT-ST  
                 physical id: 1  
                 bus info: scsi@1:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/dvdrw  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 logical name: /cdrom  
                 version: 1.00  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready  
               *-medium  
                    physical id: 0  
                    logical name: /dev/cdrom  
                    logical name: /cdrom 
                    configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted  
         *-usb:0  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 12  
              bus info: pci@0000:00:12.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f024a000-f024afff  
         *-usb:1  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 12.2  
              bus info: pci@0000:00:12.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024ba00-f024baff  
         *-usb:2  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 13  
              bus info: pci@0000:00:13.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f0249000-f0249fff  
         *-usb:3  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 13.2  
              bus info: pci@0000:00:13.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024b900-f024b9ff  
         *-serial UNCLAIMED  
              description: SMBus  
              product: Hudson SMBus Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14  
              bus info: pci@0000:00:14.0 
              version: 13  
              width: 32 bits  
              clock: 66MHz  
              configuration: latency=0  
         *-multimedia:1  
              description: Audio device  
              product: Hudson Azalia Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.2  
              bus info: pci@0000:00:14.2 
              version: 01  
              width: 64 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=HDA Intel latency=64  
              resources: irq:16 memory:f0240000-f0243fff  
         *-isa  
              description: ISA bridge  
              product: Hudson LPC Bridge 
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.3  
              bus info: pci@0000:00:14.3 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-pci:2  
              description: PCI bridge  
              product: Hudson PCI Bridge 
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.4  
              bus info: pci@0000:00:14.4 
              version: 40  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci subtractive_decode bus_master  
         *-usb:4  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 16  
              bus info: pci@0000:00:16.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f0248000-f0248fff  
         *-usb:5  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 16.2  
              bus info: pci@0000:00:16.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024b800-f024b8ff  
      *-pci:1  
           description: Host bridge  
           product: Family 12h/14h Processor Function 0  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 101  
           bus info: pci@0000:00:18.0  
           version: 43  
           width: 32 bits  
           clock: 33MHz  
      *-pci:2  
           description: Host bridge  
           product: Family 12h/14h Processor Function 1  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 102  
           bus info: pci@0000:00:18.1  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:3  
           description: Host bridge  
           product: Family 12h/14h Processor Function 2  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 103  
           bus info: pci@0000:00:18.2  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:4  
           description: Host bridge  
           product: Family 12h/14h Processor Function 3  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 104  
           bus info: pci@0000:00:18.3  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=k10temp 
           resources: irq:0  
      *-pci:5  
           description: Host bridge  
           product: Family 12h/14h Processor Function 4  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 105  
           bus info: pci@0000:00:18.4  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:6  
           description: Host bridge  
           product: Family 12h/14h Processor Function 6  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 106  
           bus info: pci@0000:00:18.5  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:7  
           description: Host bridge  
           product: Family 12h/14h Processor Function 5  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 107  
           bus info: pci@0000:00:18.6  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:8  
           description: Host bridge  
           product: Family 12h/14h Processor Function 7  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 108  
           bus info: pci@0000:00:18.7  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
 ubuntu@ubuntu:~$
```

---

### Post by benpearsonnelson on 2011-09-30
Update: I have tried a number of alternative methods for installation.  I burned a new live cd, ran the MD5SUM to insure the disc was good, and then booted into "install ubuntu".  I tried both "update 11.04" and later "reinstall 11.04".  Both times the installation hangs at the end of the process during the "Please remove installation media and close the tray (if any) and then press ENTER:"  So I download a new copy of 11.04, ran the MD5SUM and made a USB.  I tried "reinstall 11.04".  Same result.  Frozen at the end and a reboot just brings up windows.  Here's the output from the terminal code "lshw":
```

                     p { margin-bottom: 0.08in; }   vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 33  
           bus info: cpu@0  
           version: AMD A6-3400M APU with Radeon(tm) HD Graphics  
           slot: Socket FS1  
           size: 800MHz  
           capacity: 1400MHz  
           width: 64 bits  
           clock: 100MHz  
           capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt cpb npt lbrv svm_lock nrip_save pausefilter cpufreq  
           configuration: cores=4 enabledcores=4 threads=4  
         *-cache:0  
              description: L1 cache  
              physical id: 34  
              slot: L1 Cache  
              size: 512KiB  
              capacity: 512KiB  
              clock: 1GHz (1.0ns)  
              capabilities: pipeline-burst internal write-back unified  
         *-cache:1  
              description: L2 cache  
              physical id: 35  
              slot: L2 Cache  
              size: 4MiB  
              capacity: 4MiB  
              clock: 1GHz (1.0ns)  
              capabilities: pipeline-burst internal write-back unified  
      *-pci:0  
           description: Host bridge  
           product: Advanced Micro Devices [AMD]  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 00  
           width: 32 bits  
           clock: 66MHz  
           configuration: latency=64  
         *-display UNCLAIMED  
              description: VGA compatible controller  
              product: ATI Technologies Inc  
              vendor: ATI Technologies Inc  
              physical id: 1  
              bus info: pci@0000:00:01.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm pciexpress msi vga_controller bus_master cap_list  
              configuration: latency=0  
              resources: memory:e0000000-efffffff ioport:2000(size=256) memory:f0200000-f023ffff  
         *-multimedia:0  
              description: Audio device  
              product: ATI Technologies Inc  
              vendor: ATI Technologies Inc  
              physical id: 1.1  
              bus info: pci@0000:00:01.1 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pm pciexpress msi bus_master cap_list  
              configuration: driver=HDA Intel latency=0  
              resources: irq:46 memory:f0244000-f0247fff  
         *-pci:0  
              description: PCI bridge  
              product: Advanced Micro Devices [AMD]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 4  
              bus info: pci@0000:00:04.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:16 memory:f0300000-f03fffff ioport:f0000000(size=1048576)  
            *-network  
                 description: Ethernet interface  
                 product: NetLink BCM57785 Gigabit Ethernet PCIe  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:01:00.0  
                 logical name: eth0  
                 version: 10  
                 serial: 20:6a:8a:4c:f8:28  
                 capacity: 1Gbit/s  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  
                 configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb latency=0 link=no multicast=yes port=twisted pair  
                 resources: irq:16 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:f0050000-f00507ff  
            *-generic:0  
                 description: SD Host controller  
                 product: NetXtreme BCM57765 Memory Card Reader  
                 vendor: Broadcom Corporation  
                 physical id: 0.1  
                 bus info: pci@0000:01:00.1  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress bus_master cap_list  
                 configuration: driver=sdhci-pci latency=0  
                 resources: irq:17 memory:f0020000-f002ffff  
            *-generic:1 UNCLAIMED  
                 description: System peripheral  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0.2  
                 bus info: pci@0000:01:00.2  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress cap_list  
                 configuration: latency=0  
                 resources: memory:f0030000-f003ffff  
            *-generic:2 UNCLAIMED  
                 description: System peripheral  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0.3  
                 bus info: pci@0000:01:00.3  
                 version: 10  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress cap_list  
                 configuration: latency=0  
                 resources: memory:f0040000-f004ffff  
         *-pci:1  
              description: PCI bridge  
              product: Advanced Micro Devices [AMD]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 6  
              bus info: pci@0000:00:06.0 
              version: 00  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list  
              configuration: driver=pcieport  
              resources: irq:18 memory:f0100000-f01fffff  
            *-network  
                 description: Wireless interface  
                 product: Broadcom Corporation  
                 vendor: Broadcom Corporation  
                 physical id: 0  
                 bus info: pci@0000:02:00.0  
                 logical name: eth1  
                 version: 00  
                 serial: cc:af:78:07:73:5e  
                 width: 64 bits  
                 clock: 33MHz  
                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
                 configuration: broadcast=yes driver=wl1 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn  
                 resources: irq:18 memory:f0100000-f0103fff  
         *-storage  
              description: SATA controller  
              product: Hudson SATA Controller [AHCI mode]  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 11  
              bus info: pci@0000:00:11.0 
              logical name: scsi1  
              logical name: scsi2  
              version: 00  
              width: 32 bits  
              clock: 66MHz  
              capabilities: storage msi ahci_1.0 bus_master cap_list emulated  
              configuration: driver=ahci latency=64  
              resources: irq:40 ioport:2118(size=8) ioport:2124(size=4) ioport:2110(size=8) ioport:2120(size=4) ioport:2100(size=16) memory:f024b000-f024b7ff  
            *-disk  
                 description: ATA Disk  
                 product: WDC WD5000BPVT-2  
                 vendor: Western Digital 
                 physical id: 0  
                 bus info: scsi@1:0.0.0  
                 logical name: /dev/sda  
                 version: 01.0  
                 serial: WD-WXH1E31DPT32 
                 size: 465GiB (500GB)  
                 capabilities: partitioned partitioned:dos  
                 configuration: ansiversion=5 signature=8db51a8d  
               *-volume:0  
                    description: Windows NTFS volume  
                    physical id: 1  
                    bus info: scsi@1:0.0.0,1  
                    logical name: /dev/sda1  
                    version: 3.1  
                    serial: 14f3-f4ce  
                    size: 14GiB  
                    capacity: 14GiB  
                    capabilities: primary ntfs initialized  
                    configuration: clustersize=4096 created=2011-01-24 07:26:01 filesystem=ntfs label=PQSERVICE state=clean  
               *-volume:1  
                    description: Windows NTFS volume  
                    physical id: 2  
                    bus info: scsi@1:0.0.0,2  
                    logical name: /dev/sda2  
                    version: 3.1  
                    serial: 16ff-cabb  
                    size: 94MiB  
                    capacity: 100MiB  
                    capabilities: primary bootable ntfs initialized  
                    configuration: clustersize=4096 created=2011-07-21 12:44:58 filesystem=ntfs label=SYSTEM RESERVED state=clean  
               *-volume:2  
                    description: Windows NTFS volume  
                    physical id: 3  
                    bus info: scsi@1:0.0.0,3  
                    logical name: /dev/sda3  
                    version: 3.1  
                    serial: a4d79531-2074-db44-aeae-fefd424373e5  
                    size: 241GiB  
                    capacity: 241GiB  
                    capabilities: primary ntfs initialized  
                    configuration: clustersize=4096 created=2011-07-21 12:45:09 filesystem=ntfs label=ACER modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true  
               *-volume:3  
                    description: Extended partition  
                    physical id: 4  
                    bus info: scsi@1:0.0.0,4  
                    logical name: /dev/sda4  
                    size: 210GiB  
                    capacity: 210GiB  
                    capabilities: primary extended partitioned partitioned:extended  
                  *-logicalvolume:0  
                       description: Linux swap / Solaris partition  
                       physical id: 5  
                       logical name: /dev/sda5  
                       capacity: 5605MiB 
                       capabilities: nofs  
                  *-logicalvolume:1  
                       description: Linux swap / Solaris partition  
                       physical id: 6  
                       logical name: /dev/sda6  
                       capacity: 5600MiB 
                       capabilities: nofs  
                  *-logicalvolume:2  
                       description: Linux swap / Solaris partition  
                       physical id: 7  
                       logical name: /dev/sda7  
                       capacity: 5604MiB 
                       capabilities: nofs  
                  *-logicalvolume:3  
                       description: Linux swap / Solaris partition  
                       physical id: 8  
                       logical name: /dev/sda8  
                       capacity: 5600MiB 
                       capabilities: nofs  
                  *-logicalvolume:4  
                       description: Linux swap / Solaris partition  
                       physical id: 9  
                       logical name: /dev/sda9  
                       capacity: 5605MiB 
                       capabilities: nofs  
                  *-logicalvolume:5  
                       description: Linux filesystem partition  
                       physical id: a  
                       logical name: /dev/sda10  
                       capacity: 177GiB  
                  *-logicalvolume:6  
                       description: Linux swap / Solaris partition  
                       physical id: b  
                       logical name: /dev/sda11  
                       capacity: 5602MiB 
                       capabilities: nofs  
            *-cdrom  
                 description: DVD-RAM writer  
                 product: DVDRAM GT32N  
                 vendor: HL-DT-ST  
                 physical id: 1  
                 bus info: scsi@2:0.0.0  
                 logical name: /dev/cdrom  
                 logical name: /dev/cdrw 
                 logical name: /dev/dvd  
                 logical name: /dev/dvdrw  
                 logical name: /dev/scd0 
                 logical name: /dev/sr0  
                 version: 1.00  
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram  
                 configuration: ansiversion=5 status=nodisc  
         *-usb:0  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 12  
              bus info: pci@0000:00:12.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f024a000-f024afff  
         *-usb:1  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 12.2  
              bus info: pci@0000:00:12.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024ba00-f024baff  
         *-usb:2  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 13  
              bus info: pci@0000:00:13.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f0249000-f0249fff  
         *-usb:3  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 13.2  
              bus info: pci@0000:00:13.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024b900-f024b9ff  
         *-serial UNCLAIMED  
              description: SMBus  
              product: Hudson SMBus Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14  
              bus info: pci@0000:00:14.0 
              version: 13  
              width: 32 bits  
              clock: 66MHz  
              configuration: latency=0  
         *-multimedia:1  
              description: Audio device  
              product: Hudson Azalia Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.2  
              bus info: pci@0000:00:14.2 
              version: 01  
              width: 64 bits  
              clock: 33MHz  
              capabilities: pm bus_master cap_list  
              configuration: driver=HDA Intel latency=64  
              resources: irq:16 memory:f0240000-f0243fff  
         *-isa  
              description: ISA bridge  
              product: Hudson LPC Bridge 
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.3  
              bus info: pci@0000:00:14.3 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-pci:2  
              description: PCI bridge  
              product: Hudson PCI Bridge 
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 14.4  
              bus info: pci@0000:00:14.4 
              version: 40  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pci subtractive_decode bus_master  
         *-usb:4  
              description: USB Controller  
              product: Hudson USB OHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 16  
              bus info: pci@0000:00:16.0 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ohci bus_master  
              configuration: driver=ohci_hcd latency=64  
              resources: irq:18 memory:f0248000-f0248fff  
         *-usb:5  
              description: USB Controller  
              product: Hudson USB EHCI Controller  
              vendor: Hynix Semiconductor (Hyundai Electronics)  
              physical id: 16.2  
              bus info: pci@0000:00:16.2 
              version: 11  
              width: 32 bits  
              clock: 66MHz  
              capabilities: pm debug ehci bus_master cap_list  
              configuration: driver=ehci_hcd latency=64  
              resources: irq:17 memory:f024b800-f024b8ff  
      *-pci:1  
           description: Host bridge  
           product: Family 12h/14h Processor Function 0  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 101  
           bus info: pci@0000:00:18.0  
           version: 43  
           width: 32 bits  
           clock: 33MHz  
      *-pci:2  
           description: Host bridge  
           product: Family 12h/14h Processor Function 1  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 102  
           bus info: pci@0000:00:18.1  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:3  
           description: Host bridge  
           product: Family 12h/14h Processor Function 2  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 103  
           bus info: pci@0000:00:18.2  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:4  
           description: Host bridge  
           product: Family 12h/14h Processor Function 3  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 104  
           bus info: pci@0000:00:18.3  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=k10temp 
           resources: irq:0  
      *-pci:5  
           description: Host bridge  
           product: Family 12h/14h Processor Function 4  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 105  
           bus info: pci@0000:00:18.4  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:6  
           description: Host bridge  
           product: Family 12h/14h Processor Function 6  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 106  
           bus info: pci@0000:00:18.5  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:7  
           description: Host bridge  
           product: Family 12h/14h Processor Function 5  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 107  
           bus info: pci@0000:00:18.6  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-pci:8  
           description: Host bridge  
           product: Family 12h/14h Processor Function 7  
           vendor: Hynix Semiconductor (Hyundai Electronics)  
           physical id: 108  
           bus info: pci@0000:00:18.7  
           version: 00  
           width: 32 bits  
           clock: 33MHz  
      *-scsi  
           physical id: 1  
           bus info: usb@3:2  
           logical name: scsi0  
           capabilities: emulated scsi-host  
           configuration: driver=usb-storage  
         *-disk  
              description: SCSI Disk  
              physical id: 0.0.0  
              bus info: scsi@0:0.0.0  
              logical name: /dev/sdb  
              size: 984MiB (1031MB)  
              capabilities: partitioned partitioned:dos  
              configuration: signature=00004ac1  
            *-volume  
                 description: Windows FAT volume  
                 vendor: SYSLINUX  
                 physical id: 1  
                 bus info: scsi@0:0.0.0,1  
                 logical name: /dev/sdb1 
                 logical name: /cdrom  
                 version: FAT32  
                 serial: 14fc-0c66  
                 size: 983MiB  
                 capacity: 983MiB  
                 capabilities: primary bootable fat initialized  
                 configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
```

---

### Post by benpearsonnelson on 2011-09-30
I am not sure if this helps, but I found a post where someone had a problem with installation and they were asked for the output of "lspci -n" and "free".  So here it is in case there is something useful:

Output for "lspci -n":

                     p { margin-bottom: 0.08in; }  00:00.0 0600: 1022:1705  
 00:01.0 0300: 1002:9647  
 00:01.1 0403: 1002:1714  
 00:04.0 0604: 1022:1709  
 00:06.0 0604: 1022:170b  
 00:11.0 0106: 1022:7804  
 00:12.0 0c03: 1022:7807 (rev 11)  
 00:12.2 0c03: 1022:7808 (rev 11)  
 00:13.0 0c03: 1022:7807 (rev 11)  
 00:13.2 0c03: 1022:7808 (rev 11)  
 00:14.0 0c05: 1022:780b (rev 13)  
 00:14.2 0403: 1022:780d (rev 01)  
 00:14.3 0601: 1022:780e (rev 11)  
 00:14.4 0604: 1022:780f (rev 40)  
 00:16.0 0c03: 1022:7807 (rev 11)  
 00:16.2 0c03: 1022:7808 (rev 11)  
 00:18.0 0600: 1022:1700 (rev 43)  
 00:18.1 0600: 1022:1701  
 00:18.2 0600: 1022:1702  
 00:18.3 0600: 1022:1703  
 00:18.4 0600: 1022:1704  
 00:18.5 0600: 1022:1718  
 00:18.6 0600: 1022:1716  
 00:18.7 0600: 1022:1719  
 01:00.0 0200: 14e4:16b5 (rev 10)  
 01:00.1 0805: 14e4:16bc (rev 10)  
 01:00.2 0880: 14e4:16be (rev 10)  
 01:00.3 0880: 14e4:16bf (rev 10)  
 02:00.0 0280: 14e4:4358  
 

 And the output for the terminal command &#8220;free&#8221;:
 

 bash: /usr/bin/free: Input/output error

---

### Post by Blasphemist on 2011-09-30
Normally after installing linux for the first time as dual boot with windows, windows prompts for a chkdsk. You follow the prompt, run that and all it good. Are you doing that?

As for why windows is still booting, during the install where did you choose to install the boot loader? 

Now your partitioning is all messed up. You've kept creating new linux and swap partitions each time you try doing the same thing. You have installed successfully multiple times except you don't seem to be succeeding in getting the boot loader to write to the master boot record, mbr. 

Do you have a setting in bios for protection of the mbr and if so can you change it? If so, we can help you fix the partitions and get the boot loader installed. Please see this program to get the boot loader written to the mbr. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You likely do have protection in bios in place that is keeping the mbr protected and that does need changed. This program will also create a summary that we can review for better specifics. Please post the url it gives you and we'll look it over and help correct the partition mess.

---

### Post by oldfred on 2011-09-30
+1 on Blasphemist suggestion of boot repair.

Boot repair will offer to download boot_info_script which gives us a lot of info on how you have system configured.  And boot repair may also fix system.

Also please use code tags for long data/code listings. From the new message screen, you can auto add code tags by highlighting what you want and clicking on the # in the edit panel. If updated your posts.

---

### Post by benpearsonnelson on 2011-09-30
I did get the windows chkdsk prompt and it ran without problem.

As for why windows is still booting: I did not have an option during install to choose the bootloader.  However, the original live CD I used on another laptop worked fine and again, without me choosing a bootloader, automatically gave me the option to use either windows or ubuntu (in fact ubuntu was the default, which was great).

I will run the boot repair and report back.

Thanks for your help,
Ben

---

### Post by benpearsonnelson on 2011-09-30
> **oldfred said:**
> +1 on Blasphemist suggestion of boot repair.

Boot repair will offer to download boot_info_script which gives us a lot of info on how you have system configured.  And boot repair may also fix system.

Also please use code tags for long data/code listings. From the new message screen, you can auto add code tags by highlighting what you want and clicking on the # in the edit panel. If updated your posts.

Thank you.  I apologize for the cut and paste.

---

### Post by benpearsonnelson on 2011-09-30
Sad.  I installed and ran boot-repair.  Twice.  The first time I tried to shut down ubuntu and it asked me to remove the [usb] and press enter.  I did.  And nothing happened just frozen.  When did a hard reboot, windows started, and prompted chkdsk, which checked out.  And then restarted windows, which again promped chkdsk.  I did another hard reboot, replaced my usb, restarted ubuntu, reran boot-repair.  The URL that resulted is: 
[http://paste.ubuntu.com/700046/](http://paste.ubuntu.com/700046/)
I tried to shut down.  Ended up at the same frozen place: 
"Please remove installation media and close the tray (if any) and then press ENTER:"
Did that and the dots stopped and then: nothing.  Just frozen.  
I really appreciate your help.  Either I am not clever enough to master this install (likely) or there is some idiosyncratic problem with this laptop that prevents proper installation (less likely).

---

### Post by Blasphemist on 2011-09-30
While I review the summary, did you look in bios for any setting that may be protecting the mbr?

Oh, sometimes you do need to do chkdsk more than once.

---

### Post by oldfred on 2011-09-30
I have not seen the swsuspend. Did you at some poiht suspend the system? You do have a lot of swaps, all but the last one can be deleted. But those are not your problem.

Do you have a BIOS that prevents writing into the MBR or a Windows virus program that prevents it?

These were reported by others as issues:
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem

I see Blasphemist just beat me to it.:)

---

### Post by benpearsonnelson on 2011-09-30
> **Blasphemist said:**
> While I review the summary, did you look in bios for any setting that may be protecting the mbr?

Oh, sometimes you do need to do chkdsk more than once.
Hmm.  I do not know how to do that.  I can press F2 and pull up "Phoenix SecureCore Tiano Setup" which gives me: "Information, Main, Security, Boot, and Exit" categories, but how I find any setting that may be protecting the mbr is unknown to me.

---

### Post by benpearsonnelson on 2011-09-30
> **oldfred said:**
> I have not seen the swsuspend. Did you at some poiht suspend the system? You do have a lot of swaps, all but the last one can be deleted. But those are not your problem.

Do you have a BIOS that prevents writing into the MBR or a Windows virus program that prevents it?

These were reported by others as issues:
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
core unlocker feature on asus m4a87td usb3 was causing the problem

I see Blasphemist just beat me to it.:)

I need some forensic insight.  I do not know how to show swsuspend.  I am not sure if I suspended the system, but surely I did not intentionally.  And whether or not BIOS has a setting that prevents writing to the MBR (or a preventative windows virus program) is not clear to me.  The more questions you ask, the more clear it becomes I am operating way above my pay grade.

---

### Post by Blasphemist on 2011-09-30
Do press F2 and go into setup (that's what we are referring to as bios) and check each menu especially boot for anything that may be involved with protecting the master boot record.

---

### Post by benpearsonnelson on 2011-09-30
Boot has only "Boot Priority Order"
1.  USB HDD:
2.  USB FDD:
3.  USB CDROM
4.  HDDO: WDC WD5000BPVT-22HXZT1
5. ATAPI CDROM: HL-DT-STDVDRAM GT32N
6. Network Boot: BRCM MBA Slot 0100 v14.6.9

Security has:
1. Supervisor Password is: Clear
2. User Password is : Clear
3. HDD Password State Clear
4. Set Supervisor Password [Enter]
5. Set Supervisor Password [Enter]
6.  Password on Boot [Disabled]

Main has:
1.  System time [16:59:58]
2.  System Date: [09/30/2011]
3.  Total Memory: 6144 MB
4.  Video Memory: 512 MB
5.  Quiet Boot: [Enabled]32
6.  Network Boot: [Enabled]
7.  F12 Boot Menu: [Disabled]
8.  D2D Recovery: [Enabled]
9.  SATA Mode: [AHCI Mode]

Information has:
CPU Type: AMD A6-3400M APU with Radeon(tm) HD Graphics
CPU Speed: 1.40GHz
HDD Model Name: WDC WD5000BPVT-22HXZT1
HDD Serial Number: WD-WXH1E31DPT32
ATAPI Model Name: HL-DT-STDVDRAM GT32N
System BIOS Version: BK-ATI VERO12.043.000.014.040915
KBC Version: 1.07
Serial Number: LXRNTO2O571290A6352000
Asset Tag Number: No Asset Tag
Product Name: Aspire 5560
Manufacturer Name: Acer
UUID: EF6FA140-B379-11EO-91D6-96A69A37A52D

---

### Post by oldfred on 2011-09-30
Someone posted once that quiet boot caused problems. Try turning that off. Also enable f12 boot. There should be some place else that chooses which hard drive or when you click on hard drive it gives additional choices.

---

### Post by benpearsonnelson on 2011-09-30
I disabled quiet boot, and enabled f12 boot.  Then I closed the bios and windows started right up.  I restarted and windows started up again.  I listed every category and the options I have in bios.  Do you have any idea where I might locate a choice for hard drive or a place to click on hard drive to give additional options?

---

### Post by viperdvman on 2011-09-30
With a newer laptop, I assume you're running Windows 7, correct? Now, when you installed Ubuntu, did you install GRUB to the MBR or to the same partition that Ubuntu is on?

If you tried to install to the MBR, and you're still getting Windows, then something is preventing you from writing to the MBR. There is a way around that. I would suggest installing Ubuntu **again** and, when the options come up, installing GRUB to the same partition as Ubuntu. Once you've done that, or if you already have, then you'll want to download and install a program to your Windows called **EasyBCD** (preferably the latest version). That program allows you to manipulate the Windows Vista/7 bootloader and allow you to add the Ubuntu entry and point it to the partition where Ubuntu is loaded.

Hopefully, this helps you get around your MBR problem. I boot my Ubuntu with the Windows bootloader on both my desktop and netbook and don't mind it one bit.

---

### Post by Blasphemist on 2011-09-30
Good progress! Now that you made the change, have you tried boot-repair to see if it could get grub2 working? Let us know how that and/or easybcd works!

---

### Post by benpearsonnelson on 2011-09-30
I reran boot-repair, but had the same outcome.   When I tried to shut down ubuntu the screen froze after I removed the usb and hit enter.  I did a hard reboot and windows restarted, prompted and ran chkdsk twice and then opened.  

I am currently running windows 7.  Oddly, I installed ubuntu on an HP running windows 7 with the original live cd I used in this series of installations and had no problem.

I did not get an option in terms of installing GRUB to the MRB when installing.  The only questions I am asked are: where I live, a user name, and password.  I do not know how ot install GRUB to the MRB either during installation or otherwise.  I will do some research to see if I can figure out how to do that.

I will also install EASY BCD and see if that helps.

Thanks for your help.

---

### Post by benpearsonnelson on 2011-09-30
> **viperdvman said:**
> With a newer laptop, I assume you're running Windows 7, correct? Now, when you installed Ubuntu, did you install GRUB to the MBR or to the same partition that Ubuntu is on?

If you tried to install to the MBR, and you're still getting Windows, then something is preventing you from writing to the MBR. There is a way around that. I would suggest installing Ubuntu **again** and, when the options come up, installing GRUB to the same partition as Ubuntu. Once you've done that, or if you already have, then you'll want to download and install a program to your Windows called **EasyBCD** (preferably the latest version). That program allows you to manipulate the Windows Vista/7 bootloader and allow you to add the Ubuntu entry and point it to the partition where Ubuntu is loaded.

Hopefully, this helps you get around your MBR problem. I boot my Ubuntu with the Windows bootloader on both my desktop and netbook and don't mind it one bit.

I downloaded EasyBCD 2.1 and it allows me to add linux.  I am just not sure which options to use.  Under "type" it lists GRUB (Legacy), GRUB 2, LIL)/eLILO, FreeBSD/PC-BSD, Wubi, or SysLinux.

Also, under "device" it lists 10 partitions (I believe a product of me repeatedly trying to install ubuntu) but I am not sure which one to choose.  The list is: Drive 0, Partition 1 (0x27-14 GiB), Partition 2 (NTFS- 100MiB), Partition 3  (C:\ as NTFS - 241 GiB), Partitons 4-8 (Swap - 5 GiB), Partition 9 (Linux 178 GiB), and Partition 10 (swap - 5 GiB).

---

### Post by benpearsonnelson on 2011-09-30
All right it looks like GRUB2 is the default for ubuntu.  And then the EasyBCD automatically detects the partition.  I made that selection and when I booted windows I got a new option for NeoSmart Linux.  I selected that and then I get a screen that says: "grub>" with a blinking cursor.  So I am guessing I still need to figure out how to move GRUB to  where ever it needs to be.

---

### Post by benpearsonnelson on 2011-09-30
Is there some way to simplify this process by deleting all the partitions with ubuntu (resetting the computer to an original state with just the partitions used by windows 7) and then reinstalling ubuntu and if I can figure out how, putting GRUB2 where I need it?

If this is a possibility, how do I know what I can delete (I am not sure which partitions are which).

---

### Post by Blasphemist on 2011-09-30
> **benpearsonnelson said:**
> Is there some way to simplify this process by deleting all the partitions with ubuntu (resetting the computer to an original state with just the partitions used by windows 7) and then reinstalling ubuntu and if I can figure out how, putting GRUB2 where I need it?

If this is a possibility, how do I know what I can delete (I am not sure which partitions are which).
Yes you can clean things up, and re-install or not. Don't delete sda1-4. sda4 is the extended partition in which all of the Linux partitions have been created. sda5-9 can be deleted. sda10 and sda 11 are Ubuntu and the swap I'd keep. I guess if you don't mind re-installing you should delete sda10 and sda11 just because those partition numbers may change when you delete the swaps that aren't needed. Even if you delete all of the logical partitions sda5-11 there is no need to delete the extended partition.

Please see my GParted screen shot. You need to run GParted from the live cd to delete the partitions. Notice that the partition numbers are not the same order as on the physical disk. I originally had just what you are doing. Ubuntu installed in addition to win 7 and I had chosen the option to install alongside win 7. Later I decided to have multiple distros and made partition changes myself in GParted. 

You can create the partitions you need in GParted and that is my recommendation. See how much progress you've made that I'd recommend that! In the existing extended partition, you should create a logical partition that takes up all of the extended except a few GB at the end of the disk. Leave enough at the end for a little bigger than the amount of memory you have. And create a swap partition in that space. Note that as in my screen shot it may leave a few MB at the in between partitions or at the end un-used.

GParted is really quite user friendly. You can modify partitions by dragging the sides or using the combo boxes in the dialogs. The biggest thing to understand and remember is that what I'm discussing here are changes to partitions within the extended partition and all of your windows are in the primary partitions sda1-3. If you look at the properties of your sda1 you'll notice it doesn't start at 0000. There is space before sda1. That is where the MBR is. That space is so small it is hard to see in GParted because it is small and not in a partition.

After you've prepared the partitions using GParted from the live cd, you can install. I can't remember if it prompts you to reboot after the changes before you go into the install. During the installation you'll come to an allocate disk space screen. Choose the "Something Else" option to manually specify what partitions to use, instead of the option to use the available space, if you have created the partitions to use. Long sentence, hope it made sense. If you want, use this great site from forum user Herman on doing all of this. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

When you use the something else manual process, you'll want to set these partition properties. For the ubuntu partition, format it to EXT4, set its mount point as root (/) and don't set any flags on it. There isn't much to do to the swap partition other than tell it to be a swap. There are other partitions that could be created with mount points such as /Home but that is more complexity than you need for now in my opinion. That is covered on Herman's site if you want to think about it. It puts all of your personal files and settings on a separate partition. 

And also do post back any questions you may have.

---

### Post by GregA on 2011-10-01
Have you tried to install Ubuntu via a CD versus USB devices?  On a very few systems,, USB installs are not yet reliable.  Also, via the BIOS, change the boot order to CD first (above the USB).   Then download a new iso image & burn to CD using no faster than 8x.  Upon install, the CD should provide a selection option for you on where to install Grub2 (which should be to the MBR of SD0).

---

### Post by benpearsonnelson on 2011-10-01
> **Blasphemist said:**
> Yes you can clean things up, and re-install or not. Don't delete sda1-4. sda4 is the extended partition in which all of the Linux partitions have been created. sda5-9 can be deleted. sda10 and sda 11 are Ubuntu and the swap I'd keep. I guess if you don't mind re-installing you should delete sda10 and sda11 just because those partition numbers may change when you delete the swaps that aren't needed. Even if you delete all of the logical partitions sda5-11 there is no need to delete the extended partition.[http://ubuntuforums.org/newreply.php?do=newreply&p=11300772](http://ubuntuforums.org/newreply.php?do=newreply&p=11300772)

Please see my GParted screen shot. You need to run GParted from the live cd to delete the partitions. Notice that the partition numbers are not the same order as on the physical disk. I originally had just what you are doing. Ubuntu installed in addition to win 7 and I had chosen the option to install alongside win 7. Later I decided to have multiple distros and made partition changes myself in GParted. 

You can create the partitions you need in GParted and that is my recommendation. See how much progress you've made that I'd recommend that! In the existing extended partition, you should create a logical partition that takes up all of the extended except a few GB at the end of the disk. Leave enough at the end for a little bigger than the amount of memory you have. And create a swap partition in that space. Note that as in my screen shot it may leave a few MB at the in between partitions or at the end un-used.

GParted is really quite user friendly. You can modify partitions by dragging the sides or using the combo boxes in the dialogs. The biggest thing to understand and remember is that what I'm discussing here are changes to partitions within the extended partition and all of your windows are in the primary partitions sda1-3. If you look at the properties of your sda1 you'll notice it doesn't start at 0000. There is space before sda1. That is where the MBR is. That space is so small it is hard to see in GParted because it is small and not in a partition.

After you've prepared the partitions using GParted from the live cd, you can install. I can't remember if it prompts you to reboot after the changes before you go into the install. During the installation you'll come to an allocate disk space screen. Choose the "Something Else" option to manually specify what partitions to use, instead of the option to use the available space, if you have created the partitions to use. Long sentence, hope it made sense. If you want, use this great site from forum user Herman on doing all of this. [http://members.iinet.net.au/~herman546/index.html]("http://members.iinet.net.au/%7Eherman546/index.html")

When you use the something else manual process, you'll want to set these partition properties. For the ubuntu partition, format it to EXT4, set its mount point as root (/) and don't set any flags on it. There isn't much to do to the swap partition other than tell it to be a swap. There are other partitions that could be created with mount points such as /Home but that is more complexity than you need for now in my opinion. That is covered on Herman's site if you want to think about it. It puts all of your personal files and settings on a separate partition. 

And also do post back any questions you may have.

Thank you so much for the detailed instructions.  I used GParted to erase the extra swap partitions and even the partitions I had for ubuntu.  Then I created new partitions (a small one for windows and a mammoth one for ubuntu and one for swap).  I am reinstalling ubuntu as we speak.  I really appreciate your patience and careful teaching. This has been a frustrating experience, but you have given me renewed hope and optimism.  And I have learned a great deal.   I will keep you posted.

---

### Post by benpearsonnelson on 2011-10-01
> **GregA said:**
> Have you tried to install Ubuntu via a CD versus USB devices?  On a very few systems,, USB installs are not yet reliable.  Also, via the BIOS, change the boot order to CD first (above the USB).   Then download a new iso image & burn to CD using no faster than 8x.  Upon install, the CD should provide a selection option for you on where to install Grub2 (which should be to the MBR of SD0).

Indeed I have.  I actually tried two different live CDs that I had checked out using MD5SUM to insure integrity.  I only create the USB pendrive to see if, perhaps, there was some problem with reading from the cd.  I still have not found a selection option (during installation) for where to install Grub2, but I am hoping by wiping the slate clean, and following the instructions using GParted, maybe I will be in the clear.  If not, I will still have to figure out where and how I insure Grub2 ends up on the MBR of SD0.  Thanks for your help.

---

### Post by benpearsonnelson on 2011-10-01
update: Once I reinstalled ubuntu and used the "other" option to specify that I wanted  ubuntu on my newly created partition formatted to EXT4 and my newly created partition for the swap as swap, I shut down (after the installation was complete).  The screen froze at the same point: please remove the disk from the tray.  I did a hard reboot and a windows menu opened up giving me the option to use windows or Neosmart linux (these options a product of me using the EasyBCD software).  I choose Neosmart linux, but just got "grub>" followed by a blinking cursor.  It appears that I need to find a way to put Grub2 somewhere where it will open when I am booting, but I am at a loss for how to make that happen.  Or am I missing something else that I should be doing?

---

### Post by oldfred on 2011-10-01
I do not fully understand EasyBCD, but I thought you had to install grub2's boot loader to the PBR, partition boot sector of the partition you install the system to. 

Normally grub2 is not recommended to install to a PBR as it has to squeeze itself into a smaller space and uses hardcoded links to the rest of grub. It works until grub gets updated and then you may have to reinstall as the hard coded address may change. Since that is less reliable or you have to know to reinstall occassionally it is not recommended. Using easyBCD makes Windows 7 somewhat more reliable if you have some virus checkers that think grub is a virus in the MBR, use DRM software that writes hidden info in the same space as grub and maybe a few other cases. Most users do not have issues with grub2, some like EasyBCD.

---

### Post by Blasphemist on 2011-10-01
Well I don't know why this is being such a pain! When you get the grub> prompt, is you type this what does it show.
```
set
```
And this too.
```
ls
```
It looks to me like the way easybcd plans to work is to pass off booting linux to grub2 on your ubuntu partition. It then wants you to set the grub2 timeout to 0 so it doesn't show. I suppose this would work for now but if you ever want to add another distro or version it just complicates it. 

Fred- Aren't we showing that the mbr can be written to by getting easybcd installed? What the heck else could be stopping a normal grub installation?

---

### Post by oldfred on 2011-10-01
I do not think EasyBCD changes MBR. Windows in MBR just chainloads to the PBR and I think Easy may just change PBR to load its files instead of bootmgr or have a modified bootmgr or just a special BCD? Just do not know details and I only have XP so I cannot test partitions with BCD.

---

### Post by Junior41180 on 2011-10-01
using easybcd is good, make sure when you choose the "install option" under linux choose grub2, easyBCD will automatically look at all your hard drives and locate where grub2 has been written to.

if it's not finding it, then you never wrote to the MBR of any disk. The Grub option in easyBCD requires you actually set which drive grub is installed to. and from what i read from the pastebin above.

```

Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

```looks like some kind of boot loader is set to sdb (second harddrive in system) not sda, more than likely easyBCD did this.. not sure if thats your issue, grub is also installed to sda11, which could be an issue as well. if you edit syslinux to look at sda11, that may fix that issue. or what i suggest is delete all linux partitions, and start from scratch using manual options for partitioning, and make a boot, swap, / (or root), and a home partition. Just my opinion considering the Automatic option isn't working for you, that also allows for you to set where grub2 installs the bootloader.

again hope it helps a little.



Hope this helps.


> **oldfred said:**
> I do not think EasyBCD changes MBR. Windows in  MBR just chainloads to the PBR and I think Easy may just change PBR to  load its files instead of bootmgr or have a modified bootmgr or just a  special BCD? Just do not know details and I only have XP so I cannot  test partitions with BCD.

as far as i know it writes to the MBR, it can also set either windows or linux as your primary bootloaders..

```

There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \windows\system32\winload.exe

Entry #2
Name: Kubuntu
BCD ID: {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

```

Extended output below
```

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
resumeobject            {cebe4e89-6d8f-11e0-9aa7-dfb2d77c9d3d}
displayorder            {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
                        {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 10

Windows Boot Loader
-------------------
identifier              {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
device                  partition=C:
path                    \windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
recoverysequence        {cebe4e8b-6d8f-11e0-9aa7-dfb2d77c9d3d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \windows
resumeobject            {cebe4e89-6d8f-11e0-9aa7-dfb2d77c9d3d}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
device                  partition=C:
path                    \NST\AutoNeoGrub0.mbr
description             Kubuntu

```this is how my laptop is set up to use windows, not Grub2 as the primary.

---

### Post by benpearsonnelson on 2011-10-01
> **Blasphemist said:**
> Well I don't know why this is being such a pain! When you get the grub> prompt, is you type this what does it show.
```
set
```And this too.
```
ls
```It looks to me like the way easybcd plans to work is to pass off booting linux to grub2 on your ubuntu partition. It then wants you to set the grub2 timeout to 0 so it doesn't show. I suppose this would work for now but if you ever want to add another distro or version it just complicates it. 

Fred- Aren't we showing that the mbr can be written to by getting easybcd installed? What the heck else could be stopping a normal grub installation?
  
I took linux off of my easybcd menu and then readded it to see if it would find grub2 since I erased the linux partitions, made new partitions, and then reinstalled last night.  When I rebooted, I chose neolinux and got the same "grub>" followed  by a blinking cursor.  when I type "set" nothing happens.  It just prompts another "grub>" and cursor.  When I type "ls" I get

  ```
elements $AttrDef $BadClus $Bitmap $Boot $Extend $LogFile $MFT $MFTMirr $Recycle.Bin $Secure $UpCase $Volume ANGO BOOK bootmgr BOOTSECT.BAK bootsqm.dat Documents\ and\ Settings DOCUME~1 Dolby\ PCEE4 DOLBYP~1 hiberfil.sys NST OEM pagefile.sys Patch.rev PerfLogs Preload.rev Program\ Files Program\ Files\ (x86) ProgramData PROGRA~1 PROGRA~2 PROGRA~3 Recovery RHDSetup.log System\ Volume\ Information SYSTEM~1 Users Windows
```

I am not sure if there is some line of code I should used to actually get into ubuntu from that "grub<" line.

---

### Post by benpearsonnelson on 2011-10-01
> **Junior41180 said:**
> using easybcd is good, make sure when you choose the "install option" under linux choose grub2, easyBCD will automatically look at all your hard drives and locate where grub2 has been written to.

if it's not finding it, then you never wrote to the MBR of any disk. The Grub option in easyBCD requires you actually set which drive grub is installed to. and from what i read from the pastebin above.

```

Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

```looks like some kind of boot loader is set to sdb (second harddrive in system) not sda, more than likely easyBCD did this.. not sure if thats your issue, grub is also installed to sda11, which could be an issue as well. if you edit syslinux to look at sda11, that may fix that issue. or what i suggest is delete all linux partitions, and start from scratch using manual options for partitioning, and make a boot, swap, / (or root), and a home partition. Just my opinion considering the Automatic option isn't working for you, that also allows for you to set where grub2 installs the bootloader.

again hope it helps a little.



Hope this helps.




as far as i know it writes to the MBR, it can also set either windows or linux as your primary bootloaders..

```

There are a total of 2 entries listed in the bootloader.

Default: Windows 7
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \windows\system32\winload.exe

Entry #2
Name: Kubuntu
BCD ID: {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
Drive: C:\
Bootloader Path: \NST\AutoNeoGrub0.mbr

```Extended output below
```

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
resumeobject            {cebe4e89-6d8f-11e0-9aa7-dfb2d77c9d3d}
displayorder            {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
                        {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 10

Windows Boot Loader
-------------------
identifier              {cebe4e8a-6d8f-11e0-9aa7-dfb2d77c9d3d}
device                  partition=C:
path                    \windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
recoverysequence        {cebe4e8b-6d8f-11e0-9aa7-dfb2d77c9d3d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \windows
resumeobject            {cebe4e89-6d8f-11e0-9aa7-dfb2d77c9d3d}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {cebe4e90-6d8f-11e0-9aa7-dfb2d77c9d3d}
device                  partition=C:
path                    \NST\AutoNeoGrub0.mbr
description             Kubuntu

```this is how my laptop is set up to use windows, not Grub2 as the primary.

I did erase all the linux partitions and make new partitions, and assigned a root, and a swap, but not a boot, so maybe that is my problem.  I will erase the partitions again, and correct that.  And report back.  Thanks for your help.

---

### Post by benpearsonnelson on 2011-10-01
Just to make sure I understand correctly: I just used GParted to delete the linux partitions so I now have /dev/sda1-3 which are ntfs (the windows partitions) and /dev/sda4 which is an extended file system and where I will specify my root (/) to go.  Also two unallocated partitions are listed, although one must be the same partition as sda4, because the first unallocated partition is listed at 346.54 GiB (the same as sda4), and I only have 500 total.  

I also created an new partition at the end for the swap (7 GiB).  Where should I specify the boot to go?  Do I create another partition or does it go in one I have already?

---

### Post by oldfred on 2011-10-02
The /boot folder is just part of / (root) with most desktops. 

You normally install the grub2 boot loader to the MBR, but with EasyBCD, I think you have to install the grub2 bootloader to the PBR or the / partition. Normally that is not recommended and you may have to reinstall grub2's bootloader on every grub update.

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by benpearsonnelson on 2011-10-02
Well I have tried a few things.  I deleted the linux partitions and reinstalled manually specifying the / and swap partitions and using sda as the device for boot loader intallation.  The installation went smoothly until the very end, where it froze.  I rebooted, went into windows opened EasyBCD, deleted the old linux link and create a new one for Grub2.  Rebooted clicked on Neolinux, and ended up with the same "grub>" line as before.  I rebooted went back into windows and chose "grub (legacy)" instead and directed the software to look to sda.  Rebooted and using Neolinux just got me back to "grub>".
So I reopened linux from the live cd, deleted the linux partitions.  And reinstalled linux.  But this time I specified I wanted the device for bootloader installation on the same partition as my /.  Finished installation, frozen at the end.  Rebooted to windows used EasyBCD to delete the link to linux and then create a new one for GRUB2.  Rebooted and this time I got one option for windows and three for neolinux.  However clicking any of the three just lead me back to "grub>".

At this point, I am wondering if EasyBCD is not causing more complications than it is worth.  I am wondering if I should just remove EasyBCD, go back into linux with the live CD, delete linux again, and just automatically install it.  I realize that I did that the very first time, when I started this journey, but maybe something else I tweaked along the way will allow a proper install.  

Otherwise, I am not sure how to proceed.

---

### Post by benpearsonnelson on 2011-10-02
I uninstalled EasyBCD, booted linux from the live cd, deleted the linux partions, and then tried to automatically install ubuntu.  The process froze in the last stage, I did a hard reboot, and I got the option to use windows or one of three neolinux options.  I went into windows downloaded EasyBCD, deleted the linux options and then reloaded a new option for grub2.  Rebooted I could choose windows or neolinux, I chose neolinux, but just ended up at the same place:
```
grub<
```I am not sure what to try next.  Should I delete and reinstall ubuntu, create partitions and then specify /, swap, and /boot?  I have specified /, and swap and tried a couple of options for the device for boot loader installation, but I have never specified /boot.  If so, should /boot go into my ubuntu partition?

---

### Post by oldfred on 2011-10-02
If the BIOS does not directly lock the MBR from writing, does the McAfee software do something that prevents grub from installing? As it seems to be a continuing issue of grub2's boot loader not installing. But I would not think it could prevent you from installing grub2's boot loader in the PBR of the Ubuntu partition.

---

### Post by Blasphemist on 2011-10-02
From using easybcd, or some dang thing, you are getting left with a grub> prompt but in the windows partition. I can tell that from the ls command results in post 35. 

So the stage of the boot process that is currently written to the mbr is loading the next stage in the windows partition. That just is not working for us at all. I don't even understand how the mbr could be made protected. As it should be, the boot-repair boot info shows the first 2048 are not within a partition. 

I think you should either run boot-repair or reinstall to accomplish having a standard grub2 setup for sure. No boot partiton with grub written to the mbr. I think you should go through the following commands to boot ubuntu and then install and run boot-repair from there. In boot-repair, I'd use the advanced options tabs to ensure it is going to do as you choose.

This is from the grub2 documentation.
> ''grub>'' Prompt Booting
If GRUB 2 leaves you at the grub> prompt, it has normally found the grub folder and loaded at least some basic modules. The configuration file (grub.cfg) may be missing or corrupted.

If the user has confirmed the paths and existence of the proper folders in the previous section, attempt to load the configuration file with the following command:
configfile (hdX,Y)/boot/grub/grub.cfg [COLOR="Red"]This will not work for you.[/COLOR]
If the configuration file is located, the GRUB 2 menu should appear and the user should be able to choose a selection and boot. If the configuration file is not found, a message will be generated and the user must enter the boot commands manually. [COLOR="red"]This is what you need to do.[/COLOR]
Press ENTER after completing each line. Some entries will not provide feedback. This is normal.
If a "file not found" or similar error message is displayed while running these commands, ensure you are using the correct X,Y values. [COLOR="red"]Your X value is a and your Y value is the partition you installed ubuntu last. This is likely 5 now but you can tell using GParted on the live cd if needed.[/COLOR]
Command Summary *:
```
set root=(hdX,Y)
```
```
linux /vmlinuz root=/dev/sdXY ro
```
```
initrd /initrd.img
```
```
boot
```
This is what follows in the documentation.
> Expanded Instructions *:
1.* set root=(hdX,Y)
Type with correct X,Y results confirmed earlier and press ENTER. Remember GRUB 2 counts the first drive as 0, the first partition as 1. Example: If the Ubuntu system is on sda5, enter: set root=(hd0,5)
2.* linux /vmlinuz root=/dev/sdXY ro
Example: linux /vmlinuz root=/dev/sda5 ro
* Wubi users see note.
* Wubi users only - substitute these commands in Steps 1 and 2:
1.* set root=(loop0)
2.* linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
Non-Wubi and Wubi users should now both continue with ...
3. initrd /initrd.img
Selects the latest initrd image.
4. boot
Boot to the latest kernel on the selected partition.
Remember that the commands issued at the grub> prompt are not permanent! After successfully booting into the system the user should run
5. sudo update-grub
and inspect the GRUB 2 configuration file, /boot//grub/grub.cfg. For problems with booting the main linux kernel, ensure the search, linux, and initrd lines in the "### BEGIN /etc/grub.d/10_linux ###" section of the file now correctly point to the correct locations. The user may need to reinstall GRUB 2
6. sudo grub-install /dev/sdX
If the system fails to boot, proceed to the grub rescue> section to run more targeted boot commands.
Steps 5 and 6 won't help in this case and should be done manually or in boot-repair as we know grub2 is not in the mbr. Let's see if we can get to that point have re-installed grub2 from within ubuntu. You may want to post that you were able to get ubuntu booted before the reinstall and see if anyone has come up with other recommendations.

---

### Post by benpearsonnelson on 2011-10-02
I really appreciate you guys sticking with me through this.  You guys have been patient and very thoughtful.  I will go through the recommended steps and report back.  I thought EasyBCD might be interfering or at least making things more complicated, and so I tried removing the software, but the boot menu it created remained intact.  Does anyone know if there is come way to go remove the effects of EasyBCD without, e.g.,  reinstalling windows.

---

### Post by Blasphemist on 2011-10-02
I looked at the bcdedit site again and see that it does not actually write to the mbr, just as fred said if I remember right. So we can't say that anything has been able to change the ipl in the mbr. When installing grub, that is what it's doing when its told to install to sdx. That small ipl just continues the process by loading files from the desired partition. 

Do report back on my previous post please. Your boot process right now is bios, win ipl, win bootloader, hand off to grub for booting linux. The hand off to to grub requires that what normally is done by the little grub ipl stage gets done. That isn't much more than what I've asked you to do in my previous post, set the environment for grub to start the next stage.

---

### Post by benpearsonnelson on 2011-10-03
All right.  I wanted a fresh start, just to make sure I knew where I stood in the process of making changes.  I booted upbuntu from the live cd, used GParted to delete my swap and main linux partition.  Then I reinstalled ubuntu, chose, "do something else" and specified the / partition and the swap partition, and left the default for the "device for bootloader installation".  I followed the process precisely as laid out by Herman (cited earlier in our discussion).  The only difference in my application of the steps is that when Herman created the linux / partition he highlighted "primary" for type of type of new partition, whereas when I highlighted "primary" I could not then create a partition for swap, so I chose "logical" instead.  Once I was finished I went ahead and ran boot repair.

Next, I rebooted and opened windows, opened EasyBCD, removed the linux Grub2 boot option and then reinstalled it.  Then I rebooted and selected Neolinux from my boot menu and got :



```
grub> set root=(hda,5)
grub> linux /vmlinuz root=/dev/sta5 ro

Warning! No such command: linux

grub> initrd /initrd.img
Error 19: Linux kernel must be loaded before initrd

grub> boot
Error 8: Kernel must be loaded before booting
```

---

### Post by oldfred on 2011-10-03
If you copied it you type sta not sda, but I do not think that is the issue.

Grub2 does not have error messages like that. Unless EasyBCD is still in the middle somehow. But I think All Easy does is chain load. It looks like a grub legacy error. But a standard install uses grub2. Does Easy convert back to grub legacy?

Another user with EasyBCD. They have grub2 installed to sda5's partition per boot script.
[http://ubuntuforums.org/showthread.php?t=1852930](http://ubuntuforums.org/showthread.php?t=1852930)

---

### Post by benpearsonnelson on 2011-10-04
Thanks for the information.  I will reinstall ubuntu and try pointing the device for bootloader installation to sda5.  If that doesn't work I will burn a new 32 bit version of the live cd (I have been using the 64 bit version) because someone else reported that solved a booting problem.  I will report back.

---

### Post by benpearsonnelson on 2011-10-04
I reinstalled ubuntu and used sda5 as the device for boot installation.  Then I rebooted into windows and used EasyBCD to delete and reapply a linux boot.  Then I went back into linux using the live CD and ran boot-repair.  Then rebooted, and the neolinux option just takes me to the same "grub>" screen.  The first line reads: GRUB4DOS 0.4.5b 2011-04-23, Mem: 630K/3051M, End: 351489. 

I am burning a new live cd, the 32 bit version, and I am also restoring windows to the point when I first started using the laptop.  Hopefully this step will wipe the slate clean in terms of changes made from windows (e.g., getting rid of EasyBCD).  I can then update the bios settings according to OldFred's recommendations.  Then install the 32 bit version.   This approach should at least simplify the issue.  

Update: Despite restoring windows, the EasyBCD login screen came up again upon  reloading.  I am not sure if there is anyway to disable this program.   If anyone has any tips on that I would appreciate it.

---

### Post by benpearsonnelson on 2011-10-04
Yeah!  Installing the 32 version did the trick!  At the end of the install, I removed the disc, and clicked enter, and the restart kicked in!  My heart skipped a beat.
The normal linux/windows dual boot screen open and I got into ubuntu.  Thank you so much for your help.  Jim and OldFred, you two went above and beyond, and your detailed instructions and discussion were very helpful.  I have learned a great deal from both of you.  Thanks for sticking with me.

---

### Post by Junior41180 on 2011-10-04
> **benpearsonnelson said:**
> I reinstalled ubuntu and used sda5 as the device for boot installation.  Then I rebooted into windows and used EasyBCD to delete and reapply a linux boot.  Then I went back into linux using the live CD and ran boot-repair.  Then rebooted, and the neolinux option just takes me to the same "grub>" screen.  The first line reads: GRUB4DOS 0.4.5b 2011-04-23, Mem: 630K/3051M, End: 351489. 

I am burning a new live cd, the 32 bit version, and I am also restoring windows to the point when I first started using the laptop.  Hopefully this step will wipe the slate clean in terms of changes made from windows (e.g., getting rid of EasyBCD).  I can then update the bios settings according to OldFred's recommendations.  Then install the 32 bit version.   This approach should at least simplify the issue.  

Update: Despite restoring windows, the EasyBCD login screen came up again upon  reloading.  I am not sure if there is anyway to disable this program.   If anyone has any tips on that I would appreciate it.

For future reference for those using easyBCD, gointo and delete the entry and it will restore the normal function of the Windows loader.

But you figured out and fixed your issues. glad you have a working dual boot.

---

### Post by oldfred on 2011-10-04
Glad it worked out.:)

---


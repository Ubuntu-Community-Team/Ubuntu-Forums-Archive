---
title: "Sound isn't working on my HP laptop (13.04)"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by pbandjam on 2013-09-01
Hi guys,    This is my first linux experience so please bare with me if I seem really inexperienced. So I installed 13.04 and everything is working great so far except the sound. What's weird is that the system is detecting the audio device but nothing is playing. The volume is turned all the way up. My laptop is an HP elitebook 6390p.     Any suggestions?    Thanks

---

### Post by Crusty Old Fart on 2013-09-01
Just to eliminate the most simple problem, your laptop should have some manual sound controls above your keyboard towards the right side. If the sound-mute control is lit in amber, then the sound is muted and you need to touch the control to un-mute it. There is also a sound volume slider to the right of the mute button. That needs to be positioned to play loud enough to hear.

If the solution isn't that simple, then please open a terminal window and post the output of the following command:
```

sudo lshw

```
There may be more than one screen full of output. You can drag your mouse over all of it and copy and paste it into a code box in your next post.

---

### Post by pbandjam on 2013-09-02
I tried doing that. By touching the sound it either increases or decreases. But no sound output.   The code I receive is:  >       description: Notebook     product: HP EliteBook 6930p (GW684AV#ABA)     vendor: Hewlett-Packard     version: F.0F     serial: 2CE9162VS0     width: 64 bits     capabilities: smbios-2.4 dmi-2.4 vsyscall32     configuration: boot=normal chassis=notebook family=103C_5336AN sku=GW684AV#ABA uuid=24AAE0D3-B02E-DE11-80BF-58A4B30040AD   *-core        description: Motherboard        product: 30DB        vendor: Hewlett-Packard        physical id: 0        version: KBC Version 87.24      *-firmware           description: BIOS           vendor: Hewlett-Packard           physical id: a           version: 68PCU Ver. F.0F           date: 03/05/2009           size: 64KiB           capacity: 1472KiB           capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot      *-cpu           description: CPU           product: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz           vendor: Intel Corp.           physical id: 0           bus info: cpu@0           version: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz           slot: Intel(R) Genuine processor           size: 2267MHz           capacity: 2267MHz           width: 64 bits           clock: 266MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq         *-cache:0              description: L2 cache              physical id: 1              slot: Internal Cache              size: 3MiB              capacity: 3MiB              capabilities: asynchronous internal write-back unified         *-cache:1              description: L1 cache              physical id: 3              slot: Internal Cache              size: 32KiB              capacity: 32KiB              capabilities: asynchronous internal write-back data      *-cache           description: L1 cache           physical id: 2           slot: Internal Cache           size: 32KiB           capacity: 32KiB           capabilities: asynchronous internal write-back instruction      *-memory           description: System Memory           physical id: 4           slot: System board or motherboard           size: 4GiB         *-bank:0              description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)              product: HYMP125S64CP8-S6              vendor: Hynix              physical id: 0              serial: 00001044              slot: Top              size: 2GiB              width: 64 bits              clock: 800MHz (1.2ns)         *-bank:1              description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)              product: HYMP125S64CP8-S6              vendor: Hynix              physical id: 1              serial: 04008056              slot: Bottom              size: 2GiB              width: 64 bits              clock: 800MHz (1.2ns)      *-pci           description: Host bridge           product: Mobile 4 Series Chipset Memory Controller Hub           vendor: Intel Corporation           physical id: 100           bus info: pci@0000:00:00.0           version: 07           width: 32 bits           clock: 33MHz           configuration: driver=agpgart-intel           resources: irq:0         *-display:0              description: VGA compatible controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2              bus info: pci@0000:00:02.0              version: 07              width: 64 bits              clock: 33MHz              capabilities: msi pm vga_controller bus_master cap_list rom              configuration: driver=i915 latency=0              resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7110(size=8)         *-display:1 UNCLAIMED              description: Display controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation              physical id: 2.1              bus info: pci@0000:00:02.1              version: 07              width: 64 bits              clock: 33MHz              capabilities: pm bus_master cap_list              configuration: latency=0              resources: memory:d0400000-d04fffff         *-network              description: Ethernet interface              product: 82567LM Gigabit Network Connection              vendor: Intel Corporation              physical id: 19              bus info: pci@0000:00:19.0              logical name: eth0              version: 03              serial: 00:24:81:f7:ce:77              width: 32 bits              clock: 33MHz              capabilities: pm msi cap_list ethernet physical              configuration: broadcast=yes driver=e1000e latency=0 multicast=yes              resources: irq:22 memory:d8800000-d881ffff memory:d8824000-d8824fff ioport:70e0(size=32)         *-usb:0              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #4              vendor: Intel Corporation              physical id: 1a              bus info: pci@0000:00:1a.0              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:16 ioport:70c0(size=32)         *-usb:1              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #5              vendor: Intel Corporation              physical id: 1a.1              bus info: pci@0000:00:1a.1              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:17 ioport:70a0(size=32)         *-usb:2              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #6              vendor: Intel Corporation              physical id: 1a.2              bus info: pci@0000:00:1a.2              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:18 ioport:7080(size=32)         *-usb:3              description: USB controller              product: 82801I (ICH9 Family) USB2 EHCI Controller #2              vendor: Intel Corporation              physical id: 1a.7              bus info: pci@0000:00:1a.7              version: 03              width: 32 bits              clock: 33MHz              capabilities: pm debug ehci bus_master cap_list              configuration: driver=ehci-pci latency=0              resources: irq:19 memory:d8825c00-d8825fff         *-multimedia              description: Audio device              product: 82801I (ICH9 Family) HD Audio Controller              vendor: Intel Corporation              physical id: 1b              bus info: pci@0000:00:1b.0              version: 03              width: 64 bits              clock: 33MHz              capabilities: pm msi pciexpress bus_master cap_list              configuration: driver=snd_hda_intel latency=0              resources: irq:48 memory:d8820000-d8823fff         *-pci:0              description: PCI bridge              product: 82801I (ICH9 Family) PCI Express Port 1              vendor: Intel Corporation              physical id: 1c              bus info: pci@0000:00:1c.0              version: 03              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:40 ioport:8000(size=4096) memory:d8700000-d87fffff ioport:d8900000(size=2097152)         *-pci:1              description: PCI bridge              product: 82801I (ICH9 Family) PCI Express Port 2              vendor: Intel Corporation              physical id: 1c.1              bus info: pci@0000:00:1c.1              version: 03              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:41 ioport:9000(size=4096) memory:d8600000-d86fffff ioport:d8b00000(size=2097152)            *-network                 description: Wireless interface                 product: Ultimate N WiFi Link 5300                 vendor: Intel Corporation                 physical id: 0                 bus info: pci@0000:02:00.0                 logical name: wlan0                 version: 00                 serial: 00:21:6a:2e:ff:ee                 width: 64 bits                 clock: 33MHz                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                 configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=8.83.5.1 build 33692 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn                 resources: irq:46 memory:d8600000-d8601fff         *-pci:2              description: PCI bridge              product: 82801I (ICH9 Family) PCI Express Port 3              vendor: Intel Corporation              physical id: 1c.2              bus info: pci@0000:00:1c.2              version: 03              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:42 ioport:5000(size=8192) memory:d4600000-d85fffff ioport:d8d00000(size=2097152)         *-pci:3              description: PCI bridge              product: 82801I (ICH9 Family) PCI Express Port 5              vendor: Intel Corporation              physical id: 1c.4              bus info: pci@0000:00:1c.4              version: 03              width: 32 bits              clock: 33MHz              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list              configuration: driver=pcieport              resources: irq:43 ioport:3000(size=8192) memory:d0600000-d45fffff ioport:d8f00000(size=2097152)         *-usb:4              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #1              vendor: Intel Corporation              physical id: 1d              bus info: pci@0000:00:1d.0              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:20 ioport:7060(size=32)         *-usb:5              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #2              vendor: Intel Corporation              physical id: 1d.1              bus info: pci@0000:00:1d.1              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:22 ioport:7040(size=32)         *-usb:6              description: USB controller              product: 82801I (ICH9 Family) USB UHCI Controller #3              vendor: Intel Corporation              physical id: 1d.2              bus info: pci@0000:00:1d.2              version: 03              width: 32 bits              clock: 33MHz              capabilities: uhci bus_master cap_list              configuration: driver=uhci_hcd latency=0              resources: irq:18 ioport:7020(size=32)         *-usb:7              description: USB controller              product: 82801I (ICH9 Family) USB2 EHCI Controller #1              vendor: Intel Corporation              physical id: 1d.7              bus info: pci@0000:00:1d.7              version: 03              width: 32 bits              clock: 33MHz              capabilities: pm debug ehci bus_master cap_list              configuration: driver=ehci-pci latency=0              resources: irq:20 memory:d8825800-d8825bff         *-pci:4              description: PCI bridge              product: 82801 Mobile PCI Bridge              vendor: Intel Corporation              physical id: 1e              bus info: pci@0000:00:1e.0              version: 93              width: 32 bits              clock: 33MHz              capabilities: pci subtractive_decode bus_master cap_list              resources: ioport:2000(size=4096) memory:d0500000-d05fffff ioport:dc000000(size=67108864)            *-firewire                 description: FireWire (IEEE 1394)                 product: R5C832 IEEE 1394 Controller                 vendor: Ricoh Co Ltd                 physical id: 9                 bus info: pci@0000:85:09.0                 version: 06                 width: 32 bits                 clock: 33MHz                 capabilities: pm ohci bus_master cap_list                 configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2                 resources: irq:20 memory:d0501000-d05017ff            *-generic                 description: SD Host controller                 product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter                 vendor: Ricoh Co Ltd                 physical id: 9.1                 bus info: pci@0000:85:09.1                 version: 25                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list                 configuration: driver=sdhci-pci latency=64                 resources: irq:22 memory:d0501900-d05019ff            *-pcmcia                 description: CardBus bridge                 product: RL5c476 II                 vendor: Ricoh Co Ltd                 physical id: 9.2                 bus info: pci@0000:85:09.2                 version: bb                 width: 64 bits                 clock: 33MHz                 capabilities: pcmcia bus_master cap_list                 configuration: driver=yenta_cardbus latency=176 maxlatency=5                 resources: iomemory:b08986850-b0898684f irq:22 memory:d0500000-d0500fff ioport:2000(size=256) ioport:2400(size=256) memory:dc000000-dfffffff memory:f0000000-f3ffffff         *-isa              description: ISA bridge              product: ICH9M-E LPC Interface Controller              vendor: Intel Corporation              physical id: 1f              bus info: pci@0000:00:1f.0              version: 03              width: 32 bits              clock: 33MHz              capabilities: isa bus_master cap_list              configuration: driver=lpc_ich latency=0              resources: irq:0         *-storage              description: SATA controller              product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]              vendor: Intel Corporation              physical id: 1f.2              bus info: pci@0000:00:1f.2              version: 03              width: 32 bits              clock: 66MHz              capabilities: storage msi pm ahci_1.0 bus_master cap_list              configuration: driver=ahci latency=0              resources: irq:45 ioport:7108(size=8) ioport:711c(size=4) ioport:7100(size=8) ioport:7118(size=4) ioport:7000(size=32) memory:d8825000-d88257ff      *-scsi:0           physical id: 1           logical name: scsi0           capabilities: emulated         *-disk              description: ATA Disk              product: WDC WD1600BEKT-6              vendor: Western Digital              physical id: 0.0.0              bus info: scsi@0:0.0.0              logical name: /dev/sda              version: 11.0              serial: WD-WXMY08L63507              size: 149GiB (160GB)              capabilities: partitioned partitioned:dos              configuration: ansiversion=5 sectorsize=512 signature=80d2f3ee            *-volume:0                 description: Windows NTFS volume                 physical id: 1                 bus info: scsi@0:0.0.0,1                 logical name: /dev/sda1                 version: 3.1                 serial: aa05fbbd-3f45-fc4e-90c4-0cc465808318                 size: 121GiB                 capacity: 121GiB                 capabilities: primary bootable ntfs initialized                 configuration: clustersize=4096 created=2010-07-24 12:17:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true            *-volume:1                 description: Extended partition                 physical id: 2                 bus info: scsi@0:0.0.0,2                 logical name: /dev/sda2                 size: 27GiB                 capacity: 27GiB                 capabilities: primary extended partitioned partitioned:extended               *-logicalvolume:0                    description: Linux swap / Solaris partition                    physical id: 5                    logical name: /dev/sda5                    capacity: 3995MiB                    capabilities: nofs               *-logicalvolume:1                    description: Linux swap / Solaris partition                    physical id: 6                    logical name: /dev/sda6                    capacity: 3988MiB                    capabilities: nofs               *-logicalvolume:2                    description: Linux filesystem partition                    physical id: 7                    logical name: /dev/sda7                    logical name: /                    capacity: 20GiB                    configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted      *-scsi:1           physical id: 3           logical name: scsi1           capabilities: emulated         *-cdrom              description: DVD-RAM writer              product: DVD RW AD-7561S              vendor: Optiarc              physical id: 0.0.0              bus info: scsi@1:0.0.0              logical name: /dev/cdrom              logical name: /dev/cdrw              logical name: /dev/dvd              logical name: /dev/dvdrw              logical name: /dev/sr0              version: AH03              capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram              configuration: ansiversion=5 status=nodisc   *-battery        product: TD06055        vendor: SDI - SDI        physical id: 1        version: 3A73        serial: 211B        slot: Primary        capacity: 5100mWh        configuration: voltage=10.8V    I truly apologize. I have no idea how to format the code :(

---

### Post by mörgæs on 2013-09-02
Better to run 
```
sudo lshw -sanitize > lshw.txt
``` 
and post the results in CODE tags.

---

### Post by Crusty Old Fart on 2013-09-02
We definitely need to spend some time helping pbandjam with some posting tips.

You can post command results in code tags like this:
```
[noparse]
[code]
These
are example
command
results

```[/noparse]
[/code]
Fortunately, I'm familiar enough with the output from the lshw command to manually put it right. But it took so long that I really don't want to do something like it again. When you ran the command in your terminal window, its output probably looked a lot like this:
```

     description: Notebook
     product: HP EliteBook 6930p (GW684AV#ABA)
     vendor: Hewlett-Packard
     version: F.0F
     serial: 2CE9162VS0
     width: 64 bits
     capabilities: smbios-2.4 dmi-2.4 vsyscall32
     configuration: boot=normal chassis=notebook family=103C_5336AN sku=GW684AV#ABA uuid=24AAE0D3-B02E-DE11-80BF-58A4B30040AD
   *-core
        description: Motherboard
        product: 30DB
        vendor: Hewlett-Packard
        physical id: 0
        version: KBC Version 87.24
      *-firmware
           description: BIOS
           vendor: Hewlett-Packard
           physical id: a
           version: 68PCU Ver. F.0F
           date: 03/05/2009
           size: 64KiB
           capacity: 1472KiB
           capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
      *-cpu
           description: CPU
           product: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
           vendor: Intel Corp.
           physical id: 0
           bus info: cpu@0
           version: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
           slot: Intel(R) Genuine processor
           size: 2267MHz
           capacity: 2267MHz
           width: 64 bits
           clock: 266MHz
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
         *-cache:0
              description: L2 cache
              physical id: 1
              slot: Internal Cache
              size: 3MiB
              capacity: 3MiB
              capabilities: asynchronous internal write-back unified
         *-cache:1
              description: L1 cache
              physical id: 3
              slot: Internal Cache       
              size: 32KiB
              capacity: 32KiB
              capabilities: asynchronous internal write-back data
      *-cache
           description: L1 cache
           physical id: 2
           slot: Internal Cache
           size: 32KiB
           capacity: 32KiB
           capabilities: asynchronous internal write-back instruction
      *-memory
           description: System Memory
           physical id: 4
           slot: System board or motherboard
           size: 4GiB
         *-bank:0
              description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
              product: HYMP125S64CP8-S6
              vendor: Hynix
              physical id: 0
              serial: 00001044
              slot: Top
              size: 2GiB
              width: 64 bits
              clock: 800MHz (1.2ns)
         *-bank:1
              description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
              product: HYMP125S64CP8-S6
              vendor: Hynix
              physical id: 1
              serial: 04008056
              slot: Bottom
              size: 2GiB
              width: 64 bits
              clock: 800MHz (1.2ns)
      *-pci
           description: Host bridge
           product: Mobile 4 Series Chipset Memory Controller Hub
           vendor: Intel Corporation
           physical id: 100
           bus info: pci@0000:00:00.0
           version: 07
           width: 32 bits
           clock: 33MHz
           configuration: driver=agpgart-intel
           resources: irq:0
         *-display:0
              description: VGA compatible controller
              product: Mobile 4 Series Chipset Integrated Graphics Controller
              vendor: Intel Corporation
              physical id: 2
              bus info: pci@0000:00:02.0
              version: 07
              width: 64 bits
              clock: 33MHz
              capabilities: msi pm vga_controller bus_master cap_list rom
              configuration: driver=i915 latency=0
              resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7110(size=8)
         *-display:1 UNCLAIMED
              description: Display controller
              product: Mobile 4 Series Chipset Integrated Graphics Controller
              vendor: Intel Corporation
              physical id: 2.1
              bus info: pci@0000:00:02.1
              version: 07
              width: 64 bits
              clock: 33MHz
              capabilities: pm bus_master cap_list
              configuration: latency=0
              resources: memory:d0400000-d04fffff
         *-network
              description: Ethernet interface
              product: 82567LM Gigabit Network Connection
              vendor: Intel Corporation
              physical id: 19
              bus info: pci@0000:00:19.0
              logical name: eth0
              version: 03
              serial: 00:24:81:f7:ce:77
              width: 32 bits
              clock: 33MHz
              capabilities: pm msi cap_list ethernet physical
              configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
              resources: irq:22 memory:d8800000-d881ffff memory:d8824000-d8824fff ioport:70e0(size=32)
         *-usb:0
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #4
              vendor: Intel Corporation
              physical id: 1a
              bus info: pci@0000:00:1a.0
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:16 ioport:70c0(size=32)
         *-usb:1
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #5
              vendor: Intel Corporation
              physical id: 1a.1
              bus info: pci@0000:00:1a.1
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:17 ioport:70a0(size=32)
         *-usb:2
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #6
              vendor: Intel Corporation
              physical id: 1a.2
              bus info: pci@0000:00:1a.2
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:18 ioport:7080(size=32)
         *-usb:3
              description: USB controller
              product: 82801I (ICH9 Family) USB2 EHCI Controller #2
              vendor: Intel Corporation
              physical id: 1a.7
              bus info: pci@0000:00:1a.7
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pm debug ehci bus_master cap_list
              configuration: driver=ehci-pci latency=0
              resources: irq:19 memory:d8825c00-d8825fff
         *-multimedia
              description: Audio device
              product: 82801I (ICH9 Family) HD Audio Controller
              vendor: Intel Corporation
              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 03
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi pciexpress bus_master cap_list
              configuration: driver=snd_hda_intel latency=0
              resources: irq:48 memory:d8820000-d8823fff
         *-pci:0
              description: PCI bridge
              product: 82801I (ICH9 Family) PCI Express Port 1
              vendor: Intel Corporation
              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:40 ioport:8000(size=4096) memory:d8700000-d87fffff ioport:d8900000(size=2097152)
         *-pci:1
              description: PCI bridge
              product: 82801I (ICH9 Family) PCI Express Port 2
              vendor: Intel Corporation
              physical id: 1c.1
              bus info: pci@0000:00:1c.1
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:41 ioport:9000(size=4096) memory:d8600000-d86fffff ioport:d8b00000(size=2097152)
            *-network
                 description: Wireless interface
                 product: Ultimate N WiFi Link 5300
                 vendor: Intel Corporation
                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlan0
                 version: 00
                 serial: 00:21:6a:2e:ff:ee
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=8.83.5.1 build 33692 ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE802.11abgn
                 resources: irq:46 memory:d8600000-d8601fff
         *-pci:2
              description: PCI bridge
              product: 82801I (ICH9 Family) PCI Express Port 3
              vendor: Intel Corporation
              physical id: 1c.2
              bus info: pci@0000:00:1c.2
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:42 ioport:5000(size=8192) memory:d4600000-d85fffff ioport:d8d00000(size=2097152)
         *-pci:3
              description: PCI bridge
              product: 82801I (ICH9 Family) PCI Express Port 5
              vendor: Intel Corporation
              physical id: 1c.4
              bus info: pci@0000:00:1c.4
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:43 ioport:3000(size=8192) memory:d0600000-d45fffff ioport:d8f00000(size=2097152)
         *-usb:4
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #1
              vendor: Intel Corporation
              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:20 ioport:7060(size=32)
         *-usb:5
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #2
              vendor: Intel Corporation
              physical id: 1d.1
              bus info: pci@0000:00:1d.1
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:22 ioport:7040(size=32)
         *-usb:6
              description: USB controller
              product: 82801I (ICH9 Family) USB UHCI Controller #3
              vendor: Intel Corporation
              physical id: 1d.2
              bus info: pci@0000:00:1d.2
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master cap_list
              configuration: driver=uhci_hcd latency=0
              resources: irq:18 ioport:7020(size=32)
         *-usb:7
              description: USB controller
              product: 82801I (ICH9 Family) USB2 EHCI Controller #1
              vendor: Intel Corporation
              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: pm debug ehci bus_master cap_list
              configuration: driver=ehci-pci latency=0
              resources: irq:20 memory:d8825800-d8825bff
         *-pci:4
              description: PCI bridge
              product: 82801 Mobile PCI Bridge
              vendor: Intel Corporation
              physical id: 1e
              bus info: pci@0000:00:1e.0
              version: 93
              width: 32 bits
              clock: 33MHz
              capabilities: pci subtractive_decode bus_master cap_list
              resources: ioport:2000(size=4096) memory:d0500000-d05fffff ioport:dc000000(size=67108864)
            *-firewire
                 description: FireWire (IEEE 1394)
                 product: R5C832 IEEE 1394 Controller
                 vendor: Ricoh Co Ltd
                 physical id: 9
                 bus info: pci@0000:85:09.0
                 version: 06
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm ohci bus_master cap_list
                 configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                 resources: irq:20 memory:d0501000-d05017ff
            *-generic
                 description: SD Host controller
                 product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                 vendor: Ricoh Co Ltd
                 physical id: 9.1
                 bus info: pci@0000:85:09.1
                 version: 25
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm bus_master cap_list
                 configuration: driver=sdhci-pci latency=64
                 resources: irq:22 memory:d0501900-d05019ff
            *-pcmcia
                 description: CardBus bridge
                 product: RL5c476 II
                 vendor: Ricoh Co Ltd
                 physical id: 9.2
                 bus info: pci@0000:85:09.2
                 version: bb
                 width: 64 bits
                 clock: 33MHz
                 capabilities: pcmcia bus_master cap_list
                 configuration: driver=yenta_cardbus latency=176 maxlatency=5
                 resources: iomemory:b08986850-b0898684f irq:22 memory:d0500000-d0500fff ioport:2000(size=256) ioport:2400(size=256) memory:dc000000-dfffffff memory:f0000000-f3ffffff
         *-isa
              description: ISA bridge
              product: ICH9M-E LPC Interface Controller
              vendor: Intel Corporation
              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 03
              width: 32 bits
              clock: 33MHz
              capabilities: isa bus_master cap_list
              configuration: driver=lpc_ich latency=0
              resources: irq:0
         *-storage
              description: SATA controller
              product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
              vendor: Intel Corporation
              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              version: 03
              width: 32 bits
              clock: 66MHz
              capabilities: storage msi pm ahci_1.0 bus_master cap_list
              configuration: driver=ahci latency=0
              resources: irq:45 ioport:7108(size=8) ioport:711c(size=4) ioport:7100(size=8) ioport:7118(size=4) ioport:7000(size=32) memory:d8825000-d88257ff
      *-scsi:0
           physical id: 1
           logical name: scsi0
           capabilities: emulated
         *-disk
              description: ATA Disk
              product: WDC WD1600BEKT-6
              vendor: Western Digital
              physical id: 0.0.0
              bus info: scsi@0:0.0.0
              logical name: /dev/sda
              version: 11.0
              serial: WD-WXMY08L63507
              size: 149GiB (160GB)
              capabilities: partitioned partitioned:dos
              configuration: ansiversion=5 sectorsize=512 signature=80d2f3ee
            *-volume:0
                 description: Windows NTFS volume
                 physical id: 1
                 bus info: scsi@0:0.0.0,1
                 logical name: /dev/sda1
                 version: 3.1
                 serial: aa05fbbd-3f45-fc4e-90c4-0cc465808318
                 size: 121GiB
                 capacity: 121GiB
                 capabilities: primary bootable ntfs initialized
                 configuration: clustersize=4096 created=2010-07-24 12:17:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
            *-volume:1
                 description: Extended partition
                 physical id: 2
                 bus info: scsi@0:0.0.0,2
                 logical name: /dev/sda2
                 size: 27GiB
                 capacity: 27GiB
                 capabilities: primary extended partitioned partitioned:extended
               *-logicalvolume :0
                    description: Linux swap / Solaris partition
                    physical id: 5
                    logical name: /dev/sda5
                    capacity: 3995MiB
                    capabilities: nofs
               *-logicalvolume:1
                    description: Linux swap / Solaris partition
                    physical id: 6
                    logical name: /dev/sda6
                    capacity: 3988MiB
                    capabilities: nofs
               *-logicalvolume:2
                    description: Linux filesystem partition
                    physical id: 7
                    logical name: /dev/sda7
                    logical name: /
                    capacity: 20GiB
                    configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
      *-scsi:1
           physical id: 3
           logical name: scsi1
           capabilities: emulated
         *-cdrom
              description: DVD-RAM writer          
              product: DVD RW AD-7561S
              vendor: Optiarc
              physical id: 0.0.0
              bus info: scsi@1:0.0.0
              logical name: /dev/cdrom
              logical name: /dev/cdrw
              logical name: /dev/dvd
              logical name: /dev/dvdrw
              logical name: /dev/sr0
              version: AH03
              capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
              configuration: ansiversion=5 status=nodisc
   *-battery
        product: TD06055
        vendor: SDI - SDI
        physical id: 1
        version: 3A73
        serial: 211B
        slot: Primary
        capacity: 5100mWh
        configuration: voltage=10.8V

```
The part of the results that I was most interested in follows:
```

         *-multimedia
              description: Audio device
              product: 82801I (ICH9 Family) HD Audio Controller
              vendor: Intel Corporation
              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 03
              width: 64 bits
              clock: 33MHz
              capabilities: pm msi pciexpress bus_master cap_list
              configuration: **[COLOR=#0000FF]driver=snd_hda_intel[/COLOR]** latency=0
              resources: irq:48 memory:d8820000-d8823fff

```
As you can see by the **[COLOR=blue]bold blue text[/COLOR]** above, your system loaded a driver for your sound controller. That's good.

Next, I'd like you to post the output from the following command:
```

aplay -l

```
You may find the page at this link helpful --> [https://help.ubuntu.com/13.04/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/13.04/ubuntu-help/sound-nosound.html)

Crusty

---

### Post by pbandjam on 2013-09-03
> **mörgæs said:**
> Better to run 
```
sudo lshw -sanitize > lshw.txt
``` 
and post the results in CODE tags.

When I run that code all it says is 'PCI (sysfs)', blinks for a few seconds and goes away.

---

### Post by pbandjam on 2013-09-03
This is what I get when entering: ```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Crusty Old Fart on 2013-09-03
> **pbandjam said:**
> When I run that code all it says is 'PCI (sysfs)', blinks for a few seconds and goes away.
That's right. The rest of the command output was redirected into a file named: lshw.txt.
You're likely to find that file in your home directory, and if you open it, you should see the output from the lshw command.

---

### Post by Crusty Old Fart on 2013-09-03
> **pbandjam said:**
> This is what I get when entering: ```
aplay -l
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
That looks good.
Your system has detected your playback device. That's good.

Now you should make sure it is selected as the output device:

[LIST]
[*]Click the sound menu in the menu bar and click Sound Settings.


[*]In the Sound window that appears, try selecting it as the output from the Play sound through list.


[*]For the selected device, click Test Sound.  In the pop-up window, click the   button for each speaker. Each button will speak its position only to the channel   corresponding to that speaker.


[*]If that doesn't work, you might want to try doing the same for any other  devices that are listed.

[/LIST]

---

### Post by pbandjam on 2013-09-03
Ok thanks. This is what it turns up:

```

computer
    description: Notebook
    product: HP EliteBook 6930p (GW684AV#ABA)
    vendor: Hewlett-Packard
    version: F.0F
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=GW684AV#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 30DB
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 87.24
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: a
          version: 68PCU Ver. F.0F
          date: 03/05/2009
          size: 64KiB
          capacity: 1472KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
          slot: Intel(R) Genuine processor
          size: 2267MHz
          capacity: 2267MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Internal Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 2
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125S64CP8-S6
             vendor: Hynix
             physical id: 0
             serial: [REMOVED]
             slot: Top
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125S64CP8-S6
             vendor: Hynix
             physical id: 1
             serial: [REMOVED]
             slot: Bottom
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0400000-d04fffff
        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:44 memory:d8800000-d881ffff memory:d8824000-d8824fff ioport:70e0(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:70c0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:70a0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7080(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:d8825c00-d8825fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:d8820000-d8823fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:8000(size=4096) memory:d8700000-d87fffff ioport:d8900000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:9000(size=4096) memory:d8600000-d86fffff ioport:d8b00000(size=2097152)
           *-network
                description: Wireless interface
                product: Ultimate N WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=8.83.5.1 build 33692 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:d8600000-d8601fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=8192) memory:d4600000-d85fffff ioport:d8d00000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=8192) memory:d0600000-d45fffff ioport:d8f00000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:7060(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:7040(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7020(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:d8825800-d8825bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0500000-d05fffff ioport:dc000000(size=67108864)
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:85:09.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:d0501000-d05017ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:85:09.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d0501900-d05019ff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:85:09.2
                version: bb
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b08986850-b0898684f irq:22 memory:d0500000-d0500fff ioport:2000(size=256) ioport:2400(size=256) memory:dc000000-dfffffff memory:f0000000-f3ffffff
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:7108(size=8) ioport:711c(size=4) ioport:7100(size=8) ioport:7118(size=4) ioport:7000(size=32) memory:d8825000-d88257ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEKT-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 11.0
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=80d2f3ee
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 121GiB
                capacity: 121GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-07-24 12:17:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 27GiB
                capacity: 27GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3995MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 3988MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 20GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7561S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AH03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: TD06055
       vendor: SDI - SDI
       physical id: 1
       version: 3A73
       serial: [REMOVED]
       slot: Primary
       capacity: 5100mWh
       configuration: voltage=10.8V

```

---

### Post by pbandjam on 2013-09-03
> **Crusty Old Fart said:**
> That looks good.
Your system has detected your playback device. That's good.

Now you should make sure it is selected as the output device:

[LIST]
[*]Click the sound menu in the menu bar and click Sound Settings. 
[*]In the Sound window that appears, try selecting it as the output from the Play sound through list. 
[*]For the selected device, click Test Sound.  In the pop-up window, click the   button for each speaker. Each button will speak its position only to the channel   corresponding to that speaker. 
[*]If that doesn't work, you might want to try doing the same for any other  devices that are listed. 
[/LIST]


Its the only device that shows up on the output devices. But still no sound.

---

### Post by Crusty Old Fart on 2013-09-03
> **pbandjam said:**
> Ok thanks. This is what it turns up:

```

computer
    description: Notebook
    product: HP EliteBook 6930p (GW684AV#ABA)
    vendor: Hewlett-Packard
    version: F.0F
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=GW684AV#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 30DB
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 87.24
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: a
          version: 68PCU Ver. F.0F
          date: 03/05/2009
          size: 64KiB
          capacity: 1472KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
          slot: Intel(R) Genuine processor
          size: 2267MHz
          capacity: 2267MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L2 cache
             physical id: 1
             slot: Internal Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 3
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 2
          slot: Internal Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 4
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125S64CP8-S6
             vendor: Hynix
             physical id: 0
             serial: [REMOVED]
             slot: Top
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: HYMP125S64CP8-S6
             vendor: Hynix
             physical id: 1
             serial: [REMOVED]
             slot: Bottom
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:7110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0400000-d04fffff
        *-network
             description: Ethernet interface
             product: 82567LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.1.4-k firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:44 memory:d8800000-d881ffff memory:d8824000-d8824fff ioport:70e0(size=32)
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:70c0(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:70a0(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7080(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:d8825c00-d8825fff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:d8820000-d8823fff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:8000(size=4096) memory:d8700000-d87fffff ioport:d8900000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:9000(size=4096) memory:d8600000-d86fffff ioport:d8b00000(size=2097152)
           *-network
                description: Wireless interface
                product: Ultimate N WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-29-generic firmware=8.83.5.1 build 33692 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:d8600000-d8601fff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:5000(size=8192) memory:d4600000-d85fffff ioport:d8d00000(size=2097152)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:3000(size=8192) memory:d0600000-d45fffff ioport:d8f00000(size=2097152)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:7060(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:7040(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:7020(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:d8825800-d8825bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0500000-d05fffff ioport:dc000000(size=67108864)
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:85:09.0
                version: 06
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:20 memory:d0501000-d05017ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:85:09.1
                version: 25
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:d0501900-d05019ff
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:85:09.2
                version: bb
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b08986850-b0898684f irq:22 memory:d0500000-d0500fff ioport:2000(size=256) ioport:2400(size=256) memory:dc000000-dfffffff memory:f0000000-f3ffffff
        *-isa
             description: ISA bridge
             product: ICH9M-E LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:7108(size=8) ioport:711c(size=4) ioport:7100(size=8) ioport:7118(size=4) ioport:7000(size=32) memory:d8825000-d88257ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEKT-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 11.0
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=80d2f3ee
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 121GiB
                capacity: 121GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-07-24 12:17:06 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 27GiB
                capacity: 27GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3995MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 3988MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 20GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD RW AD-7561S
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AH03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: TD06055
       vendor: SDI - SDI
       physical id: 1
       version: 3A73
       serial: [REMOVED]
       slot: Primary
       capacity: 5100mWh
       configuration: voltage=10.8V

```
Perfect. Nice job. You're learning fast.

---

### Post by Crusty Old Fart on 2013-09-03
> **pbandjam said:**
> Its the only device that shows up on the output devices. But still no sound.
I was afraid of that. We've done everything suggested on the official documentation page for sound problems with your OS.

Let's take a look at your kernel messages. There will be a lot of them. So, I'll give you a command that will put them in a file, like the output from your last lshw command did:
```

dmesg > dmesg1.txt

```
By the way, in case you didn't know this, you can copy text from code boxes with your mouse and past them into your shell. It's usually the best way to enter a command that someone gives you, in that it cuts down on typing errors.

So, please post the contents of the file named dmesg1.txt. Then you can delete it. You can also delete the one named: lshw.txt.

---

### Post by mörgæs on 2013-09-04
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by Crusty Old Fart on 2013-09-04
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)
Oh wow.
This could get complicated.
What a mess.
My computer has security measures installed that prevent it from accessing anything on Google.
But, I made a quick reading of the page at: [Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
Sixteen steps of troubleshooting, many of which are somewhat advanced for a brand new user of Linux.
I'm beginning to get concerned about making suggestions to someone to run commands that may alter their system, especially since I'm still running Lucid and have no experience with Raring. The more I think about it, the more concerned I get. My inexperience with Raring may make it impossible for me to instruct a user how to "undo" something that doesn't go well.

I think pbandjam would be much better served by someone with more experience with Raring than I have. So, for his sake, I think I should step aside and leave him in more capable hands.

Thanks for exposing me to how involved this problem can be, mörgæs. You may have saved pbandjam a whole lot of frustration, and me from messing up his system.

Good Luck,

Crusty

---

### Post by mörgæs on 2013-09-04
May I guess... does the application which claims that Google is a security breach come from Microsoft?

I am not specialist on sound, but I know that the thread to which I linked has helped a lot of people.

---

### Post by Crusty Old Fart on 2013-09-04
> **mörgæs said:**
> May I guess... does the application which claims that Google is a security breach come from Microsoft?...
It's not an application. It doesn't come from Microsoft. The security measures are my own custom modifications, that I won't elaborate on, for security reasons.

---


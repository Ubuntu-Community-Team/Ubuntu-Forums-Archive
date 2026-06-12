---
title: "Dell Latitude e5400: Fan running on full"
date: 2014-11-26
forum: New to Ubuntu
---

### Post by jack114 on 2014-11-26
Hey lads, what's up. 
Have a Dell latitude e5400 running 14.04. Have only been using it again for the last week because I got sick of all the trouble with it during the summer. It was over heating and shutting down and wifi was dropping randomly. Since I've started using it again it's alot better don't know how though. However the fan is still running on full, all the time. It still randomly over heats but its a lot less frequent as before, a non issure now really. Think it started acting up around the 13.10 update, can't really remember. 

Where do I start?
 Any and all help will be seriously appreciated.

---

### Post by zircon_34 on 2014-11-26
I had once such a problem, opened the computer, and cleaned a big amount of dust that was stuck in the fan. Perhaps that might be the issue....

---

### Post by Impavidus on 2014-11-27
Sometimes this is related to a component not switching to energy saving mode. Have you checked for proprietary drivers? And have you checked your CPU load? Computers shouldn't overheat, even when number crunching, but under the wrong circumstances it might happen.

---

### Post by jack114 on 2014-11-27
Went to additional drivers and after searching said there was none available and that I have no proprietary drivers in use. Ya gave the inside a little dusting, everything looks good. Installed htop, nothing really looks out of the ordinary...

Has been switching off at random times all morning and the WiFi is becoming more and more erratic. I just have to reboot and hope it's on when I log back in. 
Temperature is staying around 40-60 but going up to the 90s

---

### Post by Mark Phelps on 2014-11-27
You could try using "tlp" and seeing if that helps:  [http://linuxg.net/tlp-the-new-jupiter-install-tlp-on-ubuntu-13-04/]("http://linuxg.net/tlp-the-new-jupiter-install-tlp-on-ubuntu-13-04/")

---

### Post by jack114 on 2014-11-27
Haven't noticed anything so far after installing tlp. Have been looking around and the wifi dropping seems to be a common enough problem with the e5400 and also a lot of people seem to have experienced an issue with fan control.

[http://www.zdnet.com/blog/hardware/dell-releases-bios-updates-to-fix-underperformingoverthrottling-notebooks/6347](http://www.zdnet.com/blog/hardware/dell-releases-bios-updates-to-fix-underperformingoverthrottling-notebooks/6347)
Have no clue where to start in relation to drivers, anyone point me in the right direction?

Is going back to an older version like 10.04 an option?

---

### Post by Impavidus on 2014-11-28
90 degrees is indeed too hot. Have you checked the heat sinks? They may not be properly attached. Maybe you have to apply new thermal paste. I've never needed it, but I read it's sometimes necessary.

10.04 is no longer supported, so don't use that, but 12.04 has over two years of support left.

---

### Post by jack114 on 2014-11-28
What exactly am I supposed to be looking in regards to the heat sinks? Everything seems ok.

Pretty sure it's nothing physical that's the problem. Had to reboot ten mins ago and now my mouse and keyboard are acting up. When I have control pressed while browsing in firefox it zooms in as if I was scrolling up with the mouse wheel, also when hovering over tabs it will scroll to the first tab and will not allow me to move back up to the more recently opened tabs. This is slowly becoming unusable.

Wifi is dropping more and more also. Everythings getting worse..

---

### Post by mörgæs on 2014-11-28
Which BIOS are you using?

---

### Post by jack114 on 2014-11-28
used
sudo dmidecode -s bios-version
and got A19

---

### Post by jack114 on 2014-12-01
[COLOR=#000000] Can I update my BIOS with out going into the boot menu or BIOS options? Laptop screen is broken and the monitor I'm using only starts up when prompted to log in. [/COLOR]

---

### Post by mörgæs on 2014-12-01
Your BIOS is fairly recent so I don't think there's a need for upgrading.

If overheating is a problem have you tried something lighter like for example Lubuntu 14.10?

---

### Post by jack114 on 2014-12-01
Sorry actually using lubuntu,  everything was running perfect for about 6 months so don't think it's the machine that's not up to the task. Sometimes when I turn it on it runs dead silent, like not a whisper from it. The other 98% of the time it sounds like a lawnmower. I would get over the noise from it but randomly shutting down and not being able to maintain a wifi connection makes it almost unusable. Really have no clue where to go??

---

### Post by mörgæs on 2014-12-01
Let's see the hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by jack114 on 2014-12-01
```

computer
    description: Portable Computer
    product: Latitude E5400 ()
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0D695C
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A19
          date: 06/13/2013
          size: 64KiB
          capacity: 1536KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.10
          serial: [REMOVED]
          slot: Microprocessor
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 266MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 3MiB
             capacity: 3MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: NT1GT64UH8D0FN-AD
             vendor: Nanya Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: NT1GT64UH8D0FN-AD
             vendor: Nanya Technology
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_B
             size: 1GiB
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
             resources: irq:44 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:efe8(size=8)
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
             resources: memory:f6b00000-f6bfffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f60(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f80(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6fa0(size=32)
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f6afc000-f6afffff
        *-pci:0
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:84000000-841fffff ioport:84200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f6900000-f69fffff ioport:84400000(size=2097152)
           *-network
                description: Wireless interface
                product: WiFi Link 5100
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-40-generic firmware=8.83.5.1 build 33692 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:45 memory:f69fe000-f69fffff
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f6800000-f68fffff ioport:84600000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5761e Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5761e-v3.60 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:47 memory:f68e0000-f68effff memory:f68f0000-f68fffff
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f00(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f20(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:f6700000-f67fffff ioport:80000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:02:01.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603020-b0060301f irq:19 memory:88000000-88000fff ioport:5000(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:8c000000-8fffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:17 memory:f67ff800-f67fffff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f67ff600-f67ff6ff
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
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
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=32) memory:fed1c800-fed1cfff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6afbf00-f6afbfff ioport:1100(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Crucial_CT120M50
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MU03
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=00030465
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 109GiB
                capacity: 109GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-07-17 17:47:54 filesystem=ext4 lastmountpoint=/ modified=2014-12-02 00:26:11 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-02 00:26:11 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2001MiB
                capacity: 2001MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2001MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW GT10N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: A106
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       product: DELL PW64096
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 52000mWh
       configuration: voltage=11.1V


```

---

### Post by mörgæs on 2014-12-02
It all looks fine, only thing that caught my attention is the Intel Mobile 4 Series graphics chip which sometimes gives problems for 14.04. 

Again I recommend that you try 14.10. Could be in a live boot or (better) installed in a dual boot, if you have some space left on the hard disk, but don't upgrade your existing system.

---

### Post by jack114 on 2014-12-04
Installed 14.10 fresh and everythings working pretty well. temps are staying around 35-50 and the fan is only running on full every so often. Thanks for your help!

---

### Post by mörgæs on 2014-12-04
You're welcome. Please spread the word - too many people here are struggling with 14.04 - and mark the thread 'solved'.

---


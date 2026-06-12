---
title: "Adobe flash for Chromium in Lubuntu?"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by Nick_Brennan on 2014-12-14
I've decided to run Lubuntu on my old HP laptop due to Ubuntu being a bit sluggish. I've installed Chromium via synaptic. What I wanted to know is how to get get adobe flash working in Chromium? Just confused on how to do it.

Thanks! :)

---

### Post by oldrocker99 on 2014-12-14
Try this:
```
sudo apt-get install flashplugin-installer
```
This will pull in the latest version and install it.

---

### Post by Frogs Hair on 2014-12-14
For Chromium, you might want to install pepperflashplugin-nonfree and restart the browser.

---

### Post by Nick_Brennan on 2014-12-14
> **Frogs Hair said:**
> For Chromium, you might want to install pepperflashplugin-nonfree and restart the browser.


How would I do this?

---

### Post by nerdtron on 2014-12-14
> **Nick_Brennan said:**
> How would I do this?

You can search the software center for the pepperflash plugin or from the terminal.
```
sudo apt-get install pepperflashplugin-nonfree 
```

---

### Post by Nick_Brennan on 2014-12-14
Thanks that worked. Should I uninstall the other flash version? I tired installing the regular Chrome version with regular flash and Chrome couldn't install. That's what prompted me to install Chromium from SPM. What would be the best way to remove both of those just so my install is clean?

Also I keep getting "Aw Snap" Chromium crashed when viewing youtube videos. What would be the best way to troubleshoot that?

I'm new to linux but this is interesting as heck!

Thanks.

---

### Post by nerdtron on 2014-12-14
HHmm not sure about that. Besides if I'm not mistaken, the pepperflash plugin for chromium basically "extracts" the flash player of the Google Chrome version. I guess you can just uninstall google chrome. And I think the flash plugin installer is part of the Ubuntu restricted extras package, which you should also install.

---

### Post by Nick_Brennan on 2014-12-14
Ok. Is there any difference in the install between Ubuntu and Lubuntu? When I look up software, Ubuntu pops up all the time. Lubuntu is basically the same as Ubuntu correct?

---

### Post by nerdtron on 2014-12-14
For chrome? It's the same for Ubuntu and Lubuntu.
For the restricted extras (mp3 codecs. etc.) the package is "lubuntu-restricted-extras"

---

### Post by Nick_Brennan on 2014-12-14
K understood. Can Chrome itself run in Lubuntu? Or is Chromium recommended?

---

### Post by nerdtron on 2014-12-14
Chrome will run, plus it includes its own flash player and auto updates too, and some google stuffs
Chromium is the open source base for Chrome without the proprietary code/google stuff.

It's upto you to choose what you want. I'm using Chromium, but I'll say, use what works for you. Less problems = more work done.

---

### Post by Nick_Brennan on 2014-12-14
Ok I'll stick with Chromium then. Firefox on here plays youtube videos without crashing so I'm not sure why Chromium is crashing. I'm used to troubleshooting in windows. What are some things I can try out first to narrow down why it could be crashing? Reinstall?

---

### Post by mörgæs on 2014-12-15
'Aw, snap' often indicates that you are low on memory. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Nick_Brennan on 2014-12-15
Here you go,


```
 computer    description: Notebook
    product: HP Compaq 6910p (GV630UC#ABA) (GV630UC#ABA)
    vendor: Hewlett-Packard
    version: F.19
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=GV630UC#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 30BE
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 68.36
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MCU Ver. F.19
          date: 07/06/2010
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: [REMOVED]
          slot: U10
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida dtherm tpr_shadow vnmi flexpriority cpufreq
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
             size: 4MiB
             capacity: 4MiB
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
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 8HTF12864HDY-667E1
             vendor: Micron Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM #1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M4 70T2864QZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: DIMM #2
             size: 1GiB
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
             resources: irq:44 memory:e4300000-e43fffff memory:d0000000-dfffffff ioport:4000(size=8)
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
             resources: memory:e4400000-e44fffff
        *-communication:0
             description: Communication controller
             product: Mobile PM965/GM965 MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:45 memory:e4500000-e450000f
        *-ide:0
             description: IDE interface
             product: Mobile PM965/GM965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=ata_generic latency=0
             resources: irq:18 ioport:4008(size=8) ioport:4010(size=4) ioport:4018(size=8) ioport:4020(size=4) ioport:4030(size=16)
        *-communication:1
             description: Serial controller
             product: Mobile PM965/GM965 KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:4040(size=8) memory:e4501000-e4501fff
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: [REMOVED]
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=0.3-0 ip=[REMOVED] latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:42 memory:e4520000-e453ffff memory:e4540000-e4540fff ioport:4060(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:4080(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:40a0(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:e4541000-e45413ff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:e4544000-e4547fff
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
             resources: irq:40
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=8192) memory:e0000000-e3ffffff ioport:7e000000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:40c0(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:40e0(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:4100(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:e4548000-e45483ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:5000(size=4096) memory:e4000000-e42fffff
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
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00303020-b0030301f irq:18 memory:e4000000-e4000fff ioport:5000(size=256) ioport:5400(size=256) memory:80000000-83ffffff memory:84000000-87ffffff
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
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00704020-b0070401f irq:19 memory:e4001000-e4001fff ioport:5800(size=256) ioport:5c00(size=256) memory:88000000-8bffffff memory:8c000000-8fffffff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:19 memory:e4002000-e40020ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:1
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4120(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:43 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:4160(size=32) memory:e4549000-e45497ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4246N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 0C07
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD3200BPVT-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=88728d5e
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 296GiB
                capacity: 296GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-12-14 01:16:32 filesystem=ext4 lastmountpoint=/ modified=2014-12-14 17:01:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-12-14 17:01:33 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                size: 2006MiB
                capacity: 2006MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2006MiB
                   capabilities: nofs
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 11/11/2009
       serial: [REMOVED]
       slot: Primary
       capacity: 52000mWh
       configuration: voltage=10.8V
nick@HP-Compaq-6910p:~$ 
```

---

### Post by mörgæs on 2014-12-15
Fine hardware. Doesn't seem to be the reason for the error message.

---

### Post by Nick_Brennan on 2014-12-15
What would be the best way to reinstall Chromium and pepper flash? I'd like to rename my Chrome profile also so it installs a fresh profile.

Can you guys help me out how to do that?

Actually, I'd like to just install Chrome with it's built in flash. What would be the best way to fully uninstall Chromium and pepper then just install Chrome?

Thanks!  :)

---

### Post by mörgæs on 2014-12-16
For installing Chrome please see the link in my signature.

---

### Post by Jeroen Mathon on 2014-12-16
Doesn't chromium have flash build in or is that only in the closed source version(Chrome)?

---

### Post by j0sk on 2014-12-17
> **Jeroen Mathon said:**
> Doesn't chromium have flash build in or is that only in the closed source version(Chrome)?

Its only in Chrome. For Chromium: 
apt-get install pepperflashplugin-nonfree

---


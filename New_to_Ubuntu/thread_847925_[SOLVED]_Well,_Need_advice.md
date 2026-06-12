---
title: "[SOLVED] Well, Need advice"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-03
I have been having trouble with all the different linuxs on my computer. I am currently running xubuntu and from what I have heard it is for low end computers. I have had trouble with my drivers (graphics are a deffinent problem). 

All I need to know is what linux would run great on my computer.

---

### Post by iaculallad on 2008-07-03
> **deadlySniper said:**
> I have been having trouble with all the different linuxs on my computer. I am currently running xubuntu and from what I have heard it is for low end computers. I have had trouble with my drivers (graphics are a deffinent problem). 

All I need to know is what linux would run great on my computer.


All you have to do is post the specification of your unit. That way, we could give you suggestions on what Ubuntu variant or Linux distro would run great on that unit of yours.

---

### Post by deadlySniper on 2008-07-03
Memory- 1010.8
Processor- Intel(R) Pentium(R) M processor 1600MHz
Disk space- 47.7 GB

---

### Post by iaculallad on 2008-07-03
> **deadlySniper said:**
> Memory- 1010.8
Processor- Intel(R) Pentium(R) M processor 1600MHz
Disk space- 47.7 GB

On your terminal:

```
lshw
```

---

### Post by powerpleb on 2008-07-03
To list all your hardware and save the info to a text file.
```

sudo aptitude install hwinfo
hwinfo >> hardware.txt
```

Edit: the method in iaculallad's post is probably better but you can still save the output to a text file by using
```
sudo lshw >> hardware.txt
```

---

### Post by deadlySniper on 2008-07-03
```
deadlysniper-laptop       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1010MB
     *-cpu
          product: Intel(R) Pentium(R) M processor 1600MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.9.5
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2 cpufreq
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:0
                description: Ethernet interface
                product: 82540EP Gigabit Ethernet Controller (Mobile)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 03
                serial: 00:0d:60:c5:26:4f
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes
           *-network:1
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wifi0
                version: 01
                serial: 00:05:4e:49:77:3a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0

```

---

### Post by iaculallad on 2008-07-03
> **deadlySniper said:**
> Memory- 1010.8
Processor- Intel(R) Pentium(R) M processor 1600MHz
Disk space- 47.7 GB

You can install Ubuntu v7.10 (Gutsy Gibbon) v8.04 (Hardy Heron) with this hardware specification. Virtually, all 32-bit Ubuntu GNOME variant could be installed on your machine.

---

### Post by deadlySniper on 2008-07-03
**[SIZE="6"]USE THIS ONE, THE ABOVE ONE IS NOT DETAILED[/SIZE]**
```
deadlysniper-laptop       
    description: Notebook
    product: 2374N01
    vendor: IBM
    version: ThinkPad T41
    serial: 99783BK
    width: 32 bits
    capabilities: smbios-2.33 dmi-2.33
    configuration: administrator_password=enabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=F743DA81-46E7-11CB-9520-D843FB2F3120
  *-core
       description: Motherboard
       product: 2374N01
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J1W7K4791DW
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: 1RETDNWW (3.19 ) (10/13/2005)
          size: 144KB
          capacity: 960KB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1600MHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.9.5
          slot: None
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 32KB
             capacity: 32KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: Internal L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 2c
          slot: System board or motherboard
          size: 1GB
          capacity: 1GB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 02
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-2.0 pm vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-pcmcia:1
                description: CardBus bridge
                product: PCI4520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:0
                description: Ethernet interface
                product: 82540EP Gigabit Ethernet Controller (Mobile)
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 03
                serial: 00:0d:60:c5:26:4f
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
           *-network:1
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wifi0
                version: 01
                serial: 00:05:4e:49:77:3a
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: SCSI Disk
                product: HTS726060M9AT00
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MH4O
                serial: MRH403M4GRD7RB
                size: 55GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 53GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2384MB
                   capacity: 2384MB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2384MB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: RW/DVD GCC-4242N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0J04
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0

```

---

### Post by deadlySniper on 2008-07-03
I have tried Gutsy and it caused my comp to freeze after a while. cant use fedora because of my drivers. I heard about xubuntu and used it since my comp is kinda low end

---

### Post by powerpleb on 2008-07-03
Xubuntu would fly on that computer. I have a laptop with almost the same specs and Xubuntu and it's a rocket, even with full compiz-fusion effects.
This page may help getting your graphics drivers properly installed
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Does wireless work? That chipset can be a problem.

---

### Post by iaculallad on 2008-07-03
> **deadlySniper said:**
> I have tried Gutsy and it caused my comp to freeze after a while. cant use fedora because of my drivers. I heard about xubuntu and used it since my comp is kinda low end

With that specification posted above with BOLD+CAPSLOCK words, you can run the latest version of Ubuntu. If you want other distro option, try Gentoo.

You can check it yourself the requirement to run Ubuntu 8.04 LTS:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by starcannon on 2008-07-03
You can run any version of Ubuntu you wish with those specifications.
You could run Mint Linux as well, an Ubuntu derivative.

You'll need to get your graphics card working, on an 8.04 live cd press F4 at the menu screen and choose safe mode for the install type, this will get you going, then you can move on to install drivers.

Nice computer, you should be fine.

GL

---

### Post by deadlySniper on 2008-07-03
I got the wireless on my own to work.

---

### Post by deadlySniper on 2008-07-03
that link really helped out

---

### Post by hyper_ch on 2008-07-03
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---


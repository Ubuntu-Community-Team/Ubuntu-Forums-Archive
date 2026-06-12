---
title: "[SOLVED] problem Playing DVD's"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Hypo_Mix on 2008-05-28
i was trying to play a real (not burnt) dvd,
when i tried to play in Movie Player (totem?) it came up with the error message
> Could not read from resource.

then i tried in VLC
it played the menu for about 15 seconds before stopping and going back to minimized (stopped) screen
same happened after hitting play.

Any thing i am missing here?

PS: i have installed libdvdcss2

---

### Post by Dan++ on 2008-05-28
I would recommend checking out [Medibuntu](https://help.ubuntu.com/community/Medibuntu) and the [Restricted Formats how-to](https://help.ubuntu.com/community/RestrictedFormats), particularly [the part about playing DVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs). Once you've installed all of the packages those three places instruct you to, you should be able to play pretty much any format, including DVDs.

---

### Post by Hypo_Mix on 2008-05-28
> **Dan++ said:**
> I would recommend checking out [Medibuntu](https://help.ubuntu.com/community/Medibuntu) and the [Restricted Formats how-to](https://help.ubuntu.com/community/RestrictedFormats), particularly [the part about playing DVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs). Once you've installed all of the packages those three places instruct you to, you should be able to play pretty much any format, including DVDs.

no dice,
i installed all of them, and it hasn't helped much, it can start playing the movie then locks up and semi shuts down.
:(

---

### Post by t0p on 2008-05-28
> **Hypo_Mix said:**
> 


then i tried in VLC
it played the menu for about 15 seconds before stopping and going back to minimized (stopped) screen
same happened after hitting play.


To play a dvd in vlc, click **File > Open disc**, then check **DVD** instead of **DVD (Menus)**.  Your disc should play.

---

### Post by Hypo_Mix on 2008-05-28
> **t0p said:**
> To play a dvd in vlc, click **File > Open disc**, then check **DVD** instead of **DVD (Menus)**.  Your disc should play.

still no good :S

---

### Post by philinux on 2008-05-28
What are your full system specs.

---

### Post by Hypo_Mix on 2008-05-28
> **philinux said:**
> What are your full system specs.
is this the right stuff?
hope it means more to you than to me

```
WARNING: you should run this program as super-user.
ian-pc                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1011MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82915G/P/GV/GL/PL/910GL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV370 5B60 [Radeon X300 (PCIE)]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV370 [Radeon X300SE]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: uhci bus_master
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
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 5
                bus info: pci@0000:02:05.0
                logical name: eth0
                version: 10
                serial: 00:0f:ea:1d:5d:ac
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.1.1.102 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
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
        *-ide
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---

### Post by philinux on 2008-05-28
Ok so you got an ati radeon x300 graphics card.

Have a look in System>Admin>Hardware Drivers

---

### Post by Hypo_Mix on 2008-05-28
> **philinux said:**
> Ok so you got an ati radeon x300 graphics card.

Have a look in System>Admin>Hardware Drivers

ATI accelerated graphics driver in use...

---

### Post by philinux on 2008-05-28
Well I'd try a shutdown then a startup.

Follow this see if you've missed anything
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Hypo_Mix on 2008-05-28
> **philinux said:**
> Well I'd try a shutdown then a startup.

Follow this see if you've missed anything
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

wellp, that didn't work, some how following the instructions on that page i have managed to make VLC freeze up completely when i put a dvd in the player.

oh and dvds still don't play

and also if i turn on special effect the menu bar in a window no longer appears, i don't think this is related but i am about ready to crack it at ubuntu. it worked perfectly untill i wanted to do anything

---

### Post by philinux on 2008-05-28
Torrid.

Does mplayer play a dvd?

---

### Post by Hypo_Mix on 2008-05-28
> **philinux said:**
> Torrid.

Does mplayer play a dvd?

noup, tried about 4 different media players.

any way its too late to keep trying, i'll fix the damage i have done some other time.

---


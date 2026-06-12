---
title: "Atheros Wi-Fi problem"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Firedfox on 2008-10-11
Hey guys, my wireless card doesn't show up in the network manager but it shows up in the hardware section and it's says that it uses propriety drivers. So I'm assuming that it uses propriety drivers already or do I need new drivers or something?

---

### Post by WastePotato on 2008-10-11
Hey,

I'm relatively new here, and had the same problem as you.

Could you open up a terminal and type

network-admin 

and post the results?

Thanks.

---

### Post by Firedfox on 2008-10-11
Ok... I'm on vista now, i'll connect via Ethernet cable and post my result with Ubuntu.

:guitar:

---

### Post by Firedfox on 2008-10-11
> **WastePotato said:**
> Hey,

I'm relatively new here, and had the same problem as you.

Could you open up a terminal and type

network-admin 

and post the results?

Thanks.

(network-admin:5947): Gtk-WARNING **: Unknown property: GtkComboBox.items

came up inside the terminal, the network manager also opened

---

### Post by WastePotato on 2008-10-11
How odd.

Hmm. Try...

> sudo lshw

And post the output of that?


You know it's an Atheros, so as soon as we find the chipset, it should be easy to get working...




EDIT: 

My god I'm dumb. Shouldn't have told you to try network-manager. Same thing happened with me. :P

---

### Post by Firedfox on 2008-10-11
```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1898MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-60
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.8.2
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch ts fid vid ttp tm stc 100mhzsteps cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=64
        *-pci:1
             description: PCI bridge
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8101E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: 01
                serial: 00:a0:d1:94:cb:b5
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.4 latency=0 module=r8169 multicast=yes
        *-pci:3
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 2)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:0e:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64 module=ahci
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-cdrom
                   product: TSSTcorp CDDVDW TS-L632H
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   capabilities: packet
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:14:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:14:06.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:14:06.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ricoh-mmc latency=64 module=ricoh_mmc
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:14:06.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-generic UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:14:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

```

:)

---

### Post by thomasboleyn on 2008-10-11
I have the exact same problem, mine is an Atheros AR5212/AR5213 apparantly..though I've had no luck using madwifi so far. It actually annoyed me so much in Hardy/Intrepid I'm now back using feisty where my card is picked up no problem :confused:

---

### Post by WastePotato on 2008-10-11
Yes!

You have the same chipset as me! 

[http://ubuntuforums.org/showthread.php?t=901571](http://ubuntuforums.org/showthread.php?t=901571) <-- My thread on the issue.

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984) <-- This guys got my wifi working. 

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158) <-- This guide doesn't require you to remove stuff. Use this.

Good luck. :)


BTW: Is that a Toshiba? It looks awfully close to my model. You've even got the same graphics card as me. Compiz may be an issue, if you want to try it.

---

### Post by Firedfox on 2008-10-11
Thanks. 

I have a Toshiba a215.

:KS

---

### Post by Firedfox on 2008-10-11
I did the stuff in the 3rd link.... but I don't see the Wireless connection in the network manager. What am I supposed to do now? :confused:

---

### Post by WastePotato on 2008-10-11
Have you restarted?

---

### Post by Firedfox on 2008-10-11
> **WastePotato said:**
> Have you restarted?

Yep :(

---

### Post by WastePotato on 2008-10-11
Hmm. Try

> sudo iwlist scan

If that doesn't work, then I'm stumped. :(

---

### Post by Firedfox on 2008-10-11
> **WastePotato said:**
> Hmm. Try



If that doesn't work, then I'm stumped. :(

Tried that. :( (saw it in the thread)
Interface doesn't support scanning for both eth0 and lo.
I'm guessing eth0 is my Ethernet connection, but what's lo?

Should i try the stuff in the txt file in the 2nd link?

---

### Post by WastePotato on 2008-10-11
Only eth0 and lo came up?

Nothing about ath0?

How odd.


Could you go into Restricted drivers and untick the Atheros Driver and see if that does anything? (and restart)

---

### Post by Firedfox on 2008-10-11
> **WastePotato said:**
> Only eth0 and lo came up?

Nothing about ath0?

How odd.


Could you go into Restricted drivers and untick the Atheros Driver and see if that does anything? (and restart)

No ath0,

I unticked it and it says I gotta restart, will do so. :(

---

### Post by Firedfox on 2008-10-11
Same thing. :(:(:(:(:(

---

### Post by WastePotato on 2008-10-11
Then I am sorry to say that I am well and truly out of ideas. :(

Sorry I couldn't help.


Maybe someone else looking at the thread could chime in with any ideas? :confused:

---

### Post by WastePotato on 2008-10-12
?

---


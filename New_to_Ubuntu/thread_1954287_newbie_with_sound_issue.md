---
title: "newbie with sound issue"
date: 2012-04-07
forum: New to Ubuntu
---

### Post by Bizobinator on 2012-04-07
Hello!

So, I recently downloaded/installed Ubuntu 11.10.  I've had some odd issues with sound.

I noticed it first when I tried to play a youtube video (about 5 min after installing).  The youtube video loaded (the gray bar at the bottom), but when I tried to play, it was incredibly glitchy and played in stutters.

Later, I tried doing something else with sound (installing WoW via POL), and the same sound issue happened: it was glitchy and sounded like it was delayed/stuttered.

I've also gone into a sound check.  When I select the baseline sound system, and try to play out of the different speakers, it occasionally glitches in a similar fashion.

What is the issue?  How do I fix this?  Please post stuff in stuff a newbie can easily understand :)

---

### Post by dylan07 on 2012-04-07
Please give me information about your computer:

1) What version of ubuntu are you running? ubuntu 11.10?
2) Are you using onboard audio, or do you have a sound card? 
3) please tell me what motherboard you have and/or soundcard.

---

### Post by PhantomTurtle on 2012-04-07
I'm sure you had some other OS like Windows on there before. Did youtube video's play well on that. Did WoW play well on that? No sound issues at all?

---

### Post by Bizobinator on 2012-04-07
I'm running Ubuntu 11.10.

I think I have a sound card.  I don't remember though.  Is there a way to check?  

Also, how would I check what motherboard I have? (Although I'm fairly certain I have some sort of intel board).

Yeah, I had Windows 7 installed before this.  Everything worked fine then.

---

### Post by Basher101 on 2012-04-07
to check your entire hardware type ```
sudo lshw
``` in a terminal and post the output here. Make sure to put everything you paste inside [CODE ] [CODE ] (wihtout the spaces after the E) brackets to avoid flooding the thread.

---

### Post by dylan07 on 2012-04-07
I am actually having a sound issue as well, that i did not have in windows.

my motherboard is an MSI 790FX-GD70, I use onboard sound. My linux info is, ubuntu 11.10 64 bit, kernel 3.0.0-17-generic. My issue is static/fuzz going through my speakers, constantly, but it doesnt start until AFTER i log in. On the login screen, it doesnt have the issue.

---

### Post by Bizobinator on 2012-04-09
Here is the response I got, although I think there was too much, since it looks kind of like it cut some stuff off at the top:

            ```
 resources: irq:21 ioport:b480(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:b800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fb9f8000-fb9f83ff
        *-pci:5
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:d000(size=4096) memory:fbd00000-fbdfffff ioport:faf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 03
                serial: b8:ac:6f:cd:0e:33
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:48 ioport:d800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbde0000-fbdfffff
        *-pci:6
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:46 ioport:2000(size=4096) memory:fbc00000-fbcfffff ioport:c0200000(size=2097152)
           *-pci
                description: PCI bridge
                product: [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
                vendor: Creative Labs
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                resources: memory:fbc00000-fbcfffff
              *-multimedia
                   description: Audio device
                   product: [SB X-Fi Xtreme Audio] CA0110-IBG
                   vendor: Creative Labs
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: 00
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=HDA Intel latency=64 maxlatency=20 mingnt=2
                   resources: irq:17 memory:fbcfc000-fbcfffff
        *-pci:7
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:47 ioport:1000(size=4096) memory:fbb00000-fbbfffff ioport:c0000000(size=2097152)
           *-network DISABLED
                description: Wireless interface
                product: AR928X Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: c4:46:19:4c:09:1b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.0.0-17-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
                resources: irq:18 memory:fbbf0000-fbbfffff
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:b880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:bc00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c000(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fb9fa000-fb9fa3ff
        *-pci:8
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fba00000-fbafffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:23 memory:fbaff800-fbafffff memory:fbaf8000-fbafbfff
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:49 ioport:c880(size=8) ioport:c800(size=4) ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=32) memory:fb9fc000-fb9fc7ff
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW TS-H653H
                vendor: TSSTcorp
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D400
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: Hitachi HDS72107
                vendor: Hitachi
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: JP3O
                serial: JP2760HP0AGJKM
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f0575
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: d6762864-bb96-4ef6-ab2d-3e09c752f124
                   size: 690GiB
                   capacity: 690GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-04-02 19:55:15 filesystem=ext4 lastmountpoint=/ modified=2012-04-02 20:47:14 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2012-04-09 19:47:53 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 8181MiB
                   capacity: 8181MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 8181MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fb9fe000-fb9fe0ff ioport:400(size=32)
     *-pci:1
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:ff:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Xeon 5500/Core i7 QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:ff:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:ff:02.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Xeon 5500/Core i7 QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:ff:02.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:ff:03.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:ff:03.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Test Registers
          vendor: Intel Corporation
          physical id: 107
          bus info: pci@0000:ff:03.4
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers
          vendor: Intel Corporation
          physical id: 108
          bus info: pci@0000:ff:04.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers
          vendor: Intel Corporation
          physical id: 109
          bus info: pci@0000:ff:04.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers
          vendor: Intel Corporation
          physical id: 10a
          bus info: pci@0000:ff:04.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10b
          bus info: pci@0000:ff:04.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:12
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers
          vendor: Intel Corporation
          physical id: 10c
          bus info: pci@0000:ff:05.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers
          vendor: Intel Corporation
          physical id: 10d
          bus info: pci@0000:ff:05.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers
          vendor: Intel Corporation
          physical id: 10e
          bus info: pci@0000:ff:05.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 10f
          bus info: pci@0000:ff:05.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:16
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers
          vendor: Intel Corporation
          physical id: 110
          bus info: pci@0000:ff:06.0
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:17
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers
          vendor: Intel Corporation
          physical id: 111
          bus info: pci@0000:ff:06.1
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:18
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers
          vendor: Intel Corporation
          physical id: 112
          bus info: pci@0000:ff:06.2
          version: 05
          width: 32 bits
          clock: 33MHz
     *-pci:19
          description: Host bridge
          product: Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers
          vendor: Intel Corporation
          physical id: 113
          bus info: pci@0000:ff:06.3
          version: 05
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 0
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
```


What's the verdict doc?

---

### Post by dylan07 on 2012-04-09
If this affects your HDA Intel sound card, there are two methods the driver can read the position reports.  You can test the two different methods by editing the /etc/modprobe.d/alsa-base.conf file, and add either 
edit the file by typing, this to open it:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Add one of these, if one doesnt fix it, or causes issues, remove it and try the other. If neither fix it, or both cause issues, then remove them both after testing.
```
options snd-hda-intel position_fix=1
```or  
```
options snd-hda-intel position_fix=2
```After editing the file, reboot your computer for 
changes to take effect.  
(Technical  info: position_fix=1 will read the position from the LPIB register, and  position_fix=2 will read from the DMA position buffer map. The latter  is the default for most chips.)

---

### Post by d4m1r on 2012-04-09
Seems like you have a dedicated sound card and a decent one at that:

**description: PCI bridge                 product: [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge                 vendor: Creative Labs                 physical id: 0                 bus info: pci@0000:03:00.0                 version: 00                 width: 32 bits**

@Youtube choopyness, what browser (and version of it) are you using? Also, are you 100% you have the latest version of flash installed? I'd google something like "Ubuntu sound SB X-Fi".

As for the WoW issue, I doubt you'll be able to work it out as easily because troubleshooting programs running through WINE/POL is very difficult...

---

### Post by Bizobinator on 2012-04-09
@dylan07:  I tried both of those options, but neither worked :/.  The youtube videos were still choppy.

@d4m1r: I'm running Firefox 11.0.  I've got into the ubuntu software dealio and downloaded the adobe flash player plugin (I think it's version 11?)

I haven't just had the sound problem with youtube or the internet.  I tried to do some sound check stuff, and it had the stuttery/glitchy slow sound.

I'll go google that, see what I can come up with :/.


Thank you guys for all your help so far!  I really do appreciate it.  Any other ideas what it could be?  Or how to fix it?

---

### Post by Bizobinator on 2012-04-09
Found something potentially interesting:

[http://www.intervigil.net/sound-blaster-x-fi-titanium-hd-on-ubuntu-1110](http://www.intervigil.net/sound-blaster-x-fi-titanium-hd-on-ubuntu-1110)

Will this fix what I'm looking for?

---

### Post by dylan07 on 2012-04-09
> **Bizobinator said:**
> Found something potentially interesting:

[http://www.intervigil.net/sound-blaster-x-fi-titanium-hd-on-ubuntu-1110](http://www.intervigil.net/sound-blaster-x-fi-titanium-hd-on-ubuntu-1110)

Will this fix what I'm looking for?
looks worth trying!

---


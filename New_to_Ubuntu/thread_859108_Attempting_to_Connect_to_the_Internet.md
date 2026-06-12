---
title: "Attempting to Connect to the Internet"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by The Marsh Man on 2008-07-14
Hello ubuntu!
Right, so I'm completely lost - I only just installed ubuntu 8.04 and I know squat, and my most pressing concern being my lack of internets. I'm attempting to connect to a netgear wireless router (don't have any more details about model other than it's white - i know, not very helpful!)
I really don't know what information to provide, so perhaps it's best if you tell me.

Thanks,

Marsh

---

### Post by Ryadt on 2008-07-14
In terminal put ```
lshw
```
then print the output.

---

### Post by brian_p on 2008-07-14
> **The Marsh Man said:**
> Hello ubuntu!
Right, so I'm completely lost - I only just installed ubuntu 8.04 and I know squat, and my most pressing concern being my lack of internets. I'm attempting to connect to a netgear wireless router (don't have any more details about model other than it's white - i know, not very helpful!)
I really don't know what information to provide, so perhaps it's best if you tell me.

If it is possible I would put the wireless part to one side and first make sure  you can connect with an ethernet cable between machine and router.

Isn't the router model printed on its base?

---

### Post by The Marsh Man on 2008-07-14
unfortunately, no, it's my desktop upstairs trying to connect to the router downstairs, so to create a wired connection would involve a lot of disassembling and reassembling. I checked the router a few times, no model. There's a mac and a serial, 00184d41bb3c and 1j3268bn17768 respectively. It's the one that sky provide with their wireless broadband package. I'm just printing off the output from lshw. There's a lot of it...

---

### Post by brian_p on 2008-07-14
> **The Marsh Man said:**
> unfortunately, no, it's my desktop upstairs trying to connect to the router downstairs, so to create a wired connection would involve a lot of disassembling and reassembling. I checked the router a few times, no model. There's a mac and a serial, 00184d41bb3c and 1j3268bn17768 respectively. It's the one that sky provide with their wireless broadband package. I'm just printing off the output from lshw. There's a lot of it...

It's probably a DG834GT, not that that's particularly important for connecting to the internet. You are able to access the router with a browser?

---

### Post by The Marsh Man on 2008-07-14
Not a clue, perhaps - I had to change the encryption from WPA to WEP once, and some sky person guided me through some sort of browser thingy to change that. I've printed off that bumph now, 6 pages of computer talk for me to read through. What am I supposed to be doing with that?

---

### Post by The Marsh Man on 2008-07-14
h, and btw, the computer I'm on at the moment is a mac, and that's the one that's physically connected to the router. If that helps.

---

### Post by The Marsh Man on 2008-07-14
this is what I got:

administrator@administrator-desktop:~$ lshw
WARNING: you should run this program as super-user.
administrator-desktop     
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1009MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.3
          serial: 0000-0F43-0000-0000-0000-0000
          size: 18EHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr
          configuration: id=0
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
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV41.1 [GeForce 6800]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
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
             product: 82801G (ICH7 Family) USB UHCI Controller #2
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
             product: 82801G (ICH7 Family) USB UHCI Controller #3
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
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network:0
                description: Network controller
                product: BCM4306 802.11b/g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy LS
                vendor: Creative Labs
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=CA0106 latency=64 maxlatency=20 mingnt=2 module=snd_ca0106
           *-network:1
                description: Ethernet interface
                product: 82801G (ICH7 Family) LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:05:08.0
                logical name: eth0
                version: 01
                serial: 00:12:3f:74:a5:0e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM TS-H352C
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE02
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-RW  CRX217E
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1DS2
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801GR/GH (ICH7 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@6
       logical name: scsi6
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:1e:e2:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by appi2012 on 2008-07-14
on your mac:

download the driver here
[ftp://downloads.netgear.com/files/dg834gt_1_02_09.img](ftp://downloads.netgear.com/files/dg834gt_1_02_09.img)

mount the disk using disk utility. copy everything in it to a folder.

on ubuntu: 
insert your 8.04 disk

go to a terminal and type:
```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```

copy the folder that has the driver to your hard drive.

follow the instructions from my post on this page:
[http://ubuntuforums.org/showthread.php?t=852372&page=3](http://ubuntuforums.org/showthread.php?t=852372&page=3)
start at:
```
cd [folder that has the inf files]
```

that should set up your wireless!

---

### Post by The Marsh Man on 2008-07-14
Awesomes, I'll be back soon, presumably to tell you it worked.

---

### Post by The Marsh Man on 2008-07-14
Lame. Whenever I try and mount the image it says unable to attach, no mountable file systems

---

### Post by The Marsh Man on 2008-07-14
Right, so I have this .img file and whenever I try and mount it on Disk Utility it says can't mount, and Windows likes it even less. I've tried searching for another version of the driver in a .iso image, but no luck there either.
This is turning out to be a lot more work than Windows ever was, and I've still not got anywhere at all.

---

### Post by The Marsh Man on 2008-07-14
Please? Someone? Help?

---

### Post by brian_p on 2008-07-14
> **The Marsh Man said:**
> Please? Someone? Help?

If you look at the output from lshw you will see you have a BCM4306 802.11b/g Wireless LAN Controller. I am unfamiliar with that chipset but there is:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

to help you. It is possible the driver is already loaded into the kernel.

```
sudo lsmod | grep b43
```

to check.

---

### Post by The Marsh Man on 2008-07-14
Well I would, but I can't even get it to boot up now. all I get is this:

"BusyBox v1.1.3 (Debian 1:1,1,3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) _"

I'm now getting seriously pissed off with all of this. All I wanted was a computer that worked, and now it's even worse than it was when I started!

---


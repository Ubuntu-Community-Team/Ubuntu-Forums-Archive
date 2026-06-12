---
title: "does not recognize usb wireless interface"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by k2013anc on 2013-06-26
I am new to ubuntu I have always used windows so this is new to me. For days I have been trying to get aircrack-ng to work for me. However when I type in the command "airmon-ng" there is absolutely nothing that pops up under interface chipset etc..... I googled a lot and came accross a few posts that said I needed a usb wireless interface.. So I looked on the ubuntu website for the supported models and ended up purchasing a NETGEAR WNA1100.. here is some additional information for you guys to try and help me out please. 

> kayla@kayla-VirtualBox:~$ sudo iwconfig
[sudo] password for kayla: 
eth0      no wireless extensions.

lo        no wireless extensions.

kayla@kayla-VirtualBox:~$ sudo iwconfig eth1 down
iwconfig: unknown command "down"
kayla@kayla-VirtualBox:~$ sudo iwconfig eth1 mode managed
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; No such device.
kayla@kayla-VirtualBox:~$ sudo airmon-ng start


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
790    avahi-daemon
792    avahi-daemon
872    NetworkManager
2639    dhclient


usage: airmon-ng <start|stop|check> <interface> [channel or frequency]

kayla@kayla-VirtualBox:~$ clear

kayla@kayla-VirtualBox:~$ sudo lshw
kayla-virtualbox          
    description: Computer
    product: VirtualBox ()
    vendor: innotek GmbH
    version: 1.2
    serial: 0
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: family=Virtual Machine uuid=2BE765B5-3314-4F43-AA80-9FAE9BCA2DEB
  *-core
       description: Motherboard
       product: VirtualBox
       vendor: Oracle Corporation
       physical id: 0
       version: 1.2
       serial: 0
     *-firmware
          description: BIOS
          vendor: innotek GmbH
          physical id: 0
          version: VirtualBox
          date: 12/01/2006
          size: 128KiB
          capabilities: isa pci cdboot bootselect int9keyboard int10video acpi
     *-memory
          description: System memory
          physical id: 1
          size: 995MiB
     *-cpu
          product: Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp x86-64 constant_tsc rep_good nopl pni ssse3 lahf_lm
     *-pci
          description: Host bridge
          product: 440FX - 82441FX PMC [Natoma]
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-isa
             description: ISA bridge
             product: 82371SB PIIX3 ISA [Natoma/Triton II]
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:d000(size=16)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: VirtualBox Graphics Adapter
             vendor: InnoTek Systemberatung GmbH
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master
             configuration: latency=0
             resources: memory:e0000000-e7ffffff
        *-network
             description: Ethernet interface
             product: 82540EM Gigabit Ethernet Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             logical name: eth0
             version: 02
             serial: 08:00:27:b8:08:97
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.254.9 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:19 memory:f0000000-f001ffff ioport:d010(size=8)
        *-generic UNCLAIMED
             description: System peripheral
             product: VirtualBox Guest Service
             vendor: InnoTek Systemberatung GmbH
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
             resources: ioport:d020(size=32) memory:f0400000-f07fffff memory:f0800000-f0803fff
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=snd_intel8x0 latency=64
             resources: irq:21 ioport:d100(size=256) ioport:d200(size=64)
        *-usb
             description: USB controller
             product: KeyLargo/Intrepid USB
             vendor: Apple Inc.
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:22 memory:f0804000-f0804fff
        *-bridge UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:21 ioport:d240(size=8) ioport:d250(size=8) ioport:d260(size=16) memory:f0806000-f0807fff
     *-scsi:0
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/sr0
             logical name: /media/kayla/WNA1100
             capabilities: audio dvd
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-scsi:1
          physical id: 4
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: VBOX HARDDISK
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1.0
             serial: VBe917b990-063838e1
             size: 60GiB (64GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00052007
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 14f84e44-603d-457d-a633-366be47a1009
                size: 58GiB
                capacity: 58GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-06-24 23:49:32 filesystem=ext4 lastmountpoint=/ modified=2013-06-26 02:36:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-06-26 02:36:19 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1022MiB
                capacity: 1022MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1022MiB
                   capabilities: nofs
kayla@kayla-VirtualBox:~$ sudo lshw -businfo
Bus info          Device      Class       Description
=====================================================
                              system      VirtualBox ()
                              bus         VirtualBox
                              memory      128KiB BIOS
                              memory      995MiB System memory
cpu@0                         processor   Intel(R) Core(TM) i5-3210M CPU @ 2.50G
pci@0000:00:00.0              bridge      440FX - 82441FX PMC [Natoma]
pci@0000:00:01.0              bridge      82371SB PIIX3 ISA [Natoma/Triton II]
pci@0000:00:01.1              storage     82371AB/EB/MB PIIX4 IDE
pci@0000:00:02.0              display     VirtualBox Graphics Adapter
pci@0000:00:03.0  eth0        network     82540EM Gigabit Ethernet Controller
pci@0000:00:04.0              generic     VirtualBox Guest Service
pci@0000:00:05.0              multimedia  82801AA AC'97 Audio Controller
pci@0000:00:06.0              bus         KeyLargo/Intrepid USB
pci@0000:00:07.0              bridge      82371AB/EB/MB PIIX4 ACPI
pci@0000:00:0d.0              storage     82801HM/HEM (ICH8M/ICH8M-E) SATA Contr
                  scsi1       storage     
scsi@1:0.0.0      /dev/cdrom  disk        DVD reader
                  scsi2       storage     
scsi@2:0.0.0      /dev/sda    disk        64GB VBOX HARDDISK
scsi@2:0.0.0,1    /dev/sda1   volume      58GiB EXT4 volume
scsi@2:0.0.0,2    /dev/sda2   volume      1022MiB Extended partition
                  /dev/sda5   volume      1022MiB Linux swap / Solaris partition
kayla@kayla-VirtualBox:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 02
       serial: 08:00:27:b8:08:97
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.254.9 latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:f0000000-f001ffff ioport:d010(size=8)
kayla@kayla-VirtualBox:~$ sudo lsusb
Bus 001 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kayla@kayla-VirtualBox:~$ 


---

### Post by newb85 on 2013-06-26
Deleted duplicate...

---

### Post by newb85 on 2013-06-26
Are you running Ubuntu inside VirtualBox?  If so, the wireless should be handled by the host system, and Ubuntu will simply show a wired connection (even if you don't have a physical wired connection).

---

### Post by doctorbighands on 2013-06-26
It looks like you're running Ubuntu as a Virtualbox guest (on a Mac host?). Everything here indicates that Ubuntu can't see the USB device. Did you enable the USB WLAN device in Virtualbox? In the settings for your VM, in the USB section, make sure you include your WLAN device so the VM can see it. That way, Ubuntu can use the device "natively" as though it were attached to a host OS.

Side note: When I'm using aircrack, I always disable the host ethernet connection and use a USB device as passthrough (which is what it appears you're trying to do). In fact, I have an Alfa AWUS036NHR specifically for that purpose!

---


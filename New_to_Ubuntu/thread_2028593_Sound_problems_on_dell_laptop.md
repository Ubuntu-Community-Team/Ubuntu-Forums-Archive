---
title: "Sound problems on dell laptop"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by pratik_narain on 2012-07-18
I am certainly very happy with ubuntu as an os. Currently I am using the latest ubuntu 12.04 precise and it is by far the best os in the world. And btw, unity is awesome.

Now as with every thing, I have a small problem. I am getting no sound out of my laptop speakers. Sound is coming when I connect my earphones. I am giving below my laptop specs in detail. Kindly help me with this problem.

Model - Dell Inspiron 1545
OS - Ubuntu 12.04(fully updated)

---

### Post by mebomechanicno1 on 2012-07-18
Try opening a terminal (hold CTRL ALT and press T) then copy and paste 
 
sudo gedit /etc/modprobe.d/alsa-base.conf &
 
[FONT=Arial]You shoudl be prompted for your password, insert it (don't worry if the password does not appear as you are typing; type it then hit return, then copy and paste:[/FONT]
 
options snd-hda-intel model=generic.

---

### Post by jmfal on 2012-07-18
Welcome to Ubuntu
Run these commands in a terminal
```
  aplay -l      
``` 
And 
```
sudo lshw     
```

Please post output between [CODE][CODE]  brackets using # above reply window.

---

### Post by pratik_narain on 2012-07-18
output of aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

output of sudo lshw

```
pratik-laptop             
    description: Portable Computer
    product: Inspiron 1545 ()
    vendor: Winbond Electronics
    serial: JB2F3BS
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-4200-1032-8046-CAC04F334253
  *-core
       description: Motherboard
       vendor: Winbond Electronics
       physical id: 0
       serial: .JB2F3BS.              .
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A14
          date: 12/07/2009
          size: 64KiB
          capacity: 15MiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Microprocessor
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: cores=2 enabledcores=2 id=0 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: M4 70T2864QZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: 9565E6EE
             slot: DIMM_A
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR Synchronous 800 MHz (1.2 ns)
             product: HMP125S6EFR8C-S6
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 1
             serial: 00002026
             slot: DIMM_B
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
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:f6d00000-f6efffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RV710 [Mobility Radeon HD 4300 Series]
                vendor: Hynix Semiconductor (Hyundai Electronics)
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:48 memory:e0000000-efffffff ioport:de00(size=256) memory:f6df0000-f6dfffff memory:f6d00000-f6d1ffff
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
             resources: irq:20 ioport:6f60(size=32)
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
             resources: irq:21 ioport:6f80(size=32)
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
             resources: irq:22 ioport:6fa0(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
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
             resources: irq:47 memory:f6ffc000-f6ffffff
        *-pci:1
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
             resources: irq:41 ioport:3000(size=4096) memory:c0400000-c05fffff ioport:c0600000(size=2097152)
        *-pci:2
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
             resources: irq:42 ioport:2000(size=4096) memory:f6c00000-f6cfffff ioport:c0200000(size=2097152)
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:25:56:43:82:3b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f6cfc000-f6cfffff
        *-pci:3
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
             resources: irq:43 ioport:c000(size=4096) memory:f6b00000-f6bfffff ioport:c0000000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 13
                serial: 00:25:64:5f:ac:0f
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:f6bfc000-f6bfffff ioport:ce00(size=256)
        *-pci:4
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
             resources: irq:44 ioport:b000(size=4096) memory:f6800000-f6afffff ioport:f0000000(size=2097152)
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
             resources: irq:20 ioport:6f00(size=32)
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
             resources: irq:21 ioport:6f20(size=32)
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
             resources: irq:22 ioport:6f40(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:5
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:6e70(size=8) ioport:6e78(size=4) ioport:6e80(size=8) ioport:6e88(size=4) ioport:6ea0(size=32) memory:fed1c800-fed1cfff
           *-disk
                description: ATA Disk
                product: WDC WD3200BEVT-7
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXH409979235
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0000ef91
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 62336266-3410-432c-a5a1-23bb8e976cc1
                   size: 19GiB
                   capacity: 20GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-02-20 10:17:17 filesystem=ntfs label=Windows state=clean
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: 53ee4441-c96e-46d1-9a6d-8299d058e270
                   size: 4GiB
                   capacity: 4GiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:2
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 020da1d4-7e44-4fbd-9ce7-684729970b82
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2012-07-14 05:33:34 filesystem=ext4 lastmountpoint=/ modified=2012-07-14 00:42:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2012-07-18 22:20:31 state=mounted
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 244GiB
                   capacity: 244GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /home
                      capacity: 244GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,user_xattr,acl,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW AD-7560S
                vendor: Optiarc
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: SD05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f6ffbf00-f6ffbfff ioport:1100(size=32)
  *-battery
       product: DELL Y823G95
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 44000mWh
       configuration: voltage=11.1V

```

---

### Post by NikTh on 2012-07-18
Hi , 
please open a terminal and write this 
```
sudo alsa force-reload
``` 
check if sound works. 
Thanks

---

### Post by pratik_narain on 2012-07-18
NikTh - Thnx but it didn't work

---

### Post by jmfal on 2012-07-18
Open a terminal and run

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf     
```

Enter password in window
Scroll to end of file and enterthis line
```
   options snd-hda-intel model=generic    
```
Save/close and save to etc (ckicj on etc in window and save)

Restart laptop 
open alsamixer and make sure all speaker/pcm are not muted
play some music

If that doesn't work go back into file and change"= generic" to"= auto"  (no quotes)

---

### Post by pratik_narain on 2012-07-18
> **jmfal said:**
> Open a terminal and run

```
 gksudo gedit /etc/modprobe.d/alsa-base.conf     
```

Enter password in window
Scroll to end of file and enterthis line
```
   options snd-hda-intel model=generic    
```
Save/close and save to etc (ckicj on etc in window and save)

Restart laptop 
open alsamixer and make sure all speaker/pcm are not muted
play some music

If that doesn't work go back into file and change"= generic" to"= auto"  (no quotes)
didn't work. tried both "generic" and "auto"

---

### Post by NikTh on 2012-07-18
Hi , 
did you try what @jmfal told you ? 

> **jmfal said:**
> 
open alsamixer and make sure all speaker/pcm are not muted


Open a terminal and write 
```
alsamixer
```check if something is muted [MM] and un-mute it with "m" key . You can volume-up or down with arrow keys. 
Thanks

---

### Post by jmfal on 2012-07-18
Were there any options before you entered these options?

Try  and change it to :::    =m81

Restart
check alsamixer again
 play some music

---

### Post by pratik_narain on 2012-07-18
> **NikTh said:**
> Hi , 
did you try what @jmfal told you ? 



Open a terminal and write 
```
alsamixer
```check if something is muted [MM] and un-mute it with "m" key . You can volume-up or down with arrow keys. 
Thanks
nothing was muted. i double checked

---

### Post by pratik_narain on 2012-07-18
> **jmfal said:**
> Were there any options before you entered these options?

Try  and change it to :::    =m81

Restart
check alsamixer again
 play some music
putting m81 also didn't work. now its late here and i should sleep. i will try further solutions tomorrow.

---

### Post by pratik_narain on 2012-07-18
> **pratik_narain said:**
> putting m81 also didn't work. now its late here and i should sleep. i will try further solutions tomorrow.
and there were no "option" lines before I put one in there.

---

### Post by pratik_narain on 2012-07-19
> **pratik_narain said:**
> I am certainly very happy with ubuntu as an os. Currently I am using the latest ubuntu 12.04 precise and it is by far the best os in the world. And btw, unity is awesome.

Now as with every thing, I have a small problem. I am getting no sound out of my laptop speakers. Sound is coming when I connect my earphones. I am giving below my laptop specs in detail. Kindly help me with this problem.

Model - Dell Inspiron 1545
OS - Ubuntu 12.04(fully updated)
sry to bother friends. it was a hardware fault. the laptop speakers failed. i tested them and i m not getting dound even in my windows installation. thnx for the help anyways.

---


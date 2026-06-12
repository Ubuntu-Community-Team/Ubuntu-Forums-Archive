---
title: "Need help maximizing performance."
date: 2011-10-09
forum: New to Ubuntu
---

### Post by th3k1ng on 2011-10-09
Hello everyone! This is my first post on Ubuntu forums. 
Okay, so I've had Ubuntu for about a year now, but never really got into it. I'm an inspiring programmer, and have tried to get techy with linux, but haven't really got there yet.
 I'm currently using a few year old laptop, the Acer 5315, and I've had to fix a ton of stuff to get it to work normally. Anyway, lately it seems Ubuntu is getting slower and slower. Many times it will freeze up, small things will slow everything down, so on and so forth. I've read things about getting Ubuntu to be the eye candy it can be, but not as much about getting it to preform as well as it can. I'm semi computer smart, I hope to get better and make a job of it when I'm older, so I don't have to be treated like a total beginner. 

Computer Info :
**Acer Aspire 5315**
**Video Card** : Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller. 
**Ubuntu 10.04**

Specific little issues : 
The menus like Applications Places and System are a bit laggy, they take a few seconds to open.
The computer seems too easy to bog down, I'm not sure if this is Chromium, or something else. 

Any help would appreciated.

---

### Post by wildmanne39 on 2011-10-09
Hi, you can run top in a terminal and see what is eating up resources, you may have a application not responding.

You can also use system monitor instead of top but top does a better job.

You can look at your log files and see if there are any errors.
```
sudo tail -n100 /var/log/syslog
```
```
dmesg | less
```
Thank you

---

### Post by th3k1ng on 2011-10-09
> **wildmanne39 said:**
> Hi, you can run top in a terminal and see what is eating up resources, you may have a application not responding.

You can also use system monitor instead of top but top does a better job.

You can look at your log files and see if there are any errors.
```
sudo tail -n100 /var/log/syslog
```
```
dmesg | less
```
Thank you

Thanks, I've done these things before. Nothing ever seems to be doing anything.

---

### Post by dFlyer on 2011-10-09
How much memory do you have?

How much of your swap space are you using?

How much eye candy have you installed?

---

### Post by wildmanne39 on 2011-10-09
Hi, you may want to also run a disk check and make sure your drive does not have bad sectors, mine recently crashed I have it running but not like it was so I am setting up 11.10 since I have been running it for testing and it is about to be released.

You may want to check disk space and make sure it is not getting low.

Please post the results of this command:
```
sudo lshw
```
Thank you

---

### Post by th3k1ng on 2011-10-09
> **wildmanne39 said:**
> Hi, you may want to also run a disk check and make sure your drive does not have bad sectors, mine recently crashed I have it running but not like it was so I am setting up 11.10 since I have been running it for testing and it is about to be released.

You may want to check disk space and make sure it is not getting low.

Please post the results of this command:
```
sudo lshw
```
Thank you
Haha. Okay. /
> justin-aspire-5315        
    description: Computer
    product: Aspire 5315
    vendor: Acer
    version: V1.43
    serial: LXALC0Y0797380670A1601
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: cpus=1 uuid=3B178399-8347-7389-E0D2-001B3852A26C
  *-core
       description: Motherboard
       product: Acadia
       vendor: Acer
       physical id: 0
       version: V1.43
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Acer
          physical id: 0
          version: V1.43 (06/25/2008)
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305436353534455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 0
             serial: 0xE208C6D0
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: 0x4D342037305436353534455A332D43453620
             vendor: 0xCE00000000000000
             physical id: 1
             serial: 0xE1024361
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU          530  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 20
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          slot: uPGA-478
          size: 1733MHz
          capacity: 1733MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
        *-cache:0
             description: L2 cache
             physical id: 21
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 23
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
     *-cache
          description: L1 cache
          physical id: 22
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:54000000-540fffff memory:40000000-4fffffff ioport:5110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:58400000-584fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:50c0(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:50a0(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:58304c00-58304fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:46 memory:58300000-58303fff
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
             resources: irq:40 ioport:4000(size=4096) memory:57300000-582fffff ioport:50000000(size=16777216)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:56300000-572fffff ioport:51000000(size=16777216)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:55200000-562fffff ioport:52000000(size=16777216)
           *-network
                description: Ethernet interface
                product: NetLink BCM5906M Fast Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 02
                serial: 00:1b:38:52:a2:6c
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:47 memory:55200000-5520ffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:1000(size=4096) memory:54100000-551fffff ioport:53000000(size=16777216)
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: wlan0
                version: 01
                serial: 00:1c:26:c7:74:7a
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-30-generic firmware=N/A ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:54100000-5410ffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:5080(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:5060(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:5040(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:58304800-58304bff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:50e0(size=16)
           *-cdrom
                description: DVD reader
                product: CD-RW CRX880A
                vendor: Optiarc
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: KX07
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:50f8(size=8) ioport:511c(size=4) ioport:50f0(size=8) ioport:5118(size=4) ioport:5020(size=32) memory:58304000-583047ff
           *-disk
                description: ATA Disk
                product: Hitachi HTS54108
                vendor: Hitachi
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: MB4O
                serial: MPBDP0XKK01VVM
                size: 73GiB (78GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00063249
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 05379ceb-e949-4224-b8ce-7435c08ca46b
                   size: 70GiB
                   capacity: 70GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-05 11:40:08 filesystem=ext4 lastmountpoint=/Fr&#65533;p&#65533;&#65533;[&#65533;&#65533;&#65533;&#615;&#65533;P&#65533;&#65533;&#65533;&#1280;!&#65533;&#65533;[&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;1&#65533;&#65533;p&#65533;&#65533;A&#65533;h&#65533;&#65533;&#65533;y&#65533;!&#65533;} modified=2011-07-06 15:21:33 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-10-02 16:35:48 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2998MiB
                   capacity: 2998MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2998MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:58305000-583050ff ioport:5000(size=32)
  *-battery
       description: Lithium Ion Battery
       product: Li-ion(6cell)
       vendor: Sony
       physical id: 1
       serial: Not Supported
       slot: Internal Battery
       capacity: 51840mWh
       configuration: voltage=10.8V


---

### Post by th3k1ng on 2011-10-09
> **dFlyer said:**
> How much memory do you have?

How much of your swap space are you using?

How much eye candy have you installed?

Sorry for the double post. 

I'm not sure how to check the first two things. And I don't have any special eye candy.

---

### Post by dFlyer on 2011-10-09
open a terminal then enter

free -tom

Post the results.

---

### Post by wildmanne39 on 2011-10-09
Hi, from the information I do not see anything that is wrong.

I will say that this is not a very powerful computer so you will not have great speed, but if it has slowed down I only have a couple of suggestions that I have not mentioned.

1. You can install bleachbit to remove files that are no longer need. [COLOR="Red"]**Watch what you remove sometimes it will remove applications that are still being used. **[/COLOR]

2. Go to start up applications and uncheck applications that you do not need to run.
Thank you

---

### Post by Zeta-K on 2011-10-09
Use an lxde, xfce, awesome, or fluxbox environment. You should get Plenty of speed from it. You could also look into lubuntu, debian, or if you want a challenge, gentoo or archlinux.

---

### Post by th3k1ng on 2011-10-09
> **dFlyer said:**
> open a terminal then enter

free -tom

Post the results.
>              total       used       free     shared    buffers     cached
Mem:           992        664        327          0         14        267
Swap:         2997        165       2832
Total:        3990        830       3159

Wildmanne, thank you. I will do that.

Zeta, what exactly are those things?

Thanks alot you guys! I love learning new things, even if they don't help. :)

---

### Post by dFlyer on 2011-10-09
> **th3k1ng said:**
> Wildmanne, thank you. I will do that.

Zeta, what exactly are those things?

Thanks alot you guys! I love learning new things, even if they don't help. :)

It shows you have 1 gig of ram, and about 3 gig swap file of which your using 165 meg of your swap file.

You might want to try increasing your ram to 2 gig which would take away your use of the swap file. 1 gig is good, 2 gig better and 4 gig great on a 32 bit system running pae kernel.

You might also look at a lighter version of ubuntu as posted above.

---

### Post by th3k1ng on 2011-10-09
> **dFlyer said:**
> It shows you have 1 gig of ram, and about 3 gig swap file of which your using 165 meg of your swap file.

You might want to try increasing your ram to 2 gig which would take away your use of the swap file. 1 gig is good, 2 gig better and 4 gig great on a 32 bit system running pae kernel.

You might also look at a lighter version of ubuntu as posted above.
Ah, thank you!

---

### Post by Zeta-K on 2011-10-09
Lxde, xfce, awesome, and fluxbox are Desktop Environments. Download them with synaptic. They are WAY more lightweight  desktop environments than gnome, kde, or unity. After installation, you  will be able to choose them from the login screen. It gets some getting  used to, as they have less eye-candy. But they are functional and some prefer less eye-candy.

Lubuntu is the most lightweight full-featured ubuntu distro I've seen. Mostly because it uses a lighter Desktop Environment, though.

Debian is what Ubuntu was based on. It has a slightly bigger learning curve than ubuntu and an installation system that I hate, but it would be rather similar to ubuntu in functionality.

Archlinux is a highly configurable distro with a steep learning curve compared to ubuntu and Debian, but is worth it for the control you obtain over the system.

Gentoo I DO NOT suggest if you know little enough that I had to post this. It is very powerful, but requires hours (days) of tweaking to even get a gnome desktop if you have no idea what you're doing. Trust me, two of my friends started installing it about a week ago and haven't finished yet. If you're trying to become a programmer though, you may be interested in it after you've learned a bit more.

---

### Post by th3k1ng on 2011-10-09
> **Zeta-K said:**
> Lxde, xfce, awesome, and fluxbox are Desktop Environments. Download them with synaptic. They are WAY more lightweight  desktop environments than gnome, kde, or unity. After installation, you  will be able to choose them from the login screen. It gets some getting  used to, as they have less eye-candy. But they are functional and some prefer less eye-candy.

Lubuntu is the most lightweight full-featured ubuntu distro I've seen. Mostly because it uses a lighter Desktop Environment, though.

Debian is what Ubuntu was based on. It has a slightly bigger learning curve than ubuntu and an installation system that I hate, but it would be rather similar to ubuntu in functionality.

Archlinux is a highly configurable distro with a steep learning curve compared to ubuntu and Debian, but is worth it for the control you obtain over the system.

Gentoo I DO NOT suggest if you know little enough that I had to post this. It is very powerful, but requires hours (days) of tweaking to even get a gnome desktop if you have no idea what you're doing. Trust me, two of my friends started installing it about a week ago and haven't finished yet. If you're trying to become a programmer though, you may be interested in it after you've learned a bit more.

I have another computer, that I really have no use for other than to try different things on. I might try to do that. I know more than it seems, I just make sure. I didn't know about the lightweight versions of ubuntu, though, I've never read about them. Thanks bunches man!

---


---
title: "Laptop Heat and Graphics Issues"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by funcify on 2011-12-19
Hello,

Laptop specs:
Toshiba Satellite T135D-S1320
Proc: AMD Athlon Neo MV-40
3GB RAM
Graphics: ATI Radeon 3200

So I decided to give Linux a try about a week ago, and installed Ubuntu 11.10.  I really liked the look and feel of the interface, but I found that it was bogging down pretty badly, and my laptop was getting hot (even while just running XScreenSaver the fan was going full blast and the back of the case was hot to the touch).  

So two days ago, I switched to lubuntu.  It runs much more smoothly  and overall I really like it.  However, I am still having some heat issues (though not to the degree I experienced with full Ubuntu).  It is still pretty warm to the touch almost constantly, even with just XScreenSaver running in black screen mode.  I have installed Jupiter, and set it to "High Performance" mode.  It seems to have helped marginally, but not much.  I have also edited GRUB as per the suggestions [here](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/).  Not really sure what this was supposed to do, but I did it anyways :).

I'm also experiencing major slowness with pdf images.  I've been trying to view a scanned book, but it takes about 30 seconds per page to load, and is basically unusable.  I have installed the proprietary AMD graphics drivers; the "post-release update" version would not activate, but I was able to activate the previous version.  Not really sure what to do beyond that, because, well I'm a noob.  But any help would greatly be appreciated.  I am really eager to learn the ropes.

Thank you for reading.

---

### Post by amjjawad on 2011-12-22
> **funcify said:**
> Hello,

Laptop specs:
Toshiba Satellite T135D-S1320
Proc: AMD Athlon Neo MV-40
3GB RAM
Graphics: ATI Radeon 3200

So I decided to give Linux a try about a week ago, and installed Ubuntu 11.10.  I really liked the look and feel of the interface, but I found that it was bogging down pretty badly, and my laptop was getting hot (even while just running XScreenSaver the fan was going full blast and the back of the case was hot to the touch).  

So two days ago, I switched to lubuntu.  It runs much more smoothly  and overall I really like it.  However, I am still having some heat issues (though not to the degree I experienced with full Ubuntu).  It is still pretty warm to the touch almost constantly, even with just XScreenSaver running in black screen mode.  I have installed Jupiter, and set it to "High Performance" mode.  It seems to have helped marginally, but not much.  I have also edited GRUB as per the suggestions [here]("http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround/").  Not really sure what this was supposed to do, but I did it anyways :).

I'm also experiencing major slowness with pdf images.  I've been trying to view a scanned book, but it takes about 30 seconds per page to load, and is basically unusable.  I have installed the proprietary AMD graphics drivers; the "post-release update" version would not activate, but I was able to activate the previous version.  Not really sure what to do beyond that, because, well I'm a noob.  But any help would greatly be appreciated.  I am really eager to learn the ropes.

Thank you for reading.

Hello and Welcome to Ubuntu Forum and thanks for using Lubuntu :)

I've been told that AMD Processors are not good as Intel and same goes to ATI. However, your case might be different.

1) Kindly post the output of these commands:

```
lsb_release -a

```

and

```
uname -r

```


2) Is this new machine?

3) Is there any thing in BIOS that can tell about the status or speed of your FAN?

4) Overheating is less with Lubuntu but it's still hot, right? just to confirm!

5) What is the output of 

```
sudo lshw -C display
```

Please make sure to wrap up the text with "CODE" tags when posting any output of any command:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

Thank you!

---

### Post by wildmanne39 on 2011-12-22
Hi amjjawad, this is not true in my opinion > I've been told that AMD Processors are not good as Intel
I have ran both with out any problems from either.
Thanks

---

### Post by |{urse on 2011-12-22
Definitely stick around for other suggestions BUT this is a known issue with your laptop regardless of what OS it is running.

Massive recall on your model..
[http://news.cnet.com/8301-31021_3-20015470-260.html](http://news.cnet.com/8301-31021_3-20015470-260.html)

the fix for this problem is a bios update on their site.

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2761378&ref=EV](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2761378&ref=EV)

I'd hurry and fix it fast, says the plastic around the battery jack can literally melt and cause a fire.

---

### Post by |{urse on 2011-12-22
Well, I hope OP sees that, I'd hate for them to come back home to a smoldering pile of plastic and then notice someone posted a solution 2 days later. :s

---

### Post by funcify on 2011-12-22
Thanks for responding, amjjawad.
I am unable to boot into my normal installation of lubuntu; I have posted another thread about it [HERE](http://ubuntuforums.org/showthread.php?t=1898714).  However, I'll enter the commands using the live usb from which I installed it.

1)lubuntu 11.10 oneiric, 
kernel version 3.0.0-12-generic

2)No, it is about 2 years old.

3)I will check the BIOS and post back.

4)Yes, that is correct.  The heat is not as intense with lubuntu but it is still considerable.  

5)
```

ubuntu                    
    description: Notebook
    version: PST3LU-00F001
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=202E19FF-6101-DF11-B305-00269EC04D80
  *-core
       description: Motherboard
       product: Satellite T135D
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: 1A043963W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.90
          date: 07/21/2010
          size: 113KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int5printscreen int9keyboard int14serial int17printer int10video acpi usb ieee1394boot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Neo Processor MV-40
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          slot: S1G1/BGA
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow up extd_apicid pni cx16 lahf_lm svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: S1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: S2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: Toshiba America Info Systems
             vendor: Toshiba America Info Systems
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:cfd00000-cfefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: RS780M/RS780MN [Radeon HD 3200 Graphics]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff
           *-multimedia
                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:cfdec000-cfdeffff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 1)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:80000000-800fffff
           *-network
                description: Ethernet interface
                product: AR8132 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: eth0
                version: c0
                serial: 00:26:9e:c0:4d:80
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
                resources: irq:42 memory:80000000-8003ffff ioport:1000(size=128)
        *-pci:2
             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:f0500000-f05fffff
           *-network
                description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 10
                serial: 00:26:b6:c3:a2:54
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 ioport:d000(size=256) memory:f0500000-f0503fff
        *-storage
             description: SATA controller
             product: SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:8420(size=8) ioport:8414(size=4) ioport:8418(size=8) ioport:8410(size=4) ioport:8400(size=16) memory:f0808000-f08083ff
           *-disk
                description: ATA Disk
                product: TOSHIBA MK2555GS
                vendor: Toshiba
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FG00
                serial: Z949CIHQT
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000237fc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 5d2ca1ff-b8e0-475e-b60a-ba5b4c730466
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-12-12 20:30:34 filesystem=ext4 lastmountpoint=/ modified=2011-12-12 20:49:47 mounted=2011-12-22 22:11:46 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1789MiB
                   capacity: 1789MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1789MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0604000-f0604fff
        *-usb:1
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:f0605000-f0605fff
        *-usb:2
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:f0808400-f08084ff
        *-usb:3
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0606000-f0606fff
        *-usb:4
             description: USB Controller
             product: SB7x0 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:f0607000-f0607fff
        *-usb:5
             description: USB Controller
             product: SB7x0/SB8x0/SB9x0 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:f0808800-f08088ff
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3c
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:f0600000-f0603fff
        *-isa
             description: ISA bridge
             product: SB7x0/SB8x0/SB9x0 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@1:1
          logical name: scsi1
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: SanDisk Cruzer
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 8.02
             serial: u
             size: 7663MiB (8036MB)
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 7663MiB (8036MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=00041b71
              *-volume
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /cdrom
                   version: FAT32
                   serial: b353-c8c8
                   size: 7661MiB
                   capacity: 7662MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=A mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
        *-cdrom
             description: SCSI CD-ROM
             product: SanDisk Cruzer
             vendor: SanDisk
             physical id: 0.0.1
             bus info: scsi@1:0.0.1
             logical name: /dev/cdrom
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/U3 System
             version: 8.02
             serial: u
             capabilities: removable audio
             configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /media/U3 System
                configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500 state=mounted
dubuntu@ubuntu:~$ uname -r
3.0.0-12-generic
ubuntu@ubuntu:~$ uname -r
3.0.0-12-generic
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
ubuntu@ubuntu:~$ uname -r
3.0.0-12-generic
ubuntu@ubuntu:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff

```

---

### Post by amjjawad on 2011-12-23
> **wildmanne39 said:**
> Hi amjjawad, this is not true in my opinion 
I have ran both with out any problems from either.
Thanks

Hello my friend :)

> **amjjawad said:**
> **I've been told** that AMD Processors are not good as Intel

I have never used AMD Processors, I've been told these are not as good as Intel :)
Perhaps the one who told me had a bad experience with AMD.

Take care :)

---

### Post by amjjawad on 2011-12-23
> **|{urse said:**
> Definitely stick around for other suggestions BUT this is a known issue with your laptop regardless of what OS it is running.

Massive recall on your model..
[http://news.cnet.com/8301-31021_3-20015470-260.html](http://news.cnet.com/8301-31021_3-20015470-260.html)

the fix for this problem is a bios update on their site.

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2761378&ref=EV](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/bulletin.jsp?ct=SB&soid=2761378&ref=EV)

I'd hurry and fix it fast, says the plastic around the battery jack can literally melt and cause a fire.

@OP

As I mentioned on my last reply/post on your other thread, this is VERY important and the above posts confirms there is an issue with your model so that's two of us confirming that, actually 3 :)

Please check and let us know what will happen with you!

That's why I like Desktop PCs, never have to worry about that. I don't play, I don't do anything that will add any load so I'm fine.

---

### Post by |{urse on 2011-12-23
Haha, yeah, I didn't want to be rude and shout over anyone.. but you need to follow the links in my post above to fix your problem. All the bios update does is allow io to check for a faulty wire harness, If you have one of the faulty harnesses the bios will then let you know that you need to contact toshiba to send your unit in.

Toshiba did something similar to this in 1997 with another recall involving exploding sony batteries. I'd heed their warning if I were you. They may throw in a ram upgrade if you complain to the right person (they've done it for me before on a similar issue).

---

### Post by funcify on 2011-12-24
> **|{urse said:**
> Haha, yeah, I didn't want to be rude and shout over anyone.. but you need to follow the links in my post above to fix your problem. All the bios update does is allow io to check for a faulty wire harness, If you have one of the faulty harnesses the bios will then let you know that you need to contact toshiba to send your unit in.

Toshiba did something similar to this in 1997 with another recall involving exploding sony batteries. I'd heed their warning if I were you. They may throw in a ram upgrade if you complain to the right person (they've done it for me before on a similar issue).

Yea . . . 

From the 2nd link you posted:
"Should the BIOS determine that a harness failure is occurring, external power will immediately be disabled eliminating the possibility of the over heating.  You will then need to contact the Toshiba call center to set up a warranty repair.  If the harness failure is detected while the system is operating you will receive a system message indicating that the failure has occurred and that external power has been disabled.  You may continue to use the system, without risk of overheating, using the remaining battery charge.  You should immediately close all open files and applications to avoid any data loss.  Once the data has been saved the system should be properly shutdown.   It will not be possible to recharge the battery within the system until it has been repaired."

I'm going to hold off on doing this update for a week or so.  Out of town at the moment and can't really afford to be locked out of my laptop.  

But still, I don't think this is a related issue.  The heat is definitely not coming from the power input area, but from the processor and gpu.  Also, the heat issue was not present with Windows 7 (except of course during heavy processing).  I am sure it is software related.

---

### Post by |{urse on 2011-12-25
Suit yourself :)

---


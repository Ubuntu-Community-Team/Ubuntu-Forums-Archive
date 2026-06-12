---
title: "Do I have a bad 12.04 instal?"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2013-03-26
Using a disk burned 8 months ago I put 12.04 on my desktops new 300GB hard drive 2 days a go, got all updates. Added  some firefox add ons to stop so much tracking. Everything seemed good Only have mouse, keyboard, monitor and sound plugged in. Everything seemed good but everyday Firefox locks up and all I can do is  get to terminal and give it  sudo halt now.
The machine can't shut down. I get an ubuntu close down screen that has 5 luittle lights showing the progress of shut down, but afdter an hour I have to resort to the power switch.
This sounds to me like the beginning of a long bad experience, but what can be done?
If you have a suggestion, please keep directions basic. Thanks
Mickey Pilgrim

---

### Post by gifford on 2013-03-26
What are the hardware specifications, video card, etc? Some folks have had an issue with 12.04 shutting down properly, myself included. There are some fixes. But first, let's get your specifics.

---

### Post by MickeyPilgrim on 2013-03-26
Can you show the commands needed to produce  a list of hardware specs.? Afraid I don't know them or where to find them. But thanks
Mickey Pilgrim

---

### Post by deadflowr on 2013-03-26
```
sudo lshw
```

```
lspci
```

```
lsusb
```

Just a couple generic commands to show some hardware.

---

### Post by gifford on 2013-03-26
Try this: sudo lshw.
Post what video card you have and whether proprietary drivers are in use.

---

### Post by MickeyPilgrim on 2013-03-26
> **gifford said:**
> Try this: sudo lshw.
Post what video card you have and whether proprietary drivers are in use.
===============================================================================

Everything seemed to be working, so I haven't messed with any drivers. Looking below, I saw the video card shown as ....   G72 [GeForce 7300 LE]
                vendor: NVIDIA Corporation
. 
I'm pasting below what came up as a description.
MickeyPilgrim
=======================================================================

sysinfo@mikescomputer:~$ lshw
WARNING: you should run this program as super-user.
            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2011MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:fa000000-fcffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G72 [GeForce 7300 LE]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff memory:fb000000-fbffffff memory:fc000000-fc01ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fdff8000-fdffbfff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:80300000-804fffff ioport:80500000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:d000(size=4096) memory:7ff00000-802fffff ioport:fde00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 06
                serial: 6c:f0:49:c5:57:90
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.103 latency=0 multicast=yes port=MII speed=100Mbit/s
                resources: irq:43 ioport:de00(size=256) memory:fdeff000-fdefffff memory:fdef8000-fdefbfff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff00(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:fe00(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:fd00(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:fc00(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fdfff000-fdfff3ff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fdd00000-fddfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: uPD72873 [Firewarden] IEEE1394a OHCI 1.1 Link/2-port PHY Controller
                vendor: NEC Corporation
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=44 mingnt=20
                resources: irq:19 memory:fddff000-fddfffff
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
        *-ide:0
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
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f900(size=16)
           *-cdrom
                description: SCSI CD-ROM
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/sr0
                capabilities: audio
                configuration: status=nodisc
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f800(size=8) ioport:f700(size=4) ioport:f600(size=8) ioport:f500(size=4) ioport:f400(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 0.1.0
                bus info: scsi@2:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr1
                version: BL02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
sysinfo@mikescomputer:~$

---

### Post by gifford on 2013-03-26
This is how I fixed the problem on my system. [http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer)
I now make sure I update grub & grub2 when a new kernel is installed.
Let us know if it works for you.

---

### Post by MickeyPilgrim on 2013-03-26
The first problem is that everything froze. I could guess that proprietary drivers could fix that, but it looks from the "AskUbuntu" reference that people have had to uninstal those ([http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer](http://askubuntu.com/questions/125844/shutdown-does-not-power-off-computer))

I do not know if a kernel was updated - I just let Ubuntu do it's thing.
Has my kernel been changed?

---

### Post by iMac71 on 2013-03-26
> **MickeyPilgrim said:**
> I do not know if a kernel was updated - I just let Ubuntu do it's thing.
Has my kernel been changed?use this command```
uname -r
```to show your kernel release.

---

### Post by deadflowr on 2013-03-26
Since your running Nvidia 7300 LE graphics, I;d follow along with this to see about using the closed-source drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

At this point, it might be best to go with nvidia-current over any of the other options.

Then, if it doesn't work, move up the list.

---

### Post by MickeyPilgrim on 2013-03-26
My kernel is shown as 

3.2.0-39-generic-pae

is this the original kernel for 12.04 ?

I had forgotten that I quit Ubuntu a while back because of the way they would sneak a new kernel in with other, more routine updates, and then I would be frustrated with the advice to only instal a new kernel in a new clean instal. After a lot of consideration I decided to go with Ubuntu again, and when finishing the instal I see that there are 250 Mb od updates. I thought, "certainly they wont put kernels on top of kernels". Was I wrong?
===================================================================



> **iMac71 said:**
> use this command```
uname -r
```to show your kernel release.

---

### Post by MickeyPilgrim on 2013-03-26
Thank you for that.   I guess this means that I have not been running Unity, whatever that is.  Could that be why the 'Hide the Launcher buttons " feature is so insensitive that it can't be used?
MickeyP

---

### Post by matt_symes on 2013-03-26
Hi

You can check when your new kernels were installed with this command.

```
grep ".*[^-]installed.*linux-image-[0-9].*" /var/log/dpkg.log
```

Can you marry up the dates with when the problem started happening ?

Kind regards

---

### Post by MickeyPilgrim on 2013-03-26
Looks like the original kernal was updated one when I ran the post-instalation updates- it shows this...

2012-04-23 11:35:46 status installed linux-image-3.2.0-23-generic-pae 3.2.0-23.36
2013-03-24 13:08:33 status installed linux-image-3.2.0-39-generic-pae 3.2.0-39.62

It was suggested that I get in the terminal and update grub and grub2, but I don't know anything about that and would expect that ubuntu would take care of that on its own. So I'll see if the Nvidia drivers stop the lock-up.

Where can I find a list of alternative commands to try differnt turn off commands?
Mickey Pilgrim
=====================================================



> **matt_symes said:**
> Hi

You can check when your new kernels were installed with this command.

```
grep ".*[^-]installed.*linux-image-[0-9].*" /var/log/dpkg.log
```

Can you marry up the dates with when the problem started happening ?

Kind regards

---

### Post by matt_symes on 2013-03-26
Hi

Boot into your old kernel from the grub menu. Use the system for a period of time. 

Do you still get lockups ?

If not then one option is to remove the newest kernel and pin the old one so it will not update (or uninstall the package linux-image).

> matthew-S206:/home/matthew % apt-cache show linux-image
<snip>
Description-en: Generic Linux kernel image.
 This package will always depend on the latest generic Linux kernel image
 and headers.

You will stay at the older kernel and there are potential security issues with that but you will have a working system (assuming you get no lockups).

I would consider this a last resort option though and it does, of course, depend on whether you get lockups in the old kernel.

Try the other advice given in this thread first.

Kind regards

---

### Post by MickeyPilgrim on 2013-03-29
The change to Nvidia drivers seems to have resolved the problem.

I do knot know how to mark this thread solved.

---


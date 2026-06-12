---
title: "s video intel chipset issue"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by csabanyi-laszlo on 2014-03-06
I checked many forums I wrote on irc support but no one could solve my problem.
 So, I'm using an old laptop with Xubuntu 12.04 LTS it works great but  the kernel doesn't support old video cards (intel chipset) so I can't  connect my device with hdtv via S-video cable.
 I found out Xubuntu 10.04 kernel supports my card.
 I downloaded many times and I tried to create a bootable usb but I  couldn't install it. I didn't have this problem with higher versions.
 
 Could please anyone find solution for my problem or give me a link to  download 10.04 which is working and able to put it on usb?

---

### Post by phidia on 2014-03-06
Try [this]("http://old-releases.ubuntu.com/releases/xubuntu/releases/10.04/release/") and good luck.

---

### Post by nunecas123 on 2014-03-06
First of all, click [here]("http://old-releases.ubuntu.com/releases/xubuntu/releases/10.04/release/xubuntu-10.04-desktop-i386.iso") to download the ISO for Xubuntu 10.04.
Have you ever tried the dd command? Why can't you install Xubuntu?

By the way, here's the code for dd(careful with this command, I recommend you backing up everything from the USB you're using - this command is rather unstable and destructive):
```
sudo dd if=path/of/iso of=/dev/sdx
```

X is the right letter for your drive(PLEASE, do not write the number after the letter). Check it by typing on the terminal:
```
fdisk -l
```

---

### Post by csabanyi-laszlo on 2014-03-06
nunecas123

I downloaded that iso and I typed in to the terminal the dd command but I've got this message:
dd: opening `path/of/iso': No such file or directory

---

### Post by csabanyi-laszlo on 2014-03-06
phidia,

I made up my usb with netbootin and I tried to install but after the xubuntu install screen where I choosed to install started the xubuntu screen, dissapeared and nothing happened :(

---

### Post by mörgæs on 2014-03-07
> **csabanyi-laszlo said:**
> the kernel doesn't support old video cards (intel chipset)

Sounds strange. Intel should have good Linux support.

Please run (using any Buntu release)
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

---

### Post by protoss96 on 2014-03-07
Hi,

Why you just don't keep Xubuntu 12.04 and just downgrade kernel? its easy with Ubuntu:
```
http://kernel.ubuntu.com/~kernel-ppa/mainline/
```

Go there and download the kernel you need, install .deb file and then run in terminal:
```
sudo update-grub
```

Restart PC and everything should work.

---

### Post by csabanyi-laszlo on 2014-03-07
> **mörgæs said:**
> Sounds strange. Intel should have good Linux support.

Please run (using any Buntu release)
```
sudo lshw -sanitize > lshw.txt
```
and post lshw.txt in CODE tags.

I did type this code and I've got this: PCI (sysfs)

---

### Post by csabanyi-laszlo on 2014-03-07
> **protoss96 said:**
> Hi,

Why you just don't keep Xubuntu 12.04 and just downgrade kernel? its easy with Ubuntu:
```
http://kernel.ubuntu.com/~kernel-ppa/mainline/
```

Go there and download the kernel you need, install .deb file and then run in terminal:
```
sudo update-grub
```

Restart PC and everything should work.

dear protoss96,

when I try to install the software center doesn't let me to install the image, only the headers.
which one is the proper kernel for xubuntu 10.04?

---

### Post by nunecas123 on 2014-03-07
> **csabanyi-laszlo said:**
> nunecas123

I downloaded that iso and I typed in to the terminal the dd command but I've got this message:
dd: opening `path/of/iso': No such file or directory

You didn't specify the ISO directory. For example, if my ISO is named "Something.iso" and it is at the Home directory, I should write this down:
```
dd if=/home/Something.iso of=/dev/sdX
```

X is the drive letter, don't forget that.

See what you can do there.

---

### Post by csabanyi-laszlo on 2014-03-07
> **nunecas123 said:**
> You didn't specify the ISO directory. For example, if my ISO is named "Something.iso" and it is at the Home directory, I should write this down:
```
dd if=/home/Something.iso of=/dev/sdX
```

X is the drive letter, don't forget that.

See what you can do there.

Dear nunecas123,

I have done finally the dd command, it made up my usb but when I restart my device and choose from the boot menu to boot from usb tham I get the message: missing operating system, then restarts the old xubuntu 12.04

---

### Post by csabanyi-laszlo on 2014-03-07
I tried now to install xubuntu 10.04 from cd but I couldn't go further just until the xubuntu screen after I choosed to install than became black again.

---

### Post by csabanyi-laszlo on 2014-03-07
> **protoss96 said:**
> Hi,

Why you just don't keep Xubuntu 12.04 and just downgrade kernel? its easy with Ubuntu:
```
http://kernel.ubuntu.com/~kernel-ppa/mainline/
```

Go there and download the kernel you need, install .deb file and then run in terminal:
```
sudo update-grub
```

Restart PC and everything should work.

I changed my system to lubuntu 12.04 which is allowed me to install 2.6.32-020632-generic as far as I know this is the kernel for 10.04 which should support my intel chipset but I can't change it from 3.2.0-23-generic to 2.6.32-020632-generic.

---

### Post by mörgæs on 2014-03-07
Quoting myself:

> **mörgæs said:**
> 
and post lshw.txt in CODE tags.

---

### Post by csabanyi-laszlo on 2014-03-08
> **mörgæs said:**
> Quoting myself:  Dear morgaes,  I think you asked for this: macila-latitude-d505           description: Portable Computer     product: Latitude D505     vendor: Dell Inc.     serial: D36Q81J     width: 32 bits     capabilities: smbios-2.3 dmi-2.3     configuration: boot=normal chassis=portable uuid=44454C4C-3300-1036-8051-C4C04F38314A   *-core        description: Motherboard        product: 0H2049        vendor: Dell Inc.        physical id: 0        serial: .D36Q81J.CN4864348P4162.      *-firmware           description: BIOS           vendor: Dell Inc.           physical id: 0           version: A06 (06/28/2004)           size: 64KiB           capacity: 448KiB           capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot      *-cpu           description: CPU           product: Intel(R) Pentium(R) M processor 1.50GHz           vendor: Intel Corp.           physical id: 400           bus info: cpu@0           version: 6.13.6           slot: Microprocessor           size: 600MHz           capacity: 1800MHz           width: 32 bits           clock: 133MHz           capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq         *-cache:0              description: L1 cache              physical id: 700              size: 8KiB              capacity: 8KiB              capabilities: internal write-back data         *-cache:1              description: L2 cache              physical id: 701              size: 2MiB              capacity: 2MiB              clock: 66MHz (15.0ns)              capabilities: pipeline-burst internal varies unified      *-memory           description: System Memory           physical id: 1000           slot: System board or motherboard           size: 1GiB           capacity: 2GiB         *-bank:0              description: DIMM DDR Synchronous 333 MHz (3.0 ns)              physical id: 0              slot: DIMM_A              size: 512MiB              width: 64 bits              clock: 333MHz (3.0ns)         *-bank:1              description: DIMM DDR Synchronous 333 MHz (3.0 ns)              physical id: 1              slot: DIMM_B              size: 512MiB              width: 64 bits              clock: 333MHz (3.0ns)      *-pci           description: Host bridge           product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller           vendor: Intel Corporation           physical id: 100           bus info: pci@0000:00:00.0           version: 02           width: 32 bits           clock: 33MHz           configuration: driver=agpgart-intel           resources: irq:0         *-generic:0 UNCLAIMED              description: System peripheral              product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller              vendor: Intel Corporation              physical id: 0.1              bus info: pci@0000:00:00.1              version: 02              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: latency=0         *-generic:1 UNCLAIMED              description: System peripheral              product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller              vendor: Intel Corporation              physical id: 0.3              bus info: pci@0000:00:00.3              version: 02              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: latency=0         *-display:0              description: VGA compatible controller              product: 82852/855GM Integrated Graphics Device              vendor: Intel Corporation              physical id: 2              bus info: pci@0000:00:02.0              version: 02              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list rom              configuration: driver=i915 latency=0              resources: irq:11 memory:f0000000-f7ffffff memory:faf80000-faffffff ioport:c000(size=8)         *-display:1 UNCLAIMED              description: Display controller              product: 82852/855GM Integrated Graphics Device              vendor: Intel Corporation              physical id: 2.1              bus info: pci@0000:00:02.1              version: 02              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list              configuration: latency=0              resources: memory:e8000000-efffffff memory:faf00000-faf7ffff         *-usb:0              description: USB Controller              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1              vendor: Intel Corporation              physical id: 1d              bus info: pci@0000:00:1d.0              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0              resources: irq:11 ioport:bf80(size=32)         *-usb:1              description: USB Controller              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2              vendor: Intel Corporation              physical id: 1d.1              bus info: pci@0000:00:1d.1              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0              resources: irq:11 ioport:bf40(size=32)         *-usb:2              description: USB Controller              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3              vendor: Intel Corporation              physical id: 1d.2              bus info: pci@0000:00:1d.2              version: 01              width: 32 bits              clock: 33MHz              capabilities: bus_master              configuration: driver=uhci_hcd latency=0              resources: irq:11 ioport:bf20(size=32)         *-usb:3              description: USB Controller              product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller              vendor: Intel Corporation              physical id: 1d.7              bus info: pci@0000:00:1d.7              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm debug bus_master cap_list              configuration: driver=ehci_hcd latency=0              resources: irq:11 memory:faeffc00-faefffff         *-pci              description: PCI bridge              product: 82801 Mobile PCI Bridge              vendor: Intel Corporation              physical id: 1e              bus info: pci@0000:00:1e.0              version: 81              width: 32 bits              clock: 33MHz              capabilities: pci bus_master              resources: ioport:e000(size=4096) memory:fc000000-fdffffff memory:40000000-43ffffff            *-pcmcia                 description: CardBus bridge                 product: PCI4510 PC card Cardbus Controller                 vendor: Texas Instruments                 physical id: 1                 bus info: pci@0000:01:01.0                 version: 02                 width: 32 bits                 clock: 33MHz                 capabilities: pcmcia bus_master cap_list                 configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192                 resources: irq:11 memory:fc000000-fc000fff ioport:e000(size=256) ioport:e400(size=256) memory:40000000-43ffffff memory:48000000-4bffffff            *-firewire                 description: FireWire (IEEE 1394)                 product: PCI4510 IEEE-1394 Controller                 vendor: Texas Instruments                 physical id: 1.1                 bus info: pci@0000:01:01.1                 version: 00                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list                 configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2                 resources: irq:11 memory:fcfff800-fcffffff memory:fcff8000-fcffbfff            *-network                 description: Ethernet interface                 product: 82801DB PRO/100 VE (MOB) Ethernet Controller                 vendor: Intel Corporation                 physical id: 8                 bus info: pci@0000:01:08.0                 logical name: eth0                 version: 81                 serial: 00:0f:1f:c1:c1:f1                 size: 100MB/s                 capacity: 100MB/s                 width: 32 bits                 clock: 33MHz                 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                 configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.67 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s                 resources: irq:11 memory:fcffe000-fcffefff ioport:ecc0(size=64)         *-isa              description: ISA bridge              product: 82801DBM (ICH4-M) LPC Interface Bridge              vendor: Intel Corporation              physical id: 1f              bus info: pci@0000:00:1f.0              version: 01              width: 32 bits              clock: 33MHz              capabilities: isa bus_master              configuration: latency=0         *-ide              description: IDE interface              product: 82801DBM (ICH4-M) IDE Controller              vendor: Intel Corporation              physical id: 1f.1              bus info: pci@0000:00:1f.1              logical name: scsi0              logical name: scsi1              version: 01              width: 32 bits              clock: 33MHz              capabilities: ide bus_master emulated              configuration: driver=ata_piix latency=0              resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:44000000-440003ff            *-disk                 description: ATA Disk                 product: ST9402112A                 vendor: Seagate                 physical id: 0                 bus info: scsi@0:0.0.0                 logical name: /dev/sda                 version: 3.06                 serial: 3PJ0VR6P                 size: 37GiB (40GB)                 capabilities: partitioned partitioned:dos                 configuration: ansiversion=5 signature=000061d9               *-volume:0                    description: EXT4 volume                    vendor: Linux                    physical id: 1                    bus info: scsi@0:0.0.0,1                    logical name: /dev/sda1                    logical name: /                    version: 1.0                    serial: 4ac539ad-fedb-4c52-a890-1a4e41f23a76                    size: 35GiB                    capacity: 35GiB                    capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized                    configuration: created=2014-03-08 15:34:02 filesystem=ext4 lastmountpoint=/W&#65533;&#65533;k&#65533;~&#65533;X&#65533;&#65533;&#65533;`&#1931;&#65533;&#65533; &#65533;X&#65533;&#65533;&#65533;&#65533;&#289;&#65533;`&#65533;\&#1931;&#65533;Y&#65533;!&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#1931;&#65533;&#65533; modified=2014-03-08 15:37:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2014-03-08 16:42:15 state=mounted               *-volume:1                    description: Extended partition                    physical id: 2                    bus info: scsi@0:0.0.0,2                    logical name: /dev/sda2                    size: 1610MiB                    capacity: 1610MiB                    capabilities: primary extended partitioned partitioned:extended                  *-logicalvolume                       description: Linux swap / Solaris partition                       physical id: 5                       logical name: /dev/sda5                       capacity: 1610MiB                       capabilities: nofs            *-cdrom                 description: DVD reader                 product: RW/DVD GCC-4243N                 vendor: HL-DT-ST                 physical id: 1                 bus info: scsi@1:0.0.0                 logical name: /dev/cdrom                 logical name: /dev/cdrw                 logical name: /dev/dvd                 logical name: /dev/scd0                 logical name: /dev/sr0                 version: A102                 capabilities: removable audio cd-r cd-rw dvd                 configuration: ansiversion=5 status=nodisc         *-multimedia              description: Multimedia audio controller              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller              vendor: Intel Corporation              physical id: 1f.5              bus info: pci@0000:00:1f.5              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm bus_master cap_list              configuration: driver=Intel ICH latency=0              resources: irq:5 ioport:d800(size=256) ioport:dc40(size=64) memory:faeff800-faeff9ff memory:faeff400-faeff4ff         *-communication UNCLAIMED              description: Modem              product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller              vendor: Intel Corporation              physical id: 1f.6              bus info: pci@0000:00:1f.6              version: 01              width: 32 bits              clock: 33MHz              capabilities: pm cap_list              configuration: latency=0              resources: ioport:d400(size=256) ioport:d080(size=128)      *-scsi           physical id: 1           bus info: usb@1:3           logical name: scsi3           capabilities: emulated         *-disk              description: SCSI Disk              physical id: 0.0.0              bus info: scsi@3:0.0.0              logical name: /dev/sdb              size: 298GiB (320GB)

---

### Post by sammiev on 2014-03-08
Use the code tag and insert your output from that command you used. The code tag above shows a # symbol above.

---


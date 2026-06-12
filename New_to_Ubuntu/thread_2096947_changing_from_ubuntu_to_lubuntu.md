---
title: "changing from ubuntu to lubuntu"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by zirgut on 2012-12-21
I have been advised to switch to a lighter system because my computer is now crashing quite regularly. I am currnetly operating ubuntu 12.04 LTS. 
How do I switch? I tried doing a torrent download and got confused about the process as it did not write onto a CD. 
I have read just now that I can enter into the terminal
sudo apt-get install lubuntu-desktop
If I do this will it carry over existing data I have on the ubuntu system.
Sorry but I do require very simplified instructions as still total novice and just computorially mind-blocked

---

### Post by snowpine on 2012-12-21
> **zirgut said:**
> I have readjust now that I can enter into the terminal
sudo apt-get install lubuntu-desktopIf I do this will it carry over existing data I have on the ubuntu system.

This is correct. (You can also install lubuntu-desktop with a click in the Software Center if you don't like the Terminal.)


If you want to go one step further and **remove** all traces of Unity/Ubuntu, read here: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

---

### Post by AlexDudko on 2012-12-21
1. Execute command:
> sudo apt-get update && sudo apt-get install lubuntu-desktop
2. Log out.
3. Under Session, select lxde.
4. Log back in again.

After that you'll have both Gnome and LXDE installed and will be able to choose between them. But mind that Lubuntu-12.04 isn't an LTS version so it won't be supported for 5 years like Ubuntu, only 18 months.

---

### Post by kansasnoob on 2012-12-21
> **snowpine said:**
> This is correct. (You can also install lubuntu-desktop with a click in the Software Center if you don't like the Terminal.)


If you want to go one step further and **remove** all traces of Unity/Ubuntu, read here: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

You're almost right but the OP said, "I am currnetly operating ubuntu 12.04 LTS", so your link should direct to:

[http://www.psychocats.net/ubuntu/purelubuntuprecise](http://www.psychocats.net/ubuntu/purelubuntuprecise)

And it may be useful to say you'll need to log out and then log in to the new desktop environment.

---

### Post by zirgut on 2012-12-21
Thanks snowpine and AlexDudko. I have tried backing things up in Back up in system settings but for some reason is not working for me. Will I lose data if I make this move to lubuntu?

---

### Post by AlexDudko on 2012-12-21
This command shouldn't damage anything, you can safely execute it. What's the error when you run the command?

---

### Post by zirgut on 2012-12-21
On the back up the system backs up and then changes to uploading but nothing happens even when I leave it for quite a long period of time.

---

### Post by AlexDudko on 2012-12-21
> **zirgut said:**
> On the back up the system backs up and then changes to uploading but nothing happens even when I leave it for quite a long period of time.

What's the output of 
> sudo apt-get install lubuntu-desktop

---

### Post by Pjotr123 on 2012-12-21
It's easier and better, and maybe even quicker, to do a clean install of Lubuntu. With previous formatting of the Ubuntu partition:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

But before you install Lubuntu, check whether your hardware is capable of running Xubuntu, which is more complete and better looking than Lubuntu:
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

If your computer can handle it, Xubuntu is the preferred choice. :)

---

### Post by kansasnoob on 2012-12-21
> **Pjotr123 said:**
> It's easier and better, and maybe even quicker, to do a clean install of Lubuntu. With previous formatting of the Ubuntu partition:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

But before you install Lubuntu, check whether your hardware is capable of running Xubuntu, which is more complete and better looking than Lubuntu:
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

If your computer can handle it, Xubuntu is the preferred choice. :)

Xubuntu being "preferred" is clearly a personal choice ;)

---

### Post by Pjotr123 on 2012-12-21
> **kansasnoob said:**
> Xubuntu being "preferred" is clearly a personal choice ;)

My statement might indeed have benefited by the addition "in my opinion". :)

---

### Post by audiomick on 2012-12-21
> **zirgut said:**
>  Will I lose data if I make this move to lubuntu?

The suggestions up to this point, i.e. adding the Lubuntu desktop to the existing install, will not remove anything and will not cause you to lose any data. 

I think perhaps a word of explanation might help. The advice you
recieved that caused you to post here is that your computer can't deal well with the resource requirements of the current Ubuntu desktop, and would run better on a version which does not need as much in the way of resources. Hence the suggestion to use Lubuntu.

If you add the Lubuntu desktop and boot into it as suggested in the thread, you are effectively using Lubuntu. You have added some modules, are running them, and the ones from the Ubuntu Unity environment that are suspected of using too many resources are largely not running. All they are doing is taking up a little bit of space on the drive. You can happily leave them there if your are not really short of space on the drive.

I would suggest trying this out, i.e install the lubuntu desktop and try running from that for a bit. I am not convinced that your crashes are a simple case of too little resources, but running from the Lubuntu desktop for a bit should show if that is really the case or not.

Just for interests sake, do
```
sudo lshw
```
and post the output here so we can see the specifications of your machine. It might be interesting to see what other people think about whether it should be having trouble with a standard Ubuntu or not.

---

### Post by vasa1 on 2012-12-21
> **Pjotr123 said:**
> ...
But before you install Lubuntu, check whether your hardware is capable of running Xubuntu, which is more complete and better looking than Lubuntu:
...

Yes, this thread is specifically about "changing from ubuntu to lubuntu". If we go down the road of recommending other flavors or distros things will get chaotic pretty soon :)

To OP:
BTW, Lubuntu has **its own** documentation and an [**its own** mailing list]("https://lists.ubuntu.com/mailman/listinfo/lubuntu-users") which may, IMO, be safer than taking advice from third-party sites.
[http://lubuntu.net/](http://lubuntu.net/) is a good starting point.

---

### Post by zirgut on 2012-12-22
Thanks everyone for the advice. I downloaded Lubuntu following the advice to use this code
(sudo apt-get update && sudo apt-get install lubuntu-desktop 			 		). Sorry I've forgotten how you get it in the box.
Please tell me if what I am getting is right?
When I start up from the grub menu the Lubuntu logo comes up but then when I reach the log-in screen I am back to Ubuntu 12.04LTS.
But so far the computer has not crashed although I have not used in very much since installation.
Audiomick, I will post that output soon from the code you gave me.
Again thanks for the support.
Adrian

---

### Post by GameX2 on 2012-12-22
> **AlexDudko said:**
> But mind that Lubuntu-12.04 isn't an LTS version so it won't be supported for 5 years like Ubuntu, only 18 months.

Thanks for the info - didn't knew that.

---

### Post by zirgut on 2012-12-22
Here is the output from 
[sudo lshw]
```
adrian-dell-dm051         
    description: Mini Tower Computer
    product: Dell DM051
    vendor: Winbond Electronics
    serial: 1F2V62J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=hardware-failure-fw chassis=mini-tower cpus=2 power-on_password=enabled uuid=44454C4C-4600-1032-8056-B1C04F36324A
  *-core
       description: Motherboard
       product: 0HJ054
       vendor: Winbond Electronics
       physical id: 0
       serial: ..CN6986163119F1.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 03/31/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          slot: Microprocessor
          size: 2800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl cid cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 16KiB
             capacity: 16KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MiB
             capacity: 2MiB
             capabilities: internal varies unified
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
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: M3 78T6553CZ3-CD5
             vendor: Samsung
             physical id: 0
             serial: F4230908
             slot: DIMM_1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: FFFFFFFF
             slot: DIMM_3
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             product: M3 78T6553CZ3-CD5
             vendor: Samsung
             physical id: 2
             serial: F4230909
             slot: DIMM_2
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM DDR Synchronous 533 MHz (1.9 ns) [empty]
             vendor: FFFFFFFFFFFFFFFF
             physical id: 3
             serial: FFFFFFFF
             slot: DIMM_4
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.4.7
          serial: 0000-0F47-0000-0000-0000-0000
          size: 2800MHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:ec000000-efefffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8400 GS]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:ec000000-edffffff ioport:dc80(size=128) memory:efe00000-efe1ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:efffc000-efffffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:ebf00000-ebffffff ioport:40100000(size=2097152)
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
             resources: irq:21 ioport:ff80(size=32)
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
             resources: irq:22 ioport:ff60(size=32)
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
             resources: irq:18 ioport:ff40(size=32)
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
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:ebe00000-ebefffff
           *-multimedia
                description: Multimedia audio controller
                product: CA0106 Soundblaster
                vendor: Creative Labs
                physical id: 2
                bus info: pci@0000:03:02.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_ca0106 latency=64 maxlatency=20 mingnt=2
                resources: irq:18 ioport:cca0(size=32)
           *-network
                description: Ethernet interface
                product: N10/ICH 7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 01
                serial: 00:13:72:c3:91:3d
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.64 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
                resources: irq:20 memory:ebeff000-ebefffff ioport:ccc0(size=64)
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD writer
                product: DVD-RW  DVR-112D
                vendor: PIONEER
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/sr0
                version: 1.21
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
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
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:40000000-400003ff
           *-disk
                description: ATA Disk
                product: WDC WD1600JS-75N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WCANM3550420
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e686f016
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 0a4446de-b73a-7942-a52c-8ae42ce4dc98
                   size: 88GiB
                   capacity: 88GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-01-08 13:30:49 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 60GiB
                   capacity: 60GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1020MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 59GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
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
             resources: ioport:ece0(size=32)
adrian@adrian-Dell-DM051:~$
```

---

### Post by audiomick on 2012-12-22
Well, as far as I can see, it is an oldish processor, a single core at 2.8Ghz. I don't really know how that should deal with a Unity desktop. I think it should, but it might be a little slow. There are 2GB of RAM in there, which is a good thing.

I see here
```
description: VGA compatible controller
product: G86 [GeForce 8400 GS]
vendor: NVIDIA Corporation
```

that there is an nVidia graphics card. Had you not originally posted that it was intel graphics? Anyway, you should have a look at using the "additional drivers" application to get the nVidia drivers for that, if you haven't already.

In short, I think that is an older processor, and therefore I think that Lubuntu is probably not a bad idea. I'll be interested to see what other people have to say.

By the way, when you have a long output like that, it is a good idea to use the # button at the top of the posting window to put code tags around it. Then it appears in a window of it's own as did the text that I quoted in the "code" window above. If it is a lot of text, the window gets scroll bars. The other advantage is that the text is posted exactly as it is, without special characters being rendedered as smileys or whatever ever, like this: one of these : and then this D looks like this :D

---

### Post by AlexDudko on 2012-12-23
> **zirgut said:**
> Thanks everyone for the advice. I downloaded Lubuntu following the advice to use this code
(sudo apt-get update && sudo apt-get install lubuntu-desktop 			 		). Sorry I've forgotten how you get it in the box.
Please tell me if what I am getting is right?
When I start up from the grub menu the Lubuntu logo comes up but then when I reach the log-in screen I am back to Ubuntu 12.04LTS.
But so far the computer has not crashed although I have not used in very much since installation.
Audiomick, I will post that output soon from the code you gave me.
Again thanks for the support.
Adrian

Being in login screen click on the circle with a footprint icon in it (if your previous session was gnome) next to your username or the last used if there are several of them. In the dropdown menu choose lxde.
By the way, do you have a swap partition? Your crashes could be caused by the lack of physical memory.

---

### Post by Filip II on 2012-12-23
> **Pjotr123 said:**
> It's easier and better, and maybe even quicker, to do a clean install of Lubuntu. With previous formatting of the Ubuntu partition:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

But before you install Lubuntu, check whether your hardware is capable of running Xubuntu, which is more complete and better looking than Lubuntu:
[https://sites.google.com/site/easylinuxtipsproject/xubuntu](https://sites.google.com/site/easylinuxtipsproject/xubuntu)

If your computer can handle it, Xubuntu is the preferred choice. :)

Thanks for the Xubuntu idea, I was thinking of trying a more stripped down distro. I will definetly give it a try!

---

### Post by 3rdalbum on 2012-12-23
Bit concerned about the advice you have been given. A 2.8GHz CPU with a gig of RAM and an Nvidia 8400 is more than enough grunt to run normal Ubuntu. Plenty of power for that.

If you are having low performance then ensure you have activated the Nvidia driver from the Software Properties program.

If you are having crashes then you should test each of your RAM sticks for problems.

---

### Post by zirgut on 2012-12-23
#
[
If you are having crashes then you should test each of your RAM sticks for problems.[/QUOTE]#

Hi could you tell me how I carry out those tests?
Thanks.
And thanks for all the other replies.

---

### Post by zirgut on 2012-12-23
Under additional drivers there are 5 different Nvidia drivers listed. How do I decide which one to activate? When the sound disappeared I activated the one that was recommended but that is also when some of the crashing problems started. So now I have just gone back and activated the first one on the list which is the Nvidia accelerated graphics driver (version 173). Any comments?
Thanks

---

### Post by mysteriousdarren on 2013-01-11
I would do use google as a resource. Usually install the latest driver is what works the best. What are your choices?

---

### Post by zirgut on 2013-01-12
Hi mysteriousdarren,
The options which are offered are:
1.Nvidia accelerated graphics driver (version173-updates)
2. Nvidia accelerated graphics driver (post release updates)(version 173-updates)
3.Nvidia accelerated graphics driver (version current)[recommended]
4.Nvidia accelerated graphics driver (post release updates) (version current-updates)
5.Nvidia accelerated graphics driver (**experimental**beta)(version experimental-304)
I am currently using option 2. When I used No. 3 that is when I experienced computer crashing issues.
Look forward to hearing your opinion.
Thanks

---


---
title: "Error after grub and hard drive light on all the time after error slow"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by WinXpRefugee on 2014-04-24
&#65279;Hello,

K7VT3, Athlon XP 2200+, 1026MB, GeForce2 MX200] (rev b2) dual boot with win XP Pro
ATA ST3120026A
Ubuntu 14.04 LTS

I recently installed lubuntu 13.10 on this machine and am having some issues 
(it updated to 14.04 but I am still having the same problems)

Problem 1. I get this error after the GRUB screen

 25.2536386 via-ircc 000:00:11.0: (can't reserve IO 0<4000-0x407f)

Problem 2 (or symptom of problem 1?) 
After the machine gets to the desktop the Hard drive indicator light is on all the time.

Problem 3 I am running Lubuntu on a lower spec machine and it seems to run a lot faster.

Is it something to do with the VIA chip set. 
Is it because I installed the wrong version of Lubuntu I think I have installed the Intel x86 version???

Thank you in advance for any assistance.

---

### Post by WinXpRefugee on 2014-04-25
Still having this problem could it be chip set?

---

### Post by mörgæs on 2014-04-25
This is very old hardware and you have to accept a low performance if you want to carry on with it.

The Lubuntu version you used is correct. What matters is that you have a 32 bit processor, not whether it's Intel or AMD.

Some people report that the old (around 2000) Nvidia cards are buggy in 14.04. Might be a better option to install something 12.04-based like Bodhi Linux or LXLE.

---

### Post by WinXpRefugee on 2014-04-25
mörgæs,

Thanks for your reply I can accept the "slowness" it does not make the  computer unusable I am just curious if it is related to the ERROR. 


My Inner geek wants to know what the error is and how fix it. Why the hard drive light is on all the time?
I would really like to know what the error is  (IO  sounds like IDE bus issue.   I was thinking via-ircc?  it is a VIA chip  set)
 [COLOR=#ff0000](VIA[SUP]®[/SUP] Apollo KT333 North Bridge VT8367 / VIA[SUP]®[/SUP] VT8235 South Bridge)[/COLOR]
 
I keep wanting to use Ubuntu flavors( Lubuntu, Xbuntu) but can't seem to get any of them to work very well.
 I usually end up going with [Linux lite OS 1.0.6] it seems to preform a  lot better with less problems than any other distro I have tried.
 I can't understand why, since it is based off of Ubuntu.

---

### Post by mörgæs on 2014-04-25
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by WinXpRefugee on 2014-04-25
[ 						 							]("http://ubuntuforums.org/member.php?u=939075")[**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"),
Thank you for your response 
I will have to try this on Monday I am AFK this weekend. I will post ASAP.

---

### Post by WinXpRefugee on 2014-04-30
[FONT=arial][SIZE=2]mörgæs,

Thanks for your reply[/SIZE][/FONT]

```

computer
    description: Desktop Computer
    product: VT8367-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: VT8367-8235
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG
          date: 09/22/2003
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot virtualmachine
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: Socket A
          size: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 1GiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
     *-pci
          description: Host bridge
          product: VT8366/A/7 [Apollo KT266/A/333]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via
          resources: irq:0 memory:d0000000-d7ffffff
        *-pci
             description: PCI bridge
             product: VT8366/A/7 [Apollo KT266/A/333 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:e0000000-e1ffffff memory:d8000000-dfffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV11 [GeForce2 MX200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
                resources: memory:e0000000-e0ffffff memory:d8000000-dfffffff memory:e1000000-e100ffff
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:11 ioport:d000(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:3 ioport:d400(size=32)
        *-usb:2
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32
             resources: irq:10 ioport:d800(size=32)
        *-usb:3
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32
             resources: irq:5 memory:e2000000-e20000ff
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=32
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:dc00(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx latency=0
             resources: irq:10 ioport:e000(size=256)
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=snd_via82xx_modem latency=0
             resources: irq:10 ioport:e400(size=256)
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 74
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.1 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 ioport:e800(size=256) memory:e2001000-e20010ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3120026A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.06
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0051f2c6
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 37GiB
                capacity: 37GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2007-01-21 05:11:11 filesystem=ntfs label=120GBHD modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 73GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 1022MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: CD-R/CD-RW writer
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw
             configuration: status=nodisc

```

---

### Post by mörgæs on 2014-04-30
It's very old stuff and in addition to what I mentioned above you will be facing problems with Flash. 


I can't explain the always-on hard disk light.


Your problem 1 could, assuming that 0<4000 in original post should be 0x4000, be due to a bad memory block.

---

### Post by WinXpRefugee on 2014-04-30
[FONT=arial][SIZE=2]mörgæs,

Thanks for your reply[/SIZE][/FONT]

from the dmesg command

[   25.539051] via-ircc 0000:00:11.0: device not available (can't reserve [io  0x4000-0x407f])

if that helps any
Maybe I should do the linux lite it seems to behave better on the old hard ware that I am encountering although I am using Lubuntu on the machine right now as I am typing this???

---

### Post by mörgæs on 2014-04-30
Distrohopping is always a good thing if you stick to supported distros. 
Here's some inspiration: [http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027) 

Another option is to see what old hardware you are able to get for $50 or for free. 

The Flash problem is going to persist but you can install a semi-good old version. More information in the link in my signature.

---

### Post by WinXpRefugee on 2014-05-05
Thanks [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"),
Lubuntu is working, just thought I could tweak it to make it perform perfectly.

---

### Post by WinXpRefugee on 2014-05-09
Ok if i was old you would call this a senior moment since I am not it is just a stupid mistake. The cause of ALL my problems was a loose IDE connection on the back of one of the CD Rom Dives JEEESH! Lubuntu 14.04 works fine on this machine!!! I think I am going to try mint MATE just because I think it is prettyerer.

---

### Post by LastDino on 2014-05-09
> **WinXpRefugee said:**
> Ok if i was old you would call this a senior moment since I am not it is just a stupid mistake. The cause of ALL my problems was a loose IDE connection on the back of one of the CD Rom Dives JEEESH! Lubuntu 14.04 works fine on this machine!!! I think I am going to try mint MATE just because I think it is prettyerer.

Or try to customize Lubuntu and since you're prepared to re-install, why not experiment as much as you could? :P

---

### Post by WinXpRefugee on 2014-05-09
Last Dino,
Thank you for your post

I really want to use ubuntu flavors since the support forum is so much better.
 I really like the Menu system in mint I like being able to un-install with the right click I like that it has a windows 7 style search bar I like the Weather app that is in the dock
I like that it imports Xp files and account information during the install process 
I don't like unity at all reminds me of win 8 which I also don't like.
 
I have used a lot of Ubuntu Remix "Linux lite OS 1.0.6" (not 1.0.8)  just because it seems to work out of the box. I don't really need a support forum if everything works. I have installed it on 6 machines now it is not real pretty like mint and lacks some of the features but it is really fast.

So how can I tweak Lubuntu to to do the things mint does
(The windows looking menu system in mint, un-install with the right click, windows 7 style search bar integrated into the menu,  Weather app in the dock)
I will gladly play with it.  I kind of understand that some of the things "I like" are just packages that are included in the mint distro not nessisarily Mint only like MATE is not mint only or am I mistaken (yet again)
Thanks

---

### Post by LastDino on 2014-05-09
Well, you can start by installing synaptic. Then google things like Tweak Lubuntu, Conky for Lubuntu etc. Try your hand there and then if you get bored go with something different. No point in simply installing and uninstalling if you're not going to have fun with it.

---


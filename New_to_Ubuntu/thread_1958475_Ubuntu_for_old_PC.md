---
title: "Ubuntu for old PC"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by dawnboat on 2012-04-14
hello, I am brand new to Ubuntu.  I found a desktop cpu on the street corner in a box with free written on it.  Yesterday I turned it on and discovered it had Ubuntu.  I have never used anything of the linux variety, or anything outside of windows and mac for that matter, and I have no idea what I am doing when it comes to the terminal.  Yesterday I updated to version 10.04 from 8.04, but now it's way too slow.  I have a wireless adapter i need to get installed on here that's been driving me nuts. My dvd drive won't play dvd movies, I am now having trouble installing anything from the software center.  PLEASE HELP ME GET THIS THING WORKING GOOD!!!!!!

---

### Post by mörgæs on 2012-04-14
Hi, welcome to the fora.

Rather than using something you found I recommend that you erase the hard drive with [www.killdisk.com](www.killdisk.com) and do a clean install of X/Lubuntu 11.10.

(And please use a more descriptive thread title next time).

---

### Post by kio_http on 2012-04-14
> **dawnboat said:**
> hello, I am brand new to Ubuntu.  I found a desktop cpu on the street corner in a box with free written on it.  Yesterday I turned it on and discovered it had Ubuntu.  I have never used anything of the linux variety, or anything outside of windows and mac for that matter, and I have no idea what I am doing when it comes to the terminal.  Yesterday I updated to version 10.04 from 8.04, but now it's way too slow.  I have a wireless adapter i need to get installed on here that's been driving me nuts. My dvd drive won't play dvd movies, I am now having trouble installing anything from the software center.  PLEASE HELP ME GET THIS THING WORKING GOOD!!!!!!

Welcome. I would suggest you download the latest version 11.10. I would recommend trying Kubuntu and Ubuntu and seeing which one you prefer. Also note the on the 26th the next version 12.04 comes out so it might be better to wait until then. In my opinion the Ubuntu version has had too many recent changes in its software and is heavily tied to something called compiz (which is not a good idea).

You can try a livecd of all varriants that exist and see which you prefer. See the previous posters signature. If you happen to chose the Kubuntu route, see the link in my signature.

---

### Post by 3Miro on 2012-04-14
Well, it was probably left on the street for a reason. If the hardware is busted, no amount of software would help.

Go to the terminal (Apps -> Accessories -> Terminal) and use the command:
```
sudo lshw
```
this will give you a list of the entire hardware. Try to find out the details on the hardware like: CPU type and speed, amount of RAM, **type of video card** (very important), motherboard chipset, network card.

In general for DVD movies check here:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
(you need to run the two commands then DVDs should play, but you need internet)

Wireless cards are hit and miss, depending on the wifi that you have, it may not run under Linux. I would try using wired Internet.

---

### Post by dawnboat on 2012-04-14
the computer is kinda old, it came factory loaded with windows xp so someone put ubuntu on it.  I put 10.04 on it, but I think i need to go back down a couple versions, because it's running way slower now.  Is this possible?  I'm not even sure the disk drive is capable of burning cds, it says it is, but it also says it plays dvd's and it doesn't do that because it's probably been messed with a bit.  I guess I will try wiping the drive and putting 11.04 on it, but with 10 it's too slow to run the desktop graphics and stuff.

---

### Post by dawnboat on 2012-04-14
description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 181MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          size: 2950MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
     *-pci
          description: Host bridge
          product: 661FX/M661FX/M661MX Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d8000000-dfffffff
        *-pci
             description: PCI bridge
             product: SiS AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:e8000000-e80fffff memory:e0000000-e7ffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=0
                resources: memory:e0000000-e7ffffff(prefetchable) memory:e8000000-e801ffff ioport:d000(size=128)
        *-isa
             description: ISA bridge
             product: SiS964 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 36
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4000(size=16)
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:e000(size=256) ioport:e400(size=128)
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:20 memory:e8122000-e8122fff
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:21 memory:e8124000-e8124fff
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:22 memory:e8120000-e8120fff
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80
             resources: irq:23 memory:e8121000-e8121fff
        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant Systems, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=32
             resources: memory:e8100000-e810ffff ioport:e800(size=8)
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: eth0
             version: 10
             serial: 00:11:09:be:1c:5e
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom ethernet physical
             configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.44 latency=32 maxlatency=64 mingnt=32 multicast=yes
             resources: irq:18 ioport:ec00(size=256) memory:e8123000-e81230ff memory:c000000-c00ffff(prefetchable)
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage

---

### Post by yeats on 2012-04-14
> I put 10.04 on it, but I think i need to go back down a couple versions, because it's running way slower now. Is this possible?

10.04 is the oldest supported version.  If that's running slow, you definitely want to consider running [Xubuntu]("http://xubuntu.org/") or [Lubuntu]("http://lubuntu.net/").

---

### Post by mörgæs on 2012-04-14
Always install one of the recent versions. Don't pick an old (=abandoned) one in order to gain speed.

As mentioned above, X/Lubuntu is a better choice than K/Ubuntu, since the hardware is old.

Edit: You should also give the poor thing some more memory.

---

### Post by dawnboat on 2012-04-14
ok, thanks guys.  Like I said I have no idea what I'm doing, but I am eager to learn, because up till yesterday I didn't know a OS like this exsisted.  I am thrilled at the concept of learning to use this properly

---

### Post by mörgæs on 2012-04-14
Good. Now you have some inputs, so time for self-study and experimenting :-)

---

### Post by kio_http on 2012-04-14
> **mörgæs said:**
> Always install one of the recent versions. Don't pick an old (=abandoned) one in order to gain speed.

As mentioned above, X/Lubuntu is a better choice than K/Ubuntu, since the hardware is old.

Edit: You should also give the poor thing some more memory.

The old stereotype about Kubuntu doesn't apply anymore especially since KDE 4.8. I have succeeded in running it on slower pentium 3 systems with decent performance. 

Ubuntu with Unity/Compiz on the other hand is simply bloated. I'd recommend trying Kubuntu with kde 4.8 series and installing "kubuntu-low-fat-settings".

Edit: Just saw the memory. Lubuntu is what you should chose. If you add more memory however, you would be surprised how well this thing can still perform today. A 2.9Ghz P4 is still very capable even today. The previous owner probably salvaged some memory from this PC.

---

### Post by 3Miro on 2012-04-14
On memory that is so low, only Lubuntu would be a viable option. You should also pick a newer version like 11.10. You should have no trouble with the wired Internet, use a wire to get the updates and only then try to mess with the wifi.

---

### Post by dawnboat on 2012-04-14
yeah downloading current version of Lubuntu now, when it's done I'm going to throw it on a stick drive and wipe the drive as previously suggested.  then I am going to see if the dvd player is fixed and go from there...

---

### Post by lkraemer on 2012-04-14
Your Desktop really needs more memory...............

Until you get that done, you can always download some of the Distro's
that will run fine on the current Memory. 

REF:
[http://distrowatch.com](http://distrowatch.com) 

Good LiveCD choices are:
1. Debian 6 "SQUEEZE" (Gnome 2.x) (XFCE LXDE Installs from CD) Supports i486
Install as Minimum Install & select the 486 Kernel
2. TinyCore 4.x (XFCE)
3. Vector 7 (XFCE)
4. Slitaz
5. AntiX M11 IceWM Rox Default (Fluxbox, wmii and dwm also installed)
6. Arch Linux (XFCE) i686
7. Porteus 1.2 RC2 (XFCE)
8. Puppy

There's lots of options. Burn some of the LiveCD's on a CDRW and give them a test. (Arch is a Source Distrbution......Well worth a test! GREAT Wiki/Forum & Documentation)

Your Memory really needs to be 128 or 256 Meg. The best i486 choices are:
1. Antix M11
2. Tinycore
3. Arch Linux i686
4. Porteus
5. Salix OS
6. Semplice Linux
7. Slackware 13.37
8. Vector Linux 7
9. Zenwalk Linux
10. CRUX i686

So, start your search at distrowatch.com..........

lk

---

### Post by dawnboat on 2012-04-14
when doing killdisk do I use the PC and DOS version or the compact DOS version?

---

### Post by pinkpanther1569 on 2012-04-14
If you plan to wipe the drive you can also create a DBAN disk.  Just click the link below.  [http://www.dban.org/download](http://www.dban.org/download)  
 
HD could be fragmented.  I am new to Ubuntu as well, but not new to hardware
 
Reinstall newest version and up the RAM!

---

### Post by dawnboat on 2012-04-14
ok, so i tried running both dban and killdisc, both times I got an error message: DISK BOOT ERROR, PLEASE INSERT BOOT DISK AND PRESS ENTER.  for shits and giggles I tried running lubunta anyways and I got the same thing.  I was using a usb stick.  I had changed the bios settings to reflect that i was using a stick, so that shouldn't have been the problem...I don't know I'm stuck..

---

### Post by mörgæs on 2012-04-14
Have you tried booting from a CD? 

Does the USB stick boot in another computer?

There are more steps for troubleshooting in the link in my signature.

---

### Post by GregA on 2012-04-14
Will that old of a system recognize a USB Flash Stick as a boot device?  May need your Linux on CD-Rom.  

Re choice of linux distro, perhaps antiX with Fluxbox is lite enough (fluxbox considerably lighter than most other options.)

---

### Post by kurt18947 on 2012-04-14
> **mörgæs said:**
> Have you tried booting from a CD? 

Does the USB stick boot in another computer?

There are more steps for troubleshooting in the link in my signature.

That vintage PC may well not support booting from USB.  +1 on more RAM, IMO 512 is a minimum, 2 gig is a sweet spot.  I'm not sure what type RAM you'd need but here's a vendor I've used that seemed to have decent prices.  There may be other better vendors but I have no experience and the usual  sources such as newegg can be pretty expensive on obsolete RAM. 
  
[http://stores.ebay.com/xtremeRam/Desktop-Memory-/_i.html?_fsub=300548919&_sid=74462619&_trksid=p4634.c0.m322](http://stores.ebay.com/xtremeRam/Desktop-Memory-/_i.html?_fsub=300548919&_sid=74462619&_trksid=p4634.c0.m322)

 They offer 30 days money back.  I used memtestX86  found on at least some Ubuntu CDs.  Installed the RAM as soon as I got it, uninstalled existing and let memtest run for a few hours.  If you use what you have now, you could run memtest on that as well.  

I see your foundling has an Sis chipset.  SiS doesn't have the greatest rep for linux but it seems to be working so what the hey:p.

---

### Post by kurt18947 on 2012-04-14
> **mörgæs said:**
> Have you tried booting from a CD? 

Does the USB stick boot in another computer?

There are more steps for troubleshooting in the link in my signature.

That vintage PC may well not support booting from USB.  +1 on more RAM, IMO 512 is a minimum, 2 gig is a sweet spot IMO.  I'm not sure what type RAM you'd need but here's a vendor I've used that seemed to have decent prices.  There may be other better vendors but I have no experience and the usual  sources such as newegg can be pretty expensive on obsolete RAM. 
  
[http://stores.ebay.com/xtremeRam/Desktop-Memory-/_i.html?_fsub=300548919&_sid=74462619&_trksid=p4634.c0.m322](http://stores.ebay.com/xtremeRam/Desktop-Memory-/_i.html?_fsub=300548919&_sid=74462619&_trksid=p4634.c0.m322)

 They offer 30 days money back.  I used memtestX86  found on at least some Ubuntu CDs.  Installed the RAM as soon as I got it, uninstalled existing and let memtest run for a few hours.  If you use what you have now, you could run memtest on that as well.  

I see your foundling has an Sis chipset.  I think SiS doesn't have the greatest rep for Linux  but it seems to be working so what the hey:p.

---

### Post by decktrio on 2012-04-14
I use Lubuntu, and right now it's consuming 460MiB. ...*but* that's because I use it with some pretty heavy apps (some of which require compositing to look decent); for example, I use conky, cairo dock, firefox, thunderbird, and pidgin. I also use xcompmgr for conky and cairo dock.

That being said, from my experience [Lubuntu 11.10]("http://cdimages.ubuntu.com/lubuntu/releases/11.10/release/") with the default apps is fantastically light. Light & easy to use; best of both worlds. **That's what I recommend; Lubuntu with default apps.** At this point, just wait a little while longer until 12.04, right? Fresh installs are best.

---

### Post by dawnboat on 2012-04-14
well, I am going to give putting it on a cd a try.  I looked at my hard drive in disk utility it has one huge rectangle with 79Gb on it, and then two small blocks with 698mb each that sa they are extensions, someone mentioned my disk was possibly fragmented.  I appreciate all the help guys.  The sugestions are helpful.  I'm trying to limit my own posts to supplying info and only when I absolutely cannot figure out what to do next.  I am worried that my disc drive may not burn cds..You think it might be wise to just order a pack of boot disks from linux?

---

### Post by mörgæs on 2012-04-15
> **dawnboat said:**
> I looked at my hard drive in disk utility it has one huge rectangle with 79Gb on it, and then two small blocks with 698mb each that sa they are extensions, someone mentioned my disk was possibly fragmented.

You are looking at the partition scheme, not a measure of fragmentation. 

Besides, disk fragmentation is a Windows problem, (almost) never in Linux, and you are going to wipe the drive completely, so it does not matter if it was fragmented before.


> **dawnboat said:**
> I'm trying to limit my own posts to supplying info and only when I absolutely cannot figure out what to do next.

Good, that's how people learn.


> **dawnboat said:**
> You think it might be wise to just order a pack of boot disks from linux?

Yes, they are cheap to get, but you should focus on finding more memory first.

---

### Post by mörgæs on 2012-04-15
If you want to get something running using your present RAM, this might help:

[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

The computer will be too slow for practical use, but you'll get to see how Lubuntu works.

You still need to burn a CD, though. Don't you have some friends around who can help you with that?

---

### Post by dawnboat on 2012-04-17
Okie dokie, lots to update.  I figured out how to burn the iso images to discs, so I am running killdisk now, and after that I am going to reinstall lubuntu 11.10.  I had the normal iso and the mini iso, but it wouldn't get past the boot menu with the primary, and the mini didn't have a desktop, I'd just get stuck in the middle of booting.  DL'd the alternate iso and that was the ticket, got lubuntu 11.10 running, so I figured  I'd better go back and run killdisk now that i know which iso file to use for lubuntu.  SOOOOO much work, but so worth it.  Lubunu looks beautiful on this cpu, I can't wait for killdisk to be done running so I can reinstall it. my disk was cut into five partitions.

---

### Post by mörgæs on 2012-04-17
First time around is always slow, but now you know the cure if you get your hands on more old hardware. 

If your problem is solved, please mark the thread so using 'thread tools' (or post again, if you still have questions).

---


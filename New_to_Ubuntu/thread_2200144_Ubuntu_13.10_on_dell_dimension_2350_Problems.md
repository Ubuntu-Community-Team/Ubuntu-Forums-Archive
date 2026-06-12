---
title: "Ubuntu 13.10 on dell dimension 2350 Problems"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by WinXpRefugee on 2014-01-17
I have never installed any distribution of linux
With the impending farewell of xp I was looking for a cheap alternitive (like free) to the Microsoft upgrade path.  I have been doing computer service since the early 90's but only in the M$ relm so I am really comfortable tweaking Microsoft software. 
I Installed zorin and had graphical problems with it as well 
I just installed ubuntu 13.10 I saw no problems durring install 
The system post's and boots to the default desktop picture only!
I can change it with R-click
I created a folder and it is on the desktop.
I can open a term Ctrl-Alt-T
I went online and figured out how to launch firefox
this is what it said 
```

$ firefox
(process:3095): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed

```
but the window came up that is how I am posting
I did this 
```

gksu lshw-gtk
```

It said I did not have gksu  and how to install it so I did that.

I really don't know what I am doing but i am patient and can read English (lol)
I noticed when I closed the Term window that the program that I launched goes bye bye so I asume that is how linux works it is just hidden form the end user.
here is the data from gksu lshw-gtk
```

Desktop Computer
product: Dimension 2350
vendor: Dell Computer Corporation
version: A02
serial: 4HWC231
width: 32 bits
capabilities:
    SMBIOS version 2.3,
    DMI version 2.3,
    SMP specification v1.4,
    Symmetric Multi-Processing
configuration:
    boot: normal
    chassis: desktop
    cpus: 1
    uuid: 44454C4C-4800-1057-8043-B4C04F323331

```

I also got this after reading the absolute begginer forum sticky since I fugure it it some kind of video problem since both Zorin and 13.10 had issues.
 Zorin did show a GUI menu but it was incomplete no Max Min Close buttons
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 
82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```
I know there is a intel video driver I have not tried anything with that 
since it is not working without the driver and when I installed it in Zorin it did not help.
(or maybe it did not install?)

I hope some one can help me I will try anything since I am a noob.
I have no data on this machine other than the ubuntu os so if it toast'ed no biggie
I have run ubuntu 13.10 from the cd on my normal computer and it is way fast compared to my xp,vist,7 OS's
So I am at your mercy but I learn fast and would help other's once I learn stuff.

---

### Post by WinXpRefugee on 2014-01-17
did all the stuff in this forum
[http://ubuntuforums.org/showthread.php?t=2183298](http://ubuntuforums.org/showthread.php?t=2183298) 
still no go 
--
Dont know what this means
--
"OK, it seems to work fine under Linux 3.8.0-32-generic"?

"I type this from Xubuntu, and it works! ^_^
Xubuntu is just as good as Ubuntu, maybe even better for my PC because is lighter."?

---

### Post by DuckHook on 2014-01-17
Hi Bill and welcome to Ubuntu and the forums.

Though I hope to help with your technical issues, a few words first about the adventure on which you are embarking:

1. Although various Linux distros are indeed "free" (as in beer) you will find that they all have a learning curve and, not being mainstream and therefore automatically supported by HW vendors, there are times when certain HW needs some tweaking before it runs with certain distros.

2. I highly encourage you to read [this]("http://linux.oneandoneis2.org/LNW.htm") and [this]("http://www.psychocats.net/ubuntu/index"). The first explains the differences between Windows and Linux. The second is a great intro to how Linux works.

3. Although Zorin is derived from Ubuntu, it is not associated with Ubuntu and has its own support site. There are Zorin-specific issues that the members of this site are unlikely to be able to help with. In any case, the Zorin installed base is very small. If you are considering it for its resemblance to the MS world, then as a seasoned user of both Linux and Windows, I should alert you to the fact that the resemblance is superficial and therefore misleading. In the end, Linux is a very different beast from Windows. Papering over those differences with a familiar GUI will only create nasty surprises when you find yourself having to deal with those differences.

4. If your old HW was running XP, then it is possible that it is not quite powerful enough to run Ubuntu. The 'buntu family comes in four flavours for exactly this reason—to accommodate HW of differing capacities. If you would like a better idea of which flavour would work best on your HW, then please post your HW details to this thread. For old XP machines, I would recommend Xubuntu or Lubuntu depending on just how old they really are.

On to your technical issues:

1. I don't understand what you mean by> ...boots to the default desktop picture only...isn't this what you want? What desktop background were you expecting if not the default?

2. Rather than gksu lshw-gtk, please do the command-line-only```
sudo lshw -sanitize
```The resulting code is easier to copy and paste back into this thread.

3. In Linux, when you launch a program from a terminal session, the program is created as a child process to the terminal session and will die if you close the parent terminal session. It is not necessary to tie a GUI program to a terminal session, but you would need to launch the program using its GUI launcher and not from a terminal session.

**EDIT**

Did not see your second post. It seems that you have resolved many issues with Xubuntu. As per my above note, I suspected that this was the best distro for you in the first place. If you are happy, please mark thread solved. If you would still like to discuss other distros, please provide output of lshw command above.

---

### Post by WinXpRefugee on 2014-01-17
Duckhook,
Thank you for responding 
I have not solved the problem those are Quotes from another post I dont understand what they mean
Linux 3.8.0-32-generic 
I dont know what this means but it seems that something was left out of the distribution  what ever that means?
I dont know what Xubuntu is 
You may be right this tower may not have the juice to run the os
result from  sudo lshw -sanitize

```
computer                  
    description: Desktop Computer
    product: Dimension 2350
    vendor: Dell Computer Corporation
    version: A02
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 07W080
       vendor: Dell Computer Corporation
       physical id: 0
       version: A00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Mitac International
          physical id: 1
          version: A02
          date: 03/24/2003
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 2200MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:ee000000-ee07ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ee080000-ee0803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:ec000000-edffffff memory:40000000-400fffff
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=32
                resources: irq:16 memory:ed002000-ed002fff ioport:c000(size=16)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:ed000000-ed001fff memory:40000000-40003fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40100000-401003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:ee081000-ee0811ff memory:ee082000-ee0820ff
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD800JB-00JJ
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 05.0
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000b0f0b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 modified=2014-01-17 17:17:11 mount.fstype=ext2 mount.options=rw,relatime,errors=continue,user_xattr,acl state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 74GiB
                capacity: 74GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: [REMOVED]
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom:0
             description: DVD-RAM writer
             product: iHAP222   W
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 7L05
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: CD-R/CD-RW writer
             product: CD-RW  CRX216E
             vendor: SONY
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/sr1
             version: PD01
             capabilities: removable audio cd-r cd-rw
             configuration: ansiversion=5 status=nodisc
```


I keep reading posts and I have tried so many things that I don't know up from down 
but it seems to be somthing related to something called 
unity

---

### Post by WinXpRefugee on 2014-01-17
Duckhook,
in repsonce to
 1. I don't understand what you mean by 	 		 			 			 				...boots to the default desktop picture only 			 		

 	
 
...isn't this what you want? What desktop background were you expecting if not the default?

I mean I get the picture and a mouse cursor nothing else no menu's icons nothing just the background image 
sorry about the confusion and again thank you for helping

---

### Post by Roger Cook on 2014-01-17
Bill, welcome to the new world of linux, when you get the right distro for your setup you will probably never go back. Let me suggest that you try one  of the Mint flavors of linux
they are much easier to get going for a noob especially with old hardware. Mint Mate and xfce are both lightweight distros but kde from mint will probably run well on your rig.

There is not the display problems that you are having with mint!

---

### Post by WinXpRefugee on 2014-01-17
Roger Cook,
Thanks for your reply.
I have just looked in to xubuntu and Lubuntu as they were named previously in this post.
The thing that I think I would like about them is the Ubuntu One seems analogus to android market.
What I am really looking for is an all purpose distrobution. (if it exists)
That I could recomend to freinds and family to install on their xp machines, (I will have to install it on my multiboot machine as well as I do computer support as a hobby)
Something that could handle similar tasks of the XPOSs.

 I have good friend that has a small buisness with 6 machines all running xp. He has "mission critcal software, (some design software and some intuit products) " that were designed for Win98/2K/XP.  
His machines are all Core2Duo's 3.0Ghz with 4GB Ram GefForce 9800 1Gb GTX and 500GB hard drives.

Is that enough juice to handle Ubuntu 13.10 ?
I have seen people mention WINE how well does that work? 

I may have to geek out on two distributions to meet the needs of my hobby.
 
I also want to set up a RAID NAS if I can get a good enough background in linux
So that would probably be 3 distributions.

In short I feel like I am late to the party.
 I want to learn to trouble shoot linux and work with it as adeptly as windows 3.1/3.11/95/98/suckyMe/Vista/7.  
I figure it will be alittle like learning a new language but I want too.

I apriciate any guidance (or even a beat down if I can learn something LOL)

---

### Post by wildmanne39 on 2014-01-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by WinXpRefugee on 2014-01-17
Wild Man
Thanks for your reply.

```
 I was not sure if I should put the "sudo lshw -sanitize" Output in a code box and did not know how to 
Ps i hope this is not considered abuse i am just testing it out 
```

I was thinking Mint 16 Mate
 
It says some stuf about 3rd party software.
download's with and with out since I live in the USA do I have to get with out in order to install.
 I am just going to use it on my personal computer.
Or does it mater?

---

### Post by DuckHook on 2014-01-17
> **Bill_Graves said:**
> ...I get the picture and a mouse cursor nothing else no menu's icons nothing just the background image...Ah. Okay. Got it.

Your HW specs are barely enough to run Ubuntu, and I doubt that you will enjoy the experience. Yours is a Pentium 4 with 1 GB RAM and an integrated Intel video chipset. This is not high-powered HW by today's standards and Ubuntu/Kubuntu is designed to run on multi-core CPUs with minimum 2GB RAM and more powerful graphics.

Ubuntu comes in different flavours. The two high-powered flavours are Ubuntu and Kubuntu. They use different desktop environments, but both are high-end and resource hungry. The next level down is Xubuntu, which is designed for HW of about your power. The lightest flavour is Lubuntu, which is pretty plain to look at, but runs like stink on even relatively old HW. There are limits. Really ancient dinosaur HW won't run any of these distros because they are all still graphics-based, but if XP will run on it, then chances are that Lubuntu will do just fine.

Aside from the above four official flavours, there are many other derivative distros that are "based" on Ubuntu, but are actually independent. Bodhi is one such and a very interesting one at that. It takes some getting used to, but once you get the hang of it, is just awesome. Zorin is another. The Mint family is a third. I have all of these running as Virtual Machines on my box, and Mint has proven to be the most ornery and problematic. Its claim to fame is that it already comes with the proprietary drivers for AMD and nVidia chipsets that often cause problems in the Ubuntu flavours, but since your chipset is an Intel, Mint is unlikely going to be of any benefit when it comes to video.

I would recommend that you download both Xubuntu and Lubuntu in their Live DVD/CD/USB form, burn them and try them out. If you wish, try Mint as well. Linux is about choice, and you may find that you strongly prefer one over another. However, with your equipment, stay away from Ubuntu or Kubuntu.

---

### Post by DuckHook on 2014-01-17
> **Roger Cook said:**
> ...There is not the display problems that you are having with mint!Begging pardon but it is not possible to make this claim realistically. See my previous post. In general, video problems have to be chased down before they can be squashed. These forums are filled with video issues and they are all different. The only way to solve them is through the process of diagnosis, research and solution implementation.> Mint Mate and xfce are both lightweight distros but kde from mint will probably run well on your rig.Again, I beg to differ. Mint is a derivation of Ubuntu. It cannot magically operate more efficiently than Ubuntu unless it largely ceases to be based on Ubuntu and its developers decide to base it on another distro. KDE is a very bloated DE that drags in QT, Compiz and a large infrastructure. It is designed to run on more modern multi-core machines with lots of RAM and high-end graphics. It will not run well on the OP's box. XFCE would be far less resource intensive, but then, the OP may as well try Xubuntu, which is also XFCE.

As mentioned, the only advantage the Mint brings to the table is a looser ideology on closed-source drivers. In the case of Intel video chipsets, this advantage is largely superfluous. However, the OP may wish to try it out and see for himself.

---

### Post by WinXpRefugee on 2014-01-17
Duck Hook, Roger Cook, 
Thank you both for your responses, 
 I am running low on DVD's LOL  
I am running a Live version of  **Linux Mint 16 "Petra" - MATE (32-bit)   **
Based on a recomendation I read. That it was what another guy did for his xp users ( I think it was his mom) 
It seems to preform better than XPPSP3 that got beefed by malware and became unbootable, and that is from the DVD.
I expect better on HD I am downloading **xubuntu 13.10, Saucy Salamander** right now and plan to try it out the same way.
 I am goging to put WINE on it and try to run/install an old windows program (Sling media player or a hoyle card game)
 I am sure there are linux versions but I want to see how WINE works.

---

### Post by DuckHook on 2014-01-17
> **Bill_Graves said:**
> The thing that I think I would like about them is the Ubuntu One seems analogus to android market.I think you have an erroneous impression of Ubuntu One. In the Linux-sphere the repositories take the place that the Market takes in the Android-sphere. Ubuntu One is more a combo of iTunes and Dropbox. I would not be surprised if Shuttleworth positions it to also take on elements of Amazon over time.> What I am really looking for is an all purpose distrobution. (if it exists)It does not. You should already have some idea of the spectrum of machines that various flavours of Ubuntu alone are designed to cover. For even older machines, there are nano-sized distros like Puppy/Slitaz/Tiny Core. On the other end, for a full-fledged experience bloated to the bursting point with apps and services, try PCLinuxOS Full Monty edition which is so obese it requires intervention.> That I could recomend to freinds and family to install on their xp machines,Until you become a Linux Poweruser, it is difficult to support friends and family. I know because this is exactly what I do in retirement. The good news is that it isn't that difficult to become a Linux Poweruser, but the initial learning curve is steep: for both you and those you are seeking to convert. You are sensing some of it now.

The biggest problem facing users new to Linux is that they think it is just a free version of Windows. This creates unrealistic and unfulfillable expectations, misguided agendas, and a string of bad habits that they don't think they need to unlearn. Please read my links in post #3. It is only after expectations, agendas and bad habits have been adjusted to the Linux way that you can realistically get your buddies working with Linux.> I have good friend that has a small buisness with 6 machines all running xp. He has "mission critcal software, (some design software and some intuit products) " that were designed for Win98/2K/XP.Then Linux is not for him. The concepts "Mission Critical", "Intuit" and "design software" do not mix with the term "Linux". None of his software is likely to run on Linux natively and Intuit in particular is a real pig in a poke. The only way to run what he wants would be to run Windows inside a Linux Virtual Machine, which is far too complex for a small business and defeats the point of going to Linux in the first place. Unless your friend recognizes that he is currently suffering from a classical case of vendor lock-in and is prepared to break his addiction at an early stage before he is even further locked-in, there is no remedy to his current needs. And if he is willing to break the addiction, then he must be prepared for a long and painful process of withdrawal, replacing his accounting software with a Linux-based package, and his design software with Linux-based packages too. Most businesses that depend on these tools for their very existence cannot afford the risk, time, resources and frustration to learn everything all over again just for the questionable benefits of having a "free" OS.> His machines are all Core2Duo's 3.0Ghz with 4GB Ram GefForce 9800 1Gb GTX and 500GB hard drives.

Is that enough juice to handle Ubuntu 13.10 ?Yes. But the problem isn't the HW. See above.> I have seen people mention WINE how well does that work?...for a gamer? Not bad. If his game crashes, he may just lose a character. For a mission critical app in a business? Not at all well. Intuit is awful in WINE. So is most "design" software. AutoCAD, for example, won't even load. Nor will Photoshop or Illustrator. WINE is not the way to go for anything that is even remotely mission critical.> I may have to geek out on two distributions to meet the needs of my hobby.This is where Linux shines. If you have the luxury of treating the OS as a hobby, then the sky is the limit. And once you get past the "hobby" stage, you would be ready to make it a true working OS.> I also want to set up a RAID NAS if I can get a good enough background in linuxAgain, where Linux shines. The backoffice and things like NAS is where Linux is demonstrably superior to Windows.> In short I feel like I am late to the party.
I want to learn to trouble shoot linux and work with it as adeptly as windows 3.1/3.11/95/98/suckyMe/Vista/7.
I figure it will be alittle like learning a new language but I want too.

I apriciate any guidance (or even a beat down if I can learn something LOL)You are never late to the party. Linux is one never-ending party. So how can you be late?

It is heartwarming to see your enthusiasm and I am not trying to discourage you with some of my comments above. It's just that one has to keep a sense of perspective about these things. Linux is not a magic bullet. It becomes more and more of one as you get better and better with it, but it starts out as rather a damp squib actually. The learning curve is steep, it is not at all like what you are familiar with, and it requires time, effort and patience to slay the dragons that keep rearing their ugly heads. I've been at it for so long that Windows is kept around just for some old games that I can't bear to part with. But for, say, your small-business friend, Linux is not a realistic solution.

I hope that you become as fascinated and awestruck by your journey with Linux as I was. And there may come a point at which you are so comfortable with it that you can guide your friend through a complete changeover of his business to this wonderful OS. If you ever do so, we on this forum would love to hear about it.

---

### Post by WinXpRefugee on 2014-01-17
Duck Hook,
Thank you for your response.
I read both the links you suggested Good stuff love the motorcycle and car comparison!

Mint DVD does not offer install must have downloaded the wrong ISO 
I am installing Xubuntu Now

I found that most of the people that I help with their computer only use it for web and web based email.
Maybe some low end games like card games Spider solitare ect. 
They really don't need the power they have but hey think they need it?
[SIZE=1](Heck I used my AMD K-6 700Mhz 1GbRAM 80gbHD with AGP Video until 2007 damn thing is bullet proof it would probably boot right now if I pluged it in LOL)[/SIZE]

My freinds design software is from the win 95 days it is 16 bit
 I cant remember what its called but it is old enough that you can move the file folder from machine to machine and it works 
So I think it has very little dependance on the win OS.

What are the alternatives to QuickBooks ?(Google search)

Of course he could just have one windows machine.

The other thing he uses alot is office2000 esp excell and Access 
He programed a Database in VBasic For Access that he uses constantly.
He has an I pad and I phone 
I thought Mac was based on linux this might be an advantage for him.
But you may be right He may just have to bite the bullet or not do it 

Any way My "problem" is **SOLVED** [SIZE=1]
(or to be more accurate my problem was lack of knowlege.[/SIZE])
Probably should delete the whole thread, I doubt that this will really help anyone else.

[COLOR=#ff0000]Post Title: I changed the oil and can't make my riding lawnmower go 100Mph?:(
[/COLOR][COLOR=#008000]Reply post:  No you can't, The oil has nothing to do with Mph :biggrin: [/COLOR]

**Last ? Can I post questions about xubuntu here will I get blasted for not being in some specific forum. I suspect I will run into problems with intel video drivers**.

---

### Post by DuckHook on 2014-01-18
> **Bill_Graves said:**
> I found that most of the people that I help with their computer only use it for web and web based email.
Maybe some low end games like card games Spider solitare ect.That's what I thought until I actually paid some attention to how they used it. They tell you that they only use it for surfing and e-mail... until they phone you up asking why that powerpoint attachment that their son sent them can't open. Or that Apple-based movie of their grandson can't play. Or why that Word document someone sent them is all wonky and misconfigured. It is possible to break our dependence on Microcrack, but it starts with a realistic acceptance from all parties about just how difficult the process will be. I've converted dozens of Windows users to Linux, but it all starts with an acknowledgement that it will be an involved process that will sometimes frustrate them and won't be easy. The worst cases are always the ones where some well meaning but clueless Linux enthusiast has told them them nothing could be easier. The unfullfillable expectations usually sour them on Linux by the second problem.> ...I used my AMD K-6 700Mhz 1GbRAM 80gbHD with AGP Video until 2007You might try running Lubuntu on that thing. It may surprise you how well it works.> My freinds design software is from the win 95 days it is 16 bit
I cant remember what its called but it is old enough that you can move the file folder from machine to machine and it works
So I think it has very little dependance on the win OS.More than you think. And even a small dependence is enough to bork its working under WINE. But you can always try. No harm done trying. [Here]("http://appdb.winehq.org/") is a link to WINE's app database. Anything less than Platinum is unacceptable for production use.> What are the alternatives to QuickBooks ?The only one I can suggest is GNUCash. The other ones available from the repositories are all Quicken alternatives—acceptable for home use, but absurdly underpowered in a small business setting. Ignore all of the breathless accolades in the reviews: home users generally have no idea about the demands of business accounting. Most of them are not even double entry-based. GNUCash is the only one I'm aware of that is, but doesn't cost you an arm and a leg. Beyond GNUCash, there is a vast wasteland until you get to the really high-powered mid-level enterprise stuff that is developed for accounting departments of several dozen simultaneous users. Their licencing costs are proportional to their power and every bit as expensive as you are likely imagining. A fellow forum member has mentioned web-based accounting as a workaround, and this is a good alternative for some people.> Of course he could just have one windows machine.This is a possibility, but only you and he could tell how viable this would be.> The other thing he uses alot is office2000 esp excell and Access
He programed a Database in VBasic For Access that he uses constantly.Another huge roadblock in his adopting Linux. Access is as bad as Quickbooks.> I thought Mac was based on linux this might be an advantage for him.A common mistake. It is based on a Unix variant called BSD, but has glued on so many proprietary appendages by now that it no longer counts as a variant. It's a Frankenstein's monster in nylons and lipgloss with a really cool hairdo.> Any way My "problem" is SOLVED
(or to be more accurate my problem was lack of knowlege.)Good to hear. Knowledge (or lack thereof) is a relative thing. Compared to many on these forums, I'm just a lightweight.> ...I doubt that this will really help anyone else.On the contrary, I wish more new users would read threads like this. It would save them a lot of headache and heartache trying to hang on to their Windows mindsets/expectations in Linux. You can do everyone a favour and mark the thread "solved" using the thread tools at top of page.> Post Title: I changed the oil and can't make my riding lawnmower go 100Mph?
Reply post: No you can't, The oil has nothing to do with Mph:)> Can I post questions about xubuntu here will I get blasted for not being in some specific forum. I suspect I will run into problems with intel video drivers.This is the perfect forum for you. Just tag your thread with "Xubuntu" and it will attract Xubuntu experts. If you run into specific problems, try specific forums, but general questions are fine here. Video drivers are a good example of a proper thread in this forum, although it should be noted that if your installation is running fine now, you don't need any further video driver. Unlike Windows, drivers are built into the kernel in Linux, and in the case of Intel, they cooperate so well with the Linux community that Intel open source drivers are as good as any proprietary driver that may exist—often better.

Good luck with your explorations and Happy Xubuntuing!

---

### Post by bobblex on 2014-01-19
Bill,
I see this topic has been marked "SOLVED", but I just came across it and wanted to let you know that I'm running Lubuntu 13.10 on my Dell 2350 with a 1.8G Pentium 4.  At times it gets kind of slow because so much of the software will load the CPU to 100%.  I've got 1.5G of RAM and two 80G HDs.  I've got Lubutnu 13.10 loaded on one and LXLE 12.04.4 on the other.  I installed an NVidia GeForce 6200 video card to help with display speed, but really didn't gain much over the integrated Intel video other than a little better 3D performance.  The 1.8G CPU and probably the old, slow data bus of the motherboard are the real choke points.  

But, it does work and is nominally better and faster than it was under XP as it aged and applications needed more power.  

If you have Xubuntu running, you might want to give Lubuntu 13.10 a try.  It seems a little faster and less resource intensive than Xubuntu and sometime in April there should be a long term supported (LTS) version, Lubuntu 14.04, released.

Good luck.

---

### Post by robin7 on 2014-01-19
> **bobblex said:**
> 
If you have Xubuntu running, you might want to give Lubuntu 13.10 a try.  It seems a little faster and less resource intensive than Xubuntu and sometime in April there should be a long term supported (LTS) version, Lubuntu 14.04, released.

I did exactly that, and found that Abiword crashed every time I opened it, video would not play despite installing all the restricted-extras, and Lubuntu refused to load my printer even though it "recognized" it.  I did all the little things I found on the forums to do, but Lubuntu just misbehaves on my poor old computer.  So I'm back where I started from, on Xubuntu 12.04, and will learn how to make it leaner and faster.  I'll likely try Lubuntu again after the new LTS is released, but as long as Xubuntu is performing as it should, I'll just "lighten it up" carefully as I can.

---

### Post by WinXpRefugee on 2014-01-20
**[COLOR=#ff0000]Bobblex and Robin 7 [/COLOR]**
Thanks for your response.
 
I ended up using LM16 MATE seem to be pretty stable. After all the video mubojumbo got strightend out.

If you care to ask why am I doing this?

 [COLOR=#0000ff]I am getting readdy for the [SIZE=4]**XP[SIZE=2]ocalypse[/SIZE]**[/SIZE] this April. 
 I do computer work as a hobby and need a distro that I can swich my xp people to.
[COLOR=#0000ff]It is getting harder and harder to fix xp.[/COLOR] 
Most of them run similar hardware to this machine (something you can buy at walmart)  
Most of them are like me, working people and don't have the $$$ to just go buy an new computer or upgrade to the latest windows ver. 
So I had a good freind who was brought me his nuked (typical malware virus stuff) Dell 2350 running XPP32SP3 , Thought he would be a good test case see if real "non geek" users could live with Linux.
If this works out well I can really help alot of people.

I took it to him january 18, 2014 and he is using it after about an hour of drinking beer.
 er I mean an hour of my expert tutalge (LOL)[/COLOR][COLOR=#ffd700].

[/COLOR]
[COLOR=#ff0000]**Bobblex,**[/COLOR]
I would love to hear about your experiences. I am having a problem with the Dell 2350 comming out of suspend (It won't) and on Cold boot there is no video rendering of the login screen without alot of mouse movement/clicking.
Did you ever have these problems, If so how did you solve them?  
(planning on trolling your post after this post since you have the same machine and similar software as far as I understand.) 

**[COLOR=#ff0000]Robin 7,[/COLOR]**
 I have been using Libre office? (I think that is right)

---

### Post by robin7 on 2014-01-20
> **Bill_Graves said:**
> **[COLOR=#ff0000]Bobblex and Robin 7 [/COLOR]**

I ended up using LM16 MATE seem to be pretty stable. After all the video mubojumbo got strightend out.



Probably more demanding on resources than the others you've tried, but I hear it's a sweet distro!

> **Bill_Graves said:**
> 
If you care to ask why am I doing this?

 [COLOR=#0000ff]I am getting readdy for the [SIZE=4]**XP[SIZE=2]ocalypse[/SIZE]**[/SIZE] this April. 
 I do computer work as a hobby and need a distro that I can swich my xp people to.
[/COLOR]
[COLOR=#0000ff]

[/COLOR]Just remember that a lot of us who have old XP machines probably have lower RAM and less processing power on those old machines.  Too low for many of the big-name fancy one-size-fits-all desktop distros.  

> **Bill_Graves said:**
> 
**[COLOR=#ff0000]Robin 7,[/COLOR]**
 I have been using Libre office? (I think that is right)

Lubuntu "ships" with Abiword and Gnumeric - two "lightweight" programs, a word processor and a spreadsheet program, that do *most* of what the big office suites (OpenOffice, LibreOffice) do.  Xubuntu 12.04 comes with those too instead of the big, heavy, resource-hogging office suites.  Unless those XP machines are fairly new, I think I'd be pointing new Linux users to these lightweight alternatives.

---

### Post by WinXpRefugee on 2014-01-20
Robin,
Thanks for your response,
So are you advocating for Lubuntu as opposed to Xubuntu
I have not downloaded any Lubuntu ditributions

On the test Dell 2350 P4w1GBRAM and intel 845 it's running Mint 16-Mate  having 2 issues I have one [SOLVED] The other one I am working around  until I figure it out.

I have used open office on windows machines 
The 2350 runs libre office really well, but good to know that there are Lighter versions if I run into a system that is really low powered.

---

### Post by bobblex on 2014-01-20
Bill, 
I also moved to Linux to keep my old XP Dell 2350 useful.  I first ran Mint 13 Mate and found it to be pretty decent, but I kept reading about Lubuntu and Xubuntu being less resource intense and being a little faster.

When I first started running Mint I had a lot of trouble getting the drivers for the NVidia card to load and run right.  It turned out that even though I was able to load 2G of RAM on the motherboard, it caused memory conflicts in the video memory areas.  I dropped back to one 1G module and a 512M module and everything has been OK ever since on any Linux distro I've tried.  I did have to learn how to insert the NOMODESET into grub in order to get any of the distros to display properly when I use the NVidia drivers. 

I use the LibreOffice suite on the 2350 because that's what I use on all the other computers in the house.  I definitely have fewer problems with Lubuntu 13.10 than I did with Mint or XP and I've got it running fine and sharing files across the network and with an old NAS device that I have.  Getting the links to the NAS to come up was little tricky as I learned my way around the mount command and CIFS.  Other than that, I can't really think of any real problems.  

I also have My-Weather-Indicator running on it and an automatic background changer (Variety) running by just following the on-line instructions for downloading, installing and configuring them.  Same for Vuescan, which I needed because my Microtek scanner is supported by Sane/XSane.

After I'd used Mint and some other distros, including PC-BSD, I moved to Lubuntu 12.04.  After I had 12.04 running good, I upgraded to 13.04 when it came out, and then upgraded to 13.10 when it came out.  I upgraded to them just using the Upgrade option rather than a clean install and found that it went quite well.  I did have to reload a couple of applications, but that was it. 

I'd be happy to answer any questions I can about getting Lubuntu to run OK.  

Bob

---

### Post by WinXpRefugee on 2014-01-22
bobblex,
Thank again I am still having problems with this machine Ihave fixed the video problem but it won't come on after sleep and after cold boot won'trender the login screen I am still using the intel onboard graphics.
I am live distro ing Lubuntu now I really like the way mint-MATE looks and feels. 
As I am larning more I dont know what package I really like just saw screens of cinnimon and it looked like my MATE so maybe I need to figur out what the thing that I like actually is and try to install that pkg
I like libre office alot better than abi and the machine seems to run it at least as good as it ran Office 2003 in xp 
It is pretty old computer

---

### Post by WinXpRefugee on 2014-01-23
Update:
I think I fond my distro for this Machine 
**Linux Lite 1.0.6  32bit**
[https://www.linuxliteos.com/index.html](https://www.linuxliteos.com/index.html)
Seems to have every thing I want no video problems and suspends and resumes ey have a LTS
but [B]Linux Lite 1.0.6 32bit
[/B]was just put up 7 days ago.
I probably will use something geeky for my main use machine but I am excited right now about the way the live cd is working I will edit if i have problems.

---

### Post by bobblex on 2014-01-23
As to Can't resume from sleep:  I never let my Dimension 2350 got into sleep or hibernate mode as that was troublesome even under XP.  I do let the monitor shut down after a period of time.

It will be interesting to see how Linux Lite works for you.  Did you ever try the Lubuntu 13.10 Live?

---

### Post by WinXpRefugee on 2014-01-27
Sorry took so long to respond have been having some account issues wanted to use a psuedomym

All the Distros I tried had same problem Video which I could fix with the creation of the .conf file
then they would not resume Tried S3 and S1 settings in BIOS.

Linux Lite OS 1.0.6 worked great out of the box. video, resume, 
 I am not sure why since it uses ubuntu as well.
had to manually install lite user manager and lite Software manager some how they did not get packaged.

I modded it with 
wiskers 
and installed 
Libre office, Banshee, shotwell, weather app 
VLC does not autoplay DVD's have to swich to the Device tab and select the Drive but then it plays 
tried tux cart for kicks (NOPE!) Unistalled it

---

### Post by hpzgod on 2014-03-19
This helped me. Thank you.

---

### Post by WinXpRefugee on 2014-04-24
Hpzgod,
 I am glad that it helped It is so cool to have a forum like this to make linux easier,

This might also help you 
[https://bbs.linuxdistrocommunity.com/showthread.php?tid=1867](https://bbs.linuxdistrocommunity.com/showthread.php?tid=1867)

---


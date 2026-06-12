---
title: "Flash plugin on Firefox crashes - non-SSE2 PC"
date: 2015-07-22
forum: New to Ubuntu
---

### Post by soundgeek on 2015-07-22
I have installed 32-bit Lubuntu 14.04.2 on an old PC. It included Firefox 39.9+build5-0

Flash player does not seem to work at all. It crashed when I tested it with BBC iPlayer.

On another 64-bit PC, Flash on Firefox on 64bit Ubuntu works fine.

How do I fix this problem?

---

### Post by Vladlenin5000 on 2015-07-22
What are the specs of that old PC?

---

### Post by soundgeek on 2015-07-23
It has 765 MB memory and AMD Athlon XP/MP processor, 2GHz "frequency" with 250kB cache.

Plenty of disk. I gave it 1.5 GB swap partition.

I've swapped out the old 64MB Nvidia card for a similar card with 512MB of memory in case a lack of video memory was causing the crashes. Will Linux/Flash automatically make use of the extra video memory?

I still get crashes.

---

### Post by mörgæs on 2015-08-19
An Athlon XP has SSE but not SSE2, which is necessary for Flash.
If you click the Old Hardware link in my signature there is a workaround in post 2.

---

### Post by tristan16 on 2015-08-19
I have the latest version of Ubuntu, a 4.3Ghz processor, and 8GB of RAM. Flash Player support in the latest version of Firefox is absolutely terrible. I think YouTube was the only website that didn't crash, and even then, the HTML5 player works much better.

Basically, Flash Player doesn't support Ubuntu anymore and doesn't provide updates, which means it's no surprise it doesn't work.

---

### Post by soundgeek on 2015-09-20
Thanks for this reply[**[COLOR=#DD4814][B] mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075") 	 . I don't know what SSE2 is, but I'll check it out. 

Flash does seem very fussy!

tristan16,  I have a PC running 64 bit Ubuntu and Flash seems to run fine. BBC iPlayer is glorious!

After the success with the new 64 bit machine, I thought I would try Lubuntu on the old 32 bit PC and that's when I hit the Flash player problem. So many sites use Flash; it is hard to avoid it. BBC iPlayer seems totally dependent on it and an alternative player [Beebotron]("http://beebotron.org") stopped working (though may now be re-surrected).

I have heard of HTML5 player, but I don't know how to invoke it. Is it packaged in with Firefox?

---

### Post by monkeybrain20122 on 2015-09-21
The mpv addon works for iPlayer and many other sites (e.g Youtube, Vimeo etc) Performance is better than flash anyway even if flash works.
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

To use this you need to install up to date version for mpv and youtube-dl (repo version is too old to work)

For mpv, either            [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests) (Trusty)
or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

For youtube-dl
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

See instructions in links for how to add ppa to your sources list.

---

### Post by Sweet_Baby_Jamie on 2015-09-21
Usually installing ubuntu-restricted-extras has been enough for my computer.

---

### Post by tristan16 on 2015-09-21
> **soundgeek said:**
> tristan16,  I have a PC running 64 bit Ubuntu and Flash seems to run fine. BBC iPlayer is glorious!

After the success with the new 64 bit machine, I thought I would try Lubuntu on the old 32 bit PC and that's when I hit the Flash player problem. So many sites use Flash; it is hard to avoid it. BBC iPlayer seems totally dependent on it and an alternative player [Beebotron]("http://beebotron.org") stopped working (though may now be re-surrected).

I have heard of HTML5 player, but I don't know how to invoke it. Is it packaged in with Firefox?

HTML5 is a code standard, and Firefox has good support for it. However, the HTML5 Video player is only used if the website uses it. If the website wants to use Flash, it will use Flash.

---

### Post by soundgeek on 2015-09-22
> **Sweet_Baby_Jamie said:**
> Usually installing ubuntu-restricted-extras has been enough for my computer.

Yes I installed restricted extras on both machines. Flash works on the new 64 bit PC, but not on the old 32 bit PC.

> **monkeybrain20122 said:**
> The mpv addon works for iPlayer and many other sites (e.g Youtube, Vimeo etc) Performance is better than flash anyway even if flash works.
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

To use this you need to install up to date version for mpv and youtube-dl (repo version is too old to work)

For mpv, either            [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests) (Trusty)
or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

For youtube-dl
[https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)

See instructions in links for how to add ppa to your sources list.

Thank you for the links monkeybrain. I'll check them out later.

---

### Post by mörgæs on 2015-09-22
> **Sweet_Baby_Jamie said:**
> Usually installing ubuntu-restricted-extras has been enough for my computer.

Yes if the computer has SSE2, which this one does not have.

---

### Post by soundgeek on 2015-09-22
> **mörgæs said:**
> An Athlon XP has SSE but not SSE2, which is necessary for Flash.
If you click the Old Hardware link in my signature there is a workaround in post 2.

Thanks for collating all this information!  I tried:
sudo lshw -C cpu | grep -i sse2
Unfortunately each line of output overwrites the previous, so the next prompt overwrites the final line and leaves no result. However I read "PCI (sysfs)" and "SCSI" before they disappeared. So I'm not clear whether I have SSE2.

I tried installing libre-office. The commands: 
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install libreoffice
  
seemed to work, but

sudo apt-get install libreoffice-help-xx
sudo apt-get install libreoffice-l10n-xx
 
yielded "Unable to locate package" errors, so I stopped before purging the existing Lubuntu packages.

I'll try turning off "Use hardware acceleration when availablere" in Firefox & re-installing Flash and then see if I still get crashes in Firefox.

Also thanks for the "sudo lshw -sanitize > lshw.txt"  command. This yielded:
```
computer
    description: Computer
    product: K7NF2-RAID
    version: 1.00
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: uuid=[REMOVED]
  *-core
       description: Motherboard
       product: K7NF2-RAID
       physical id: 0
       version: 1.00
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30
          date: 07/31/2006
          size: 64KiB
          capacity: 448KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 2200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 6.8.1
          serial: [REMOVED]
          slot: CPU Socket
          size: 1795MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow vmmcall cpufreq
        *-cache:0
             description: L1 cache
             physical id: 4
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 5
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System memory
          physical id: 1
          size: 1015MiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c1
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:f4000000-f7ffffff
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: NVIDIA Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: NVIDIA Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: NVIDIA Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: NVIDIA Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: c1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP2A ISA bridge
             vendor: NVIDIA Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP2A SMBus
             vendor: NVIDIA Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:5 ioport:d480(size=32)
        *-usb:0
             description: USB controller
             product: MCP2A USB Controller
             vendor: NVIDIA Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:febfb000-febfbfff
        *-usb:1
             description: USB controller
             product: MCP2A USB Controller
             vendor: NVIDIA Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:febfc000-febfcfff
        *-usb:2
             description: USB controller
             product: MCP2A USB Controller
             vendor: NVIDIA Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:febfdc00-febfdcff
        *-bridge
             description: Ethernet interface
             product: MCP2A Ethernet Controller
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a3
             serial: [REMOVED]
             size: 100000000
             capacity: 100000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=[REMOVED] latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
             resources: irq:21 memory:febfe000-febfefff ioport:dc00(size=8)
        *-multimedia
             description: Multimedia audio controller
             product: MCP2S AC'97 Audio Controller
             vendor: NVIDIA Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
             resources: irq:20 ioport:d800(size=256) ioport:e800(size=128) memory:febff000-febfffff
        *-pci:0
             description: PCI bridge
             product: MCP2A PCI Bridge
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
        *-ide:0
             description: IDE interface
             product: MCP2A IDE
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: nForce2 Serial ATA Controller
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:ff8(size=8) ioport:ff0(size=4) ioport:fe8(size=8) ioport:fe0(size=4) ioport:e400(size=16) ioport:e000(size=128)
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: NVIDIA Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c1
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:faa00000-feafffff memory:b2900000-f28fffff
           *-display
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:19 memory:fd000000-fdffffff memory:c0000000-dfffffff memory:fc000000-fcffffff memory:feae0000-feafffff
     *
```

and much else, but I missed some in the copy and paste...

Just an aside, on the same 32 bit machine, Firefox 40.0.2 with Shockwave Flash 11.9 r 900 on WinXP runs BBC iPlayer haltingly, but does not crash.

> **mörgæs said:**
> An Athlon XP has SSE but not SSE2, which is necessary for Flash.
If you click the Old Hardware link in my signature there is a workaround in post 2.

I finally figured out how to remove the latest Flash which doesn't work and install the older SSE2-free Flash which you suggested.

I only had time for a quick test, but it seems to work!

It does seem that the significant difference between my new 64-bit machine & the old 32-bit machine is SSE2.

Thank you for your excellent guide & in particular for all the Linux command strings :)

---

### Post by mörgæs on 2015-09-24
Good, please mark the thread 'solved' using Thread Tools in order to help other readers.

---

### Post by monkeybrain20122 on 2015-09-24
> **soundgeek said:**
> I finally figured out how to remove the latest Flash which doesn't work and install the older SSE2-free Flash which you suggested.


Which older flash? Just so you know it is a very bad idea for security to install unsupported version of flash. With youtube and many popular sites switching to html5 flash is becoming less and less important. The mpv addon I posted before can handle many flash streaming sites.

---

### Post by mörgæs on 2015-09-25
There is already a warning in the guide I wrote.

Does MPV also work for non-SSE2-computers?

---

### Post by soundgeek on 2015-10-06
> **monkeybrain20122 said:**
> Which older flash? Just so you know it is a very bad idea for security to install unsupported version of flash. With youtube and many popular sites switching to html5 flash is becoming less and less important. The mpv addon I posted before can handle many flash streaming sites.

It was this Flash adobe-flashplugin_11.2.202.236-no-sse2.deb at this URL:
[http://www65.zippyshare.com/v/78802631/file.html](http://www65.zippyshare.com/v/78802631/file.html)

Will the MPV add-on work with older non-SSE2 PCs like mine?

---

### Post by syntaxerror74 on 2016-01-22
> **soundgeek said:**
> It was this Flash adobe-flashplugin_11.2.202.236-no-sse2.deb at this URL:
[http://www65.zippyshare.com/v/78802631/file.html](http://www65.zippyshare.com/v/78802631/file.html)


Funny. This is the very same link you will get when delving through mörgaes' several pagefuls of howto.
And now it comes: the "packager" of this was **yours truly**. Yes. :)

[byteforge]("http://www.linuxquestions.org/questions/user/byteforge-1000218") is *actually* my handle on linuxquestions.org, where I first posted about this:
[http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/](http://www.linuxquestions.org/questions/linuxquestions-org-member-success-stories-23/getting-flash-plug-in-to-work-with-older-cpus-4175420481/)

(Some more in-depth tech info about the .deb package's contents can be found there, too.)
Well, in fact it was my first .deb package I've ever created, and I can say, it's a success, and a huge one at that!
This puppy was upped to ZippyShare back in the beginning of October 2013, and still 3 YEARS later I notice dozens of download requests on there per week, probably also from **other continents**. thousands of miles away.
Just take **Africa** as a good example, for some people down there are fairly tech-savvy, however Athlon XPs are almost deemed luxury in most of these regions, and perhaps one in 5,000 people will happen to own a multicore CPU, let alone one of the Core i7 class.

---

### Post by mörgæs on 2016-01-24
Thanks for your contribution. Keeping users happy and old computers out of the dumps at the same time is a noble task.

People often forget the world wide perspective. Good to see that someone takes it seriously.

Keep up the good work :-)

---

### Post by sudodus on 2016-01-24
> **mörgæs said:**
> Thanks for your contribution. Keeping users happy and old computers out of the dumps at the same time is a noble task.

People often forget the world wide perspective. Good to see that someone takes it seriously.

Keep up the good work :-)

+1 :-)

---

### Post by Vladlenin5000 on 2016-01-24
> **mörgæs said:**
> Thanks for your contribution. Keeping users happy and old computers out of the dumps at the same time is a noble task.

People often forget the world wide perspective. Good to see that someone takes it seriously.

Keep up the good work :-)

+1

---


---
title: "Alert! Automatic updates screwed up my Ubuntu!"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2008-09-10
For the benefit of those who don't read but the first and last post, I will edit my original comment:

I believe that something was put in the updates that should not have been put in there. Today I experience an identical problem to one I had in July: [http://ubuntuforums.org/showthread.php?t=845287](http://ubuntuforums.org/showthread.php?t=845287) (which I never got sorted). I used the update manager, then suddenly I could no longer use Ubuntu -- Meaning If I click to open a folder, Firefox, any of the menu items or any files on the desktop nothing comes up. Basically, my desktop may as well be painted on.  I cannot even shut down or restart. ctrl+alt+bksp works, and starting the computer, and going directly into fail safe mode works, as does terminal mode.

In July, I could not take days to work on this problem, so I reinstalled Hardy. Hardy worked as usual, but then I used the update manager Ubuntu died again! (as mentioned above) I reinstalled AGAIN, and this time I installed all the updates except for anything Gnome related, and the computer worked. 

Here it is September, and I had not done an update since that time. I ran the updates today thinking that if it there were a problem in there, it would be solved by now, but BAM! I updated, and my normal desktop is dead again. 

I am looking for a way I can fix this without installing Hardy ALL OVER AGAIN.

On page 2 of this post is my  sudo lshw

PS, if you don't read other people's comments below, "No" Firefox, Konquerer and Home do not respond in KDE either, only in fail safe mode.  Thanks for your help with this problem.

---

### Post by hyper_ch on 2008-09-10
what update kills your machine? How does it kill it? You don't really give much info.

---

### Post by Motorhead Kaze on 2008-09-10
I gave as much info as I have, and any more info is in the link I posted as well.  All I can do is pretty much write the same thing again, and hope I get more detail.

In July (and again today) updating Hardy, and the required restart of the system, caused ALL applications: menu bar items, Firefox, as well as items on the desktop to simply be non-accessible. There is nothing I CAN click.  At first, a mouse over of an item or button will make it seem like I can select it, but upon clicking on the item, either nothing would happen, or the little time circle would start up, than 30sec. later would stop and after that, still nothing can be clicked. 

Basically NOTHING works except I can see the menu bar and my desktop background.

As I said in the previous thread, when I reinstalled Hardy, I skipped any update with the word Gnome in it. Obviously I am not going to try one update at a time, to see if the computer crashes, because I don't have that kind of time. If someone knows of a way I can go through the terminal to get some sort of log that will help, I will do it, but for now, I know nothing. This time I downloaded all the updates, and there is no way that I would know which one it was, but something in there is off.

Again, I cannot go in through fail safe mode, nor can I go through another kernel. But that is it. Nothing is responsive.

The only thing I can tell you is, I updated, was in the middle of an email and everything froze up, and I cannot get back in to save what was on my desktop.

---

### Post by misfitpierce on 2008-09-10
Thats exceedingly strange. I have all updates and everything runs super smooth. Perhaps its one of the video drivers that may be making it freeze or not show properly... No idea what to do but it is strange... Ill research some ideas.

---

### Post by devosion on 2008-09-10
What are the specs on your PC?

Can you log into ubuntu through the terminal without it crashing?

---

### Post by Motorhead Kaze on 2008-09-10
Hi, I was able to get in via the combination of 2.6.24-16-generic kernel and fail safe mode! Oh yeaaaah!  Not fixed yet, but at least I could save the stuff on the desktop, and feel I have a better chance of fixing this problem.

Yes it is strange, and my apologies for the dramatic title, but it is dramatic for me. My friend uses every update and has zero issues with Hardy. We use the same programs, just have different hardware.

Which specs would you like? People often ask that, and I really don't know which ones people want. 

I am running i386 Hardy (Gnome 2.22.3)
AMD Sempron processor 3400+
ATI Radeon vid card

...what other info will help?

I just reread my post from July when this exact thing happened.  In fact that day and today are identical, I ran the updates and resumed my video conversions with Kino. However, the reason I blame the updates is that 1. It is Gnome that is not working, Kino worked all weekend. Also,last time I reinstalled and left out the updates related to Gnome, my computing was hassle free until updating again.

Are there clues to be found in the System Log?  Whatever I can do to help, please just let me know!

PS things SHOW properly, I just cannot access anything (System menu, places, calendar, shutdown/restart, etc.) everything LOOKS lovely.

---

### Post by devosion on 2008-09-10
So from what I understand Gnome is completely unresponsive at this point but loads up. Have you tried to use a different desktop manager? XFCE? KDE?

I only ask because this seems altogether odd.

---

### Post by Perfect Storm on 2008-09-10
Hmmm...how did you install the ATI driver? By manual or you're using the one from the repo?

---

### Post by Motorhead Kaze on 2008-09-10
Hello again, and yes, I think it is odd too, but more annoying. My Ubuntu pal says I always have weird problems in Ubuntu, but I don't go looking for them or anything.

(Just tried restarted and checked out variations on starting up, but only starting in failsafe will get my desktop and programs to respond.)

Well, I just installed KDE, I will check it out...

---

### Post by Motorhead Kaze on 2008-09-10
KDE: Konqueror and Home will not open, I just get the hour glass.

ATI driver: I installed the propriety driver for my graphics card, BUT somehow, that kept Ubuntu from noticing my second monitor (it was only a clone of the other monitor) At that time I went to System > Administration > Hardware Drivers and disabled the proprietary driver so that I could use the dual monitor system. But before we go barking up this particular tree, I have been using this vid card with dual monitors for 2 months, and use the computer 7 days a week (sad).  So, unless there is a time limit on my vid card, I can't see how it could just go all wacky.

Again, in fail safe mode, everything works...except that Japanese isn't working, which sucks since I need THAT for work too. But the dual monitors and graphics are good.

---

### Post by moody_mark on 2008-09-10
This probably needs some of the forum experts to help you out here. Im far from an expert but just to ask, can you press CTRL+ALT+F1 to get you out to a terminal? (this should also work for keys F2 through to F6 too)

Once in terminal mode you might want to take a look at thing like your /var/log/Xorg.log for errors. Although I dont have a clue what the entries in here mean. Im just a beginner here with Ubuntu. Im thinking it could be something to do with your X11 config where its not seeing your mouse commands etc.

Also you might want to paste the output of the command

```
sudo lshw
```

This will show some of the experts on here which hardware you got and if theres any incompatibility I think.

Cheers

---

### Post by Motorhead Kaze on 2008-09-10
This is long, sorry.

```

kaze@kaze-desktop:~$ sudo lshw
[sudo] password for kaze: 
kaze-desktop              
    description: Desktop Computer
    product: PROD00000000
    vendor: OEM00000
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=7605ED4C-E000-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: C51MCP51
       physical id: 0
       slot: &#65533;FDD
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/22/2006)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Sempron(tm) Processor 3400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          slot: Socket 940
          size: 2GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: 0.1
          bus info: pci@0000:00:00.1
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 1
          vendor: nVidia Corporation
          physical id: 0.2
          bus info: pci@0000:00:00.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:4 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 5
          vendor: nVidia Corporation
          physical id: 0.3
          bus info: pci@0000:00:00.3
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:5 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 4
          vendor: nVidia Corporation
          physical id: 0.4
          bus info: pci@0000:00:00.4
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master
          configuration: latency=0
     *-memory:6 UNCLAIMED
          description: RAM memory
          product: C51 Host Bridge
          vendor: nVidia Corporation
          physical id: 0.5
          bus info: pci@0000:00:00.5
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-memory:7 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 3
          vendor: nVidia Corporation
          physical id: 0.6
          bus info: pci@0000:00:00.6
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-memory:8 UNCLAIMED
          description: RAM memory
          product: C51 Memory Controller 2
          vendor: nVidia Corporation
          physical id: 0.7
          bus info: pci@0000:00:00.7
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-pci:0
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:1
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 3
          bus info: pci@0000:00:03.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: C51 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport-driver
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: RV370 5B60 [Radeon X300 (PCIE)]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: RV370 [Radeon X300SE]
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@0000:03:00.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress cap_list
             configuration: latency=0
     *-memory:9 UNCLAIMED
          description: RAM memory
          product: MCP51 Host Bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP51 LPC Bridge
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP51 SMBus
          vendor: nVidia Corporation
          physical id: a.1
          bus info: pci@0000:00:0a.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 module=i2c_nforce2
     *-memory:10 UNCLAIMED
          description: RAM memory
          product: MCP51 Memory Controller 0
          vendor: nVidia Corporation
          physical id: a.2
          bus info: pci@0000:00:0a.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP51 USB Controller
          vendor: nVidia Corporation
          physical id: b.1
          bus info: pci@0000:00:0b.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP51 IDE
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          logical name: scsi0
          logical name: scsi1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
        *-disk
             description: ATA Disk
             product: ST3320620A
             vendor: Seagate
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AA
             serial: 9QF4HNBB
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000080e3
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 1c4ac11b-5d1a-6043-b509-3c32251c7b2b
                size: 99GiB
                capacity: 99GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2008-01-20 19:47:52 filesystem=ntfs state=clean
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 5177MiB
                capacity: 5177MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2588MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2588MiB
                   capabilities: nofs
           *-volume:2
                description: EXT3 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: 94a6f017-1cdd-47c8-ae8d-f3c6667258ca
                size: 193GiB
                capacity: 193GiB
                capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-07-01 20:15:17 filesystem=ext3 modified=2008-09-10 17:37:35 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-09-10 17:37:35 state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: DVD DC DW1670
             vendor: BENQ
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/dvd
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 100
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=open
     *-ide:1
          description: IDE interface
          product: MCP51 Serial ATA Controller
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
     *-pci:3
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-multimedia
          description: Multimedia audio controller
          product: MCP51 AC97 Audio Controller
          vendor: nVidia Corporation
          physical id: 10.2
          bus info: pci@0000:00:10.2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a1
          serial: 00:e0:4c:ed:05:76
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.24.51 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 5
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: R120L0
             vendor: Maxtor 4
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: RAMB
             size: 114GiB (122GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=6441e136
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Super Hardrive!!!
                version: 3.1
                serial: e887f35b-a582-1e45-a1e8-df7f8e20322d
                size: 114GiB
                capacity: 114GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2003-08-17 08:10:56 filesystem=ntfs label=Super Hardrive!!! mount.fstype=fuseblk mount.options=rw,nosuid,nodev,noatime,relatime,user_id=0,group_id=0,allow_other state=mounted

```

---

### Post by Motorhead Kaze on 2008-09-10
Hello again. I think most of you in the US are asleep right now, but an Ubuntu pal just mentioned something about the possibility of this issue being related to my video card versus a vid lib related update that freaked out my card. Now that I think from this p.o.v. it is true that both times I upgraded and had this crash were since I have been running this particular ATI video card, and both times the desktop froze up after I upgraded, and I was using Kino at the time of the crash. 

What I wonder is, if it were the vid card versus a download, how can I know which upgrades I should stay away from? Did my vid card overload or something? The fact that everything works in fail safe mode does point to an upgrade does it not?

Well, I hope someone can come up with something I can check or do, otherwise it will be me reinstalling Hardy again tomorrow, and staying clear of updates.

Thanks in advance if you can help.

---

### Post by handydan918 on 2008-09-10
It kinda sounds like an issue with the xserver, so maybe you could try (from a console login) ```
sudo dpkg-reconfigure xserver-xorg
```

It might be interesting to select the vesa driver during that process rather than the Radeon driver, just to see if that might be a contributing factor...

---

### Post by Motorhead Kaze on 2008-09-10
Hello there.  Yes, I have gone through this reconfig process before, but lack the knowledge to answer some of the questions correctly. ...the first question is one that makes me say, "Huh?"

About the update manager, is there no way to find out which updates are not compatible with my computer's configuration? For example, looking at my graphics card, I should steer clear of update Lib ABC, etc.?

---

### Post by Motorhead Kaze on 2008-09-10
Hi again. I am back, and very sorry that I could not wait for "The" answer. I asked this question in July, and never got the issue worked out, and with this being where I work, I had to get this fixed...new install of Hardy.

However, I would like to say, that my deduction that the cause was due to an update somehow not working well with my computer, rather than blaming my ATI graphics card solely still stands. The reason is, last install things worked smoothly until I updated.  After that, the menu bars and desktop icons again became useless. For me, that ruled out blaming Kino too.  I re-reinstalled and the SAME thing happened upon applying the updates.  One more try and I left out all updates that applied to Compiz and most of the Gnome ones. This was not an educated guess, just a hunch.

Now, I have reinstalled, chose not to use the ATI driver offered me, added my couple lines of code to .gconf to get my dual monitors up and running, and did a limited update.  Things are cool so far.  Now, would someone in the know, please look at these updates which I did not accept and tell me if any of them would cause a computer with an ATI graphics card (and all the other specs listed above in the previous reply) would cause the problems I experienced (also detailed in this thread)?

Any of your expert advice would really help me out.

compiz
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
deskbar-applet
gdm
ALL updates beginning with "gnome-"
libdecoration0
libgnome-desktop-2
libgnome-window-settings1
python-gmenu

there were some other Gnome things I let go by, but it seems to me that anything compiz or gnome desktop may be related to my computer's wacked out behavior.  No?

Of course, one would also deduce then that because the internet and home would not function in KDE either, that Gnome would have zip to do with my problem right? Well I don't know do I?  Just trying.  "Gnome-panel-data" is my vote for a big ol' hmmm.

So again, I am only guessing.  Anyone knowledgeable in this area?

---

### Post by misswham on 2008-09-10
Funny the same thing happened to me last night.  Everything just froze on my desktop and I had to cut it off by the tower.  The same problem happened to me but when I rebooted everything was fine but I have had incredibly slow surfing speed for the past 10 days and I dont know whats up.  I always update because I assume the updates wont harm my pc.  I have Ubuntu on all 3 of my computers and they all are running the same even my pidgion wont stay on.  I notice that sometimes it logs itself off.  All of these issues are recent.

---


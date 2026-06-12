---
title: "Menu bars and overall look too big Ubuntu 9.04"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-12-30
II have restarted my PC with an other sound system connected to it .  Since that restart all my screens (Gnome display, Firefox displays, etc...) are a lot bigger and do not fit on my display anymore .  I have searche the Help that comes with Ubuntu, but I can not get the screens right again .  Can anybody help me please ? :(

---

### Post by Iowan on 2013-12-30
Has the resolution setting changed for the monitor? I use a KVM switch, and must reset the monitor when I switch back from one particular machine - which likes to lower the resolution.

---

### Post by monkeybrain20122 on 2013-12-30
Ubuntu 9.04?? It is a typo, right?

---

### Post by Hankbonk on 2013-12-30
Thanks for your quick reply Iowan .

I didn't change a thing, I only connected another sound system to the headphones outlet, I really do not understand how this can affect my display settings, can you ?  And how do I get a normally sized screen back ?

---

### Post by Iowan on 2013-12-30
Doesn't seem like it *should* have changed the display settings.  I'm trying to remember if 9.04 will let you access display settings by right-clicking the desktop, or if you need to go through a menu option. My monitor will tell me at what resolution it's running. I have a laptop that required dinking around with **xrandr** to get decent resolution.  Curiously, it worked fine on the previous Ubuntu version.

---

### Post by Hankbonk on 2013-12-30
Dear Iowan,

when I right click on the panel bar, I can access proprieties, so I did : I could reduce the pixels down to 19, but then I couldn't go down no more .  I must say there's a slight change : ther's a little bit more screen info on the display, but it's not what it used to be, far from that .  Anymore ideas ?

---

### Post by mörgæs on 2013-12-30
The warnings from your [previous thread]("http://ubuntuforums.org/showthread.php?t=2180523") deserve to be repeated. If we are talking of the same computer you should first of all convince the owner to install a supported release.

---

### Post by Impavidus on 2013-12-30
I am beginning to wonder, with the amount of tweaks and manual installations to get 9.04 properly running, can it still be called Ubuntu?

---

### Post by Hankbonk on 2013-12-30
Dear Mörgaes,

I allready tried to install 12.04 LTS, but got an input/output error over half of the installation off my self burned disk .  I tried it three times, without any success !

---

### Post by Iowan on 2013-12-30
Did you run the disk self-check?
Was that a DVD? As I recall, the standard Ubuntu won't fit a CD. 
(Or maybe you tried Lubuntu,.).

---

### Post by Hankbonk on 2013-12-30
Dear Iowan,

Idid not do a disk self-check on the burned DVD, no .  But now I discovered that I don't have the old  9.04 disk with me (my partner has it with him and is asleep) for insurance if I tried to burn 12.04 LTS again .  I will do that now, but you will have to explain me how you run that self-check, ok ?

---

### Post by Iowan on 2013-12-30
On live CD's (at least some I've used), when the CD boots, you have the option to check the CD for errors, try out the OS without installing, or install the OS from the CD.  It's been awhile since I loaded an OS, so I don't remember if the 12.04 live CD/DVD had that option.  As I recall, though, I burned a 12.04 CD - burner had no complaints, but it didn't copy all the files (CD too small). Besides not installing, it failed the MD5 test I belatedly checked.

---

### Post by Hankbonk on 2013-12-30
Now I get a surplus problem : the systems states that "there is no recordable disk inserted", but there is . I am starting to feel the urge of throwing the whole thing out on the street and demolish it  for good !!!

---

### Post by Hankbonk on 2013-12-31
I just got out the disk and threw it away !  Now my friend has been here and he will install RedHat on another partition, but that will be for the new year !

---

### Post by Bucky Ball on 2013-12-31
Red Hat is a whole different kettle of fish.

9.04? Very little chance you'd get much help or get it up anyhow, though.

What machine are you using? RAM, CPU? I have a feeling that if 9.04 is installed on it we are looking at an older machine that can possibly not deal with 12.04 anyhow. 

Have you tried with a lighter flavour? Xubuntu or Lubuntu might do the trick. Also, if they don't work with the desktop ISO, try the alternate. Could be probs with graphics further down the track.

You are burning the disk correctly? Download ISO>burn disk image>boot from install media? Seems obvious but just asking ... ;)

FYI: 9.04 hasn't been supported since October 2010. If you did get it running it would be a security risk and a vulnerable machine that probably shouldn't be online. It hasn't had security updates (or anything else) in over three years and there are none forthcoming.

---

### Post by Hankbonk on 2014-01-05
Dear Forum members,

I'm still running under ubuntu 9.04 Jaunty (my PC is too old for 12.04 LTS) . 

The new problem I got now is that the GNOME displays the standard items too big : 
   - Cursor pointer
   - All menu bars (Firefox, standard main menu bar on top of the screen, standard bottom bar, and so on ...)

These settings changed overnight when I installed another sound system to my headphones output and restarted the PC .

Is there any "old" guy that has a lot of experience with the ubuntu 9.04 GNOME in this forum that has any idea where and how I have to get the GNOME display to be at its old, standard output size ?

Thanks in advance for your replies,

Henk .

---

### Post by mörgæs on 2014-01-05
Threads merged.
Please don't create new threads dealing with the same or a closely related topic.

Your best option is reading Bucky's advice in post #15.

---

### Post by Hankbonk on 2014-01-05
Dear Mörgaes,

   I must apologize for creating a new thread .  I hope I did not offend you too much .  The only explanation is my bad memory, I am a recovering alcoholist that is sober for over three years now, but I still have big problems with my short term memory .

  I will reply on Bucky's reply now .

---

### Post by Hankbonk on 2014-01-05
Dear Bucky Ball,

   We did start the RedHat Linux installation but did not end it because of errors while installing .  So I'm still running ubuntu 9.04 jaunty .  I have had success in installing ubuntu 12.04 LTS on a different partition, but it runs too slow and with lots of faulty screen output (blinking, terminal window becomes transparent or whitens out, and so on...) and difficulties with the software center (I tried to install Steam, but could not fin it anymore on my system) .

My systems specs are :
```

*-cpu
          description: CPU
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.4
          slot: Slot A
          size: 1050MHz
          width: 32 bits
          clock: 100MHz

*-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 256KiB
             capacity: 2MiB
             capabilities: synchronous external write-back

 *-memory
          description: Flash Memory
          physical id: 20
          slot: System board or motherboard
          size: 768MiB

*-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display
                description: VGA compatible controller
                product: NV20 [GeForce3 Ti 200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
           *-cdrom:0
                description: CD-R/CD-RW writer
                product: CD-R   PX-W2410A
                vendor: PLEXTOR
                physical id: 0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: WDC WD800BB-00CA
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 17.0
                serial: WD-WMA8E3750229
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=e760e760
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: fc64dbd0-ad52-c24c-a471-ebfbf6b1449d
                   size: 31GiB
                   capacity: 31GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-08-15 21:02:16 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 41GiB
                   capacity: 41GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: W95 FAT32 partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 29GiB
                 *-logicalvolume:1
                      description: W95 FAT16 (LBA) partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 10001MiB
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 2384MiB
                 *-logicalvolume:3
                      description: Linux swap / Solaris partition
                      physical id: 8
                      logical name: /dev/sda8
                      capacity: 172MiB
                      capabilities: nofs
           *-cdrom:1
                description: DVD reader
                product: DVD Writer 100j
                vendor: HP
                physical id: 1
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /media/WOESTIJNVIS_10J
                version: 1.34
                serial: EHP      DVD Writer 100j 1.34011016CN1C6028
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /media/WOESTIJNVIS_10J
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 10
             serial: 00:40:f4:42:e3:48
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-storage
             description: Mass storage controller
             product: HPT366/368/370/370A/372/372N
             vendor: HighPoint Technologies, Inc.
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: scsi2
             logical name: scsi3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=pata_hpt37x latency=120 maxlatency=8 mingnt=8 module=pata_hpt37x
           *-disk:0
                description: ATA Disk
                product: IBM-DTTA-371440
                vendor: IBM
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: T71O
                serial: WK0WK0S2138
                size: 13GiB (14GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000c2a24
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: c1be0eb4-6948-4207-9971-09f04b714deb
                   size: 12GiB
                   capacity: 12GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2013-12-22 01:24:16 filesystem=ext3 modified=2014-01-05 06:06:01 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-01-05 06:06:01 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 627MiB
                   capacity: 627MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 627MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: Maxtor 2B020H1
                vendor: Maxtor
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdc
                version: WAH2
                serial: B17RTAYE
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00073222
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdc1
                   version: 1.0
                   serial: f6890bff-44df-407f-adbd-4c6203ee636d
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2013-12-31 15:10:11 filesystem=ext4 lastmountpoint=/arget modified=2014-01-03 18:17:08 mounted=2014-01-04 00:40:58 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@3:0.0.0,2
                   logical name: /dev/sdc2
                   size: 766MiB
                   capacity: 766MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdc5
                      capacity: 766MiB
                      capabilities: nofs
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:14:f7:3d:a5:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

This is a lot off information from the lshw command, hope you find everything you need .
I do think too that with this dinosaur of a PC ubuntu 12.04 LTS can not run properly, so I leave it on the HD partition and use my old ubuntu 9.04 again with that screen output problem (from another partition).

What do you or anyone else suggest that I do ?

---

### Post by mörgæs on 2014-01-05
Correct, Ubuntu will never work. The **NV20 [GeForce3 Ti 200]** screen card is too weak.

There are two options worth considering: Lubuntu 13.10 and Bodhi Linux. How do they behave in a live boot?

(By the way, it's an interesting rig. Three small hard disks...)

---

### Post by Hankbonk on 2014-01-05
Dear Mörgaes, 
I hoped you could help me restoring my display in Ubunu 9.04, because a game that I regularly play also appears too big on the screen, so I can't check some checkboxes in the game simply because they are not on the screen .  I will try out your suggested Linux versions later, thank you for that information .

---

### Post by Hankbonk on 2014-01-05
Dear Mörgaes,

I have installed Lubuntu 13.10 Saucy Salamander : It runs almost as slow as the Ubuntu 12.04 LTS and gets a lot of internal errors while running !  I quickly decided to leave it as it is and use my Ubuntu 9.04 Jaunty again, which runs far more quicker but still has that display size problem, which I really would like to see solved .  So please, can anyone help me out on the screen size problem I have on the Ubuntu 9.04 Jaunty, ok ?

---

### Post by mörgæs on 2014-01-05
Sorry, I don't know about settings specific for 9.04. 

You are of course welcome to wait and see if a solution to the problem comes up, but I guess most people have forgotten about that old hard- and software.

---

### Post by mc4man on 2014-01-05
If you use google site search & some relevant search terms maybe you can pick up on some useful jaunty/9.04 info from the archives (not search-able from forum search

"These settings changed overnight when I installed another sound system to my headphones output and restarted the PC ."
If that was the cause then what did you install & how (did it alter an xorg.conf?, ect.

Not sure why you threw out the jaunty cd, seems you have the time & space, just install 9.04 to some free space, enable the old-release repos so you can update/install stuff & don't "installed another sound system" or possibly pay closer attention to what is  to happen

Old release images are available here, if you don't know how to enable the old-release repos, ask, I'm sure many do.. (you may also be able to use 9.10 or 10.04, both better than 9.04
[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by Hankbonk on 2014-01-05
I finally have been able to change the resoluiotn setting of my display : Under System>Preferences I clicked Display and then the system told me that the standard tool in ubuntu was not complete and if I wanted to run the graphics driver vendor's tool instead, which I answered with <Yes> .  There, after clicking different options, I finally got one where the screen resolution could be altered, which I did : Now the whole screen has shrunk a little too much, but I can run that game now with all possibilities available ! Thanks for your efforts everybody, I will close this thread now !

---


---
title: "Asus A2500h with SIS 65x/M650/740 graphics"
date: 2016-02-12
forum: New to Ubuntu
---

### Post by Graham_Barlow on 2016-02-12
Hi my first time in a forum.
                        Ubuntu 14.04 wont install on old Asus A2500h laptop
                        

Xubuntu 14.04 i386, installation stops at “configuring bemwl – kernal – source (i386 )” and won't finish installing. If I try 64bit version, it reports I need a version for i686 cpu
 Have tried puppy, zoran and other version and non of them will work properly in this laptop.
 I have Ubuntu Mate running on 2 desktop machines and Ubuntu running on other laptops, they all perform beautifully.  
  This machine can run XP and a lite 7 but I don't want to be tied down to MS, any suggestions please

---

### Post by Vladlenin5000 on 2016-02-12
Hi and welcome.

Others might have other suggestions but I wouldn't be wasting my time with such machine.
It has a SiS integrated Graphics chip, one of worse ever invented, barely works with Windows and has known unresolved issues with any Ubuntu newer than 12.04.
Plus the maximum RAM at 1GB (256MB was the factory standard configuration) limits a lot what you can do with it in this day and age.

---

### Post by Graham_Barlow on 2016-02-12
Thanks Vladlenin5000
I'm setting up any PC's i can get cheap, for demos to show other "Oldies" how to save buying a new computer and have noticed the problems you mentioned, might have to give up on it.

---

### Post by corbin.loftis on 2016-02-12
You might try downloading an older unsupported version of Ubuntu if you're just going to use it for demonstration. Older versions may be lighter on the resources.

---

### Post by mörgæs on 2016-02-12
We need to know the hardware details.

Running any kind of Linux distro, supported or not, please execute 
```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Mr._Hope__Change on 2016-02-12
> **Vladlenin5000 said:**
> Hi and welcome.

Others might have other suggestions but I wouldn't be wasting my time with such machine.
It has a SiS integrated Graphics chip, one of worse ever invented, barely works with Windows and has known unresolved issues with any Ubuntu newer than 12.04.
Plus the maximum RAM at 1GB (256MB was the factory standard configuration) limits a lot what you can do with it in this day and age.

I wonder if Lubuntu would work considering the GPU and RAM limitations?  It may be worth a try.

---

### Post by haplorrhine on 2016-02-12
In one instance, I had to install an earlier version and update to the current.  You might need to use ethernet or else separately download some wlan drivers before you can connect to update.

---

### Post by Graham_Barlow on 2016-02-12
Thanks mörgæs
 
 
   I installed Ubuntu 11.10 and tried your terminal input ( copy and past ) but got no results, so uninsulated ubuntu.    Have installed  Lubuntu 15.10 again, this time with out selecting to upgrade and apart from videos not working too well, it may be the best I can expect from this machine.
 I have again run your terminal input and received the same result
 ```
graham@graham-A2H-L:~$ sudo lshw -sanitize > lshw.txt
 [LEFT][sudo] password for graham:  [/LEFT]
 graham@graham-A2H-L:~$
```
 
 
 I'm just starting to try to use a terminal and so far have not had a lot of success. I did put my password in after hitting enter and tried doing the whole thing again in a new terminal, no luck
 
 
 I also read through your Bringing [old hardware]("http://ubuntuforums.org/showthread.php?t=2130640") back to life.  Thank you

Udate
I found this  lshw.txt file, i think this is what you asked for
```
computer
    description: Computer
    width: 32 bits
    capabilities: smbios-2.3
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1982MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 2800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: 650/M650 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 80
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:e8000000-ebffffff
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=4096) memory:e7800000-e7ffffff memory:f0000000-febfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller cap_list
                configuration: latency=0
                resources: memory:f0000000-f7ffffff memory:e7800000-e781ffff ioport:d800(size=128)
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO] LPC Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 14
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2/3 SMBus controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0
             resources: irq:0 ioport:e600(size=32)
        *-firewire
             description: FireWire (IEEE 1394)
             product: FireWire Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.3
             bus info: pci@0000:00:02.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list rom
             configuration: driver=firewire_ohci latency=32 maxlatency=12 mingnt=4
             resources: irq:17 memory:e7000000-e7000fff memory:7e000000-7e01ffff
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_sis latency=32
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:b800(size=16)
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=32 maxlatency=11 mingnt=52
             resources: ioport:b400(size=256) ioport:b000(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: SiS7012 AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=32 maxlatency=11 mingnt=52
             resources: irq:18 ioport:a800(size=256) ioport:a400(size=128)
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:9 memory:e6800000-e6800fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:21 memory:e6000000-e6000fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=32 maxlatency=80
             resources: irq:22 memory:e5800000-e5800fff
           *-usbhost
                product: OHCI PCI host controller
                vendor: Linux 4.2.0-27-generic ohci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.02
                capabilities: usb-1.10
                configuration: driver=hub slots=2 speed=12Mbit/s
              *-usb
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: PixArt
                   physical id: 1
                   bus info: usb@4:1
                   version: 1.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
        *-usb:3
             description: USB controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=32 maxlatency=80
             resources: irq:23 memory:e5000000-e5000fff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.2.0-27-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.02
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Generic USB device
                   product: 802.11 n WLAN
                   vendor: Ralink
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.01
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
              *-usb:1
                   description: Mass storage device
                   product: TransMemory
                   vendor: TOSHIBA
                   physical id: 4
                   bus info: usb@1:4
                   logical name: scsi2
                   version: 1.10
                   serial: [REMOVED]
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=480Mbit/s
                 *-disk
                      description: SCSI Disk
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      size: 955MiB (1001MB)
                      capabilities: partitioned partitioned:dos
                      configuration: logicalsectorsize=512 sectorsize=512 signature=0001d766
                    *-volume
                         description: Windows NTFS volume
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdb1
                         logical name: /media/graham/Toshiba 1Gb
                         version: 3.1
                         serial: [REMOVED]
                         size: 952MiB
                         capacity: 954MiB
                         capabilities: primary ntfs initialized
                         configuration: clustersize=4096 created=2016-01-07 07:46:32 filesystem=ntfs label=Toshiba 1Gb mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
        *-network:0
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: enp0s4
             version: 90
             serial: [REMOVED]
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10Mbit/s
             resources: irq:19 ioport:a000(size=256) memory:e4800000-e4800fff memory:7e020000-7e03ffff
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: irq:16 memory:80000000-80000fff ioport:1000(size=256) ioport:1400(size=256) memory:84000000-87ffffff memory:88000000-8bffffff
        *-network:1
             description: Network controller
             product: BCM4301 802.11b Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=b43-pci-bridge latency=32
             resources: irq:17 memory:e4000000-e4001fff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: FUJITSU MHT2060A
             vendor: Fujitsu
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0022
             serial: [REMOVED]
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=e90be90b
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 17GiB
                capacity: 17GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2016-02-02 18:35:28 filesystem=ntfs state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/graham/Data
                version: 3.1
                serial: [REMOVED]
                size: 8226MiB
                capacity: 8257MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2016-02-02 18:35:33 filesystem=ntfs label=Data mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 29GiB
                capacity: 29GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 27GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 2014MiB
                   capabilities: nofs
        *-cdrom
             description: DVD reader
             product: CDRW/DVD SBW-242
             vendor: QSI
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: UR01
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlx000db00304c3
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.2.0-27-generic firmware=0.29 ip=[REMOVED] link=yes multicast=yes wireless=IEEE 802.11bgn
```

Hope this is right ?

 
 
 Thanks to all for your input, you do a great job.  
 
 
 Graham

---

### Post by mörgæs on 2016-02-13
You're welcome. Good to see that you have 15.10 running.

What exactly is the problem with graphics now? 

By the way, if you change the thread title to Asus A2500h or similar there is a better chance that other people will find it.

---

### Post by Graham_Barlow on 2016-02-13
I think i'm going to have to admit that this computer is never going to  be any good as a demo to show of Linux distros but as what may happen  with old computers.
I reinstalled Lubuntu 15.10 and set it for  security updates only and it seemed that it would work for very basic  every day internet browsing and a word doc or 2, until i switched it on  the next day, when it booted up, it had changed the monitor settings  from 1024x768 to 640x 480, which meant i can't get to the window control  buttons up in the right hand corner and photos and videos are way to  big, not much good for a demo!
I even tried a 10.04 version and this was no better.
So I&#8217;ve learnt a lot about installing and repartitioning if nothing else

Cheers to those who offered help.

By the way, where do i find out how to change the thread title, I can't find any info on doing this.

Graham

---

### Post by Geoffrey_Arndt on 2016-02-14
Another distro, even lighter than Lubuntu by quite a bit, is antix . . . . check it out at Distrowatch.com.     If you time, it seems worth a shot imho.

---

### Post by mörgæs on 2016-02-14
I think it's too early to give up. I don't know this particular SIS processor, but there is some advice for related graphics processors here:
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

Adding an xorg.conf often does the trick, as can be seen in the thread.

Another one is here: 
[https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+question/145098](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+question/145098)

If you edit the initial post and choose 'advanced' you will get the option of changing the title. *Asus A2500h with SIS 65x/M650/740 graphics* is probably better.

---

### Post by gordintoronto on 2016-02-14
With 2 GB of memory, everything should work, but it might be gruesomely slow. I would stick with a current OS, either Lubuntu or Xubuntu.

---

### Post by Graham_Barlow on 2016-02-14
Hi Geoffrey,  I have just now downloaded MX-15 and installed it in the Asus laptop, what a great OS, so much packed in, it installed and ran quite good, as to be expected the videos slow down every thing and vlc player has audio and no video but the OS does work, i have to give you that. I'm really looking for distros that old folks can install and use easily, as in ubuntu and linux mint installations. Any way, thanks for your info, I'm tempted to use it on my main pc.

Morgaes, I'm working my way through links but may be getting out of my depth as i am not that good at the terminal, will keep going though, have changed the title, thanks.

Cheers
  	[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1973436")

---

### Post by mörgæs on 2016-02-15
Thanks for changing the title. 
The second link I posted requires very little terminal exercise. Most of it is copy-paste.

---

### Post by Graham_Barlow on 2016-02-16
Installed Xubuntu 12.04  Success !!!
 
 
 Some success with the Asus A2500h laptop
 After going through [http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)[COLOR=#000080] [/COLOR][COLOR=#000080][COLOR=#000000]again, I noted that "[/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]Up to and including 12.04 there was no problem [/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]with SIS video cards[/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]" [/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]so I installed [/COLOR][/COLOR][COLOR=#000080][COLOR=#000000] Xubuntu 12.04.[/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]1 i386 and it installed and performed quite well, where as 14.04 would not even install. The built in media player, Parole, won,t show video but when i installed VLC media player the videos work. Given it's age performance is quite good over all.[/COLOR][/COLOR]
 [COLOR=#000080][COLOR=#000000]It's reporting that there are 474 updates available, going on my previous run of updating [/COLOR][/COLOR][COLOR=#000080][COLOR=#000000]other versions and losing the resolution and other problems, I'm going to leave this version "as is", after all it is only running as a  demo machine.[/COLOR][/COLOR]
 
 
 [COLOR=#000080][COLOR=#000000]Mörgæs  I don't have enough experience with terminal work to understand just what is being done in [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+question/145098](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+question/145098)  even though you said It's mostly copy & past, " add the text above to the file" is where i get lost, perhaps there is a more detailed tutorial some where for newcomers ?[/COLOR][/COLOR]
 
 
 [COLOR=#000080][COLOR=#000000]Thanks to all for your input.[/COLOR][/COLOR]
 
 
 [COLOR=#000080][COLOR=#000000]Cheers [/COLOR][/COLOR] 
 [COLOR=#000080][COLOR=#000000]Graham[/COLOR][/COLOR]

---

### Post by mörgæs on 2016-02-17
Hi, just create and save a file with the contents as shown here. Remember the TAB before the indented lines. 
Post again when that is done.

```
Section "Device"
    Identifier    "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
    Driver    "sis"
    BusID    "PCI:1:0:0"
EndSection


Section "Monitor"
    Identifier    "Plug and play"
    Option    "DPMS"
    HorizSync    30-69
    VertRefresh    50-120
EndSection


Section "Screen"
    Identifier    "Default Screen"
    Device    "Silicon Integrated Systems (SiS) 65x/M650/740 PCI/AGP VGA Display Adapter"
    Monitor    "Plug and play"
    DefaultDepth    24
    SubSection "Display"
        Depth    24
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


Section "ServerLayout"
    Identifier    "Default Layout"
    Screen    "Default Screen"
EndSection


Section "DRI"
    Mode    0666
EndSection

```

---

### Post by Graham_Barlow on 2016-02-17
Ok, Morgaes,   I'm back with Lubuntu 15.10  installed in the Asus A2500h, videos and every thing was working well and when rebooted it is now in the 640X480 resolution. I have a text file with the exact copy of your file from your last post ready on the desktop.
I then copied      	 	 	 	   	 	 	 	   	 	 	 	         	 	 	 	   [LEFT][SIZE=3]gksudo gedit /etc/X11/xorg.conf  into the terminal and it showed ```
   	 	 	 	[/SIZE][SIZE=3]   
[/SIZE][SIZE=3]To run a command as administrator (user "root"), use "sudo <command>".
[/SIZE][/LEFT][SIZE=3] [/SIZE][LEFT][SIZE=3]See "man sudo_root" for details.
[/SIZE][/LEFT][SIZE=3] [/SIZE][LEFT][SIZE=3]graham@graham-A2H-L:~$ gksudo gedit /etc/X11/xorg.conf
[/SIZE][/LEFT][SIZE=3] [/SIZE][LEFT][SIZE=3]graham@graham-A2H-L:~$
``` 
[SIZE=2]What now ?
Sorry I'm making a mess of this font size. Never been on a forum before.[/SIZE]
[/SIZE]
[/LEFT]

---

### Post by mörgæs on 2016-02-19
The error message means what it says: Use sudo in stead of gksudo.

If the file is created correctly you just copy it to the right location using the command ```
sudo cp <pathToFile> /etc/X11/xorg.conf
```

---


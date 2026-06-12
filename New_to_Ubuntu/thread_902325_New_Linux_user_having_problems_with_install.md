---
title: "New Linux user having problems with install"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Finger78 on 2008-08-27
Hello, I have been trying to install Linux for close to a week now and have had a multitude of problems and I'm still stuck.

For a full read on what my problems are/have been and what steps I've already taken here is a link to another forum post to help any that think they can.

[http://kubuntuforums.net/forums/index.php?topic=3097043.0](http://kubuntuforums.net/forums/index.php?topic=3097043.0)

Long story short, I've finally managed to install Linux (Tried Ubuntu, Kubuntu, Linux Mint) and they ALL have the same issue:

Once the install is completed (by choosing the "use entire disk" method form the installer) when the system goes to boot up without the CD for the first time it brings up the splash screen and appears to be loading (bouncing bar) it just freezes with no HD activity (via the HDD light on the front of the computer) and then after a few minutes I get the message:

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)"

This is where I am stuck at with the Ubuntu based distros, now I have no coding experience and no Linux knowledge so please, any help that can be offered either give detailed instructions or a link with some.

Also, I have been trying to find any info at all on suggested BIOS settings but have been unsuccessful in my search. I urge you to read the posts in the link I provided to help avoid any backtracking.

My system specs:
AMD Opteron 165 Dual Core
Asus A8N32 SLI Deluxe (Most current BIOS)
2g Corsair XMS Ram DDR1
Soundblaster X-Fi Xtreme Music (PCI)
EVGA nVidia 8800 GTS 640mb (PCI-E)
24in Acer Widescreen LCD Monitor (Model P243W, DVI connection)
Logitech G15 USB Keyboard (older model)
Logitech G5 USB 2000dpi Mouse
Asus generic Webcam USB (came with an Asus ATI X800 Pro card)

3 Hard Drives:

250g SATA WD with Windows Vista Home Premium x86 (32bit)Installation on it
320g IDE WD (The entire drive is available for Linux install)
400g SATA USB WB External also for storage

(Note, all HD's removed/disconnected during the installation except the 320g IDE, I am attempting to use the entire disk for install)

I am begging for some help, no one seems to know what to do or try next and I genuinely would like to get to know and learn Linux and hopefully be able to migrate from Windows permanently.

---

### Post by linuxguymarshall on 2008-08-27
At the beginning of the Ubuntu (or Kubuntu) live cd, hit F6 and type "acpi=off" then hit enter.

---

### Post by chronographer on 2008-08-27
Sounds very strange to me, I have never had an issue like this, I guess you haven't plugged the windows hdd back in afterwards? (which would be bad!)

I personally have no fear of linux deleting windows, and would heartily recommend that you try to install ubuntu with all your hdds in. just be careful to only format the drives you have to, and that you know which hdd is which (i.e. sda may be vista, sdb may be linux, or whatever.) If you get onto Ubuntu IRC (google search to find out how) pose your question concisely and someone will help you in real time.

Stick with it, i am a recent convert (2-3 years) and love it, although Windows just works for games, Linux works for productivity IMHO.

If you want to learn a lot about Linux, install debian without GUI (no gnome), then have fun getting a GUI up and running! I did this on a laptop and it really gets you understanding the important components, and improves confidence in the command line (which is ultra powerful and cool!)

good luck,

agl

---

### Post by forger on 2008-08-27
1) Is it Ubuntu or Kubuntu that you have installed currently?
2) Are you using the latest [COLOR="Red"]**8.04.1**[/COLOR] release? (Not 8.04 or older)
3) Did you put/connect all your hard drives after you installed ubuntu? (Maybe that's the problem, it can't find the correct partition)

---

### Post by Finger78 on 2008-08-27
> **linuxguymarshall said:**
> At the beginning of the Ubuntu (or Kubuntu) live cd, hit F6 and type "acpi=off" then hit enter.

As posted in my link I have already tried numerous boot line commands with no results

Currently I have Kubuntu installed, but as I said I have tried 3 separate distros and all have had the same result. (all with fresh formatting via Gparted)

As for learning the coding, I'd like to do that at a slower pace and having a GUI to help guide me and make the transition to Linux from Windows less of a culture shock.

As for the Distros I have tried:

kubuntu-8.04.1-desktop-i386
LinuxMint-5-XFCE-BETA-025
ubuntu-8.04.1-desktop-i386

During installation only the 320g HD is connected, then after it finishes it asks to reboot, then after reboot it gets stuck during the loading splash screen. No hard drives have been connected/disconnected between the reboot prompt and actual reboot, only the CD is removed (ejected by Linux prior to reboot)

For specifics on the install steps I've taken I again urge you to read my posts from the link I provided.

---

### Post by forger on 2008-08-27
can you boot from live cd and execute these commands in Applications > Accessories > Terminal:
```

lspci
lsusb
sudo lshw -C disk -C storage
```

---

### Post by Finger78 on 2008-08-27
Since I'm unsure of the expected outcome of these commands are I will post the resulting info here.

I'm assuming that the ubunutu@ubuntu Shell Konsole is what you mean... (didn't see a path as you described it)

If this was supposed to fix something please let me know, I haven't re-tried to boot up but again I'm not sure what I was supposed to do with the commands or the resulting info outside of entering it into the Terminal.

NOTE: I left the 400g External Plugged in during these tests

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
04:08.0 Multimedia audio controller: Creative Labs SB X-Fi
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 006: ID 046d:c222 Logitech, Inc.
Bus 002 Device 005: ID 046d:c221 Logitech, Inc.
Bus 002 Device 004: ID 046d:c041 Logitech, Inc.
Bus 002 Device 003: ID 046d:c223 Logitech, Inc.
Bus 002 Device 002: ID 05a9:8519 OmniVision Technologies, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1058:0900 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 0000:0000
```

```
ubuntu@ubuntu:~$ sudo lshw -C disk -C storage
  *-storage
       description: Mass storage controller
       product: SiI 3132 Serial ATA Raid II Controller
       vendor: Silicon Image, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress bus_master cap_list
       configuration: driver=sata_sil24 latency=0 module=sata_sil24
  *-ide:0
       description: IDE interface
       product: CK804 IDE
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: scsi2
       logical name: scsi3
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-disk
          description: ATA Disk
          product: WDC WD3200AAJB-0
          vendor: Western Digital
          physical id: 0
          bus info: scsi@2:0.0.0
          logical name: /dev/sda
          version: 00.0
          serial: WD-WCARW5746059
          size: 298GiB (320GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=d291429b
     *-cdrom
          description: DVD-RAM writer
          product: CD/DVDW SH-S182M
          vendor: TSSTcorp
          physical id: 1
          bus info: scsi@3:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/dvd
          logical name: /dev/scd0
          logical name: /dev/sr0
          logical name: /cdrom
          version: SB03
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
        *-medium
             physical id: 0
             logical name: /dev/cdrom
             logical name: /cdrom
             configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-ide:1
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
  *-ide:2
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 11
       bus info: pci@0000:00:11.0
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
  *-scsi
       physical id: 5
       bus info: usb@1:2
       logical name: scsi8
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
     *-disk
          description: SCSI Disk
          product: 4000KS External
          vendor: WD
          physical id: 0.0.0
          bus info: scsi@8:0.0.0
          logical name: /dev/sdb
          version: 101a
          serial: WD-WMANU1014732
          size: 372GiB (400GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=4 signature=e93a112c
```

---

### Post by Finger78 on 2008-08-27
I tried to boot up after my last post and still the same issue.

I am re-running the commands after unhooking the 400g External to make sure it didnt taint any results you might have needed to see.

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:0a.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a4)
00:0a.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:0f.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:10.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:11.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:12.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:13.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:16.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:17.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
04:08.0 Multimedia audio controller: Creative Labs SB X-Fi
04:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

```
ubuntu@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 046d:c222 Logitech, Inc.
Bus 001 Device 005: ID 046d:c221 Logitech, Inc.
Bus 001 Device 004: ID 046d:c041 Logitech, Inc.
Bus 001 Device 003: ID 046d:c223 Logitech, Inc.
Bus 001 Device 002: ID 05a9:8519 OmniVision Technologies, Inc.
Bus 001 Device 001: ID 0000:0000
```

```
ubuntu@ubuntu:~$ sudo lshw -C disk -C storage
  *-storage
       description: Mass storage controller
       product: SiI 3132 Serial ATA Raid II Controller
       vendor: Silicon Image, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: storage pm msi pciexpress bus_master cap_list
       configuration: driver=sata_sil24 latency=0 module=sata_sil24
  *-ide:0
       description: IDE interface
       product: CK804 IDE
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: scsi6
       logical name: scsi7
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-disk
          description: ATA Disk
          product: WDC WD3200AAJB-0
          vendor: Western Digital
          physical id: 0
          bus info: scsi@6:0.0.0
          logical name: /dev/sda
          version: 00.0
          serial: WD-WCARW5746059
          size: 298GiB (320GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=d291429b
     *-cdrom
          description: DVD-RAM writer
          product: CD/DVDW SH-S182M
          vendor: TSSTcorp
          physical id: 1
          bus info: scsi@7:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/dvd
          logical name: /dev/scd0
          logical name: /dev/sr0
          logical name: /cdrom
          version: SB03
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
        *-medium
             physical id: 0
             logical name: /dev/cdrom
             logical name: /cdrom
             configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-ide:1
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
  *-ide:2
       description: IDE interface
       product: CK804 Serial ATA Controller
       vendor: nVidia Corporation
       physical id: 11
       bus info: pci@0000:00:11.0
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv
```

---

### Post by forger on 2008-08-27
I thought you had some piece of hardware that wasn't detected..
I'm out of ideas unfortunately :(

Since it happened with various ubuntu releases, I'd suggest to start trying out other non-ubuntu distros, such as [PCLinuxOS]("http://www.pclinuxos.com/") or [opensuse]("http://www.opensuse.org")

---

### Post by Finger78 on 2008-08-27
ERUEKA!

Well through the hundred of pages of forum posts and websites/tutorials I've read through I decided to try a few things while I was in the mood to work on this issue.

First I tested the jumper settings:
First tried removing the jumper on the HD from "cable select" to "master/single" Neither seemed to make any difference.

Then I decided to try something I read and thought was WAY beyond a long shot (even the poster said it was unlikely a cause) but I changed the connection it used on the IDE cable form the top uppermost connection to the middle connection (still had the jumper set for master) and BAM! Booted into Kubuntu within 10 seconds.

I will now turn off yet again to A: reset the drive to a safe position within the computer and B: replace the "cable select" jumper settings to ensure thats not part of the issue.

Could someone tell me how to PROPERLY have a dual boot system since I installed this without any other HD's connected? I'd prefer that Windows remain on top of the boot option (as for now I will still be using it a lot until I figure out how to migrate most of my programs over or find equivilent ones.

Now, since I have someones attention hopefully could someone give me a rundown on how I go about getting the latest drivers for my video and sound cards? And maybe a link on trying to get a network set up (I'm assuming that Windows and Linux can communicate on a network somehow, would that be correct?)

I know the replies to this post didnt lead to the hopeful resolution of this problem but I do greatly appreciate the quick responses and I hope to be able to pick your collective brains and get to know Linux!

---

### Post by Michael.Godawski on 2008-08-27
well
concerning the drivers question

if ubuntu ( or kubuntu ) does not support your hardware out of the box then a quick look into the 
administration > hardware drivers 
should tell you if there are disabled drivers you may want to download

if not and everything is working be happy.

For the network issue have a look at Samba:
[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by Finger78 on 2008-08-27
I guess Linux saw my need for my video driver and prompted me when I rebooted to install it lol.

Just to confirm the jumper is now set to "cable select" and still functions as expected.

---

### Post by Finger78 on 2008-08-27
I'm looking for the most current video drivers and audio drivers, now I'm downloading the only version of drivers for my audio from Creative but on the nvidia page it has multiple listings and I'm unsure which to choose.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Any suggestions?

---

### Post by silverglade00 on 2008-08-27
I would suggest using the hardware drivers program from System->Administration to install the driver. Quick, easy, and you don't have to reinstall every time a new kernel comes out.

---

### Post by Finger78 on 2008-08-27
There is no audio on the hardware drivers program, and I'm unsure on how to go about checking the version of my video drivers.

Ok the only problems I'm having now is:

1: Trying to add a boot option into vista to let me select Kubuntu (these guides assume I've had all my HD's hooked up to recognize other OS's etc and I havent)

2: How to install my audio and video drivers I downloaded from the companies ( I do a lot of beta testing and having the current versions is crucial)

How to install Firefox (havent really dug into this yet, there may be a tutorial I can use for it)

---

### Post by TheMaxzilla on 2008-08-27
> **Finger78 said:**
> 
How to install Firefox

Boot into terminal and type in:
```
sudo apt-get install firefox
```

---

### Post by forger on 2008-08-28
> **Finger78 said:**
> 
1: Trying to add a boot option into vista to let me select Kubuntu (these guides assume I've had all my HD's hooked up to recognize other OS's etc and I havent)

2: How to install my audio and video drivers I downloaded from the companies ( I do a lot of beta testing and having the current versions is crucial)

How to install Firefox (havent really dug into this yet, there may be a tutorial I can use for it)

Firefox is already pre-installed in ubuntu 8.04.1

2. If you wish to try the "bleeding edge" of Ubuntu, you might want to try out the upcoming release, intrepid ibex:
[http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)
But I **warn** you, if you're inexperienced with commands, you **will suffer** (sometimes packages can break) - beta testing needs great knowledge on how to overcome problems.

1. I think this can be solved using the [supergrubdisk]("http://www.supergrubdisk.org/") which can help you fix your GRUB boot menu - on the right side you'll find various versions for floppy, usb and cdrom to download.

---


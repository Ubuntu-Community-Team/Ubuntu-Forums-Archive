---
title: "[SOLVED] New and new some help 8.10 instal troubles"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by iminhell on 2008-11-24
I didn't search yet, kick me later, but I'm having troubles.

I'm stuck in Ubuntu . I upgraded to the 8.10 version from the 8.04. I installed 8.04 from Windows, mounted the .iso with Daemon Tools and installed that way. With the 8.10 I burnt it to a disc and installed from the disc on startup (switch first boot device to cd-rom instead of HDD). I changed the boot priorities back to HDD then CD-ROM and restarted after install. Now Ubuntu loads right away with out giving me any choice if I want it or Windows to load (which is how I had it working before with 8.04, which btw I did not remove).

I need to know if I ****** up or how to get back to the boot menu I had so I can still load Windows. I don't see anything in BIOS that changed other than my manual changes.

Help 


-John


Searched and found this thread --> [http://ubuntuforums.org/showthread.php?t=948584&highlight=system+startup](http://ubuntuforums.org/showthread.php?t=948584&highlight=system+startup)
Not sure if that's what I'm looking for or not though.

---

### Post by halitech on 2008-11-24
open a terminal and post the response to```
sudo fdisk -l
```
thats a lower case L, not a 1

---

### Post by Olivier2371 on 2008-11-24
Which windows?

If you have xp or vista, you should have the disk. 

load the widows disk and you should have the option to repair the boot.

never mind halitech will be able to help you.

---

### Post by halitech on 2008-11-24
thats going to depend on if they even still have windows

---

### Post by iminhell on 2008-11-24
Windows XP (sp3) and I don't have a disc. It's a HP unit and all the factory info is on a locked partition of the HDD (accessible through system recovery).

Giving the terminal command a shot now, back in a bit.



[quote=terminal window]Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
[/quote]

---

### Post by Olivier2371 on 2008-11-24
He or she probably messed up the root of the disk.

I hope so!

---

### Post by halitech on 2008-11-24
well I'm hoping that as well but I guess we'll see shortly

---

### Post by iminhell on 2008-11-24
That quote I edited in is what was spit back at me. I don't know coding at all so it really means nothing to me. I'm assuming they are more commands to tell me the partition names to see what is where, but I'm not sure how to get that to spit out. Tried copy/paste but nothing.

---

### Post by halitech on 2008-11-24
did you do sudo fdisk -l (lower case L) or just sudo fdisk?

---

### Post by iminhell on 2008-11-24
Yup, I cut/pasted what you had there. Or was I supposed to take some spaces out?

---

### Post by halitech on 2008-11-24
are you in the installed version or on a live cd?

---

### Post by Olivier2371 on 2008-11-24
fdisk (space) -l

---

### Post by iminhell on 2008-11-24
Installed version


typed it in Oliver's way and it tells me:
[quote=terminal window]Cannot open /dev/sda[/quote]

---

### Post by iminhell on 2008-11-24
AH success!!


> john@john-desktop:~$ sudo fdisk -l
[sudo] password for john: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0af20af2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23589   189478611   83  Linux
/dev/sda2           23590       24321     5879790    5  Extended
/dev/sda5           23590       24321     5879758+  82  Linux swap / Solaris


---

### Post by Sorivenul on 2008-11-24
Nevermind, let's look at your output.

---

### Post by Sorivenul on 2008-11-24
Do you have more than one HD?  From your output it looks like the typical result of the "Use Entire Disk" option from the Ubuntu installer.

---

### Post by iminhell on 2008-11-24
[quote=command window]john@john-desktop:~$ sudo fdisk /dev/sda1
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x2ec9b4fe.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 23588.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): 

[/quote]


???

---

### Post by Olivier2371 on 2008-11-24
Apparently it is worse than though, he or she used the entire disk.

---

### Post by iminhell on 2008-11-24
He

... and hwat? 
This won't be good.

---

### Post by ndefontenay on 2008-11-24
Hi.

I think it's a terrible news but...

It seems you've installed Linux on the totality of your hard disk.
So the next questions will be:

1) Have you lost substantial information which were stored on windows? Which?

2) If yes, is it stored somewhere else

3) What do you use windows for? (because now that it's there, if you're not a gamer or having special software working only on windows, you could use only unbuntu)

What we can do now is try to help you recover your data if possible. And for the rest have you discover and enjoy linux anyway.

---

### Post by Olivier2371 on 2008-11-24
Do you have a recovery disc for your computer or a backup?

Is it a laptop or a desktop?

---

### Post by ndefontenay on 2008-11-24
Oh there's something which might have saved your data.

Since ubuntu 8.04, ubuntu detects your windows partition and copy the data from your documents (pictures, music etc...).

Have you been prompted for such information?

---

### Post by iminhell on 2008-11-24
It's a home PC and nothing as far as business. But I had about 15 movies I was waiting to burn to DVD, about 2,000 Repair manuals for automobiles (that is the real killer) and some pictures and such, oh and pirated programs some good ones too.


Thing that really sucks is I don't have a Windows disc.
Think I could cheat Vist off our laptop and get it to work?

I would use Ubuntu full time, but this computer is shared and my brother and mom wouldn't like this system. Actually I don't like it simply because I can't find anything, before my screw up that is, stuff from the windows side. That and I have no sound. Which is the whole reason I upgraded to 8.10, no sound with 8.04 and someone suggested upgrading may fix it, being none of the codec's would or drivers (SB live 24 bit btw).

Bad to worse I tell ya.

But ya recovery process please.

---

### Post by iminhell on 2008-11-24
> **ndefontenay said:**
> Oh there's something which might have saved your data.

Since ubuntu 8.04, ubuntu detects your windows partition and copy the data from your documents (pictures, music etc...).

Have you been prompted for such information?


Not that i recall.

---

### Post by iminhell on 2008-11-24
The file structure is just awkward for me. How can i check and see if something that say would have been, c:/users/profiles/john/desktop
may still be there?
Everything is named weird from what I'm used to, personal stuff wise.

---

### Post by ndefontenay on 2008-11-24
Yes.

There is a learning curve but that's nothing to be worried of.

On Linux there's no such things as C: D: and E: etc...

everything starts with / (root) then your data will be in /home/yourname

On the top left, you'll see 3 menus Applications Spaces and System.

Go the the spaces area and explore a bit.

If it's empty, the sad truth is that you have lost pretty much everything.

If you got an ipod, then your music (at least those you put on it) are secured. There are ways to get music back from ipod.

If your contacts are synchronized with ipod, these are secured too.

We will start gather the information back slowly.

If you got any other questions, let me know.

Stand back and relax.

Next thing you know you'll be showing off with Linux ^^

---

### Post by Olivier2371 on 2008-11-24
I would like to be optimistic but as far as I know when you told Ubuntu installer to use the entire space of the disk it normally format each partition.

The only real way that I can think off is by using forensic software, similar than what the internet police use to recover file from low level formated hard-drive.

But Ubuntu is fun to use.

tell me what type hard-drive do you have? (Maxtor,Seagate)

---

### Post by iminhell on 2008-11-24
Don't have an iPod, but thankfully all my music is on an external HDD, all 20,000+ songs.

So if I select -> places -> computer -> file system -> 
I should find something from the windows side if it where still there?
But I tried the same thing with the previous install and nothing showed up, though it was still there.
That's what has me confused.



But how do I go about this recovery process?

---

### Post by ndefontenay on 2008-11-24
Sorry. I didn't read the previous thread...

I'm not a vista guru and can hardly help you. If it's HP, the support should help you get it back. Since you should have a licence withit.

But they won't live any kind of space for a clean dual boot of linux.

The experience you are having not finding your way around is pretty common. It's called the "super user syndrom". You knew how to do things before and now you are lost.

It's likely your mom and sis won't like this either for the same reasons.

What are the apps you mention?

---

### Post by ndefontenay on 2008-11-24
Yes.

If you still had windows, you should have seen a disk called winXP or winVista in the spaces menu.

---

### Post by ndefontenay on 2008-11-24
For the sound problem, you mentioned, you simply can't hear anything (like the little jingle when gnome starts) or it's just a coded problem when you try to listen to mp3s?

---

### Post by Olivier2371 on 2008-11-24
If you are talking about the recovery using forensic software it is very technical.

But If you bought the pc from for example HP, you should have a recovery disk or at least the windows vista disk.

Give me the exact model of you pc.

---

### Post by pi.boy.travis on 2008-11-24
Sounds like you need to edit you GRUB configuration file to me.  Don't worry, it's easy.  Once we have your disk info, we can give you the commands.  In the mean time, check out: [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

EDIT:  OOPS, didn't read the thread in it's entirety.  My bad. . .  That is what I get for staying up so late. . . .

---

### Post by pi.boy.travis on 2008-11-24
OK, Now I read it ;)

If you had the Ubuntu installer use the entire disk, as it would appear, the entire Windows partition would have disappeared.  Gone.  Nowhere.  Obliterated.  This is because Linux uses a totally different filesystem than what Windows uses (FAT, NTFS, I haven't used Window sin a while. . . )  There isn't really any way to get that partition back.  If you think there is the possibility that the partition is intact, you can install the package: GParted, a partition editor, to look for it.

If you were to have Windows and Linux dual-booted on the same disk, they would be in separate partitions, and in order to see your Windows files, you would have to mount the partition.

As for your sound problem, we will need some more info.
.
If you don't hear anything at all, please run:
```
sudo lshw
```
and post the result.

If it is only certain files, than it is a codec problem.  If you tell us more about the files you want to play, we can help you install the proper codecs.

---

### Post by Olivier2371 on 2008-11-24
pi.boy.travis,

I am sure you would like to help but I would suggest you read the post  from the begining.

Since we already determined that the all disk as been used.

At the moment we trying to find out if he's got a recovery disk from the manufacturer or windows XP/Vista, so that we can reinstall windows.

---

### Post by iminhell on 2008-11-24
No sound what so ever. Here is what it spit out (notice no partition for Windows :()


[quote=terminal window]john@john-desktop:~$ sudo lshw
[sudo] password for john: 
john-desktop              
    description: Desktop Computer
    product: PJ509AA-ABA A720N
    vendor: HP Pavilion 061
    version: 0nB1211RE101KELUT00
    serial: MXK44011FQ NA440
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=404A8C50-720F-D911-975F-98AE182DB477
  *-core
       description: Motherboard
       product: Kelut
       vendor: ASUSTek Computer INC.
       physical id: 0
       version: 2.02
       serial: MB-1234567890
       slot: LPT1
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 3.15 (06/06/2005)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3200+
          vendor: Advanced Micro Devices [AMD]
          physical id: 5
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2200MHz
          capacity: 3GHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
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
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 2GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: KM400/KN400/P4M800 [S3 UniChrome]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 cap_list
                configuration: latency=32 mingnt=2
        *-display
             description: VGA compatible controller
             product: NV34 [GeForce FX 5500]
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
        *-multimedia:0
             description: Multimedia audio controller
             product: SB Audigy LS
             vendor: Creative Labs
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2 module=snd_ca0106
        *-firewire
             description: FireWire (IEEE 1394)
             product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
             vendor: VIA Technologies, Inc.
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=32 maxlatency=32 module=ohci1394
        *-ide:0
             description: IDE interface
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: scsi2
             logical name: scsi3
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_via latency=32 module=sata_via
           *-cdrom:0
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BL06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
           *-cdrom:1
                description: DVD-RAM writer
                product: DVDRW LH-20A1L
                vendor: LITE-ON
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /media/cdrom0
                version: BL06
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom1
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             logical name: scsi0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: ST3200822A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.01
                serial: 3LJ23G2M
                size: 186GiB (200GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0af20af2
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 6715043a-0b48-472a-ae5e-019df31296a9
                   size: 180GiB
                   capacity: 180GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-11-24 17:17:54 filesystem=ext3 modified=2008-11-24 20:43:12 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2008-11-24 20:43:12 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 5741MiB
                   capacity: 5741MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 5741MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-multimedia:1
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication UNCLAIMED
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:11:2f:8c:37:93
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.101 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
     *-scsi
          physical id: 1
          bus info: usb@4:1
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@4:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@4:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@4:0.0.3
             logical name: /dev/sde
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 82:32:16:0a:2e:8f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/quote]

---

### Post by iminhell on 2008-11-24
> **Olivier2371 said:**
> pi.boy.travis,

I am sure you would like to help but I would suggest you read the post  from the begining.

Since we already determined that the all disk as been used.

At the moment we trying to find out if he's got a recovery disk from the manufacturer or windows XP/Vista, so that we can reinstall windows.


I have no recovery disc for Windows.

Now that I think of it though I do have a HDD from an old lap top that I put in a case that does have Windows XP on it. I can probably run off that some how ... ?
Other than that I have no Windows disc's at all.



and I realize you probably didn't want that whole quote, but I wasn't exactly sure where to cut it at

---

### Post by Olivier2371 on 2008-11-24
No probs, 

Wait a minute while I check something.

---

### Post by Furat on 2008-11-24
Guys the Windows "recovery" disk will wipe every thing and reinstall vista so it will not return his data back , the only hope he has is Ubuntu import his documnets from Winows try 
> df -h 
because if Ubuntu import the files  you will have more than 10G of data in your "/"

---

### Post by iminhell on 2008-11-24
Nope. Looking at that Gdisc program there is only 5G used, previously I had 150G used. Yes I lost A LOT.
So I think it's pretty safe to say that is a lost cause, awe well. I am running of the install cd right now just in case though, read something that may help, try not to add new info to the hdd and such, might be able to get something back, dunno, can only hope.


Oh, and with a windows recovery cd I wouldn't loose anything but the user profiles. All the files are still intact, just disorganized some. had to do this couple times before, but it was from the boot screen and it ran off the partition, which is all gone now.

---

### Post by Olivier2371 on 2008-11-24
tell me is your computer    HP Pavilion a720n Desktop PC  

Secondly concerning the quote where you gave a lot of info did you have you external drive plugged as well?

---

### Post by pi.boy.travis on 2008-11-24
lshw would appear to have found your sound card (assuming "multimedia device?")

Try running alsamixer and checking the settings there?

I'll have to see what I can find out about that card. . . 

As for your lost data. . . Remember the #1 rule: Backup
I wouldn't recommend trying to boot, XP from that old drive on the new machine.  I have tried it myself, it hardly ever works.  I would recommend contacting your manufacturer for a new install disc.

---

### Post by iminhell on 2008-11-24
Yes, damn you're good :)
and no external plugged in at the moment, usb's are used be Mouse/keyboard and printer nothing else at the moment.

---

### Post by pi.boy.travis on 2008-11-24
So it's safe to say your sound problem is fixed? ;)

If you are interested, here is the basic guide to dual-booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

That is how I started out, but you may notice yourself using Windows less and less and less, until you decide to be rid of it for good!

---

### Post by Olivier2371 on 2008-11-24
this is an extract from your last big quote page 4 

-scsi
physical id: 1
bus info: usb@4:1
logical name: scsi4
capabilities: emulated scsi-host
configuration: driver=usb-storage
*-disk:0
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
*-disk:1
description: SCSI Disk
physical id: 0.0.1
bus info: scsi@4:0.0.1
logical name: /dev/sdc
*-disk:2
description: SCSI Disk
physical id: 0.0.2
bus info: scsi@4:0.0.2
logical name: /dev/sdd
*-disk:3
description: SCSI Disk
physical id: 0.0.3
bus info: scsi@4:0.0.3
logical name: /dev/sde

do you have a card reader with your printer?

If not what are all those disk?

Is your pc the HP Pavilion a720n Desktop PC?

I am at the moment on the HP website trying to figure out something that can help.

The reason why you do not have a recovery disc is because you had a hidden partion with the recovery on it, which you should have burnt on cd.

---

### Post by pi.boy.travis on 2008-11-24
> **Olivier2371 said:**
> this is an extract from your last big quote page 4 

-scsi
physical id: 1
bus info: usb@4:1
logical name: scsi4
capabilities: emulated scsi-host
configuration: driver=usb-storage
*-disk:0
description: SCSI Disk
physical id: 0.0.0
bus info: scsi@4:0.0.0
logical name: /dev/sdb
*-disk:1
description: SCSI Disk
physical id: 0.0.1
bus info: scsi@4:0.0.1
logical name: /dev/sdc
*-disk:2
description: SCSI Disk
physical id: 0.0.2
bus info: scsi@4:0.0.2
logical name: /dev/sdd
*-disk:3
description: SCSI Disk
physical id: 0.0.3
bus info: scsi@4:0.0.3
logical name: /dev/sde

do you have a card reader with your printer?

If not what are all those disk?

Is your pc the HP Pavilion a720n Desktop PC?

I am at the moment on the HP website trying to figure out something that can help.

He could have more than one disk in the machine, but with no fstab entries, so they would be treated like removable media by GVM.  Just my guess. . .

---

### Post by Olivier2371 on 2008-11-24
Here is what I found on hp site.

Try this.

Recovering during startup
Use the following steps to perform a recovery from the hard drive :

   1.
      Backup files from the My Documents folder and from other folders you may have created.
   2.
      Disconnect all connected devices (such as the Personal Media Drive, USB drives, printer, and fax), remove media from drives, and remove any recently added internal hardware. Do not disconnect the monitor, keyboard, mouse, and power cord.
   3.
      Turn on the computer.
   4.
      Just after the first screen appears (the logo screen), press the F10 key repeatedly until a recovery menu appears.
   5.
      Select one of the following procedures, depending on which recovery type you want to perform:
          *
            To perform a standard system recovery, click Next , and then click Yes .
          *
            To perform a destructive recovery, click Advanced , (select Destructive Recovery ) and then click Next .
            CAUTION: 	A destructive recovery will format the hard drive. This will delete all the information on the hard drive and reinstall Windows XP and the original software that came with the computer .
   6.
      Read and respond to each window and screen that appears.
   7.
      After the System Recovery is complete, the computer restarts and continues into Windows setup. Complete the setup screens and wait until the computer finishes the setup.

---

### Post by Olivier2371 on 2008-11-24
pi.boy.travis  	

Who know's, maybe god.

---

### Post by iminhell on 2008-11-24
> **pi.boy.travis said:**
> So it's safe to say your sound problem is fixed? ;)


No :(
I was just saying he did a good job reading through all that and finding what he needed (?).

Oh wait, ya. I got sound. Least I can watch movies again and hear them.


Thanks a lot you guys. I'll figure that thank you thing out and use it.
if you guys need help with cars, mechanical or other wise hit me up (only way I know I can repay the favor).

---

### Post by ndefontenay on 2008-11-24
It all seems to look better now :)

Before you completely ditch linux out of your computer.
Let your sis and mom give a try. 
Your lost apps could be replaced by others working on linux.

remember to backup things you can't afford to loose ^^

---

### Post by pi.boy.travis on 2008-11-24
> **Olivier2371 said:**
> Here is what I found on hp site.

Recovering during startup
Use the following steps to perform a recovery from the hard drive :

   1.
      Backup files from the My Documents folder and from other folders you may have created.
   2.
      Disconnect all connected devices (such as the Personal Media Drive, USB drives, printer, and fax), remove media from drives, and remove any recently added internal hardware. Do not disconnect the monitor, keyboard, mouse, and power cord.
   3.
      Turn on the computer.
   4.
      Just after the first screen appears (the logo screen), press the F10 key repeatedly until a recovery menu appears.
   5.
      Select one of the following procedures, depending on which recovery type you want to perform:
          *
            To perform a standard system recovery, click Next , and then click Yes .
          *
            To perform a destructive recovery, click Advanced , (select Destructive Recovery ) and then click Next .
            CAUTION: 	A destructive recovery will format the hard drive. This will delete all the information on the hard drive and reinstall Windows XP and the original software that came with the computer .
   6.
      Read and respond to each window and screen that appears.
   7.
      After the System Recovery is complete, the computer restarts and continues into Windows setup. Complete the setup screens and wait until the computer finishes the setup.

Not sure if this guide will be effective, considering the partition that is it retrieving from probably doesn't exist.  Even then, this would also destroy the GRUB configuration, and perhaps even the entire installation.  

If the recovery partition is there, I would recommend mounting it with the GParted application I mentioned earlier, then copying it's contents to a CD or DVD.  Perhaps it can be booted from?

---

### Post by Olivier2371 on 2008-11-24
Even better, once your drive is restored with windows ,before to install

Ubuntu dual boot with xp send us a private message and will help.

---

### Post by iminhell on 2008-11-24
Travis, yes those are the card reader on the pc, not the printer. I got confused when I first looked too, was like oh hell ya I still have info there. Then reality set in.
And Yes it is a HP pavilion a720n (but now the only thing that is factory is the MB and the BIOS for the most part).


I'm going to go try that F10 thing. *fingers crossed

---

### Post by pi.boy.travis on 2008-11-24
If the object of this thread is solved, please mark it as such with the "Thread tools" menu above.  This will help other users with similar problems find your thread.

---

### Post by Olivier2371 on 2008-11-24
So where is the original hard-drive?

---

### Post by iminhell on 2008-11-24
^^Oh and that, sorry.

RAM, CD-ROM's video card and audio card have been upgraded along with several different firmware updates, IIRC BIOS was one of them.


Either way I'm writing it off as a lost cause. Problem's where solved and it was found to be my negligence that cause them.

---

### Post by theozzlives on 2008-11-24
> **iminhell said:**
> I would use Ubuntu full time, but this computer is shared and my brother and mom wouldn't like this system. Actually I don't like it simply because I can't find anything, before my screw up that is, stuff from the windows side. That and I have no sound. Which is the whole reason I upgraded to 8.10, no sound with 8.04 and someone suggested upgrading may fix it, being none of the codec's would or drivers (SB live 24 bit btw).

Bad to worse I tell ya.



Since you are now a certified Linux user you can go to [http://www.virtualbox.org]("http://www.virtualbox.org") and run Windows in a Virtual Machine for your mom and brother.

---

### Post by crazyness003 on 2008-11-24
actually, all is not lost. you files may be recoverable. when the partitioning software overwrites the drive it only overwrites it once...with a 0 (zero). There's an app called 'Get Data Back' [HERE]("http://www.runtime.org/data-recovery-software.htm"). You can try it for free, and see if you can recover the data. Then you have many options...if you catch my drift. But its only $80 (yikes) for the NTFS one (the one you need).

I'd give that a try and see how it goes from there. But only to recover your lost datas

As for nixing Ubuntu completely...id think twice about that. then think again afterwards. You'll get used to it, as long as you remember: you are now a n00b again (and thats a good thing, you get to re-learn about computers, in a whole new way). Trust me, these forums are the best place to get answeres.

SUMMARY: 
1. All is not lost.
2. Try Get Data Back for NTFS
3a. If it works, great..
3b. If it dosnt work...cant get any worst
4. Dont get rid of Ubuntu
5a. dualboot if you must!
5b. VirtualBox is also your friend. (but id go with the non-free version. its still $0 but not open source...but has USB support. yummy) [http://www.virtualbox.org/wiki/VirtualBox_PUEL](http://www.virtualbox.org/wiki/VirtualBox_PUEL)
6. cheers

---

### Post by iminhell on 2008-11-24
^^I just went to add/remove programs and searched all available. Just easier for me because I don't quite understand how to install downloads, learning though. Like that it's easier to look through repositories and use the package manager to do the install work rather than downloading from websites.

---

### Post by pi.boy.travis on 2008-11-24
> **iminhell said:**
> ^^I just went to add/remove programs and searched all available. Just easier for me because I don't quite understand how to install downloads, learning though. Like that it's easier to look through repositories and use the package manager to do the install work rather than downloading from websites.

BTW install files for Ubuntu, or any Debian based system, are called .deb files.  You can also get source code as well.  That comes in .tar.gz , but you have to compile it yourself. . . :-k

---

### Post by crazyness003 on 2008-11-24
> **pi.boy.travis said:**
> BTW install files for Ubuntu, or any Debian based system, are called .deb files.  You can also get source code as well.  That comes in .tar.gz , but you have to compile it yourself. . . :-k
which, contrary to popular belief is not that hard!
just read the README or INSTALL file. 99% of the time it will basically walk you through it (although there are mad options you can append to get different results...i dont know any of them). But still easy, nonetheless.

./configure
make
makeinstall

these three commands are like the windows **click, click, double-click**; in linuxspeak

But try to use the reops as much as possible. its easier and they give you auto-notification for updates on all your repo-installed software (take that windows ***AND*** mac)
welcome to the party!

---

### Post by Drakkor on 2008-11-25
I didn't read all 7 pages,but thought maybe you didn't install grub on the mbr, so you have boot options,if so it's easily corrected

---


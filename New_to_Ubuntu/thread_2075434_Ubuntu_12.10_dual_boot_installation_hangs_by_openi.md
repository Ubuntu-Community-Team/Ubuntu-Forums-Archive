---
title: "Ubuntu 12.10 dual boot installation hangs by opening disk partitioner"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by tonycabo on 2012-10-23
Greetings to the whole Ubuntu Forums community.

 First of all,

 Thank you.

 ;D

 I'm an absolute beginner as an active user of the amazing tools that  the open source movement has been creating. The spirit and  motivations that sustain the will of all the people involved in these initiatives is one of those things that reinforces one's faith in  humanity. :O

So, I've got a low spec machine that I need to prepare for creative purposes. Details:
 
[LIST]
[*]Lenovo 3000 N100 laptop
[*]Intel Celeron M CPU 420 @ 1.60 GHz
[*]504 Mb RAM
[*]90 Gb hard drive with 40 Gb of free space
[*]Windows XP installed
[/LIST]
 The target is to achieve the best performance possible with audio  software like Pure Data or Ardour, powerful document creating tools like  LaTeX based text applications or Lilypond, and other programs like  GIMP. I'm well-informed about the poor specs of my machine for some of  these applications, but there's not money to get better hardware and my  only choice is to adapt. However, I dream with expanding my RAM to 2 Gb  some day in the future.

I chose the Lubuntu 12.10 distribution, downloaded the Wibu installer and  tested it. After applying solutions to small common issues (drivers,  Broadcom wireless...) that I could fix with the resources of this forum  and other sites, everything was working smooth and perfectly. I also tested  the applications I'm planning to use frequently and they did very well. So I wanted to go further and make a dual boot installation alongside  Windows XP, having uninstalled Wubi first. I first tried the Lubuntu Installer, which was just too big for my RAM and hanged at the beginning  of the installation. Despite of that, I can run Lubuntu from the Live CD  without problems.

After that, I tried the Lubuntu Alternate Installer unsuccessfully and  also tried it through Ubuntu Minimal Installer having exactly the same  problem: Right after getting the message *"Starting up partitioner"*  nothing happens. The screen remains empty, showing just the background  colour and a white bar at the bottom. At this point, if I hit the *Enter*  key additional white bars appear. When hitting *Esc* the  ]^ symbols are written  in the blank lines of the screen. I also can type regular text in the  blank lines. I always exit from this stuck point with *Ctrl+Alt+Del*.

All the .iso installers were mounted in CD-R disks and tested before  burning the CD with MD5sum, and after with the checker that comes in the  CD. I didn't have any errors at both of the processes.

Since the thing seems to be related with disk partitions I booted  Windows XP and made disc scan with CHKDSK, defragmented the drive with  Diskeeper and ran CClean. I also made a backup of the important files. After, I downloaded GParted and mounted it on a CD and booted to start the application from the Live CD. Following tutorials, I resized Windows XP's partition to 43 Gb, Created an ext4 partition for Lubuntu's root folder (40 Gb) and also created a swap-linux partition (4 Gb). I booted Windows XP twice, making another CHKDSK. Windows XP seems to have adapted perfectly to it's reduced hard drive space. After the whole thing I retried the three installation CDs mentioned above and got stuck exactly at the same point.

Finally, after searching in this forum and other sites for solutions to this thing without success I created this thread looking for hope. I really tried to do my best after posting, but i really can't get over the thing and it is quite frustrating. Sorry for relating the whole *Installing Lubuntu* chapter of my life in such a long post. I just thought it could be useful explaining the process of what I tried. D:

So, please, beloved experts: What's going on here? ;D

---

### Post by tonycabo on 2012-10-24
bump

---

### Post by NikTh on 2012-10-24
Hi , 

It seems here that you tried almost everything and is difficult to someone to advise you. 

However I will give my suggestions . 

**First. **

Try with a Live-USB instead of CD . You can create a LiveUSB with Unetbootin program : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) , then boot from the Live-USB and try again.

**Second **

You said you tried with alternate CD , so the suggestion for a nomodeset option , might be not useful , but take a look here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

**Third**
Also you can try with another version eg: [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)  as the 12.10 is pretty new and maybe a bug exists in the installation CD. 
If the installation of 12.04 goes well , you can try to upgrade to the newer version 12.10 with update manager. 

Thanks

---

### Post by oldfred on 2012-10-24
I have to agree with NikTh, that is seems like you have done everything correctly.

The one time I had issues with gparted not opening my sda drive, chkdsk resolved that issue. 

You seem to have verified ISO & CDs which is often an issue as sometimes downloads may not be good. And tying different ISOs sometime resolves that issue.

Does gparted show any issue with partitions? You can post screenshot of gparted.

---

### Post by tonycabo on 2012-10-24
Here you are. This is my report:

I spoke about the thing with a college mate and I told him NikTh's suggestions. The second one seemed to be the most promising due to his thoughts, and after reading P4man's first post in [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) I saw there things that seem to have solved situations like mine: using noapic, nolapic and acpi=off.

[QUOTE=P4man][SIZE=2]**acpi=off**[/SIZE]
This disables ACPI completely. 
Note: this may not work with all computers and will disable a lot of  useful (or even needed) features. In some cases it may even disable some  crucial features, like.. fans. Be careful with this option, it might  cause your machine to overheat if the fans no longer turn. Think of this  as a last resort. Also note some machines require **acpi=ht** instead.

[SIZE=2]**Noapic and nolapic**[/SIZE]
noapic and nolapic kernel options instruct the kernel to not use   certain programmable interrupt controllers. To understand what that  means exactly requires a deep knowledge of PC hardware, I will not go in  to that here, Ill limit myself to saying on some bioses, especially for  older systems, there are problems in the implementation  of this and it  may be necessary to disable either or both to cure a wide range of   obscure problems, often but not always related to **keyboard and mouse and power management (standby/resume issues)**.[/QUOTE]

I tried all three options from the Lubuntu Installer, one by one and all together and I get stuck again at the same point. The percentage bar that appears under *Starting up the partitioner* actually reaches 100%, but after it always happens what I told above. Reading about ACPI, APIC and LAPIC I learnt it has something to do with standards within stuff that is set in part through the BIOS. I saw my BIOS software was out of date and downloaded the latest version from Lenovo support site and successfully installed it. Windows XP runs perfectly. I tried again the Lubuntu Alternate Installer after doing this, also messing with the apic, lapic and acpi=off options and didn't get anything new. D:

oldfred, here are the GParted screenshots (thanks to Bartender for his howto):

[CENTER][IMG]http://imageshack.us/a/img171/618/gparted.jpg[/IMG]
[/CENTER]
 
Instinct also made me take a picture of this:

[CENTER][IMG]http://imageshack.us/a/img217/1658/gpartedfilesystem.jpg[/IMG]
[/CENTER]
 
It's maybe worth clearing that another thing I did after partitioning the disk and retrying installation without success was opening GParted again and formatting the ext4 and swap-linux partitions to it's respective file systems. They just lose the labels I set when creating them (Lubuntu_root and Lubuntu_swap), but it had no effect by trying again to install.

This seems to be something hard, but I won't give up. I'll try also the other options NikTh suggested. Thanks for your interest, NikTh and oldfred!

Just tell me if the new posted info leads to further conclusions. Let's see if we get this working! :O

---

### Post by oldfred on 2012-10-24
I still do not see any issue. Are you using gparted from Ubuntu liveCD or a gparted liveCD?

If you need the extra boot parameters you usually have to add them to boot Ubuntu liveCD. Some of the other liveCD like gparted may then work as they often are designed to work on older systems.

From LiveCD have you run memory tests? Sometimes Ubuntu/Linux shows memory issues that Windows just ignores (until something major happens).

Sometimes BIOS settings can make a difference. When you installed a new BIOS it reverted to defaults also.

---

### Post by squakie on 2012-10-24
A couple of quick questions:

- are you running anything like fakeraid?

- does it just sit there, or does it say "xx%" and "scanning disks"?

---

### Post by oldfred on 2012-10-24
Good question squakie

If drive was ever in a RAID configuration, that leaves meta-data on the drive. Ubuntu sees that and usually does not work.

---

### Post by squakie on 2012-10-25
I wish I could say it was an original thought, but I found mention of it on the net and I remember the same problem when I tried to set up raid a while back.  Took a bit of monkeying around to get that off the drive so I could really use it.  For the OP:  being able to use gparted on the disk wouldn't show this problem.  I remember I used gparted and it did it's thing, but I couldn't use the drive.  I wish I could tell you what to check, how to check it, and fix it, but I don't have those answers.  Perhaps someone like OldFred can point you in the right direction for those.

---

### Post by oldfred on 2012-10-25
If you ever turned RAID on in BIOS. But never run this if you have or want to keep RAID:

sudo dmraid -E -r /dev/sda

There are many BIOS settings that can cuase issues. I have kept a few. Most will not apply but you can review list.

Some issues on booting install:
fixed the problem by adding rootdelay to grub.cfg this allows time for the usb drive to load.
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
BIOS settings need USB mouse & keyboard
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB
[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)
Old gpt data on drive
Disable Quickboot in BIOS
turning off UDMA in the BIOS my problem has gone away.(old system & may make system slower)
BIOS setting, Keyboard response in grub really slow
Fast Boot setting prevents keyboard from working & other issues
Bios not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
After update, It had reset to the BIOS defaults, setting the video to ONBOARD and switching off the dynamic video memory allocation (manually allocating 32Mb instead of leaving it as AUTO).
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Sometimes specific issues by motherboard like this:
[Natty] Marvell 88SE9120 IDE-Part not working 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/777325)
External drive needed separate power supply
Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramter
So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!
lib64 folder missing??
[http://ubuntuforums.org/showthread.php?t=2069764](http://ubuntuforums.org/showthread.php?t=2069764)

---

### Post by tonycabo on 2012-10-25
I never used RAID, but I'm not the first owner of this machine, so I ran Lubuntu from the Live CD, opened the terminal and used codes to check RAID status. I had to install mdadm and postfix packages to run what psusi suggests here in his post at [http://ubuntuforums.org/showthread.php?t=889195](http://ubuntuforums.org/showthread.php?t=889195)

So, this is what the terminal told:

```
lubuntu@lubuntu:~$ sudo mdadm -D /dev/md0
mdadm: cannot open /dev/md0: No such file or directory 
```I opened /dev through GUI and didn't found any other md{number} file.

I also typed what jack_hmr indicates in [http://ubuntuforums.org/showthread.php?t=1764162](http://ubuntuforums.org/showthread.php?t=1764162)

```
lubuntu@lubuntu:~$ cat /proc/mdstat
Personalities : 
unused devices: <none>
```It seems that this machine doesn't have RAID enabled. Am I wrong?

I also typed codes to see what's up with BIOS, using the orders that ciscosurfer describes in the *BIOS INFORMATION* section from his first post at [http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

```
lubuntu@lubuntu:~$ sudo biosdecode
# biosdecode 2.11
SMBIOS 2.4 present.
    Structure Table Length: 1436 bytes
    Structure Table Address: 0x000DC010
    Number Of Structures: 42
    Maximum Structure Size: 134 bytes
ACPI 2.0 present.
    OEM Identifier: LENOVO
    RSD Table 32-bit Address: 0x1F694F93
    XSD Table 64-bit Address: 0x000000001F694FE7
BIOS32 Service Directory present.
    Revision: 0
    Calling Interface Address: 0x000FD610
PNP BIOS 1.0 present.
    Event Notification: Not Supported
    Real Mode 16-bit Code Address: F000:B610
    Real Mode 16-bit Data Address: 0040:0000
    16-bit Protected Mode Code Address: 0x000FB62E
    16-bit Protected Mode Data Address: 0x00000400
PCI Interrupt Routing 1.0 present.
    Router ID: 00:1f.0
    Exclusive IRQs: None
    Compatible Router: 8086:122e
    Slot Entry 1: ID 00:00, on-board
    Slot Entry 2: ID 00:07, on-board
    Slot Entry 3: ID 00:01, on-board
    Slot Entry 4: ID 01:00, slot number 6
    Slot Entry 5: ID 00:02, on-board
    Slot Entry 6: ID 00:1b, on-board
    Slot Entry 7: ID 00:1c, on-board
    Slot Entry 8: ID 02:00, slot number 7
    Slot Entry 9: ID 03:00, slot number 8
    Slot Entry 10: ID 00:1d, on-board
    Slot Entry 11: ID 05:01, on-board
    Slot Entry 12: ID 05:04, on-board
    Slot Entry 13: ID 05:06, on-board
    Slot Entry 14: ID 00:1f, on-board 
``````
lubuntu@lubuntu:~$ sudo hwinfo --bios | less
sudo: hwinfo: command not found 
``````
lubuntu@lubuntu:~$ sudo dmidecode --type bios
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: LENOVO
    Version: 61ET37WW
    Release Date: 06/04/07
    Address: 0xE6B70
    Runtime Size: 103568 bytes
    ROM Size: 1024 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        ACPI is supported
        USB legacy is supported
        AGP is supported
        BIOS boot specification is supported
``````
lubuntu@lubuntu:~$ sudo lshw
PCI (sysfs)  
lubuntu                   
    description: Notebook
    product: 07683FU ()
    vendor: LENOVO
    version: 3000 N100
    serial: L3F7346
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=88746217-C34F-11DA-81F4-000FB0C91A10
  *-core
       description: Motherboard
       product: CAPELL VALLEY(NAPA) CRB
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W1220Z1ZBUA6468WK
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 61ET37WW
          date: 06/04/07
          size: 101KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        420  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1600MHz
          capacity: 2048MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm dtherm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 512MiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: M1
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:d0200000-d027ffff ioport:1800(size=8) memory:c0000000-cfffffff memory:d0300000-d033ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d0280000-d02fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:d0340000-d0343fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:24000000-241fffff ioport:24200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:d0000000-d00fffff ioport:24400000(size=2097152)
           *-network
                description: Network controller
                product: BCM4311 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0
                resources: irq:17 memory:d0000000-d0003fff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d0544000-d05443ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:2000(size=4096) memory:d0100000-d01fffff ioport:20000000(size=67108864)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:c9:1a:10
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:28000000-28000fff ioport:2400(size=256) ioport:2800(size=256) memory:20000000-23ffffff memory:2c000000-2fffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:22 memory:d0100800-d0100fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:23 memory:d0100400-d01004ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=r592 latency=0
                resources: irq:23 memory:d0101000-d01010ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=r852 latency=0
                resources: irq:23 memory:d0101400-d01014ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS541010G9SA00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MBZI
             serial: MP2ZM4X0JXKS7R
             size: 93GiB (100GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=cccdcccd
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 3848e99d-e2ab-e54e-82cb-700325aad5fa
                size: 44GiB
                capacity: 44GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2011-11-04 07:13:20 filesystem=ntfs label=TONY DRIVE modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSWIN4.1
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: FAT32
                serial: 1b33-0a00
                size: 5338MiB
                capacity: 5341MiB
                capabilities: primary boot fat initialized
                configuration: FATs=2 filesystem=fat label=IBM_SERVICE
           *-volume:2
                description: EXT4 volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1.0
                serial: 7e0eb46f-84e3-4eb1-a58d-b5dd59e90ffe
                size: 39GiB
                capacity: 39GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2012-10-23 11:00:07 filesystem=ext4 modified=2012-10-23 11:00:34 state=clean
           *-volume:3
                description: Linux swap volume
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 1
                serial: b951c53f-309e-46ce-9bc2-10c8650c9abf
                size: 3999MiB
                capacity: 3999MiB
                capabilities: primary nofs swap initialized
                configuration: filesystem=swap pagesize=4096
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4244N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             logical name: /cdrom
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
                logical name: /cdrom
                capabilities: partitioned partitioned:dos
                configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=0f759e24 state=mounted
              *-volume UNCLAIMED
                   description: Hidden HPFS/NTFS partition
                   physical id: 1
                   capacity: 692MiB
                   capabilities: primary bootable hidden
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
```The last one didn't give any output.

```
lubuntu@lubuntu:~$ gksudo lshw-gtk
```GParted has been always run from a dedicated Live CD to the program.

I also used Memtest86+ v 4.20 once from the standard Lubuntu Installer Live CD and again from the Lubuntu Alternate Installer Live CD. The test displays thousands of errors that keep on growing and growing in number as long I leave the test on. I searched info about this and found different and confusing things, some of them saying that they aren't actually that number of errors and that Memtest86+ displays them because of some reason I actually couldn't understand.

Here is a screenshot

[LEFT][IMG]http://img688.imageshack.us/img688/7775/lubuntumemtest86.jpg[/IMG]
[/LEFT]

and a [short video displaying how fast the errors appear, like a continuous stream]("http://imageshack.us/clip/my-videos/803/h8thdudixshnlewtezcfot.mp4/"). It seems the test doesn't get any further from 59%

What's wrong with these over ten million listed errors? D:

Here is also a photo of my screen when it arrives at the Ubuntu installation point where always remains hanged. Just plain screen, no symbols or text. It looks like a zoomed close-up of a Smurf. D:

[IMG]http://img402.imageshack.us/img402/4056/lubuntuhangs.jpg[/IMG]

[Here is also a video of the hanged computer and the weird key reactions]("http://imageshack.us/clip/my-videos/254/7m9tsmvpyeagxoedvljjkk.mp4/").

[QUOTE=oldfred]If you ever turned RAID on in BIOS. But never run this if you have or want to keep RAID:

sudo dmraid -E -r /dev/sda

There are many BIOS settings that can cuase issues. I have kept a few. Most will not apply but you can review list.[/QUOTE]

So, after knowing the info above, should I run that at Lubuntu's Live CD session terminal? Is it possible to run terminal codes from the Alternate Installer Live CD, which hasn't the *Try Ubuntu without installing* option? Would the change have effect if I run the command from the Lubuntu Live Session, and after switch CD to the Alternate Installer one, so that I am able to install and avoid RAM lack freezing?

I'm honestly kind of lost with the list and links you posted, oldfred. I can't figure out what of those options could do something for my clog on installing. 

Thanks for your help, squakie and oldfred. I think I answered to all your questions and requirements. I'm looking forward to being able to finally install the OS and start working with it. This is taking way more time to set than expected! xD

---

### Post by squakie on 2012-10-25
I'm afraid I can't really help you much.  If the disk was previously used in a different environment from the current laptop, it's possible someone may have tried raid with it, but I don't know how to tell.  I just know I had a heck of time straightening mine back out of it.

I'm going to back away and let the knowledgeable people help you.

Best of luck.

---

### Post by oldfred on 2012-10-25
If you are not running RAID, running the command to remove RAID meta-data will not hurt anything. But I am not optimistic, if  that is the issue.

But failing memtest is an issue. 

How much memory do you have. Is it more than one SIMM? Can you run with one just to see if that is ok, then switch. If too little memory the only choice may be to buy new memory.

---

### Post by tonycabo on 2012-10-26
@squakie: Ok! Thanks for trying to help, thou! :D

@oldfred: It seems my RAM card works with DIMM, not SIMM. Here is the info I could gather from my RAM. According to the *[Lenovo 3000 N100 and N200 Hatdware Maintenance Manual]("http://download.lenovo.com/pccbbs/mobiles_pdf/42x3553_03.pdf")* my RAM card is named 512-MB DDR2-667 SDRAM SO-DIMM (PC2-5300) card × 1 

[IMG]http://imageshack.us/a/img690/9031/lenovoram.jpg[/IMG]

Windows System Properties:

[IMG]http://imageshack.us/a/img145/5981/lenovosysproperties.jpg[/IMG]

Windows System Information:

[IMG]http://imageshack.us/a/img513/8652/lenovomsinfo32.jpg[/IMG]

[IMG]http://imageshack.us/a/img191/4619/63206977.jpg[/IMG]

Question: Why does System Properties say I've got 504 Mb RAM if there are 512 Mb in my card?

Also, when I ran Lubuntu form the Live CD saw something strange: a file named *lost+found* in my empty partition that I couldn't open:

[IMG]http://imageshack.us/a/img7/9769/lubuntufileinpartition.png[/IMG]

[IMG]http://imageshack.us/a/img694/8240/lubuntufileinpartitiond.png[/IMG]

I tried a combination of NikTh's suggestions preparing a Live USB with Lubuntu 12.04 Alternate Installer. I couldn't use UNetbootin from Windows XP. It alwasy hanged at the beginning. But I could create the Live USB using UNetbootin through a live session from the Lubuntu Live CD. I installed it successfully! ;D

But!

After going further very happily from my usual stuck point things didn't happened as expected. When the disk partitioner successfully opened instinct told me to remake the partitions from that tool, so I deleted the ext4 and swap partitions I already had and made new ones with the same size, putting the 4 Gb swap area right after the Windows partition, and after the 40 Gb ext4 partition. At the ext4 partition creating menu I had trouble with the *Enable boot flag* option. Some tutorials told to turn it on and some to leave it off. I left that off. Also, unlike at the screenshots of tutorials I read, my Windows partition hadn't the *B* for Bootable at the partition's table.

After some processes I was prompted to select installation features and chose LXDE Desktop. I also set GRUB to main. I restarted and saw the GRUB menu with everything listed, but the new OS was named Ubuntu, not Lubuntu. When I selected it I also didn't get the Lubuntu logo and it's GUI as I had it in my LiveCD sessions. The general Ubuntu logo appeared instead of the Lubuntu one, and no GUI loaded. Just a terminal in full screen.

As that looked somehow as just a core installation was done, I did

```
sudo apt-get update
sudo apt-get install lubuntu-desktop
```to get my actual Ubuntu installation to the Lubuntu settings. And the computer is now doing that process.

What happened? Why didn't I get the Lubuntu distro installed from the Lubuntu Alernate Installer, but a general Ubuntu installation?

I don't undestand what's going on. D:

---

### Post by oldfred on 2012-10-26
Unless you used the Ubuntu alternative not the Lubuntu alternative, I do not know. I only installed Lubuntu once and that was the standard version not alternative.

Boot flag should always be on a NTFS primary partition if using Windows. Grub does not use boot flag for Ubuntu or chain loading Windows, Windows has to have boot flag to directly boot, install, or repair the NTFS primary Windows boot partition. A few BIOS need a boot flag, so we always suggest one anyway.

New partitions in Linux get the lost & found folder. It is somewhat like the chkdsk folder in Windows,  that chkdsk creates if it has to copy files with issues.

---

### Post by tonycabo on 2012-10-26
Ok.

Then, should I leave things as they are and upgrade to Lubuntu 12.10 from this point or reinstall Ubuntu ensuring that I mark the NTFS partition as bootable?

Is it possible to mount a LiveUSB with Lubuntu 12.10 despite it isn't listed among the UNetbootin options?

Ubuntu is still downloading and installing the lubuntu-desktop packages. Hope it ends well. D:

Thanks.

---

### Post by tonycabo on 2012-10-27
All right!

Done!

:D

It wasn't a CD or USB matter. Just the version of Lubuntu. I mounted Lubuntu 12.10 .iso on a USB key and I got stuck at the same point as with the CD.

I mounted Lubuntu 12.04 .iso on a CD and could successfully install it without any issue.

So, in conclusion, Ubuntu 12.10 Installer doesn't run in my machine for some reason, but 12.04 does work. :D

Is this something I've got to notify somewhere?

The only weird thing I saw is that task manager tells I've got 486 Mb RAM instead of the 512 Mb I should have. Is that normal?

[[IMG]http://img42.imageshack.us/img42/4708/lubuntu486ram.png[/IMG]]("http://imageshack.us/photo/my-images/42/lubuntu486ram.png/")

I want to thank the community for your support. I learned a lot in this first community support experience, figuring out how to apply all your hints and suggestions.

Rock!

---


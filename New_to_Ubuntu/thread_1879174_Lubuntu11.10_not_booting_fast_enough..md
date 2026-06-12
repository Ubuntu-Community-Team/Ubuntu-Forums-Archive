---
title: "Lubuntu11.10 not booting fast enough."
date: 2011-11-11
forum: New to Ubuntu
---

### Post by ask_ on 2011-11-11
Hello , I have an HP PC , 1.24 GB Ram , 2.93 Ghz Intel Pentium (4) CPU. 80 GB Hard disk space. (I will post detailed specs at the bottom of this post ). Till now I had windows XP installed on the PC. Recently I tried out Ubuntu 11.10 then Xubuntu 11.10 and finally I am on Lubuntu11.10. Note, I am overall satisfied with it as compared to Ubuntu 11.10 and Xubuntu 11.10 . But Lubuntu doesn't seem to be taking appreciably less time to boot than the other two.(Though I must say it shuts down in a jiffy)
What's more Windows XP would boot pretty fast.(Though the reason for that was that I had uninstalled every unwanted program from it .I only had AVG , Openoffice , VLC media player and other small programs on it).

My need for a PC is following :-
1) browsing internet , (also youtube)
2) programming on gcc , gnuOctave .
3) Playing normal resolution videos on VLC media player.

When I use youtube , CPU usage is very high (more than 80%).


I would like to remove inessentials from my PC. Which softwares if removed will help increase speed.
Is it really necessary to have both Lubuntu and LXDE environments. Can I remove one of them ? Will it reduce booting time? Which is faster gedit or Leafpad(I like Gedit ,so do not wish to remove it)

Will changing swap settings help (Though I would like to know how to do so)?

Note , I had selected all the Updates which Lubuntu asked me to install after installation.

```
           

    description: Desktop Computer
    version: 04H0211RE101GROUP10
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=A04E51C5-FC31-D911-BB31-E779CD25D775
  *-core
       description: Motherboard
       product: Grouper
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.xx
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 3.06
          date: 08/27/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.4
          serial: 0000-0F34-0000-0000-0000-0000
          slot: CPU 1
          size: 2933MHz
          capacity: 3800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 21
          slot: System board or motherboard
          size: 1280MiB
        *-bank:0
             description: DIMM DDR Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM DDR Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfe00000-cfe7ffff ioport:cc00(size=8) memory:d0000000-dfffffff memory:cfdc0000-cfdfffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82915G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:cfe80000-cfefffff
        *-multimedia
             description: Audio device
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:41 memory:cfdb8000-cfdbbfff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:50000000-501fffff ioport:50200000(size=2097152)
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c480(size=32)
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c800(size=32)
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c880(size=32)
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:cfdb7c00-cfdb7fff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:e000(size=4096) memory:cff00000-cfffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:20 memory:cffff800-cfffffff ioport:ec00(size=128)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:11:2f:a6:54:ae
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:21 ioport:e800(size=256) memory:cffff400-cffff4ff
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 5
                bus info: pci@0000:02:05.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
                resources: memory:cffff000-cffff0ff ioport:e480(size=8) ioport:e000(size=256)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AW-G170A
                vendor: SONY
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.75
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=8) ioport:b880(size=4) ioport:b800(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD800JD-22JN
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAM91950835
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0001d524
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: ececbda8-912d-4c7c-9065-122f7942b6b0
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-11-10 16:37:04 filesystem=ext4 lastmountpoint=/ modified=2011-11-10 11:44:55 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-11-11 14:10:49 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 1270MiB
                   capacity: 1270MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1270MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi:0
          physical id: 1
          bus info: usb@5:1
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
     *-scsi:1
          physical id: 2
          bus info: usb@5:2
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-cdrom
             description: SCSI CD-ROM
             product: Mass Storage
             vendor: HUAWEI
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/scd1
             logical name: /dev/sr1
             version: 2.31
             serial: 3
             capabilities: removable audio
             configuration: status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1
                capabilities: partitioned partitioned:mac
              *-volume:0 UNCLAIMED
                   description: Apple partition map
                   physical id: 1
                   capacity: 1KiB
              *-volume:1 UNCLAIMED
                   description: Apple HFS
                   physical id: 2
                   version: 4
                   serial: 00000000-0000-0000-0000-000000000800
                   size: 12MiB
                   capacity: 12MiB
                   capabilities: hfsplus initialized
                   configuration: checked=2009-01-24 07:22:34 created=2009-01-24 01:52:34 filesystem=hfsplus lastmountedby=LSDf modified=2009-01-24 07:22:34 state=unclean
        *-disk
             description: SCSI Disk
             product: SD Storage
             vendor: HUAWEI
             physical id: 0.0.1
             bus info: scsi@9:0.0.1
             logical name: /dev/sdf
             version: 2.31
             capabilities: removable
             configuration: ansiversion=2
           *-medium
                physical id: 0
                logical name: /dev/sdf    

```

---

### Post by mikewhatever on 2011-11-11
1. There is no connection between installed applications and boot times, unless those applications are run at startup (AVG).

2. You can have LXDE without Lubuntu as well as the other way around, but that would do nothing to the boot times.

3. Leafpad is faster, but Gedit has more features.

4. Flash is known to be more efficient on Windows.

11.10 is known to boot slower then its predecessors, so if the boot time is very important to you, use 10.04.

---

### Post by BillyBoa on 2011-11-11
In 11.10 the startup applications dialog is removed. 

So you have to 

```
gksu nautilus
```

and then go to /etc/xdg/autostart and remove the applications you don't use, eg bluetooth, deja-dup, jockey, sounds etc.

This way you will notice a difference on booting time.

From software center you can remove Ubuntu One, Tomboy, Games, Thunderbird, Gwibber, Empathy and all the programs you don't need.

Then you have to run

```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
```

to clean your computer from the remnants of the programs

---

### Post by ask_ on 2011-11-11
> **mikewhatever said:**
> 1. There is no connection between installed applications and boot times, unless those applications are run at startup (AVG).

2. You can have LXDE without Lubuntu as well as the other way around, but that would do nothing to the boot times.

3. Leafpad is faster, but Gedit has more features.

4. Flash is known to be more efficient on Windows.

11.10 is known to boot slower then its predecessors, so if the boot time is very important to you, use 10.04.



Thanks .  That removed many of my doubts.

Would doing anything to swap change boot times ? 

Is there any other way to view youtube w/o flash ?
I mean suppose I view the youtube as a stream in VLC will it perform better ?

---

### Post by ask_ on 2011-11-11
> **BillyBoa said:**
> In 11.10 the startup applications dialog is removed. 

So you have to 

```
gksu nautilus
```

and then go to /etc/xdg/autostart and remove the applications you don't use, eg bluetooth, deja-dup, jockey, sounds etc.

This way you will notice a difference on booting time.

From software center you can remove Ubuntu One, Tomboy, Games, Thunderbird, Gwibber, Empathy and all the programs you don't need.

Then you have to run

```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
```

to clean your computer from the remnants of the programs

I am using lubuntu  , in autostart dejadup,sounds  etc is not there. From the looks of it only bluetooth Manager is there which i can remove.

contents of autostart :-
[CODE]
bluetooth-applet.desktop         gsettings-data-convert.desktop
bluetooth-applet-unity.desktop   jockey-gtk.desktop
gdu-notification-daemon.desktop  nm-applet.desktop
gnome-keyring-gpg.desktop        notification-daemon.desktop
gnome-keyring-pkcs11.desktop     polkit-gnome-authentication-agent-1.desktop
gnome-keyring-secrets.desktop    print-applet.desktop
gnome-keyring-ssh.desktop        update-notifier.desktop
gnome-user-share.desktop         xfce4-power-manager.desktop

[CODE]
which of these do you reckon can be removed

---

### Post by bryncoles on 2011-11-11
As another poster said, installed programmes won't slow your boot times unless they run at boot.  So, what you want to do is find you services settings (perhaps session manager?) and toggle off all the things you do not routinely use.  

Perhaps 

```
sysv-rc-conf
``` would help?  (you may need to install it from synaptic).  

I recall however that once, I had a Xubuntu install that took around 15  minutes to boot up, due to some preposterously heavy bootloader, and some incredibly low powered hardware.  I 'solved' the issue by disabling the graphical boot! You might like to try that too  (don't worry, you can start the graphics after the boot has completed.  


open a terminal and type 

```
gksudo gedit /etc/default/grub &
```

and change the line that reads > GRUB_CMDLINE_LINUX_DEFAULT=" quiet splash" to read > GRUB_CMDLINE_LINUX_DEFAULT="text"  Save and close.  then type into the terminal ```
sudo update-grub
```. 

When you boot, it'll ask you for your username and password at a comman prompt.  Then it'll boot you into a cli environment.  Type ```
startx
``` to get your desktop back.  perhaps add 'startx' to your start-up services?

If you decide you don't like doing things this way, just repeat the steps, replacing 'text' with 'quiet splash' again.  

Or, install 'bootchart' from syanptic (software centre?)  and ask someone here how to use it.  It'll help you identify what's slowing your boot times down.  Somehow (I have no idea how to use it).

---

### Post by mikewhatever on 2011-11-11
> **ask_ said:**
> Thanks .  That removed many of my doubts.

Would doing anything to swap change boot times ? 

Is there any other way to view youtube w/o flash ?
I mean suppose I view the youtube as a stream in VLC will it perform better ?

Swap should also be irrelevant to boot times. In fact, with over 1GB of RAM, it's likely that swap is very rarely used. That said, the number of partitions that has to be mounted at boot may affect boot times considerably.

For flash, there is a Firefox addon, [FlashVideoReplaycer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/?src=userprofile"). Obviously, you have to install and use Firefox.
There is also Minitube, a dedicated youtube client.
[http://www.ubuntumini.com/2009/12/minitube-youtube-without-flash.html](http://www.ubuntumini.com/2009/12/minitube-youtube-without-flash.html)

As for the startup applications, I'd recommend against removing anything from /etc/xdg/autostart.

---

### Post by ask_ on 2011-11-11
> **mikewhatever said:**
> Swap should also be irrelevant to boot times. In fact, with over 1GB of RAM, it's likely that swap is very rarely used.

For flash, there is a Firefox addon, [FlashVideoReplaycer]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/?src=userprofile"). Obviously, you have to install and use Firefox.
There is also Minitube, a dedicated youtube client.
[http://www.ubuntumini.com/2009/12/minitube-youtube-without-flash.html](http://www.ubuntumini.com/2009/12/minitube-youtube-without-flash.html)

As for the startup applications, I'd recommend against removing anything from /etc/xdg/autostart.

ok. I won't remove anything from autostart. But I never use bluetooth , hence was thinking of removing it.

---

### Post by ask_ on 2011-11-11
> **bryncoles said:**
> 
 

When you boot, it'll ask you for your username and password at a comman prompt.  Then it'll boot you into a cli environment.  Type ```
startx
``` to get your desktop back.  perhaps add 'startx' to your start-up services?

what will startx boot me into LXDE or Lubuntu ? Will startx give me the choice ?

---

### Post by BillyBoa on 2011-11-11
> **ask_ said:**
> I am using lubuntu  , in autostart dejadup,sounds  etc is not there. From the looks of it only bluetooth Manager is there which i can remove.

contents of autostart :-
[CODE]
bluetooth-applet.desktop         gsettings-data-convert.desktop
bluetooth-applet-unity.desktop   jockey-gtk.desktop
gdu-notification-daemon.desktop  nm-applet.desktop
gnome-keyring-gpg.desktop        notification-daemon.desktop
gnome-keyring-pkcs11.desktop     polkit-gnome-authentication-agent-1.desktop
gnome-keyring-secrets.desktop    print-applet.desktop
gnome-keyring-ssh.desktop        update-notifier.desktop
gnome-user-share.desktop         xfce4-power-manager.desktop

[CODE]
which of these do you reckon can be removed

You could remove bluetooth, jockey (is for the extra drivers) and update notifier (you can search manually for updates). If you are not going to use extensively the printers you could remove print-applet as well.

---

### Post by bryncoles on 2011-11-11
> **ask_ said:**
> what will startx boot me into LDXE or Lubuntu ? Will startx give me the choice ?

So far as I know, no.  It won't give you a choice.  It should boot into whatever your default environment is -- which I'm guessing would be Lubuntu.  I'm not sure how you could choose which one you want, but there must be a way!

---

### Post by ask_ on 2011-11-11
I tried booting via cli but it didn't make much difference. So switched back to quiet splash.
I thought booting would be quite fast as my system specs are quite good as compared to minimum requirements.
But when I say the boot time is not fast enough I don't mean it takes eons to boot. It is actually quite fast - under 1-2 minutes.

I was actually comparing to Windows XP boot. But Windows XP is quite old OS and I had removed most of the programs from it.Furthermore , I was hoping Lubuntu on my 7-yr-old machine would run as fast as Ubuntu on a new machine.

But I would like to thank all of you. Now at least I know that applications installed don't cause boot time to increase.

Will try the other things pointed out in the thread and inform if/when the boot process speeds up.

Once booted , the OS performs quite fast(better than Windows XP). Only trouble was youtube videos consumed lot of CPU. But as you pointed out flash would give such performance when not in Windows, so no worries.

---

### Post by bioterror on 2011-11-13
Seems like you have a Pentium 4 capable of doing Hyper Threading, but it not enabled.

You should check your BIOS settings for hyper threading settings.
Hyper Threading will boost your computer by ~30% what comes to CPU usage.

---

### Post by ask_ on 2011-11-13
[IMG]http://www.intel.com/products/i/browse/p4pht.gif[/IMG]

By PC doesn't have the sticker as shown above. 

It doesn't have the HT written on it.

But still will check , but I read on one or two web forums , that if the sticker doesn't have HT written on it , then perhaps the motherboard doesn't have the ability to handle it. Are you sure from the HW specs that HT won't cause any problems ? 

Anyways , I am quite satisfied with CPU performance once the PC has started. And I measured boot time , it is around 35 seconds. Perhaps I should be satisfied with it. Can't expect the old PC to boot up in 10 seconds.(at least not until , I know enough to tweak it safely. For I found changing sysv-rc-conf advanced for my level. Will try it after I learn more.)

---


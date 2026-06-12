---
title: "Screen Blurry/Fuzzy"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by caeras on 2013-03-12
Hi folks, ):P

Hoping someone can help me with a rather annoying problem that has occurred with ubuntu and now xubuntu.

I have a Fujitsu Amilo Li705 that is about 5 (maybe older) years old,which shipped with vista basic, 1gb ram, 1.7 processor.  It has been sitting in a cupboard for the best part of 12 months but I need another computer so decided to resurrect it.

I took off all the photos, files etc that I needed as I did not want to run a dual boot as I have no need for vista (who does?!), all the software I need is available for linux.  Therefore, I was going to so a complete installation over writing any previous data.

I have used xubuntu in the past on an old netbook and was really pleased with it but I thought I would like to try ubuntu for a change as the machine met the minimum requirements.  I struggled to get the live cd to run, after some research I used the "xforcevesa" switch which got me in, but when I used the live CD the screen looked, what can only be described as blurry/fuzzy in places, predominately on text but also in general.

Anyway, I decided to go ahead and install anyway, hoping the full installation would not have this issue.  However, it did still have the issue, it was also extremely slow, unresponsive and the fan was constantly running.  I did some research on this and I altered resolution to no avail, I then came up with the solution of installing compbiz so I could disable the effects, then I thought what is the point?  If I am not going to have the effects I may as well stick with trusty xubuntu.

I downloaded xubuntu and tested the disk on a different machine, and all was fine.  When I tried on my laptop I needed to use the xforcevesa again to get into the live disk, the screen was blurry again, but I decided to go ahead and install anyway as I had nothing to lose.

Once I installed it, I ran all the updates and added restricted extras but the screen still remained fuzzy.  Here are a few pictures to illustrate, in fairness the pictures doesn't do it justice as it is a lot worse than it looks but thought they may help diagnose the problem.
[http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070111.jpg](http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070111.jpg)
[http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070048.jpg](http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070048.jpg)
[http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070015.jpg](http://i562.photobucket.com/albums/ss62/racecourseambyth/Linux%20screen%20problem/2013-03-12070015.jpg)

I suspected a resolution issue but have tried every available option to no avail, I also thought it may be a graphics driver issue but I think it uses viachrome9 which I believe is already in xubuntu?

Also, I have no idea if related or not but the fan is running all the time, not as loud as when I had ubuntu on it but still noticeable.

I would really appreciate any help that you can give me, I do have limited experience with linux, so understand the very basics but apologies in advance if I haven't made any sense.  If you need further information please let me know!

Thanks again

Craig

---

### Post by caeras on 2013-03-12
I meant to add, I tried fiddling with the font (alias) settings to no avail!

---

### Post by mastablasta on 2013-03-12
first you will need to post exact GPU.

lshw

and

lspci 

should do the job. then continue from there on.

---

### Post by caeras on 2013-03-12
Thank you for replying.  I am in work now, but will post this evening.

I am assuming I need to enter those commands into the terminal?  And then paste the results for each here?

Sorry for the newb q's!

---

### Post by caeras on 2013-03-12
LSHW.  Advised to do as super user so did with sudo:

craig@craig-XubuntuLaptop:~/Desktop$ sudo lshw
[sudo] password for craig: 
craig-xubuntulaptop       
    description: Notebook
    product: AMILO Li1705 ()
    vendor: FUJITSU SIEMENS
    version: 20
    serial: YSMI032165
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1
  *-core
       description: Motherboard
       product: AMILO Li1705
       vendor: FUJITSU SIEMENS
       physical id: 0
       version: 0.1
       serial: 9N7865437
     *-firmware
          description: BIOS
          vendor: FUJITSU SIEMENS
          physical id: 0
          version: 1.0A-2308-8A20
          date: 01/02/2007
          size: 92KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect edd int5printscreen int9keyboard int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: mPGA 479M
          size: 1730MHz
          capacity: 1730MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor tm2 xtpr pdcm dtherm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MiB
             capabilities: burst external write-through
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 0
             slot: S1
             size: 512MiB
             width: 128 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: S2
             size: 512MiB
             width: 128 bits
             clock: 533MHz (1.9ns)
     *-pci:0
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8
          resources: irq:0 memory:c0000000-c7ffffff
        *-generic UNCLAIMED
             description: PIC
             product: CN896/VN896/P4M900 I/O APIC Interrupt Controller
             vendor: VIA Technologies, Inc.
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: io_x_-apic bus_master
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
             resources: memory:c8000000-c8ffffff memory:a0000000-bfffffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: CN896/VN896/P4M900 [Chrome 9 HC]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
                configuration: latency=16 mingnt=2
                resources: memory:a0000000-bfffffff memory:c8000000-c8ffffff
        *-pci:1
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:1000(size=4096) memory:40000000-401fffff ioport:40200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: CN896/VN896/P4M900 PCI to PCI Bridge Controller
             vendor: VIA Technologies, Inc.
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress pm msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 ioport:7000(size=4096) memory:c9000000-c90fffff ioport:40400000(size=2097152)
        *-ide:0
             description: IDE interface
             product: VT8237A SATA 2-Port Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=sata_via latency=64
             resources: irq:21 ioport:4c70(size=8) ioport:4c64(size=4) ioport:4c68(size=8) ioport:4c60(size=4) ioport:4c40(size=16) ioport:4400(size=256)
        *-ide:1
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_via latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:4c50(size=16)
        *-usb:0
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:20 ioport:4c00(size=32)
        *-usb:1
             description: USB controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=64
             resources: irq:22 ioport:4c20(size=32)
        *-usb:2
             description: USB controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:21 memory:c9400000-c94000ff
        *-isa
             description: ISA bridge
             product: VT8237A PCI to ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm cap_list
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 7c
             serial: 00:14:0b:0a:6f:d1
             size: 10Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=half latency=24 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10Mbit/s
             resources: irq:23 ioport:4800(size=256) memory:c9400400-c94004ff
        *-pci:3
             description: PCI bridge
             product: VT8237A Host Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: memory:c9100000-c91fffff
           *-multimedia
                description: Audio device
                product: VT8237A/VT8251 HDA Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:c9100000-c9103fff
        *-pci:4
             description: PCI bridge
             product: VT8237A PCI to PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht subtractive_decode bus_master cap_list
             resources: memory:40600000-406fffff
           *-network
                description: Wireless interface
                product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
                vendor: Atheros Communications Inc.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: wlan0
                version: 01
                serial: 00:c0:a8:d3:9a:5c
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.5.0-25-generic firmware=N/A ip=192.168.1.67 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:40600000-4060ffff
     *-pci:1
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN896/VN896/P4M900 Security Device
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: CN896/VN896/P4M900 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 106
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: VT8237/8251 Ultra VLINK Controller
          vendor: VIA Technologies, Inc.
          physical id: 107
          bus info: pci@0000:00:11.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST980811AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.AL
             serial: 5LY1W24C
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000e1588
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 9ead0ad6-0e02-4484-9f53-20c0834ce14d
                size: 73GiB
                capacity: 73GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-03-11 19:32:43 filesystem=ext4 lastmountpoint=/ modified=2013-03-12 17:29:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-03-12 17:29:16 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 765MiB
                capacity: 765MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 765MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-T10N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: PW03
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium-Ion Battery
       product: SMP-LMXXSS3
       vendor: SMP
       physical id: 1
       serial: e00431401B03A52202757
       slot: In the Back,on the middle
       capacity: 24420mWh
       configuration: voltage=11.1V
craig@craig-XubuntuLaptop:~/Desktop$

---

### Post by caeras on 2013-03-12
LSPCI

craig@craig-XubuntuLaptop:~/Desktop$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN896/VN896/P4M900 [Chrome 9 HC] (rev 01)
04:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
05:01.0 Ethernet controller: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] (rev 01)
craig@craig-XubuntuLaptop:~/Desktop$

---

### Post by ManamiVixen on 2013-03-12
Ooooohhhhhh..... VIA.... You are on your own. VIA has given absolutely no support for linux. Not even specs to create open source drivers for their hardware. Meaning your Laptop isn't supported by Linux. What you currently have is the best you can get.

EDIT: I'm a doofus! I confused SIS for VIA... D'oh! But VIA support is still pretty bad. There is 2d support for some VIA graphics chips. Need to look up what graphics chip you have

---

### Post by TK999 on 2013-03-12
Hi there, I think the situation can be salvaged :). Try these:
From a terminal (ctrl+alt+t) run:
```

sudo apt-get install xserver-xorg-video-openchrome

```
Then:
```

sudo nano /etc/X11/xorg.conf.d/10-openchrome.conf

```
Into this file, paste the following:
```

Section "Device"
   Identifier "Monitor0"
   Driver "openchrome"
   Option "AccelMethod" "XAA"
EndSection

```

And reboot the system.

---

### Post by caeras on 2013-03-12
I already had the driver and opened the file but I can't save the file once I paste it in?
Thanks for the help

---

### Post by TK999 on 2013-03-12
Ah yes, probably you don't have a default Xorg config file. My bad, sorry.
```

sudo Xorg -configure
sudo nano /etc/X11/xorg.conf.d

```
Once you opened the file, post the results here & quit nano with Ctrl+X.
As for identifying your current screen resolution, type the following into the terminal:
```

xrandr -q

```
, which has a line like "Foobar connected your_screen_width×your_screen_height", e.g "VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 359mm x 287mm"

---

### Post by caeras on 2013-03-12
craig@craig-XubuntuLaptop:~$ sudo Xorg -configure
[sudo] password for craig: 

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) 
craig@craig-XubuntuLaptop:~$ 




Opened file and it is blank




craig@craig-XubuntuLaptop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x720        0.0  
   1024x768       61.0  
   800x600        61.0  
   720x576         0.0  
   720x540         0.0  
   720x480         0.0  
   640x480        60.0  
   1280x768        0.0* 
craig@craig-XubuntuLaptop:~$ 


Hope that is all you needed?  
Thanks again fo the help. Appreciate it!

---

### Post by caeras on 2013-03-13
Do you think there is a solution to this or am I best giving up and throwing a copy of xp on?
Thanks!

---

### Post by TK999 on 2013-03-13
Hm, the screen res should be 1280 × 800. You might want to try this:

When the computer boots, you'll see the GNU GRUB menu (looks like this: [https://upload.wikimedia.org/wikipedia/commons/1/12/GRUB_screenshot.png](https://upload.wikimedia.org/wikipedia/commons/1/12/GRUB_screenshot.png)). Once that menu appears, press the **e **key on your keyboard; this brings up a menu that resembles this:
```

linux   /boot/vmlinuz-linux root=UUID=blah_blah_numbers ro

```
 Append the **bolded** parameters below to the end and leave everything that was already there untouched, so that it will look like this:
```

linux   /boot/vmlinuz-linux root=UUID=blah_blah_numbers ro ***viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD***

```
Tell me if this works; such configs worked for me on a laptop with VIA S3 Unichrome Pro.

---

### Post by caeras on 2013-03-13
Thanks for that but no luck. Exactly the same. I pressed shift to get to grub and ctrl and x out. Tried twice to make sure. When I logged in checked res and it hadn't changed to 800. Appreciate your help. Any other ideas?

---

### Post by TK999 on 2013-03-13
Hm, you would not need to press Ctrl+X to leave GRUB. Press **e **to edit the parameters, and once you entered the parameters, press Enter to boot with them.

---

### Post by caeras on 2013-03-13
Enter just takes me to a new line. Even if I go to the end of all the text. it says at the bottom press f10 or ctrl and x to reboot or esc to discard changes.

---

### Post by TK999 on 2013-03-13
Oh yes, sorry. I accidentally mxied it up with something else. Once you added the parameters, press the **b** key to boot with them. Sorry for the confusion.

---

### Post by caeras on 2013-03-13
B just types the letter b. Ctrl and b goes back a character.

---

### Post by TK999 on 2013-03-13
In this case, edit the GRUB config from a terminal:
```

sudo nano /etc/default/grub

```
Find the line that says GRUB_CMDLINE_LINUX_DEFAULT, and add your options to it:
```

GRUB_CMDLINE_LINUX_DEFAULT="*anything previously there**** viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD***"

```
Save & quit with Ctrl+X, then run
```

sudo update-grub2

```
and reboot.

---

### Post by caeras on 2013-03-13
Thanks. Done that but no change unfortunately. When I check the grub it is altered so updated ok.

---

### Post by TK999 on 2013-03-13
What does the **xrandr -q **command show? If the resolution is 1280 × 800, please provide some further info about the fuzziness -- which parts of the screen it occurs on and the like.

---

### Post by caeras on 2013-03-13
Still showing wrong res on the command:

craig@craig-XubuntuLaptop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x720        0.0  
   1024x768       61.0  
   800x600        61.0  
   720x576         0.0  
   720x540         0.0  
   720x480         0.0  
   640x480        60.0  
   1280x768        0.0* 
craig@craig-XubuntuLaptop:~$ 


Here is the grub file, if you can check it is all as it should?  Maybe I have put something in wrong such as no space, extra space etc:

  GNU nano 2.2.6                              File: /etc/default/grub                                                                   

If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)

^G Get Help           ^O WriteOut           ^R Read File          ^Y Prev Page          ^K Cut Text           ^C Cur Pos
^X Exit               ^J Justify            ^W Where Is           ^V Next Page          ^U UnCut Text         ^T To Spell



The issue is hard to explain, it does appear to be a resolution problem, pictures on my first post explain it, but it is almost like adding extra pixels in, especially text but images don't look right either.

I do appreciate your help, thanks!

---

### Post by TK999 on 2013-03-14
What is in
```

dmesg | grep viafb

```?
I need to see if we configured viafb correctly.

---

### Post by caeras on 2013-03-14
```
craig@craig-XubuntuLaptop:~$ dmesg | grep viafb
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=9ead0ad6-0e02-4484-9f53-20c0834ce14d ro quiet splash viafb.viafb_mode=1280x800 viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=lcd vt.handoff=7
craig@craig-XubuntuLaptop:~$ 


```

viafb.viafb on all occassions is in a pink colour.

thanks

---

### Post by TK999 on 2013-03-14
One more thing we could try... perhaps the viafb driver isn't initialized at all. Let's try this:
```

sudo nano /etc/default/grub

```
----
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD"

```
Change this to:
```

GRUB_CMDLINE_LINUX_DEFAULT="splash **viafb** viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD"

```
Then **sudo update-grub .** With "quiet" gone, perhaps we'll see more useful messages.

---

### Post by caeras on 2013-03-14
Done that but no change. Do you want me to run anything else to show if it made a difference.

---

### Post by TK999 on 2013-03-14
Yes; now that you booted without quite (and hopefully did not reboot since then), try
```

dmesg | grep viafb

```
again and paste it here as there might be more info.

---

### Post by caeras on 2013-03-14
craig@craig-XubuntuLaptop:~$ dmesg | grep viafb
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=9ead0ad6-0e02-4484-9f53-20c0834ce14d ro quiet splash viafb.viafb_mode=1280x800 viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=lcd vt.handoff=7
craig@craig-XubuntuLaptop:~$

---

### Post by caeras on 2013-03-14
Only booted once, results as above.

---

### Post by TK999 on 2013-03-14
There's one more thing I could think of. Edit /etc/default/grub again, and change
```

GRUB_CMDLINE_LINUX_DEFAULT="splash viafb viafb.viafb_mode="1280x800" viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=LCD"

```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=viafb:viafb_mode=1280x800,viafb_lcd_panel_id=19,viafb_active_dev=LCD"

```

---

### Post by caeras on 2013-03-14
Nope, no change to screen:
```
craig@craig-XubuntuLaptop:~$ dmesg | grep viafb
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=9ead0ad6-0e02-4484-9f53-20c0834ce14d ro quiet splash viafb.viafb_mode=1280x800 viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=lcd vt.handoff=7
craig@craig-XubuntuLaptop:~$ 


```

xrand:
```
craig@craig-XubuntuLaptop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x720        0.0  
   1024x768       61.0  
   800x600        61.0  
   720x576         0.0  
   720x540         0.0  
   720x480         0.0  
   640x480        60.0  
   1280x768        0.0* 
craig@craig-XubuntuLaptop:~$ 


```

---

### Post by TK999 on 2013-03-14
I think you might have forgot about running **sudo update-grub **after the last change.

---

### Post by caeras on 2013-03-14
I thought I had but have done it again just to make sure and no change to screen:
Grub:

```
  GNU nano 2.2.6           File: /etc/default/grub                              

If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=viafb:viafb_mode=1280x800,viafb_$
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
                               [ Read 34 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


```

```
craig@craig-XubuntuLaptop:~$ dmesg | grep viafb
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-generic root=UUID=9ead0ad6-0e02-4484-9f53-20c0834ce14d ro quiet splash viafb.viafb_mode=1280x800 viafb.viafb_lcd_panel_id=19 viafb.viafb_active_dev=lcd vt.handoff=7
craig@craig-XubuntuLaptop:~$ 


```

```
craig@craig-XubuntuLaptop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x720        0.0  
   1024x768       61.0  
   800x600        61.0  
   720x576         0.0  
   720x540         0.0  
   720x480         0.0  
   640x480        60.0  
   1280x768        0.0* 
craig@craig-XubuntuLaptop:~$ 


```

---


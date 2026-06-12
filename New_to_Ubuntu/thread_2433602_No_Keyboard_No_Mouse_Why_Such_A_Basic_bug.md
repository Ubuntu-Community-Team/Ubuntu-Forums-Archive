---
title: "No Keyboard No Mouse? Why Such A Basic bug?"
date: 2019-12-22
forum: New to Ubuntu
---

### Post by soundchaser59 on 2019-12-22
I was going to post about installing Ubuntu 19 from usb live and coming up with no keyboard and no mouse, but I ran into a more immediate problem. I logged in to this forum, typed my post, and as soon as I hit "Submit New Thread" it went to a page that said I have to register before I can post, and my post was lost, it even wiped out the "back" history of the Firefox tab so there was no way to go back and see if my typed text was still there. 

Kick me out of the forum when making my first post? And a fundamental and basic "bug" like having no (usb) keyboard or mouse on first install? I guess the great Ubuntu spirit doesn't want me in the club! 

Mint has been nearly flawless for me, so I guess it's back to Mint I go. Unless someone has a quick and painless fix for the no keyboard problem?

---

### Post by QIII on 2019-12-22
You weren't kicked off of the forum.  Something happened with your browser.  We can't control that.

What bug?  You haven't provided any information that would indicate a bug.  

You could ask for help in fixing your issue, or you can go back to Mint.  That's entirely up to you.

---

### Post by soundchaser59 on 2019-12-22
> A thing discovered and shared with others need be discovered only the once.
> **QIII said:**
> You could ask for help in fixing your issue, or you can go back to Mint.
I thought maybe this comment> **soundchaser59 said:**
> Unless someone has a quick and painless fix for the no keyboard problem?would be interpreted as asking for help. This issue is plastered all over the google search results, some of them dated back 6 or 7 years, but every "fix" I read about involves entering commands and downloading extra packages or whatever......but none of them explain how a guy is supposed to do that if I can't even get past the first screen to install Ubuntu because it doesn't recognize that a usb keyboard is attached to my machine. It seems to be a pretty clear Catch-22. (I call it a "bug" for lack of a better term, since it seems to have been an on-going issue for several years now, but I'm a total rookie newbie trying to get a first install to work, so I wouldn't know) 

Does anyone have a fix discovered and ready to share?

---

### Post by QIII on 2019-12-22
Your post was more likely to be interpreted as a gripe.

You would likely get better responses by taking a friendlier tone.  We are all volunteers here.

To get things rolling:  tell us about your hardware -- both the computer and the peripherals.  Be as detailed as you can.

By the way, I, along with millions of people, manage to install and use *buntu with USB peripherals every day.  Your issue may be something unique, or nearly unique, to your hardware.  It may also be a partly incomplete or corrupt installation.

---

### Post by soundchaser59 on 2019-12-22
My frustration gets ahead of me after too many attempts to find a fix on my own for such a seemingly simple problem that already has some history to it. Wasn't supposed to be a gripe, but I can sure see how it would be taken that way. Thanks for listening. 

I have a second (sata) hard drive in this machine that has 64 bit Linux Mint (Cinnamon Mate 19) working, and I am pulling these commands from that command window. That is what I used to create the (32gb) live usb stick with the latest version of Ubuntu on it, 19.1 I believe. Then I disable (disconnect) that hard drive, enable (connect) the ssd drive and set the machine (in bios) to boot to the usb stick. It boots slowly, takes several minutes to start, but eventually comes to the screen where it wants me to choose to install it or run it. I can do nothing because there is no mouse cursor and no keyboard response, can't even turn caps lock on/off or num lock on/off, can't do ctrl+alt+del, etc. Bios is set to allow the usb ports to run as both 1.1 and 2.0, which I mention because I see in the lshw results below that this generic keyboard I have is listed as usb 1.1, while the wireless mouse is listed as usb 2. However, I hope that does not matter since this same keyboard worked fine for the Mint install. 

In case it is not listed below, this machine has 2gb 800mhz ram (bumping up to 4gb in a couple days), AMD Athlon X2 64 bit cpu, Gigabyte mobo, 500gb ssd drive, Radeon video adapter. Nothing dazzling, but should be adequate to run 64 bit Linux. I didn't see any separate downloads for 32 bit vs 64 bit Ubuntu, just the one download, so I assume it will install as a 64 bit OS? Or perhaps there is no 32 bit Ubuntu? (after another look I see now that those specs are listed below!) No peripherals, the only extras are the rw (IDE) dvd drive and the usb wireless mouse and usb keyboard, not sure which model of Dell monitor this is. 

> **QIII said:**
> To get things rolling:  tell us about your hardware -- both the computer and the peripherals.  Be as detailed as you can.

```
rootbeer@SC59:~$ uname -a
Linux SC59 5.0.0-32-generic #34~18.04.2-Ubuntu SMP Thu Oct 10 10:36:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
rootbeer@SC59:~$ sudo lshw
[sudo] password for rootbeer:            
sc59                        
    description: Desktop Computer
    product: M61PME-S2P
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal chassis=desktop uuid=30303234-3144-3032-4636-3835FFFFFFFF
  *-core
       description: Motherboard
       product: M61PME-S2P
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 12/30/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          slot: Socket M2
          size: 2600MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl cpuid extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
             configuration: level=2
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-memory:0
          description: System Memory
          physical id: 18
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             physical id: 0
             slot: A0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns) [empty]
             physical id: 1
             slot: A1
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:7 ioport:e000(size=64) ioport:1c00(size=64) ioport:c400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fa007000-fa007fff
        *-usbhost
             product: OHCI PCI host controller
             vendor: Linux 5.0.0-32-generic ohci_hcd
             physical id: 1
             bus info: usb@2
             logical name: usb2
             version: 5.00
             capabilities: usb-1.10
             configuration: driver=hub slots=10 speed=12Mbit/s
           *-usb:0
                description: Keyboard
                product: USB Keyboard
                vendor: SIGMACHIP
                physical id: 2
                bus info: usb@2:2
                version: 1.10
                capabilities: usb-1.10
                configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
           *-usb:1
                description: Mouse
                product: USB Receiver
                vendor: Logitech
                physical id: 4
                bus info: usb@2:4
                version: 30.00
                capabilities: usb-2.00
                configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
     *-usb:1
          description: USB controller
          product: MCP61 USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fa006000-fa0060ff
        *-usbhost
             product: EHCI Host Controller
             vendor: Linux 5.0.0-32-generic ehci_hcd
             physical id: 1
             bus info: usb@1
             logical name: usb1
             version: 5.00
             capabilities: usb-2.00
             configuration: driver=hub slots=10 speed=480Mbit/s
           *-usb
                description: Generic USB device
                product: 802.11ac WLAN Adapter
                vendor: Realtek
                physical id: 1
                bus info: usb@1:1
                version: 2.00
                serial: 00e04c000001
                capabilities: usb-2.10
                configuration: driver=rtl8812au maxpower=500mA speed=480Mbit/s
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:a000(size=4096)
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:23 memory:fa000000-fa003fff
     *-ide
          description: IDE interface
          product: MCP61 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm isa_compatibility_mode_controller__supports_both_channels_switched_to_pci_native_mode__supports_bus_mastering bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: enp0s7
          version: a2       
          size: 100000000
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.5 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:25 memory:fa004000-fa004fff ioport:c800(size=8)
     *-storage
          description: RAID bus controller
          product: MCP61 SATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fa005000-fa005fff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: NVIDIA Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:0 ioport:b000(size=4096) memory:f8000000-f9ffffff ioport:e0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: Redwood XT [Radeon HD 5670/5690/5730]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0
             bus info: pci@0000:02:00.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=radeon latency=0
             resources: irq:24 memory:e0000000-efffffff memory:f9000000-f901ffff ioport:b000(size=256) memory:c0000-dffff
        *-multimedia
             description: Audio device
             product: Redwood HDMI Audio [Radeon HD 5000 Series]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:26 memory:f9020000-f9023fff
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: a
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GSA-4120B
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A102
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: b
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: CT500MX500SSD1
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 023
             serial: 1846E1D7E1B6
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=16e20f2f
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 8f7ebbfc-72ef-44ef-97d1-efdb30244c19
                size: 465GiB
                capacity: 465GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-12-21 02:22:47 filesystem=ext4 lastmountpoint=/ modified=2019-12-21 22:48:24 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-12-21 22:48:25 state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.11 multicast=yes wireless=IEEE 802.11bgn
rootbeer@SC59:~$ 

```

---

### Post by kurt18947 on 2019-12-22
> **soundchaser59 said:**
> 
.............................
 I logged in to this forum, typed my post, and as soon as I hit "Submit New Thread" it went to a page that said I have to register before I can post, and my post was lost, it even wiped out the "back" history of the Firefox tab so there was no way to go back and see if my typed text was still there. 
..........................


I've used live sessions and more than a few installs. I've never seen a problem with keyboard or pointing device. I can't help with your input device problem but that behavior (loss of post on back button) is the norm for most web sites IME. Having experienced what you experienced, If I'm going to type more than a line or two, I use a text editor of some sort to create the message then copy/paste it into the web page. If the message goes away no problem, paste it again.

---

### Post by olduse78802 on 2019-12-22
I use leafpad if I am going to type more than a small sentence.   Then cut an paste,  If it turns into a long discussion I just continue adding to the leafpad entrys.  That way I have at a glance what I have said.

---

### Post by soundchaser59 on 2019-12-22
> **kurt18947 said:**
> I've used live sessions and more than a few installs. I've never seen a problem with keyboard or pointing device. I can't help with your input device problem but that behavior (loss of post on back button) is the norm for most web sites IME. Having experienced what you experienced, If I'm going to type more than a line or two, I use a text editor of some sort to create the message then copy/paste it into the web page. If the message goes away no problem, paste it again.My experience is the opposite. Very few web sites wipe out the "back" list and prevent me from going back, but maybe that "protocol" is different where entering text is involved. Usually I can go back, even if my text message is not preserved. This one didn't just lose my message post, it would not even let me go back at all. 

Maybe my keyboard issue is related to using older hardware? I googled the problem and there are a bunch of results describing the same problem, some quite recent and some as far back as 7 years, but many of them also seem to be working with old hardware. I've had this machine for 10 years and this is the fourth time I've attempted to refurbish it, but only the second time I've tried to use Linux. The first time was Win XP, the second time was 32 bit Mint, the third time was just last week with a new (to me) 64 bit cpu and 64 bit Mint. But when I ran into the Realtek wireless usb nightmare with Mint, a friend suggested that recent editions of Ubuntu might not have the hardware issues. His own install of Ubuntu got his Realtek wireless usb device working the first time with no problems at all. So this no keyboard no mouse problem really threw me a curve.  
 
Good tip about using a text editor. Sometimes I remember to select all and copy my message before I hit submit, but I missed it this time. Probably a good thing since my original post probably would have sounded a lot more frustrated than the post I started with above.

---

### Post by CatKiller on 2019-12-22
> **soundchaser59 said:**
> Maybe my keyboard issue is related to using older hardware?
Potentially. The thing I would try is to look in the BIOS for a setting called something like Legacy USB Support. During the early parts of the boot process there is no OS loaded, so there is only minimal hardware support; the  support that is there is provided by the BIOS.

---

### Post by soundchaser59 on 2019-12-22
> **CatKiller said:**
> Potentially. The thing I would try is to look in the BIOS for a setting called something like Legacy USB Support.Yup, caught that setting a long time ago with the first install of 32 bit Mint. All usb settings in bios are Enabled. In this bios it is actually called Legacy USB Storage Device. 

Since my last install a day or so ago was 64 bit Mint (after I encountered this no keyboard problem with the Ubuntu bootable usb ) I'm going to download Ubuntu again and make this usb stick bootable again. 
Any suggestions on which version of Ubuntu I should try? (keeping in mind that I consider myself a Linux rookie/newbie)

---

### Post by soundchaser59 on 2019-12-22
This (esp the last post) is the closest I've come to finding any plausible explanation of this problem..... 

[https://askubuntu.com/questions/1038030/ubuntu-18-04-install-try-no-mouse-clicks-possible-and-no-keyboard-input-mou](https://askubuntu.com/questions/1038030/ubuntu-18-04-install-try-no-mouse-clicks-possible-and-no-keyboard-input-mou)

---

### Post by soundchaser59 on 2019-12-22
Howzabout Ubuntu 18.04 ? 

EDIT: I went ahead and made a new bootable usb using the Ubuntu 18.04 image. This time it booted up with both usb keyboard and usb (wireless) mouse working correctly. It is now installing to the 300gb sata drive. 

It is worth noting that earlier today I made a new bootable usb stick image using 18.04 but I used UNETBOOTIN to make the usb stick bootable. When I rebooted - with nothing connected but the usb stick - the machine would not boot. If I hit DEL to go into bios, it would hang on "Entering set up..." If I let it boot it would hang on "Verifying DMI pool data." It simply would not boot to the usb stick. When I tried to boot to live usb with Ubuntu (19.10 I believe it was) but ended up with no keyboard no mouse, that bootable usb was also created using UNETBOOTIN. 

So I went back into Mint and this time I used "USB Image Writer" which is something that comes installed with Mint. I used the same iso file that I had used before, that was saved on my Mint drive. I then went back to having nothing but the usb stick connected and this time the machine booted normally to the usb image...... with keyboard and mouse working correctly. 

So I rebooted with the hdd connected and the image 18.04 is installing to the hdd.

---

### Post by cpt-ankitsharma on 2019-12-23
I wouldn't really install Ubuntu on that hardware. If you want a really fast and responsive system you really have the option of Lubuntu (lightweight version of Ubuntu) or maybe some other light weight distro. 

If you are feeling adventurous and want to learn a bit more about Linux. I can suggest you to install Arch Linux with Xfce environment. There is a ton of support online regarding Arch and I am sure you would easily find solution for any keyboard and pointing devices errors. The first thing you normally do in a Arch install is to setup the keyboard.

---

### Post by kurt18947 on 2019-12-23
> **soundchaser59 said:**
> Howzabout Ubuntu 18.04 ? 

EDIT: I went ahead and made a new bootable usb using the Ubuntu 18.04 image. This time it booted up with both usb keyboard and usb (wireless) mouse working correctly. It is now installing to the 300gb sata drive. 

It is worth noting that earlier today I made a new bootable usb stick image using 18.04 but I used UNETBOOTIN to make the usb stick bootable. When I rebooted - with nothing connected but the usb stick - the machine would not boot. If I hit DEL to go into bios, it would hang on "Entering set up..." If I let it boot it would hang on "Verifying DMI pool data." It simply would not boot to the usb stick. When I tried to boot to live usb with Ubuntu (19.10 I believe it was) but ended up with no keyboard no mouse, that bootable usb was also created using UNETBOOTIN. 

So I went back into Mint and this time I used "USB Image Writer" which is something that comes installed with Mint. I used the same iso file that I had used before, that was saved on my Mint drive. I then went back to having nothing but the usb stick connected and this time the machine booted normally to the usb image...... with keyboard and mouse working correctly. 

So I rebooted with the hdd connected and the image 18.04 is installing to the hdd.

Unetbootin has been a problem for me for some years, at least running under Ubuntu. Usually it won't even start to create a bootable DVD or flash drive. Startup Disk Creator included with Ubuntu has been quite reliable for me of late.

---


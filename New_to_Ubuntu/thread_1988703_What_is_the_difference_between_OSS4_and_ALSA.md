---
title: "What is the difference between OSS4 and ALSA?"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by venom104 on 2012-05-28
Here is my story. I had a TON of issues with ALSA and pulse audio, so I uninstalled them from my system, and installed OSS4 instead. Everything worked fine, except I could not for the life of me, get my microphone to work. After googling for numerous hours and searching linux forums, I gave up and reinstalled ALSA. Turns out that I could only hear output from one program at a time, I googled this, and found out alsa needs a hardware or software mixer to work. I found a solution on the linux mint forums, and installed esound. NOW EVERYTHING WORKS!

My question is, why does ALSA require a mixer when OSS4 does not? OSS4 would allow me to listen to sound from as many programs as I wanted, but not ALSA.

What is the difference?

---

### Post by jtarin on 2012-05-28
Open a terminal and type ```
alsamixer
```this comes with the standard alsa installation. I have never installed esound. I have always used the standard mixer. Too bad I didn't know about your previous problems.

[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

---

### Post by Vereinfachen on 2012-05-28
Okay, here's a little history lesson ;)

In the beginning of Linux multimedia, there was only OSS (it didn't support multiple programs at that time (it's called mixing)). OSSv3 was the default sound system and also in the kernel. Then, the developer changed the license of OSSv4 to a proprietary one, so it was replaced by ALSA. In 2007 however, the developer changed the license of OSSv4 back, so now you have two choices.

OSSv4 has integrated software mixing and ALSA has a plugin called dmix, which enables software mixing aswell. ALSA 1.0.9rc2 and higher will automatically enable dmix, so you don't have to configure anything.

But actually, you don't have to think about this anymore, because later, PulseAudio was invented.

PulseAudio is a wrapper daemon that will take care of everything (including mixing). All modern linux distributions (like Ubuntu) use PulseAudio by default. The esound daemon also got replaced by PulseAudio, because it wasn't developed since 2000 (12 years ago!!!).

So I have to ask you: What the hell are you doing? Remove esound, nobody uses it anymore, reinstall pulseaudio. Why did you remove it in the first place? ^^

---

### Post by prshah on 2012-05-28
> **Vereinfachen said:**
> reinstall pulseaudio.

+1; this is good advice.

Early pulseaudio had a lot of issues; it is now stable and awesome. In most cases, pulseaudio problems are because of:

a) "carried forward" configurations, eg, after an upgrade. Easy to resolve; rename the ~/.pulse folder, and a new one will be created.

b) Underlying issues with ALSA backend; this has nothing to do with pulse.

Pulse is now very mature, and does not need command-line configurations of "sink" and "source" and so on. The pulse applet can help in configuration of volume, device type (2.1/5.1/7.1 etc) as well as advanced configurations such as mutliple sound devices (sound card, webcam, usb sound, etc).

Please post about your hardware to check ALSA compatibility. As long as it works with ALSA, you will have no problems with pulse.

---

### Post by venom104 on 2012-05-28
> **Vereinfachen said:**
> Okay, here's a little history lesson ;)

In the beginning of Linux multimedia, there was only OSS (it didn't support multiple programs at that time (it's called mixing)). OSSv3 was the default sound system and also in the kernel. Then, the developer changed the license of OSSv4 to a proprietary one, so it was replaced by ALSA. In 2007 however, the developer changed the license of OSSv4 back, so now you have two choices.

OSSv4 has integrated software mixing and ALSA has a plugin called dmix, which enables software mixing aswell. ALSA 1.0.9rc2 and higher will automatically enable dmix, so you don't have to configure anything.

But actually, you don't have to think about this anymore, because later, PulseAudio was invented.


PulseAudio is a wrapper daemon that will take care of everything (including mixing). All modern linux distributions (like Ubuntu) use PulseAudio by default. The esound daemon also got replaced by PulseAudio, because it wasn't developed since 2000 (12 years ago!!!).

So I have to ask you: What the hell are you doing? Remove esound, nobody uses it anymore, reinstall pulseaudio. Why did you remove it in the first place? ^^

I don't usually answer questions about what I am attempting to do unless  I feel the question warrants it. I feel it does this time (for the  readers sake). I HAD pulseaudio installed (it was installed by default in my installation, obviously). As I stated previously, I had problems getting alsa to work with more than one program at the same time (I had not heard of esound), but I tried MANY MANY MANY different configurations of my ~/.asoundrc file, and NONE of them worked. So I uninstalled alsa and pulse audio to install OSS4, and everything worked awesomely, except for one problem, my microphone would not work (and I require it for ventilo). After some google-fu, I found this page [http://forums.linuxmint.com/viewtopic.php?f=42&t=70675](http://forums.linuxmint.com/viewtopic.php?f=42&t=70675) . I took the suggestion from there and reinstalled alsa, THEN installed esound (which apparently has pulseaudio as some type of dependency as it was installed as well).

So to answer your question, I had no idea what I was doing. I was simply googling about stuff I didn't know. Everything works now (except the sound in wine seems to cut out) , so I plan on staying with that for a while.

---

### Post by venom104 on 2012-05-28
> **prshah said:**
> +1; this is good advice.

Early pulseaudio had a lot of issues; it is now stable and awesome. In most cases, pulseaudio problems are because of:

a) "carried forward" configurations, eg, after an upgrade. Easy to resolve; rename the ~/.pulse folder, and a new one will be created.

b) Underlying issues with ALSA backend; this has nothing to do with pulse.

Pulse is now very mature, and does not need command-line configurations of "sink" and "source" and so on. The pulse applet can help in configuration of volume, device type (2.1/5.1/7.1 etc) as well as advanced configurations such as mutliple sound devices (sound card, webcam, usb sound, etc).

Please post about your hardware to check ALSA compatibility. As long as it works with ALSA, you will have no problems with pulse.


```

venom@venom-desktop ~ $ sudo lshw
[sudo] password for venom: 
venom-desktop             
    description: Desktop Computer
    product: M68MT-S2 ()
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=desktop uuid=35304535-3439-4430-3541-3442FFFFFFFF
  *-core
       description: Motherboard
       product: M68MT-S2
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: FB
          date: 08/26/2011
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-8120 Eight-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: AMD FX(tm)-8120 Eight-Core Processor
          slot: Socket M2
          size: 3100MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L3 cache
             physical id: a
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
     *-cache
          description: L1 cache
          physical id: 4
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 0
             slot: A0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns)
             physical id: 1
             slot: A1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
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
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:1c40(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
          resources: ioport:b000(size=4096) memory:fdf00000-fdffffff memory:fde00000-fdefffff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fe024000-fe027fff
     *-bridge
          description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth1
          version: a2
          serial: 50:e5:49:d0:5a:4b
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:41 memory:fe02d000-fe02dfff ioport:f000(size=8)
     *-ide:0
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe02c000-fe02cfff
        *-disk
             description: ATA Disk
             product: ST1000DM003-9YN1
             vendor: Seagate
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC47
             serial: Z1D0CCPJ
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=68cab5e3
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: a496-a374
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-02-02 10:07:55 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/windows
                version: 3.1
                serial: 5c34c2e1-10e3-344f-ab46-2f6a2841964e
                size: 292GiB
                capacity: 292GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-02-02 10:07:57 filesystem=ntfs modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /media/transfer
                version: 3.1
                serial: 8cadd7ee-629b-904a-aee1-5d168b39e402
                size: 195GiB
                capacity: 195GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-02-14 05:14:40 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 443GiB
                capacity: 443GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4000MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /boot
                   capacity: 800MiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 438GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: iHAS124   C
             vendor: ATAPI
             physical id: 1
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom1
             logical name: /dev/cdrw1
             logical name: /dev/dvd1
             logical name: /dev/dvdrw1
             logical name: /dev/sr0
             version: LL02
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8.1
          bus info: pci@0000:00:08.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c800(size=16) memory:fe02b000-fe02bfff
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 101
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:a000(size=4096) memory:f8000000-fbffffff ioport:d0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: GF116 [GeForce GTX 550 Ti]
             vendor: nVidia Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:16 memory:f8000000-f9ffffff memory:d0000000-d7ffffff memory:dc000000-dfffffff ioport:ac00(size=128) memory:d8000000-d807ffff
        *-multimedia
             description: Audio device
             product: GF116 High Definition Audio Controller
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:fbffc000-fbffffff
     *-pci:2
          description: Host bridge
          product: Family 15h Processor Function 0
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Family 15h Processor Function 1
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Family 15h Processor Function 2
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 15h Processor Function 3
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 105
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:6
          description: Host bridge
          product: Family 15h Processor Function 4
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 106
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=fam15h_power
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Family 15h Processor Function 5
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 107
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1
       logical name: wlan0
       serial: 00:14:78:78:0e:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.2.0-2-amd64 firmware=1.7 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bg
venom@venom-desktop ~ $ 


```

I am running the ALC887 chipset.

---

### Post by venom104 on 2012-05-28
> **jtarin said:**
> Open a terminal and type ```
alsamixer
```this comes with the standard alsa installation. I have never installed esound. I have always used the standard mixer. Too bad I didn't know about your previous problems.

[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

I appreciate your concern and apologize for my own doing. I used arch-linux for a while and got tired of constantly having to reconfigure some text file to do something, so I came to ubuntu. Anyway, in the arch wiki, it says something to the effect of "it's okay to NOT know everything, but is NOT acceptable to ask for help without doing some research". 

I usually don't ask for help on forums (or in IRC) unless I absolutely cannot fix the issue with the aid of google. Perhaps I should change my way of thinking...

---


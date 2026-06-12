---
title: "Comp Freeze Completely Randomly"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by fattymatty on 2008-11-08
The comp freeze quite often for what seems completely random but probably if i knew more it wouldnt be random but it freeze alot, sometimes while surfing or doing 2 things at one installing new program and surfing or just downloading new program with update manager or downloading updates in terminal or just plain surfing websites or installing wow in wine. basiclly freeze once every 10 minutes depending on what im doing. and when i mean freeze its frozen tried ctrl+alt+backspace but nothing to unfreeze it and never any reports on why its frozen pop up after rebooting

any suggestions

thank you in advance 

  Matt

---

### Post by bscbrit on 2008-11-08
> **fattymatty said:**
> The comp freeze quite often for what seems completely random but probably if i knew more it wouldnt be random but it freeze alot, sometimes while surfing or doing 2 things at one installing new program and surfing or just downloading new program with update manager or downloading updates in terminal or just plain surfing websites or installing wow in wine. basiclly freeze once every 10 minutes depending on what im doing. and when i mean freeze its frozen tried ctrl+alt+backspace but nothing to unfreeze it and never any reports on why its frozen pop up after rebooting
Matt

Matt

Are you running compiz / visual effects?  If you are, try switching off the visual effects (System->Preferences->Appearance->Visual Effects) for a few hours and see if the problem is reduced or even disappears completely.  Let me know how you get on please.

---

### Post by fattymatty on 2008-11-09
Tried doing what was suggested, but didnt seem to have an effect but i did keep track of what was doing everytime it crashed and froze

12:00 - opened wow installer with wine, froze at !% of install. so decided maybe was just wine so went on to something else after holding down power button and turning unit back on after.

12:10 - open firefox, then opened synaptic package manager. freezes comp right away. Then held down power button and turning unit back on after.

12:15: open firefox, was looking for some good extra packages to install found a list of some. opened up system log but didnt understand any of it so just closed it . so opened synaptic package manager put in password and freeze. held down power button and turning unit back on after as computer again wouldnt respond to alt+ctrl+backspace

1225: did hardware testing once computer loaded back up no problems occured or found.decided to download opera 9.5, downloaded fine, started 
install fine and downloaded 2 files needed for install fine but froze when started to insatll package @12:31

12:33 unit back up and hasnt had any problems while typing up this so so confused on whats going on with my unit. current time 12:45

---

### Post by bscbrit on 2008-11-09
When you next start the computer, use the boot menu to select the memory test and let it run for a while.  You either have a very corrupted installation or you have a hardware problem.  You can test the memory as I have suggested, and my next thought would be the video/display system.  You need to make sure that you have the correct driver installed for your video card.

What version of Ubuntu are you using?  How did you install it i.e. was it an upgrade from the previous version or was it a clean install?  What were you doing immediately before the problem began ( e.g. installing software, running a game or other program etc)?

---

### Post by fattymatty on 2008-11-09
I used ultimate boot cd to check my hard drive on friday and it came back with nothing which surprised me so i thought it would of been the drive but apparently not. Its been a problem the entire time ive had it installed so ive reinstalled it once already. its a complete fresh install  8.10

---

### Post by fattymatty on 2008-11-09
the first time i installed i just used my ati on board but then figured since maybe it was that i put my ati x1650 in the comp and ive installed the fglrx driver but the problem was occuring before it too.

---

### Post by bscbrit on 2008-11-09
> Its been a problem the entire time ive had it installed so ive reinstalled it once already. its a complete fresh install 8.10

Do you mean the whole time that you've owned the computer, or since you installed 8.10?  Is it a dual-boot computer?  If it is, does the other operating system still work correctly? If the other OS works then it would indicate that it is a software problem rather than a hardware one.  Was there another OS installed before 8.10 and did you experience any problems with that?

My first suggestion is to check the memory but, if that passes with no obvious faults, then I would suggest that you load 8.04 and try that.  There are some known bugs with 8.10 displays and you may have stumbled upon one of them. There have been significant changes in the code since the previous release.  8.04 is stable and has long-term support (until 2011).  If 8.04 works then we know it is code in 8.10 that is causing the problem and we can investigate further if you wish or you can stay with 8.04 - many people have.  If there are faults with both OS I would tend to suspect a possible hardware problem somewhere.  We can decide how to address that if and when it occurs. 

Does the 8.10 Live Disk function correctly?

---

### Post by fattymatty on 2008-11-09
Yes i used to have window xp on the computer and it ran fine without problems. but now that i formated drive and put on ubuntu 8.1 it has had issues of freezing from begining. i did have to put on some no apci or something on the install to get it to install

also live cd functions perfectly

---

### Post by bscbrit on 2008-11-09
I would recommend that you install 8.04 because it is pointing more and more to a problem caused by something in 8.10.  Intermittent problems are notoriously difficult to debug because you never know if a crash is caused by something that you have just done or whether it is something entirely different.  If XP was working fine then it suggests that it is not hardware but it is possible that it might be a new hardware fault that is just developing.  Starting from 8.04 would give us some additional information:

1. If 8.04 runs but 8.10 doesn't, then we can definitely point the finger at 8.10.

2. If 8.04 exhibits the same problems as 8.10 then there is an problem between your hardware and Ubuntu. I think that this is unlikely and I suspect that 8.04 will function perfectly well.  It would also hint as to whether there is a hardware fault that is just developing.

Once we have that information you can decide how you want to proceed.  8.10 is still having some rough edges smoothed of and, after a few bug fixes and upgrades will probably stabilize such that, if it is currently the cause of your problems - which I suspect that it is - it will be OK for you in a month or two.  My guess at the moment is that there is nothing wrong with your hardware and this is a software problem.

However, you might not want to use your bandwidth downloading another 700MB of data so I really have to leave the decision on what to do next up to you.  Did you burn your 8.10 CD yourself or is it one that you obtained from elsewhere?  I would recommend that if you produced it yourself you burn yourself another one but at slow speed - much less than either your drive or CD would suggest is possible.  If you have produced a corrupt CD then you can only install corrupt software.  I only ever burn my ISOs at about 10x where, in theory, I should be able to burn at 52x.  But I don't get any bad CDs anymore :-)  I spend the extra minutes having a coffee!

What do you want to do next?

---

### Post by fattymatty on 2008-11-09
well I downloaded 8.04 lts from ubuntu.com burned it and installed it first install was going great but froze at 96% restarted and seemed to be okay clicked on system updates was going about 21.5kb/s so thought that was so so i click on firefox to see if it was my side or not and froze so decided to reinstall it to make sure wasnt because it froze at 96%. 

Second time around went through install without error but when went into ubuntu for first time froze up after login once seemed everything was loaded. rebooted computer and when went into ubuntu this time seemed okay so clicked on firefox so i could come one here and post my issue it froze. so rebooted again.

Third time it loaded up fine and firefox loaded fine as well. but seems there is still some sort of problem going on here

Edit: Thought it might of been my display drivers so i updated my ati x1650 driver to the fglrx ati driver so far no crashes but will keep posted

---

### Post by nhasian on 2008-11-09
I dont suppose you have an Intel 4965 wifi adaptor do you?  if so you'll need to install the intrepid backports to stop if from locking up...

---

### Post by fattymatty on 2008-11-09
Nope after update, still having issue where freezing randomly so how do we narrow it down to what is causing the freezing. and prior to installing ran memtest and there was no errors found

---

### Post by fattymatty on 2008-11-10
No dont have a wifi adapter just a normal v2a-vm board with ethernet port.

---

### Post by patrickballeux on 2008-11-10
One thing you could do is using the Vesa graphic driver.  Open your /etc/X11/xorg.conf file using:

```
sudo gedit /etc/X11/xorg.conf
```

Then look for:

```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option	    "TexturedVideo" "on"
	Option	    "XaaNoOffscreenPixmaps"
	Option	    "UseFastTLS" "2"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
	BusID       "PCI:1:5:0"
	Driver	"fglrx"
EndSection

```

The line "Driver", put "vesa" instead of "fglrx".

Reboot.  Display will be a lot slower, and not 3d.  But this will tell your if it's your graphic card driver or not...

Good luck!

---

### Post by bscbrit on 2008-11-10
Have you made any hardware changes to your computer recently?  I'm wondering if there is a hardware conflict somewhere that is causing the problem.  Look at the logs to see what is happening when the freeze occurs (/var/log/messages).  You should be able to find each freeze easily as the time markings will appear different from the markings leading up to it i.e. a delay or big jump.

I note that you earlier said that you had installed a new graphics card, so you seem confident enough to open your computer and change the hardware.  Check that all cables are firmly seated.  Is any component running particularly hot? - check the power supply as a fault here could appear exactly as you have described.  Why did you think that your previous test should have found a problem with the hard drive? ("...which surprised me so i thought it would of been the drive...") ;

Does the system appear to work when using a Live Disk (it will run more slowly than from a hard disk but it should run)?

Please give me full details of your hardware (run 'sudo lshw' while running the Live Disk please).

---

### Post by fattymatty on 2008-11-10
trying that idea with vesa now but also a thought my xorg only has 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

for the card section would that have a major effect on card freezing comp

---

### Post by bscbrit on 2008-11-10
That is a typical xorg.conf under xorg 7.4.  The configuration was, prior to 8.10, controlled by the contents of xorg.conf but that is no longer the case.  The video configuration **can** be influenced by entries in this file but it is no longer the default way of the system being configured.  Unfortunately (- or so it seems to me -) at the same time that they have changed the method of configuration, they have also removed the tools that we used to use to control the configuration to meet our requirements.  That is why I have suggested sticking with 8.04 for the time being.  It is more stable, it is easier to influence the configuration and it has a better set of tools for the user.  I'm not criticising 8.10 it is simply a case of there being a few rough edges.

By all means try the new video settings but, if you don't mind me saying so, we should be looking for a logical way ahead to find what is causing the problem and then solving it.  We are not yet certain that it **is** the video that is the culprit - it might be but there are lots of other things that could give the same problems.  Please see my post of about 25-30 minutes ago.

---

### Post by jbg on 2008-11-10
I have been following this thread, I have the same problem. I was running 8.10 but it kept freezing so I switched back to 8.04 and it froze...I ran the mem test as suggested and it came back with 3 counts (I stopped the test after 2 hrs) of fail bit.the listing said
Test:7
Pass: 2
Address: 00010b2b994
mem: 267.6MB
Good: a9fdlfal
Bad: a9edlfal
Err Bit: 00100000

Same thing came up on 3 counts........what does this mean ?

---

### Post by fattymatty on 2008-11-10
at work at the moment but will post my components when i get home in about 6 hours but. last night i tried the vesa thing and tried to install wow, wine installed without issue but wow froze again at 4% but maybe thats just an issue with wine not to do with the other but dont know. 

I orginally thought it was the hard drive because about two months ago when i had my old board it came up with an error on bios constantly that my hard drive had some issue but it would load fine into xp which was loaded at the time. But then the board eventually bite the dust so i replace with my new asus v2a-vm board which doesnt have the bios error so maybe was the board all along.

when i was having the issue orginally with the freezing i removed my ati x1650 pro 512mb pcie board to see if that was the issue and that didnt solve the issue so i reinstalled the graphics card.

So guess when i get home i will check all connections to see if they are connected firmly and see if anything is running hot also would i test my power supply with a multimeter i guess to see if its putting out the right power and what setting on the multimeter would that be.

---

### Post by fattymatty on 2008-11-10
LiveCD seems to run fine but since i dont install anything and am only using the firefox and terminal it seems to do everything fine is there any command that you think would normally freeze my current setup that i could try in liveCD to see if its working fantasicly

---

### Post by bscbrit on 2008-11-10
fattymatty

I'll wait for your post from home.

---

### Post by fattymatty on 2008-11-10
ubuntu@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=0 uuid=A04C8B05-F030-DD11-B1A2-001FC6C4A8FA
  *-core
       description: Motherboard
       product: M2A-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.XX
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS M2A-VM ACPI BIOS Revision 1705 (03/28/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
          slot: Socket AM2
          size: 2100MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: b
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 2e
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM 800 MHz (1.2 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: Radeon X1650 Pro
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list
                configuration: latency=0
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon X1650 Pro (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 01
                serial: 00:1f:c6:c4:a8:fa
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.197 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-cdrom
                description: DVD-RAM writer
                product: DVDRW LH-20A1S
                vendor: LITE-ON
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /cdrom
                version: 9L09
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /cdrom
                   configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ATIIXP_IDE latency=64 module=atiixp
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: ST3160021A
                   vendor: Seagate
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 8.11
                   serial: 5JS774LM
                   size: 149GiB (160GB)
                   capabilities: ata dma lba iordy smart pm partitioned partitioned:dos
                   configuration: signature=0004f103 smart=on
                 *-volume:0
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      version: 1.0
                      serial: efe6bafc-03e3-4240-95d9-f685c7752862
                      size: 142GiB
                      capacity: 142GiB
                      capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                      configuration: created=2008-11-10 02:53:46 filesystem=ext3 modified=2008-11-11 03:35:22 mounted=2008-11-11 03:31:49 state=clean
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 6236MiB
                      capacity: 6236MiB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 6236MiB
                         capabilities: nofs
        *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master vga_palette
           *-multimedia
                description: Multimedia audio controller
                product: SB Audigy
                vendor: Creative Labs
                physical id: 6
                bus info: pci@0000:03:06.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=EMU10K1_Audigy latency=64 maxlatency=20 mingnt=2 module=snd_emu10k1
           *-input
                description: Input device controller
                product: SB Audigy Game Port
                vendor: Creative Labs
                physical id: 6.1
                bus info: pci@0000:03:06.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=64 module=emu10k1_gp
           *-firewire
                description: FireWire (IEEE 1394)
                product: SB Audigy FireWire Port
                vendor: Creative Labs
                physical id: 6.2
                bus info: pci@0000:03:06.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp

---

### Post by bscbrit on 2008-11-11
I'm still going through all the data but one thing that I have found from Google is that others have had a similar problem with this particular mobo. The problem was found under 7.04 but disappeared when 7.10 was installed.  The actual cause was never identified in the bug report - which isn't good news.  But there were some tips that made the situation better:

As root, edit your /boot/grub/menu.lst

At the end of the line that boots your current kernel add 'acpi=off' e.g.

```
kernel		/vmlinuz-2.6.27-7-generic root=/dev/mapper/laptop-root ro quiet splash acpi=off
```

Try rebooting with that option and see if it makes any difference.

I'll be back later - I'm busy for the next hour or two.

---

### Post by bscbrit on 2008-11-11
Another thing that you can try.  Boot the computer in Recovery Mode i.e from the boot menu select the Recovery Mode option which is usually the second option in the menu.

Once you get to the RM menu, select the option which lets you select a terminal/command line as Root - I'm not sure of the precise wording and cannot look it up here but I think that it will be clear to you.

Let the computer run for at least 30 minutes.  You do not have to use the computer i.e. you do not have to type anything, I just want it to sit there.  This will run everything except graphics and Gnome.  What I'm trying to do is isolate the part of the system that is causing the freezes. Let me know if it freezes by typing a simple command every 5-10 minutes or so e.g. 'ls' .

If that works for a full 30 minutes, create a new user from the command line, giving that user administrative rights so that, if it works, the new user can use 'sudo' like your current main user can.  When you have finished setting the user up, exit from the terminal by typing 'exit' which should return you to the RM menu.  Do a complete reboot and try logging on as the new user.  Run as the new user for as long as you can to see if that removes the freeze problem.  That should keep you busy for a while :-)  Again, let me know how you get on, please.

If you can operate without the computer crashing, do a full update and upgrade using either Synaptic or your preferred command line method e.g. apt-get or aptitude.  There have been quite a few bug fixes over the last week or so and one of them might help.

---

### Post by fattymatty on 2008-11-11
Close but no cigar, well thought id try the apci=off thing first and i really thought that it worked because i was able to use the terminal as well a research what to install as a basics for ubuntu at the same time but it eventually crashed upon going into one website. but will keep at it with this setup for a while longer.

---

### Post by fattymatty on 2008-11-11
k scrap the thought of seemed to work good lol, because update through update manager came up after reboot and froze computer once i started it guess i'll move on to the other suggestion from yesterday

---

### Post by bscbrit on 2008-11-11
If you can just get it stable at the command line without starting any other programs, we should be able to recover it with a little bit of effort.  You can always do the update from the command line:

sudo apt-get update
sudo apt-get upgrade

Give it a try.  Just a quick note, you sounded as though you had started Gnome to get to the command line - you don't need to do this.  As soon as you are logged on as Root from the Recovery Menu you are at the command line.  In fact from there, you can enter the 2 commands above without the use of sudo.  I thought that I would mention this in case you were confused.

---

### Post by fattymatty on 2008-11-11
ya its so randomly freezing its sort of anoying lol like now i rebooted into gnome, went on to forums to write down how to create account in terminal so i could try the other idea and just for the heck of it i redid the update thru the manager and worked fine no freezing and i had left before doing update for 15 minutes to drive wife to work. and then it froze while surfing net lol just cant win lol. in process of trying other idea with ls command and if that works i'll do a new user

---

### Post by fattymatty on 2008-11-11
well the new user seems to be working, i tired updates and upgrades to test new user but wasnt any to download so i tried installing wow and its going before wouldnt go past 7% would freeze up before then but now im past 10% so will see if you fixed the issue or found the issue

---

### Post by bscbrit on 2008-11-11
What is the longest that you have used the command line direct from the Recovery Menu?  It is important because I think it is the graphics that are causing the crash.  Each time you go into Gnome it eventually crashes.  That is why I need you to stay on the Recovery Menu command line and not to start Gnome or any other program.  If we can be sure that it will not crash on the command line then we can start to fix your computer.

---

### Post by fattymatty on 2008-11-11
so i was at the recovery root screen for 45minutes and probably the longest length between ls command would of been somewhere between 10-15 minutes

---

### Post by DrMega on 2008-11-11
> **fattymatty said:**
>  but now that i formated drive and put on ubuntu 8.1 it has had issues of freezing from begining. i did have to put on some no apci or something on the install to get it to install

also live cd functions perfectly

> **fattymatty said:**
> well I downloaded 8.04 lts from ubuntu.com burned it and installed it first install was going great but froze at 96% restarted and seemed to be okay clicked on system updates was going about 21.5kb/s so thought that was so so i click on firefox to see if it was my side or not and froze so decided to reinstall it to make sure wasnt because it froze at 96%. 

Second time around went through install without error but when went into ubuntu for first time froze up after login once seemed everything was loaded. rebooted computer and when went into ubuntu this time seemed okay so clicked on firefox so i could come one here and post my issue it froze. so rebooted again.

Third time it loaded up fine and firefox loaded fine as well. but seems there is still some sort of problem going on here

Edit: Thought it might of been my display drivers so i updated my ati x1650 driver to the fglrx ati driver so far no crashes but will keep posted

You might be affected by [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239021") or [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/252977"). Neither of which apparently exist.

---

### Post by bscbrit on 2008-11-11
DrMega - Thank you, they look interesting.  If it is one of those faults then we are in for a hard time but I'm hoping that with an update and a re-installation of Gnome that we can move forward.  The fact that, at the last report from fattymatty, the 'new' user was not experiencing the same problem leads me to suspect that something in the user's files is also corrupted.

---

### Post by fattymatty on 2008-11-11
okay so seemed to be doing alot better so i basicly just farted around on net while installing stuff and waited for the thing to crash or see if it would. took a while but it did eventually crash. so it installed wow without problem and then tried to download patches but blizzard is so slow so when and torrented them instead on other computer and left the ubuntu one downloading it even thought i was going to stop it later just to see if it would freeze well it didnt so eventually i stopped it and then tried to get zune to work to find out it cant be done on wine so decided to use use gnome symantec driver updater to download acrobat and java while it was doing that i was looking at d3 stuff and seemed fine but eventually it crashed on me

---

### Post by bscbrit on 2008-11-11
Can you please do the update and upgrade from the command line. I explained how to do it a couple of posts back.  Stay on the command line while it is happening because I want to have a successful upgrade without crashing.  I'm calling it a day for today, but I will be back online tomorrow morning.

Cheers and good luck.

---

### Post by fattymatty on 2008-11-11
well it came up with an error of

w:failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-update/release.grg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-update/release.grg) could not resolve ca.archieve.ubuntu.com and did the same for all the other ones as well just didnt want to wrtie it all down to come a post them. ie security.ubuntu.com, medibuntu.org ect.. and upgrade worked but since update didnt nothing to install

---

### Post by bscbrit on 2008-11-11
How do you connect to the internet?  Wifi, ethernet?

---

### Post by fattymatty on 2008-11-11
tried this to get to start up intertnet but still wont work
/etc/init.d/udev restart
/etc/init.d/module-init-tools restart
/etc/init.d/networking start

it worked fine but apt-get doesnt work still

---

### Post by fattymatty on 2008-11-11
ethernet

---

### Post by bscbrit on 2008-11-12
At the command line type 'ifconfig' and it should tell you your IP.  We need to identify whether your ethernet card is configured incorrectly or whether this is a DNS problem.  Read the displayed data carefully and look for an IP, usually in the 192.168.. If it looks like you are connected, try 'ping' your own IP and then try to ping ubuntuforums.org - let me know how you get on please.

If you know where to find the information, have your gateway IP address to hand please.

---

### Post by fattymatty on 2008-11-12
its coming up with
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0   TX bytes:0

but when i run it in gnome with all loaded is this

matty@matt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:c4:a8:fa  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fec4:a8fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2092615 (1.9 MB)  TX bytes:237286 (231.7 KB)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:101100 (98.7 KB)  TX bytes:101100 (98.7 KB)

---

### Post by bscbrit on 2008-11-12
```

auto eth0
iface eth0 inet static
address 192.168.0.197
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

```

Hello fattymatty,

Enter the command line as Root from the Recovery Menu. Copy your existing /etc/network/interfaces to interfaces.old, and then replace its contents with the code above.  I'm guessing at your gateway but it looks a reasonably safe bet. If you then issue the command 'sudo /etc/inet.d/networking restart' it should start your network.

Try pinging 'ubuntuforums.org' and let me know if it is successful.  If it isn't then probably your DNS isn't configured and we will have to sort that out next. If it works, however, then carry on....

If you start Gnome it will probably overwrite the contents of your new interfaces file so until you have completed the next commands, please stay at the command line:

sudo apt-get update
sudo apt-get upgrade

---

### Post by fattymatty on 2008-11-13
well that worked to have it connect to internet and downloaded easily but now when loading into gnome it doesnt freeze but doesnt go all the way in it sits after loging in with the yellow background from login screen

---

### Post by bscbrit on 2008-11-13
Hi again.

Sorry I typed my response without fully understanding what you are seeing.

Is there any disk activity.  Try pressing Ctrl-Alt-Backspace.

---

### Post by fattymatty on 2008-11-25
Been a while since ive been able to work on my comp but it eventually went into ubuntu after loging in this is the error its getting
_______________________________________________________
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
__________________________________________________________________________

so guess its try to fix this error and then back to why freeze all the time but not in terminal

---

### Post by fattymatty on 2008-11-26
okay fixed error it was how we changed the network interface for when testing in terminal but now back to normal well execpt still freezing so back to knowing its only in gnome not terminal it crashes

---

### Post by fattymatty on 2008-11-26
Bump

---

### Post by fattymatty on 2008-11-26
New update: my comp can be just sitting for a while at the desktop and not freeze but its when i start doing things it freezes up just thought id interject that point

---

### Post by fattymatty on 2008-11-28
bump

---

### Post by fattymatty on 2008-11-29
Here is logs of whats going on dont know what to look for if you could help

Nov 28 22:39:58 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Nov 28 22:39:58 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Nov 28 22:39:58 matt-desktop kernel: Loaded 28513 symbols from /boot/System.map-2.6.24-21-generic.
Nov 28 22:39:58 matt-desktop kernel: Symbols match kernel version 2.6.24.
Nov 28 22:39:58 matt-desktop kernel: Loaded 23911 symbols from 94 modules.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:09:30 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] end_pfn_map = 1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F81B0 checksum 0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F81B0, 0024 (r2 ATI   )
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: XSDT CFEE3100, 004C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACP CFEE8440, 00F4 (r3 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: DSDT CFEE3280, 5155 (r1 ATI    ASUSACPI     1000 MSFT  3000000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACS CFEE0000, 0040
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: SSDT CFEE8680, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET CFEE8900, 0038 (r1 ATI    ASUSACPI 42302E31 AWRD       98)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: MCFG CFEE8980, 003C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: APIC CFEE8580, 0084 (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] CPU has 2 num_cores
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] No NUMA configuration found
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal    1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:        0 ->      159
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:      256 ->   851680
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:  1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #1
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Setting APIC routing to flat
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8200 base: 0xfed00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029945
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Policy zone: Normal
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing CPU#0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] TSC calibrated against HPET
Nov 28 22:39:58 matt-desktop kernel: [   17.205040] Marking TSC unstable due to TSCs unsynchronized
Nov 28 22:39:58 matt-desktop kernel: [   17.205042] time.c: Detected 2099.924 MHz processor.
Nov 28 22:39:58 matt-desktop kernel: [   17.206136] Console: colour VGA+ 80x25
Nov 28 22:39:58 matt-desktop kernel: [   17.206139] console [tty0] enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.206157] Checking aperture...
Nov 28 22:39:58 matt-desktop kernel: [   17.206159] CPU 0: aperture @ 348000000 size 32 MB
Nov 28 22:39:58 matt-desktop kernel: [   17.206161] Aperture too small (32 MB)
Nov 28 22:39:58 matt-desktop kernel: [   17.215150] No AGP bridge found
Nov 28 22:39:58 matt-desktop kernel: [   17.215152] Your BIOS doesn't leave a aperture memory hole
Nov 28 22:39:58 matt-desktop kernel: [   17.215153] Please enable the IOMMU option in the BIOS setup
Nov 28 22:39:58 matt-desktop kernel: [   17.215155] This costs you 64 MB of RAM
Nov 28 22:39:58 matt-desktop kernel: [   17.240082] Mapping aperture over 65536 KB of RAM @ 4000000
Nov 28 22:39:58 matt-desktop kernel: [   17.240087] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
Nov 28 22:39:58 matt-desktop kernel: [   17.271260] Memory: 4046344k/4980736k available (2490k kernel code, 146420k reserved, 1318k data, 320k init)
Nov 28 22:39:58 matt-desktop kernel: [   17.271291] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov 28 22:39:58 matt-desktop kernel: [   17.350831] Calibrating delay using timer specific routine.. 4202.95 BogoMIPS (lpj=8405905)
Nov 28 22:39:58 matt-desktop kernel: [   17.350859] Security Framework initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350864] SELinux:  Disabled at boot.
Nov 28 22:39:58 matt-desktop kernel: [   17.350876] AppArmor: AppArmor initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350879] Failure registering capabilities with primary security module.
Nov 28 22:39:58 matt-desktop kernel: [   17.351170] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.353105] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.354044] Mount-cache hash table entries: 256
Nov 28 22:39:58 matt-desktop kernel: [   17.354155] Initializing cgroup subsys ns
Nov 28 22:39:58 matt-desktop kernel: [   17.354158] Initializing cgroup subsys cpuacct
Nov 28 22:39:58 matt-desktop kernel: [   17.354170] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354173] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354175] CPU 0/0 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354177] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354179] CPU: Processor Core ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354198] SMP alternatives: switching to UP code
Nov 28 22:39:58 matt-desktop kernel: [   17.354709] Early unpacking initramfs... done
Nov 28 22:39:58 matt-desktop kernel: [   17.646497] ACPI: Core revision 20070126
Nov 28 22:39:58 matt-desktop kernel: [   17.646544] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 28 22:39:58 matt-desktop kernel: [   17.703526] Using local APIC timer interrupts.
Nov 28 22:39:58 matt-desktop kernel: [   17.751092] Detected 12.499 MHz APIC timer.
Nov 28 22:39:58 matt-desktop kernel: [   17.751176] SMP alternatives: switching to SMP code
Nov 28 22:39:58 matt-desktop kernel: [   17.751575] Booting processor 1/2 APIC 0x1
Nov 28 22:39:58 matt-desktop kernel: [   17.761858] Initializing CPU#1
Nov 28 22:39:58 matt-desktop kernel: [   17.839195] Calibrating delay using timer specific routine.. 4199.90 BogoMIPS (lpj=8399803)
Nov 28 22:39:58 matt-desktop kernel: [   17.839201] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839203] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839205] CPU 1/1 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839207] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839208] CPU: Processor Core ID: 1
Nov 28 22:39:58 matt-desktop kernel: [   17.839302] AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Nov 28 22:39:58 matt-desktop kernel: [   17.839159] Brought up 2 CPUs
Nov 28 22:39:58 matt-desktop kernel: [   17.839496] net_namespace: 120 bytes
Nov 28 22:39:58 matt-desktop kernel: [   17.839867] Time:  6:39:36  Date: 11/29/08
Nov 28 22:39:58 matt-desktop kernel: [   17.839896] NET: Registered protocol family 16
Nov 28 22:39:58 matt-desktop kernel: [   17.840071] ACPI: bus type pci registered
Nov 28 22:39:58 matt-desktop kernel: [   17.840137] PCI: Using configuration type 1
Nov 28 22:39:58 matt-desktop kernel: [   17.845663] ACPI: Interpreter enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.845666] ACPI: (supports S0 S1 S4 S5)
Nov 28 22:39:58 matt-desktop kernel: [   17.845679] ACPI: Using IOAPIC for interrupt routing
Nov 28 22:39:58 matt-desktop kernel: [   17.850054] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 28 22:39:58 matt-desktop kernel: [   17.850220] pci 0000:00:12.0: set SATA to AHCI mode
Nov 28 22:39:58 matt-desktop kernel: [   17.851435] PCI: Transparent bridge - 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.870737] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870832] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870924] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871022] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871114] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871206] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871298] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871389] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871500] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 28 22:39:58 matt-desktop kernel: [   17.871528] pnp: PnP ACPI init
Nov 28 22:39:58 matt-desktop kernel: [   17.871535] ACPI: bus type pnp registered
Nov 28 22:39:58 matt-desktop kernel: [   17.874129] pnpacpi: exceeded the max number of mem resources: 12
Nov 28 22:39:58 matt-desktop kernel: [   17.874179] pnp: PnP ACPI: found 14 devices
Nov 28 22:39:58 matt-desktop kernel: [   17.874181] ACPI: ACPI bus type pnp unregistered
Nov 28 22:39:58 matt-desktop kernel: [   17.874393] PCI: Using ACPI for IRQ routing
Nov 28 22:39:58 matt-desktop kernel: [   17.874396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 28 22:39:58 matt-desktop kernel: [   17.882977] NET: Registered protocol family 8
Nov 28 22:39:58 matt-desktop kernel: [   17.882979] NET: Registered protocol family 20
Nov 28 22:39:58 matt-desktop kernel: [   17.883052] PCI-DMA: Disabling AGP.
Nov 28 22:39:58 matt-desktop kernel: [   17.883416] PCI-DMA: aperture base @ 4000000 size 65536 KB
Nov 28 22:39:58 matt-desktop kernel: [   17.883420] PCI-DMA: using GART IOMMU.
Nov 28 22:39:58 matt-desktop kernel: [   17.883422] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov 28 22:39:58 matt-desktop kernel: [   17.883635] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 28 22:39:58 matt-desktop kernel: [   17.883639] hpet0: 4 32-bit timers, 14318180 Hz
Nov 28 22:39:58 matt-desktop kernel: [   17.884688] AppArmor: AppArmor Filesystem Enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.886925] Time: hpet clocksource has been installed.
Nov 28 22:39:58 matt-desktop kernel: [   17.894924] system 00:01: ioport range 0x4100-0x411f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894927] system 00:01: ioport range 0x228-0x22f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894929] system 00:01: ioport range 0x40b-0x40b has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894931] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894934] system 00:01: ioport range 0xc00-0xc01 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894936] system 00:01: ioport range 0xc14-0xc14 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894938] system 00:01: ioport range 0xc50-0xc52 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894940] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894942] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894945] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894947] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894949] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894954] system 00:01: ioport range 0x4000-0x40fe has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894957] system 00:01: ioport range 0x4210-0x4217 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894959] system 00:01: ioport range 0xb10-0xb1f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894968] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894970] system 00:07: ioport range 0x220-0x225 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894980] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894986] system 00:0d: iomem range 0xcf600-0xcffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894988] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894990] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894993] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894995] system 00:0d: iomem range 0xcfef0000-0xcffeffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894998] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895001] system 00:0d: iomem range 0xcfee0000-0xcfefffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895003] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895005] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895008] system 00:0d: iomem range 0x100000-0xcfedffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895010] system 00:0d: iomem range 0x0-0x0 could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895012] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895392] PCI: Bridge: 0000:00:02.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895394]   IO window: d000-dfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895397]   MEM window: fdb00000-fdbfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895399]   PREFETCH window: d0000000-dfffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895403] PCI: Bridge: 0000:00:07.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895405]   IO window: e000-efff
Nov 28 22:39:58 matt-desktop kernel: [   17.895407]   MEM window: fdf00000-fdffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895409]   PREFETCH window: fdc00000-fdcfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895413] PCI: Bridge: 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.895415]   IO window: c000-cfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895420]   MEM window: fde00000-fdefffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895423]   PREFETCH window: fdd00000-fddfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895461] NET: Registered protocol family 2
Nov 28 22:39:58 matt-desktop kernel: [   17.930974] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.932183] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.935814] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.936297] TCP: Hash tables configured (established 524288 bind 65536)
Nov 28 22:39:58 matt-desktop kernel: [   17.936301] TCP reno registered
Nov 28 22:39:58 matt-desktop kernel: [   17.946962] checking if image is initramfs... it is
Nov 28 22:39:58 matt-desktop kernel: [   18.515725] Freeing initrd memory: 7549k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.520419] audit: initializing netlink socket (disabled)
Nov 28 22:39:58 matt-desktop kernel: [   18.520429] audit(1227940776.264:1): initialized
Nov 28 22:39:58 matt-desktop kernel: [   18.522301] VFS: Disk quotas dquot_6.5.1
Nov 28 22:39:58 matt-desktop kernel: [   18.522370] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   18.522486] io scheduler noop registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522488] io scheduler anticipatory registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522489] io scheduler deadline registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522585] io scheduler cfq registered (default)
Nov 28 22:39:58 matt-desktop kernel: [   18.782345] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.782437] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.808223] Real Time Clock Driver v1.12ac
Nov 28 22:39:58 matt-desktop kernel: [   18.808404] Linux agpgart interface v0.102
Nov 28 22:39:58 matt-desktop kernel: [   18.808406] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 28 22:39:58 matt-desktop kernel: [   18.808547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.809095] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.810033] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 28 22:39:58 matt-desktop kernel: [   18.810096] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 28 22:39:58 matt-desktop kernel: [   18.810180] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.810182] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Nov 28 22:39:58 matt-desktop kernel: [   18.810275] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825716] mice: PS/2 mouse device common for all mice
Nov 28 22:39:58 matt-desktop kernel: [   18.825750] cpuidle: using governor ladder
Nov 28 22:39:58 matt-desktop kernel: [   18.825752] cpuidle: using governor menu
Nov 28 22:39:58 matt-desktop kernel: [   18.825887] NET: Registered protocol family 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825974] registered taskstats version 1
Nov 28 22:39:58 matt-desktop kernel: [   18.826093]   Magic number: 0:976:671
Nov 28 22:39:58 matt-desktop kernel: [   18.826202] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Nov 28 22:39:58 matt-desktop kernel: [   18.826205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 28 22:39:58 matt-desktop kernel: [   18.826207] EDD information not available.
Nov 28 22:39:58 matt-desktop kernel: [   18.826214] Freeing unused kernel memory: 320k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.826595] Write protecting the kernel read-only data: 1036k
Nov 28 22:39:58 matt-desktop kernel: [   18.854326] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 28 22:39:58 matt-desktop kernel: [   20.012699] fuse init (API version 7.9)
Nov 28 22:39:58 matt-desktop kernel: [   20.025134] ACPI: Fan [FAN] (on)
Nov 28 22:39:58 matt-desktop kernel: [   20.029538] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.029550] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.030823] ACPI: Thermal Zone [THRM] (40 C)
Nov 28 22:39:58 matt-desktop kernel: [   20.384272] usbcore: registered new interface driver usbfs
Nov 28 22:39:58 matt-desktop kernel: [   20.384167] SCSI subsystem initialized
Nov 28 22:39:58 matt-desktop kernel: [   20.390145] usbcore: registered new interface driver hub
Nov 28 22:39:58 matt-desktop kernel: [   20.393883] usbcore: registered new device driver usb
Nov 28 22:39:58 matt-desktop kernel: [   20.396075] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 28 22:39:58 matt-desktop kernel: [   20.396105] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   20.396367] eth0: RTL8168b/8111b at 0xffffc20001032000, 00:1f:c6:c4:a8:fa, XID 38000000 IRQ 509
Nov 28 22:39:58 matt-desktop kernel: [   20.399509] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   20.399675] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.399939] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 28 22:39:58 matt-desktop kernel: [   20.399967] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Nov 28 22:39:58 matt-desktop kernel: [   20.433381] Floppy drive(s): fd0 is 1.44M
Nov 28 22:39:58 matt-desktop kernel: [   20.451212] FDC 0 is a post-1991 82077
Nov 28 22:39:58 matt-desktop kernel: [   20.460283] usb usb1: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.460306] hub 1-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.460316] hub 1-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.564093] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.564268] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.564327] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 28 22:39:58 matt-desktop kernel: [   20.564349] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Nov 28 22:39:58 matt-desktop kernel: [   20.624020] usb usb2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.624040] hub 2-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.624050] hub 2-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.727851] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   20.728019] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.728076] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 28 22:39:58 matt-desktop kernel: [   20.728102] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Nov 28 22:39:58 matt-desktop kernel: [   20.787789] usb usb3: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.787809] hub 3-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.787818] hub 3-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.891629] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.891799] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.891857] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov 28 22:39:58 matt-desktop kernel: [   20.891874] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Nov 28 22:39:58 matt-desktop kernel: [   20.951592] usb usb4: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.951615] hub 4-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.951625] hub 4-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.054917] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   21.055087] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   21.055147] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov 28 22:39:58 matt-desktop kernel: [   21.055166] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Nov 28 22:39:58 matt-desktop kernel: [   21.114853] usb usb5: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.114875] hub 5-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   21.114884] hub 5-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.214518] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   21.214697] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 28 22:39:58 matt-desktop kernel: [   21.214703] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 28 22:39:58 matt-desktop kernel: [   21.525963] usb 5-2: new low speed USB device using ohci_hcd and address 2
Nov 28 22:39:58 matt-desktop kernel: [   21.753023] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.766572] usbcore: registered new interface driver hiddev
Nov 28 22:39:58 matt-desktop kernel: [   21.773072] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input2
Nov 28 22:39:58 matt-desktop kernel: [   21.802333] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   21.802345] usbcore: registered new interface driver usbhid
Nov 28 22:39:58 matt-desktop kernel: [   21.802348] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov 28 22:39:58 matt-desktop kernel: [   22.217065] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 28 22:39:58 matt-desktop kernel: [   22.217070] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Nov 28 22:39:58 matt-desktop kernel: [   22.218026] scsi0 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218313] scsi1 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218455] scsi2 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218594] scsi3 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218663] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218667] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218671] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218674] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.692386] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   22.861287] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L09, max UDMA/100, ATAPI AN
Nov 28 22:39:58 matt-desktop kernel: [   23.029131] ata1.00: configured for UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   23.339497] ata2: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.651069] ata3: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.962643] ata4: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.964011] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L09 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   23.965004] ACPI: PCI Interrupt 0000:03:06.2[B] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   23.966241] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   23.966405] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   23.966461] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov 28 22:39:58 matt-desktop kernel: [   23.966503] ehci_hcd 0000:00:13.5: debug port 1
Nov 28 22:39:58 matt-desktop kernel: [   23.966520] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Nov 28 22:39:58 matt-desktop kernel: [   24.015082] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 28 22:39:58 matt-desktop kernel: [   24.014913] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 28 22:39:58 matt-desktop kernel: [   24.015022] usb usb6: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.015044] hub 6-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   24.015052] hub 6-0:1.0: 10 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   24.015405] usb 5-2: USB disconnect, address 2
Nov 28 22:39:58 matt-desktop kernel: [   24.022517] Driver 'sr' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.031125] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 28 22:39:58 matt-desktop kernel: [   24.031130] Uniform CD-ROM driver Revision: 3.20
Nov 28 22:39:58 matt-desktop kernel: [   24.035040] sr 0:0:0:0: Attached scsi generic sg0 type 5
Nov 28 22:39:58 matt-desktop kernel: [   24.118621] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   24.119495] scsi4 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120061] scsi5 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120491] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
Nov 28 22:39:58 matt-desktop kernel: [   24.120494] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
Nov 28 22:39:58 matt-desktop kernel: [   24.338563] ata5.00: ATA-6: ST3160021A, 8.11, max UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   24.338566] ata5.00: 312581808 sectors, multi 1: LBA48 
Nov 28 22:39:58 matt-desktop kernel: [   24.338576] ata5.00: limited to UDMA/33 due to 40-wire cable
Nov 28 22:39:58 matt-desktop kernel: [   24.354510] ata5.00: configured for UDMA/33
Nov 28 22:39:58 matt-desktop kernel: [   24.510985] scsi 4:0:0:0: Direct-Access     ATA      ST3160021A       8.11 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   24.511053] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Nov 28 22:39:58 matt-desktop kernel: [   24.519622] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 28 22:39:58 matt-desktop kernel: [   24.519628] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 28 22:39:58 matt-desktop kernel: [   24.541416] Driver 'sd' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.541500] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541509] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541525] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541563] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541571] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541584] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541587]  sda: sda1 sda2 < sda5 >
Nov 28 22:39:58 matt-desktop kernel: [   24.573016] sd 4:0:0:0: [sda] Attached SCSI disk
Nov 28 22:39:58 matt-desktop kernel: [   24.665904] usb 5-2: new low speed USB device using ohci_hcd and address 3
Nov 28 22:39:58 matt-desktop kernel: [   24.848219] Attempting manual resume
Nov 28 22:39:58 matt-desktop kernel: [   24.880556] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 28 22:39:58 matt-desktop kernel: [   24.880560] EXT3-fs: write access will be enabled during recovery.
Nov 28 22:39:58 matt-desktop kernel: [   24.892914] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.902011] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input3
Nov 28 22:39:58 matt-desktop kernel: [   24.926095] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   25.428215] kjournald starting.  Commit interval 5 seconds
Nov 28 22:39:58 matt-desktop kernel: [   25.428230] EXT3-fs: sda1: orphan cleanup on readonly fs
Nov 28 22:39:58 matt-desktop kernel: [   25.428260] EXT3-fs: sda1: 1 orphan inode deleted
Nov 28 22:39:58 matt-desktop kernel: [   25.428262] EXT3-fs: recovery complete.
Nov 28 22:39:58 matt-desktop kernel: [   25.442180] EXT3-fs: mounted filesystem with ordered data mode.
Nov 28 22:39:58 matt-desktop kernel: [   35.029771] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 28 22:39:58 matt-desktop kernel: [   35.585166] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 28 22:39:58 matt-desktop kernel: [   35.585199] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Nov 28 22:39:58 matt-desktop kernel: [   35.674740] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 28 22:39:58 matt-desktop kernel: [   35.711237] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 28 22:39:58 matt-desktop kernel: [   35.795452] input: Power Button (FF) as /devices/virtual/input/input5
Nov 28 22:39:58 matt-desktop kernel: [   35.838585] gameport: EMU10K1 is pci0000:03:06.1/gameport0, io 0xce00, speed 607kHz
Nov 28 22:39:58 matt-desktop kernel: [   35.855225] ACPI: Power Button (FF) [PWRF]
Nov 28 22:39:58 matt-desktop kernel: [   35.855284] input: Power Button (CM) as /devices/virtual/input/input6
Nov 28 22:39:58 matt-desktop kernel: [   35.919133] ACPI: Power Button (CM) [PWRB]
Nov 28 22:39:58 matt-desktop kernel: [   35.945160] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 28 22:39:58 matt-desktop kernel: [   36.231814] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 28 22:39:58 matt-desktop kernel: [   36.250659] [fglrx] Maximum main memory to use for locked dma buffers: 3797 MBytes.
Nov 28 22:39:58 matt-desktop kernel: [   36.250689] [fglrx] ASYNCIO init succeed!
Nov 28 22:39:58 matt-desktop kernel: [   36.250972] [fglrx] PAT is enabled successfully!
Nov 28 22:39:58 matt-desktop kernel: [   36.250998] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Nov 28 22:39:58 matt-desktop kernel: [   36.490050] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   36.556714] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov 28 22:39:58 matt-desktop kernel: [   36.563192] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
Nov 28 22:39:58 matt-desktop kernel: [   37.602403] lp0: using parport0 (interrupt-driven).
Nov 28 22:39:58 matt-desktop kernel: [   37.716151] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
Nov 28 22:39:58 matt-desktop kernel: [   38.271599] EXT3 FS on sda1, internal journal
Nov 28 22:39:58 matt-desktop kernel: [   39.308038] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 28 22:39:58 matt-desktop kernel: [   39.602862] No dock devices found.
Nov 28 22:39:58 matt-desktop kernel: [   39.937700] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)
Nov 28 22:39:58 matt-desktop kernel: [   39.937503] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
Nov 28 22:39:58 matt-desktop kernel: [   39.937507] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
Nov 28 22:39:58 matt-desktop kernel: [   39.937509] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
Nov 28 22:39:58 matt-desktop kernel: [   39.937511] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Nov 28 22:39:59 matt-desktop kernel: [   41.066516] ppdev: user-space parallel port driver
Nov 28 22:39:59 matt-desktop kernel: [   41.247176] audit(1227940799.749:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5155 profile="/usr/sbin/cupsd" namespace="default"
Nov 28 22:39:59 matt-desktop dhcdbd: Started up.
Nov 28 22:40:00 matt-desktop kernel: [   41.941185] Clocksource tsc unstable (delta = -261917412 ns)
Nov 28 22:40:01 matt-desktop kernel: [   42.384723] r8169: eth0: link up
Nov 28 22:40:02 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 28 22:40:04 matt-desktop kernel: [   43.612850] Bluetooth: Core ver 2.11
Nov 28 22:40:04 matt-desktop kernel: [   43.613341] NET: Registered protocol family 31
Nov 28 22:40:04 matt-desktop kernel: [   43.613346] Bluetooth: HCI device and connection manager initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.613350] Bluetooth: HCI socket layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.625083] Bluetooth: L2CAP ver 2.9
Nov 28 22:40:04 matt-desktop kernel: [   43.625088] Bluetooth: L2CAP socket layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664575] Bluetooth: RFCOMM socket layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664591] Bluetooth: RFCOMM TTY layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664593] Bluetooth: RFCOMM ver 1.8
Nov 28 22:40:04 matt-desktop kernel: [   43.679466] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:40:05 matt-desktop kernel: [   43.980825] NET: Registered protocol family 17
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Nov 28 22:40:05 matt-desktop kernel: [   44.396785] [fglrx] Reserve Block - 0 offset =  0X1fffb000 length = 0X5000
Nov 28 22:40:05 matt-desktop kernel: [   44.396790] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov 28 22:40:05 matt-desktop kernel: [   44.396792] [fglrx] Reserve Block - 2 offset =  0Xffc0000 length = 0X40000
Nov 28 22:40:05 matt-desktop kernel: [   44.426803] [fglrx] interrupt source 20008000 successfully enabled
Nov 28 22:40:05 matt-desktop kernel: [   44.426808] [fglrx] enable ID = 0x00000008
Nov 28 22:40:05 matt-desktop kernel: [   44.426815] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Nov 28 22:40:06 matt-desktop kernel: [   44.910680] NET: Registered protocol family 10
Nov 28 22:40:06 matt-desktop kernel: [   44.910915] lo: Disabled Privacy Extensions
Nov 28 22:40:15 matt-desktop kernel: [   48.567982] hda-intel: Invalid position buffer, using LPIB read method instead.

Froze at this point

---


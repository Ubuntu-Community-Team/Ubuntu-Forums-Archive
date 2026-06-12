---
title: "New user having freeze problems"
date: 2015-06-16
forum: New to Ubuntu
---

### Post by tim125 on 2015-06-16
I have recently installed Ubuntu 15.04 onto to an Acer desktop computer, all seemed to go well on the installation to a clean SATA drive, after the re-boot the computer sprang to life for a minute or so, then froze, no mouse or keyboard activity. 
I tried another clean IDE drive as the board had an IDE socket and cable still the same result.

Thanks in advance.

I am a new user to this so forgive my limited knowledge

---

### Post by RobGoss on 2015-06-16
Hello and welcome, If you don't mind posting the specs for your machine it will help others t help you.

---

### Post by Vladlenin5000 on 2015-06-16
> **RobGoss said:**
> Hello and welcome, If you don't mind posting the specs for your machine it will help others t help you.

+1
... And considering the symptom you described, testing the drive would be very low in my troubleshooting list. Further considerations and eventual hypotheses after you post the specs.

---

### Post by tim125 on 2015-06-17
Does this help


[https://mail.google.com/mail/ca/u/0/?ui=2&ik=46b7cf4db7&view=fimg&th=14e027395cf446bd&attid=0.1&disp=inline&realattid=28343c75bf058a9c_0.1&safe=1&attbid=ANGjdJ8McMgGdkaMCIoZfLvZsLjMHrnR5mvrqRwKwOrzP94nSrRJbrKPS93d9XbOdB55todKLj7wTM-WXWP8UHFc6dPK6BQf-PS2Zk5kqSbN2U_CGni7CQWQ2bzO0VM&ats=1434560268326&rm=14e027395cf446bd&zw&sz=w1338-h500](https://mail.google.com/mail/ca/u/0/?ui=2&ik=46b7cf4db7&view=fimg&th=14e027395cf446bd&attid=0.1&disp=inline&realattid=28343c75bf058a9c_0.1&safe=1&attbid=ANGjdJ8McMgGdkaMCIoZfLvZsLjMHrnR5mvrqRwKwOrzP94nSrRJbrKPS93d9XbOdB55todKLj7wTM-WXWP8UHFc6dPK6BQf-PS2Zk5kqSbN2U_CGni7CQWQ2bzO0VM&ats=1434560268326&rm=14e027395cf446bd&zw&sz=w1338-h500)

---

### Post by deadflowr on 2015-06-17
> **tim125 said:**
> Does this help


[https://mail.google.com/mail/ca/u/0/?ui=2&ik=46b7cf4db7&view=fimg&th=14e027395cf446bd&attid=0.1&disp=inline&realattid=28343c75bf058a9c_0.1&safe=1&attbid=ANGjdJ8McMgGdkaMCIoZfLvZsLjMHrnR5mvrqRwKwOrzP94nSrRJbrKPS93d9XbOdB55todKLj7wTM-WXWP8UHFc6dPK6BQf-PS2Zk5kqSbN2U_CGni7CQWQ2bzO0VM&ats=1434560268326&rm=14e027395cf446bd&zw&sz=w1338-h500](https://mail.google.com/mail/ca/u/0/?ui=2&ik=46b7cf4db7&view=fimg&th=14e027395cf446bd&attid=0.1&disp=inline&realattid=28343c75bf058a9c_0.1&safe=1&attbid=ANGjdJ8McMgGdkaMCIoZfLvZsLjMHrnR5mvrqRwKwOrzP94nSrRJbrKPS93d9XbOdB55todKLj7wTM-WXWP8UHFc6dPK6BQf-PS2Zk5kqSbN2U_CGni7CQWQ2bzO0VM&ats=1434560268326&rm=14e027395cf446bd&zw&sz=w1338-h500)

No, it gives me a 403 forbidden.

A better way to get the info to us, is to boot an installation cd, select the option Try Ubuntu.
Boot into it.
Open a terminal window (you can either search ubuntu's menu system, or try pressing ctrl+alt +T)
and run
```
sudo lshw
```
then highlight the output and copy, then open Firefox and navigate to the forums, then login come to this page and paste the output into code tags.
see: [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168) on using code tags.
(Use code tags, please.)

my guess, though without any other knowledge to go by, would be that your gpu has insufficient drivers...

I'm also hopeful that a livecd session might run longer than the install, which can happen.
If the livecd try ubuntu method also fails, then it'll be time to look at another method.

---

### Post by tim125 on 2015-06-18
Thanks for the info, 
I tried to do as mentioned, I ran the o/s from the CD, I copied the system info then it froze !! I have installed the 32 & 64 bit versions and get the same results, I have also installed from two different media (CD & USB) I can open the settings window and sometimes the firefox but after a click here and there it freezes.

I will try again tomorrow to see if I can post the system info

---

### Post by deadflowr on 2015-06-18
Other route wold be to post everything you might know about the machine, like make and model.

---

### Post by mastablasta on 2015-06-19
a screenshot from BIOS for example. also the GPU model is important in this case.

try a lighter distro something that doesn't use hardware acceleration like Lubuntu or if force the boot in VGA mode (not sure if it's possible in Ubuntu)

---

### Post by leunam12 on 2015-06-19
Sounds like the CPU heatsink has a lot of dust or maybe the fan is stopping or not working well; or maybe a power supply issue.

---

### Post by akash14 on 2015-06-19
hello, i am also new user and this same problem happens for me when i was coding website in ATOM Editor.. i am also waiting if there any solution,
Thanks in Advance :)

---

### Post by oldrocker99 on 2015-06-19
I had the same lockup problem with a new motherboard, and it turned out to be badly seated RAM. Do reseat the RAM and check that out; it worked for me.

By the way, GRUB offers the excellent Memtest86+, which will find anything bad in your RAM. It takes several hours to complete one pass, so you might want to run it all night. If it does find errors, there is the source of your lockup.

---

### Post by tim125 on 2015-06-19
This is the code,
 I installed Linux Mint and had the same trouble, HOWEVER after a reboot with the Mnt o/s, the option came up to boot  without the video drivers and everything is running great, I have copied the code using the same method as was suggested and am typing this with no problems, been on the internet and all is fine ;)

So what do I need to do to make it work on Ubuntu ?



```
    version: R02-B0    serial: PSM44E1U13839024691800
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=0021856C-E8BB-2008-1004-062152000000
  *-core
       description: Motherboard
       product: MCP73O
       vendor: ACER
       physical id: 0
       version: NVIDIA MCP73O
       serial: 000000000
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R02-B0
          date: 07/18/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E4700  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: SOCKET775 M/B
          size: 2603MHz
          capacity: 2603MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 17
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          size: 2603MHz
          capacity: 2603MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: MCP73 Host Bridge
          vendor: NVIDIA Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: nForce 630i memory controller
             vendor: NVIDIA Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP73 LPC Bridge
             vendor: NVIDIA Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
             resources: ioport:4f00(size=256)
        *-serial
             description: SMBus
             product: MCP73 SMBus
             vendor: NVIDIA Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0
             resources: irq:11 ioport:4900(size=64) ioport:4d00(size=64) ioport:4e00(size=64)
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-processor UNCLAIMED
             description: Co-processor
             product: MCP73 Co-processor
             vendor: NVIDIA Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: latency=0 maxlatency=1 mingnt=3
             resources: memory:feb80000-febfffff
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: MCP73 Memory Controller
             vendor: NVIDIA Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB controller
             product: GeForce 7100/nForce 630i USB
             vendor: NVIDIA Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:23 memory:feb7f000-feb7ffff
        *-usb:1
             description: USB controller
             product: MCP73 [nForce 630i] USB 2.0 Controller (EHCI)
             vendor: NVIDIA Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0 maxlatency=1 mingnt=3
             resources: irq:22 memory:feb7ec00-feb7ecff
        *-ide:0
             description: IDE interface
             product: MCP73 IDE
             vendor: NVIDIA Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-multimedia
             description: Audio device
             product: MCP73 High Definition Audio
             vendor: NVIDIA Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
             resources: irq:23 memory:feb78000-feb7bfff
        *-pci:0
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-pci:1
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40
        *-pci:2
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41
        *-pci:3
             description: PCI bridge
             product: MCP73 PCI Express bridge
             vendor: NVIDIA Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42
        *-ide:1
             description: IDE interface
             product: MCP73 IDE
             vendor: NVIDIA Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
             resources: irq:20 ioport:e480(size=8) ioport:e400(size=4) ioport:e080(size=8) ioport:e000(size=4) ioport:dc00(size=16) memory:feb7c000-feb7dfff
        *-network
             description: Ethernet interface
             product: MCP73 Ethernet
             vendor: NVIDIA Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: a2
             serial: 00:21:85:6c:e8:bb
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:43 memory:feb77000-feb77fff ioport:d880(size=8) memory:feb7e800-feb7e8ff memory:feb7e400-feb7e40f
        *-display UNCLAIMED
             description: VGA compatible controller
             product: C73 [GeForce 7050 / nForce 630i]
             vendor: NVIDIA Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a2
             width: 64 bits
             clock: 66MHz
             capabilities: pm msi vga_controller bus_master cap_list
             configuration: latency=0
             resources: memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fc000000-fcffffff memory:feb40000-feb5ffff
     *-scsi:0
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST380013AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 3.00
             serial: 4MR0NNYG
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0003252c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 86dcc21d-e6d0-45e2-97fc-0abf2fd4c9f3
                size: 72GiB
                capacity: 72GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2015-06-19 15:54:04 filesystem=ext4 lastmountpoint=/ modified=2015-06-19 16:04:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-06-19 16:04:16 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 1790MiB
                capacity: 1790MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1790MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GH15F
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: EG00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 5
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:10
       logical name: wlan0
       serial: f4:ec:38:8a:5a:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ath9k_htc driverversion=3.13.0-37-generic firmware=1.3 ip=192.168.1.122 link=yes multicast=yes wireless=IEEE 802.11bgn



```

---

### Post by tim125 on 2015-06-19
Hi, I installed Linux Mint today and the same problem occurred HOWEVER !! when I re-booted it gave me the option to boot without the graphic/video drivers and hey presto everything worked great, all programmes and the internet, used it for an hour or so and no problems. I will copy the system info but had to go home and the computer is not there.

I am assuming it must be a driver problem with the graphics, there is no separate card they run off the motherboard.

---

### Post by deadflowr on 2015-06-19
I think you should be able to just install the driver marked as nvidia-current

I would think the safest way to do so without running into the lockup would be to boot up and when you get to the login screen, ignore logging in like normal and instead press ctrl + alt + F1.
It'll bring up a console fullscreen window with a login prompt.
Login like normal, username and password then run
```
sudo apt-get install nvidia-current
```
When it finishes do a reboot, like so:
```
sudo reboot
```
Then when it restarts log in like normal, and open the progam nvidia xserver settings.
The name might be slightly different.

It'll open the nvidia configuration program.
set whatever settings you want, like resolution.
Then in one of the selections should be an option to save x configuration.
Click on that and save.
(It'll ask for a user password to do this, becasue it will write the settings to the system.)
from then on it should boot up with whatever settings you set.

Hope this helps.

added: reference here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
As far as I can tell nvidia-current should be the nvidia-304 driver.

---

### Post by tim125 on 2015-06-20
I did this on the Mint o/s and it is going like a train....  

Thanks for the help

---


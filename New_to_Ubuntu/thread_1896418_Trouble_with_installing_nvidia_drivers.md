---
title: "Trouble with installing nvidia drivers"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by garyhibdon on 2011-12-16
i know this is an old topic, but im having a similiar problem with mine.

i am running 11.10 and have a nvidia 8800 gts. went through additional drivers and when i use the recomended one it still wont configure it properly. 
for some reason as the computer loads, i get white lines straight up and down the screen as it loads. and any time i try to play a game, it says that the picture is out of frequency.


any help would be great. thanks in advance!

---

### Post by overdrank on 2011-12-16
Hi and I have moved your post to it's own thread. No need to revive a old thread. :)

---

### Post by wildmanne39 on 2011-12-16
Hi, if there are other drivers listed in the additional drivers section try another one until you hopefully find one that works, if not you can install one from nvidia website but it is a little more difficult.
Thanks

---

### Post by garyhibdon on 2011-12-17
ive actually tried all the available drivers listed via additional drivers.

is there a way to use the terminal to install the drivers from nvidias site?

---

### Post by garyhibdon on 2011-12-17
and to extend an explanation, i can play the games in windowed mode. its just when they try to go full screen that i get the errors. does this change anything?

---

### Post by wildmanne39 on 2011-12-17
Hi please run these commands in a terminal and post the results here:
```
lsmod
```
```
lspci | grep VGA
```
```
sudo lshw
```

The errors when you play your games does not sound like a driver problem, maybe you need to set your frequency rate in your x.org file but I am not the best person to tell you how to do that and the file will have to be created to do that.

The lines when you boot means you probably need to use momodset during boot, here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by garyhibdon on 2011-12-17
this is what it gave me respectively for those lines

```
gary@gary-System-Product-Name:~$ lsmod
Module                  Size  Used by
snd_seq_dummy          12686  0 
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
binfmt_misc            17292  1 
nvidia              10390874  44 
joydev                 17393  0 
ppdev                  12849  0 
hid_logitech           17405  0 
ff_memless             12945  1 hid_logitech
snd_usb_audio         100880  1 
usbhid                 41905  1 hid_logitech
snd_usbmidi_lib        24558  1 snd_usb_audio
hid                    77367  2 hid_logitech,usbhid
snd_hda_codec_via      61329  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80435  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
psmouse                63474  0 
serio_raw              12990  0 
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
asus_atk0110           17742  0 
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
atl1e                  32809  0 
```

```
gary@gary-System-Product-Name:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GTX] (rev a1)
```

```
gary@gary-System-Product-Name:~$ sudo lshw
[sudo] password for gary: 
gary-system-product-name  
    description: Desktop Computer
    product: System Product Name (To Be Filled By O.E.M.)
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=40B54B21-BCB5-DE11-9685-90E6BA6F6ECD
  *-core
       description: Motherboard
       product: P5KPL-AM EPU
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: x.0x
       serial: 102052000000535
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0501
          date: 08/20/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 246MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
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
             capabilities: internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM A1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM B1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1200MHz
          capacity: 1200MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fc000000-feafffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G70 [GeForce 7800 GTX]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff memory:fc000000-fcffffff ioport:dc00(size=128) memory:feae0000-feafffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:fbffc000-fbffffff
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f4200000-f43fffff ioport:f4400000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:e000(size=4096) memory:feb00000-febfffff ioport:f4000000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: b0
                serial: 90:e6:ba:6f:6e:cd
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c480(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c800(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:c880(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:cc00(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fbffbc00-fbffbfff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             logical name: scsi3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:23 ioport:c400(size=8) ioport:c080(size=4) ioport:c000(size=8) ioport:bc00(size=4) ioport:b880(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAWF1659499
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000488fc
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 565e94ae-bdd6-442e-9910-faa1be4aade0
                   size: 294GiB
                   capacity: 294GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                   configuration: created=2011-12-11 22:49:03 filesystem=ext4 lastmountpoint=/ modified=2011-12-11 23:03:30 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-16 22:18:57 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 4095MiB
                   capacity: 4095MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4095MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVD Writer 1270d
                vendor: HP
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GH22
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
gary@gary-System-Product-Name:~$ 

```

---

### Post by wildmanne39 on 2011-12-17
Hi, everything looks good in the information you posted. 

Here is a link for people that have had the same problem look at the last poster.
[http://ubuntuforums.org/archive/index.php/t-849043.html](http://ubuntuforums.org/archive/index.php/t-849043.html)

Here is another link.
[http://ubuntuforums.org/archive/index.php/t-953649.html](http://ubuntuforums.org/archive/index.php/t-953649.html)

This link looks like the most promising.
[http://www.garyshood.com/diablo-frequency/](http://www.garyshood.com/diablo-frequency/)

[https://www.google.com/search?client=ubuntu&channel=fs&q=frequency+out+of+range+in+ubuntu+when+playing+gmes+in+full+screen+mode&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=frequency+out+of+range+in+ubuntu+when+playing+gmes+in+full+screen+mode&ie=utf-8&oe=utf-8)

That is all I can do to help in this matter since I have never played any games in ubuntu and am out of my field depth here.
Thank you

---

### Post by garyhibdon on 2011-12-17
> **wildmanne39 said:**
> Hi, everything looks good in the information you posted. 

Here is a link for people that have had the same problem look at the last poster.
[http://ubuntuforums.org/archive/index.php/t-849043.html](http://ubuntuforums.org/archive/index.php/t-849043.html)

Here is another link.
[http://ubuntuforums.org/archive/index.php/t-953649.html](http://ubuntuforums.org/archive/index.php/t-953649.html)

This link looks like the most promising.
[http://www.garyshood.com/diablo-frequency/](http://www.garyshood.com/diablo-frequency/)

[https://www.google.com/search?client=ubuntu&channel=fs&q=frequency+out+of+range+in+ubuntu+when+playing+gmes+in+full+screen+mode&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=frequency+out+of+range+in+ubuntu+when+playing+gmes+in+full+screen+mode&ie=utf-8&oe=utf-8)

That is all I can do to help in this matter since I have never played any games in ubuntu and am out of my field depth here.
Thank you
i appreciate your fast replies and all your help. will update if this takes care of it.

---

### Post by garyhibdon on 2011-12-17
ive tried EVERY way i can think of to do these, and the only conclusive one i found was 
[http://www.garyshood.com/diablo-frequency/](http://www.garyshood.com/diablo-frequency/)

the others did nothing.
the last thing i could not figure out was how to change the target so that that program would force the game to open using it.

any ideas on that. ive googled it every way i can think of and didnt find anything.

---

### Post by wildmanne39 on 2011-12-18
Hi, no I have no idea, hopefully someone with experience with this exact issue will reply.

---

### Post by garyhibdon on 2011-12-18
i really hope so and again, i really do appreciate all your help so far.

---

### Post by garyhibdon on 2011-12-19
ive done everything i can think of, and the modications ive made have gotten the white lines to go away, but i still cannot get fullscreen mode. anyone have any other ideas?

and yes ive been using google :lolflag:


im still getting the error:

d-sub   frequency out of range 81.x / 65

where x is either a 3 or 1

---

### Post by Ripose on 2011-12-19
Would it help any if told you the numbers are horizontal and vertical frequency.

Also the latest Nvidia driver for your card is version 290, 32 or 64 bit.

---

### Post by garyhibdon on 2011-12-19
the other part i guess i should point out seen as how noone else has noticed, 

i have an nvidia geforce 8800 gts.

trust me, thats what it is, so its rather confusing that its showing a 7800 gtx

---

### Post by wildmanne39 on 2011-12-19
Hi, that was the first thing I noticed when I saw the information you posted but it did not make any difference in my opinion so I did not mention it.
Thanks

---

### Post by garyhibdon on 2011-12-19
ok i wasnt sure if it mattered either way.

anyone have any other ideas? still cant find anything out.
i found a post with a kind of similiar problem, he reported that compizconfig fixed his probelm, so naturally i tried it.

it made it worse.

---

### Post by garyhibdon on 2011-12-19
as an update,

[http://ubuntuforums.org/showthread.php?t=1892526&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=1892526&highlight=nvidia)

thats the thread i was referring to, and just like the man with the initial problem in there,
i get this error message
```
xrandr: Failed to get size of gamma for output default
```and when i tried this
```
gedit ~/.config/monitors.xml
```it let me open that file where i was able to modify the refresh rate, but it doesnt seem to keep the values.
Heres what that file says:
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="default">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>81</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA1">
          <vendor>GSM</vendor>
          <product>0x57a0</product>
          <serial>0x0001c762</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>81</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
  </configuration>
</monitors>
```please help!! im so lost now.

on a side note, im really starting to miss 10.10. never had these problems

---

### Post by garyhibdon on 2011-12-20
ok so i found another page that recomended trying this code

```
First add the following PPA:
- Open a terminal
- Type in: **sudo add-apt-repository ppa:ubuntu-x-swat/x-updates**
- press enter and type your password
 
- Then type the following: **sudo apt-get remove nvidia-current**
- Then type the following: **sudo apt-get purge nvidia-***
 
- Then type the following: **sudo apt-get update**
- Then type: **sudo apt-get upgrade**
```that killed any visuals that i DID have and made it so that ubuntu cannot even detect monitor now. but i got it straightened out.

the only size setting thats working is the built in 1024X768, thusly making it very difficult to see. i believe it cut some of the screen off, but im not entirely sure

also just to clarify, im using a lg flatron w2240 monitor.

ubuntu is not recognizing the monitor, but the nvidia drivers are.
found out about nouveau and how to disable it and tried.

```
gary@gary-System-Product-Name:~$ sudo echo nouveau >> /etc/modprobe.d/blacklist.conf
```and got this:
```
gary@gary-System-Product-Name:~$ sudo echo nouveau >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
```

---

### Post by garyhibdon on 2011-12-20
no new ideas . . . ?

---

### Post by garyhibdon on 2011-12-20
> **garyhibdon said:**
> no new ideas . . . ?

. . .

---

### Post by garyhibdon on 2011-12-21
> **garyhibdon said:**
> . . .
more . . .  no progress made so far

---

### Post by garyhibdon on 2011-12-21
ok so im going to uninstall 11.10 because its not suiting my needs at all and has given me ALOT of problems. i suppose ill switch back to 10.04 or 10.10 if i can find a dl sight, so nvm on this.

thanks for all the help i did get though.

p.s. im taking the nvidia out for now

---

### Post by garyhibdon on 2011-12-26
ok so its been a week ish and heres what i have so far.

i dropped back down to 10.10 (i prefered the way that the gui acted over 11.10)
blacklisted nouveau, installed the proprietary drivers,and redid the settings.

the problem ive run into is that it still cannot find the edid from the monitor. 
any ideas on what may fix this?

---

### Post by wildmanne39 on 2011-12-26
Hi, here is a link for setting edid but I have never tired it myself.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
Scroll down the page until you see > Adding undetected resolutions
That has the directions. 

This gets technical so read carefully and I have found that on my system I could not make it recognize my card using this method in 11.04 but in 11.10 it did it automatically. Sorry I can not be of more help.
Thanks

---

### Post by garyhibdon on 2011-12-27
wildmanne, you sir are heaven sent. you have MOST helpful through all this, but heres the thing.

i fixed it. i had a dvi to vga adapter on the gfx card and used the regular vga plug to plug into my monitor. i plugged a straight dvi-d cable to the mopnitor and gfx card, and it worked great.

im so sorry for not thinking of this as an answer sooner, i am so embarassed by such a basic mistake.

and thank you so much for all of your help:lolflag:

---

### Post by wildmanne39 on 2011-12-27
Hi, I am glad to hear you got it working! 
Enjoy

---


---
title: "Help with Nvidia CK804 Ethernet controler"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by TLD98541 on 2013-07-13
Hi, I'm new to Linux and am having a problem with one of the network controllers in the machine that i installed Ubuntu 12.04LTS on. It's a duel boot machine with Windows Vista on a separate partition.

The mother board is a ASUS A8N-SLI Premium and has 2 onboard Ethernet controllers eth0 is a Marvel 88E81001 and is attached to the internet, it works fine.
The second controller eth1 is identified as Nvidia CK804, it is attached to my LAN and i need to get it working so i can set up Internet connection sharing.

The controller will connect for a few minutes then it disconnects for a few minutes, this happens over and over. 
I'm wondering if this is a driver issue? I've found this driver [http://manpages.ubuntu.com/manpages/lucid/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/nfe.4freebsd.html) with some instructions but i'm not sure how to go about installing a driver on Ubuntu, if it is a driver issue.

The driver file is a .gz file. Is that like a zip file? 
If it is then how do i go about extracting it, and where do i extract it to in the file system before using the commands in the instructions?

Any help would be appreciated.

---

### Post by farrinux on 2013-07-14
I assume when you say eth0 is attached to the internet that you mean it is attached to the WAN port on your router or modem. How is eth1 attached to your LAN?  By the LAN port on the back of the same router or modem or to a switch?

---

### Post by TLD98541 on 2013-07-14
eth0 is attached to a modem. and i can get on the internet so it is working fine.
eth1 is attached to a switch that attaches to 2 other computers, that is why i need to get ICS going so the other computers can access the internet.

---

### Post by TLD98541 on 2013-07-14
I found this thread [http://ubuntuforums.org/showthread.php?t=1781299&highlight=Nvidia+CK804](http://ubuntuforums.org/showthread.php?t=1781299&highlight=Nvidia+CK804) the motherboard they are talking about is similar to mine so i followed the link in the thread to [http://ubuntuforums.org/showthread.php?t=211823](http://ubuntuforums.org/showthread.php?t=211823) i followed th instructions and found the [COLOR=#000000]forcedeth driver was not loaded
 
So i followed the instructions and loaded the driver. but it didn't help as the pop up on the desktop still kept coming back saying that the [/COLOR][COLOR=#000000]controller was disconnected and then it would connect again and then disconnect again.
 
When i click on the network indicator on the taskbar it shows the [/COLOR][COLOR=#000000]Marvel 88E81001[/COLOR][COLOR=#000000]Ethernet controller eth0 [/COLOR][COLOR=#000000]connected continually but the [/COLOR][COLOR=#000000]Nvidia CK804 [/COLOR][COLOR=#000000]Ethernet controller eth1 connects [/COLOR][COLOR=#000000]for a couple [/COLOR][COLOR=#000000]minutes[/COLOR][COLOR=#000000] then disconnected for a few minutes.
 
FYI: This setup is working when booted to windows. [/COLOR]

---

### Post by farrinux on 2013-07-15
Did you configure the eth1 port for ICS in the network manager?

---

### Post by TLD98541 on 2013-07-15
Yes i guess so, I followed this guide here - [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) the section - Ubuntu Internet Gateway Method (iptables) and Advanced Gateway Configuration,

I don't think i did anything in a window it was all in a terminal and editing some config files. Ir was the only setup i saw that was for i wired Ethernet connection.

---

### Post by farrinux on 2013-07-15
OK right click on the panel network indicator and select " edit connections" from the drop down menu.  This should bring up the network manager and show all current in use ports wired and wireless. If your cables are plugged in, 
eth0 and eth1 should be there. Click on eth1 to select it and them click on edit on the right. This should bring up the properties for eth1.  Now click on the IPV4 heading and it should say "Shared with other computers" or somethond similar. If not you have not got ICS configured right.

---

### Post by varunendra on 2013-07-15
> **TLD98541 said:**
> The controller will connect for a few minutes then it disconnects for a few minutes, this happens over and over.

If it works even for a few seconds, it means there is a driver already loaded for it. Please post back the outputs of -
```
lshw -C network
nm-tool
lsmod
```

Please remember to wrap the outputs in 'Code' tags while posting, to put them in a box like above one. Follow the "Code Tags example" link in my signature to see an elaborated example.

---

### Post by TLD98541 on 2013-07-15
```
tld@US1:~$ sudo lshw -C network[sudo] password for tld: 
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth0
       version: 13
       serial: 00:13:d4:77:fc:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full firmware=N/A ip=98.237.219.196 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:d7000000-d7003fff ioport:a000(size=256) memory:d8100000-d811ffff
tld@US1:~$ sudo nm-tool


NetworkManager Tool


State: connected (global)


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             disconnected
  Default:           no
  HW Address:        00:13:D4:77:ED:8C


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on




- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            skge
  State:             connected
  Default:           yes
  HW Address:        00:13:D4:77:FC:00


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         98.237.219.196
    Prefix:          21 (255.255.248.0)
    Gateway:         98.237.216.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76




tld@US1:~$ sudo lsmod
Module                  Size  Used by
rfcomm                 38063  0 
bnep                   17830  2 
vesafb                 13516  1 
bluetooth             158089  10 rfcomm,bnep
nvidia              10245054  30 
ppdev                  12849  0 
ir_lirc_codec          12739  0 
lirc_dev               18700  1 ir_lirc_codec
ir_mce_kbd_decoder     12681  0 
ir_sony_decoder        12462  0 
ir_jvc_decoder         12459  0 
ir_rc6_decoder         12459  0 
ir_rc5_decoder         12459  0 
rc_rc6_mce             12454  0 
ir_nec_decoder         12459  0 
mceusb                 17791  0 
rc_core                21263  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
snd_intel8x0           33423  3 
snd_ac97_codec        106117  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_wavefront          38833  0 
snd_cs4236             29294  0 
snd_wss_lib            30063  2 snd_wavefront,snd_cs4236
snd_opl3_lib           18863  2 snd_wavefront,snd_cs4236
snd_hwdep              13276  2 snd_wavefront,snd_opl3_lib
serio_raw              13027  0 
snd_pcm                80916  4 snd_intel8x0,snd_ac97_codec,snd_cs4236,snd_wss_lib
snd_mpu401             13847  0 
snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401
snd_seq_midi           13132  0 
k8temp                 12905  0 
snd_rawmidi            25424  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ns558                  12654  0 
gameport               15060  2 ns558
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_seq_device         14172  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  20 snd_intel8x0,snd_ac97_codec,snd_wavefront,snd_cs4236,snd_wss_lib,snd_opl3_lib,snd_hwdep,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
soundcore              14635  1 snd
snd_page_alloc         14108  3 snd_intel8x0,snd_wss_lib,snd_pcm
asus_atk0110           17742  0 
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40904  3 ppdev,parport_pc,lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
usbhid                 41937  0 
hid                    77428  1 usbhid
usb_storage            39646  0 
skge                   44767  0 
crc_itu_t              12627  1 firewire_core
sata_mv                28386  0 
floppy                 60184  0 
pata_amd               13750  0 
forcedeth              58021  0 
sata_nv                23360  3 
tld@US1:~$ 

```

---

### Post by TLD98541 on 2013-07-15
Well i see the forcedeth driver is loading now when i started this thread it wasn't loading see post #4.

---

### Post by varunendra on 2013-07-15
> **TLD98541 said:**
> Well i see the forcedeth driver is loading now when i started this thread it wasn't loading see post #4.

In your previous post, the output for lshw doesn't seem complete. Or maybe you need to run lshw with "sudo" (sudo lshw -C network).

Anyway, now that it seems to be loading, does it stay connected? If not, please post the output of lshw again (with the part pertaining to the Nvidia card), as well as -
```
dmesg | egrep -i 'forcedeth|eth1'
ifconfig -a
cat /etc/network/interfaces
```

Also, does the LAN part work if you disconnect the cable from the other port (the WAN port)? Try rebooting without that cable connected and see if it makes a difference.

---

### Post by TLD98541 on 2013-07-15
```
 tld@US1:~$ sudo lshw -C network[sudo] password for tld: 
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth0
       version: 13
       serial: 00:13:d4:77:fc:00
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full firmware=N/A ip=98.237.219.196 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:d7000000-d7003fff ioport:a000(size=256) memory:d8100000-d811ffff
tld@US1:~$ sudo dmesg | egrep -i 'forcedeth|eht1'
[    0.780387] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.780574] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.780579] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.302777] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:13:d4:77:ed:8c
[    1.302781] forcedeth 0000:00:0a.0: highdma csum gbit lnktim desc-v3
tld@US1:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:d4:77:fc:00  
          inet addr:98.237.219.196  Bcast:98.237.223.255  Mask:255.255.248.0
          inet6 addr: fe80::213:d4ff:fe77:fc00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1214134 (1.2 MB)  TX bytes:36195 (36.1 KB)
          Interrupt:17 


eth1      Link encap:Ethernet  HWaddr 00:13:d4:77:ed:8c  
          inet6 addr: fe80::213:d4ff:fe77:ed8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117879 (117.8 KB)  TX bytes:84116 (84.1 KB)
          Interrupt:23 Base address:0xa000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5786 (5.7 KB)  TX bytes:5786 (5.7 KB)


tld@US1:~$ sudo cat /etc/network/interface
cat: /etc/network/interface: No such file or directory
tld@US1:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


tld@US1:~$ 

```

---

### Post by varunendra on 2013-07-15
Still nothing for eth1 in lshw output?? That's strange! Does it even show up under any category if you just use
```
sudo lshw
``` command?

There are no clues in above outputs, and the Nvidia card is missing from the lshw output, I'd assume it to be a BIOS or hardware problem. Please check your BIOS to see if there are any settings to disable it when one interface is up. And did you try rebooting without the cable plugged in the other port like I asked in my previous post?

---

### Post by TLD98541 on 2013-07-15
Yes it can be disabled i BIOS, Keep in mind that this exact setup works when i boot to windows vista so all the cables and hardware are working.

I tried rebooting with eth0 unplugged and there was no difference. 

I will run ```
 [COLOR=#000000][FONT=Ubuntu Mono]sudo lshw 
``` and post back the results.[/FONT][/COLOR]

---

### Post by TLD98541 on 2013-07-15
```
 tld@US1:~$ sudo lshw[sudo] password for tld: 
us1                       
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=6018F6FA-5E1D-D711-9018-0013D477ED8C
  *-core
       description: Motherboard
       product: A8N-SLI Premium
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: 1.02
       serial: 123456789000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: ASUS A8N-SLI Premium ACPI BIOS Revision 1009
          date: 10/21/2005
          size: 128KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.3.2
          slot: Socket 939
          size: 2200MHz
          capacity: 3700MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy
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
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory:0
          description: System Memory
          physical id: 43
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             size: 1GiB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM 400 MHz (2.5 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 512MiB
             width: 64 bits
             clock: 400MHz (2.5ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.3.2
          size: 2200MHz
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory:1 UNCLAIMED
          description: Memory controller
          product: CK804 Memory Controller
          vendor: NVIDIA Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a3
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: CK804 ISA Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: CK804 SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
          resources: irq:255 ioport:e400(size=32) ioport:4c00(size=64) ioport:4c40(size=64)
     *-usb:0
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:d8004000-d8004fff
     *-usb:1
          description: USB controller
          product: CK804 USB Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:d8005000-d80050ff
     *-multimedia
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: NVIDIA Corporation
          physical id: f
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=snd_intel8x0 latency=0 maxlatency=5 mingnt=2
          resources: irq:22 ioport:dc00(size=256) ioport:e000(size=256) memory:d8003000-d8003fff
     *-ide:0
          description: IDE interface
          product: CK804 IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: f2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
     *-ide:1
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:21 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d800(size=16) memory:d8002000-d8002fff
     *-ide:2
          description: IDE interface
          product: CK804 Serial ATA Controller
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi5
          logical name: scsi7
          version: f3
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:20 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:c400(size=16) memory:d8001000-d8001fff
        *-disk:0
             description: ATA Disk
             product: ST3500320AS
             vendor: Seagate
             physical id: 0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdf
             version: SD15
             serial: 5QM1QXC4
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=e1143743
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@5:0.0.0,1
                logical name: /dev/sdf1
                version: 3.1
                serial: 2c1d4698-8490-c34b-b4af-88c67957ca83
                size: 79GiB
                capacity: 79GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-05-08 03:09:11 filesystem=ntfs label=WinVista state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@5:0.0.0,2
                logical name: /dev/sdf2
                version: 3.1
                serial: aa8f-f85b
                size: 305GiB
                capacity: 305GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2013-07-09 11:10:13 filesystem=ntfs label=NAS state=clean
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@5:0.0.0,3
                logical name: /dev/sdf3
                size: 79GiB
                capacity: 79GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sdf5
                   logical name: /
                   capacity: 33GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sdf6
                   capacity: 2929MiB
                   capabilities: nofs
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sdf7
                   logical name: /home
                   capacity: 43GiB
                   configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered state=mounted
        *-disk:1
             description: ATA Disk
             product: WDC WD2002FAEX-0
             vendor: Western Digital
             physical id: 1
             bus info: scsi@7:0.0.0
             logical name: /dev/sdg
             version: 05.0
             serial: WD-WMAY01654284
             size: 1863GiB (2TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=46697619
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdg1
                version: 3.1
                serial: 22793d75-75e4-8442-ae9f-9e6fdd913635
                size: 1863GiB
                capacity: 1863GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2012-09-29 22:30:16 filesystem=ntfs label=2TCav state=clean
     *-pci:0
          description: PCI bridge
          product: CK804 PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master
          resources: ioport:a000(size=4096) memory:d6000000-d7ffffff memory:d8100000-d81fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
             vendor: Texas Instruments
             physical id: b
             bus info: pci@0000:05:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
             resources: irq:16 memory:d7008000-d70087ff memory:d7004000-d7007fff
        *-network
             description: Ethernet interface
             product: 88E8001 Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: c
             bus info: pci@0000:05:0c.0
             logical name: eth0
             version: 13
             serial: 00:13:d4:77:fc:00
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.14 duplex=full firmware=N/A ip=98.237.219.196 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:17 memory:d7000000-d7003fff ioport:a000(size=256) memory:d8100000-d811ffff
     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth1
          version: a3
          serial: 00:13:d4:77:ed:8c
          size: 1000000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1Gbit/s
          resources: irq:23 memory:d8000000-d8000fff ioport:b000(size=8)
     *-pci:1
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:9000(size=4096) memory:d4000000-d5ffffff ioport:d8200000(size=1048576)
        *-scsi
             description: SCSI storage controller
             product: RocketRAID 2310 4 Port SATA-II Controller
             vendor: HighPoint Technologies, Inc.
             physical id: 0
             bus info: pci@0000:04:00.0
             logical name: scsi0
             logical name: scsi2
             logical name: scsi4
             logical name: scsi6
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: scsi pm msi pciexpress bus_master cap_list rom emulated
             configuration: driver=sata_mv latency=0
             resources: irq:17 memory:d5000000-d50fffff ioport:9000(size=256) memory:d8200000-d827ffff
           *-disk:0
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WCATR7223053
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=47dce5c3
              *-volume
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 1862GiB
                   capabilities: primary
           *-disk:1
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 05.0
                serial: WD-WCATR7237105
                size: 931GiB (1TB)
                configuration: ansiversion=5
           *-disk:2
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 2
                bus info: scsi@4:0.0.0
                logical name: /dev/sdd
                version: 05.0
                serial: WD-WCATR7259587
                size: 931GiB (1TB)
                configuration: ansiversion=5
           *-disk:3
                description: ATA Disk
                product: WDC WD1002FAEX-0
                vendor: Western Digital
                physical id: 3
                bus info: scsi@6:0.0.0
                logical name: /dev/sde
                version: 05.0
                serial: WD-WCATR7168257
                size: 931GiB (1TB)
                configuration: ansiversion=5
     *-pci:2
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41
     *-pci:3
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:42
     *-pci:4
          description: PCI bridge
          product: CK804 PCIE Bridge
          vendor: NVIDIA Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a3
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:43 ioport:8000(size=4096) memory:d0000000-d3ffffff ioport:c0000000(size=268435456)
        *-display
             description: VGA compatible controller
             product: G84 [GeForce 8600 GT]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:01:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nvidia latency=0
             resources: irq:18 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:8000(size=128) memory:d3000000-d301ffff
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 10
          bus info: usb@1:3
          logical name: scsi10
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@10:0.0.0
             logical name: /dev/sdc
             size: 3824MiB (4009MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=fdf8b019
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@10:0.0.0,1
                logical name: /dev/sdc1
                version: FAT32
                serial: 802e-e198
                size: 3820MiB
                capacity: 3820MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat
tld@US1:~$ 

```

---

### Post by varunendra on 2013-07-15
> **TLD98541 said:**
> ```

     *-bridge
          description: Ethernet interface
          product: CK804 Ethernet Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth1
          version: a3
          serial: 00:13:d4:77:ed:8c
          **[COLOR="#FF0000"]size: 1000000000[/COLOR]**
          **[COLOR="#FF0000"]capacity: 1000000000[/COLOR]**
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes **[COLOR="#006400"]driver=forcedeth[/COLOR]** driverversion=0.64 duplex=full latency=0 **[COLOR="#006400"]link=yes[/COLOR]** maxlatency=20 mingnt=1 multicast=yes port=MII **[COLOR="#FF0000"]speed=1Gbit/s[/COLOR]**
          resources: irq:23 memory:d8000000-d8000fff ioport:b000(size=8)

```

Okay, so it is bridged to the other interface. Have you read [this part]("https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI_Method_via_Network_Manager_.28Ubuntu_11.10.29") in the guide page that you followed ? -
> Follow the GUI Method via Network Manager (Ubuntu 9.10 and up) below but there is a bug which turn off and on the share connection. The workaround for now is to set IPv6 options to Ignore and then sudo killall dnsmasq. Reconnect and it should work.

ONLY If yes, and it didn't help, we can try forcing the lowest speed and see if it can get connected -
```
sudo mii-tool -F 10baseT-FD eth1
```
If it gets you connected, you can try 100MB/s full duplex by replacing "10baseT-FD" with "100baseTx-FD".

But the behaviour you described sounds exactly like the bug, so you shouldn't need the above trick of forcing a speed after trying the workaround.

---

### Post by TLD98541 on 2013-07-15
Well i didn't use "GUI Method via Network Manager (Ubuntu 9.10 and up)" i used "Ubuntu Internet Gateway Method (iptables)"
but apparently the bug applies to that too.

I ended up removing dnsmasq and setting IPv6 options to Ignore and it's working now.
Since I had to remove dnsmasq but not dnsmasq-base do you know if i will still be able to set a IP range?

varunendra you have been extremely helpful and patient i can't thank you enough.

---

### Post by varunendra on 2013-07-15
It's a pleasure to be able to help, glad you got it sorted. :)
> **TLD98541 said:**
> Since I had to remove dnsmasq but not dnsmasq-base do you know if i will still be able to set a IP range?

I'm not sure I understand above question correctly, but if you mean the IP range assigned assigned to the clients, it's the job of DHCP server. Removing or leaving dnsmasq (which only deals with DNS server addresses) shouldn't have any effect on DHCP functionality. If you mean some other kind of IP range, please explain it.

---

### Post by TLD98541 on 2013-07-15
When doing ICS with windows the computer with the shared internet connection is always 192.168.0.1 then a client attaches it is given a IP between 192.168.0.2 to 192.168.0.250 i'd like to set the Linux internet connection server to the same range.

---

### Post by varunendra on 2013-07-16
Just re-read the wiki page and realized what you meant. I didn't know dnsmasq can also be configured to act as a dhcp server. You may use the "Other approaches" methods on the same page to configure dedicated dhcp server (or other suggested ways) on the system though : [https://help.ubuntu.com/community/Internet/ConnectionSharing#Other_approaches](https://help.ubuntu.com/community/Internet/ConnectionSharing#Other_approaches)

---


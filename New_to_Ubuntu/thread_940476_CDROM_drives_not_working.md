---
title: "CDROM drives not working"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by camoguy on 2008-10-07
This is what I did, installed 8.04.1, compiled a custom kernel.
Installed the Creative XFi and Nvidia drivers.
Now /dev/ is missing my cdroms.
This is where I'm getting a bit confused.
My CD/DVD drives are both IDE but lshw says this:

```

 *-ide:0
             description: IDE interface
             product: MCP55 IDE
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: scsi0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
           *-cdrom:0 UNCLAIMED
                description: SCSI CD-ROM
                product: DVD-ROM SD-616E
                vendor: SAMSUNG
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                version: F503
                capabilities: removable
                configuration: ansiversion=5
           *-cdrom:1 UNCLAIMED
                description: SCSI CD-ROM
                product: DRW-0804P
                vendor: ASUS
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                version: 1.21
                capabilities: removable
                configuration: ansiversion=5

```

lsmod says:
```

alex@pacnow:~$ lsmod
Module                  Size  Used by
ipv6                  311080  16 
parport_pc             41384  0 
ppdev                  11656  0 
parport                44684  2 parport_pc,ppdev
ctalsa                580268  1 
haxfi                5437304  0 
cthwiut               411176  0 
ctexfifx             2737456  0 
ct20xut               958760  0 
ctsfman               290508  0 
emupia                382436  0 
snd_pcm_oss            47904  0 
snd_mixer_oss          20480  1 snd_pcm_oss
snd_pcm                93704  2 ctalsa,snd_pcm_oss
snd_page_alloc         12944  1 snd_pcm
snd_seq_dummy           5892  0 
snd_seq_oss            37504  0 
snd_seq_midi_event     10368  1 snd_seq_oss
snd_seq                62592  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_timer              27656  2 snd_pcm,snd_seq
snd_seq_device         10644  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd                    69096  10 ctalsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              10656  4 ctalsa,ctsfman,emupia,snd
ctossrv               162688  7 ctalsa,haxfi,cthwiut,ctexfifx,ct20xut,ctsfman,emupia
cpufreq_ondemand       11408  0 
cpufreq_conservative    10888  0 
cpufreq_powersave       3456  0 
cpufreq_userspace       6564  0 
cpufreq_stats           8672  0 
freq_table              6720  2 cpufreq_ondemand,cpufreq_stats
container               6912  0 
video                  23700  0 
output                  6016  1 video
sbs                    18064  0 
sbshc                   9216  1 sbs
dock                   13216  0 
battery                17032  0 
iptable_filter          4864  0 
ip_tables              24360  1 iptable_filter
x_tables               23944  1 ip_tables
ac                      8584  0 
coretemp               10240  0 
f71882fg               14600  0 
sbp2                   27528  0 
evdev                  15360  5 
nvidia               8115600  34 
psmouse                46620  0 
i2c_nforce2             8960  0 
serio_raw               9348  0 
button                 11168  0 
pcspkr                  5248  0 
i2c_core               28800  2 nvidia,i2c_nforce2
ext3                  140432  8 
jbd                    57256  1 ext3
mbcache                11648  1 ext3
sg                     38424  0 
sd_mod                 30208  13 
amd74xx                11928  0 [permanent]
ide_core              136856  1 amd74xx
usbhid                 35552  0 
hid                    43968  1 usbhid
pata_amd               17028  0 
sata_sil24             20740  0 
sata_nv                32008  10 
libata                176688  3 pata_amd,sata_sil24,sata_nv
floppy                 69352  0 
scsi_mod              131896  4 sbp2,sg,sd_mod,libata
ohci1394               36788  0 
ehci_hcd               42124  0 
ohci_hcd               27780  0 
forcedeth              55692  0 
ieee1394              105808  2 sbp2,ohci1394
usbcore               169520  4 usbhid,ehci_hcd,ohci_hcd
thermal                20000  0 
processor              41832  1 thermal
fan                     7048  0 
fuse                   56368  5 

```

lspci:
```

alex@pacnow:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:05.0 Multimedia audio controller: Creative Labs SB X-Fi
04:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
0a:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)
alex@pacnow:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:14.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:05.0 Multimedia audio controller: Creative Labs SB X-Fi
04:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
0a:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTX] (rev a2)

```

I'm using the MSI P6N Diamond motherboard, 8800 Gtx video, and XFi PCI sound card, everything but the drives work. When I boot up from the live cd it works and the lshw looks different. I'm wondering if there's some kind of kernel setting I forgot to check or if it was something that got broken by installing the sound/video drivers.

I be very appreciative for some advice how to get things rolling again. Strange is that they disappeared from the /dev/ directory.

---


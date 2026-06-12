---
title: "wireless problem in Ubuntu 12.04 after some updates"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by yacob_1 on 2012-06-20
Dear All

I have had the new ubuntu 12.04 installed for a month now and my wireless internet (wifi) has been working flawlessly. But suddenly my wireless internet does not work at all, I suspect the problems starts soon after updating some of the packages from ubuntu. I have tried some of the recommendations that I'm able to get from googling. If it helps, I have printed out some of the networking related commands under linux:

 

ifconfig -a

eth0      Link encap:Ethernet  HWaddr d0:67:e5:48:46:31
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
................................................................

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions
.................................................................

sudo lshw -C network

  *-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e3c00000-e3c03fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 10
       serial: d0:67:e5:48:46:31
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=5761-v3.78 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:e2010000-e201ffff memory:e2000000-e200ffff
.................................................................

lsmod

Module                  Size  Used by
usbhid                 47199  0
hid                    99559  1 usbhid
iptable_filter         12810  0
ip_tables              27473  1 iptable_filter
x_tables               29846  2 iptable_filter,ip_tables
snd_hda_codec_hdmi     32474  1
snd_hda_codec_idt      70795  1
rfcomm                 47604  12
bnep                   18281  2
joydev                 17693  0
snd_hda_intel          33773  3
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
dell_wmi               12681  0
ppdev                  17113  0
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
sparse_keymap          13890  1 dell_wmi
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
parport_pc             32866  0
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            18119  0
dcdbas                 14490  1 dell_laptop
wmi                    19256  1 dell_wmi
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18288  2
uvcvideo               72627  0
videodev               98259  1 uvcvideo
mac_hid                13253  0
soundcore              15091  1 snd
psmouse                87692  0
v4l2_compat_ioctl32    17128  1 videodev
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
bluetooth             180104  23 rfcomm,bnep,btusb
i915                  468745  3
serio_raw              13211  0
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
mei                    41616  0
video                  19596  1 i915
lp                     17799  0
parport                46562  3 ppdev,parport_pc,lp
tg3                   152032  0
firewire_ohci          41000  0
firewire_core          63558  1 firewire_ohci
sdhci_pci              18826  0
crc_itu_t              12707  1 firewire_core
sdhci                  33205  1 sdhci_pci
.............................................................

lspci -k

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
        Subsystem: Dell Device 049b
        Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
        Subsystem: Dell Device 049b
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: Dell Device 049b
        Kernel driver in use: mei
        Kernel modules: mei
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
        Subsystem: Dell Device 049b
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: Dell Device 049b
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
        Subsystem: Dell Device 049b
        Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
        Subsystem: Dell Device 049b
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
        Subsystem: Dell Device 049b
        Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
        Subsystem: Dell Device 049b
        Kernel modules: i2c-i801
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
        Subsystem: Dell Wireless 1530 Half-size Mini PCIe Card
09:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
        Subsystem: Dell Device 049b
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci
09:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
        Subsystem: Dell Device 049b
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci
09:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)
        Subsystem: Dell Device 049b
0a:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)
        Subsystem: Dell Device 049b
        Kernel driver in use: tg3
        Kernel modules: tg3
..........................................................
nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        D0:67:E5:48:46:31

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
................................................................
uname -a
Linux luxadd 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
............................................................

Kind regards
yacob

---

### Post by yacob_1 on 2012-06-20
Dear ALL,

I want to stress the fact that my Dell laptop is a dual boot and apparently the wireless in the Windows OS works like a charm. Hope to get some clue how to solve the issue with the problems in Ubuntu 12.04LTS. It is very frustrating.

---

### Post by yacob_1 on 2012-06-24
Hi All

Is there any one out there able to give comments to my problems or  am I in wrong forum?

---

### Post by steeldriver on 2012-06-24
there are certainly some wireless superheroes on here who can help you, unfortunately I don't know what bat signal you need to have them stop by

the Broadcom driver situation is complicated so I won't even try to suggest a fix - you should probably do a more detailed 

lspci -nn

to get the actual pci vendor / subsystem id and search with that else you will waste your time trying a lot of things that are inappropriate for your particular device - it may be as simple as going to Additional Drivers and selecting the appropriate package e.g.

[http://ubuntuforums.org/showthread.php?t=1967805&highlight=broadcom-sta](http://ubuntuforums.org/showthread.php?t=1967805&highlight=broadcom-sta)

---

### Post by wildmanne39 on 2012-06-24
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---


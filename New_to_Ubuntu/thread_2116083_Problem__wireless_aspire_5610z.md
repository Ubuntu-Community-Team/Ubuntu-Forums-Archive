---
title: "Problem  wireless aspire 5610z"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by SalamFromMaroc on 2013-02-14
i have acer aspire 5610z and i can connect to my wireless
pls if someone can give me help. i have ubuntu 12.10

i did check on system config, and it s show wireless hardware,but unfortunately i can t connect to my wifi

---

### Post by westie457 on 2013-02-14
Welcome to the Forum.

Please open a terminal (Ctrl=Alt=T)and post the output of
Code:
lspci -vnn
Select all the output then copy & paste into a new reply, then highlight what you pasted in and click on the # symbol at the top of the message area. This will place [code] brackets around it and make things easier to read.

Thank you

---

### Post by SalamFromMaroc on 2013-02-15
```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 5088 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0
    Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 44000000-441fffff
    Prefetchable memory behind bridge: 0000000044200000-00000000443fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 44400000-445fffff
    Prefetchable memory behind bridge: 0000000044600000-00000000447fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 3 [8086:27d4] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 44800000-449fffff
    Prefetchable memory behind bridge: 0000000044a00000-0000000044bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: d0000000-d00fffff
    Prefetchable memory behind bridge: 0000000044c00000-0000000044dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 50a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 50c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 50e0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 5400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=0a, sec-latency=32
    I/O behind bridge: 00007000-00007fff
    Memory behind bridge: d0100000-d01fffff
    Prefetchable memory behind bridge: 0000000040000000-0000000043ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, lpc_ich, intel-rng

00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 5440 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 10
    I/O ports at 5420 [size=32]
    Kernel modules: i2c-i801

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at d0000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, fast devsel, latency 64, IRQ 21
    Memory at d0100000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: b44
    Kernel modules: b44

06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: bus master, medium devsel, latency 168, IRQ 16
    Memory at 48000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
    Memory window 0: 40000000-43ffffff (prefetchable)
    Memory window 1: 4c000000-4fffffff
    I/O window 0: 00007000-000070ff
    I/O window 1: 00007400-000074ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

06:04.1 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0530] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 11
    Memory at d0103000 (32-bit, non-prefetchable) [disabled] [size=128]
    Capabilities: <access denied>

06:04.2 SD Host controller [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller [1524:0550] (rev 01) (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 17
    Memory at d0103400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

06:04.3 FLASH memory [0501]: ENE Technology Inc FLASH memory: ENE Technology Inc: [1524:0520] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 11
    Memory at d0103800 (32-bit, non-prefetchable) [disabled] [size=128]
    Capabilities: <access denied>

06:04.4 FLASH memory [0501]: ENE Technology Inc SD/MMC Card Reader Controller [1524:0551] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Flags: medium devsel, IRQ 17
    Memory at d0102000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci



```

---

### Post by SalamFromMaroc on 2013-02-16
plz if anyone can give me help.I need use internet in my Ubuntu,if no have solution need know how can i desinstall Ubuntu.

---

### Post by westie457 on 2013-02-17
Run ```
sudo apt-get install linux-firmware-nonfree
```

Wait a little while to see if it connects. If not run ```
sudo modprobe b43
```and try again.

If after this it is still not working post the output of ```
lsmod
```

Thank you.

---

### Post by SalamFromMaroc on 2013-02-17
karim@karim-Aspire-5610Z:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
joydev                 17161  0 
snd_hda_codec_realtek    63356  1 
acer_wmi               27586  0 
sparse_keymap          13658  1 acer_wmi
b43                   347284  0 
pcmcia                 39509  0 
mac80211              461161  1 b43
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
videodev               95841  2 uvcvideo,videobuf2_core
microcode              18209  0 
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              24411  2 snd_pcm,snd_seq
cfg80211              175375  2 b43,mac80211
psmouse                84843  0 
lpc_ich                16925  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13031  0 
bcma                   34483  1 b43
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457161  3 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
soundcore              14599  1 snd
ssb_hcd                12749  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
wmi                    18590  1 acer_wmi
i2c_algo_bit           13197  1 i915
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
mac_hid                13037  0 
video                  18847  2 acer_wmi,i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
b44                    31326  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  3 b43,ssb_hcd,b44
```

```

---

### Post by SalamFromMaroc on 2013-02-17
thank you so much for you support

until now I have wireless problem,

I am waiting for your help,

---

### Post by SalamFromMaroc on 2013-02-17
```
karim@karim-Aspire-5610Z:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
joydev                 17161  0 
snd_hda_codec_realtek    63356  1 
acer_wmi               27586  0 
sparse_keymap          13658  1 acer_wmi
b43                   347284  0 
pcmcia                 39509  0 
mac80211              461161  1 b43
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
videodev               95841  2 uvcvideo,videobuf2_core
microcode              18209  0 
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              24411  2 snd_pcm,snd_seq
cfg80211              175375  2 b43,mac80211
psmouse                84843  0 
lpc_ich                16925  0 
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13031  0 
bcma                   34483  1 b43
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457161  3 
drm_kms_helper         45271  1 i915
drm                   230463  4 i915,drm_kms_helper
soundcore              14599  1 snd
ssb_hcd                12749  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
wmi                    18590  1 acer_wmi
i2c_algo_bit           13197  1 i915
parport_pc             31968  0 
bnep                   17707  2 
ppdev                  12817  0 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
mac_hid                13037  0 
video                  18847  2 acer_wmi,i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
b44                    31326  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  3 b43,ssb_hcd,b44


```

---

### Post by westie457 on 2013-02-17
Had you already tried to install other drivers?

For example the Broadcom STA driver.

If so remove it ```
sudo apt-get remove bcmwl-kernel-source
```

Then run ```
sudo apt-get install b43-fwcutter
```

and ```
sudo apt-get install --reinstall linux-firmware-nonfree
```

and finally these three ```
sudo modprobe -r b43
sudo modprobe -r ssl
sudo modprobe b43
```

Is it working now?

If it, is a reboot should make the changes permanent.

---

### Post by SalamFromMaroc on 2013-02-17
```

```karim@karim-Aspire-5610Z:~$ sudo apt-get remove bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms fakeroot
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karim@karim-Aspire-5610Z:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
karim@karim-Aspire-5610Z:~$ sudo apt-get install --reinstall linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
karim@karim-Aspire-5610Z:~$ sudo modprobe -r b43
karim@karim-Aspire-5610Z:~$ sudo modprobe -r ssl
FATAL: Module ssl not found.
karim@karim-Aspire-5610Z:~$ sudo modprobe b43
karim@karim-Aspire-5610Z:~$

---

### Post by westie457 on 2013-02-18
Something is not right here, I have a laptop running the same wireless chip and the drivers will be the correct ones.

Can you post the output of all these commands ```
uname -r

rfkill list all

nm-tool

lshw -C network

lsmod
```

And finally can you confirm the version you are running please. 

One way to do this is open 'system monitor' go to the System tab, this will show the release number eg 12.10 and the kernel version eg 3.5.0-37 generic (or something similar)

---

### Post by SalamFromMaroc on 2013-02-18
```
karim@karim-Aspire-5610Z:~$ sudo apt-get remove bcmwl-kernel-source 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dkms fakeroot
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karim@karim-Aspire-5610Z:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
karim@karim-Aspire-5610Z:~$ sudo apt-get install --reinstall linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
karim@karim-Aspire-5610Z:~$ sudo modprobe -r b43
karim@karim-Aspire-5610Z:~$ sudo modprobe -r ssl
FATAL: Module ssl not found.
karim@karim-Aspire-5610Z:~$ sudo modprobe b43
karim@karim-Aspire-5610Z:~$
```

---

### Post by SalamFromMaroc on 2013-02-18
```
karim@karim-Aspire-5610Z:~$ uname -r
3.5.0-17-generic
karim@karim-Aspire-5610Z:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
karim@karim-Aspire-5610Z:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:16:D4:D8:46:D8

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


karim@karim-Aspire-5610Z:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 02
       serial: 00:16:d4:d8:46:d8
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:d0100000-d0101fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
karim@karim-Aspire-5610Z:~$ lsmod
Module                  Size  Used by
coretemp               13168  0 
snd_hda_codec_realtek    63356  1 
b43                   347284  0 
joydev                 17161  0 
acer_wmi               27586  0 
sparse_keymap          13658  1 acer_wmi
pcmcia                 39509  0 
mac80211              461161  1 b43
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
microcode              18209  0 
snd_seq_midi           13132  0 
cfg80211              175375  2 b43,mac80211
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
snd_rawmidi            25382  1 snd_seq_midi
videodev               95841  2 uvcvideo,videobuf2_core
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_seq_midi_event     14475  1 snd_seq_midi
lpc_ich                16925  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
psmouse                84843  0 
serio_raw              13031  0 
rfcomm                 37276  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             31968  0 
bnep                   17707  2 
bcma                   34483  1 b43
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457161  3 
drm_kms_helper         45271  1 i915
soundcore              14599  1 snd
ssb_hcd                12749  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
wmi                    18590  1 acer_wmi
mac_hid                13037  0 
video                  18847  2 acer_wmi,i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
b44                    31326  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  3 b43,ssb_hcd,b44
karim@karim-Aspire-5610Z:~$ 



```

---

### Post by SalamFromMaroc on 2013-02-18
i have Ubuntu 12.10 like told in my first poste


thank you so much for your support,

---

### Post by westie457 on 2013-02-18
Silly me, have just noticed that the needed driver cannot be found.

The necessary repositories have not been enabled.

Open 'Software Sources', go to the 'Ubuntu Software' tab and put a check mark in the first four boxes leaving the 'source code' box blank. Enter your password when prompted.

Close software sources then open a terminal and run ```
sudo apt-get update
``` to bring everything together then run ```
sudo apt-get install linux-firmware-nonfree
```

After this unplug the cable and reboot your computer.

The wireless should now be working. Check the Network icon at the top-right of the screen (it should look like a piece of pie with lines on it).

Let us know how things are.

Thank you.

---

### Post by SalamFromMaroc on 2013-02-18
```
karim@karim-Aspire-5610Z:~$ sudo apt-get update
[sudo] password for karim: 
Err http://br.archive.ubuntu.com quantal InRelease
  
Err http://br.archive.ubuntu.com quantal-updates InRelease
  
Err http://br.archive.ubuntu.com quantal-backports InRelease
  
Err http://security.ubuntu.com quantal-security InRelease
  
Err http://extras.ubuntu.com quantal InRelease
  
Err http://br.archive.ubuntu.com quantal Release.gpg
  Could not resolve 'br.archive.ubuntu.com'
Err http://br.archive.ubuntu.com quantal-updates Release.gpg
  Could not resolve 'br.archive.ubuntu.com'
Err http://security.ubuntu.com quantal-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://extras.ubuntu.com quantal Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://br.archive.ubuntu.com quantal-backports Release.gpg
  Could not resolve 'br.archive.ubuntu.com'
Reading package lists... Done           
W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal/InRelease  

W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/InRelease  

W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/InRelease  

W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Could not resolve 'br.archive.ubuntu.com'

W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal-updates/Release.gpg  Could not resolve 'br.archive.ubuntu.com'

W: Failed to fetch http://br.archive.ubuntu.com/ubuntu/dists/quantal-backports/Release.gpg  Could not resolve 'br.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
karim@karim-Aspire-5610Z:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
karim@karim-Aspire-5610Z:~$ 



```

---

### Post by SalamFromMaroc on 2013-02-18
I FORGOT MENTION THAT I HAVE WPA2-PSK  WITH AES WIRELESS SECURITY AND WHEN I TRY ADD THIS CONNECTION I CAN T ,
I CAN ACCESS TO THIS OPTION FOR ADD WIRELESS.BUT I DON T KNOW  CONFIGURATION ,
THIS IS MY FIRST TIME WITH UBUNTU
MAYBE IS BETTER FOR ME TO USE JUST WINDOWS BECAUSE IT S VERY EASY AND EVERYTHING IS CLEAR AND HAVE ALTO OF SOLUTION IN ALTO OF FORUMs.

so if you can pls help me to uninstall ubuntu dualboot from my computer,maybe in the future when ubuntu will more easy i will try use it

thank you so much for your help

---

### Post by westie457 on 2013-02-19
Before giving up and going back to Windows would you be willing to try one more thing to get the drivers installed?
Once the drivers are installed it should be very easy to connect wirelessly.

Open Software Sources > Ubuntu Software again and go to the 'Download From' box. In here select 'Main Server' or 'Server for <the country>  you are in or 'Other' followed by 'Select Best Server' and finally click 'Choose Server'.

Open a terminal and rerun the update and install commands given earlier. Reboot.

Let us know what happens.

Thank you.

---

### Post by SalamFromMaroc on 2013-02-19
How i can download update or driver and i no have Internet access in Ubuntu

when i did try choose best server show message box  NEED INTERNET TO CONNECT TO SERVER.

---

### Post by westie457 on 2013-02-19
Do you have an ethernet cable plugged in to the router?

---

### Post by wildmanne39 on 2013-02-19
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

That will let westie457 see everything that is going on if you do not have an ethernet connection there are directions here for running the script without internet access.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

If it is a firmware issue we you can get it without an ehternet connection if needed.
Thanks

---

### Post by aspireone722 on 2013-02-19
try different distros on live cd sometimes the you get one that just works. as long as you back up your stuff no harm to try .

---

### Post by SalamFromMaroc on 2013-02-19
```

*************** info trace ****************



**** uname -a ****


Linux karim-Aspire-5610Z 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel driver in use: b43-pci-bridge
--
06:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0090]
    Kernel driver in use: b44


**** lsusb ****


Bus 001 Device 002: ID 5986:0100 Acer, Inc Orbicam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**** iwconfig ****




**** rfkill ****


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
snd_hda_codec_realtek    63356  1 
coretemp               13168  0 
joydev                 17161  0 
b43                   347284  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
acer_wmi               27586  0 
sparse_keymap          13658  1 acer_wmi
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
pcmcia                 39509  0 
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              461161  1 b43
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
microcode              18209  0 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              175375  2 b43,mac80211
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
psmouse                84843  0 
snd                    61991  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457161  3 
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
serio_raw              13031  0 
bcma                   34483  1 b43
yenta_socket           27095  0 
pcmcia_rsrc            18191  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
lpc_ich                16925  0 
drm_kms_helper         45271  1 i915
soundcore              14599  1 snd
drm                   230463  4 i915,drm_kms_helper
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
ssb_hcd                12749  0 
i2c_algo_bit           13197  1 i915
rfcomm                 37276  0 
bnep                   17707  2 
parport_pc             31968  0 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
wmi                    18590  1 acer_wmi
mac_hid                13037  0 
video                  18847  2 acer_wmi,i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
b44                    31326  0 
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ssb                    50087  3 b43,ssb_hcd,b44


**** nm-tool ****



NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off




**** NetworkManager.state ****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


**** NetworkManager.conf ****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false


**** NetworkManager.conf-10.04 ****




**** interfaces ****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


**** iwlist ****




**** resolv ****


# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN


**** blacklist.conf ****


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


**** dmesg ****


[    2.012074] ssb: Found chip with id 0x4311, rev 0x01 and package 0x00
[    2.012087] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    2.012096] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    2.012105] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    2.012115] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    2.052313] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    2.135852] b44 0000:06:01.0: >setting latency timer to 64
[    2.152093] ssb: Found chip with id 0x4401, rev 0x02 and package 0x00
[    2.152105] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    2.152112] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    2.152120] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    2.192157] ssb: Sonics Silicon Backplane found on PCI device 0000:06:01.0
[    2.192193] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    2.212599] b44 ssb1:0: >eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver <MAC address removed>
[   16.971224] wmi: Mapper loaded
[   17.542871] acer_wmi: Acer Laptop ACPI-WMI Extras
[   17.592631] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   17.640603] acer_wmi: Function bitmap for Communication Device: 0x21
[   17.641517] Registered led device: acer-wmi::mail
[   17.757150] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   17.757157] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   17.757161] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   17.825285] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.825785] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready


**************** done ********************




```

---

### Post by SalamFromMaroc on 2013-02-19
I don t have Ethernet cable.I no have internet access in my Ubuntu is because of this i try use my wifi,but unfortunately don t want work with me until now.
 I HAVE WPA2-PSK  WITH AES WIRELESS SECURITY AND WHEN I TRY ADD THIS CONNECTION I CAN T ,
I CAN ACCESS TO THIS OPTION FOR ADD WIRELESS.BUT I DON T KNOW  CONFIGURATION ,.I THINK IF EVERYTHING WORK CORRECTLY WILL SHOW CONNECT TO HIDDEN WIRELESS THEN I WILL ADD MY SSID + MY NETWORK KEY TO CONNECT,but this is impossible from me

---

### Post by westie457 on 2013-02-20
Boot into Windows. Go to here and click on any of these links. [http://packages.ubuntu.com/quantal/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/quantal/all/linux-firmware-nonfree/download)

Copy to a USB stick or a CD. Boot into Ubuntu and copy the file to your Desktop. Double click it and Software Centre should install the package for you.

If it does not, open a terminal and ```
cd ~/Desktop
sudo dpkg -i linux*.deb
```
The above assumes there is only the one file on your Desktop, if more than one type in the full name of the package.

You might have to run the modprobe commands again. A reboot should reset everything for you anyway.

Again let us know what happens.

Thank you.

@ Wild Man

Thanks for reminding me of the wireless script, it came in handy for a different thread.

---

### Post by bigmonmulgrew on 2013-02-20
Would it not be easier to just dig out an ethernet cable from somewhere, routers come with them. You must have one in a box somewhere or maybe its plugged into another pc, you could borrow it.

---

### Post by SalamFromMaroc on 2013-02-21
thank you so much for our help,

my decision is back to windows ,maybe in future when Ubuntu will be more easier i will use it.

---

### Post by westie457 on 2013-02-21
As you said your decision.

Good luck and enjoy yourself.

If/when you change your mind we will still help.

---

### Post by wildmanne39 on 2013-02-21
Your are welcome to come back anytime.

---

### Post by SalamFromMaroc on 2013-02-21
I did try this last solution and now everything ok,i can connect to my wireless.thank you so much for everything.

now i will not use only windows but i will use ubuntu also,and i am very happy for see pple help each other like you friends

may god bless you all

---


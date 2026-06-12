---
title: "Setting up the wireless connection in Ubuntu (Dell Vostro 1400)"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by user0110 on 2012-06-30
Hello,

This forum looks really helpful! I installed Ubuntu 11.04 and was trying to configure the wireless, but I don't know how I could get started. I was browsing a few threads and thought that executing this command might get me started:

sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

I don't know if the command messed up any of the drivers. I would really appreciate it someone could someone please help me setup the wireless?

Thanks so much!

---

### Post by mikewhatever on 2012-07-01
Hi, and welcome to the forums. Generally speaking, you should not run any commands. If a driver for the wireless card is available, you should see a notification offering to install it. If you don't, please post the output of **lspci**.

PS: The command you've used removes packages which aren't installed by default, so it shouldn't have caused any harm.

---

### Post by user0110 on 2012-07-01
Hi Mike,

Thanks a lot for taking the time to help me out! The following is what I got from running lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

---

### Post by westie457 on 2012-07-01
Hi, if I remember correctly the Broadcom 4311 chip uses the Driver that is suggested by 'Additional Drivers'. Install that and reboot, your wireless should now be working.

If it does not repost here and we will dig deeper.

---

### Post by user0110 on 2012-07-01
I just opened System Settings and installed the additional drivers (restarted my laptop upon the installation completion), but the wireless isn't working yet. Did I miss something?

Thanks again!

---

### Post by westie457 on 2012-07-01
Please post the output of these commands
```
lspci -vnn

lsmod

rfkill list all
```

Thank you.

---

### Post by rg4w on 2012-07-01
FWIW I have a Dell Vostro 1400 (hate the touchpad, love the monitor), and wireless has always worked out of the box for me in 10.04, 10.10, 11.10, and 12.04.

Are you sure you have the hardware switch on the front of the case turned on?  I accidentally flipped mine once and it took me more than an hour to figure out that it wasn't a software issue. ;)

---

### Post by user0110 on 2012-07-01
Here is what lspci -vnn displayed:

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at fea00000 (64-bit, non-prefetchable) [size=1M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at efe8 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, fast devsel, latency 0
    Memory at feb00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f20 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f00 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 80400000-805fffff
    Prefetchable memory behind bridge: 0000000080600000-00000000807fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: fe800000-fe8fffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fe600000-fe7fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fe500000-fe5fffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6f80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6f60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) (prog-if 00 [UHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6f40 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 20
    Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: fe400000-fe4fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 6fa0 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 6eb0 [size=8]
    I/O ports at 6eb8 [size=4]
    I/O ports at 6ec0 [size=8]
    I/O ports at 6ec8 [size=4]
    I/O ports at 6ee0 [size=16]
    I/O ports at eff0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
    Subsystem: Dell Device [1028:0227]
    Flags: medium devsel, IRQ 10
    Memory at fe9fbf00 (32-bit, non-prefetchable) [size=256]
    I/O ports at 10c0 [size=32]
    Kernel modules: i2c-i801

03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at fe4ff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci

03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) (prog-if 01)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe4ff500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe4ff600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r592
    Kernel modules: r592

03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, medium devsel, latency 64, IRQ 18
    Memory at fe4ff700 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: r852
    Kernel modules: r852

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Dell Device [1028:0227]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at fe5f0000 (64-bit, non-prefetchable) [size=64K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: tg3
    Kernel modules: tg3

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at fe8fc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl, ssb


----------------------------------------------

lsmod generated the following text:

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
joydev                 17393  0 
snd_hda_codec_idt      60049  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          28358  2 
dell_laptop            13519  0 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
dcdbas                 14098  1 dell_laptop
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
r592                   17808  0 
psmouse                73673  0 
serio_raw              12990  0 
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
memstick               15857  1 r592
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
wl                   2646601  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
wmi                    18744  1 dell_wmi
i915                  513798  3 
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19069  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
tg3                   132972  0 

-----------------------

lskill list all:

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

I have the wireless switch turned on :--) , but I don't see my wireless network. Yeah, the touch pad isn't very impressive, but the 14 inch monitor is pretty decent!

---

### Post by westie457 on 2012-07-02
Hi, follow the directions in this post [http://ubuntuforums.org/showpost.php?p=12015089&postcount=3](http://ubuntuforums.org/showpost.php?p=12015089&postcount=3)

Post back here with the news

Thank you

---

### Post by user0110 on 2012-07-02
Hi Westie,

Not working yet, but the "enable Wireless" is showing up (i.e. I'm able to enable and disable the option). Is the wireless card working?

The following output was produced when I executed the commands you gave me:

sudo apt-get install b43-fwcutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-----------

sudo apt-get install firmware-b43-fwcutter

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-fwcutter

Thank you.

---

### Post by westie457 on 2012-07-02
Hi, if that has happened then you need to enable the 'restricted repositories'.

Open the 'Software Centre', click on Edit and select Software Sources. Make sure the first four boxes are checked in the first tab of the window. Click on Close. At some stage your password will be needed.

Open a terminal and run the ```
sudo apt-get install firmware b43-installer
``` command again.

Leave the terminal open just in case it is needed. Check the Network icon for available networks. It will take some seconds for them to appear.

If none after a short period of time in the terminal type in and run ```
sudo modprobe b43
```. It should now be working.

Again post back here with the news.

Thank you.

---

### Post by user0110 on 2012-07-03
Hi,

The output for sudo apt-get install firmware b43-installer is just the same as the output I got the last time. I tried Software Center and the all the 4 options have been selected. The sudo modprobe b43 didn't work either. The "Enable Wireless" (network applet menu) shows up, but the "Wireless Networks" option has been grayed out.  What should I do next?

Thank you.

---

### Post by westie457 on 2012-07-03
Hi, apologies from me, there is a typo in the command. It should be ```
sudo apt-get install firmware-b43-installer
```

The modprobe command will only be necessary if no networks show after a few seconds.

let us know the result.

Thank you

---

### Post by user0110 on 2012-07-03
Hi Westie,

Excellent! The wireless is working and I jumped off my chair when I saw my wireless working :-D Thanks so much for your time!!

I can now enjoy my Linux installation. How can I start learning Linux? Could you please give me some suggestions? Are there any good books? I will also browse different threads here and learn new things.

Thanks again!!

---


---
title: "Problema Wi Fi Invoco al conocimiento de Uds."
date: 2015-07-13
forum: Peru Team
---

### Post by renzothc23 on 2015-07-13
Hola uso la versión 15.04 y mi tarjeta es Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] no conecta a red wi fi solo cableado (la versión 14.04 tampoco conectaba).
Al insertar lspci -nn


00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
0a:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
0a:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
0a:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
0a:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
root@BK23-LENOVO3000-N200:/home/bikeman23# lsmod
Module                  Size  Used by
nls_utf8               16384  0 
btrfs                 937984  0 
xor                    28672  1 btrfs
raid6_pq               98304  1 btrfs
ufs                    77824  0 
qnx4                   16384  0 
hfsplus                94208  0 
hfs                    53248  0 
minix                  32768  0 
ntfs                  102400  0 
msdos                  20480  0 
jfs                   172032  0 
xfs                   831488  0 
libcrc32c              16384  1 xfs
rfcomm                 65536  8 
bnep                   20480  2 
snd_hda_codec_conexant    24576  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_conexant
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
arc4                   16384  2 
acer_wmi               20480  0 
r852                   20480  0 
sparse_keymap          16384  1 acer_wmi
sm_common              20480  1 r852
snd_seq_midi_event     16384  1 snd_seq_midi
iwl3945                65536  0 
nand                   69632  2 r852,sm_common
iwlegacy               90112  1 iwl3945
i915                  937984  3 
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
nand_ecc               16384  1 nand
mac80211              626688  2 iwl3945,iwlegacy
nand_bch               16384  1 nand
cdc_ether              16384  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
bch                    20480  1 nand_bch
usbnet                 40960  1 cdc_ether
mii                    16384  1 usbnet
coretemp               16384  0 
cdc_acm                32768  2 
joydev                 20480  0 
nand_ids               12288  1 nand
serio_raw              16384  0 
snd                    69632  16 snd_hwdep,snd_timer,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
mtd                    57344  2 nand,sm_common
drm_kms_helper        110592  1 i915
btusb                  32768  0 
cfg80211              462848  3 iwl3945,iwlegacy,mac80211
soundcore              16384  2 snd,snd_hda_codec
drm                   286720  5 i915,drm_kms_helper
bluetooth             434176  22 bnep,btusb,rfcomm
r592                   20480  0 
memstick               16384  1 r592
lpc_ich                20480  0 
i2c_algo_bit           16384  1 i915
wmi                    20480  1 acer_wmi
shpchp                 32768  0 
video                  20480  2 i915,acer_wmi
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                40960  3 lp,ppdev,parport_pc
autofs4                40960  2 
ahci                   28672  2 
psmouse               106496  0 
firewire_ohci          36864  0 
libahci                32768  1 ahci
firewire_core          65536  1 firewire_ohci
crc_itu_t              16384  1 firewire_core
pata_acpi              16384  0 
sdhci_pci              20480  0 
tg3                   159744  0 
sdhci                  45056  1 sdhci_pci
ptp                    20480  1 tg3
pps_core               20480  1 ptp




Agradesco quien me pueda ayudar. Saludos, Bk23

---

### Post by Ricardo_Velasco on 2015-11-25
Saludos:

Intenta este tipo de solucion:

Ejecuta en tu terminal:

> dmesg | grep -i iwl3945

Si te sale algo como esto:
> 
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
iwl3945: Copyright(c) 2003-2007 Intel Corporation
Detected Intel PRO/Wireless 3945BG Network Connection
iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
wmaster0: Selected rate control algorithm &#8216;iwl-3945-rs&#8217;
iwl3945: Microcode SW error detected.  Restarting 0x82000008.
iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
iwl3945: Can&#8217;t stop Rx DMA.

Luego de esto pones en la terminal:

> sudo su
Contraseña de root

> echo alias wlan0 iwl3945>/etc/modprobe.d/iwl3945

> echo options iwl3945 disable_hw_scan=1>>/etc/modprobe.d/iwl3945

> modprobe -r iwl3945


Me dices si te funciono ahi la tarjeta inalambrica

---


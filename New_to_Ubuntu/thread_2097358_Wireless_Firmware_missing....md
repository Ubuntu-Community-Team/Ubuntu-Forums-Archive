---
title: "Wireless Firmware missing...?"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by RaineShadow on 2012-12-22
Everything works except for the wireless connection. 

I've heard to type in these codes and this is what it gives with each.

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

```
uname -a
Linux giselle-HP-Pavilion-ze2000-EC196UA-ABA 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 athlon i386 GNU/Linux
```

```
dmesg | grep -ie firm
[    0.076004] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[   26.138604] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   26.138611] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   26.138616] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  978.973278] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  978.973285] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  978.973290] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

```
lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:3091]
	Kernel driver in use: 8139too
--
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:1355]
	Kernel driver in use: b43-pci-bridge

```

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
lsmod
Module                  Size  Used by
snd_atiixp_modem       18604  5
snd_via82xx_modem      18377  0
snd_intel8x0m          18498  0
joydev                 17393  0
hp_wmi                 13652  0
sparse_keymap          13658  1 hp_wmi
arc4                   12473  2
b43                   342643  0
snd_atiixp             19337  2
snd_seq_midi           13132  0
pcmcia                 39791  0
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436455  1 b43
bnep                   17830  2
rfcomm                 38139  0
snd_ac97_codec        106082  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp
ac97_bus               12642  1 snd_ac97_codec
bluetooth             158438  8 bnep,rfcomm
parport_pc             32114  0
radeon                737789  3
ppdev                  12849  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80845  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_seq,snd_pcm
cfg80211              178679  2 b43,mac80211
yenta_socket           27465  0
psmouse                72919  0
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12905  0
bcma                   25651  1 b43
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
snd                    62064  22 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_rawmidi,snd_ac97_codec,snd_seq,snd_pcm,snd_timer,snd_seq_device
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
serio_raw              13027  0
video                  19068  0
soundcore              14635  1 snd
snd_page_alloc         14108  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_atiixp,snd_pcm
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 hp_wmi
i2c_piix4              13093  0
ati_agp                13242  0
shpchp                 32325  0
mac_hid                13077  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
ssb                    50691  1 b43
8139too                23283  0
8139cp                 26759  0
pata_atiixp            12999  2

```

---

### Post by ptn107 on 2012-12-22
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by RaineShadow on 2012-12-22
Thanks

---

### Post by wildmanne39 on 2012-12-22
Hi, this is what you need to do.

[http://ubuntuforums.org/showthread.php?t=2094547](http://ubuntuforums.org/showthread.php?t=2094547)
Post 9.
Thanks

---


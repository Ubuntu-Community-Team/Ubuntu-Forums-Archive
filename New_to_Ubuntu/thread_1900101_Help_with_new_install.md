---
title: "Help with new install"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by sparkylabs on 2011-12-25
I'm working through the commands now, The laptop cost me £130, it cost 1300 6 years ago when it WAS cutting edge, hence my thinking it's hardware must be pretty much legacy by now.

I'm not here just to moan but I'm so bewildered, there is so much talk of it working out of the box and being great for begginers, and runs on so many systems - are we sure ?

> **waynefoutz said:**
> Is the OP looking for help or is this just going to be an "Ubuntu sucks" thread?

Sparky, you were given a list of command a few posts back, if you post the output of them, we can then know what kind of hardware you're sporting and give you a hand in getting it working. 

If you spent that much money on a laptop with bleeding edge hardware, then you can't really expect Linux support if the OEM doesn't provide it. 

Again if you get more specific, ask constructive questions, the community here would be more than happy to lend you a hand.

---

### Post by sparkylabs on 2011-12-25
lsmod gives:


simon@Ubuntu-Laptop:~$ lsmod
Module                  Size  Used by
michael_mic            12540  4 
arc4                   12473  2 
lib80211_crypt_tkip    17240  1 
lib80211_crypt_ccmp    12789  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
sata_via               13534  0 
mmc_block              22393  2 
joydev                 17393  0 
tifm_sd                17566  0 
snd_intel8x0           33318  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  3 snd_intel8x0,snd_ac97_codec
hp_wmi                 13652  0 
ppdev                  12849  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
r8712u                163310  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcmcia                 39822  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146148  0 
tifm_7xx1              12937  0 
libipw                 46701  1 ipw2200
cfg80211              172392  2 ipw2200,libipw
tifm_core              15040  2 tifm_sd,tifm_7xx1
snd                    55902  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
lib80211               14570  4 lib80211_crypt_tkip,lib80211_crypt_ccmp,ipw2200,libipw
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
binfmt_misc            17292  1 
i915                  505159  3 
irda                  185428  0 
parport_pc             32114  1 
crc_ccitt              12595  1 irda
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
tg3                   132972  0

---

### Post by sparkylabs on 2011-12-25
simon@Ubuntu-Laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
02:06.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
02:06.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
02:06.5 Communication controller [0780]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller [104c:8035]
03:00.0 RAID bus controller [0104]: VIA Technologies, Inc. VT6421 IDE RAID Controller [1106:3249] (rev 50)
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express [14e4:167d] (rev 11)

---

### Post by sparkylabs on 2011-12-25
simon@Ubuntu-Laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

---

### Post by Elfy on 2011-12-25
Sorry - didn't notice this was closed - not sure what happened there.

---


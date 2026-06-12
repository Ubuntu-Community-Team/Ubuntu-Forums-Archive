---
title: "Turn on wifi"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by richie16171 on 2012-11-09
After I changed the wifi card, I cant get the wifi.
Please help me

  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:8d:22:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=full ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 memory:d3307000-d330707f ioport:1000(size=128)
richie@richie-Tehom-8160:~$ lspci -nn | grep -e 0280 -e 0200
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
richie@richie-Tehom-8160:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

richie@richie-Tehom-8160:~$ rfkill list all
richie@richie-Tehom-8160:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
hfsplus                84442  1 
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
coretemp               13400  0 
snd_hda_codec_si3054    13008  1 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
microcode              22803  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
jmb38x_ms              17416  0 
soundcore              15047  1 snd
psmouse                95552  0 
memstick               16554  1 jmb38x_ms
serio_raw              13215  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
joydev                 17457  0 
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
nouveau               895609  4 
mac_hid                13205  0 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
drm                   275528  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19335  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
sis_agp                13327  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
sis190                 22625  0 
richie@richie-Tehom-8160:~$

---

### Post by cariboo on 2012-11-11
What make/model wireless device are you using?

---

### Post by richie16171 on 2012-11-14
> **cariboo907 said:**
> What make/model wireless device are you using?

Thank you,, Infact I installed probably faulty intel wifi card. Replaced and now it is ok.

---


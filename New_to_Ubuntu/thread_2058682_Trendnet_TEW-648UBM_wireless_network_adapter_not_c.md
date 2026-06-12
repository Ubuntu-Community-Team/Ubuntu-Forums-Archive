---
title: "Trendnet TEW-648UBM wireless network adapter not connecting"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by pshone on 2012-09-16
Hi 

I am an absolute newbie to Ubuntu.  I have installed Ubuntu 12.04 and am trying to  get my Ubuntu machine to connect to my home network.  The wireless sees the network and attempts to connect but after a few seconds asks for the network key.  It tries to connect again then asks for the key again.

My lsmod
pshone@Ubuntu1:~$ lsmod
Module                  Size  Used by
arc4                   12473  2 
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
cfg80211              178679  2 rtlwifi,mac80211
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0 
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
serio_raw              13027  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
nouveau               712294  2 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197692  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
video                  19068  1 nouveau
parport_pc             32114  1 
mac_hid                13077  0 
shpchp                 32325  0 
sis_agp                13165  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 26759  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0

Can someone please help.

---


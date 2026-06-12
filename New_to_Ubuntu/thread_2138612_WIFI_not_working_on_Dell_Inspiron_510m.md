---
title: "WIFI not working on Dell Inspiron 510m"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by basmatig on 2013-04-24
Dear forum users,

I just installed Ubuntu 12.04 LTS on my Dell Inspiron 510m. Everything is runnng fine but I cannot connect through WIFI. No wireless connections are shown in the upper right menu and using the FnF2 command shows no results.

Can anyone please help me. I have tried quite some things but without any succes.

---

### Post by Hadaka on 2013-04-24
Hi, please open a terminal ctrl/alt/t
then COPY and paste the following..
```
lspci -nn | egrep '0200|0280'
lsmod
rfkill list all
```
post the results
thanks.

---

### Post by basmatig on 2013-04-26
Dear Adaka,

Tnx for your help. I have not been responding real quick but I am out of the house a lot these days due to the holidays. I noticed that when I boot the pc under windows the WIFI is off too. In windows the fnF2 command does the job. See the results hereunder:

basmaat@basmaat-laptop:~$ lspci -nn | egrep '0200|0280'
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
basmaat@basmaat-laptop:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
wl                   3032542  1 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
joydev                 17393  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
dell_laptop            17767  0 
cfg80211              178877  1 wl
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14040  1 wl
dcdbas                 14098  1 dell_laptop
psmouse                96718  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
serio_raw              13027  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32265  0 
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
i915                  423514  2 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
e100                   36289  0 
crc_itu_t              12627  1 firewire_core
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915

---


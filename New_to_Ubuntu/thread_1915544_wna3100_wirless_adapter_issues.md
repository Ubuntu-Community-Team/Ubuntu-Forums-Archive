---
title: "wna3100 wirless adapter issues"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by Calgacus on 2012-01-26
More problems for this forum on WNA3100 wireless adapters

ndiswrapper -l    brings up   autorun:invalid driver
                                             bcmn43xx64:driver installed
                                             device (0846:9020) present

is this wireless adapter working correctly as    iwlist scan just says
                                             lo interface doesnt support scanning
                                             etho interface doesnt support scanning but no mention of wlan



Any help would be greatly appreciated and your community spirit is awesome and would like to learn to contribute but a bit of a noob here

---

### Post by Calgacus on 2012-01-26
**wna3100 wirless adapter issues**             
                                                                More problems for this forum on WNA3100 wireless adapters

ndiswrapper -l    brings up   autorun:invalid driver
                                             bcmn43xx64:driver installed
                                             device (0846:9020) present

is this wireless adapter working correctly as    iwlist scan just says
                                             lo interface doesnt support scanning
                                             etho interface doesnt support scanning but no mention of wlan



Any help would be greatly appreciated and your community spirit is  awesome and would like to learn to contribute but a bit of a noob here

---

### Post by Calgacus on 2012-01-26
1. dani@dani-imedia-S1300:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux dani-imedia-S1300 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 athlon i386 GNU/Linux

2. dani@dani-imedia-S1300:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device [1025:8000]
    Kernel driver in use: forcedeth

but lsusb gives
dani@dani-imedia-S1300:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
dani@dani-imedia-S1300:~$ 

3. dani@dani-imedia-S1300:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

dani@dani-imedia-S1300:~$ 

4. dani@dani-imedia-S1300:~$ rfkill list all
dani@dani-imedia-S1300:~$ 

5.dani@dani-imedia-S1300:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
nvidia               7098131  34 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
k10temp                12990  0 
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  0 
snd                    55902  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  0 
uas                    17699  0 
pata_amd               13753  0 
sata_nv                23379  2 
forcedeth              58103  0 
dani@dani-imedia-S1300:~$

---

### Post by lisati on 2012-01-26
Threads merged.

Please do not start multiple threads for a problem, it dilutes the community's ability to help.

---

### Post by anewguy on 2012-01-26
You are just compounding things by making a duplicate thread.  I have reported this thread as a duplicate and it will get merged back into the original.  All you would end up with is answers spread out all over the forum.  If you want your thread looked at, *AND* it's been at least 24 hours, then bump it.

Any reply I post will be in the original thread.

Both of the threads merged here belong with your ORIGINAL thread - [http://ubuntuforums.org/showthread.php?t=1793758](http://ubuntuforums.org/showthread.php?t=1793758)

---

### Post by Calgacus on 2012-01-27
Sorry guys was unaware of the problem, just growing frustrated

---


---
title: "Wireless Card present, networks present, not connecting"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by steve04412 on 2012-06-28
Hi there - I'm another Linux newbie having wireless problems.  I've looked around, and tried some troubleshooting, but I'm still having no luck.  

From what I've read in this forum, there is some specific information you need, regarding my computer, so I have tried to include as much info as possible below.

I recently got a used HP/Compaq nx7400 computer (512mb ram, celeron M processor), wiped the HDD, and installed Ubuntu 12.04 as the only OS.  I'm really enjoying the Ubuntu 'experience' but I am unable to connect to any wireless networks.  Wired networking seems fine.  I have tried running updates, and I also checked drivers, and it says that the Broadcom wireless card is active, but when I click on the network connections up by the clock, I only have Wired Network options.  I have checked in the BIOS of the laptop to ensure that the Ethernet is on, and LAN/WLAN switching is enabled (so wireless stays on, even when the network cable is plugged in), but I still cannot get anything.  I have rebooted 5-6 times in all my troubleshooting.  I have checked inside the case, and the network card IS there, and the antenna is plugged in.  There is a 'wireless button' above the keyboard, but when I click it, it doesn't illuminate blue like I would expect it to, but I'm not sure if that is a 'windows-only' button or something?

From what I've seen, I kinda thought that having a wireless nic installed, with proper drivers and all, that my laptop would auto-detect available networks, but it doesn't seem to work.  I've tried at home, and on my company's guest access network, no luck either place.  (I did also confirm that I was able to connect to each of these networks with non-ubuntu laptops).

Any help you all could offer would be great! Please let me know if any additional information is required to aid in troubleshooting. 

Thanks, 
Steve

```

page@Page02:~$ uname -a 
Linux Page02 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux 

page@Page02:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01) 
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01) 
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01) 
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 01) 
00:1d.0 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01) 
00:1d.1 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01) 
00:1d.2 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01) 
00:1d.3 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01) 
00:1d.7 USB controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] [8086:27c5] (rev 01) 
02:06.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039] 
02:06.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a] 
02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
10:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
page@Page02:~$  

page@Page02:~$ lsmod 
Module                  Size  Used by 
btrfs                 638208  0  
zlib_deflate           26622  1 btrfs 
libcrc32c              12543  1 btrfs 
ufs                    78131  0  
qnx4                   13309  0  
hfsplus                83507  0  
hfs                    49479  0  
minix                  31418  0  
ntfs                  100171  0  
vfat                   17308  0  
msdos                  17132  0  
fat                    55605  2 vfat,msdos 
jfs                   175085  0  
xfs                   747494  0  
reiserfs              230896  0  
ext2                   67987  0  
bnep                   17830  2  
bluetooth             158438  7 bnep 
snd_hda_codec_si3054    12864  1  
snd_hda_codec_analog    75395  1  
snd_hda_intel          32765  2  
snd_hda_codec         109562  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80845  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0  
hp_wmi                 13652  0  
snd_rawmidi            25424  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
sparse_keymap          13658  1 hp_wmi 
joydev                 17393  0  
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
ppdev                  12849  0  
pcmcia                 39791  0  
b44                    31364  0  
ssb                    50691  1 b44 
snd_timer              28931  2 snd_pcm,snd_seq 
wl                   2646601  0  
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
yenta_socket           27465  0  
pcmcia_rsrc            18367  1 yenta_socket 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
i915                  414603  3  
psmouse                72846  0  
serio_raw              13027  0  
drm_kms_helper         45466  1 i915 
snd                    62064  14 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
parport_pc             32114  1  
wmi                    18744  1 hp_wmi 
drm                   197692  4 i915,drm_kms_helper 
i2c_algo_bit           13199  1 i915 
lib80211               14040  1 wl 
soundcore              14635  1 snd 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm 
video                  19068  1 i915 
mac_hid                13077  0  
lp                     17455  0  
parport                40930  3 ppdev,parport_pc,lp 
firewire_ohci          40172  0  
firewire_core          56906  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 


page@Page02:~$ rfkill list all 
0: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 

```

---

### Post by wildmanne39 on 2012-06-28
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot.
Thanks

---

### Post by steve04412 on 2012-06-29
wildmanne=hero.  Gold star for the day.  :)

Thanks!

---

### Post by wildmanne39 on 2012-06-29
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---


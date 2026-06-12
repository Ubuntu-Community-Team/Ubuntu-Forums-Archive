---
title: "Internet dropping"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by BeMyManikin on 2012-08-31
I know I've posted this before, but I still never got it fixed. I will try again. Here is the original post: [http://ubuntuforums.org/showthread.php?t=1969330](http://ubuntuforums.org/showthread.php?t=1969330)
**I have a dual boot of Ubuntu 11.10 and Windows 7 desktop**.
Here is the proof that it does drop it when I did some pings:
```
                                   --- google.com ping statistics ---  
 16 packets transmitted, 14 received, 12% packet loss, time 15036ms  
 rtt min/avg/max/mdev = 21.834/25.711/40.186/5.364 ms  
  
 20 packets transmitted, 19 received, 5% packet loss, time 19035ms  
 rtt min/avg/max/mdev = 21.993/26.385/44.263/6.287 ms  
  
 20 packets transmitted, 19 received, 5% packet loss, time 23082ms  
 rtt min/avg/max/mdev = 21.570/25.973/35.060/4.484 ms  
  
 20 packets transmitted, 20 received, 0% packet loss, time 19028ms  
 rtt min/avg/max/mdev = 20.902/24.485/47.741/5.593 ms  
  
 20 packets transmitted, 20 received, 0% packet loss, time 19026ms  
 rtt min/avg/max/mdev = 21.927/24.723/32.005/3.268 ms  
  
 20 packets transmitted, 19 received, 5% packet loss, time 19027ms  
 rtt min/avg/max/mdev = 20.554/25.231/48.545/6.574 ms  
  
 20 packets transmitted, 16 received, 20% packet loss, time 19045ms  
 rtt min/avg/max/mdev = 21.515/28.106/90.123/16.318 ms  
  
 20 packets transmitted, 19 received, 5% packet loss, time 23095ms
 rtt min/avg/max/mdev = 20.573/23.587/31.546/2.673 ms
  
 5 packets transmitted, 2 received, +3 errors, 60% packet loss, time 77364ms  
 rtt min/avg/max/mdev = 23.600/24.548/25.497/0.961 ms, pipe 3  
  
```That's not including the times when I said that Google was a unknown host.
Any help will be appreciated.

---

### Post by jtarin on 2012-08-31
Post the terminal results from the command ```
lsmod 
``` Let's see if it's loading the correct module for your card.

---

### Post by BeMyManikin on 2012-09-07
it says
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166150  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13844  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
snd_hda_intel          33390  2 
snd_hda_codec         104968  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17540  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
joydev                 17693  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
edac_core              53746  0 
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sp5100_tco             13791  0 
i2c_piix4              13301  0 
k10temp                13166  0 
fam15h_power           13115  0 
fglrx                2928969  98 
wmi                    19256  0 
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
usb_storage            57900  1 
uas                    18181  0 
pata_atiixp            13164  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               82820  0 
r8169                  52788  0 

```Sorry, for the late reply, been busy.
also the code for lspci -nn | grep -ia2 net
```
01:00.1 Audio device [0403]: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series] [1002:aa68]
02:00.0 USB Controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
```

---


---
title: "Enabling Wireless on Presario C300 - Ubuntu"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by rowdie85 on 2012-05-20
So I've just had some friends install Ubuntu on my old Presario C300, but not my physical switch to enable wireless internet does not function. Unfortunately, my friends had to leave town so I'm stuck with a half finished job! 

I'm not good with computers, but I searched a forum to check my devices and ran the "lshw -c network" command and it says "network UNCLAIMED".

Can anybody help me walk through how to find the correct wireless driver and how to enable wireless internet on my laptop?

Thanks!!

---

### Post by fooman on 2012-05-20
hi could you run that command again...but this time post the entire results back here (copy and paste).  

also don't know which version of ubuntu you have installed (11.04,  11.10, 12.04...etc).  and whether it was installed onto a partition or through windows (wubi).

you should check in "additional drivers" and see if there is a broadcom (or broadcom STA) driver available.  if there is then install/enable it.  you will need an ethernet connection to download the driver.

---

### Post by wildmanne39 on 2012-05-20
Hi, unclaimed means you need to install a driver please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Seizure on 2012-07-25
Hi, I'm not the OP but I'm in the exact same situation. I was wondering if anyone could help me out ith this predicament. I checked this models handling on a linux wiki and it seems that the wireless internet connection is the hardest part about this model.

Following up on what wildemanne39 said, here are the terminal dialogues in order:
```
debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux debra-Presario-C300-RH210UA-ABA 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:46:35 UTC 2012 i686 i686 i386 GNU/Linux

```

```
lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel modules: wl, ssb
08:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: 8139too
debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ 



```
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ 




```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ 

```
```
rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ 

```
```
lsmod
Module                  Size  Used by
rfcomm                 38139  4 
snd_hda_codec_conexant    52516  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
parport_pc             32114  0 
bnep                   17830  2 
i915                  414668  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13652  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
wl                   2646601  0 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
psmouse                87213  0 
lib80211               14040  1 wl
serio_raw              13027  0 
mac_hid                13077  0 
video                  19068  1 i915
wmi                    18744  1 hp_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22633  0 
debra@debra-Presario-C300-RH210UA-ABA:~/Desktop$ 

```

Right now I'm a huge Newb when it comes to this. But I'm really starting to get the feel of linux and I'm definitely eager to learn more :popcorn:

Any help is much appreciated. Thanks.

---

### Post by wildmanne39 on 2012-07-25
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install linux-firmware-nonfree
```
Make surew your wireless is turned on.
Reboot
Thanks

---

### Post by Seizure on 2012-07-25
Wildmanne thank you very, very, very, very, very much!!
Works perfectly now

---

### Post by wildmanne39 on 2012-07-25
Hi, your welcome! please use thread tools at the top of the page and mark the thread solved.
Enjoy

---

### Post by Masophere on 2013-01-21
Hi there i am just getting into linux and its features, finally got my head round what all these new words mean, I have read alot that it is not possible to enable wifi on some presario c300's with ubuntu 12.04 LTS, ive been trying to figure it out for weeks getting tired of my ethernet cable until my friend handed me a broadband providers USB dongle popped it in and hey presto instantly tells me theres 2 available networks in my vicinity connects just fine.. Hope this is helpful to others who also enjoy representing the low end laptop scene. :p:p

---


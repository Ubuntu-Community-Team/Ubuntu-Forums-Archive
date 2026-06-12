---
title: "no wireless"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by helphelp on 2012-06-24
Hi
I installed ubuntu and i havn't got any wireless connection.

---

### Post by wildmanne39 on 2012-06-24
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by helphelp on 2012-06-24
guest-XL6Zhi@mohammed-Inspiron-N5040:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux mohammed-Inspiron-N5040 3.0.0-21-generic-pae #35-Ubuntu SMP Fri May 25 18:17:24 UTC 2012 i686 i686 i386 GNU/Linux
guest-XL6Zhi@mohammed-Inspiron-N5040:~$ lspci -nnk | grep -iA2 net
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0012]
    Kernel driver in use: brcmsmac
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0505]
    Kernel driver in use: r8169
guest-XL6Zhi@mohammed-Inspiron-N5040:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 004: ID 064e:8123 Suyin Corp. 
guest-XL6Zhi@mohammed-Inspiron-N5040:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

guest-XL6Zhi@mohammed-Inspiron-N5040:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
guest-XL6Zhi@mohammed-Inspiron-N5040:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  8 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
snd_hda_codec_hdmi     31426  1 
arc4                   12473  2 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91888  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  513841  3 
snd_seq_midi           13132  0 
brcmsmac              591864  0 
brcmutil               16885  1 brcmsmac
mac80211              393421  1 brcmsmac
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
dell_wmi               12601  0 
psmouse                63474  0 
serio_raw              12990  0 
sparse_keymap          13658  1 dell_wmi
intel_ips              17753  0 
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
lp                     17455  0 
dell_laptop            13519  0 
wmi                    18744  1 dell_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dcdbas                 14098  1 dell_laptop
mei                    36466  0 
parport                40930  3 parport_pc,ppdev,lp
video                  19069  1 i915
bluetooth             148869  23 rfcomm,bnep,btusb
cfg80211              172427  2 brcmsmac,mac80211
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
crc_ccitt              12595  1 brcmsmac
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
r8169                  47200  0 
ahci                   21634  2 
libahci                25761  1 ahci
guest-XL6Zhi@mohammed-Inspiron-N5040:~$

---

### Post by wildmanne39 on 2012-06-24
Hi, please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Just copy and paste for accuracy.
Reboot.
Thanks

---

### Post by helphelp on 2012-06-24
mohammed@mohammed-Inspiron-N5040:~$ echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
[sudo] password for mohammed: 
blacklist bcma
mohammed@mohammed-Inspiron-N5040:~$ echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist brcmsmac
mohammed@mohammed-Inspiron-N5040:~$

---

### Post by wildmanne39 on 2012-06-24
Hi, did you paste those commands into the terminal? then did you reboot? If so did wireless come on?
Thanks

---

### Post by helphelp on 2012-06-24
No i didn't reboot

---

### Post by wildmanne39 on 2012-06-24
Hi, reboot please.
Thanks

---

### Post by helphelp on 2012-06-24
Sorry will try again didn't see to reboot

---

### Post by helphelp on 2012-06-24
Do i need to put the commands in again

---

### Post by wildmanne39 on 2012-06-24
No.

---


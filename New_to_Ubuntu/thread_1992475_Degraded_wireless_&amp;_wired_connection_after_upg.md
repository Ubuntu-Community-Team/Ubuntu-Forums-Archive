---
title: "Degraded wireless &amp; wired connection after upgrade to 11.04"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by jamarsh123 on 2012-05-31
Acer Aspire laptop.  Upgraded from 10.10 to 11.04.  Internet connection speeds are now slower than dial-up.  I have not found a post mentioning slow speeds with both wired and wireless internet speeds.  Any help resolving this is much appreciated

---

### Post by jamarsh123 on 2012-05-31
My subject is not in bold (don't know why), and I don't have a nifty little arrow to the left of my post.  Perhaps that is why there are no responses. :(

---

### Post by wildmanne39 on 2012-05-31
Hi, it takes time for the people with the right knowledge to get online to help you, please be patient.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

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

### Post by ts3 on 2012-05-31
> **jamarsh123 said:**
> My subject is not in bold (don't know why), and I don't have a nifty little arrow to the left of my post.  Perhaps that is why there are no responses. :(

Completely unrelated to the wireless issue but I thought I'd mention it :) your thread is not bold b/c you've accessed it, it appears in bold to other forum users who have not read it yet.

---

### Post by jamarsh123 on 2012-05-31
Hi: Thanks for the reply.  Here are the results:
cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux john-Aspire-5742 2.6.38-15-generic #60-Ubuntu SMP Tue May 22 11:28:40 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e021]
    Kernel driver in use: wl

lsusb
Bus 002 Device 005: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 002 Device 004: ID 05dc:a811 Lexar Media, Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:182  Noise level:164
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
michael_mic            12612  8 
arc4                   12529  4 
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
sparse_keymap          13898  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  515134  8 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17387  0 
psmouse                73535  0 
serio_raw              13166  0 
intel_ips              18097  0 
drm_kms_helper         42394  1 i915
pcspkr                 12702  0 
wl                   2568244  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
lib80211               14991  2 lib80211_crypt_tkip,wl
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
video                  19623  1 i915
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
ahci                   25951  3 
tg3                   141750  0 
libahci                26642  1 ahci

---

### Post by jamarsh123 on 2012-05-31
Good to know, thanks.

---

### Post by wildmanne39 on 2012-06-01
Hi, change your wetting for wireless and wired to match the screenshots by clicking on the internet icon in the top right corner of the screen,edit connections,wireless,wired.
Thanks

---

### Post by jamarsh123 on 2012-06-01
Well, that's it.  Your screen shots worked a treat, and I'm up and running at break-neck speed!

Thanks wildmanne39 for the help.
Regards,
jamarsh123

---

### Post by wildmanne39 on 2012-06-01
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Enjoy

---


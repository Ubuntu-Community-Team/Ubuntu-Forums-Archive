---
title: "Internet slow in 11.10"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by tennoshi on 2012-01-09
I've been using Ubuntu for a few months now, but recently got a new laptop and decided to install 11.10 on it and now have it set up to dual-boot with Windows 7. However, my internet speed has gone way down with this new update - it takes a full five minutes to load simple pages, sometimes longer. I know it's not an issue with my laptop, because the internet speeds are fine on the Win7 partition. I had issues originally because my wifi wasn't working at all on Ubuntu, so the problem may lie there. Any suggestions on what might be wrong?

---

### Post by Silent Warrior on 2012-01-09
I see two options: Reverting to an earlier version of Network Manager, or waiting for the next update, to see if either fixes it. It could also be a driver, which is baked into the kernel. (In this case, boot the previous kernel to see whether the problem persists. If the problem doesn't manifest in the old kernel, remove the new kernel and keep using the old one.)
So, um, what did you update, exactly? There's bound to be a log somewhere, but I haven't bothered finding out where, yet... 'Course, if I had, I might just have been using Arch today. I excel at administering things to bits. :)

Note that most of my suggestions require some tinkering in Synaptic that you really don't want to screw up.

---

### Post by tennoshi on 2012-01-09
Sorry, I misspoke earlier - apparently my old laptop also is running 11.10, but doesn't have the internet issues I've been having with the new laptop. How would I revert to an earlier version of Network Manager?

---

### Post by wildmanne39 on 2012-01-09
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tennoshi on 2012-01-12
Here's what I got:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux user 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: AzureWave Device [1a3b:1139]
	Kernel driver in use: rtl8192ce
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Santana20"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:5C:C0:00   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8192ce             141566  0 
rtlwifi               117766  1 rtl8192ce
mac80211              462092  2 rtl8192ce,rtlwifi
wmi                    19256  1 asus_wmi
i915                  566827  3 
psmouse                73882  0 
cfg80211              199587  2 rtlwifi,mac80211
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 

```

---

### Post by wildmanne39 on 2012-01-12
Hi, right now the wireless card you have is having a lot of problems with connection speeds, we have been working on it in another thread I am going to give you a link to it.
[http://ubuntuforums.org/showthread.php?t=1901422](http://ubuntuforums.org/showthread.php?t=1901422)

You will want to refer to the posts to Flash__Gordon and do the things I told him to do including as a last resort install the compat driver, if you have more questions ask here.

It is possible that we will improve the speed but not get it where you want it.
Thanks

---


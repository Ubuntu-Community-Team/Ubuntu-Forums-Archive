---
title: "No wireless"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by yasink on 2013-02-08
I see that this is a common problem but I could not solve my problem using the many posts in multiple forums.

I use lubuntu. My wireless first did not work at all. And I installed this: apt-get install bcmwl-kernel-source 

Now I can see the wireless options, I can even login to my wireless but the internet is too slow (it takes 5 minutes to open a page). My wired internet works fine.

I have a Lonovo s10e netbook.
[B]Here are some info about my system:
[/B]yasin@yasin-Lenovo:~$ sudo iwconfig
[sudo] password for yasin: 
Sorry, try again.
[sudo] password for yasin: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[B]AND THIS
[/B]yasin@yasin-Lenovo:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
	Subsystem: Lenovo IdeaPad S10e [17aa:3a23]
	Kernel driver in use: tg3
--
04:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:04b5]
	Kernel driver in use: wl

[B]AND THIS:
[/B]yasin@yasin-Lenovo:~$ lsmod
Module                  Size  Used by
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
coretemp               13168  0 
joydev                 17161  0 
microcode              18209  0 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  0 
snd_hda_codec         111547  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
psmouse                84843  0 
serio_raw              13031  0 
lib80211_crypt_tkip    17229  0 
snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
wl                   2442848  0 
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_seq_midi           13132  0 
lpc_ich                16925  0 
ums_realtek            17669  0 
uas                    17556  0 
snd_rawmidi            25382  1 snd_seq_midi
rfcomm                 37276  0 
bnep                   17707  2 
parport_pc             31968  0 
bluetooth             183228  10 rfcomm,bnep
ppdev                  12817  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13670  0 
sparse_keymap          13658  1 ideapad_laptop
lib80211               14040  2 lib80211_crypt_tkip,wl
binfmt_misc            17260  1 
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18590  0 
snd                    61991  9 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  457161  3 
soundcore              14599  1 snd
drm_kms_helper         45271  1 i915
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac_hid                13037  0 
drm                   230463  4 i915,drm_kms_helper
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
usb_storage            39350  1 ums_realtek
tg3                   130448  0

---

### Post by mapes12 on 2013-02-08
Looks like it's a know bug. Have a look at the bug report for possible solutions:-

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/989610](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/989610)

---

### Post by wildmanne39 on 2013-02-08
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe b43
```
Thanks

---

### Post by yasink on 2013-02-09
This worked! Thanks...

> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe b43
```
Thanks

---

### Post by wildmanne39 on 2013-02-09
Hi, your welcome! Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by yasink on 2013-02-09
This worked! Thanks...

> **Wild Man said:**
> Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe b43
```
Thanks

---


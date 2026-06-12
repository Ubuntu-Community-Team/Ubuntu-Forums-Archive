---
title: "Ubuntu 12.04 Wireless problem (Slow in ubuntu, Fast in Windows)"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by HanifS on 2013-01-12
Hi Everyone

I have a router connected by wired connection to a Windows PC and and wireless to a Ubuntu laptop. But the Windows internet is much faster than then the Ubuntu internet.

Here's the speedtest result for windows
[IMG]http://speedtest.net/result/2420708647.png[/IMG]



And the Ubuntu 
[IMG]http://speedtest.net/result/2416664591.png[/IMG]


I Know, thats very-very slow :)

Then I tried to use USB tethering from my Cellphone and connect it to the ubuntu laptop, it works.

I found lot of threads about the same problem, and I google searched too but I still cant solve it.

I would Appreciate any help
thanks :)

Specs:
Ubuntu 12.04
Toshiba Satellite C640
1 GB RAM
Intel® Pentium(R) CPU P6100 @ 2.00GHz × 2

```
lspci -nn | grep Network
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
``````
iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"T-35"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: F0:7D:68:7C:17:0E   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:27   Missed beacon:0

``````
lsmod 
Module                  Size  Used by
rndis_wlan             28058  0 
rndis_host             13567  1 rndis_wlan
cdc_ether              13278  1 rndis_host
usbnet                 25210  3 rndis_wlan,rndis_host,cdc_ether
cdc_acm                22277  0 
bnep                   17711  2 
rfcomm                 37289  0 
bluetooth             182881  10 bnep,rfcomm
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_conexant    52554  1 
arc4                   12473  2 
ath9k                 116137  0 
mac80211              465236  1 ath9k
ums_realtek            17920  0 
uas                    17828  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
ath9k_common           13781  1 ath9k
ath9k_hw              375986  2 ath9k,ath9k_common
snd_hda_intel          32765  2 
snd_hda_codec         109562  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
cfg80211              179339  4 rndis_wlan,ath9k,mac80211,ath
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
wmi                    18744  1 toshiba_acpi
psmouse                86520  0 
serio_raw              13027  0 
i915                  419297  3 
compat                 13351  12 rndis_wlan,rndis_host,cdc_ether,usbnet,bnep,rfcomm,bluetooth,ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
mac_hid                13077  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_ips              17822  0 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
mei                    36570  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  1 ums_realtek
``````
sudo lshw -C network
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:90:9d:99
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-35-generic-pae firmware=N/A ip=192.168.0.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:54400000-5440ffff

```

---


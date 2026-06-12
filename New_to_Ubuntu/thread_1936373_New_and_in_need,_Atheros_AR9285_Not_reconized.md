---
title: "New and in need, Atheros AR9285 Not reconized"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by tefl0n on 2012-03-05
Hi,

I'm new to Ubuntu and I'm having some trouble, I just bought a new laptop (Asus X53E) and Installed Ubuntu 10.04.4 LTS on it, and unlike my HP, the wireless card isn't recognized. I know it's a problem that ath9k will fix, but I don't know what I'm doing!! Here are some results from commands you will probably need. (Keep in mind I have a Dlink usb stick in for internet)

```
 telc0n@FYourPC:/$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux FuckYourPC 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:50:08 UTC 2012 x86_64 GNU/Linux

``````
telc0n@FYourPC:/$ lspci -nnk  |  grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)
03:00.0 USB Controller [0c03]: Device [1b21:1042]
    Kernel driver in use: xhci_hcd
--
04:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
 
``````
telc0n@FYourPC:/$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"House"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:02:72:91:35:D6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


``````
telc0n@FyourPC:/$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
telc0n@FYourPC:/$ lsmod
Module                  Size  Used by
arc4                    1473  2 
rt73usb                23600  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11243  1 rt73usb
rt2x00lib              31122  2 rt73usb,rt2x00usb
compat_firmware_class     7842  1 rt2x00lib
snd_hda_codec_realtek   279104  1 
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
binfmt_misc             7960  1 
snd_mixer_oss          16299  1 snd_pcm_oss
ppdev                   6375  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
ath9k                  77491  0 
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common            3071  1 ath9k
mac80211              261570  4 rt2x00usb,rt2x00lib,ath9k,ath9k_common
ath9k_hw              239127  2 ath9k,ath9k_common
uvcvideo               62915  0 
video                  20623  0 
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
ath                    10345  2 ath9k,ath9k_hw
cfg80211              169518  5 rt2x00lib,ath9k,ath9k_common,mac80211,ath
led_class               3764  2 rt2x00lib,ath9k
xhci                   42775  0 
psmouse                65040  0 
vga16fb                12757  1 
videodev               40614  1 uvcvideo
vgastate                9857  1 vga16fb
output                  2503  1 video
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
serio_raw               4918  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  2 

``````
telc0n@FYourPC:/$ sudo iwlist scan
[sudo] password for telc0n: 
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:02:72:91:35:D6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"House"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033c74c4117
                    Extra: Last beacon: 30ms ago
                    IE: Unknown: 0005486F757365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010630412531019200612280002729135D61021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
                    IE: Unknown: 0706555320010B1E


```

Thanks in advance for any help... Will be nice to get it working :P

---

### Post by tefl0n on 2012-03-06
Tried upgrading to 11.10, Now it shows up under the network manager, but it says device is not ready... Can't use it.

Here is the info I got back:

```
telc0n@FYourPC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux FuckYourPC 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

telc0n@FyYourPC:~$ lspci -nnk  |  grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:1186]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c

telc0n@FYourPC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID  
          Mode:Managed  Frequency:2.412 GHz  Access Point
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx inv NabUl2s8 alid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:737   Missed beacon:0

telc0n@FYourPC:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

telc0n@FYourPC:~$ lsmod
Module                  Size  Used by
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
binfmt_misc            17540  1 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  4 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17693  0 
ath9k                 127538  0 
asus_nb_wmi            12517  0 
asus_wmi               20035  1 asus_nb_wmi
mac80211              310872  3 rt2x00usb,rt2x00lib,ath9k
ath9k_common           13839  1 ath9k
psmouse                73882  0 
sparse_keymap          13890  1 asus_wmi
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              312866  2 ath9k,ath9k_common
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
wmi                    19256  1 asus_wmi
ath                    24067  2 ath9k,ath9k_hw
lp                     17799  0 
serio_raw              13166  0 
i915                  566711  3 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
cfg80211              199587  4 rt2x00lib,ath9k,mac80211,ath
i2c_algo_bit           13423  1 i915
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
video                  19412  1 i915
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41643  0 
ahci                   26002  2 
libahci                26861  1 ahci
xhci_hcd               78641  0 

telc0n@FYourPC:~$ sudo iwlist scan
[sudo] password for telc0n: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

wlan1     Scan completed :
          Cell 01 - Address: 00:02:72:91:35:D6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"House"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000034f16c5060
                    Extra: Last beacon: 4ms ago
                    IE: Unknown: 0005486F757365
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010630412531019200612280002729135D61021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401050300000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
                    IE: Unknown: 0708555320010B1E0516

```

Help!

---

### Post by NikTh on 2012-03-06
You must know that your ESSID or your Address are not help us to solve your problem and are not necessary for you to reveal them. Especially to an open forum (open forum = anyone can see your post even he is not register). 

For your problem i suggest to look 2-3 thinks. 

1) Search for a switch. FN+F2 or FN+F1 , check it. 
2) see the results of ```
  cat /var/lib/NetworkManager/NetworkManager.state 
```
if something is false , change it to true (with sudo gedit)
3) ```
sudo gedit /etc/modprobe.d/ath9k.conf
``` and add this line 
**options ath9k nohwcrypt=1** . Save it , and restart your pc. Unplug your usb and try.

---

### Post by tefl0n on 2012-03-06
Thanks for advice, took the info out of previous posts.

Here is what I got

```
telc0n@FYourPC:~$ cat /var/lib/NetworkManager/NetworkManager.state 

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```Attempted to add the like with sudo gedit but got this, and a blank gedit screen:

```
telc0n@FYourPC:~$ sudo gedit /etc/modprobe.d/ath9k.conf
[sudo] password for telc0n: 

(gedit:2785): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.PVXZAW': No such file or directory

(gedit:2785): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2785): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.S8FZAW': No such file or directory

(gedit:2785): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```

Still Showing an Atheros 9485, just device is not ready...

---

### Post by QIII on 2012-03-06
I'm on a train right now, so I'm limited.

I goggled as follows and got quite a few hits

site:ubuntuforums.org atheros 9485

Might be something helpful there.

---

### Post by QIII on 2012-03-06
I'm on a train right now, so I'm limited.

I goggled as follows and got quite a few hits

site:ubuntuforums.org atheros 9485

Might be something helpful there.

---

### Post by NikTh on 2012-03-07
Hi . Try ```
 sudo modprobe ath9k
``` if any errors appear post them here .

And check this Thread . it is similar to your problem.
[]("http://ubuntuforums.org/showthread.php?t=1857808&page=7")_[http://ubuntuforums.org/showthread.php?t=1857808](http://ubuntuforums.org/showthread.php?t=1857808)_

Thanks to [QIII]("http://ubuntuforums.org/member.php?u=628170")

---


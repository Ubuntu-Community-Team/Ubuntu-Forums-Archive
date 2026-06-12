---
title: "Problems with wireless internet connection after updating to 11.10"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by frikardellemand on 2011-11-06
Hi everybody

I'm new to Linux so I'll appreciate lengthy in-depth step by step explanations 

I have recently updated via download to ubuntu 11.10 and I have had problems with connecting with my wireless card.

01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

What happens is that it will locate my network and connect for a while. This may last for everything between 2 min to 4 hours or more. Then it disconnects and goes roaming for another connection. If I try to reconnect to my usual network it prompts me for the password which in then give but to no help. It continues to attempt to reconnect without success. What I can do is restart. That lets me connect again but with the same problem popping up. This is super frustrating and has happened once during the writing of this post. Please help me.

Frikard

---

### Post by wildmanne39 on 2011-11-06
Hi, welcome to the forum!open a terminal by hitting ctrl+alt+t then copy and paste this code into it and hit enter then enter your user password.
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
when the file opens add one line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thank you

---

### Post by frikardellemand on 2011-11-09
Hi again and thanks for your help.

However unfortunately it did not work. The problem persists without change. 

When I used the gedit command it opened an empty document and I added the line given in the last post. However nothing changed.

Any other suggestions?

/F

---

### Post by wildmanne39 on 2011-11-09
Hi, run this command please:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
``` 
Then paste the contents here.
Thank you

---

### Post by frikardellemand on 2011-11-10
Hi and thanks for the help

I have tried your suggested solution. Unfortunately it does not do a difference. Any other suggestions?

Frikard

---

### Post by wildmanne39 on 2011-11-10
Hi, before we go further I want to make sure the command worked properly please post the contents of the file from my previous post.
Thank you

---

### Post by frikardellemand on 2011-11-10
Hi again

The only content of the file ath9k.conf is the line "options ath9k nohwcrypt=1"

When I initially opened the file ath9k.conf it was blank. Then I added the line above.

Frikard

---

### Post by wildmanne39 on 2011-11-10
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
```
nm-tool
```
```
sudo iwlist scan
```
One line at a time.

```
dmesg | egrep 'ath|firm|wpa|etwork|wlan0'
```
Thank you

---

### Post by frikardellemand on 2011-11-11
Okay

Here goes:
[FONT=Courier New]cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux frikardia 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
------------------------------------------------
lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e016]
    Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022f]
    Kernel driver in use: atl1c
--------------------------------------------------
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Elias"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:D1:C3:38:1C   
          Bit Rate=11 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:41  Invalid misc:45   Missed beacon:0
------------------------------------------------------
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
--------------------------------------------------------
lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
i915                  505108  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
serio_raw              12990  0 
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
ath9k                 112711  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              272785  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              293893  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
cfg80211              172392  3 ath9k,mac80211,ath
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
atl1c                  36638  0 
usb_storage            44173  1 
uas                    17699  0 
-----------------------------------------------------------------
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Elias] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        C4:17:FE:AF:BA:4C

  Capabilities:
    Speed:           11 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TURBONETT_EC34F5:Infra, 64:68:0C:EC:34:F6, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WEP
    *Elias:          Infra, 00:15:D1:C3:38:1C, Freq 2462 MHz, Rate 54 Mb/s, Strength 41 WPA

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             200.12.232.4
    DNS:             200.12.229.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        70:5A:B6:28:B2:50

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
-----------------------------------------------------------------
sudo iwlist scan
[sudo] password for freakart: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:D1:C3:38:1C
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Elias"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b696e1a06d
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0005456C696173
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010210470010E7FE1B918CD5031098DD0015D1C3381C1021000541727269731023000941727269735F35346710240007575053303030311042000E30303031303030303034453034341054000800060050F20400011011002041727269735F3534675F57505300000000000000000000000000000000000000100800020084
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
----------------------------------------------------------------------
dmesg | egrep 'ath|firm|wpa|etwork|wlan0'
[   20.193138] type=1400 audit(1321063463.308:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=446 comm="apparmor_parser"
[   20.264726] ath9k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.264754] ath9k 0000:01:00.0: setting latency timer to 64
[   20.547111] ath: EEPROM regdomain: 0x65
[   20.547120] ath: EEPROM indicates we should expect a direct regpair map
[   20.547131] ath: Country alpha2 being used: 00
[   20.547137] ath: Regpair used: 0x65
[   20.679863] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.685085] Registered led device: ath9k-phy0
[   57.467572] type=1400 audit(1321063500.580:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=785 comm="apparmor_parser"
[   57.596051] type=1400 audit(1321063500.708:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=809 comm="apparmor_parser"
[   57.619633] type=1400 audit(1321063500.732:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=809 comm="apparmor_parser"
[   84.917479] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  107.904894] wlan0: authenticate with 00:15:d1:c3:38:1c (try 1)
[  107.908709] wlan0: authenticated
[  107.953483] wlan0: associate with 00:15:d1:c3:38:1c (try 1)
[  107.956999] wlan0: RX AssocResp from 00:15:d1:c3:38:1c (capab=0x411 status=0 aid=2)
[  107.957012] wlan0: associated
[  107.957974] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  118.912138] wlan0: no IPv6 routers present
[/FONT]-----------------------------------------------------------------------------------

That was it. I hope that gives you something.

Frikard

---

### Post by wildmanne39 on 2011-11-12
Hi, a few suggestions.

1. You should be able to enter router setup by typing 192.168.0.1 into your browser while connect to it with a hard wire.

Set your encryption to wpa2 in your router and network manager and not just wpa or wpa/wpa2 if you can it will work better.

2. Your signal strength is weak it always is with the driver used in linux see if you can get closer to your router.

3. While you are changing encryption settings in the router make sure your wireless is turned to 100 percent.

4. In network manager set ipv6 for your wireless connection to ignore.

After you have changed these settings if you still have problems please post the results of:
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlan -e etwork -e wpa | tail -n55
```
with your wired connection disconnected.

It looks like it should connect, the output mostly was good.
Thank you

---


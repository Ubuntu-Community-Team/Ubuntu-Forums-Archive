---
title: "Can see and connect to network but not resolve any pages"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by gken on 2012-06-17
Hi all,

I'm installing Ubuntu after a *long* absence and having a bit of a struggle with my network connection

I can see and connect to my wifi router.  I was able to navigate to websites successfully for a while, until I tried to go online over ethernet connection instead as I was going to install win7 in virtualbox as you need a wired connection for that.  At some stage in the (failed) win7 install, I've buggered up my wifi *and* ethernet connections and I don't know what to do now...

rfkill after the install was telling me that the wifi was hard and soft blocked, ethernet was just soft blocked.  managed to get everything unblocked now, but still no luck - ping [www.google.com](www.google.com) just times out...

IPv6 is set to ignored just in case.  iwconfig returns 

lo           no wireless extensions

wlan0     IEEE 802.11abgn ESSID:"O2wireless90E451"
              Mode:Managed Frequency:2.412 GHz Access Point: 00:26:44:90:E4:51
              Bit Rate=65 Mb/s Tx-Power=15 dBm
              Retry long limit:7 RTS thr:off Fragment thr:off
              Power Management:off
              Link Quality 63/70 Signal level=-47 dBM
              Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
              Tx excessive retries:24 Invalid misc:42 Missed beacon:0

eth0       no wireless extensions.

Any ideas????  Thanks very much in advance!

ETA: and I'm accessing the internet via the same router on my macbook so there's no issue with the router...also to clarify that both the wired and wireless connections aren't reaching the web

---

### Post by wildmanne39 on 2012-06-17
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
rfkill list all
lsmod
nm-tool
sudo iwlist scan
```
by clicking on new reply and click # then paste the information between the brackets.

Also you should be able to use a wireless connection with virtualbox it will just show in the guest as a wired connection though.
Thank you

---

### Post by gken on 2012-06-17
thanks for the super fast reply!

I know you can use wifi in virtual box, but I was under the impression that for a first install of windows you have to go to a wired connection?  Is that not true?

Anyway, here's the output...



```
georgie@GKEN-GB:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux GKEN-GB 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
georgie@GKEN-GB:~$ lspci -nnk | grep -iA2 net 
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
        Subsystem: Dell Device [1028:040a]
        Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
        Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
        Kernel driver in use: iwlwifi
georgie@GKEN-GB:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 1058:071a Western Digital Technologies, Inc. My Passport 1TB
Bus 002 Device 004: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 002 Device 005: ID 0951:1653 Kingston Technology 
Bus 002 Device 006: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 007: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
georgie@GKEN-GB:~$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
georgie@GKEN-GB:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
iptable_filter         12810  0 
ip_tables              27473  1 iptable_filter
x_tables               29846  2 iptable_filter,ip_tables
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  12 
binfmt_misc            17540  1 
joydev                 17693  0 
usbhid                 47199  0 
arc4                   12529  2 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
hid                    99559  1 usbhid
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
ses                    17417  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
wmi                    19256  1 dell_wmi
parport_pc             32866  0 
snd_timer              29990  2 snd_pcm,snd_seq
enclosure              15269  1 ses
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               332672  0 
i915                  468745  8 
drm_kms_helper         46978  1 i915
mac80211              506816  1 iwlwifi
drm                   242038  4 i915,drm_kms_helper
btusb                  18288  2 
soundcore              15091  1 snd
psmouse                87692  0 
cfg80211              205544  2 iwlwifi,mac80211
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
bluetooth             180104  23 bnep,rfcomm,btusb
serio_raw              13211  0 
intel_ips              18089  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            49198  2 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
e1000e                156693  0 
georgie@GKEN-GB:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [O2wireless90E451] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        58:94:6B:CC:B4:CC

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    WINDOWS-J6NHVIP_Network: Infra, 14:D6:4D:79:51:BA, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    O2wireless91275B:Infra, 00:26:44:91:27:5B, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    SKY0EB8C:        Infra, 90:01:3B:20:EB:8D, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    BTHub3-6MG3:     Infra, 80:B6:86:53:34:AB, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    virginmedia1594313: Infra, C4:3D:C7:42:94:78, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    virginmedia7891752: Infra, A0:21:B7:56:DC:44, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    virginmedia2559746: Infra, A0:21:B7:CC:EE:86, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    BTFON:           Infra, 5A:B6:86:53:34:AD, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    BTOpenzone-H:    Infra, 5A:B6:86:53:34:AC, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    *O2wireless90E451: Infra, 00:26:44:90:E4:51, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    ChrisNetwork:    Infra, 00:24:B2:51:8B:BC, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA2
    SKY31499:        Infra, C8:CD:72:B3:14:9A, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Philips Two:     Infra, 00:1C:DF:E3:B9:D5, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    print server 3C6A94: Ad-Hoc, 02:5E:4A:95:0E:A3, Freq 2462 MHz, Rate 11 Mb/s, Strength 20

  IPv4 Settings:
    Address:         192.168.1.141
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        5C:26:0A:39:F3:57

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


georgie@GKEN-GB:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:90:E4:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"O2wireless90E451"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001bacd7ba18d
                    Extra: Last beacon: 120ms ago
                    IE: Unknown: 00104F32776972656C657373393045343531
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD09001018020300050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001300000000000000000000000000000000000000
          Cell 02 - Address: C4:3D:C7:42:94:78
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1594313"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000421bd38fd71
                    Extra: Last beacon: 4240ms ago
                    IE: Unknown: 001276697267696E6D6564696131353934333133
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 03 - Address: 90:01:3B:20:EB:8D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"SKY0EB8C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000651d928789e
                    Extra: Last beacon: 4204ms ago
                    IE: Unknown: 0008534B593045423843
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001500000000000000000000000000000000000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B000103104700103F38BBD5BC8CAD5BD937BCD5555BD4FB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:26:44:91:27:5B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"O2wireless91275B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a137129c68
                    Extra: Last beacon: 3968ms ago
                    IE: Unknown: 00104F32776972656C657373393132373542
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD890050F204104A00011010440001021041000100103B000103104700105210036A1D7657479DDEFD509E0934A31021000754484F4D534F4E1023000A54686F6D736F6E205447102400073538376E207632104200093130343144483459411054000800060050F20400011011001154686F6D736F6E2054473538376E207632100800020084103C000101
                    IE: Unknown: DD09001018020200050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
          Cell 05 - Address: A0:21:B7:56:DC:44
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"virginmedia7891752"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000612661e70
                    Extra: Last beacon: 4004ms ago
                    IE: Unknown: 001276697267696E6D6564696137383931373532
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343830100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406081500000000000000000000000000000000000000
          Cell 06 - Address: 80:B6:86:53:34:AB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-6MG3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022e7844a95
                    Extra: Last beacon: 3864ms ago
                    IE: Unknown: 000B4254487562332D364D4733
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: 5A:B6:86:53:34:AC
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022e78665fa
                    Extra: Last beacon: 3724ms ago
                    IE: Unknown: 000C42544F70656E7A6F6E652D48
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 5A:B6:86:53:34:AD
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"BTFON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022e7875fe0
                    Extra: Last beacon: 3660ms ago
                    IE: Unknown: 00054254464F4E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:1C:DF:E3:B9:D5
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Philips Two"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010a5dc6d16d
                    Extra: Last beacon: 3892ms ago
                    IE: Unknown: 000B5068696C6970732054776F
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010A
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 050400010080
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160A000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340A000700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 10 - Address: A0:21:B7:CC:EE:86
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"virginmedia2559746"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c86128194
                    Extra: Last beacon: 3744ms ago
                    IE: Unknown: 001276697267696E6D6564696132353539373436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F20400011011000743473331303144100800020088
                    IE: Unknown: DD090010180205F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000

eth0      Interface doesn't support scanning.

```

---

### Post by wildmanne39 on 2012-06-17
Hi, I do not see why you would need to be hard wired to install windows please remember that the guest uses the internet of the host, please try:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlwifi
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
do not reboot if this helps we will need to make it permanent.

Did you change the encryption in your router?

it usually works best if you set it to wpa2 only

---

### Post by gken on 2012-06-17
hmmm well I don't know the rationale, but it is in the instruction packet I was given...either way it's stuffed now...

tried your suggestion and no progress unfortunately - I didn't modify anything for encryption on the router

---

### Post by wildmanne39 on 2012-06-17
Hi, please post the output of:
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork -e radio -e switch | tail -n75
```
Thanks

---

### Post by gken on 2012-06-17
Ok here's the output...thanks for looking at this again :)

```
georgie@GKEN-GB:/media/MYLINUXLIVE$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork -e radio -e switch | tail -n75
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.931677] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.947577] iwlwifi 0000:02:00.0: device EEPROM VER=0x43a, CALIB=0x6
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.947582] iwlwifi 0000:02:00.0: Device SKU: 0X1f0
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.947623] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.956655] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.957389] ieee80211 phy1: Selected rate control algorithm 'iwl-agn-rs'
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> found WiFi radio killswitch rfkill4 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/ieee80211/phy1/rfkill4) (driver (unknown))
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.977714] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Jun 17 21:30:31 GKEN-GB kernel: [ 3267.984650] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): using nl80211 for WiFi device control
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 5)
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): now managed
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): bringing up device.
Jun 17 21:30:31 GKEN-GB kernel: [ 3268.215825] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
Jun 17 21:30:31 GKEN-GB kernel: [ 3268.222728] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): preparing device.
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 17 21:30:31 GKEN-GB NetworkManager[964]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 17 21:30:31 GKEN-GB NetworkManager[964]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 17 21:30:31 GKEN-GB kernel: [ 3268.328398] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 17 21:30:31 GKEN-GB kernel: [ 3268.328694] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: starting -> ready
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jun 17 21:30:31 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) starting connection 'O2wireless90E451'
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0/wireless): connection 'O2wireless90E451' has security, and secrets exist.  No new secrets needed.
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 17 21:30:36 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 17 21:30:39 GKEN-GB wpa_supplicant[2322]: Trying to authenticate with 00:26:44:90:e4:51 (SSID='O2wireless90E451' freq=2412 MHz)
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.975892] wlan0: authenticate with 00:26:44:90:e4:51 (try 1)
Jun 17 21:30:39 GKEN-GB wpa_supplicant[2322]: Trying to associate with 00:26:44:90:e4:51 (SSID='O2wireless90E451' freq=2412 MHz)
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.981146] wlan0: authenticated
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.981435] wlan0: associate with 00:26:44:90:e4:51 (try 1)
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.984256] wlan0: RX AssocResp from 00:26:44:90:e4:51 (capab=0x411 status=0 aid=6)
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.984261] wlan0: associated
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 17 21:30:39 GKEN-GB wpa_supplicant[2322]: Associated with 00:26:44:90:e4:51
Jun 17 21:30:39 GKEN-GB kernel: [ 3275.987840] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 17 21:30:39 GKEN-GB wpa_supplicant[2322]: WPA: Key negotiation completed with 00:26:44:90:e4:51 [PTK=CCMP GTK=TKIP]
Jun 17 21:30:39 GKEN-GB wpa_supplicant[2322]: CTRL-EVENT-CONNECTED - Connection to 00:26:44:90:e4:51 completed (auth) [id=0 id_str=]
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'O2wireless90E451'.
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 17 21:30:39 GKEN-GB NetworkManager[964]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 17 21:30:39 GKEN-GB dhclient: Listening on LPF/wlan0/58:94:6b:cc:b4:cc
Jun 17 21:30:39 GKEN-GB dhclient: Sending on   LPF/wlan0/58:94:6b:cc:b4:cc
Jun 17 21:30:39 GKEN-GB dhclient: DHCPREQUEST of 192.168.1.141 on wlan0 to 255.255.255.255 port 67
Jun 17 21:30:42 GKEN-GB dhclient: DHCPREQUEST of 192.168.1.141 on wlan0 to 255.255.255.255 port 67
Jun 17 21:30:42 GKEN-GB NetworkManager[964]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 17 21:30:42 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 17 21:30:42 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 17 21:30:43 GKEN-GB NetworkManager[964]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 17 21:30:43 GKEN-GB NetworkManager[964]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 17 21:30:43 GKEN-GB NetworkManager[964]: <info> Policy set 'O2wireless90E451' (wlan0) as default for IPv4 routing and DNS.
Jun 17 21:30:43 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) successful, device activated.
Jun 17 21:30:43 GKEN-GB NetworkManager[964]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 17 21:30:49 GKEN-GB kernel: [ 3286.135300] wlan0: no IPv6 routers present
Jun 17 21:31:31 GKEN-GB wpa_supplicant[2322]: WPA: Group rekeying completed with 00:26:44:90:e4:51 [GTK=TKIP]
Jun 17 21:41:31 GKEN-GB wpa_supplicant[2322]: WPA: Group rekeying completed with 00:26:44:90:e4:51 [GTK=TKIP]


```

---

### Post by wildmanne39 on 2012-06-17
Hi, change the encryption to just wpa2 AES if possible before we go any further and reset your router and  then while it is resetting reboot your computer.

You will also need to make sure in network manager that security is set to wpa/wpa2.

Then we will go from there I realize everything else is still connecting to the router but sometimes with ubuntu a reset and changing those settings are needed.
Thanks

---

### Post by gken on 2012-06-17
Sorry if this is really silly - but do you mean update the encryption settings directly on the router, or in the network settings?  When I go to edit connections the choices I have are None, WEP 40/128-bit key, WEP 128 bit passphrase, LEAP, Dynamic WEP, WPA & WPA2 (Personal) and WPA & WPA2 (Enterprise)...am I looking at this the wrong way?

ETA - if it is an encryption issue, why would the wired connection also be not working?

---

### Post by wildmanne39 on 2012-06-17
Hi, in network manager change the setting to wpa/wpa2.

In the router change it to just wpa2 AES if you have that option.
Thanks

---

### Post by gken on 2012-06-17
Ok that's what I thought - in Network Manager that has been done (WPA & WPA2 Personal), but there is no option to configure encryption on my router (Thomson O2 Wireless Box IV) as far as I can see - seems to be pretty locked down by O2...

---

### Post by wildmanne39 on 2012-06-17
Hi, okay try this then:
```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi swcrypto=1
```
do not reboot and if it works we will need to make it permanent.
Thanks

---

### Post by gken on 2012-06-17
same story unfortunately after that change :(

it's bedtime here - thanks for all your really quick responses - I will have to get back to it in the morning...g'night

---

### Post by wildmanne39 on 2012-06-17
Hi, your welcome! I will be here.

---


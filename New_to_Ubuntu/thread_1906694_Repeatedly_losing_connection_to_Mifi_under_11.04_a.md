---
title: "Repeatedly losing connection to Mifi under 11.04 and 11.10. Works on 10.10"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by geekyg1023 on 2012-01-09
Hi
I have an old Dell XPS with a D-Link DWL-G520 wireless card which I used to use with our Verizon MiFi.

I upgraded to 11.04 by installing on a new disk and just replacing the drive. The wireless connection appears to work but then disconnects. It picks up again and then disconnects....

I replaced the 11.04 drive with the 10.10 drive and all is good. I waited for 11.10 thinking it may have been a bug in 11.04 but it does the same. 

I have tried to search the forums and google. Any help would be appreciated.

g

---

### Post by wildmanne39 on 2012-01-09
Hi, please post the output of:
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

### Post by geekyg1023 on 2012-01-13
11.10 -- Makes connection and then disconnects


geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux geekyg-Dimension-XPS 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Dimension XPS Gen 4 [1028:0176]
	Kernel driver in use: tg3
--
04:01.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
	Subsystem: D-Link System Inc AirPlus DWL-G520 Wireless PCI Adapter (rev. B) [1186:3a13]
	Kernel driver in use: ath5k

geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 001 Device 004: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 005: ID 0e39:1700 Smart Modular Technologies, Inc. 

geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
lm63                   13998  0 
snd_emu10k1_synth      12963  0 
snd_emux_synth         33455  1 snd_emu10k1_synth
snd_seq_virmidi        13309  1 snd_emux_synth
snd_seq_midi_emul      13526  1 snd_emux_synth
joydev                 17393  0 
snd_emu10k1           133258  3 snd_emu10k1_synth
snd_ac97_codec        106082  1 snd_emu10k1
ac97_bus               12642  1 snd_ac97_codec
ppdev                  12849  0 
snd_pcm                80468  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc         14115  2 snd_emu10k1,snd_pcm
snd_util_mem           13786  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13276  2 snd_emux_synth,snd_emu10k1
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25241  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
dcdbas                 14098  0 
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51567  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
radeon                925020  2 
ath5k                 145100  0 
snd_timer              28932  3 snd_emu10k1,snd_pcm,snd_seq
ath                    19387  1 ath5k
snd_seq_device         14172  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              272785  1 ath5k
hid_microsoft          12728  0 
snd                    55902  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
ttm                    65224  1 radeon
soundcore              12600  1 snd
drm_kms_helper         32889  1 radeon
cfg80211              172392  3 ath5k,ath,mac80211
serio_raw              12990  0 
drm                   192226  4 radeon,ttm,drm_kms_helper
parport_pc             32114  1 
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  2 hid_microsoft,usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 
tg3                   132972  0 
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY

---

### Post by geekyg1023 on 2012-01-13
I would have just made one post, but the page complained I had too many images. As I did not even have any images, I split it. 


10.10 WORKS!!!


geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux geekyg-Dimension-XPS 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell Dimension XPS Gen 4 [1028:0176]
	Kernel driver in use: tg3
--
04:01.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
	Subsystem: D-Link System Inc AirPlus DWL-G520 Wireless PCI Adapter (rev. B) [1186:3a13]
	Kernel driver in use: ath5k
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 004: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 0e39:1700 Smart Modular Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Verizon Secure"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
geekyg@geekyg-Dimension-XPS:/media/USB MEMORY$ lsmod
Module                  Size  Used by
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat
binfmt_misc             6599  1 
lm63                    5972  0 
snd_emu10k1_synth       5136  0 
snd_emux_synth         29012  1 snd_emu10k1_synth
snd_seq_virmidi         4193  1 snd_emux_synth
snd_seq_midi_emul       5547  1 snd_emux_synth
arc4                    1165  2 
snd_emu10k1           131818  3 snd_emu10k1_synth
snd_ac97_codec         99227  1 snd_emu10k1
ac97_bus                1014  1 snd_ac97_codec
radeon                829447  3 
snd_pcm                71475  2 snd_emu10k1,snd_ac97_codec
snd_page_alloc          7120  2 snd_emu10k1,snd_pcm
snd_util_mem            3118  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5040  2 snd_emux_synth,snd_emu10k1
snd_seq_midi            4588  0 
snd_rawmidi            17783  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
ath5k                 130083  0 
ttm                    56633  1 radeon
snd_seq_midi_event      6047  2 snd_seq_virmidi,snd_seq_midi
mac80211              231959  1 ath5k
snd_seq                47174  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 radeon
joydev                  8767  0 
hid_microsoft           2691  0 
snd_timer              19067  3 snd_emu10k1,snd_pcm,snd_seq
ath                     8153  1 ath5k
snd_seq_device          5744  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
usbhid                 36882  0 
cfg80211              144694  3 ath5k,mac80211,ath
ppdev                   5556  0 
hid                    67742  2 hid_microsoft,usbhid
snd                    49038  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm,snd_hwdep,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             26058  1 
dell_wmi_aio            1733  0 
dcdbas                  5402  0 
soundcore                880  1 snd
led_class               2633  1 ath5k
psmouse                59033  0 
agpgart                32011  2 ttm,drm
i2c_algo_bit            5168  1 radeon
serio_raw               4022  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
firewire_ohci          21234  0 
usb_storage            40172  1 
firewire_core          46643  1 firewire_ohci
floppy                 54311  0 
crc_itu_t               1383  1 firewire_core
tg3                   123310  0

---

### Post by wildmanne39 on 2012-01-14
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
lsmod | grep ath
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you
Thanks

---

### Post by geekyg1023 on 2012-01-20
Hi
Thanks for the help. Hope I was not too long in replying.

=================10.10
@geekg-Dimension-XPS:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:11:11:27:D3:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto Verizon Secure] ---------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:xx:xx:xx:33:7C

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Verizon  Secure: Infra, 38:16:D1:95:D6:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


geekg@geekg-Dimension-XPS:~$ sudo iwlist scan
[sudo] password for geekg: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 38:16:D1:95:D6:4D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Verizon  Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000650b3188
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 001C566572697A6F6E205343482D4C433131206436346420536563757265
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 072455532001010B0201170301170401170501170601170701170801170901170A01160B010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD920050F204104A0001101044000102103B000103104700105175616C636F6D6D5F575053520000001021000C5175616C636F6D6D20496E63102300105750535265676973747261723132333410240009343432332D343433331042000D51434F4D2D575053522D3132331054000800060050F204000110110013534F465441502D57505352656769737472617210080002008C

geekg@geekg-Dimension-XPS:~$ lsmod | grep ath
ath5k                 130083  0 
mac80211              231959  1 ath5k
ath                     8153  1 ath5k
cfg80211              144694  3 ath5k,mac80211,ath
led_class               2633  1 ath5k
geekg@geekg-Dimension-XPS:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0/wireless): access point 'Auto Verizon  Secure' has security, but secrets are required.
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0/wireless): connection 'Auto Verizon  Secure' has security, and secrets exist.  No new secrets needed.
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 20 22:08:46 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jan 20 22:08:47 geekg-Dimension-XPS wpa_supplicant[806]: Trying to associate with xx:xx:xx:xx:d6:4d (SSID='Verizon  Secure' freq=2437 MHz)
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jan 20 22:08:47 geekg-Dimension-XPS kernel: [  156.853277] wlan0: authenticate with xx:xx:xx:xx:d6:4d (try 1)
Jan 20 22:08:47 geekg-Dimension-XPS kernel: [  156.855250] wlan0: authenticated
Jan 20 22:08:47 geekg-Dimension-XPS kernel: [  156.855267] wlan0: associate with xx:xx:xx:xx:d6:4d (try 1)
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  associating -> associated
Jan 20 22:08:47 geekg-Dimension-XPS wpa_supplicant[806]: Associated with xx:xx:xx:xx:d6:4d
Jan 20 22:08:47 geekg-Dimension-XPS kernel: [  156.869603] wlan0: RX AssocResp from xx:xx:xx:xx:d6:4d (capab=0x431 status=0 aid=4)
Jan 20 22:08:47 geekg-Dimension-XPS kernel: [  156.869607] wlan0: associated
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Jan 20 22:08:47 geekg-Dimension-XPS wpa_supplicant[806]: WPA: Key negotiation completed with xx:xx:xx:xx:d6:4d [PTK=TKIP GTK=TKIP]
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Verizon  Secure'.
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 20 22:08:47 geekg-Dimension-XPS wpa_supplicant[806]: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:d6:4d completed (reauth) [id=0 id_str=]
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 20 22:08:47 geekg-Dimension-XPS dhclient: Listening on LPF/wlan0/00:13:46:75:33:7c
Jan 20 22:08:47 geekg-Dimension-XPS dhclient: Sending on   LPF/wlan0/00:13:46:75:33:7c
Jan 20 22:08:47 geekg-Dimension-XPS dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 20 22:08:47 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 22:08:47 geekg-Dimension-XPS avahi-daemon[758]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Jan 20 22:08:47 geekg-Dimension-XPS avahi-daemon[758]: New relevant interface wlan0.IPv4 for mDNS.
Jan 20 22:08:47 geekg-Dimension-XPS avahi-daemon[758]: Registering new address record for 192.168.1.3 on wlan0.IPv4.
Jan 20 22:08:48 geekg-Dimension-XPS NetworkManager[755]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Jan 20 22:08:48 geekg-Dimension-XPS NetworkManager[755]: <info> Policy set 'Auto Verizon  Secure' (wlan0) as default for IPv4 routing and DNS.
Jan 20 22:08:48 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) successful, device activated.
Jan 20 22:08:48 geekg-Dimension-XPS NetworkManager[755]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
geekg@geekg-Dimension-XPS:~$ 



===================11

geekg@geekg-Dimension-XPS:~$ nm-tool

NetworkManager Tool

State: connecting

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:11:11:27:D3:C0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Verizon  Secure] --------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:13:46:75:33:7C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Verizon  Secure: Infra, 38:xx:xx:xx:xx:4D, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA


geekg@geekg-Dimension-XPS:~$ sudo iwlist scan
[sudo] password for geekg: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:4D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Verizon  Secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000f9a1279
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 001C566572697A6F6E205343482D4C433131206436346420536563757265
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 072455532001010B0201170301170401170501170601170701170801170901170A01160B010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101810003A4000027A4000042435E0062322F00
                    IE: Unknown: DD920050F204104A0001101044000102103B000103104700105175616C636F6D6D5F575053520000001021000C5175616C636F6D6D20496E63102300105750535265676973747261723132333410240009343432332D343433331042000D51434F4D2D575053522D3132331054000800060050F204000110110013534F465441502D57505352656769737472617210080002008C

geekg@geekg-Dimension-XPS:~$ lsmod | grep ath
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              272785  1 ath5k
cfg80211              172392  3 ath5k,ath,mac80211
geekg@geekg-Dimension-XPS:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
Jan 20 22:21:11 geekg-Dimension-XPS wpa_supplicant[965]: WPA: Countermeasures - dropped EAPOL packet
Jan 20 22:21:11 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: associating -> associated
Jan 20 22:21:12 geekg-Dimension-XPS wpa_supplicant[965]: WPA: Countermeasures - dropped EAPOL packet
Jan 20 22:21:14  wpa_supplicant[965]: last message repeated 2 times
Jan 20 22:21:14 geekg-Dimension-XPS wpa_supplicant[965]: WPA: TKIP countermeasures stopped
Jan 20 22:21:15 geekg-Dimension-XPS kernel: [  329.231638] wlan0: deauthenticated from xx:xx:xx:xx:d6:4d (Reason: 7)
Jan 20 22:21:15 geekg-Dimension-XPS wpa_supplicant[965]: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:d6:4d reason=7
Jan 20 22:21:15 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: associated -> disconnected
Jan 20 22:21:15 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: Trying to authenticate with xx:xx:xx:xx:d6:4d (SSID='Verizon  Secure' freq=2437 MHz)
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: Trying to associate with xx:xx:xx:xx:d6:4d (SSID='Verizon  Secure' freq=2437 MHz)
Jan 20 22:21:16 geekg-Dimension-XPS kernel: [  330.184367] wlan0: authenticate with xx:xx:xx:xx:d6:4d (try 1)
Jan 20 22:21:16 geekg-Dimension-XPS kernel: [  330.186860] wlan0: authenticated
Jan 20 22:21:16 geekg-Dimension-XPS kernel: [  330.187206] wlan0: associate with xx:xx:xx:xx:d6:4d (try 1)
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: Associated with xx:xx:xx:xx:d6:4d
Jan 20 22:21:16 geekg-Dimension-XPS kernel: [  330.201153] wlan0: RX ReassocResp from xx:xx:xx:xx:d6:4d (capab=0x431 status=0 aid=2)
Jan 20 22:21:16 geekg-Dimension-XPS kernel: [  330.201157] wlan0: associated
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: WPA: Key negotiation completed with xx:xx:xx:xx:d6:4d [PTK=TKIP GTK=TKIP]
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:d6:4d completed (reauth) [id=0 id_str=]
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Verizon  Secure'.
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: Withdrawing address record for fe80::213:46ff:fe75:337c on wlan0.
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::213:46ff:fe75:337c.
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 20 22:21:16 geekg-Dimension-XPS dhclient: Listening on LPF/wlan0/00:13:46:75:33:7c
Jan 20 22:21:16 geekg-Dimension-XPS dhclient: Sending on   LPF/wlan0/00:13:46:75:33:7c
Jan 20 22:21:16 geekg-Dimension-XPS dhclient: DHCPREQUEST of 192.168.1.3 on wlan0 to 255.255.255.255 port 67
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 20 22:21:16 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: New relevant interface wlan0.IPv4 for mDNS.
Jan 20 22:21:16 geekg-Dimension-XPS avahi-daemon[532]: Registering new address record for 192.168.1.3 on wlan0.IPv4.
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: Michael MIC failure detected
Jan 20 22:21:16 geekg-Dimension-XPS wpa_supplicant[965]: WPA: Sending EAPOL-Key Request (error=1 pairwise=0 ptk_set=1 len=99)
Jan 20 22:21:17 geekg-Dimension-XPS avahi-daemon[532]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::213:46ff:fe75:337c.
Jan 20 22:21:17 geekg-Dimension-XPS avahi-daemon[532]: New relevant interface wlan0.IPv6 for mDNS.
Jan 20 22:21:17 geekg-Dimension-XPS avahi-daemon[532]: Registering new address record for fe80::213:46ff:fe75:337c on wlan0.*.
Jan 20 22:21:17 geekg-Dimension-XPS NetworkManager[535]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 20 22:21:17 geekg-Dimension-XPS NetworkManager[535]: <info> Policy set 'Verizon  Secure' (wlan0) as default for IPv4 routing and DNS.
Jan 20 22:21:17 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) successful, device activated.
Jan 20 22:21:17 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 20 22:21:17 geekg-Dimension-XPS NetworkManager[535]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
geekg@geekg-Dimension-XPS:~$

---

### Post by wildmanne39 on 2012-01-21
Hi, first let's try this:
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

Your signal strength is very weak I do not believe that you can connect with a signal that weak in ubuntu, how far are you from the access point and is there any walls or doors closed in between the access point and your computer.

The above command may help a little to improve signal but it is for encryption.

Also wpa2 AES encryption works better then wpa, so I suggest you change it in your router.

When you post output please only post output from the one you can not connect too and wrap up the output with code tags by clicking on #, I explained how to do it in my first post.
Thanks

---

### Post by geekyg1023 on 2012-01-29
Hi
I want to thank for your help. I realize you are volunteering and I appreciate it
I would have followed your instructions for the new reply, but the page is a wee bit overwhelming. I saw the quick reply off the right and below, so I used it.
I had posted the results for 10.10 and 11.x because the wireless was working on 10 but stopped at the upgrade. I was even hoping I would spot something that was different.
Thanks for the heads up on the WPA. I was just using the Samsung as it came from the factory and had never bothered to check the settings. When I did, I saw an upgrade was available for the Samsung that I will try.

---

### Post by wildmanne39 on 2012-02-03
Hi, please let us know if your wireless is working now.
Thanks

---

### Post by yuki2012 on 2012-02-04
Does it work?

---

### Post by Guilden_NL on 2012-02-04
Do you have wicd wireless manager installed?  I have used it for years and sometime around Meerkat or Natty it started conflicting with Network Manager resulting in the same exact behavior you describe.

I prefer wicd over Network Manager, so got rid of Network Manager.

If you do have wicd installed and want to keep it instead of Network Manager, here's the quick fix.

Open a terminal and type:
$ sudo apt-get remove network-manager

$ sudo /etc/init.d/wicd restart

---


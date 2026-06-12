---
title: "Another WiFI not working: Lenovo x220 running 11.10"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by josiahw216 on 2011-12-20
Hello, I installed 11.10 on my computer and the wireless is not working. I'm using a RTL8188CE card. I've done the following things:

1. Updated the drivers based on the official drivers from the website.
2. Found out that build-essential needed to be installed.
3. Couldn't install that because I needed dpkg and g++.
4. Tried to install both but they didn't work for various reasons.

The wireless still searches but in vain. I can connect with Windows easily.

I cannot connect to the internet whatsoever, not even with an ethernet cable.

Here is the result for:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan 
``````
josiah@josiah:~$ sudo rmmod -f wmi
[sudo] password for josiah: 
josiah@josiah:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux josiah 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux
josiah@josiah:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]
    Kernel driver in use: rtl8192ce
josiah@josiah:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
josiah@josiah:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
josiah@josiah:~$ lsmod
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
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
binfmt_misc            17292  1 
joydev                 17393  0 
arc4                   12473  2 
rtl8192ce             127398  0 
thinkpad_acpi          73942  0 
snd_hda_intel          28358  2 
nvram                  14029  1 thinkpad_acpi
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
tpm_tis                14002  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
rtlwifi               102641  1 rtl8192ce
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,thinkpad_acpi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67271  0 
i915                  509290  3 
mac80211              393459  2 rtl8192ce,rtlwifi
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36466  0 
videodev               85626  1 uvcvideo
cfg80211              172392  2 rtlwifi,mac80211
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  1 
uas                    17699  0 
ahci                   21634  2 
libahci                25761  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
e1000e                139814  0 
josiah@josiah:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        F0:DE:F1:B1:EA:21

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        60:D8:19:C5:4D:52

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    2WIRE321:        Infra, 64:0F:29:10:5C:A9, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    18:              Infra, 00:1D:7E:F9:26:A6, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA
    linksys:         Infra, 00:1D:7E:4B:97:F3, Freq 2437 MHz, Rate 54 Mb/s, Strength 70
    2WIRE962:        Infra, 00:26:50:E4:8F:C9, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    CamToy:          Infra, E0:91:F5:E4:5F:0A, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP
    2WIRE412:        Infra, 28:16:2E:0D:2F:11, Freq 2452 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    jeffw:           Infra, 00:24:01:72:2D:53, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA
    2WIRE999:        Infra, 34:EF:44:C3:EF:61, Freq 2422 MHz, Rate 54 Mb/s, Strength 75 WPA
    Selam1:          Infra, C0:3F:0E:E0:D5:96, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA
    2WIRE657:        Infra, 64:0F:28:42:AD:C9, Freq 2457 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    2WIRE352:        Infra, 98:2C:BE:29:78:B9, Freq 2457 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    2WIRE173:        Infra, 28:16:2E:22:BC:29, Freq 2422 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    2WIRE943:        Infra, 64:0F:29:03:EE:19, Freq 2427 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2


josiah@josiah:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 64:0F:29:03:EE:19
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"2WIRE943"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000757e2181
                    Extra: Last beacon: 612ms ago
                    IE: Unknown: 00083257495245393433
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030104
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:1D:7E:F9:26:A6
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"18"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a35223219f
                    Extra: Last beacon: 444ms ago
                    IE: Unknown: 00023138
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020015000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 28:16:2E:22:BC:29
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"2WIRE173"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000252b55181
                    Extra: Last beacon: 924ms ago
                    IE: Unknown: 00083257495245313733
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 04 - Address: C0:3F:0E:E0:D5:96
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Selam1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f1d32bf18f
                    Extra: Last beacon: 200ms ago
                    IE: Unknown: 000653656C616D31
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: 00:24:01:72:2D:53
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"jeffw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f57fdaa1
                    Extra: Last beacon: 564ms ago
                    IE: Unknown: 00056A65666677
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001900000000000000000000000000000000000000
                    IE: Unknown: 3D1606001900000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
          Cell 06 - Address: 98:2C:BE:29:78:B9
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"2WIRE352"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000170b064b181
                    Extra: Last beacon: 448ms ago
                    IE: Unknown: 00083257495245333532
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 07 - Address: 28:16:2E:0D:2F:11
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"2WIRE412"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000e74181
                    Extra: Last beacon: 412ms ago
                    IE: Unknown: 00083257495245343132
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C


```

Thank you very much for your help, I've been trying so hard to get something to work.

---

### Post by wildmanne39 on 2011-12-20
Hi, your driver is loaded and the wireless is scanning for networks,

What is the name of the network you want to connect too?

Disconnect your wired connection then please run this command and post all the output here:
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan1 -e wpa -e etwork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by josiahw216 on 2011-12-20
Thanks for your help. I'm trying to connect to 18.

```
josiah@josiah:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wpa -e etwork | tail -n55
[sudo] password for josiah: 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 3 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 3'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 2 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 2'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 9 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 9'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 4 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 4'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 10 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 10'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 5 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 5'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 7 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 7'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 8 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 8'
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile: parsing 18 1 ... 
Dec 20 17:19:52 josiah NetworkManager[839]:    keyfile:     read connection '18 1'
Dec 20 17:19:52 josiah NetworkManager[839]:    Ifupdown: get unmanaged devices count: 0
Dec 20 17:19:52 josiah NetworkManager[839]: <info> modem-manager is now available
Dec 20 17:19:52 josiah NetworkManager[839]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 20 17:19:52 josiah NetworkManager[839]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Dec 20 17:19:52 josiah NetworkManager[839]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 20 17:19:52 josiah NetworkManager[839]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 20 17:19:52 josiah NetworkManager[839]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 20 17:19:52 josiah NetworkManager[839]: <info> Networking is enabled by state file
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): carrier is OFF
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): new Ethernet device (driver: 'e1000e' ifindex: 2)
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): now managed
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): bringing up device.
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): preparing device.
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (eth1): deactivating device (reason 'managed') [2]
Dec 20 17:19:52 josiah NetworkManager[839]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:19.0/net/eth1
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): now managed
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 20 17:19:52 josiah NetworkManager[839]: <info> (wlan1): bringing up device.
Dec 20 17:19:53 josiah NetworkManager[839]: <info> (wlan1): preparing device.
Dec 20 17:19:53 josiah NetworkManager[839]: <info> (wlan1): deactivating device (reason 'managed') [2]
Dec 20 17:19:53 josiah dbus[821]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 20 17:19:53 josiah NetworkManager[839]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 20 17:19:53 josiah dbus[821]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 20 17:19:53 josiah NetworkManager[839]: <info> wpa_supplicant started
Dec 20 17:19:53 josiah NetworkManager[839]: <info> (wlan1): supplicant interface state: starting -> ready
Dec 20 17:19:53 josiah NetworkManager[839]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 20 17:19:53 josiah NetworkManager[839]: <info> (wlan1): supplicant interface state: ready -> inactive
Dec 20 17:19:53 josiah kernel: [   17.186418] type=1400 audit(1324430393.467:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=907 comm="apparmor_parser"
Dec 20 17:19:53 josiah NetworkManager[839]: <warn> bluez error getting default adapter: No such adapter
Dec 20 17:19:59 josiah kernel: [   22.753495] IBM TrackPoint firmware: 0x0e, buttons: 3/3

```

---

### Post by wildmanne39 on 2011-12-20
Hi, may I see"
```
cat /etc/NetworkManager/NetworkManager.conf 
cat /etc/network/interfaces
```
Thanks

---

### Post by josiahw216 on 2011-12-20
Certainly:

```
josiah@josiah:~$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
josiah@josiah:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by wildmanne39 on 2011-12-20
Hi, Please do:
```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
Change managed=false to managed=true. Proofread, save and close gedit. Reboot. 

Also set your routers encryption to wpa2 if possible and noot wpa or wpa/wpa2.

Now post:
```
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan1 -e wpa -e etwork | tail -n55
``` 
with the wired connection unplugged.

---

### Post by josiahw216 on 2011-12-20
Okay, took me a while to change to wpa2 but it's done. Here you go:

```
josiah@josiah:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlanl -e wpa -e etwork | tail -n55
[sudo] password for josiah: 
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile:     read connection '18 6'
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile: parsing 18 ... 
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile:     read connection '18'
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile: parsing 18 3 ... 
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile:     read connection '18 3'
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile: parsing 18 2 ... 
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile:     read connection '18 2'
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile: parsing 18 9 ... 
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile:     read connection '18 9'
Dec 20 18:11:02 josiah NetworkManager[833]:    keyfile: parsing 18 4 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 4'
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile: parsing 18 10 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 10'
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile: parsing 18 5 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 5'
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile: parsing 18 7 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 7'
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile: parsing 18 8 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 8'
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile: parsing 18 1 ... 
Dec 20 18:11:03 josiah NetworkManager[833]:    keyfile:     read connection '18 1'
Dec 20 18:11:03 josiah NetworkManager[833]: <info> modem-manager is now available
Dec 20 18:11:03 josiah NetworkManager[833]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 20 18:11:03 josiah NetworkManager[833]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ieee80211/phy0/rfkill0) (driver (unknown))
Dec 20 18:11:03 josiah NetworkManager[833]: <info> WiFi enabled by radio killswitch; enabled by state file
Dec 20 18:11:03 josiah NetworkManager[833]: <info> WWAN enabled by radio killswitch; enabled by state file
Dec 20 18:11:03 josiah NetworkManager[833]: <info> WiMAX enabled by radio killswitch; enabled by state file
Dec 20 18:11:03 josiah NetworkManager[833]: <info> Networking is enabled by state file
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): carrier is OFF
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): new Ethernet device (driver: 'e1000e' ifindex: 2)
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): now managed
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): bringing up device.
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): preparing device.
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (eth1): deactivating device (reason 'managed') [2]
Dec 20 18:11:03 josiah NetworkManager[833]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:19.0/net/eth1
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl8192ce' ifindex: 3)
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): now managed
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): bringing up device.
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): preparing device.
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): deactivating device (reason 'managed') [2]
Dec 20 18:11:03 josiah dbus[815]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Dec 20 18:11:03 josiah NetworkManager[833]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Dec 20 18:11:03 josiah dbus[815]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Dec 20 18:11:03 josiah NetworkManager[833]: <info> wpa_supplicant started
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): supplicant interface state: starting -> ready
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 20 18:11:03 josiah NetworkManager[833]: <info> (wlan1): supplicant interface state: ready -> inactive
Dec 20 18:11:03 josiah kernel: [   17.369080] type=1400 audit(1324433463.650:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=894 comm="apparmor_parser"
Dec 20 18:11:03 josiah NetworkManager[833]: <warn> bluez error getting default adapter: No such adapter
Dec 20 18:11:09 josiah kernel: [   23.163214] IBM TrackPoint firmware: 0x0e, buttons: 3/3
josiah@josiah:~$ 


```

---

### Post by wildmanne39 on 2011-12-20
Hi, did you get this done as well?
> Change managed=false to managed=true. Proofread, save and close gedit. Reboot. 

If so the errors are still there, I found other people with this issue and it does not look good but we will keep trying.
Thanks

---

### Post by josiahw216 on 2011-12-20
Yes, I just double checked again.

I'm having the same trouble on a desktop. Maybe I have a corrupted install? I used the same USB thumbdrive and .iso file. Maybe I should download a new one and use a different thumb drive.

---

### Post by wildmanne39 on 2011-12-20
Hi, I think you need to try what is in post 29 of this link and it will work.
[http://ubuntuforums.org/showthread.php?p=11549782](http://ubuntuforums.org/showthread.php?p=11549782)
if you need more help with it post back but reinstalling will not help.
Thanks

---

### Post by josiahw216 on 2011-12-20
I wasn't able to install build-essential. I have the .deb and tried to run it but I get the error:
```
dpkg: failed to open package info file '/usr/local/var/lib/dpkg/status' for reading: No such file or directory
```

I was able to install DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_pr  epared.tar.gz fine though.

I think build-essential is what's holding me back. Can I fix dpkg? It wasn't installed before, maybe I screwed up the installation.

---

### Post by wildmanne39 on 2011-12-20
Hi, did you run this command? and just copy and paste all commands for accuracy.
```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
Thanks

---

### Post by josiahw216 on 2011-12-20
Here's what I get:

```
root@josiah:/home/josiah/dpkg-1.15.8.11# sudo apt-get install linux-headers-$(uname -r) build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-14-generic-pae is already the newest version.
linux-headers-3.0.0-14-generic-pae set to manually installed.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@josiah:/home/josiah/dpkg-1.15.8.11# 

```

Should I try to get g++ and dpkg-dev? I tried to get g++ but found it very complicated.

---

### Post by wildmanne39 on 2011-12-20
Hi, yep you have a problem with installing packages.

First try this:
```
sudo apt-get -f install
sudo apt-get update
```
post any errors here.
Thanks

---

### Post by josiahw216 on 2011-12-20
I'm not connected to the internet so I'm not surprised this didn't work. (wired connection doesn't work either)

```
root@josiah:/home/josiah# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
  libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg libstdc++6-4.6-doc diffutils-doc
The following NEW packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
  libtimedate-perl patch
0 upgraded, 11 newly installed, 0 to remove and 277 not upgraded.
1 not fully installed or removed.
Need to get 8,709 kB of archives.
After this operation, 28.9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++ i386 4:4.6.1-2ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libtimedate-perl all 1.2000-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main patch i386 2.6.1-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main fakeroot i386 1.17-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2
  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/libstdc++6-4.6-dev_4.6.1-9ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.6/g++-4.6_4.6.1-9ubuntu3_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.6.1-2ubuntu5_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtimedate-perl/libtimedate-perl_1.2000-1_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.16.0.3ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6.1-2_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.16.0.3ubuntu5_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.17-1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-2_all.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-1build1_i386.deb  Could not resolve 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-2_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@josiah:/home/josiah# sudo apt-get update
Err http://extras.ubuntu.com oneiric InRelease
  
Err http://us.archive.ubuntu.com oneiric InRelease
  
Err http://us.archive.ubuntu.com oneiric-updates InRelease
  
Err http://us.archive.ubuntu.com oneiric-backports InRelease
  
Err http://security.ubuntu.com oneiric-security InRelease
  
Err http://extras.ubuntu.com oneiric Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://us.archive.ubuntu.com oneiric Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com oneiric-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com oneiric-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com oneiric-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@josiah:/home/josiah# 

```

---

### Post by wildmanne39 on 2011-12-20
Hi, I forgot you had no internet that makes this hard.

Lets try this click on dash type source into the search window it will bring up software sources at the bottom of the window put a check by from cdrom, put in your password then close.

Put the livecd into your drive and run the command to install build essentials again.
Thanks

---

### Post by josiahw216 on 2011-12-20
My laptop doesn't have a CD drive. How can I run livecd with a .iso image or a usb installed with a boot loader? Do I restart the machine and boot from the usb?

---

### Post by wildmanne39 on 2011-12-20
Hi, no just plug your usb in and then try to isntall the packages, the usb is can also be used just like the livecd.

Still do the source list part first.

I am getting off for tonight,I will be back tomorrow.
Thanks

---

### Post by josiahw216 on 2011-12-21
I'm trying to run the usb but it seems like it only runs in Windows. Am I doing something wrong? Can I mount an iso to /media/cdrom or direct the updater to the usb?

---

### Post by wildmanne39 on 2011-12-21
Hi, open disk utility and make sure it is mounted, if not mount it, then follow directions in post 16, still put a check by cdrom and that will direct it to the liveusb if it is showing up.
Thanks

---

### Post by josiahw216 on 2011-12-21
Even with my thumb-drive mounted it's still asking for the CD:

```
josiah@josiah:~$ sudo apt-get -f install
[sudo] password for josiah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 277 not upgraded.
josiah@josiah:~$ sudo apt-get build-essential
E: Invalid operation build-essential
josiah@josiah:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl patch
0 upgraded, 12 newly installed, 0 to remove and 277 not upgraded.
Need to get 8,546 kB/8,714 kB of archives.
After this operation, 29.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++ i386 4:4.6.1-2ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libtimedate-perl all 1.2000-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main build-essential i386 11.5ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2
  Could not resolve 'us.archive.ubuntu.com'
Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter
sudo apt-get install linux-headers-$(uname -r) build-essential
Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter
^Cjosiah@josiah:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 277 not upgraded.
josiah@josiah:~$ clear

josiah@josiah:~$ sudo apt-get install linux-headers-$(uname -r) build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.0.0-14-generic-pae is already the newest version.
linux-headers-3.0.0-14-generic-pae set to manually installed.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev
  libtimedate-perl patch
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg libstdc++6-4.6-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl patch
0 upgraded, 12 newly installed, 0 to remove and 277 not upgraded.
Need to get 8,546 kB/8,714 kB of archives.
After this operation, 29.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libstdc++6-4.6-dev i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++-4.6 i386 4.6.1-9ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main g++ i386 4:4.6.1-2ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libtimedate-perl all 1.2000-1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libdpkg-perl all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main dpkg-dev all 1.16.0.3ubuntu5
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main build-essential i386 11.5ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-perl all 1.19.02-2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-diff-xs-perl i386 0.04-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/main libalgorithm-merge-perl all 0.08-2
  Could not resolve 'us.archive.ubuntu.com'
Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter

Media change: please insert the disc labeled
 'Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)'
in the drive '/media/cdrom/' and press enter
^Cjosiah@josiah:~sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 277 not upgraded.
josiah@josiah:~$ 

```

Also I had to reinstall because I messed up fstab trying to mount an iso.

---

### Post by wildmanne39 on 2011-12-21
Hi, I do not know then you must have those packages to continue.

Can you take your computer to a friends house and use his wired connection to install the needed packages? 
Thanks

---

### Post by josiahw216 on 2011-12-21
I have a wired connection, but it doesn't work when plugged in. Is there a way to reinstall but choose what packages I want to install as well?

---

### Post by wildmanne39 on 2011-12-21
Hi, I am researching to see if I can find how to get your wired connection working.
Thanks

---

### Post by wildmanne39 on 2011-12-21
Hi, please post output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/NetworkManager/nm-system-settings.conf
```
Thanks

---

### Post by josiahw216 on 2011-12-21
I don't think I have a nm-system-settings.conf. I looked in the directory and couldn't find anything like that. Here's the rest of the result.

```
josiah@josiah:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
josiah@josiah:~$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory
josiah@josiah:~$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory
josiah@josiah:~$ 

```

In the mean time I'm researching how to add the .iso to fstab and put in the source.

---

### Post by josiahw216 on 2011-12-21
I mounted the .iso and added it to the source. The only time it looks is when I put in sudo apt-get update, and then the error: ```
Unable to find expected entry 'man/source/Sources' in Release file (Wrong sources.list entry or malformed file)
```

The other commands (sudo apt-get install linux-headers-$(uname -r) build-essential) it doesn't look in the .iso. Can I change this? Why does it only look online to find build-essential?

---

### Post by wildmanne39 on 2011-12-21
Hi, I do not know how to change it but manually editing your source list is a bad idea, and the message it gave you now means you have broken your package manager you need to remove what you added before you can install anything even with internet working.

Please show:
```
cat /etc/network/interfaces
```
Thanks

---

### Post by josiahw216 on 2011-12-21
Okay, removed the sources. Here's what I get:

```
root@josiah:/home/josiah# cat /etc/network/interfaces
auto lo
iface lo inet loopback

root@josiah:/home/josiah#
```

---

### Post by wildmanne39 on 2011-12-21
Hi, that looks good, please post:
```
dmesg | grep e1000
```
Thanks

---

### Post by josiahw216 on 2011-12-21
Done.

```
root@josiah:/home/josiah# dmesg | grep e1000
[    0.000000] ACPI: SSDT dafe1000 00A27 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)
[    1.296701] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    1.296704] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    1.296743] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.296755] e1000e 0000:00:19.0: setting latency timer to 64
[    1.296863] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[    1.491014] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) f0:de:f1:b1:ea:21
[    1.491017] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.491069] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1000FF-0FF
[   20.867571] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[   20.923328] e1000e 0000:00:19.0: irq 40 for MSI/MSI-X
[ 1225.044673] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 1225.044685] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 1276.420673] e1000e: eth0 NIC Link is Down


```

---

### Post by wildmanne39 on 2011-12-21
Hi, I asked a friend to take a look and see if he can help us, he has been working with network issues much longer then I have.
Thanks

---

### Post by josiahw216 on 2011-12-21
Thank you very much for your help. I've almost given up, but I'll wait for your friend's advice. I'll be out for a bit.

---

### Post by wildmanne39 on 2011-12-21
Hi, I made a mistake last night when I looked up the error messages even though it was the same error it was for a different wireless card so the fix that I recommended will not work, I am sorry about that I was working with to many people at once last night that I did not catch that.

He is good, I think he will at least get the wired working.

---

### Post by praseodym on 2011-12-21
Hi,

try to change the encryption mode from WPA to WPA2 if possible. If it does not work try to copy the firmware for the wireless card to the "right" place. Driver attached, save it to "Downloads" and try the fimware only:

```
cd Downloads/
tar xvf rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011.tar.gz
cd rtl_92ce_92se_92de_Ubuntu_11.x_mac80211_0004.0816.2011
sudo cp -r firmware/* /lib/firmware
``` 
Reload the driver:

```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Check:
```
iwconfig
rfkill list
dmesg | egrep 'rtl8|r8'
```

---

### Post by wildmanne39 on 2011-12-21
Thank you praseodym, also he does not have ehternet connection either.

---

### Post by westie457 on 2011-12-21
@ wildmanne39 and @ josiahw216

To install .deb packages from a USB use Nautilus. In this case for build-essential navigate your way to /pool/main/b/build-essential then double-click on the .deb package and it will install with the Software Center.

Hope this helps.

---

### Post by praseodym on 2011-12-21
Yes, I saw that. But the ethernet driver e1000e also has problems in 11.04 11.10:

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

But to compile he needs **build-essential**. Try to double click all files named by the command
```
sudo apt-get install build-essential
```
from the installation stick. The kernel header files are here:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12-generic-pae_3.0.0-12.20_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12-generic-pae_3.0.0-12.20_i386.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12_3.0.0-12.20_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.0.0-12_3.0.0-12.20_all.deb)

Can you boot from stick and connect (because kernel 3.0.0-14 is not the default kernel, there must have been an update)?

If yes, boot from stick and try:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential
```
and c/p all files from the live systems folder **/var/cache/apt/archive** to the native system, which is mounted in **/media/somelongnumberfoldername**, reboot into the native system, install the packages by:
```
sudo dpkg -i /path/to/the/files/*.deb
```
and compile the wireless driver in its folder:
```
make
sudo make install
```
and reboot again (if the firmware was already copied).

---

### Post by wildmanne39 on 2011-12-21
Hi, thank you westie457 that helps a lot.

@praseodym yes I know there is problems with the e1000e driver also that is why I am pulling my hair out.

---

### Post by josiahw216 on 2011-12-21
@praseodym: I did all of that, and still nothing. Looked for error messages or dependency issues when installing the debs but I didn't see anything. Same with compiling the driver.

Give it to me honest: is it still possible to get this to work or should I downgrade to 11.04 or 10.10?

---

### Post by josiahw216 on 2011-12-21
Unless anyone has any suggestions, I've decided to downgrade to 10.10. Thank you wildmanne39 and everyone else for your help. If you have a supervisor or someone I'd love to put in a good word.

I'm a little disappointed with 11.10 because I've had nothing but trouble. Maybe this was my fault, I don't know. Hopefully this will be solved with 12.04.

---

### Post by wildmanne39 on 2011-12-21
Hi, no it was not your fault there are issues with both of the drivers you need which makes it harder to fix but praseodym may have more idea's but he usually does not come back on for another five hours because he lives in Germany.

It is up to you what you want to do but I am stuck since neither connection is working if you tried what praseodym and westie457 suggested.
Thanks

---

### Post by josiahw216 on 2011-12-21
Thank you but I think I will downgrade still. It's not that big of a deal to have 11.10 and I've already taken up too much of your time. Again, you have helped me so much and I am grateful. Happy a happy holidays!

---

### Post by wildmanne39 on 2011-12-21
Your welcome!!! Merry Christmas.

---

### Post by praseodym on 2011-12-22
Hi,


in 10.10 you may get problems with the wireless driver, too. You can update it via "dkms" [COLOR="Red"](this driver version works only for 10.04 and 10.10)[/COLOR]:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2844083/rtl8192ce_dkms_2.6.0006.0321.tar.gz
sudo tar xvf rtl8192ce_dkms_2.6.0006.0321.tar.gz -C /usr/src
sudo dkms add -m rtl8192ce -v 2.6.0006.0321
sudo dkms build -m rtl8192ce -v 2.6.0006.0321
sudo dkms install -m rtl8192ce -v 2.6.0006.0321 
```
Reboot. Be sure to install the metapackage of your kernel-headers suitable to you kernel architecture, too (e.g. linux-headers-generic, linux-headers-generic-pae, whatever).

---


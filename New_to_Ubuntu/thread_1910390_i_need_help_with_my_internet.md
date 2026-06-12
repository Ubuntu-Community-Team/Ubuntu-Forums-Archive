---
title: "i need help with my internet"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by sweetypup8624 on 2012-01-17
So I have 10.10th and I've been trying forever to get my wireless to work. I know nothing at all about ubuntu or how to do anything but I figured out how to ping and entering  numbers i was told to enter there was 0% successful packets so I entered ubuntu.com and it can't connect to sms server if someone could please help me and explain it simple I don't know what anytging means so I mean real  
simple

Thank you so much

---

### Post by sweetypup8624 on 2012-01-17
I ment dns server sorry on phone damn auto correct. Thanks again

---

### Post by sweetypup8624 on 2012-01-17
Anyone? Please I dont know how to make it work

---

### Post by goofey24 on 2012-01-17
Hardware info would help?

---

### Post by sweetypup8624 on 2012-01-17
What kind  of info? all i know is I have an asus ng1vg and ubuntu 10.10

---

### Post by Kslawdog on 2012-01-17
You will probably want to download **_ndiswrapper_** from synaptic package manager.  It's been a while since I used it but it will help you install the correct drivers for your card.  You just have to find the right driver.

Maybe try this from terminal

```
sudo apt-get install ndiswrapper
```That's a quick way to install it. Then it will be located in System-->Administration

---

### Post by sweetypup8624 on 2012-01-17
Ok I downloaded that.....but it doesnt see any drivers and it says Add new driver but then it takes me to files in my computer???

---

### Post by gandaran on 2012-01-17
first post the wireless chipset brand and model then we can help you with what drivers to install, run this code in terminal to show wireless info about brand and driver, post the output.
```
sudo lshw -C network
```

---

### Post by sweetypup8624 on 2012-01-17
oK Here is the info after putting in that:
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:6e:ae:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-31-generic firmware=N/A ip=192.168.2.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fdff0000-fdffffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 90:e6:ba:20:5f:db
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.2.5 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:47 memory:febc0000-febfffff ioport:ec00(size=128)

---

### Post by goofey24 on 2012-01-17
Try [here]("http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285")
Not a pro at this but it's a start. :D
And [here]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285")

---

### Post by wildmanne39 on 2012-01-17
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
```
nm-tool
sudo iwlist scan
```
```
lsmod | grep ath
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by sweetypup8624 on 2012-01-17
**cat /etc/lsb-release; uname -a=**

cat: /ect/lsb-release: No such file or directory
Linux sweetypup8624 2.6.35-31-generic #63-Ubuntu SMP Mon Nov 28 19:23:11 UTC 2011 i686 GNU/Linux

**lspci -nnk | grep -iA2 net=**
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of a2
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file


**iwconfig=**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"belkin.7a6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:78:E7:A6   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-26 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
rfkill list all=[/B]

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

**lsmod=**
Module                  Size  Used by
usbhid                 36882  0 
hid                    67742  1 usbhid
aes_i586                7280  2 
aes_generic            26875  1 aes_i586
rfcomm                 32575  4 
binfmt_misc             6599  1 
sco                     7867  2 
bnep                    9305  2 
l2cap                  38677  16 rfcomm,bnep
parport_pc             26058  0 
ppdev                   5556  0 
arc4                    1165  2 
ath9k                  89901  0 
nvidia               9329739  40 
mac80211              235093  1 ath9k
joydev                  8767  0 
ath9k_common            4396  1 ath9k
snd_hda_codec_nvhdmi    13615  1 
snd_hda_codec_realtek   218460  1 
ath9k_hw              291766  2 ath9k,ath9k_common
snd_hda_intel          22235  2 
ath                     8053  2 ath9k,ath9k_hw
btusb                  10969  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              142616  3 ath9k,mac80211,ath
video                  18712  0 
output                  1883  1 video
asus_laptop            14084  0 
sparse_keymap           3145  1 asus_laptop
snd                    49102  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              53007  9 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               55911  0 
intel_agp              26566  0 
psmouse                59033  0 
serio_raw               4022  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
led_class               2633  2 ath9k,asus_laptop
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19326  2 
atl1c                  29872  0 
libahci                21728  1 ahci

---

### Post by sweetypup8624 on 2012-01-17
**nm-tool=**

NetworkManager Tool

State: connected

- Device: wlan0  [Auto belkin.7a6] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        00:25:D3:6E:AE:D7

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    myqwest5257:     Infra, 40:4A:03:F2:35:F1, Freq 2462 MHz, Rate 48 Mb/s, Strength 28 WEP
    airportthru:     Ad-Hoc, 3A:FD:9D:D3:EA:9C, Freq 2457 MHz, Rate 54 Mb/s, Strength 32
    HOMEFRONT:       Infra, 00:0F:B5:D7:91:B4, Freq 2437 MHz, Rate 54 Mb/s, Strength 31 WPA WPA2
    Jarrard1:        Infra, E0:91:F5:01:89:89, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA
    *belkin.7a6:     Infra, 08:86:3B:78:E7:A6, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        90:E6:BA:20:5F:DB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

---

### Post by sweetypup8624 on 2012-01-17
**sudo iwlist scan=**
[HTML]
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: E0:91:F5:01:89:89
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Jarrard1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d327a8d80
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 00084A61727261726431
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD840050F204104A0001101044000102103B0001031047001000000000000010000000E091F50189891021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110015574E44523337303028576972656C65737320415029100800020086103C000103
          Cell 02 - Address: 00:26:F3:4F:BA:08
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000008fdea23156
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A8800026F34FBA08103C000101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD07000C4300000000
          Cell 03 - Address: 00:26:F3:4F:BA:09
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000008fdea23ba0
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD07000C4300000000
          Cell 04 - Address: 00:26:F3:4F:BA:0A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000008fdea244a2
                    Extra: Last beacon: 164ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD07000C4300000000
          Cell 05 - Address: 00:26:F3:4F:BA:0B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000008fdea24da3
                    Extra: Last beacon: 164ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0E1016FFFF000001000000000000000000000000030000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD07000C4300000000
          Cell 06 - Address: 08:86:3B:78:E7:A6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"belkin.7a6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d825ea6ab
                    Extra: Last beacon: 16ms ago
                    IE: Unknown: 000A62656C6B696E2E376136
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501000C127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD9E0050F204104A00011010440001021041000100103B000103104700100000000000000001100008863B78E7A61021001242656C6B696E20436F72706F726174696F6E1023000A46394B3130303220763210240007322E30302E30361042000E31323131343147433230383134391054000800060050F20400011011001B42656C6B696E20576972656C65737320526F757465722857464129100800020004
                    IE: Unknown: 0706555320010B10
          Cell 07 - Address: 00:0F:B5:D7:91:B4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HOMEFRONT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043b87ca182
                    Extra: Last beacon: 1036ms ago
                    IE: Unknown: 0009484F4D4546524F4E54
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555349010B1A
                    IE: Unknown: 0C120F0002A4C80027A400004243C80062326400
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD15000AF50A0240C000030103050E04FF000700110101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 3A:FD:9D:D3:EA:9C
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"airportthru"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000648b7723a4
                    Extra: Last beacon: 776ms ago
                    IE: Unknown: 000B616972706F727474687275
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020010000000[/HTML]

---

### Post by sweetypup8624 on 2012-01-17
**lsmod | grep ath=**

ath9k                  89901  0 
mac80211              235093  1 ath9k
ath9k_common            4396  1 ath9k
ath9k_hw              291766  2 ath9k,ath9k_common
ath                     8053  2 ath9k,ath9k_hw
cfg80211              142616  3 ath9k,mac80211,ath
led_class               2633  2 ath9k,asus_laptop

**sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55=**

Aug 24 17:00:21 sweetypup8624 NetworkManager[940]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug 24 17:00:21 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 24 17:00:21 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Aug 24 17:00:22 sweetypup8624 wpa_supplicant[1058]: Trying to associate with 08:86:3b:78:e7:a6 (SSID='belkin.7a6' freq=2412 MHz)
Aug 24 17:00:22 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 24 17:00:22 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 24 17:00:22 sweetypup8624 wpa_supplicant[1058]: Associated with 08:86:3b:78:e7:a6
Aug 24 17:00:22 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 24 17:00:23 sweetypup8624 avahi-daemon[947]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::225:d3ff:fe6e:aed7.
Aug 24 17:00:23 sweetypup8624 avahi-daemon[947]: New relevant interface wlan0.IPv6 for mDNS.
Aug 24 17:00:23 sweetypup8624 avahi-daemon[947]: Registering new address record for fe80::225:d3ff:fe6e:aed7 on wlan0.*.
Aug 24 17:00:24 sweetypup8624 wpa_supplicant[1058]: WPA: Key negotiation completed with 08:86:3b:78:e7:a6 [PTK=CCMP GTK=CCMP]
Aug 24 17:00:24 sweetypup8624 wpa_supplicant[1058]: CTRL-EVENT-CONNECTED - Connection to 08:86:3b:78:e7:a6 completed (auth) [id=0 id_str=]
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  4-way handshake -> group handshake
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> (wlan0): supplicant connection state:  group handshake -> completed
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'belkin.7a6'.
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 24 17:00:24 sweetypup8624 kernel: [   17.228419] wlan0: authenticate with 08:86:3b:78:e7:a6 (try 1)
Aug 24 17:00:24 sweetypup8624 kernel: [   17.230386] wlan0: authenticated
Aug 24 17:00:24 sweetypup8624 kernel: [   17.230399] wlan0: associate with 08:86:3b:78:e7:a6 (try 1)
Aug 24 17:00:24 sweetypup8624 kernel: [   17.234379] wlan0: RX AssocResp from 08:86:3b:78:e7:a6 (capab=0x411 status=0 aid=1)
Aug 24 17:00:24 sweetypup8624 kernel: [   17.234382] wlan0: associated
Aug 24 17:00:24 sweetypup8624 kernel: [   17.242455] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 24 17:00:24 sweetypup8624 dhclient: Listening on LPF/wlan0/00:25:d3:6e:ae:d7
Aug 24 17:00:24 sweetypup8624 dhclient: Sending on   LPF/wlan0/00:25:d3:6e:ae:d7
Aug 24 17:00:24 sweetypup8624 dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 24 17:00:24 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 24 17:00:24 sweetypup8624 avahi-daemon[947]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Aug 24 17:00:24 sweetypup8624 avahi-daemon[947]: New relevant interface wlan0.IPv4 for mDNS.
Aug 24 17:00:24 sweetypup8624 avahi-daemon[947]: Registering new address record for 192.168.2.3 on wlan0.IPv4.
Aug 24 17:00:25 sweetypup8624 NetworkManager[940]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Aug 24 17:00:25 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Aug 24 17:00:25 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) successful, device activated.
Aug 24 17:00:25 sweetypup8624 NetworkManager[940]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 24 17:00:32 sweetypup8624 kernel: [   27.600591] wlan0: no IPv6 routers present
Aug 24 17:02:20 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:34:15 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:34:15 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:34:33 sweetypup8624 kernel: [  513.008057] Modules linked in: usbhid hid aes_i586 aes_generic rfcomm binfmt_misc sco bnep l2cap parport_pc ppdev arc4 ath9k nvidia(P) mac80211 joydev ath9k_common snd_hda_codec_nvhdmi snd_hda_codec_realtek ath9k_hw snd_hda_intel ath btusb snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 video output asus_laptop sparse_keymap snd bluetooth uvcvideo intel_agp psmouse serio_raw videodev v4l1_compat led_class soundcore snd_page_alloc agpgart lp parport ahci atl1c libahci
Jan 17 19:34:33 sweetypup8624 kernel: [  513.008146]  [<c014b602>] warn_slowpath_common+0x72/0xa0
Jan 17 19:34:33 sweetypup8624 kernel: [  513.008165]  [<c014b6d3>] warn_slowpath_fmt+0x33/0x40
Jan 17 19:34:38 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:34:56 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:34:56 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.
Jan 17 19:35:23 sweetypup8624 NetworkManager[940]: <info> Policy set 'Auto belkin.7a6' (wlan0) as default for IPv4 routing and DNS.

---

### Post by sweetypup8624 on 2012-01-17
I wasnt really sure how to post those but thats what i got

---

### Post by Kslawdog on 2012-01-17
[http://forums.laptopvideo2go.com/topic/14833-latest-atheros-wlan-drivers-for-windows-7-and-vista-x86-x64/](http://forums.laptopvideo2go.com/topic/14833-latest-atheros-wlan-drivers-for-windows-7-and-vista-x86-x64/) ok, go here try this version first....  [ v7.4.2.15  ]("http://files.laptopvideo2go.com/wlan/atheros_v7.4.2.15.exe")
save to desktop

It's going to download an .exe file so all you need to do is 
right click
extract here
open ndiswrapper (windows wireless drivers) navigate to file and install netathrx.inf
If that doesn't work try different drivers on the site.
hope that works, good luck!

---

### Post by sweetypup8624 on 2012-01-17
Ok so I went to that site and downloaded the exe and it popped up ith an error that said

Archive:  /home/sweetypup8624/Downloads/atheros_v7.4.2.15.exe
[/home/sweetypup8624/Downloads/atheros_v7.4.2.15.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/sweetypup8624/Downloads/atheros_v7.4.2.15.exe or
          /home/sweetypup8624/Downloads/atheros_v7.4.2.15.exe.zip, and cannot find /home/sweetypup8624/Downloads/atheros_v7.4.2.15.exe.ZIP, period.

---

### Post by wildmanne39 on 2012-01-17
Hi, the driver that you need is installed, you do not need or want ndiswrapper. I am looking over the information and will post in a few minutes.
Thanks

---

### Post by Kslawdog on 2012-01-17
did that happen after you downloaded the file or after you tried to extract it?

Oh I see the problem don't click the version click the html link...sorry

---

### Post by dineshs on 2012-01-17
Please see this post
[http://ubuntuforums.org/showpost.php?p=9842328&postcount=11](http://ubuntuforums.org/showpost.php?p=9842328&postcount=11)
I think the wifi connection will work if you unplug your ethernet cable.

---

### Post by wildmanne39 on 2012-01-18
Hi, Please do:
```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
Then go to your network icon in the top right corner of the screen click on it>edit connections>wireless make your settings look like the screenshots except you can leave connect automatically checked.

You should take the period out of your SSID.

Go into your router settings and change encryption to just wpa2 if you can.

You can usually access your routers settings by typing 192.168.0.1 into your web browser.

Please do:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

---

### Post by sweetypup8624 on 2012-01-18
**echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf**

net.ipv6.conf.all.disable_ipv6=1


i dont know if you wanted me to post that or not but thats that im finishing up and will let you know if it works

---

### Post by sweetypup8624 on 2012-01-18
Ok so that didn't work. Now I went to my moms and my wireless works but home again and It doesn't......

---

### Post by wildmanne39 on 2012-01-18
Hi, it has to be a setting that needs changed.

Did you do everything in my last post including changing encryption in the router?

Please reset your router with your wired connection unplugged.
Thanks

---

### Post by sweetypup8624 on 2012-01-18
I did everything you said in your last post and restarted the router still doesn't work

---

### Post by wildmanne39 on 2012-01-18
Hi, please open this file:
```
gksudo gedit /etc/modprobe.d/ath9k.conf
```
and paste the contents here.
```
nm-tool
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
cat /etc/resolv.conf
```
```
lsmod | grep ath
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wpa -e wlan -e etork | tail -n55
```
```
ndiswrapper -l
```
The reason I am asking for some of this information again is I want to make sure the changes were saved.

Also as was pointed out earlier in ubuntu before 11.04 it is important to have your wired connection unplugged while you are running these codes and trying to connect.
Thanks

---

### Post by badmts on 2012-01-18
I never got my wireless to work but I was told to try WICD (pronounced WICKED) good luck and keep posting I am learning too

---


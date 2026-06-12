---
title: "WiFi drop out"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by DGINSD on 2011-12-25
Just installed 11.10 on my Dell X300 works well but I get a drop out of the wireless connection every now and then, rather annoying any suggestions?

---

### Post by wildmanne39 on 2011-12-25
Hi please post the results of:
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

### Post by DGINSD on 2011-12-26
OK here it is, it's very possible the wireless router just sucks, but I figure better to ask those who know before I make assumptions

```
david@david-Latitude-X300:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux david-Latitude-X300 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux


david@david-Latitude-X300:~$ lspci -nnk | grep -iA2 net
02:04.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card [1028:0003]
	Kernel driver in use: b43-pci-bridge
--
02:05.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
	Subsystem: Dell Device [1028:2003]
	Kernel driver in use: tg3


david@david-Latitude-X300:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SITH_LAIR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:CE:6B:A5   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:179   Missed beacon:0



david@david-Latitude-X300:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


david@david-Latitude-X300:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  5 
nf_conntrack_irc       13138  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
iptable_nat            13016  0 
iptable_mangle         12646  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  8 
xt_limit               12541  13 
xt_tcpudp              12531  21 
xt_addrtype            12596  0 
xt_state               12514  13 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
mmc_block              22393  2 
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24958  3 ipt_MASQUERADE,iptable_nat,nf_nat_ftp
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
sdricoh_cs             12953  0 
pata_pcmcia            16938  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
snd_intel8x0           33318  2 
nf_conntrack           70103  11 ipt_MASQUERADE,nf_conntrack_irc,iptable_nat,nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_ac97_codec        106082  1 snd_intel8x0
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
x_tables               21975  17 ipt_MASQUERADE,xt_DSCP,iptable_nat,iptable_mangle,ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq_midi           13132  0 
arc4                   12473  2 
pcmcia                 39822  2 sdricoh_cs,pata_pcmcia
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   318816  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
joydev                 17393  0 
i915                  505159  3 
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393459  1 b43
cfg80211              172392  2 b43,mac80211
drm_kms_helper         32889  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
drm                   192194  4 i915,drm_kms_helper
shpchp                 32356  0 
psmouse                73673  0 
serio_raw              12990  0 
dcdbas                 14098  0 
irda                  185428  0 
i2c_algo_bit           13199  1 i915
crc_ccitt              12595  1 irda
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
ssb                    50682  1 b43
tg3                   132972  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

```

---

### Post by wildmanne39 on 2011-12-26
Hi, there was nothing wrong with the information you gave me and this card with that driver is usually dependable, I have one myself.

Please show the following commands when you are having trouble staying connected and make sure you do not have a hard wire pluged in also:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -wlan | tail -n55
```
Thanks

---

### Post by DGINSD on 2011-12-26
So just to clarify run those commands the next time it acts up< and post the output? If thats so, will do.

Just another stupid question totally unrelated, anything special need to be done after a default Ubuntu install to write to a SD card formatted as FAT? Its plugged into the built in reader and detects and reads the card fine (lock is off) but no matter what I do it won't let me write to it.

Thank you for your help BTW.

---

### Post by wildmanne39 on 2011-12-26
Hi, yes that is what you need to do.

I am not sure it may be a permission issue, you should start another thread on that because we are suppose to only cover the topic that is listed.
Thanks

---

### Post by DGINSD on 2011-12-31
> **wildmanne39 said:**
> Hi, there was nothing wrong with the information you gave me and this card with that driver is usually dependable, I have one myself.

Please show the following commands when you are having trouble staying connected and make sure you do not have a hard wire pluged in also:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -wlan | tail -n55
```
Thanks

OK I just had a drop out, I've actually had many since you posted this but it always seemed to be as I was walking out the door. My NM app started searching and searching and after a period of about 2 minutes the authentication window popped up, with my passkey already entered (so my passkey is remembered). While it was searching I had time to run the CLI commands you asked for I put them together as one command, so I could be sure they all got ran before a connection was reestablished I hope I did that correctly and it didn't screw up any of the output (I'm still pretty new to Linux and the CLI). So here's the output, I divided them up accordingly

```

david@david-Latitude-X300:~$ nm-tool && sudo iwlist scan && sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -wlan | tail -n55

NetworkManager Tool

State: connecting

- Device: wlan0  [SITH_LAIR] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:90:96:FC:6C:E8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SITH_LAIR:       Infra, 00:26:5A:CE:6B:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WEP
    2WIRE561:        Infra, 00:26:50:88:AE:61, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WEP
    Rincon:          Infra, 00:04:3F:00:3B:4E, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    bambam:          Infra, 00:1F:33:32:16:CC, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    2WIRE769:        Infra, 00:1D:5A:40:A6:71, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    manzanita:       Infra, 00:18:39:FC:3F:6B, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    BigDannyArvo'sBuds: Infra, 06:21:91:F8:77:42, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Panda:           Infra, 00:19:7D:4D:A2:8A, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    2WIRE080:        Infra, C0:83:0A:BA:B4:D1, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WEP
    2WIRE149:        Infra, C0:83:0A:2A:FB:D9, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    los TOWERS:      Infra, 00:1C:DF:8B:9E:23, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    meowflute:       Infra, 00:26:5A:FF:D8:01, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    Angave:          Infra, 00:27:19:14:30:2E, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    2WIRE295:        Infra, 34:EF:44:C4:1D:21, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Rita321:         Infra, 00:24:B2:45:99:16, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    R4ymond:         Infra, 00:14:6C:D3:5C:62, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    BLOODLINE:       Infra, 00:18:39:E2:BB:A3, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    kurotsushin:     Infra, A0:21:B7:AC:46:7B, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Vergil:          Infra, 20:4E:7F:19:58:1E, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    robert.connie:   Infra, 68:7F:74:28:A9:62, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2WIRE958:        Infra, 64:0F:28:9F:E1:B1, Freq 2447 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2WIRE474:        Infra, 00:1F:B3:32:A4:F1, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    linksys:         Infra, 00:1A:70:54:EB:59, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    YUPO:            Infra, 20:4E:7F:40:91:CA, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Dan-O:           Infra, 00:22:3F:A5:44:47, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    harris27:        Infra, E0:91:F5:AA:B1:C0, Freq 2417 MHz, Rate 54 Mb/s, Strength 49 WPA2
    Genom:           Infra, 58:6D:8F:2B:77:55, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Mitch:           Infra, C4:3D:C7:8C:A4:68, Freq 2432 MHz, Rate 54 Mb/s, Strength 65 WPA2
    2WIRE586:        Infra, 28:16:2E:17:A7:41, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:0F:1F:44:A5:93

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 28:16:2E:17:A7:41
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"2WIRE586"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000376375e5181
                    Extra: Last beacon: 1208ms ago
                    IE: Unknown: 00083257495245353836
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
          Cell 02 - Address: 00:26:5A:CE:6B:A5
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"SITH_LAIR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000cf5dbdd80
                    Extra: Last beacon: 636ms ago
                    IE: Unknown: 0009534954485F4C414952
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD9A0050F204104A0001101044000102103B000103104700100000000000001000000000265ACE6BA510210004467279731023000B4672797320526F757465721024000846522D3534525452104200046E6F6E651054000800060050F204000110110015467279732053797374656D732046522D3534525452100800020086103C000103104900140024E26002000101600000020001600100020001
                    IE: Unknown: DD050050F20500
          Cell 03 - Address: 58:6D:8F:2B:77:55
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Genom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f01d17e7bf
                    Extra: Last beacon: 904ms ago
                    IE: Unknown: 000547656E6F6D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD860050F204104A0001101044000102103B00010310470010A5D0C512DACD3D374B32296231DDDE8E102100074C696E6B7379731023000D4C696E6B7379732045333230301024000776312E302E30301042000234321054000800060050F20400011011000D4C696E6B737973204533323030100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180203F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: 00:1A:70:54:EB:59
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000fc94be18b
                    Extra: Last beacon: 1344ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 05 - Address: 00:22:3F:A5:44:47
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Dan-O"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008eb27547ffd
                    Extra: Last beacon: 924ms ago
                    IE: Unknown: 000544616E2D4F
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F0101003DFF7F
                    IE: Unknown: DD1A00037F030100000000223FA5444706223FA5444764002C013D08
          Cell 06 - Address: 20:4E:7F:40:91:CA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"YUPO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000194e5600d80
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 00045955504F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401020000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 07 - Address: 00:19:7D:4D:A2:8A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Panda"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002a8dea491c3
                    Extra: Last beacon: 1384ms ago
                    IE: Unknown: 000550616E6461
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0406010200000000
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 08 - Address: 00:27:19:14:30:2E
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Angave"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000d2c85bd80
                    Extra: Last beacon: 868ms ago
                    IE: Unknown: 0006416E67617665
                    IE: Unknown: 010882848B968C129824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 3204B048606C
                    IE: Unknown: DD180050F2020101860003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010006004000
          Cell 09 - Address: 00:24:B2:45:99:16
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Rita321"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d7deb1a71b
                    Extra: Last beacon: 1276ms ago
                    IE: Unknown: 000752697461333231
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601051700000000000000000000000000000000000000
                    IE: Unknown: DD710050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000744474E323030301023000744474E323030301024000631323334353610420004313233341054000800060050F20400011011000744474E32303030100800020088
                    IE: Unknown: DD090010180202F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330E181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401051700000000000000000000000000000000000000
          Cell 10 - Address: E0:91:F5:AA:B1:C0
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"harris27"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005c2cb16bd80
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 00086861727269733237
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C34020D0800000000000000000000000000000000000000
                    IE: Unknown: 3D16020D0800000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000010000000E091F5AAB1C0102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F20400011011001B574E5232303030763328576972656C6573732041502D322E344729100800020086103C000103
          Cell 11 - Address: C4:3D:C7:8C:A4:68
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Mitch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000664334eaea
                    Extra: Last beacon: 1008ms ago
                    IE: Unknown: 00054D69746368
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3405051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1605051B00000000000000000000000000000000000000
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78CA468102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F20400011011001B574E5232303030763328576972656C6573732041502D322E344729100800020086103C000103
          Cell 12 - Address: 34:EF:44:C4:1D:21
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE295"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000058160181
                    Extra: Last beacon: 992ms ago
                    IE: Unknown: 00083257495245323935
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030105
                    IE: Unknown: 050400010006
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
          Cell 13 - Address: 00:18:39:E2:BB:A3
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"BLOODLINE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f374535f36
                    Extra: Last beacon: 924ms ago
                    IE: Unknown: 0009424C4F4F444C494E45
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020015
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: 64:0F:28:9F:E1:B1
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"2WIRE958"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000d48181
                    Extra: Last beacon: 704ms ago
                    IE: Unknown: 00083257495245393538
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
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
          Cell 15 - Address: 68:7F:74:28:A9:62
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"robert.connie"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000204c515abb4
                    Extra: Last beacon: 504ms ago
                    IE: Unknown: 000D726F626572742E636F6E6E6965
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD6C0050F204104A00011010440001011041000100103B00010310470010CE239E2E22FC4A72FF5B596C3625BDE3102100074C696E6B737973102300034D3130102400063132333435361042000234321054000800060050F2040001101100034D3130100800020084103C000101
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 16 - Address: 20:4E:7F:19:58:1E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Vergil"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dcee8d2841
                    Extra: Last beacon: 492ms ago
                    IE: Unknown: 000656657267696C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001017B88E3D91C1DB4C02089A11AA618ACC1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000 

```

```

(standard input)

```

---

### Post by wildmanne39 on 2011-12-31
Hi, a couple of things may be causing problems one you have many routers in your area that is a nightmare for linux wireless.

You should change your router encryption to wpa and not wep or mixed mode like wpa/wpa2 because it is easier for ubuntu to connect too.
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```
Try this command again and post the results.

I made one little mistake in the code that caused it to fail, I am sorry about that.
Thanks

---

### Post by tuxy-love on 2012-01-01
Broadcoms wireless cards are the least desirable cards on the market. To put it bluntly they don't work. Broadcom did announce they were changing this not that long ago. However the driver is still early early stages and it is unknown if the company is sticking to or how well they will support the project. I'm surprised someone reported they have a card that works at all. Except for NDISWrapper (which tends to be flaky and causes stability issues) broadcom is largely unsupported.

I had a similar issue with Intel although more or less for slightly different reasons. It basically didn't work with some distributions. This was because it required proprietary firmware. I got a card with an atheros chipset from [www.thinkpenguin.com]("http://www.thinkpenguin.com") and now everything works great across distributions and operating systems.

---

### Post by wildmanne39 on 2012-01-01
Hi, this is not true almost all broadcom cards work in ubuntu.

I have had a broadcom card work in all versions of ubuntu for about five years, way back before this time ndiswrapper was needed. 

Since I have been working in networking broadcom is one of the easiest and most reliable cards I have helped people get going, but there are exceptions to this some people have other issues or they get a new card that linux has not had time to make a driver for yet.
Thanks

---

### Post by DGINSD on 2012-01-01
> **wildmanne39 said:**
> Hi, a couple of things may be causing problems one you have many routers in your area that is a nightmare for linux wireless.

You should change your router encryption to wpa and not wep or mixed mode like wpa/wpa2 because it is easier for ubuntu to connect too.
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
```
Try this command again and post the results.

I made one little mistake in the code that caused it to fail, I am sorry about that.
Thanks

Try it again when I get another drop out or just now?

---

### Post by DGINSD on 2012-01-01
> **wildmanne39 said:**
> Hi, this is not true almost all broadcom cards work in ubuntu.

I have had a broadcom card work in all versions of ubuntu for about five years, way back before this time ndiswrapper was needed. 

Since I have been working in networking broadcom is one of the easiest and most reliable cards I have helped people get going, but there are exceptions to this some people have other issues or they get a new card that linux has not had time to make a driver for yet.
Thanks

Yeah I can confirm this the other computer I was using before this also had a broadcom card and it worked flawlessly.

---

### Post by wildmanne39 on 2012-01-01
Hi, when you get a drop out.
Thanks

---

### Post by DGINSD on 2012-01-01
Ok strange thing, I logged into my wireless router set it up to do WPA instead of WEP Ubuntu connected like a champ easy piezy. But on my wife's Windoz XP turd, it wouldn't accept the 64 character  passcode, so I had to switch out of the dell wireless utility and change to let Windoz manage the connection. The Dell utility wanted a 63 character password. My daughter is having trouble connecting her I-touch as well, so I'm curious if the portable apple products can connect to a WPA network

---

### Post by wildmanne39 on 2012-01-01
Hi, my daughters ipod connects to my wpa2, and wpa2 is the best for linux if you have that option but not wpa/wpa2 if you have the option of wpa2 only use it.

You probably just need to change the settings in the windows unit and the ipod to use wpa2 or wpa encryption.

My wives window 7 connects to my wpa2 also but there may be a difference between xp and win7 since xp is old.
Thanks

---

### Post by DGINSD on 2012-01-01
> **wildmanne39 said:**
> Hi, my daughters ipod connects to my wpa2, and wpa2 is the best for linux if you have that option but not wpa/wpa2 if you have the option of wpa2 only use it.

You probably just need to change the settings in the windows unit and the ipod to use wpa2 or wpa encryption.

My wives window 7 connects to my wpa2 also but there may be a difference between xp and win7 since xp is old.
Thanks

Got 'em all connected, my daughter pasted some extra stuff when she tried to enter and connect. So far no drop outs for me.:D

---

### Post by wildmanne39 on 2012-01-01
Hi, I will keep my fingers crossed.
Good Luck

---

### Post by Dlambert on 2012-01-01
Please mark as solved if the problem is resolved. Haha Rhyme :D

---

### Post by DGINSD on 2012-01-01
K just have had numerous drop outs heres the out put of the output of the modified last command.

```
david@david-Latitude-X300:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -e etork -e wlan | tail -n55
[sudo] password for david: 
Jan  1 18:21:09 david-Latitude-X300 kernel: [15741.072721] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 1)
Jan  1 18:21:09 david-Latitude-X300 wpa_supplicant[1088]: CTRL-EVENT-DISCONNECTED bssid=00:26:5a:ce:6b:a5 reason=2
Jan  1 18:21:09 david-Latitude-X300 kernel: [15741.272183] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 2)
Jan  1 18:21:09 david-Latitude-X300 kernel: [15741.472169] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 3)
Jan  1 18:21:10 david-Latitude-X300 kernel: [15741.672171] wlan0: authentication with 00:26:5a:ce:6b:a5 timed out
Jan  1 18:21:10 david-Latitude-X300 kernel: [15741.680309] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat ipt_MASQUERADE xt_DSCP nf_conntrack_irc rfcomm bnep bluetooth binfmt_misc arc4 joydev b43 iptable_nat iptable_mangle mac80211 snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm ppdev ip6t_LOG xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 snd_seq_midi ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_addrtype xt_state snd_rawmidi ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast cfg80211 nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 snd_seq_midi_event nf_conntrack_ftp nf_conntrack iptable_filter ip_tables x_tables pcmcia snd_seq i915 dcdbas snd_timer yenta_socket pcmcia_rsrc pcmcia_core snd_seq_device snd psmouse drm_kms_helper drm serio_raw soundcore snd_page_alloc irda shpchp i2c_algo_bit parport_pc crc_ccitt video lp parport tg3 firewire_ohci usb_storage uas ssb firewire_core crc_itu_t
Jan  1 18:21:10 david-Latitude-X300 kernel: [15741.680560]  [<c1047a22>] warn_slowpath_common+0x72/0xa0
Jan  1 18:21:10 david-Latitude-X300 kernel: [15741.680647]  [<c1047a72>] warn_slowpath_null+0x22/0x30
Jan  1 18:21:16 david-Latitude-X300 wpa_supplicant[1088]: Trying to authenticate with 00:26:5a:ce:6b:a5 (SSID='SITH_LAIR' freq=2437 MHz)
Jan  1 18:21:16 david-Latitude-X300 kernel: [15748.140331] wlan0: direct probe to 00:26:5a:ce:6b:a5 (try 1/3)
Jan  1 18:21:16 david-Latitude-X300 kernel: [15748.340186] wlan0: direct probe to 00:26:5a:ce:6b:a5 (try 2/3)
Jan  1 18:21:16 david-Latitude-X300 kernel: [15748.540154] wlan0: direct probe to 00:26:5a:ce:6b:a5 (try 3/3)
Jan  1 18:21:17 david-Latitude-X300 kernel: [15748.740156] wlan0: direct probe to 00:26:5a:ce:6b:a5 timed out
Jan  1 18:21:21 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): roamed from BSSID 00:26:5A:CE:6B:A5 (SITH_LAIR) to (none) ((none))
Jan  1 18:21:23 david-Latitude-X300 NetworkManager[1022]: <warn> (wlan0): link timed out.
Jan  1 18:21:23 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
Jan  1 18:21:23 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): deactivating device (reason 'supplicant-timeout') [11]
Jan  1 18:21:23 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1982
Jan  1 18:21:23 david-Latitude-X300 avahi-daemon[1016]: Withdrawing address record for 192.168.0.102 on wlan0.
Jan  1 18:21:23 david-Latitude-X300 avahi-daemon[1016]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Jan  1 18:21:23 david-Latitude-X300 avahi-daemon[1016]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  1 18:21:24 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) starting connection 'SITH_LAIR'
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0/wireless): connection 'SITH_LAIR' has security, and secrets exist.  No new secrets needed.
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan  1 18:21:25 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  1 18:21:26 david-Latitude-X300 wpa_supplicant[1088]: Trying to authenticate with 00:26:5a:ce:6b:a5 (SSID='SITH_LAIR' freq=2437 MHz)
Jan  1 18:21:26 david-Latitude-X300 wpa_supplicant[1088]: Trying to associate with 00:26:5a:ce:6b:a5 (SSID='SITH_LAIR' freq=2437 MHz)
Jan  1 18:21:26 david-Latitude-X300 kernel: [15758.528304] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 1)
Jan  1 18:21:26 david-Latitude-X300 kernel: [15758.529892] wlan0: authenticated
Jan  1 18:21:26 david-Latitude-X300 kernel: [15758.531202] wlan0: associate with 00:26:5a:ce:6b:a5 (try 1)
Jan  1 18:21:26 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  1 18:21:26 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jan  1 18:21:27 david-Latitude-X300 kernel: [15758.728070] wlan0: associate with 00:26:5a:ce:6b:a5 (try 2)
Jan  1 18:21:27 david-Latitude-X300 kernel: [15758.928078] wlan0: associate with 00:26:5a:ce:6b:a5 (try 3)
Jan  1 18:21:27 david-Latitude-X300 kernel: [15759.128068] wlan0: association with 00:26:5a:ce:6b:a5 timed out
Jan  1 18:21:27 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jan  1 18:21:32 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan  1 18:21:33 david-Latitude-X300 wpa_supplicant[1088]: Trying to authenticate with 00:26:5a:ce:6b:a5 (SSID='SITH_LAIR' freq=2437 MHz)
Jan  1 18:21:33 david-Latitude-X300 kernel: [15765.560367] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 1)
Jan  1 18:21:33 david-Latitude-X300 wpa_supplicant[1088]: CTRL-EVENT-DISCONNECTED bssid=00:26:5a:ce:6b:a5 reason=2
Jan  1 18:21:33 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan  1 18:21:34 david-Latitude-X300 kernel: [15765.760203] wlan0: authenticate with 00:26:5a:ce:6b:a5 (try 2)
Jan  1 18:21:34 david-Latitude-X300 kernel: [15765.761712] wlan0: authenticated
Jan  1 18:22:25 david-Latitude-X300 NetworkManager[1022]: <warn> Activation (wlan0/wireless): association took too long.
Jan  1 18:22:25 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan  1 18:22:25 david-Latitude-X300 NetworkManager[1022]: <warn> Activation (wlan0/wireless): asking for new secrets
Jan  1 18:22:25 david-Latitude-X300 NetworkManager[1022]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
david@david-Latitude-X300:~$ 

```

---

### Post by DGINSD on 2012-01-01
So I connected wired to see if there was a reply yet an with the LAN connected  it continued to try to connect to the wireless connection. I had to go into the NM drop down and disconnect.

When just on wireless it's connecting and then disconnecting over and over again and about every 5th cycle of this my network key confirmation window pops up.

---

### Post by wildmanne39 on 2012-01-01
Hi, does your router have setting for N speed if so change it to b/g and see if that fixes the problem because your old wireless card does not support N speed.
Thanks

---

### Post by DGINSD on 2012-01-02
No setting for N on the router.

---

### Post by wildmanne39 on 2012-01-02
Hi, I only have one idea left and it is because of the error messages from the last information posted.

You can install wicd and then get rid of network manager but you must install wicd first, you are having issues with connection because of wpa-supplicant and some of the time it can be solved by installing wicd. 

Go to software center and install wicd then run this command to get rid of network manager.
```
sudo apt-get purge network-manager network-manager-gnome
```
Wicd will not show up in the top panel so you will need to click on it in dash to set up your wireless.
Thanks

---

### Post by DGINSD on 2012-01-02
Will I get some type of visual indicator of connected or not connected after setting up wicd, cause that could be frustrating if the drop outs continue.

I did have 2 non-default check  boxes checked in I belive edit connections IPV4 and IPV6, after I unchecked both of these the drop out stopped, but I haven't been around my computer very long.

---

### Post by wildmanne39 on 2012-01-02
Hi, I do not know if it will pop up on the screen and tell you that your are disconnected or not.

Yes ipv6 should be set to ignore here are screen shots of mine.
Thanks

---

### Post by DGINSD on 2012-01-02
The check box at the button that says "require IPv4 addressing for this connection to complete" I had that checked and also the IPv6 tab was set to "automatic (DHCP) addresses only" and the checkbox for "require IPv6 addressing for this connection to complete" was selected. Could this of been my problem?

Out of curiosity shouldn't wireless connections disconnect when a LAN line is plugged in by default, or do I need to set something up to assure that happens?

---

### Post by wildmanne39 on 2012-01-02
Hi, yes that is most like the problem now, I do not believe that was the only problem, we have got rid of the other problems by changing drivers and setting the dns server to google.

I noticed in 11.04 and above it stays connected and I just leave mine connected but if you do not like it that way you can disable it by unchecking enable wireless if that is available in wicd.
Thanks

---

### Post by sadaruwan12 on 2012-01-03
I have Lenovo B560 and the WiFi is from Atheros we had a same type of issue getting our WiFi signal dropped for no reason.

So what I did was I change the "Chanel Number" from auto to 8 and it solved my issue 'cos in my office environment there are so many WiFi signals available.

Try this as well and also after doing that we didn't had a single drop.

---

### Post by DGINSD on 2012-01-03
> **sadaruwan12 said:**
> I have Lenovo B560 and the WiFi is from Atheros we had a same type of issue getting our WiFi signal dropped for no reason.

So what I did was I change the "Chanel Number" from auto to 8 and it solved my issue 'cos in my office environment there are so many WiFi signals available.

Try this as well and also after doing that we didn't had a single drop.

How do I change the Channel? Do I have to  do that in the routers settings? Should I check to see whats the most least used channel in my area and use that one?

---

### Post by DGINSD on 2012-01-03
K I figured out how to change the channel, I used channel 2 as no one in my area is using that one. There's also the setting for 802.11 mode it was set to "802.11b only" I changed it to "mixed 802.11g and 802.11b" I'm pretty sure my wifi card supports 802.11g but even if it doesn't that setting should be ok, right?

Also there's this section for WPA here's how I have it set.
```

WPA
Use WPA or WPA2 mode to achieve a balance of strong security and
best compatibility. This mode uses WPA for legacy clients while
maintaining higher security with stations that are WPA2 capable.
Also the strongest cipher that the client supports will be used
For best security, use WPA2 Only mode. This mode uses AES(CCMP)
cipher and legacy stations are not allowed access with WPA
security. For maximum compatibility, use WPA Only. This mode uses
TKIP cipher. Some gaming and legacy devices work only in this
mode.

[COLOR="Red"]To achieve better wireless performance use WPA2 Only
security mode (or in other words AES cipher).[/COLOR]

WPA Mode :	                    (auto WPA or WPA2)
Cipher Type :	                     TKIP
Group Key Update Interval :	    (3600)

```

The part in red about the cipher should I change it to AES, might that help or hinder?

Is there anything else I should or can change to get things working better?

Also If I want to go back to network manager instead of Wicd, do I just reinstall network manager and purge Wicd.

---

### Post by sadaruwan12 on 2012-01-03
> **DGINSD said:**
> How do I change the Channel? Do I have to  do that in the routers settings? Should I check to see whats the most least used channel in my area and use that one?

It's in your router and no there no easy way to test for channels bets use 6-11 any one in between is ok.

---

### Post by wildmanne39 on 2012-01-03
Hi DGINSD, > "802.11b only" I changed it to "mixed 802.11g and 802.11b" I'm pretty sure my wifi card supports 802.11gYes it supports b/g mode.
> The part in red about the cipher should I change it to AES, might that help or hinder?
Yes give it a try AES is good if you have that option do it, you can always change it back if you need too.
> Is there anything else I should or can change to get things working better?
Not that I know of.
> Also If I want to go back to network manager instead of Wicd, do I just reinstall network manager and purge Wicd. Yes
Thanks

---

### Post by DGINSD on 2012-01-04
Excellent thank you for your help, the drop outs have stopped, I'm just going to give Network Manager one more go and see if it was Wicd that got things fixed or the settings changes and I should be all good.

---

### Post by wildmanne39 on 2012-01-04
Hi, your welcome! that is good to hear.
Enjoy

---


---
title: "WiFi Problem in Ubuntu 14.04 LTS"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by nico.walter on 2014-04-26
Hi, I bought a Toshiba Laptop c55-A5100 with windows 8. After a few days of use without any problem, i erased windows and installed ubuntu 14.04 LTS.
Since that day, mi wifi isn't working properly, i've tried a lot of things searching in the internet but couldn't fix the problem. Basically, I can connect to my network, but it runs very slow or doesn't work. The wired connection is working fine.

Thanks, and sorry for my bad english.

---

### Post by tfrue on 2014-04-27
Click on the Wireless Script in my signature and run the script on your Toshiba, and post the output here in [code] tags. Thanks

---

### Post by squakie on 2014-04-27
You may be interested in my post [here]("http://ubuntuforums.org/showthread.php?t=2219952") - I haven't had a chance to try what was posted, but it sounds like the same issue.

I should mention - mine is also a Toshiba C55 series.

---

### Post by squakie on 2014-04-27
Just tried the reply in my thread that I pointed you to and things are MUCH MUCH MUCH better!

---

### Post by nico.walter on 2014-04-27
Thanks you both for the help. I downloaded the script and here is the result: [s][http://pastebin.ubuntu.   /7346612/]("http://pastebin.ubuntu.com/7346612/")[/s]  (Admin Note: Script is below.)


Also, i tried the other solution, but when i type "make" i get a lot of error messages.

```
[COLOR=#000000][FONT=Verdana][TABLE="class: pastetable"]
[TR]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux nicolas-Satellite-C55-A 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: alx
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0181]
    Kernel driver in use: rtl8188ee

##### lsusb #####

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a52 Importek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"maria"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:926   Missed beacon:0

##### route #####

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [maria] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Turco house:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    BravardPG2:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WEP
    bravard_pg:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WEP
    Fibertel WiFi182:Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    FliaDan:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP
    *E.V*:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    *maria:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    fati-red:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    8A:              Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    D-LINK:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    AMOR:            Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 44 WEP
    telecentro123:   Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA
    HUGO:            Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    aee864:          Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    Telecentro-3618: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Consultorio:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    Telecentro-b97a: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    Wireless-N:      Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37

  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             200.49.130.40
    DNS:             200.42.4.203

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"maria"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000480fa9df7b
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 00056D61726961
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Turco house"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012df395c418
                    Extra: Last beacon: 1272ms ago
                    IE: Unknown: 000B547572636F20686F757365
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Fibertel WiFi182"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000adbc770186
                    Extra: Last beacon: 436ms ago
                    IE: Unknown: 0010466962657274656C2057694669313832
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010180105
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"fati-red"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002809d76159
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 0008666174692D726564
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD130050F204104A00011010440001021041000100
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000023127A
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"bravard_pg"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e0aea7187
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 000A627261766172645F7067
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010080
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180206F0000000
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FliaDan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018ebae7183
                    Extra: Last beacon: 92ms ago
                    IE: Unknown: 0007466C696144616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"*E.V*"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000012df698118b
                    Extra: Last beacon: 1796ms ago
                    IE: Unknown: 00052A452E562A
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD050010180102
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HUGO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012df36d218c
                    Extra: Last beacon: 3120ms ago
                    IE: Unknown: 00044855474F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000015ba03183
                    Extra: Last beacon: 1760ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000
          Cell 10 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Telecentro-b97a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a1d885aff
                    Extra: Last beacon: 2516ms ago
                    IE: Unknown: 000F54656C6563656E74726F2D62393761
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Wi-Fi Arnet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012df5757660
                    Extra: Last beacon: 1232ms ago
                    IE: Unknown: 000B57692D46692041726E6574
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0507000100FE7FBF01
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180217F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 12 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"D-LINK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012df6fa815c
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0006442D4C494E4B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070100000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0500001F127A
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070100000000000000000000000000000000000000
                    IE: Unknown: DD07000C4307000000
          Cell 13 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"BravardPG2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e08cf6a45
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000A42726176617264504732
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
          Cell 14 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Fibertel WiFi773"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001143fb8718f
                    Extra: Last beacon: 712ms ago
                    IE: Unknown: 0010466962657274656C2057694669373733
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 15 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"AMOR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006b5fd1582
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 0004414D4F52
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### lsmod #####

rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626489  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     1B8E36556B30AA35325F55D
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

##### modules #####

lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x1969:0x1090 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.435506] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   10.435590] rtl8188ee 0000:02:00.0: irq 43 for MSI/MSI-X
[   10.712179] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.712345] rtlwifi: wireless switch is on
[   14.750695] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.909667] wlan0: authenticate with <MAC address removed>
[   38.909790] wlan0: direct probe to <MAC address removed> (try 1/3)
[   39.111206] wlan0: direct probe to <MAC address removed> (try 2/3)
[   39.315448] wlan0: direct probe to <MAC address removed> (try 3/3)
[   39.519651] wlan0: authentication with <MAC address removed> timed out
[   40.457456] wlan0: authenticate with <MAC address removed>
[   40.467019] wlan0: send auth to <MAC address removed> (try 1/3)
[   40.469865] wlan0: authenticated
[   40.469996] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   40.472708] wlan0: associate with <MAC address removed> (try 1/3)
[   40.475104] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[   40.475724] wlan0: associated
[   40.475736] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1143.086225] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 2773.316818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2775.047632] wlan0: authenticate with <MAC address removed>
[ 2775.047745] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 2775.249046] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 2775.453283] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2775.455713] wlan0: authenticated
[ 2775.456010] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2775.457289] wlan0: associate with <MAC address removed> (try 1/3)
[ 2775.459720] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2775.459890] wlan0: associated
[ 2775.459929] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2829.464579] wlan0: Connection to AP <MAC address removed> lost
[ 2830.823936] wlan0: authenticate with <MAC address removed>
[ 2830.832620] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2830.836112] wlan0: authenticated
[ 2830.836254] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2830.838318] wlan0: associate with <MAC address removed> (try 1/3)
[ 2830.840673] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2830.840831] wlan0: associated
[ 2830.840839] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2838.769929] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 2840.110973] wlan0: authenticate with <MAC address removed>
[ 2840.118695] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2840.122553] wlan0: authenticated
[ 2840.122704] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2840.124286] wlan0: associate with <MAC address removed> (try 1/3)
[ 2840.128019] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2840.128180] wlan0: associated
[ 2845.519211] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2848.264644] wlan0: authenticate with <MAC address removed>
[ 2848.665876] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2848.769891] wlan0: send auth to <MAC address removed> (try 2/3)
[ 2848.873910] wlan0: send auth to <MAC address removed> (try 3/3)
[ 2848.977993] wlan0: authentication with <MAC address removed> timed out
[ 2850.820762] wlan0: authenticate with <MAC address removed>
[ 2850.829696] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2850.831195] wlan0: authenticated
[ 2850.831380] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2850.835215] wlan0: associate with <MAC address removed> (try 1/3)
[ 2850.838279] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2850.838444] wlan0: associated
[ 2858.792004] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 2872.630326] wlan0: authenticate with <MAC address removed>
[ 2872.639502] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2872.641889] wlan0: authenticated
[ 2872.642039] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2872.645202] wlan0: associate with <MAC address removed> (try 1/3)
[ 2872.650178] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2872.650342] wlan0: associated
[ 2873.254896] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2873.292705] wlan0: authenticate with <MAC address removed>
[ 2873.292824] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2873.295189] wlan0: authenticated
[ 2873.295317] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2873.297625] wlan0: associate with <MAC address removed> (try 1/3)
[ 2873.301383] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2873.301534] wlan0: associated
[ 2881.316746] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 2895.120832] wlan0: authenticate with <MAC address removed>
[ 2895.129998] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2895.132318] wlan0: authenticated
[ 2895.132443] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2895.135711] wlan0: associate with <MAC address removed> (try 1/3)
[ 2895.138330] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2895.138506] wlan0: associated
[ 2913.451859] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 2914.313390] wlan0: authenticate with <MAC address removed>
[ 2914.322337] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2914.323869] wlan0: authenticated
[ 2914.324074] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2914.328016] wlan0: associate with <MAC address removed> (try 1/3)
[ 2914.335161] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2914.335328] wlan0: associated
[ 2914.335354] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2922.261795] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 2923.603610] wlan0: authenticate with <MAC address removed>
[ 2923.612492] wlan0: send auth to <MAC address removed> (try 1/3)
[ 2923.614825] wlan0: authenticated
[ 2923.614961] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 2923.618016] wlan0: associate with <MAC address removed> (try 1/3)
[ 2923.620892] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 2923.621047] wlan0: associated
[ 3057.187056] wlan0: Connection to AP <MAC address removed> lost
[ 3058.583662] wlan0: authenticate with <MAC address removed>
[ 3058.591087] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3058.594400] wlan0: authenticated
[ 3058.594552] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3058.596767] wlan0: associate with <MAC address removed> (try 1/3)
[ 3058.599136] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 3058.599287] wlan0: associated
[ 3058.599295] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3410.682324] wlan0: Connection to AP <MAC address removed> lost
[ 3412.041653] wlan0: authenticate with <MAC address removed>
[ 3412.050373] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3412.058653] wlan0: authenticated
[ 3412.058900] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3412.060074] wlan0: associate with <MAC address removed> (try 1/3)
[ 3412.062393] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 3412.062551] wlan0: associated
[ 3420.112448] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 3421.471685] wlan0: authenticate with <MAC address removed>
[ 3421.481667] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3421.486461] wlan0: authenticated
[ 3421.486644] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3421.490206] wlan0: associate with <MAC address removed> (try 1/3)
[ 3421.499524] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 3421.499689] wlan0: associated
[ 3425.909026] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3428.639240] wlan0: authenticate with <MAC address removed>
[ 3429.101395] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3429.203115] wlan0: send auth to <MAC address removed> (try 2/3)
[ 3429.307192] wlan0: send auth to <MAC address removed> (try 3/3)
[ 3429.411243] wlan0: authentication with <MAC address removed> timed out
[ 3431.250670] wlan0: authenticate with <MAC address removed>
[ 3431.259302] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3431.260838] wlan0: authenticated
[ 3431.260966] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3431.264401] wlan0: associate with <MAC address removed> (try 1/3)
[ 3431.292586] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 3431.292750] wlan0: associated
[ 4945.680519] wlan0: Connection to AP <MAC address removed> lost
[ 4953.311538] wlan0: authenticate with <MAC address removed>
[ 4953.320464] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4953.522359] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4953.726578] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4953.930823] wlan0: authentication with <MAC address removed> timed out
[ 4989.506827] wlan0: authenticate with <MAC address removed>
[ 4989.506921] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4989.707668] wlan0: direct probe to <MAC address removed> (try 2/3)
[ 4989.911930] wlan0: direct probe to <MAC address removed> (try 3/3)
[ 4990.116162] wlan0: authentication with <MAC address removed> timed out
[ 4992.351783] wlan0: authenticate with <MAC address removed>
[ 4992.360962] wlan0: direct probe to <MAC address removed> (try 1/3)
[ 4992.562910] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4994.028617] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4995.041763] wlan0: authentication with <MAC address removed> timed out
[ 5007.573377] wlan0: authenticate with <MAC address removed>
[ 5007.582475] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5007.609806] wlan0: authenticated
[ 5007.609961] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5007.612139] wlan0: associate with <MAC address removed> (try 1/3)
[ 5007.615140] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5007.615312] wlan0: associated
[ 5007.615346] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5015.252720] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5016.123628] wlan0: authenticate with <MAC address removed>
[ 5016.132132] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5016.135353] wlan0: authenticated
[ 5016.135513] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5016.137853] wlan0: associate with <MAC address removed> (try 1/3)
[ 5016.146083] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5016.146245] wlan0: associated
[ 5065.512954] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5068.332111] wlan0: authenticate with <MAC address removed>
[ 5068.774318] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5068.878113] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5068.982262] wlan0: send auth to <MAC address removed> (try 3/3)
[ 5069.086380] wlan0: authentication with <MAC address removed> timed out
[ 5070.029328] wlan0: authenticate with <MAC address removed>
[ 5070.037802] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5070.041590] wlan0: authenticated
[ 5070.041874] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5070.043466] wlan0: associate with <MAC address removed> (try 1/3)
[ 5070.045868] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5070.046046] wlan0: associated
[ 5070.046061] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5078.035954] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 5079.375775] wlan0: authenticate with <MAC address removed>
[ 5079.384494] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5079.386621] wlan0: authenticated
[ 5079.386888] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5079.390137] wlan0: associate with <MAC address removed> (try 1/3)
[ 5079.397033] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5079.397196] wlan0: associated
[ 5087.348644] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 5088.690375] wlan0: authenticate with <MAC address removed>
[ 5088.699031] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5088.800905] wlan0: send auth to <MAC address removed> (try 2/3)
[ 5088.905017] wlan0: send auth to <MAC address removed> (try 3/3)
[ 5088.906725] wlan0: authenticated
[ 5088.907040] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5088.909005] wlan0: associate with <MAC address removed> (try 1/3)
[ 5088.911688] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5088.911861] wlan0: associated
[ 5093.340699] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5093.375062] wlan0: authenticate with <MAC address removed>
[ 5093.375173] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5093.376667] wlan0: authenticated
[ 5093.376799] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5093.378111] wlan0: associate with <MAC address removed> (try 1/3)
[ 5093.386037] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5093.386220] wlan0: associated
[ 5101.360284] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 5115.164216] wlan0: authenticate with <MAC address removed>
[ 5115.173339] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5115.174809] wlan0: authenticated
[ 5115.175046] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5115.179028] wlan0: associate with <MAC address removed> (try 1/3)
[ 5115.184924] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5115.185093] wlan0: associated
[ 5118.370562] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5118.403882] wlan0: authenticate with <MAC address removed>
[ 5118.404003] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5118.405513] wlan0: authenticated
[ 5118.405639] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5118.406680] wlan0: associate with <MAC address removed> (try 1/3)
[ 5118.412244] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5118.412409] wlan0: associated
[ 5126.391119] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 5140.252706] wlan0: authenticate with <MAC address removed>
[ 5140.261932] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5140.269904] wlan0: authenticated
[ 5140.270077] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5140.271701] wlan0: associate with <MAC address removed> (try 1/3)
[ 5140.281546] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5140.281705] wlan0: associated
[ 5143.399734] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5143.438701] wlan0: authenticate with <MAC address removed>
[ 5143.438820] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5143.440611] wlan0: authenticated
[ 5143.440774] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5143.443644] wlan0: associate with <MAC address removed> (try 1/3)
[ 5143.448049] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5143.448220] wlan0: associated
[ 5151.416344] wlan0: deauthenticated from <MAC address removed> (Reason: 16)
[ 5165.209364] wlan0: authenticate with <MAC address removed>
[ 5165.218503] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5165.221233] wlan0: authenticated
[ 5165.221408] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5165.224195] wlan0: associate with <MAC address removed> (try 1/3)
[ 5165.231409] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5165.231603] wlan0: associated
[ 5168.425844] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 5217.806135] wlan0: authenticate with <MAC address removed>
[ 5217.814637] wlan0: send auth to <MAC address removed> (try 1/3)
[ 5217.816268] wlan0: authenticated
[ 5217.816472] rtl8188ee 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 5217.820261] wlan0: associate with <MAC address removed> (try 1/3)
[ 5217.822766] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 5217.822929] wlan0: associated

########## wireless info END ############
[/COLOR][/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]
[Download as text]("http://pastebin.ubuntu.com/7346612/plain/")
```

I tried again with the code Squakie suggested and it seems to work well. Do you recommend any kind of test to decide if the problem is solved?
Thanks!

---

### Post by wildmanne39 on 2014-04-27
Just use your connection for about 24 hours and if you have no issues then mark this thread solved.Thanks

---

### Post by nico.walter on 2014-04-27
The problem isn't totally solved. I've been using it for a couple of hours and the connection isn't normal yet. Although, today is the first time I can download a torrent normally.

I think this might be related with the low speed between the router and my laptop (18 mb/s).Thanks

---

### Post by tfrue on 2014-04-28
Reading through the result you posted, you seem to keep loosing connection to your router, having to re-authenticate, connect, and start all over.

This line was particularly interesting to me,which WEP/TKIP may be the problem for you having to re-authenticate.
wlan0: disabling HT/VHT due to WEP/TKIP use

If you can, you should try and set up WPA2 within your router; for one, better security. Also, make sure that your firmware in your router is up-to-date by going to the support page of the manufacture of your router. You could run the script again so I could have an updated view of what is going on, but using WPA2 should also help.

---

### Post by nico.walter on 2014-04-28
But this problem is happening with all the networks I connect. Do you think that will change anything?

---

### Post by tfrue on 2014-04-29
I think it would be a great first step, my next thought would be to do a live boot into Ubuntu and see how your connections is then and record the driver module loaded and compare it to the one that is loaded when you do a normal boot.

---

### Post by nico.walter on 2014-05-04
The problem is solved. Thanks to all of you!

I solved it using this [http://ubuntuforums.org/showthread.php?t=2219952](http://ubuntuforums.org/showthread.php?t=2219952)

---

### Post by squakie on 2014-05-05
You do realize that is my post that I pointed you to in my first post?  You claimed afterward is wasn't always working.  All you did was repeat the same procedure.  Did you do something different the first time?

---

### Post by nico.walter on 2014-05-19
Sorry, i've been very busy and I forgot to answer. Yes, i know it was your post, i did the procedure only one time, and after 48 hours the problem was solved. 

I pasted the link again to make it more visible.

Thank you very much for solving my problem.

---

### Post by tgurbanov on 2014-05-25
Hi, I have very same problem. Wi-fi connection periodically drops. Here is the output of [wifi script]("http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385"): [http://pastebin.ubuntu.com/7516214/](http://pastebin.ubuntu.com/7516214/) . Can anybody help me?

---

### Post by Lucian_Ilea on 2014-09-13
Hello,

I am experiencing similar problems with my Dell XPS 15z. I can connect to any wireless networks (and it stays connected) but it never works (cannot load any webpage). 

The result of the Wireless Script is:

```



########## wireless info START ##########


Report from: 13 Sep 2014 10:12 EEST +0300


Script from: 05 Sep 2014 22:42 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop #####


Ubuntu


##### lspci #####


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5221]
    Kernel driver in use: iwlwifi


06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Dell Device [1028:0446]
    Kernel driver in use: atl1c


##### lsusb #####


Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 003: ID 0451:8044 Texas Instruments, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 24ae:2002  
Bus 003 Device 005: ID 04d9:a015 Holtek Semiconductor, Inc. 
Bus 003 Device 004: ID 045e:076f Microsoft Corp. 
Bus 003 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:642a Microdia 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info #####


##### rfkill #####


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #####


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
mxm_wmi                13021  1 nouveau
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  3 dell_wmi,mxm_wmi,nouveau


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::868f:69ff:feac:c349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5117 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:5844773 (5.8 MB)  TX bytes:738486 (738.4 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.84  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8a53:2eff:fe6f:dec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87243311 (87.2 MB)  TX bytes:3329029 (3.3 MB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Zen"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC addr Zen>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:203   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: wlan0  [Zen] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK_404840:  Infra, <MAC addr TP-LINK_404840>, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    *Zen:            Infra, <MAC addr Zen>, Freq 2422 MHz, Rate 54 Mb/s, Strength 83 WPA2
    TP-LINK_E2606E:  Infra, <MAC addr TP-LINK_E2606E>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.84
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iw reg get #####


country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels #####


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #####


Channel occupancy:


     1   WLAPs on   Frequency:2.422 GHz (Channel 3)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Zen>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:on
                    ESSID:"Zen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5b350f173
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos #####


[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512


[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)


##### module parameters #####


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1


##### /etc/modules #####


lp
rtc


##### blacklists #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


##### rc.local #####


exit 0


##### udev rules #####


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0091 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   10.570718] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   10.570996] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[   10.737109] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[   10.754282] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.754286] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.754287] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.754290] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[   10.754389] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   10.774255] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.624175] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   13.630758] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   13.905208] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   13.911737] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   14.009006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   17.298955] wlan0: authenticate with <MAC addr Zen>
[   17.303833] wlan0: send auth to <MAC addr Zen> (try 1/3)
[   17.305233] wlan0: authenticated
[   17.306727] wlan0: associate with <MAC addr Zen> (try 1/3)
[   17.308786] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[   17.314078] wlan0: associated
[   17.314114] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.635365] IPv6: wlan0: IPv6 duplicate address fe80::8a53:2eff:fe6f:dec detected!
[   49.030718] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=213.199.179.175 DST=192.168.1.84 LEN=173 TOS=0x00 PREC=0x00 TTL=53 ID=50126 DF PROTO=UDP SPT=40033 DPT=61738 LEN=153 
[   51.038157] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=213.199.179.175 DST=192.168.1.84 LEN=173 TOS=0x00 PREC=0x00 TTL=53 ID=50127 DF PROTO=UDP SPT=40033 DPT=61738 LEN=153 
[   55.034357] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=213.199.179.175 DST=192.168.1.84 LEN=173 TOS=0x00 PREC=0x00 TTL=53 ID=50128 DF PROTO=UDP SPT=40033 DPT=61738 LEN=153 
[  196.345473] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  199.660336] wlan0: authenticate with <MAC addr Zen>
[  199.664735] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  199.666035] wlan0: authenticated
[  199.669878] wlan0: associate with <MAC addr Zen> (try 1/3)
[  199.672073] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  199.674491] wlan0: associated
[  204.455657] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  207.796671] wlan0: authenticate with <MAC addr Zen>
[  207.801515] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  207.802999] wlan0: authenticated
[  207.804821] wlan0: associate with <MAC addr Zen> (try 1/3)
[  207.809631] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  207.813056] wlan0: associated
[  213.299731] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  216.636719] wlan0: authenticate with <MAC addr Zen>
[  216.642071] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  216.645032] wlan0: authenticated
[  216.648302] wlan0: associate with <MAC addr Zen> (try 1/3)
[  216.658429] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  216.664438] wlan0: associated
[  221.354480] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  224.658913] wlan0: authenticate with <MAC addr Zen>
[  224.662644] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  224.670557] wlan0: authenticated
[  224.675214] wlan0: associate with <MAC addr Zen> (try 1/3)
[  224.681884] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  224.685057] wlan0: associated
[  232.358821] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=64.233.164.188 DST=192.168.1.84 LEN=82 TOS=0x00 PREC=0x00 TTL=44 ID=45758 PROTO=TCP SPT=5228 DPT=53033 WINDOW=670 RES=0x00 ACK PSH URGP=0 
[  245.344899] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  248.646652] wlan0: authenticate with <MAC addr Zen>
[  248.651134] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  248.659241] wlan0: authenticated
[  248.663587] wlan0: associate with <MAC addr Zen> (try 1/3)
[  248.670397] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  248.674209] wlan0: associated
[  251.663139] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=64.233.164.188 DST=192.168.1.84 LEN=82 TOS=0x00 PREC=0x00 TTL=44 ID=45760 PROTO=TCP SPT=5228 DPT=53033 WINDOW=670 RES=0x00 ACK PSH URGP=0 
[  254.435103] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  257.764602] wlan0: authenticate with <MAC addr Zen>
[  257.767784] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  257.769201] wlan0: authenticated
[  257.771301] wlan0: associate with <MAC addr Zen> (try 1/3)
[  257.773511] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  257.776935] wlan0: associated
[  263.351625] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  265.616486] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  278.196738] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  278.203338] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  278.291064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  284.684162] wlan0: authenticate with <MAC addr Zen>
[  284.688706] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  284.690443] wlan0: authenticated
[  284.694180] wlan0: associate with <MAC addr Zen> (try 1/3)
[  284.696397] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  284.699083] wlan0: associated
[  284.699158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  284.938201] wlan0: deauthenticating from <MAC addr Zen> by local choice (reason=2)
[  284.946411] wlan0: authenticate with <MAC addr Zen>
[  284.950718] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  284.952905] wlan0: authenticated
[  284.954419] wlan0: associate with <MAC addr Zen> (try 1/3)
[  284.956618] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  284.958969] wlan0: associated
[  285.780014] IPv6: wlan0: IPv6 duplicate address fe80::8a53:2eff:fe6f:dec detected!
[  290.892500] wlan0: deauthenticating from <MAC addr Zen> by local choice (reason=3)
[  294.664138] wlan0: authenticate with <MAC addr Zen>
[  294.672370] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  294.674931] wlan0: authenticated
[  294.678717] wlan0: associate with <MAC addr Zen> (try 1/3)
[  294.680884] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  294.685179] wlan0: associated
[  295.541148] IPv6: wlan0: IPv6 duplicate address fe80::8a53:2eff:fe6f:dec detected!
[  299.439672] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  302.788795] wlan0: authenticate with <MAC addr Zen>
[  302.793741] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  302.799376] wlan0: authenticated
[  302.799797] wlan0: associate with <MAC addr Zen> (try 1/3)
[  302.805955] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  302.809593] wlan0: associated
[  307.441866] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  310.789802] wlan0: authenticate with <MAC addr Zen>
[  310.794465] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  310.796026] wlan0: authenticated
[  310.799709] wlan0: associate with <MAC addr Zen> (try 1/3)
[  310.801947] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  310.805892] wlan0: associated
[  316.440436] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  319.745419] wlan0: authenticate with <MAC addr Zen>
[  319.749930] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  319.751603] wlan0: authenticated
[  319.754864] wlan0: associate with <MAC addr Zen> (try 1/3)
[  319.757007] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  319.761078] wlan0: associated
[  326.461730] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  329.762647] wlan0: authenticate with <MAC addr Zen>
[  329.766792] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  329.777471] wlan0: authenticated
[  329.778365] wlan0: associate with <MAC addr Zen> (try 1/3)
[  329.783725] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  329.787842] wlan0: associated
[  334.500915] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  337.817517] wlan0: authenticate with <MAC addr Zen>
[  337.822479] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  337.829212] wlan0: authenticated
[  337.833254] wlan0: associate with <MAC addr Zen> (try 1/3)
[  337.846688] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  337.851193] wlan0: associated
[  342.471288] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  345.818969] wlan0: authenticate with <MAC addr Zen>
[  345.822348] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  345.928024] wlan0: send auth to <MAC addr Zen> (try 2/3)
[  345.929859] wlan0: authenticated
[  345.932037] wlan0: associate with <MAC addr Zen> (try 1/3)
[  345.937644] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  345.941487] wlan0: associated
[  347.555118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.95 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=54913 PROTO=TCP SPT=443 DPT=49403 WINDOW=350 RES=0x00 ACK FIN URGP=0 
[  348.362331] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.84 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=3206 PROTO=TCP SPT=443 DPT=34916 WINDOW=775 RES=0x00 ACK FIN URGP=0 
[  352.476589] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  355.851454] wlan0: authenticate with <MAC addr Zen>
[  355.855857] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  355.857378] wlan0: authenticated
[  355.859518] wlan0: associate with <MAC addr Zen> (try 1/3)
[  355.861660] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  355.865396] wlan0: associated
[  357.659380] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.84 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=3207 PROTO=TCP SPT=443 DPT=34916 WINDOW=775 RES=0x00 ACK FIN URGP=0 
[  365.525847] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=64.233.164.188 DST=192.168.1.84 LEN=186 TOS=0x00 PREC=0x00 TTL=44 ID=31937 PROTO=TCP SPT=443 DPT=51097 WINDOW=670 RES=0x00 ACK PSH URGP=0 
[  369.151663] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.95 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=57376 PROTO=TCP SPT=443 DPT=49397 WINDOW=350 RES=0x00 ACK FIN URGP=0 
[  369.343753] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.95 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=54915 PROTO=TCP SPT=443 DPT=49403 WINDOW=350 RES=0x00 ACK FIN URGP=0 
[  369.716578] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.84 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=3208 PROTO=TCP SPT=443 DPT=34916 WINDOW=775 RES=0x00 ACK FIN URGP=0 
[  375.375039] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.131 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=34466 PROTO=TCP SPT=80 DPT=52949 WINDOW=661 RES=0x00 ACK FIN URGP=0 
[  375.711619] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.131 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=34467 PROTO=TCP SPT=80 DPT=52949 WINDOW=661 RES=0x00 ACK FIN URGP=0 
[  376.223487] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.131 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=34468 PROTO=TCP SPT=80 DPT=52949 WINDOW=661 RES=0x00 ACK FIN URGP=0 
[  376.414640] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.95 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=57377 PROTO=TCP SPT=443 DPT=49397 WINDOW=350 RES=0x00 ACK FIN URGP=0 
[  376.616475] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=74.125.143.95 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=46 ID=54893 PROTO=TCP SPT=443 DPT=49403 WINDOW=350 RES=0x00 ACK FIN URGP=0 
[  382.482812] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  385.807065] wlan0: authenticate with <MAC addr Zen>
[  385.811388] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  385.812969] wlan0: authenticated
[  385.814046] wlan0: associate with <MAC addr Zen> (try 1/3)
[  385.816416] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  385.820390] wlan0: associated
[  387.753182] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=117 TOS=0x00 PREC=0x00 TTL=56 ID=46904 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK PSH URGP=0 
[  387.947890] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=97 TOS=0x00 PREC=0x00 TTL=56 ID=46905 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK PSH URGP=0 
[  388.130918] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=46906 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK FIN URGP=0 
[  388.330318] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=117 TOS=0x00 PREC=0x00 TTL=56 ID=46907 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK PSH URGP=0 
[  388.919499] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=117 TOS=0x00 PREC=0x00 TTL=56 ID=46908 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK PSH URGP=0 
[  389.884250] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=173.194.116.140 DST=192.168.1.84 LEN=117 TOS=0x00 PREC=0x00 TTL=56 ID=46909 PROTO=TCP SPT=443 DPT=55338 WINDOW=661 RES=0x00 ACK PSH URGP=0 
[  391.459530] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  394.763550] wlan0: authenticate with <MAC addr Zen>
[  394.768060] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  394.769866] wlan0: authenticated
[  394.773214] wlan0: associate with <MAC addr Zen> (try 1/3)
[  394.777217] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  394.781730] wlan0: associated
[  399.656146] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  402.951735] wlan0: authenticate with <MAC addr Zen>
[  402.959500] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  402.983993] wlan0: authenticated
[  402.988053] wlan0: associate with <MAC addr Zen> (try 1/3)
[  402.995001] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  402.998386] wlan0: associated
[  589.680846] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  592.983641] wlan0: authenticate with <MAC addr Zen>
[  592.988013] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  592.989484] wlan0: authenticated
[  592.990021] wlan0: associate with <MAC addr Zen> (try 1/3)
[  592.992300] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  592.996152] wlan0: associated
[  599.610317] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  602.887917] wlan0: authenticate with <MAC addr Zen>
[  602.890589] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  602.892355] wlan0: authenticated
[  602.894451] wlan0: associate with <MAC addr Zen> (try 1/3)
[  602.896812] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  602.900846] wlan0: associated
[  608.618034] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  611.888169] wlan0: authenticate with <MAC addr Zen>
[  611.892381] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  611.893956] wlan0: authenticated
[  611.898156] wlan0: associate with <MAC addr Zen> (try 1/3)
[  611.900360] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  611.903871] wlan0: associated
[  616.803990] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  620.106840] wlan0: authenticate with <MAC addr Zen>
[  620.109830] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  620.110570] wlan0: authenticated
[  620.113093] wlan0: associate with <MAC addr Zen> (try 1/3)
[  620.113982] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  620.118033] wlan0: associated
[  622.881571] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=89.123.118.243 DST=192.168.1.84 LEN=146 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=UDP SPT=30505 DPT=61738 LEN=126 
[  623.272251] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=109.99.82.187 DST=192.168.1.84 LEN=133 TOS=0x00 PREC=0x00 TTL=117 ID=20588 PROTO=UDP SPT=22257 DPT=61738 LEN=113 
[  625.094440] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=89.123.118.243 DST=192.168.1.84 LEN=146 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=UDP SPT=30505 DPT=61738 LEN=126 
[  626.048864] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=109.99.82.187 DST=192.168.1.84 LEN=133 TOS=0x00 PREC=0x00 TTL=117 ID=20589 PROTO=UDP SPT=22257 DPT=61738 LEN=113 
[  626.812106] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  630.108449] wlan0: authenticate with <MAC addr Zen>
[  630.112103] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  630.112804] wlan0: authenticated
[  630.113781] wlan0: associate with <MAC addr Zen> (try 1/3)
[  630.114591] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  630.117240] wlan0: associated
[  631.043126] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=157.56.52.12 DST=192.168.1.84 LEN=183 TOS=0x00 PREC=0x00 TTL=46 ID=9726 DF PROTO=UDP SPT=40020 DPT=61738 LEN=163 
[  631.921589] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=101.224.9.243 DST=192.168.1.84 LEN=142 TOS=0x00 PREC=0x00 TTL=110 ID=30892 PROTO=UDP SPT=7145 DPT=61738 LEN=122 
[  632.321066] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=213.47.237.74 DST=192.168.1.84 LEN=142 TOS=0x00 PREC=0x00 TTL=54 ID=15694 PROTO=UDP SPT=44379 DPT=61738 LEN=122 
[  634.057545] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=157.56.52.12 DST=192.168.1.84 LEN=183 TOS=0x00 PREC=0x00 TTL=46 ID=9727 DF PROTO=UDP SPT=40020 DPT=61738 LEN=163 
[  635.742101] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  639.053246] wlan0: authenticate with <MAC addr Zen>
[  639.057125] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  639.057802] wlan0: authenticated
[  639.061222] wlan0: associate with <MAC addr Zen> (try 1/3)
[  639.062186] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  639.065283] wlan0: associated
[  643.734796] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  647.033964] wlan0: authenticate with <MAC addr Zen>
[  647.038478] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  647.042796] wlan0: authenticated
[  647.043993] wlan0: associate with <MAC addr Zen> (try 1/3)
[  647.048205] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  647.051903] wlan0: associated
[  651.799712] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  655.118087] wlan0: authenticate with <MAC addr Zen>
[  655.124103] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  655.133450] wlan0: authenticated
[  655.134920] wlan0: associate with <MAC addr Zen> (try 1/3)
[  655.147714] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  655.152007] wlan0: associated
[  659.825730] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  663.127082] wlan0: authenticate with <MAC addr Zen>
[  663.130063] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  663.135705] wlan0: authenticated
[  663.137698] wlan0: associate with <MAC addr Zen> (try 1/3)
[  663.145506] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  663.149288] wlan0: associated
[  667.741820] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  671.046415] wlan0: authenticate with <MAC addr Zen>
[  671.051052] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  671.052286] wlan0: authenticated
[  671.056435] wlan0: associate with <MAC addr Zen> (try 1/3)
[  671.066984] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  671.070119] wlan0: associated
[  676.497635] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=91.208.120.100 DST=192.168.1.84 LEN=144 TOS=0x00 PREC=0x00 TTL=114 ID=24324 PROTO=UDP SPT=7621 DPT=61738 LEN=124 
[  676.684595] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  679.999231] wlan0: authenticate with <MAC addr Zen>
[  680.002551] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  680.005689] wlan0: authenticated
[  680.008030] wlan0: associate with <MAC addr Zen> (try 1/3)
[  680.013149] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  680.016672] wlan0: associated
[  680.538764] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC addr wlan0>:<MAC addr Zen>:08:00 SRC=157.56.52.12 DST=192.168.1.84 LEN=183 TOS=0x00 PREC=0x00 TTL=46 ID=9731 DF PROTO=UDP SPT=40020 DPT=61738 LEN=163 
[  684.868341] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  688.174711] wlan0: authenticate with <MAC addr Zen>
[  688.179571] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  688.182708] wlan0: authenticated
[  688.187013] wlan0: associate with <MAC addr Zen> (try 1/3)
[  688.192334] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  688.198777] wlan0: associated
[  692.772681] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  696.101263] wlan0: authenticate with <MAC addr Zen>
[  696.105947] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  696.107414] wlan0: authenticated
[  696.109732] wlan0: associate with <MAC addr Zen> (try 1/3)
[  696.115636] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  696.118601] wlan0: associated
[  702.769342] wlan0: deauthenticated from <MAC addr Zen> (Reason: 3)
[  706.052945] wlan0: authenticate with <MAC addr Zen>
[  706.057408] wlan0: send auth to <MAC addr Zen> (try 1/3)
[  706.058090] wlan0: authenticated
[  706.059364] wlan0: associate with <MAC addr Zen> (try 1/3)
[  706.060193] wlan0: RX AssocResp from <MAC addr Zen> (capab=0x411 status=0 aid=2)
[  706.064186] wlan0: associated


########## wireless info END ############

```

Thank you for your help!

---

### Post by Anna_Krassa on 2014-11-07
Hello tfrue, 

I got exactly the same problem as nico.walter in a HP machine. I run the wireless script you suggested and here are the results...

Appreciate your help. Thank you in advance.

> ```

########## wireless info START ##########

Report from: 07 Nov 2014 09:32 EET +0200

Booted last: 07 Nov 2014 09:11 EET +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:218f]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 0c45:7000 Microdia 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wl                   4207846  0 
lib80211               14381  1 wl
rtl8188ee              89677  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              630653  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  3 wl,mac80211,rtlwifi
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:580:95f8:cd00:9de1:8868:c72e:2bdf/64 Scope:Global
          inet6 addr: fe80::4a5a:b6ff:fe35:d576/64 Scope:Link
          inet6 addr: 2a02:580:95f8:cd00:4a5a:b6ff:fe35:d576/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34819 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38869999 (38.8 MB)  TX bytes:5544828 (5.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"conn-xDB66F9"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'conn-xDB66F9' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:256   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Speedport_W_724V_09071601_00_032A

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [conn-xDB66F9] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TVHALK:          Infra, <MAC 'TVHALK' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    TVHALK2:         Infra, <MAC 'TVHALK2' [AC6]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    vdslxtv:         Infra, <MAC 'vdslxtv' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    DIRECT-:         Infra, <MAC 'DIRECT-' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WEP
    HP-Print-28-LaserJet 1102: Infra, <MAC 'HP-Print-28-LaserJet 1102' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64
    *conn-xDB66F9:   Infra, <MAC 'conn-xDB66F9' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         2a02:580:95f8:cd00:9de1:8868:c72e:2bdf
    Prefix:          64
    Gateway:         fe80::20e:8fff:fedb:66f0

    Address:         2a02:580:95f8:cd00:4a5a:b6ff:fe35:d576
    Prefix:          64
    Gateway:         fe80::20e:8fff:fedb:66f0

    Address:         fe80::4a5a:b6ff:fe35:d576
    Prefix:          64
    Gateway:         fe80::20e:8fff:fedb:66f0

    DNS:             fe80::20e:8fff:fedb:66f0

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/conn-xDB66F9]] (600 root)
[connection] id=conn-xDB66F9 | type=802-11-wireless
[802-11-wireless] ssid=conn-xDB66F9 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RR1]] (600 root)
[connection] id=RR1 | type=802-11-wireless
[802-11-wireless] ssid=RR1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Athens (based on set time zone)

country GR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.467 GHz (Channel 12)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'conn-xDB66F9' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"conn-xDB66F9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001647229487b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'vdslxtv' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"vdslxtv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008cac9229e5
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-28-LaserJet 1102' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-28-LaserJet 1102"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007441d9e4f4
                    Extra: Last beacon: 8ms ago
          Cell 04 - Address: <MAC 'TVHALK' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TVHALK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004614c698fad
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC5]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000008ea7b230181
                    Extra: Last beacon: 14896ms ago
          Cell 06 - Address: <MAC 'TVHALK2' [AC6]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TVHALK2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013c663c046f
                    Extra: Last beacon: 14496ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-39-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[rtl8188ee]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     FA356D8EFD887B567263405
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=0
options rtl8192ce fwlps=0

[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  846.442648] wlan0: deauthenticating from <MAC 'conn-xDB66F9' [AC1]> by local choice (reason=2)
[  846.453109] wlan0: authenticate with <MAC 'conn-xDB66F9' [AC1]>
[  846.463383] wlan0: send auth to <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  846.465354] wlan0: authenticated
[  846.467249] wlan0: associate with <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  846.470687] wlan0: RX AssocResp from <MAC 'conn-xDB66F9' [AC1]> (capab=0x411 status=0 aid=2)
[  846.470858] wlan0: associated
[  890.845914] wlan0: Connection to AP <MAC 'conn-xDB66F9' [AC1]> lost
[  892.240591] wlan0: authenticate with <MAC 'conn-xDB66F9' [AC1]>
[  892.260044] wlan0: send auth to <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  892.261583] wlan0: authenticated
[  892.263727] wlan0: associate with <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  892.267215] wlan0: RX AssocResp from <MAC 'conn-xDB66F9' [AC1]> (capab=0x411 status=0 aid=2)
[  892.267400] wlan0: associated
[  899.423523] wlan0: Connection to AP <MAC 'conn-xDB66F9' [AC1]> lost
[  900.894335] wlan0: authenticate with <MAC 'conn-xDB66F9' [AC1]>
[  900.913718] wlan0: send auth to <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  900.915203] wlan0: authenticated
[  900.917329] wlan0: associate with <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  900.923387] wlan0: RX AssocResp from <MAC 'conn-xDB66F9' [AC1]> (capab=0x411 status=0 aid=2)
[  900.923557] wlan0: associated
[  918.103828] wlan0: Connection to AP <MAC 'conn-xDB66F9' [AC1]> lost
[  919.506350] wlan0: authenticate with <MAC 'conn-xDB66F9' [AC1]>
[  919.526151] wlan0: send auth to <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  919.527871] wlan0: authenticated
[  919.529547] wlan0: associate with <MAC 'conn-xDB66F9' [AC1]> (try 1/3)
[  919.532845] wlan0: RX AssocResp from <MAC 'conn-xDB66F9' [AC1]> (capab=0x411 status=0 aid=2)
[  919.533012] wlan0: associated

########## wireless info END ############


```

---

### Post by Baurzhan on 2015-01-25
Hello,
I have almost similar issue. Please, which code did you try in order to resolve your wifi poor signal?
I can't see any code that you mentioned here.
Thanks

---

### Post by Jeremy_Keasler on 2015-01-28
Having WIFI connection and quality issues.  The speed will degrade from 54 mb/s to 1 over a period of 10 min or so.  It jumps back up to full speed after a while, then starts degrading again.  Does anyone have any clue how I can fix this?
```


########## wireless info START ##########


Report from: 28 Jan 2015 23:07 EST -0500


Booted last: 28 Jan 2015 22:17 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:23:46 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Inspiron 9400 Laptop [1028:01cd]
	Kernel driver in use: b44


0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Intel Corporation Device [8086:1020]
	Kernel driver in use: iwl3945


##### lsusb #############################


Bus 001 Device 035: ID 05c6:6764 Qualcomm, Inc. 
Bus 001 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
dell_laptop            17808  0 
mac80211              546067  2 iwl3945,iwlegacy
dcdbas                 14448  1 dell_laptop
cfg80211              409394  3 iwl3945,iwlegacy,mac80211
wmi                    18673  1 dell_wmi
ssb                    51854  1 b44


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fea6:2f55/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:214821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:310379159 (310.3 MB)  TX bytes:14232372 (14.2 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"HOME-5FF6"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HOME-5FF6' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:65   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home.network


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [HOME-5FF6] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    WIN_ac39:        Infra, <MAC 'WIN_ac39' [AC30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    *HOME-5FF6:      Infra, <MAC 'HOME-5FF6' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 66 WPA WPA2
    BryMon0927:      Infra, <MAC 'BryMon0927' [AC26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    HOME-7B1C:       Infra, <MAC 'HOME-7B1C' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    WIN_f965:        Infra, <MAC 'WIN_f965' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    HOME-792C-2.4:   Infra, <MAC 'HOME-792C-2.4' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    HOME-792C-5:     Infra, <MAC 'HOME-792C-5' [AC34]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Howard's Wi-Fi Network: Infra, <MAC 'Howard's Wi-Fi Network' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    NotForSale:      Infra, <MAC 'NotForSale' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    brymon:          Infra, <MAC 'brymon' [AC29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    HOME-0C30:       Infra, <MAC 'HOME-0C30' [AC20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    HOME-E6B6-2.4:   Infra, <MAC 'HOME-E6B6-2.4' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    NETGEAR03:       Infra, <MAC 'NETGEAR03' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    WIN_eb73:        Infra, <MAC 'WIN_eb73' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Itty Bitty:      Infra, <MAC 'Itty Bitty' [AC23]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA2
    HOME-7EC2:       Infra, <MAC 'HOME-7EC2' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    DIRECT-roku-180-1B4BA2: Infra, <MAC 'DIRECT-roku-180-1B4BA2' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    HOME-92C6-2.4:   Infra, <MAC 'HOME-92C6-2.4' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    HP-Print-FF-Officejet Pro 8600: Infra, <MAC 'HP-Print-FF-Officejet Pro 8600' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    97RDSS50:        Infra, <MAC '97RDSS50' [AC24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    OrangeSpruce:    Infra, <MAC 'OrangeSpruce' [AC25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    WIN_93e4:        Infra, <MAC 'WIN_93e4' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    WIN_08aa:        Infra, <MAC 'WIN_08aa' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    WIN_5f7b:        Infra, <MAC 'WIN_5f7b' [AC33]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    Howard's Wi-Fi Network: Infra, <MAC 'Howard's Wi-Fi Network' [AN29]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA2
    WIN_b2ea:        Infra, <MAC 'WIN_b2ea' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2


  IPv4 Settings:
    Address:         10.0.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1


    DNS:             75.75.75.75
    DNS:             75.75.76.76


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HOME-5FF6]] (600 root)
[connection] id=HOME-5FF6 | type=802-11-wireless
[802-11-wireless] ssid=HOME-5FF6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlan0     24 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      12   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      14   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.805 GHz (Channel 161)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME-5FF6' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"HOME-5FF6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e76a33e2d
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WIN_f965' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"WIN_f965"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d9e9ecae33
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000184c7ca1180
                    Extra: Last beacon: 224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002756244180
                    Extra: Last beacon: 6148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HOME-7B1C' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"HOME-7B1C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c5d9ca729
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c5d9cb79e
                    Extra: Last beacon: 72ms ago
          Cell 07 - Address: <MAC 'HOME-7EC2' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"HOME-7EC2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002362ce5dee3
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'xfinitywifi' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002362ce5e552
                    Extra: Last beacon: 72ms ago
          Cell 09 - Address: <MAC 'HOME-0D76' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-0D76"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f9b581ceb
                    Extra: Last beacon: 6124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f9b5825a6
                    Extra: Last beacon: 6120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'xfinitywifi' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f9b5cd916
                    Extra: Last beacon: 5812ms ago
          Cell 12 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c5da1ba54
                    Extra: Last beacon: 5800ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'WIN_b2ea' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WIN_b2ea"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005f555a8453
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC '' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000260f737180
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'HOME-92C6-2.4' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-92C6-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026945f9180
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Howard's Wi-Fi Network' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Howard's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b7a5dfb0be
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'NotForSale' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NotForSale"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000184c78831bb
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'HOME-792C-2.4' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-792C-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000260f71e180
                    Extra: Last beacon: 264ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'WIN_eb73' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"WIN_eb73"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000021e2314319e
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'HOME-0C30' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HOME-0C30"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006faea32197
                    Extra: Last beacon: 5768ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC21]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006faea32a52
                    Extra: Last beacon: 5768ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'xfinitywifi' [AC22]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006faea3314e
                    Extra: Last beacon: 5764ms ago
          Cell 23 - Address: <MAC 'Itty Bitty' [AC23]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Itty Bitty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017da9be3aa0
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC '97RDSS50' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"97RDSS50"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b50b45357
                    Extra: Last beacon: 4244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'OrangeSpruce' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"OrangeSpruce"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005cd22f9c3a
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'BryMon0927' [AC26]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BryMon0927"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aebaa245b1
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC '' [AC27]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aeba9cdf8a
                    Extra: Last beacon: 5528ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC '' [AC28]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aebaa7d2f3
                    Extra: Last beacon: 4808ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'brymon' [AC29]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"brymon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e4e738c715
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'WIN_ac39' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"WIN_ac39"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018afcd6cd47
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC '' [AC31]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002aebaa7c32f
                    Extra: Last beacon: 4812ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC '' [AC32]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000026945952d2
                    Extra: Last beacon: 672ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'WIN_5f7b' [AC33]>
                    Channel:11lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WIN_5f7b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000030553c76a2
                    Extra: Last beacon: 1668ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'HOME-792C-5' [AC34]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"HOME-792C-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000260f11003b
                    Extra: Last beacon: 424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwl3945]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     63597F7C72B07A97B142DC2
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)


[iwlegacy]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     A847A747E4E6066D74E1D6A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:5E:E8:B6:65:D0:55:58:A1:DE:E8:E3:1B:F1:6E:B8:DF:8F:D8
sig_hashalgo:   sha512


##### module parameters #################


[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1


[iwlegacy]
bt_coex_active: Y
led_mode: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


coretemp


coretemp


coretemp


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/garmin-forerunner-tools.conf]
blacklist garmin_gps


[/etc/modprobe.d/iwl3945.conf]
options iwl3495 swcrypto=0


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8812au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[ 2511.492090] ieee80211 phy0: wlan0: No probe response from AP <MAC 'HOME-5FF6' [AC1]> after 500ms, disconnecting.
[ 2513.633010] wlan0: authenticate with <MAC 'HOME-5FF6' [AC1]>
[ 2513.634992] wlan0: send auth to <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2513.636855] wlan0: authenticated
[ 2513.640466] wlan0: associate with <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2513.650426] wlan0: RX AssocResp from <MAC 'HOME-5FF6' [AC1]> (capab=0x411 status=0 aid=3)
[ 2513.651719] wlan0: associated
[ 2631.504110] ieee80211 phy0: wlan0: No probe response from AP <MAC 'HOME-5FF6' [AC1]> after 500ms, disconnecting.
[ 2633.701822] wlan0: authenticate with <MAC 'HOME-5FF6' [AC1]>
[ 2633.704385] wlan0: send auth to <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2633.706195] wlan0: authenticated
[ 2633.708188] wlan0: associate with <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2633.714293] wlan0: RX AssocResp from <MAC 'HOME-5FF6' [AC1]> (capab=0x411 status=0 aid=3)
[ 2633.715648] wlan0: associated
[ 2751.492069] ieee80211 phy0: wlan0: No probe response from AP <MAC 'HOME-5FF6' [AC1]> after 500ms, disconnecting.
[ 2753.681429] wlan0: authenticate with <MAC 'HOME-5FF6' [AC1]>
[ 2753.684220] wlan0: send auth to <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2753.688626] wlan0: authenticated
[ 2753.692830] wlan0: associate with <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2753.706252] wlan0: RX AssocResp from <MAC 'HOME-5FF6' [AC1]> (capab=0x411 status=0 aid=3)
[ 2753.709131] wlan0: associated
[ 2870.500063] ieee80211 phy0: wlan0: No probe response from AP <MAC 'HOME-5FF6' [AC1]> after 500ms, disconnecting.
[ 2872.694747] wlan0: authenticate with <MAC 'HOME-5FF6' [AC1]>
[ 2872.703175] wlan0: send auth to <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2872.706205] wlan0: authenticated
[ 2872.708046] wlan0: associate with <MAC 'HOME-5FF6' [AC1]> (try 1/3)
[ 2872.713695] wlan0: RX AssocResp from <MAC 'HOME-5FF6' [AC1]> (capab=0x411 status=0 aid=3)
[ 2872.715066] wlan0: associated


########## wireless info END ############



```

---

### Post by agazordelaluz on 2015-07-15
wifi drivers in ubuntu are too bad, i have a similar problem with my laptop MSI, the wifi connection is down all time, 2 minutes, it is hard use ubuntu whit these wireless drivers.

---

### Post by Geoffrey_Arndt on 2015-07-15
Recommend that via a new, separate thread, you should provide the model of your MSI, and the type of network chips - is it using broadcom, intel, atheros, realtek, etc.   You will have to check the manufacturer specifications or run other software like Belarc Advisor to find out these details.   Also, you can run some commands from the ubuntu terminal to find detail information such as "sudo lshw".    

Sometimes it is not the drivers at fault, but the settings the user has created to connect (such as the type of security, etc.)

*****************

One last point, there are many threads in these forums about very inexpensive ($10.00 usd) usb-internet-adapters such as the _Panda Ultra 150n_ (just search for it on Amazon or similar sites).   Just plug it in and it works - finds your network, then you have to type in your password and you're done.

---

### Post by Dhivin on 2015-11-13
I am using a Dell Lattitude laptop.Please help me.

```
#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

SCRIPTDATE="2015-09-27 02:34 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"

MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
IFACEMATCHES="(wlan[0-9]|eth[0-9])"
DMESGMATCHES="(firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"

DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"

NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")
DEC2BI=({0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1}{0..1})
DEC2HEX=($(printf "%02x " {0..255}))

export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"

if [ -t 0 ]; then
    DIALOGAPP="terminal"
    DIALOGBREAK=" "
    TERMOUT="yes"
elif [ -x /usr/bin/zenity ]; then
    DIALOGAPP="zenity"
    DIALOGBREAK="\n"
elif [ -x /usr/bin/kdialog ]; then
    DIALOGAPP="kdialog"
    DIALOGBREAK="\n"
else
    exit 1
fi

if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
    GKSUDO="yes"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
    KDESUDO="yes"
    KDESUDOCMT=" needs administrative privileges. Please enter your password."
fi

dialog_info () {
    case $DIALOGAPP in
    terminal)
        printf "%b\n" "$1"
        ;;
    zenity)
        zenity --info --text="$1"
        ;;
    kdialog)
        kdialog --msgbox "$1"
        ;;
    esac
}

dialog_error () {
    case $DIALOGAPP in
    terminal)
        printf "%b\n" "$1" >&2
        ;;
    zenity)
        zenity --error --text="$1"
        ;;
    kdialog)
        kdialog --error "$1"
        ;;
    esac
}

dialog_question () {
    case $DIALOGAPP in
    terminal)
        local INPUT
        read -r -p "$1 [Y/n]: " INPUT
        echo "${INPUT,,}"
        ;;
    zenity)
        zenity --question --text="$1" || echo "no"
        ;;
    kdialog)
        kdialog --yesno "$1" || echo "no"
        ;;
    esac
}

ip6-mac () {
    for MAC in "$@"; do
    OCT1BI=${DEC2BI[0x${MAC:0:2}]}
    OCT1BI7=$((${OCT1BI:6:1} - 1))
    OCT1BIM="${OCT1BI:0:6}${OCT1BI7#-}${OCT1BI:7}"
    IP6S+=${IP6S:+$'\n'}"${DEC2HEX[2#$OCT1BIM]}${MAC:3:2}:${MAC:6:2}ff:fe${MAC:9:2}:${MAC:12:2}${MAC:15:2}"
    done
    sed 's/\(^\|:\)0\+\([[:alnum:]]\)/\1\2/g;s/^\([0:]\+\)/\\(::\\|\1\\)/' <<< "$IP6S"
}

exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
    exit 1
    }
}
exec 2>&1

printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Booted last: %s\n\n" "$LASTBOOTDT"
printf "Script from: %s\n" "$SCRIPTDATE"

printf "\n##### release ###########################\n\n"
lsb_release -idrc

printf "\n##### kernel ############################\n\n"
uname -srvmpio
echo
sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline

printf "\n##### desktop ###########################\n\n"
if [ -n "$DESKTOP_SESSION" ]; then
    DESKTOP="$DESKTOP_SESSION"
else
    DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
    DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    printf "\nCould not be determined.\n"
fi

printf "\n##### lspci #############################\n\n"
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

printf "\n##### lsusb #############################\n\n"
lsusb

printf "\n##### PCMCIA card info ##################\n\n"
if [ -x /sbin/pccardctl ]; then
    pccardctl info
else
    echo "'pccardctl' is not installed (package \"pcmciautils\")."
fi

printf "\n##### rfkill ############################\n\n"
rfkill list all

printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"

printf "\n##### interfaces ########################\n\n"
sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### ifconfig ##########################\n\n"
IFCONFIG=$(ifconfig -a)
sed '/^lo /,/^$/d' <<< "$IFCONFIG"
IFACESETH=($(sed -n 's/^\([^ ]\+\)[ ]\+Link encap:Ethernet.*/\1/p' <<< "$IFCONFIG"))
if (( ${#IFACESETH[@]} > 0 )); then
    IFETHMATCHES=${IFACESETH[@]}
    IFACEMATCHES="($IFACEMATCHES|(${IFETHMATCHES// /|}))"
fi

printf "\n##### iwconfig ##########################\n\n"
iwconfig

printf "\n##### route #############################\n\n"
route -n

printf "\n##### resolv.conf #######################\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### network managers ##################\n\n"
printf "Installed:\n\n"
for NETMGRNR in "${!NETMGRPATHS[@]}"; do
    if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
    NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
    fi
done
printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
NETMGRMATCHES=${NETMGRMATCHES// |/|}
NETMGRMATCHES="(${NETMGRMATCHES#|})"
printf "\nRunning:\n\n"
ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"

printf "\n##### NetworkManager info ###############\n\n"
if [ -x /usr/bin/nm-tool ]; then
    nm-tool
elif [ -x /usr/bin/nmcli ]; then
    nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
    echo
    nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
else
    echo "NetworkManager is not installed (package \"network-manager\")."
fi

printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### NetworkManager profiles ###########\n\n"
if [ -d /etc/NetworkManager/system-connections ]; then
    if [ -n "$SUDO" ]; then
    trap "" 2 3
    NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
        ORIGIFS="$IFS"
        IFS=$'\n'
        for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
        NMWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
        NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
        NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
        done
        IFS="$ORIGIFS"
        sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
    else
        printf "\nAcquisition of admin privileges failed.\n"
    fi
    else
    echo "No way to acquire admin privileges found."
    fi
else
    echo "No NetworkManager profiles found."
fi

printf "\n##### iw reg get ########################\n\n"
if [ -x /sbin/iw ]; then
    if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
    REGION=$(cat /etc/timezone)
    printf "Region: %s (based on set time zone)\n\n" "$REGION"
    fi
    echo "$IWREGGET"
else
    echo "'iw' is not installed (package \"iw\")."
fi

printf "\n##### iwlist channels ###################\n\n"
if [ -x /sbin/iwlist ]; then
    iwlist chan
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### iwlist scan #######################\n\n"
if [ -x /sbin/iwlist ]; then
    if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
    trap 2 3
    if [ "$SUDOSUCCESS" = "yes" ]; then
        if [[ $IWLISTSCAN = *Frequency:* ]]; then
        printf "Channel occupancy:\n\n"
        grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
        echo
        fi
        grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
    else
        printf "\nAcquisition of admin privileges failed.\n"
    fi
    else
    echo "No way to acquire admin privileges found."
    fi
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi

printf "\n##### module infos ######################\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done

printf "\n##### module parameters #################\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
    MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
    printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done

printf "\n##### /etc/modules ######################\n\n"
grep -v '^#' /etc/modules

printf "\n##### modprobe options ##################\n\n"
for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
    MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
    if [ -n "$MODPROBEOPTS" ]; then
    printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
    fi
done

printf "\n##### rc.local ##########################\n\n"
grep -v '^#' /etc/rc.local

printf "\n##### pm-utils ##########################\n\n"
for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
    PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
    if [ -n "$PMUTFLCONT" ]; then
    PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
    printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
    fi
done

printf "\n##### udev rules ########################\n\n"
for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
    printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done

printf "\n##### dmesg #############################\n\n"
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$IFACEMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'

printf "\n########## wireless info END ############\n\n"

exec 2>&4 4>&-
exec 1>&3 3>&-

##### MAC address masking #####

RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'

ORIGIFS="$IFS"
IFS=$'\n'

IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFCONFIG"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFCONFIG"))
IFACESIP6S=($(ip6-mac "${IFACESMACS[@]}"))

WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h; /^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$IWLISTSCAN"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$IWLISTSCAN"))
WLAPSIWLIP6S=($(ip6-mac "${WLAPSIWLMACS[@]}"))

WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))
WLAPSNMIP6S=($(ip6-mac "${WLAPSNMMACS[@]}"))

IFS="$ORIGIFS"

for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]-address}>;I;"
    MACMASKSED+=" /${IFACESIP6S[$IFACENR]}/ s;${IFACESIP6S[$IFACENR]/#\\(::/\(};<IP6 ${IFACESIDS[$IFACENR]-from MAC}>;I;"
done

for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSIWLIP6S[$WLAPIWLNR]}/ s;${WLAPSIWLIP6S[$WLAPIWLNR]/#\\(::/\(};<IP6 ${WLAPSIWLIDS[$WLAPIWLNR]-from MAC}>;I;"
done

for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]-address}>;I;"
    MACMASKSED+=" /${WLAPSNMIP6S[$WLAPNMNR]}/ s;${WLAPSNMIP6S[$WLAPNMNR]/#\\(::/\(};<IP6 ${WLAPSNMIDS[$WLAPNMNR]-from MAC}>;I;"
done

sed "$MACMASKSED /\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"

##### The End #####

dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"

if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
    dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
    dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
fi

if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
    PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
    if [[ ! $PASTEBIN =~ ^no?$ ]]; then
    PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
    if [ "$PASTESUCCESS" = "yes" ]; then
        dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
    else
        if [ -n "$PASTERESULT" ]; then
        dialog_error "${TERMOUT+\n}Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
        else
        dialog_error "${TERMOUT+\n}Pastebin failed, no error message given.${TERMOUT+\n}"
        fi
    fi
    else
    echo
    fi
fi
```

---

### Post by wildmanne39 on 2015-11-16
Hello, first you posted the actual script itself and not the file it created, also no one has received help in this thread in a long time so please start your own thread with a descriptive title about the issue you are having and attach the file created by the wireless script.
Thanks

---


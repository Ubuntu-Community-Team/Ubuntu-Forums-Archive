---
title: "Ubuntu 14.04 LTS connection keeps dropping"
date: 2014-06-09
forum: New to Ubuntu
---

### Post by gijs2 on 2014-06-09
Hi,

Every ones in a while my connection drops and then my pages just wont load.
It's not my connections because the same thing happends on my work.

```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux Gijs 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
	Subsystem: Hewlett-Packard Company Device [103c:2163]
	Kernel driver in use: r8169


##### lsusb #####


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 05c8:0361 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 014: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


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


wlan0     IEEE 802.11bgn  ESSID:"TP-LINK_99F562"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC address removed>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [TP-LINK_99F562] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    VGV7519B99CE5:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    VGV75191674C5:   Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    123WiFi:         Infra, <MAC address removed>, Freq 2472 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Thomson0F024A:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    Thomson0EF3F2:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    UPC243087066:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 90 WPA2
    UPC0042658:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    UPC012553:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    UPC WifiSpots:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    City_Bar:        Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA
    UPC WifiSpots:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    *TP-LINK_99F562: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 76 WPA2
    kvyb798th763cgh4589ft7u89b7j654h: Infra, <MAC address removed>, Freq 2462 MHz, Rate 11 Mb/s, Strength 100 WPA


  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_99F562"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000284aa16d976
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000E54502D4C494E4B5F393946353632
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 331AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1608071500000000000000000000000000000000000000
                    IE: Unknown: 341608071500000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD990050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E10240003382E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"UPC243087066"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d2fffc7e
                    Extra: Last beacon: 3484ms ago
                    IE: Unknown: 000C555043323433303837303636
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0103FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000022127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 07064E4C20010D10
                    IE: Unknown: DDA70050F204104A0001101044000102103B00010310470010BC329E001DD811B286015CA39DC1A7281021001A43656C656E6F20436F6D6D756E69636174696F6E2C20496E632E1023001743656C656E6F20576972656C65737320415020322E344710240006434C313830301042000831323334353637381054000800060050F20400011011000C43656C656E6F4150322E344710080002210C103C0001011049000600372A000120
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"VGV7519B99CE5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006cecdfaac5b
                    Extra: Last beacon: 4200ms ago
                    IE: Unknown: 000D56475637353139423939434535
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6C0017FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030030127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A00011010440001021041000100103B0001031047001000000000000000030000849CA6B99CE51021000B436F72706F726174696F6E1023000B564756373531394B5732321024000B30322E30302E31333076321042000A413331313030363336301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: 07064E4C20010D10
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006742683707
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"UPC0042658"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006742683f7f
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000A55504330303432363538
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180207F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"UPC012553"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000056ee2b6377
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0009555043303132353533
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"VGV75191674C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007089acc216f
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 000D56475637353139313637344335
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 32040C183060
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: 05050001001005
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1608000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030088127A
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000056ee2b6d72
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D555043205769666953706F7473
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180213F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 09 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Thomson0F024A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000205d7639197
                    Extra: Last beacon: 1748ms ago
                    IE: Unknown: 000D54686F6D736F6E304630323441
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: DD09001018020000050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Thomson0EF3F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004a4a125e186
                    Extra: Last beacon: 9104ms ago
                    IE: Unknown: 000D54686F6D736F6E304546334632
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A0C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD2C0050F204104A0001101044000102105700010010470010C6841213A5D259088E40E716289A8757103C000101
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080000000000000000000000000000000000000000
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s
                    Mode:Master
                    Extra:tsf=0000189819d65974
                    Extra: Last beacon: 9672ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 01028284
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
          Cell 12 - Address: <MAC address removed>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"123WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001823ef80c5
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000731323357694669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"City_Bar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006772d180
                    Extra: Last beacon: 2784ms ago
                    IE: Unknown: 0008436974795F426172
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3404051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1604051B00000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00


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
          Current Frequency:2.447 GHz (Channel 8)


##### lsmod #####


rtl8188ee              89601  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                63475  2 rtl_pci,rtl8188ee
mac80211              626511  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              484040  2 mac80211,rtlwifi


##### modinfo #####


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     10DA7EAAC2C7F64E6AC7BAE
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9B7F19319428FF0EFE7E350
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
sig_hashalgo:   sha512


filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     27E91755814596D634B7709
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-27-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:43:25:CC:F7:B9:5B:51:F6:C1:19:38:0E:B9:33
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


# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[52058.340257] wlan0: associate with <MAC address removed> (try 1/3)
[52058.345581] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=105)
[52058.345704] wlan0: associated
[52418.124249] wlan0: authenticate with <MAC address removed>
[52418.134335] wlan0: direct probe to <MAC address removed> (try 1/3)
[52418.335428] wlan0: send auth to <MAC address removed> (try 2/3)
[52419.626695] wlan0: send auth to <MAC address removed> (try 3/3)
[52420.614123] wlan0: authentication with <MAC address removed> timed out
[52421.755162] wlan0: authenticate with <MAC address removed>
[52421.773683] wlan0: send auth to <MAC address removed> (try 1/3)
[52421.776414] wlan0: authenticated
[52421.777430] wlan0: associate with <MAC address removed> (try 1/3)
[52421.785603] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=105)
[52421.785746] wlan0: associated
[53017.790741] wlan0: authenticate with <MAC address removed>
[53017.800826] wlan0: send auth to <MAC address removed> (try 1/3)
[53017.805039] wlan0: authenticated
[53017.806045] wlan0: associate with <MAC address removed> (try 1/3)
[53017.812685] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[53017.812794] wlan0: associated
[53138.003844] wlan0: authenticate with <MAC address removed>
[53138.013937] wlan0: send auth to <MAC address removed> (try 1/3)
[53138.016528] wlan0: authenticated
[53138.022000] wlan0: associate with <MAC address removed> (try 1/3)
[53138.026102] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=126)
[53138.026210] wlan0: associated
[54097.473922] wlan0: authenticate with <MAC address removed>
[54097.484009] wlan0: send auth to <MAC address removed> (try 1/3)
[54097.485827] wlan0: authenticated
[54097.489452] wlan0: associate with <MAC address removed> (try 1/3)
[54097.494910] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[54097.495021] wlan0: associated
[54217.123503] wlan0: authenticate with <MAC address removed>
[54217.133590] wlan0: send auth to <MAC address removed> (try 1/3)
[54217.143338] wlan0: authenticated
[54217.146912] wlan0: associate with <MAC address removed> (try 1/3)
[54217.152191] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=68)
[54217.152306] wlan0: associated
[54337.057030] wlan0: authenticate with <MAC address removed>
[54337.067197] wlan0: send auth to <MAC address removed> (try 1/3)
[54337.068629] wlan0: authenticated
[54337.072221] wlan0: associate with <MAC address removed> (try 1/3)
[54337.076468] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=141)
[54337.076617] wlan0: associated
[55056.656450] wlan0: authenticate with <MAC address removed>
[55056.666555] wlan0: send auth to <MAC address removed> (try 1/3)
[55056.671034] wlan0: authenticated
[55056.671975] wlan0: associate with <MAC address removed> (try 1/3)
[55056.679593] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=70)
[55056.679702] wlan0: associated
[55416.452457] wlan0: authenticate with <MAC address removed>
[55416.462605] wlan0: send auth to <MAC address removed> (try 1/3)
[55416.464476] wlan0: authenticated
[55416.467934] wlan0: associate with <MAC address removed> (try 1/3)
[55416.472425] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=155)
[55416.472544] wlan0: associated
[56255.985703] wlan0: authenticate with <MAC address removed>
[56255.995814] wlan0: send auth to <MAC address removed> (try 1/3)
[56255.997527] wlan0: authenticated
[56256.001037] wlan0: associate with <MAC address removed> (try 1/3)
[56256.005073] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=69)
[56256.005191] wlan0: associated
[56616.070439] wlan0: authenticate with <MAC address removed>
[56616.080516] wlan0: direct probe to <MAC address removed> (try 1/3)
[56616.280700] wlan0: send auth to <MAC address removed> (try 2/3)
[56617.316039] wlan0: send auth to <MAC address removed> (try 3/3)
[56618.291564] wlan0: authentication with <MAC address removed> timed out
[56619.504902] wlan0: authenticate with <MAC address removed>
[56619.523047] wlan0: direct probe to <MAC address removed> (try 1/3)
[56619.726729] wlan0: send auth to <MAC address removed> (try 2/3)
[56620.290480] wlan0: send auth to <MAC address removed> (try 3/3)
[56621.289915] wlan0: authentication with <MAC address removed> timed out
[56622.434350] wlan0: authenticate with <MAC address removed>
[56622.453576] wlan0: send auth to <MAC address removed> (try 1/3)
[56622.455430] wlan0: authenticated
[56622.457192] wlan0: associate with <MAC address removed> (try 1/3)
[56622.463193] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=69)
[56622.463307] wlan0: associated
[56855.655932] wlan0: authenticate with <MAC address removed>
[56855.666064] wlan0: send auth to <MAC address removed> (try 1/3)
[56855.677827] wlan0: authenticated
[56855.679456] wlan0: associate with <MAC address removed> (try 1/3)
[56855.783435] wlan0: associate with <MAC address removed> (try 2/3)
[56855.790103] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[56855.790236] wlan0: associated
[56868.659423] wlan0: Connection to AP <MAC address removed> lost
[56869.289113] wlan0: authenticate with <MAC address removed>
[56869.308182] wlan0: send auth to <MAC address removed> (try 1/3)
[56869.310025] wlan0: authenticated
[56869.311910] wlan0: associate with <MAC address removed> (try 1/3)
[56869.317689] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=69)
[56869.317803] wlan0: associated
[56929.685914] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[56940.151164] rtlwifi: wireless switch is on
[56944.083957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[56945.787192] wlan0: authenticate with <MAC address removed>
[56946.183894] wlan0: send auth to <MAC address removed> (try 1/3)
[56946.186161] wlan0: authenticated
[56946.187816] wlan0: associate with <MAC address removed> (try 1/3)
[56946.193565] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[56946.193681] wlan0: associated
[56946.193711] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[57014.570216] wlan0: authenticate with <MAC address removed>
[57014.580418] wlan0: send auth to <MAC address removed> (try 1/3)
[57014.588721] wlan0: authenticated
[57014.589771] wlan0: associate with <MAC address removed> (try 1/3)
[57014.593899] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[57014.594015] wlan0: associated
[57077.811128] wlan0: authenticate with <MAC address removed>
[57077.821234] wlan0: send auth to <MAC address removed> (try 1/3)
[57077.824544] wlan0: authenticated
[57077.826630] wlan0: associate with <MAC address removed> (try 1/3)
[57077.830665] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[57077.830786] wlan0: associated
[57263.707631] wlan0: authenticate with <MAC address removed>
[57263.717785] wlan0: send auth to <MAC address removed> (try 1/3)
[57263.722307] wlan0: authenticated
[57263.727223] wlan0: associate with <MAC address removed> (try 1/3)
[57263.731244] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[57263.731356] wlan0: associated
[57503.294670] wlan0: authenticate with <MAC address removed>
[57503.304789] wlan0: send auth to <MAC address removed> (try 1/3)
[57503.308547] wlan0: authenticated
[57503.310074] wlan0: associate with <MAC address removed> (try 1/3)
[57503.314100] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[57503.314220] wlan0: associated
[57743.441085] wlan0: authenticate with <MAC address removed>
[57743.451190] wlan0: send auth to <MAC address removed> (try 1/3)
[57743.465375] wlan0: authenticated
[57743.468414] wlan0: associate with <MAC address removed> (try 1/3)
[57743.484667] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=15)
[57743.484792] wlan0: associated
[58103.240796] wlan0: authenticate with <MAC address removed>
[58103.251559] wlan0: send auth to <MAC address removed> (try 1/3)
[58103.253846] wlan0: authenticated
[58103.256283] wlan0: associate with <MAC address removed> (try 1/3)
[58103.262101] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[58103.262226] wlan0: associated
[58343.107435] wlan0: authenticate with <MAC address removed>
[58343.117527] wlan0: send auth to <MAC address removed> (try 1/3)
[58343.119311] wlan0: authenticated
[58343.122890] wlan0: associate with <MAC address removed> (try 1/3)
[58343.126972] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=22)
[58343.127081] wlan0: associated
[58582.694194] wlan0: authenticate with <MAC address removed>
[58582.704398] wlan0: send auth to <MAC address removed> (try 1/3)
[58582.705778] wlan0: authenticated
[58582.709635] wlan0: associate with <MAC address removed> (try 1/3)
[58582.713686] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[58582.713803] wlan0: associated
[58702.908996] wlan0: authenticate with <MAC address removed>
[58702.919105] wlan0: direct probe to <MAC address removed> (try 1/3)
[58703.122733] wlan0: send auth to <MAC address removed> (try 2/3)
[58704.158169] wlan0: send auth to <MAC address removed> (try 3/3)
[58705.157617] wlan0: authentication with <MAC address removed> timed out
[58706.318683] wlan0: authenticate with <MAC address removed>
[58706.337146] wlan0: direct probe to <MAC address removed> (try 1/3)
[58706.540870] wlan0: direct probe to <MAC address removed> (try 2/3)
[58706.744758] wlan0: direct probe to <MAC address removed> (try 3/3)
[58706.948644] wlan0: authentication with <MAC address removed> timed out
[58708.108745] wlan0: authenticate with <MAC address removed>
[58708.128175] wlan0: send auth to <MAC address removed> (try 1/3)
[58708.131248] wlan0: authenticated
[58708.131935] wlan0: associate with <MAC address removed> (try 1/3)
[58708.136076] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=6)
[58708.136187] wlan0: associated
[58822.564830] wlan0: authenticate with <MAC address removed>
[58822.574934] wlan0: send auth to <MAC address removed> (try 1/3)
[58822.576345] wlan0: authenticated
[58822.581238] wlan0: associate with <MAC address removed> (try 1/3)
[58822.589480] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=27)
[58822.589597] wlan0: associated
[58942.783619] wlan0: authenticate with <MAC address removed>
[58942.793724] wlan0: send auth to <MAC address removed> (try 1/3)
[58942.796013] wlan0: authenticated
[58942.797684] wlan0: associate with <MAC address removed> (try 1/3)
[58942.801762] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[58942.801886] wlan0: associated
[59102.483699] wlan0: Connection to AP <MAC address removed> lost
[59103.317813] wlan0: authenticate with <MAC address removed>
[59103.327991] wlan0: send auth to <MAC address removed> (try 1/3)
[59103.329475] wlan0: authenticated
[59103.332098] wlan0: associate with <MAC address removed> (try 1/3)
[59103.336095] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[59103.336204] wlan0: associated
[59422.227238] wlan0: authenticate with <MAC address removed>
[59422.237340] wlan0: direct probe to <MAC address removed> (try 1/3)
[59422.438679] wlan0: direct probe to <MAC address removed> (try 2/3)
[59422.642558] wlan0: direct probe to <MAC address removed> (try 3/3)
[59422.846490] wlan0: authentication with <MAC address removed> timed out
[59423.970348] wlan0: authenticate with <MAC address removed>
[59423.990095] wlan0: send auth to <MAC address removed> (try 1/3)
[59423.991576] wlan0: authenticated
[59423.993770] wlan0: associate with <MAC address removed> (try 1/3)
[59423.998723] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[59423.998855] wlan0: associated
[59662.374254] wlan0: authenticate with <MAC address removed>
[59662.384329] wlan0: send auth to <MAC address removed> (try 1/3)
[59662.389027] wlan0: authenticated
[59662.393173] wlan0: associate with <MAC address removed> (try 1/3)
[59662.398986] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=36)
[59662.399091] wlan0: associated
[60022.177480] wlan0: authenticate with <MAC address removed>
[60022.187606] wlan0: send auth to <MAC address removed> (try 1/3)
[60022.189148] wlan0: authenticated
[60022.193076] wlan0: associate with <MAC address removed> (try 1/3)
[60022.198728] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=8)
[60022.198857] wlan0: associated
[60262.040309] wlan0: authenticate with <MAC address removed>
[60262.050452] wlan0: send auth to <MAC address removed> (try 1/3)
[60262.052038] wlan0: authenticated
[60262.055643] wlan0: associate with <MAC address removed> (try 1/3)
[60262.059769] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=43)
[60262.059886] wlan0: associated
[60381.973403] wlan0: authenticate with <MAC address removed>
[60381.983481] wlan0: send auth to <MAC address removed> (try 1/3)
[60381.986502] wlan0: authenticated
[60381.988938] wlan0: associate with <MAC address removed> (try 1/3)
[60381.993031] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[60381.993157] wlan0: associated
[60621.839977] wlan0: authenticate with <MAC address removed>
[60621.850082] wlan0: direct probe to <MAC address removed> (try 1/3)
[60622.051544] wlan0: direct probe to <MAC address removed> (try 2/3)
[60622.255430] wlan0: direct probe to <MAC address removed> (try 3/3)
[60622.459276] wlan0: authentication with <MAC address removed> timed out
[60623.656498] wlan0: authenticate with <MAC address removed>
[60623.674809] wlan0: send auth to <MAC address removed> (try 1/3)
[60623.681305] wlan0: authenticated
[60623.682547] wlan0: associate with <MAC address removed> (try 1/3)
[60623.690687] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[60623.690806] wlan0: associated
[60741.497691] wlan0: authenticate with <MAC address removed>
[60741.507788] wlan0: send auth to <MAC address removed> (try 1/3)
[60741.509623] wlan0: authenticated
[60741.513222] wlan0: associate with <MAC address removed> (try 1/3)
[60741.517369] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[60741.517482] wlan0: associated
[60861.428220] wlan0: authenticate with <MAC address removed>
[60861.438404] wlan0: send auth to <MAC address removed> (try 1/3)
[60861.441645] wlan0: authenticated
[60861.442326] wlan0: associate with <MAC address removed> (try 1/3)
[60861.448140] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=49)
[60861.448264] wlan0: associated
[61581.034704] wlan0: authenticate with <MAC address removed>
[61581.044816] wlan0: send auth to <MAC address removed> (try 1/3)
[61581.051389] wlan0: authenticated
[61581.054094] wlan0: associate with <MAC address removed> (try 1/3)
[61581.061911] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[61581.062026] wlan0: associated
[61700.960397] wlan0: authenticate with <MAC address removed>
[61700.970511] wlan0: direct probe to <MAC address removed> (try 1/3)
[61701.171381] wlan0: send auth to <MAC address removed> (try 2/3)
[61702.490613] wlan0: send auth to <MAC address removed> (try 3/3)
[61703.466042] wlan0: authentication with <MAC address removed> timed out
[61704.563005] wlan0: authenticate with <MAC address removed>
[61704.581727] wlan0: send auth to <MAC address removed> (try 1/3)
[61704.583557] wlan0: authenticated
[61704.585424] wlan0: associate with <MAC address removed> (try 1/3)
[61704.591167] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[61704.591299] wlan0: associated
[62060.760049] wlan0: authenticate with <MAC address removed>
[62060.770230] wlan0: direct probe to <MAC address removed> (try 1/3)
[62060.971258] wlan0: direct probe to <MAC address removed> (try 2/3)
[62061.175167] wlan0: direct probe to <MAC address removed> (try 3/3)
[62061.379048] wlan0: authentication with <MAC address removed> timed out
[62062.468530] wlan0: authenticate with <MAC address removed>
[62062.486717] wlan0: send auth to <MAC address removed> (try 1/3)
[62062.489966] wlan0: authenticated
[62062.490339] wlan0: associate with <MAC address removed> (try 1/3)
[62062.495722] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[62062.495828] wlan0: associated
[63871.333882] wlan0: deauthenticated from <MAC address removed> (Reason: 2)
[63871.916484] wlan0: authenticate with <MAC address removed>
[63871.926556] wlan0: direct probe to <MAC address removed> (try 1/3)
[63872.127943] wlan0: direct probe to <MAC address removed> (try 2/3)
[63872.331871] wlan0: direct probe to <MAC address removed> (try 3/3)
[63872.535754] wlan0: authentication with <MAC address removed> timed out
[63874.338614] wlan0: authenticate with <MAC address removed>
[63874.355539] wlan0: direct probe to <MAC address removed> (try 1/3)
[63874.558593] wlan0: direct probe to <MAC address removed> (try 2/3)
[63874.762520] wlan0: direct probe to <MAC address removed> (try 3/3)
[63874.966404] wlan0: authentication with <MAC address removed> timed out
[63877.031043] wlan0: authenticate with <MAC address removed>
[63877.050235] wlan0: send auth to <MAC address removed> (try 1/3)
[63877.051629] wlan0: authenticated
[63877.053134] wlan0: associate with <MAC address removed> (try 1/3)
[63877.059025] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=100)
[63877.059136] wlan0: associated
[64219.563110] wlan0: authenticate with <MAC address removed>
[64219.573206] wlan0: direct probe to <MAC address removed> (try 1/3)
[64219.774639] wlan0: direct probe to <MAC address removed> (try 2/3)
[64219.978508] wlan0: direct probe to <MAC address removed> (try 3/3)
[64220.182349] wlan0: authentication with <MAC address removed> timed out
[64221.283415] wlan0: authenticate with <MAC address removed>
[64221.301892] wlan0: send auth to <MAC address removed> (try 1/3)
[64221.304450] wlan0: authenticated
[64221.305704] wlan0: associate with <MAC address removed> (try 1/3)
[64221.313040] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=100)
[64221.313146] wlan0: associated
[64363.301576] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[64365.853341] Modules linked in: usb_storage binfmt_misc ctr ccm rfcomm bnep bluetooth snd_hda_codec_hdmi intel_ips snd_hda_codec_realtek intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm uvcvideo rtl8188ee snd_hda_intel snd_hda_codec snd_hwdep videobuf2_vmalloc videobuf2_memops videobuf2_core rtl_pci rtlwifi videodev mac80211 i915 snd_pcm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel hp_wmi sparse_keymap snd_page_alloc aesni_intel snd_seq_midi snd_seq_midi_event snd_rawmidi aes_x86_64 lrw gf128mul drm_kms_helper cfg80211 snd_seq drm snd_seq_device glue_helper snd_timer ablk_helper mei_me cryptd snd mei hp_accel lis3lv02d joydev serio_raw input_polldev wmi i2c_algo_bit lpc_ich video soundcore mac_hid nls_iso8859_1 parport_pc ppdev lp parport hid_generic usbhid hid r8169 mii psmouse ahci libahci
[64367.011426] rtlwifi: wireless switch is on
[64370.074887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[64371.789516] wlan0: authenticate with <MAC address removed>
[64371.809909] wlan0: send auth to <MAC address removed> (try 1/3)
[64371.811648] wlan0: authenticated
[64371.812148] wlan0: associate with <MAC address removed> (try 1/3)
[64371.821097] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=115)
[64371.821214] wlan0: associated
[64371.821222] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[64371.832767] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[64371.866448] wlan0: authenticate with <MAC address removed>
[64371.876550] wlan0: send auth to <MAC address removed> (try 1/3)
[64371.881112] wlan0: authenticated
[64371.884125] wlan0: associate with <MAC address removed> (try 1/3)
[64371.890741] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=115)
[64371.890868] wlan0: associated
[64397.462836] wlan0: authenticate with <MAC address removed>
[64397.473220] wlan0: send auth to <MAC address removed> (try 1/3)
[64397.490334] wlan0: authenticated
[64397.493847] wlan0: associate with <MAC address removed> (try 1/3)
[64397.497890] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[64397.498005] wlan0: associated
[64440.444408] wlan0: authenticate with <MAC address removed>
[64440.454508] wlan0: send auth to <MAC address removed> (try 1/3)
[64440.458461] wlan0: authenticated
[64440.461946] wlan0: associate with <MAC address removed> (try 1/3)
[64440.465962] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=28)
[64440.466077] wlan0: associated
[64472.996984] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[64476.092969] rtlwifi: wireless switch is on
[64478.873073] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[64479.786761] wlan0: authenticate with <MAC address removed>
[64479.796863] wlan0: send auth to <MAC address removed> (try 1/3)
[64479.799679] wlan0: authenticated
[64479.802235] wlan0: associate with <MAC address removed> (try 1/3)
[64479.807392] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[64479.807505] wlan0: associated
[64479.807528] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[64506.684116] wlan0: authenticate with <MAC address removed>
[64506.694226] wlan0: send auth to <MAC address removed> (try 1/3)
[64506.720079] wlan0: authenticated
[64506.723258] wlan0: associate with <MAC address removed> (try 1/3)
[64506.756016] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=35)
[64506.756138] wlan0: associated
[64661.488405] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[64663.680000] Modules linked in: usb_storage binfmt_misc ctr ccm rfcomm bnep bluetooth snd_hda_codec_hdmi intel_ips snd_hda_codec_realtek intel_rapl x86_pkg_temp_thermal arc4 intel_powerclamp coretemp kvm uvcvideo rtl8188ee snd_hda_intel snd_hda_codec snd_hwdep videobuf2_vmalloc videobuf2_memops videobuf2_core rtl_pci rtlwifi videodev mac80211 i915 snd_pcm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel hp_wmi sparse_keymap snd_page_alloc aesni_intel snd_seq_midi snd_seq_midi_event snd_rawmidi aes_x86_64 lrw gf128mul drm_kms_helper cfg80211 snd_seq drm snd_seq_device glue_helper snd_timer ablk_helper mei_me cryptd snd mei hp_accel lis3lv02d joydev serio_raw input_polldev wmi i2c_algo_bit lpc_ich video soundcore mac_hid nls_iso8859_1 parport_pc ppdev lp parport hid_generic usbhid hid r8169 mii psmouse ahci libahci
[64664.845167] rtlwifi: wireless switch is on
[64667.787506] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[64669.513622] wlan0: authenticate with <MAC address removed>
[64669.531252] wlan0: direct probe to <MAC address removed> (try 1/3)
[64669.734826] wlan0: direct probe to <MAC address removed> (try 2/3)
[64669.938720] wlan0: direct probe to <MAC address removed> (try 3/3)
[64670.142595] wlan0: authentication with <MAC address removed> timed out
[64670.546531] wlan0: authenticate with <MAC address removed>
[64670.557753] wlan0: send auth to <MAC address removed> (try 1/3)
[64670.562642] wlan0: authenticated
[64670.566315] wlan0: associate with <MAC address removed> (try 1/3)
[64670.577408] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[64670.577544] wlan0: associated
[64670.577563] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[64695.301198] wlan0: authenticate with <MAC address removed>
[64695.311296] wlan0: send auth to <MAC address removed> (try 1/3)
[64695.312708] wlan0: authenticated
[64695.316532] wlan0: associate with <MAC address removed> (try 1/3)
[64695.320588] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=132)
[64695.320705] wlan0: associated
[64738.277493] wlan0: authenticate with <MAC address removed>
[64738.287586] wlan0: send auth to <MAC address removed> (try 1/3)
[64738.290332] wlan0: authenticated
[64738.292630] wlan0: associate with <MAC address removed> (try 1/3)
[64738.323740] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[64738.323859] wlan0: associated
[64801.246085] wlan0: authenticate with <MAC address removed>
[64801.256174] wlan0: direct probe to <MAC address removed> (try 1/3)
[64801.457607] wlan0: direct probe to <MAC address removed> (try 2/3)
[64801.661451] wlan0: direct probe to <MAC address removed> (try 3/3)
[64801.865340] wlan0: authentication with <MAC address removed> timed out
[64803.025942] wlan0: authenticate with <MAC address removed>
[64803.044904] wlan0: send auth to <MAC address removed> (try 1/3)
[64803.046360] wlan0: authenticated
[64803.048598] wlan0: associate with <MAC address removed> (try 1/3)
[64803.053090] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=35)
[64803.053202] wlan0: associated
[64882.435834] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[64885.439803] rtlwifi: wireless switch is on
[64888.236353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[64889.152536] wlan0: authenticate with <MAC address removed>
[64889.162630] wlan0: send auth to <MAC address removed> (try 1/3)
[64889.176045] wlan0: authenticated
[64889.178890] wlan0: associate with <MAC address removed> (try 1/3)
[64889.188296] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[64889.188403] wlan0: associated
[64889.188426] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[64916.180785] wlan0: authenticate with <MAC address removed>
[64916.190898] wlan0: send auth to <MAC address removed> (try 1/3)
[64916.202276] wlan0: authenticated
[64916.203892] wlan0: associate with <MAC address removed> (try 1/3)
[64916.229235] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=35)
[64916.229347] wlan0: associated
[65208.018212] wlan0: authenticate with <MAC address removed>
[65208.028304] wlan0: send auth to <MAC address removed> (try 1/3)
[65208.040669] wlan0: authenticated
[65208.041533] wlan0: associate with <MAC address removed> (try 1/3)
[65208.047960] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=135)
[65208.048078] wlan0: associated
[65567.818013] wlan0: authenticate with <MAC address removed>
[65567.828120] wlan0: direct probe to <MAC address removed> (try 1/3)
[65568.029357] wlan0: direct probe to <MAC address removed> (try 2/3)
[65568.233246] wlan0: direct probe to <MAC address removed> (try 3/3)
[65568.437162] wlan0: authentication with <MAC address removed> timed out
[65569.594827] wlan0: authenticate with <MAC address removed>
[65569.612666] wlan0: send auth to <MAC address removed> (try 1/3)
[65569.623279] wlan0: authenticated
[65569.624455] wlan0: associate with <MAC address removed> (try 1/3)
[65569.645384] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=135)
[65569.645490] wlan0: associated
[65807.692538] wlan0: authenticate with <MAC address removed>
[65807.702633] wlan0: direct probe to <MAC address removed> (try 1/3)
[65807.903988] wlan0: direct probe to <MAC address removed> (try 2/3)
[65808.107904] wlan0: direct probe to <MAC address removed> (try 3/3)
[65808.311781] wlan0: authentication with <MAC address removed> timed out
[65809.468511] wlan0: authenticate with <MAC address removed>
[65809.478670] wlan0: send auth to <MAC address removed> (try 1/3)
[65809.481312] wlan0: authenticated
[65809.483030] wlan0: associate with <MAC address removed> (try 1/3)
[65809.491005] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=135)
[65809.491114] wlan0: associated
[66167.488777] wlan0: authenticate with <MAC address removed>
[66167.498876] wlan0: direct probe to <MAC address removed> (try 1/3)
[66167.699868] wlan0: direct probe to <MAC address removed> (try 2/3)
[66167.903759] wlan0: direct probe to <MAC address removed> (try 3/3)
[66168.107682] wlan0: authentication with <MAC address removed> timed out
[66169.264678] wlan0: authenticate with <MAC address removed>
[66169.283229] wlan0: send auth to <MAC address removed> (try 1/3)
[66169.295566] wlan0: authenticated
[66169.298974] wlan0: associate with <MAC address removed> (try 1/3)
[66169.306040] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=135)
[66169.306163] wlan0: associated
[67007.017517] wlan0: authenticate with <MAC address removed>
[67007.027608] wlan0: send auth to <MAC address removed> (try 1/3)
[67007.042558] wlan0: authenticated
[67007.048984] wlan0: associate with <MAC address removed> (try 1/3)
[67007.052974] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[67007.053087] wlan0: associated
[67246.892240] wlan0: authenticate with <MAC address removed>
[67246.902373] wlan0: direct probe to <MAC address removed> (try 1/3)
[67247.103575] wlan0: send auth to <MAC address removed> (try 2/3)
[67248.414866] wlan0: send auth to <MAC address removed> (try 3/3)
[67249.390321] wlan0: authentication with <MAC address removed> timed out
[67250.486908] wlan0: authenticate with <MAC address removed>
[67250.505955] wlan0: send auth to <MAC address removed> (try 1/3)
[67250.507362] wlan0: authenticated
[67250.509671] wlan0: associate with <MAC address removed> (try 1/3)
[67250.513728] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=37)
[67250.513844] wlan0: associated
[67726.897282] wlan0: authenticate with <MAC address removed>
[67726.907548] wlan0: send auth to <MAC address removed> (try 1/3)
[67726.917909] wlan0: authenticated
[67726.920681] wlan0: associate with <MAC address removed> (try 1/3)
[67726.929392] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[67726.929519] wlan0: associated
[67846.554932] wlan0: authenticate with <MAC address removed>
[67846.565031] wlan0: send auth to <MAC address removed> (try 1/3)
[67846.567710] wlan0: authenticated
[67846.570091] wlan0: associate with <MAC address removed> (try 1/3)
[67846.574876] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=39)
[67846.574985] wlan0: associated
[68446.221563] wlan0: authenticate with <MAC address removed>
[68446.231698] wlan0: direct probe to <MAC address removed> (try 1/3)
[68446.432536] wlan0: send auth to <MAC address removed> (try 2/3)
[68447.747767] wlan0: send auth to <MAC address removed> (try 3/3)
[68448.747231] wlan0: authentication with <MAC address removed> timed out
[68449.848951] wlan0: authenticate with <MAC address removed>
[68449.866925] wlan0: send auth to <MAC address removed> (try 1/3)
[68449.869223] wlan0: authenticated
[68449.870559] wlan0: associate with <MAC address removed> (try 1/3)
[68449.878550] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=39)
[68449.878662] wlan0: associated
[68686.087956] wlan0: authenticate with <MAC address removed>
[68686.098071] wlan0: direct probe to <MAC address removed> (try 1/3)
[68686.299154] wlan0: direct probe to <MAC address removed> (try 2/3)
[68686.503044] wlan0: direct probe to <MAC address removed> (try 3/3)
[68686.706913] wlan0: authentication with <MAC address removed> timed out
[68687.800282] wlan0: authenticate with <MAC address removed>
[68687.818444] wlan0: send auth to <MAC address removed> (try 1/3)
[68687.823356] wlan0: authenticated
[68687.826245] wlan0: associate with <MAC address removed> (try 1/3)
[68687.833468] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=39)
[68687.833605] wlan0: associated
[69045.887647] wlan0: authenticate with <MAC address removed>
[69045.897788] wlan0: send auth to <MAC address removed> (try 1/3)
[69045.909999] wlan0: authenticated
[69045.911051] wlan0: associate with <MAC address removed> (try 1/3)
[69045.924013] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[69045.924126] wlan0: associated
[69165.824436] wlan0: authenticate with <MAC address removed>
[69165.834675] wlan0: direct probe to <MAC address removed> (try 1/3)
[69166.036290] wlan0: send auth to <MAC address removed> (try 2/3)
[69167.311617] wlan0: send auth to <MAC address removed> (try 3/3)
[69168.347071] wlan0: authentication with <MAC address removed> timed out
[69169.448204] wlan0: authenticate with <MAC address removed>
[69169.466555] wlan0: send auth to <MAC address removed> (try 1/3)
[69169.469779] wlan0: authenticated
[69169.470349] wlan0: associate with <MAC address removed> (try 1/3)
[69169.477039] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[69169.477174] wlan0: associated
[69285.754421] wlan0: authenticate with <MAC address removed>
[69285.764519] wlan0: send auth to <MAC address removed> (try 1/3)
[69285.766386] wlan0: authenticated
[69285.769689] wlan0: associate with <MAC address removed> (try 1/3)
[69285.774242] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=42)
[69285.774347] wlan0: associated
[69547.859112] wlan0: Connection to AP <MAC address removed> lost
[69548.488337] wlan0: authenticate with <MAC address removed>
[69548.507723] wlan0: send auth to <MAC address removed> (try 1/3)
[69548.510712] wlan0: authenticated
[69548.511541] wlan0: associate with <MAC address removed> (try 1/3)
[69548.515522] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[69548.515630] wlan0: associated
[70209.379127] wlan0: Connection to AP <MAC address removed> lost
[70210.784337] wlan0: authenticate with <MAC address removed>
[70210.803384] wlan0: send auth to <MAC address removed> (try 1/3)
[70210.805019] wlan0: authenticated
[70210.807188] wlan0: associate with <MAC address removed> (try 1/3)
[70210.812693] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=44)
[70210.812802] wlan0: associated
[70245.216414] wlan0: authenticate with <MAC address removed>
[70245.226506] wlan0: send auth to <MAC address removed> (try 1/3)
[70245.230249] wlan0: authenticated
[70245.236044] wlan0: associate with <MAC address removed> (try 1/3)
[70245.244498] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=187)
[70245.244609] wlan0: associated
[70365.154515] wlan0: authenticate with <MAC address removed>
[70365.164607] wlan0: send auth to <MAC address removed> (try 1/3)
[70365.166207] wlan0: authenticated
[70365.169397] wlan0: associate with <MAC address removed> (try 1/3)
[70365.173669] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[70365.173811] wlan0: associated
[70605.016477] wlan0: authenticate with <MAC address removed>
[70605.026565] wlan0: send auth to <MAC address removed> (try 1/3)
[70605.032801] wlan0: authenticated
[70605.035940] wlan0: associate with <MAC address removed> (try 1/3)
[70605.040399] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[70605.040519] wlan0: associated
[70724.950014] wlan0: authenticate with <MAC address removed>
[70724.960124] wlan0: direct probe to <MAC address removed> (try 1/3)
[70725.161240] wlan0: direct probe to <MAC address removed> (try 2/3)
[70725.365084] wlan0: direct probe to <MAC address removed> (try 3/3)
[70725.568950] wlan0: authentication with <MAC address removed> timed out
[70726.734705] wlan0: authenticate with <MAC address removed>
[70726.752573] wlan0: send auth to <MAC address removed> (try 1/3)
[70726.753966] wlan0: authenticated
[70726.756280] wlan0: associate with <MAC address removed> (try 1/3)
[70726.760334] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=192)
[70726.760439] wlan0: associated
[70844.883763] wlan0: authenticate with <MAC address removed>
[70844.893937] wlan0: send auth to <MAC address removed> (try 1/3)
[70844.899267] wlan0: authenticated
[70844.902579] wlan0: associate with <MAC address removed> (try 1/3)
[70844.913074] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[70844.913195] wlan0: associated
[71084.749569] wlan0: authenticate with <MAC address removed>
[71084.759647] wlan0: send auth to <MAC address removed> (try 1/3)
[71084.764578] wlan0: authenticated
[71084.765358] wlan0: associate with <MAC address removed> (try 1/3)
[71084.769575] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=192)
[71084.769718] wlan0: associated
[72893.446743] wlan0: deauthenticated from <MAC address removed> (Reason: 2)
[72894.204672] wlan0: authenticate with <MAC address removed>
[72894.223074] wlan0: send auth to <MAC address removed> (try 1/3)
[72894.224904] wlan0: authenticated
[72894.226830] wlan0: associate with <MAC address removed> (try 1/3)
[72894.232189] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[72894.232308] wlan0: associated
[73123.620401] wlan0: authenticate with <MAC address removed>
[73123.630485] wlan0: direct probe to <MAC address removed> (try 1/3)
[73123.831145] wlan0: direct probe to <MAC address removed> (try 2/3)
[73124.035068] wlan0: direct probe to <MAC address removed> (try 3/3)
[73124.238971] wlan0: authentication with <MAC address removed> timed out
[73125.399026] wlan0: authenticate with <MAC address removed>
[73125.418484] wlan0: send auth to <MAC address removed> (try 1/3)
[73125.420884] wlan0: authenticated
[73125.422249] wlan0: associate with <MAC address removed> (try 1/3)
[73125.427944] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=5)
[73125.428081] wlan0: associated
[73363.486435] wlan0: authenticate with <MAC address removed>
[73363.496526] wlan0: send auth to <MAC address removed> (try 1/3)
[73363.498978] wlan0: authenticated
[73363.501866] wlan0: associate with <MAC address removed> (try 1/3)
[73363.508255] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=3)
[73363.508394] wlan0: associated
[73483.423873] wlan0: authenticate with <MAC address removed>
[73483.433966] wlan0: send auth to <MAC address removed> (try 1/3)
[73483.436202] wlan0: authenticated
[73483.439097] wlan0: associate with <MAC address removed> (try 1/3)
[73483.444985] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[73483.445113] wlan0: associated
[74083.086541] wlan0: authenticate with <MAC address removed>
[74083.096648] wlan0: direct probe to <MAC address removed> (try 1/3)
[74083.297493] wlan0: direct probe to <MAC address removed> (try 2/3)
[74083.501429] wlan0: direct probe to <MAC address removed> (try 3/3)
[74083.705238] wlan0: authentication with <MAC address removed> timed out
[74084.862023] wlan0: authenticate with <MAC address removed>
[74084.872186] wlan0: send auth to <MAC address removed> (try 1/3)
[74084.873676] wlan0: authenticated
[74084.876688] wlan0: associate with <MAC address removed> (try 1/3)
[74084.881539] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[74084.881657] wlan0: associated
[74562.824075] wlan0: authenticate with <MAC address removed>
[74562.834163] wlan0: direct probe to <MAC address removed> (try 1/3)
[74563.034711] wlan0: send auth to <MAC address removed> (try 2/3)
[74564.345990] wlan0: send auth to <MAC address removed> (try 3/3)
[74565.309467] wlan0: authentication with <MAC address removed> timed out
[74566.401572] wlan0: authenticate with <MAC address removed>
[74566.420965] wlan0: send auth to <MAC address removed> (try 1/3)
[74566.428413] wlan0: authenticated
[74566.428791] wlan0: associate with <MAC address removed> (try 1/3)
[74566.447488] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[74566.447602] wlan0: associated
[74922.623824] wlan0: authenticate with <MAC address removed>
[74922.633902] wlan0: direct probe to <MAC address removed> (try 1/3)
[74922.834668] wlan0: send auth to <MAC address removed> (try 2/3)
[74924.145871] wlan0: send auth to <MAC address removed> (try 3/3)
[74925.121300] wlan0: authentication with <MAC address removed> timed out
[74926.205244] wlan0: authenticate with <MAC address removed>
[74926.224837] wlan0: send auth to <MAC address removed> (try 1/3)
[74926.231213] wlan0: authenticated
[74926.232720] wlan0: associate with <MAC address removed> (try 1/3)
[74926.245295] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[74926.245401] wlan0: associated
[75763.350239] wlan0: Connection to AP <MAC address removed> lost
[75764.751131] wlan0: authenticate with <MAC address removed>
[75764.766753] wlan0: send auth to <MAC address removed> (try 1/3)
[75764.768498] wlan0: authenticated
[75764.773196] wlan0: associate with <MAC address removed> (try 1/3)
[75764.777208] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=32)
[75764.777323] wlan0: associated
[75882.084179] wlan0: authenticate with <MAC address removed>
[75882.094319] wlan0: send auth to <MAC address removed> (try 1/3)
[75882.100548] wlan0: authenticated
[75882.101052] wlan0: associate with <MAC address removed> (try 1/3)
[75882.105216] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=53)
[75882.105332] wlan0: associated
[76002.019260] wlan0: authenticate with <MAC address removed>
[76002.029351] wlan0: direct probe to <MAC address removed> (try 1/3)
[76002.230351] wlan0: send auth to <MAC address removed> (try 2/3)
[76003.545530] wlan0: send auth to <MAC address removed> (try 3/3)
[76004.509044] wlan0: authentication with <MAC address removed> timed out
[76005.666017] wlan0: authenticate with <MAC address removed>
[76005.684587] wlan0: send auth to <MAC address removed> (try 1/3)
[76005.686455] wlan0: authenticated
[76005.688345] wlan0: associate with <MAC address removed> (try 1/3)
[76005.693192] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=53)
[76005.693320] wlan0: associated
[76481.752129] wlan0: authenticate with <MAC address removed>
[76481.762348] wlan0: send auth to <MAC address removed> (try 1/3)
[76481.763816] wlan0: authenticated
[76481.767550] wlan0: associate with <MAC address removed> (try 1/3)
[76481.772781] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=38)
[76481.772897] wlan0: associated
[76601.681356] wlan0: authenticate with <MAC address removed>
[76601.691450] wlan0: send auth to <MAC address removed> (try 1/3)
[76601.694859] wlan0: authenticated
[76601.696841] wlan0: associate with <MAC address removed> (try 1/3)
[76601.700809] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[76601.700932] wlan0: associated
[76721.618948] wlan0: authenticate with <MAC address removed>
[76721.629038] wlan0: send auth to <MAC address removed> (try 1/3)
[76721.632838] wlan0: authenticated
[76721.634654] wlan0: associate with <MAC address removed> (try 1/3)
[76721.639985] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=54)
[76721.640099] wlan0: associated
[77441.474584] wlan0: authenticate with <MAC address removed>
[77441.484700] wlan0: direct probe to <MAC address removed> (try 1/3)
[77441.685736] wlan0: send auth to <MAC address removed> (try 2/3)
[77442.721169] wlan0: send auth to <MAC address removed> (try 3/3)
[77443.744637] wlan0: authentication with <MAC address removed> timed out
[77444.954187] wlan0: authenticate with <MAC address removed>
[77444.972200] wlan0: send auth to <MAC address removed> (try 1/3)
[77444.987023] wlan0: authenticated
[77444.987853] wlan0: associate with <MAC address removed> (try 1/3)
[77444.993418] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=54)
[77444.993539] wlan0: associated
[77801.018297] wlan0: authenticate with <MAC address removed>
[77801.028407] wlan0: send auth to <MAC address removed> (try 1/3)
[77801.031236] wlan0: authenticated
[77801.033826] wlan0: associate with <MAC address removed> (try 1/3)
[77801.040786] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=42)
[77801.040907] wlan0: associated
[78040.881033] wlan0: authenticate with <MAC address removed>
[78040.891150] wlan0: direct probe to <MAC address removed> (try 1/3)
[78041.092379] wlan0: direct probe to <MAC address removed> (try 2/3)
[78041.296216] wlan0: direct probe to <MAC address removed> (try 3/3)
[78041.500192] wlan0: authentication with <MAC address removed> timed out
[78042.712026] wlan0: authenticate with <MAC address removed>
[78042.722105] wlan0: send auth to <MAC address removed> (try 1/3)
[78042.723561] wlan0: authenticated
[78042.727416] wlan0: associate with <MAC address removed> (try 1/3)
[78042.731363] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[78042.731488] wlan0: a ssociated
[78160.814208] wlan0: authenticate with <MAC address removed>
[78160.824304] wlan0: send auth to <MAC address removed> (try 1/3)
[78160.825935] wlan0: authenticated
[78160.829710] wlan0: associate with <MAC address removed> (try 1/3)
[78160.833749] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=57)
[78160.833887] wlan0: associated
[79240.217853] wlan0: authenticate with <MAC address removed>
[79240.228036] wlan0: send auth to <MAC address removed> (try 1/3)
[79240.229848] wlan0: authenticated
[79240.233840] wlan0: associate with <MAC address removed> (try 1/3)
[79240.237888] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=7)
[79240.238000] wlan0: associated
[79360.159514] wlan0: authenticate with <MAC address removed>
[79360.169663] wlan0: direct probe to <MAC address removed> (try 1/3)
[79360.370570] wlan0: direct probe to <MAC address removed> (try 2/3)
[79360.574486] wlan0: direct probe to <MAC address removed> (try 3/3)
[79360.778369] wlan0: authentication with <MAC address removed> timed out
[79361.954213] wlan0: authenticate with <MAC address removed>
[79361.973893] wlan0: send auth to <MAC address removed> (try 1/3)
[79361.975681] wlan0: authenticated
[79361.977699] wlan0: associate with <MAC address removed> (try 1/3)
[79361.983962] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=62)
[79361.984072] wlan0: associated
[79379.782888] wlan0: Connection to AP <MAC address removed> lost
[79380.991453] wlan0: authenticate with <MAC address removed>
[79381.011222] wlan0: send auth to <MAC address removed> (try 1/3)
[79381.115097] wlan0: send auth to <MAC address removed> (try 2/3)
[79381.218994] wlan0: send auth to <MAC address removed> (try 3/3)
[79381.322960] wlan0: authentication with <MAC address removed> timed out
[79381.507264] wlan0: authenticate with <MAC address removed>
[79381.526988] wlan0: send auth to <MAC address removed> (try 1/3)
[79381.630771] wlan0: send auth to <MAC address removed> (try 2/3)
[79381.734728] wlan0: send auth to <MAC address removed> (try 3/3)
[79381.838666] wlan0: authentication with <MAC address removed> timed out
[79381.982963] wlan0: authenticate with <MAC address removed>
[79381.993031] wlan0: send auth to <MAC address removed> (try 1/3)
[79382.094520] wlan0: send auth to <MAC address removed> (try 2/3)
[79382.096762] wlan0: authenticated
[79382.098519] wlan0: associate with <MAC address removed> (try 1/3)
[79382.104166] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[79382.104293] wlan0: associated
[79749.393437] wlan0: Connection to AP <MAC address removed> lost
[79750.843692] wlan0: authenticate with <MAC address removed>
[79750.861709] wlan0: send auth to <MAC address removed> (try 1/3)
[79750.863467] wlan0: authenticated
[79750.865424] wlan0: associate with <MAC address removed> (try 1/3)
[79750.869565] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=9)
[79750.869669] wlan0: associated
[79839.884617] wlan0: authenticate with <MAC address removed>
[79839.894759] wlan0: direct probe to <MAC address removed> (try 1/3)
[79840.095889] wlan0: direct probe to <MAC address removed> (try 2/3)
[79840.299775] wlan0: direct probe to <MAC address removed> (try 3/3)
[79840.503665] wlan0: authentication with <MAC address removed> timed out
[79841.667757] wlan0: authenticate with <MAC address removed>
[79841.687318] wlan0: send auth to <MAC address removed> (try 1/3)
[79841.688739] wlan0: authenticated
[79841.690890] wlan0: associate with <MAC address removed> (try 1/3)
[79841.696574] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=60)
[79841.696695] wlan0: associated
[80079.747255] wlan0: authenticate with <MAC address removed>
[80079.757329] wlan0: send auth to <MAC address removed> (try 1/3)
[80079.758781] wlan0: authenticated
[80079.762525] wlan0: associate with <MAC address removed> (try 1/3)
[80079.766569] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=11)
[80079.766685] wlan0: associated
[80199.684326] wlan0: authenticate with <MAC address removed>
[80199.694430] wlan0: send auth to <MAC address removed> (try 1/3)
[80199.700749] wlan0: authenticated
[80199.703794] wlan0: associate with <MAC address removed> (try 1/3)
[80199.709013] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[80199.709135] wlan0: associated
[80439.546942] wlan0: authenticate with <MAC address removed>
[80439.557052] wlan0: direct probe to <MAC address removed> (try 1/3)
[80439.758295] wlan0: direct probe to <MAC address removed> (try 2/3)
[80439.962177] wlan0: direct probe to <MAC address removed> (try 3/3)
[80440.166067] wlan0: authentication with <MAC address removed> timed out
[80441.345939] wlan0: authenticate with <MAC address removed>
[80441.356026] wlan0: send auth to <MAC address removed> (try 1/3)
[80441.358576] wlan0: authenticated
[80441.361370] wlan0: associate with <MAC address removed> (try 1/3)
[80441.368365] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[80441.368479] wlan0: associated
[80559.736145] wlan0: authenticate with <MAC address removed>
[80559.746308] wlan0: send auth to <MAC address removed> (try 1/3)
[80559.747791] wlan0: authenticated
[80559.751542] wlan0: associate with <MAC address removed> (try 1/3)
[80559.756949] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=12)
[80559.757064] wlan0: associated
[80679.413574] wlan0: authenticate with <MAC address removed>
[80679.423668] wlan0: send auth to <MAC address removed> (try 1/3)
[80679.428503] wlan0: authenticated
[80679.432965] wlan0: associate with <MAC address removed> (try 1/3)
[80679.438685] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[80679.438796] wlan0: associated
[80799.346902] wlan0: authenticate with <MAC address removed>
[80799.357095] wlan0: direct probe to <MAC address removed> (try 1/3)
[80799.558274] wlan0: direct probe to <MAC address removed> (try 2/3)
[80799.762161] wlan0: direct probe to <MAC address removed> (try 3/3)
[80799.966044] wlan0: authentication with <MAC address removed> timed out
[80801.126159] wlan0: authenticate with <MAC address removed>
[80801.136286] wlan0: direct probe to <MAC address removed> (try 1/3)
[80801.337273] wlan0: direct probe to <MAC address removed> (try 2/3)
[80801.541109] wlan0: direct probe to <MAC address removed> (try 3/3)
[80801.745009] wlan0: authentication with <MAC address removed> timed out
[80802.058843] wlan0: authenticate with <MAC address removed>
[80802.068938] wlan0: send auth to <MAC address removed> (try 1/3)
[80802.072155] wlan0: authenticated
[80802.072779] wlan0: associate with <MAC address removed> (try 1/3)
[80802.077496] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[80802.077614] wlan0: associated
[80919.280007] wlan0: authenticate with <MAC address removed>
[80919.290077] wlan0: send auth to <MAC address removed> (try 1/3)
[80919.294503] wlan0: authenticated
[80919.295563] wlan0: associate with <MAC address removed> (try 1/3)
[80919.300545] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=4)
[80919.300656] wlan0: associated
[81039.213440] wlan0: authenticate with <MAC address removed>
[81039.223532] wlan0: send auth to <MAC address removed> (try 1/3)
[81039.227419] wlan0: authenticated
[81039.228863] wlan0: associate with <MAC address removed> (try 1/3)
[81039.238702] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=77)
[81039.238817] wlan0: associated
[81399.021219] wlan0: authenticate with <MAC address removed>
[81399.031317] wlan0: send auth to <MAC address removed> (try 1/3)
[81399.032844] wlan0: authenticated
[81399.036850] wlan0: associate with <MAC address removed> (try 1/3)
[81399.041600] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[81399.041718] wlan0: associated
[81518.954610] wlan0: authenticate with <MAC address removed>
[81518.964708] wlan0: direct probe to <MAC address removed> (try 1/3)
[81519.165966] wlan0: send auth to <MAC address removed> (try 2/3)
[81520.477257] wlan0: send auth to <MAC address removed> (try 3/3)
[81521.440790] wlan0: authentication with <MAC address removed> timed out
[81522.605441] wlan0: authenticate with <MAC address removed>
[81522.615581] wlan0: send auth to <MAC address removed> (try 1/3)
[81522.617452] wlan0: authenticated
[81522.620030] wlan0: associate with <MAC address removed> (try 1/3)
[81522.624574] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=64)
[81522.624689] wlan0: associated
[82718.293489] wlan0: authenticate with <MAC address removed>
[82718.303565] wlan0: send auth to <MAC address removed> (try 1/3)
[82718.315627] wlan0: authenticated
[82718.319065] wlan0: associate with <MAC address removed> (try 1/3)
[82718.323136] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[82718.323276] wlan0: associated
[82838.492715] wlan0: authenticate with <MAC address removed>
[82838.502877] wlan0: send auth to <MAC address removed> (try 1/3)
[82838.504369] wlan0: authenticated
[82838.508336] wlan0: associate with <MAC address removed> (try 1/3)
[82838.513076] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=67)
[82838.513190] wlan0: associated
[83078.079329] wlan0: authenticate with <MAC address removed>
[83078.089406] wlan0: send auth to <MAC address removed> (try 1/3)
[83078.092538] wlan0: authenticated
[83078.094952] wlan0: associate with <MAC address removed> (try 1/3)
[83078.100252] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[83078.100371] wlan0: associated
[83198.293254] wlan0: authenticate with <MAC address removed>
[83198.303365] wlan0: direct probe to <MAC address removed> (try 1/3)
[83198.503997] wlan0: send auth to <MAC address removed> (try 2/3)
[83199.507470] wlan0: send auth to <MAC address removed> (try 3/3)
[83200.542837] wlan0: authentication with <MAC address removed> timed out
[83201.639106] wlan0: authenticate with <MAC address removed>
[83201.658390] wlan0: send auth to <MAC address removed> (try 1/3)
[83201.660256] wlan0: authenticated
[83201.662249] wlan0: associate with <MAC address removed> (try 1/3)
[83201.667690] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[83201.667807] wlan0: associated
[83797.683763] wlan0: authenticate with <MAC address removed>
[83797.693864] wlan0: send auth to <MAC address removed> (try 1/3)
[83797.697682] wlan0: authenticated
[83797.698725] wlan0: associate with <MAC address removed> (try 1/3)
[83797.702918] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=70)
[83797.703035] wlan0: associated
[84659.069420] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[84665.776443] rtlwifi: wireless switch is on
[84669.504439] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[84670.989423] wlan0: authenticate with <MAC address removed>
[84671.456584] wlan0: send auth to <MAC address removed> (try 1/3)
[84671.462558] wlan0: authenticated
[84671.464035] wlan0: associate with <MAC address removed> (try 1/3)
[84671.467784] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[84671.467917] wlan0: associated
[84671.467966] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[94716.487804] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[94720.182151] rtlwifi: wireless switch is on
[94723.073596] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[94723.987348] wlan0: authenticate with <MAC address removed>
[94723.997544] wlan0: send auth to <MAC address removed> (try 1/3)
[94724.024829] wlan0: authenticated
[94724.027542] wlan0: associate with <MAC address removed> (try 1/3)
[94724.039017] wlan0: RX AssocResp from <MAC address removed> (capab=0x31 status=0 aid=2)
[94724.039121] wlan0: associated
[94724.039141] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[94757.103922] wlan0: Connection to AP <MAC address removed> lost
[94758.501326] wlan0: authenticate with <MAC address removed>
[94758.519514] wlan0: send auth to <MAC address removed> (try 1/3)
[94758.527596] wlan0: authenticated
[94758.531183] wlan0: associate with <MAC address removed> (try 1/3)
[94758.572866] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[94758.572989] wlan0: associated
[99366.067065] wlan0: Connection to AP <MAC address removed> lost
[99367.512686] wlan0: authenticate with <MAC address removed>
[99367.531392] wlan0: send auth to <MAC address removed> (try 1/3)
[99367.555329] wlan0: authenticated
[99367.559038] wlan0: associate with <MAC address removed> (try 1/3)
[99367.565677] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[99367.565789] wlan0: associated
[101120.773232] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[101123.488235] rtlwifi: wireless switch is on
[101126.401691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[101128.110591] wlan0: authenticate with <MAC address removed>
[101128.130169] wlan0: send auth to <MAC address removed> (try 1/3)
[101128.190457] wlan0: authenticated
[101128.193959] wlan0: associate with <MAC address removed> (try 1/3)
[101128.197694] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[101128.197801] wlan0: associated
[101128.197822] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[101128.210006] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[101128.244217] wlan0: authenticate with <MAC address removed>
[101128.254326] wlan0: send auth to <MAC address removed> (try 1/3)
[101128.277585] wlan0: authenticated
[101128.277894] wlan0: associate with <MAC address removed> (try 1/3)
[101128.290095] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[101128.290204] wlan0: associated
[103692.770543] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[103695.572837] rtlwifi: wireless switch is on
[103698.330155] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[103700.026397] wlan0: authenticate with <MAC address removed>
[103700.045858] wlan0: send auth to <MAC address removed> (try 1/3)
[103700.047731] wlan0: authenticated
[103700.049636] wlan0: associate with <MAC address removed> (try 1/3)
[103700.053338] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[103700.053449] wlan0: associated
[103700.053473] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[103700.064615] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[103700.096253] wlan0: authenticate with <MAC address removed>
[103700.106335] wlan0: send auth to <MAC address removed> (try 1/3)
[103700.109249] wlan0: authenticated
[103700.109596] wlan0: associate with <MAC address removed> (try 1/3)
[103700.113698] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[103700.113812] wlan0: associated
[104071.802611] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[104074.431088] rtlwifi: wireless switch is on
[104077.399249] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[104079.119277] wlan0: authenticate with <MAC address removed>
[104079.138464] wlan0: send auth to <MAC address removed> (try 1/3)
[104079.146698] wlan0: authenticated
[104079.150175] wlan0: associate with <MAC address removed> (try 1/3)
[104079.161017] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[104079.161157] wlan0: associated
[104079.161172] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[104079.178249] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[104079.212624] wlan0: authenticate with <MAC address removed>
[104079.222735] wlan0: send auth to <MAC address removed> (try 1/3)
[104079.232357] wlan0: authenticated
[104079.234171] wlan0: associate with <MAC address removed> (try 1/3)
[104079.244124] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[104079.244245] wlan0: associated


########## wireless info END ############

```

---

### Post by DuckHook on 2014-06-09
Firstly, it's such a pleasure dealing with someone who does so much homework before asking for help. However, notwithstanding your very complete report, please describe the following:

1. Is the problematic connection the WIFI connection? (It usually is)
2. Assuming WIFI, how long does it take before the connection drops?
3. Is there a pattern of behaviour? i.e. does it always drop when you visit certain pages or is it random?
4. Does it drop when not using a browser? i.e. when you are updating the OS?
5. What kind of router are you using and is it running its original OS? Has it been changed to OpenWRT or DD-WRT, etc?
6. Do you have other Linux machines and do they experience the same problem? If so, what is their WIFI chipset?
7. Have you ever tried other distros? If so, have they solved the connection dropping issue?
8. If you dual boot, or if the problem machine has ever run Windows, what was your experience with it under Windows?

Your WAP (TP-LINK_99F562) is on the same frequency as VGV75191674C5. Try changing to a noncompeting frequency. Channels 2, 3, 5, 7, 9 & 10 appear to be free. I would recommend #3 or #9. If you prefer an easier-to-understand quasi-graphical way of seeing what channels are in use and which are free, then please download *wavemon* to show you the whole picture.```
sudo apt-get install wavemon && sudo wavemon
```Wavemon needs to be run under *sudo*, but it is safe to do so.

---

### Post by Vladlenin5000 on 2014-06-09
> **DuckHook said:**
> Firstly, it's such a pleasure dealing with someone who does so much homework before asking for help.

+1

---

### Post by DuckHook on 2014-06-09
Just did a little more digging for you. Your problem may be this one:

[http://ubuntuforums.org/showthread.php?t=2219952&p=13003107#post13003107](http://ubuntuforums.org/showthread.php?t=2219952&p=13003107#post13003107)

If so, you will need to compile the newest driver for your WIFI card by following the instructions from *praseodym*. The best way is to copy and paste, then execute *praseodym*'s instructions (one line at a time!) into a terminal window instead of retyping. A single typo will make the instructions inoperative, so copying and pasting is the best strategy. Make sure to reboot at the end of the process.

Make sure that your *wired* NIC is plugged in and you are not trying to download through your already wonky WIFI chip.

<CAVEAT> Compiling is not for the faint of heart. But if you follow *praseodym*'s instructions precisely, I can't see you getting into too much trouble on this one. Make sure you back up all of your critical data first, in case you cannot log back in due to some OS crash. And if it works, please do not assume that compiling a driver is the solution in every case. For example, compiling the wrong video driver could leave you in a heap of trouble. Compiling drivers should always be sort of the last resort, but there are times when it is the only solution that works.

Let us know how it goes.

---

### Post by gijs2 on 2014-06-10
> **DuckHook said:**
> Just did a little more digging for you. Your problem may be this one:

[http://ubuntuforums.org/showthread.php?t=2219952&p=13003107#post13003107](http://ubuntuforums.org/showthread.php?t=2219952&p=13003107#post13003107)

If so, you will need to compile the newest driver for your WIFI card by following the instructions from *praseodym*. The best way is to copy and paste, then execute *praseodym*'s instructions (one line at a time!) into a terminal window instead of retyping. A single typo will make the instructions inoperative, so copying and pasting is the best strategy. Make sure to reboot at the end of the process.

Make sure that your *wired* NIC is plugged in and you are not trying to download through your already wonky WIFI chip.

<CAVEAT> Compiling is not for the faint of heart. But if you follow *praseodym*'s instructions precisely, I can't see you getting into too much trouble on this one. Make sure you back up all of your critical data first, in case you cannot log back in due to some OS crash. And if it works, please do not assume that compiling a driver is the solution in every case. For example, compiling the wrong video driver could leave you in a heap of trouble. Compiling drivers should always be sort of the last resort, but there are times when it is the only solution that works.

Let us know how it goes.

Hi,
Thanks for your effort but how can I make certain I do not crash my laptop?
I am not doing anything at the moment if there is a risk, at the moment i do not have a budget to get a new laptop so i don't want to break this one.

---

### Post by squakie on 2014-06-10
That link is to my thread, and the post inside that thread explains how to do it all - prerequisites and all.  It's simple.  One recommendation:  run the make as sudo - e.g.:  sudo make.  I ran into permissions problems until I did that.  It's straight forward and it works!  If you have any questions about the procedure itself, post back what your question(s) are and regarding which part of the instructions.

EDIT:  BTW - since you are building a driver you will need to rebuild it each time the kernel changes or one of the items it uses changes.  You'll know - it starts acting up again ;)   I used a USB stick wireless adapter while following all of those instructions as the default wireless connection through the included adapter was just not reliable enough.

EDIT-EDIT:  It won't mess up your hardware, you won't have to get a new system.  Worse case scenario is that you'll have to reinstall Ubuntu (hence why it was recommended previously to be sure you things backed up).  I never had any problems.

---

### Post by DuckHook on 2014-06-10
Hi squakie,

Trust all is well with you.> **squakie said:**
> ...since you are building a driver you will need to rebuild it each time the kernel changes...I thought that with *dkms* installed as per *praseodym*'s instructions, the module should update automatically with kernel updates. Just make sure that *dkms* is installed before the driver is built/installed and thereafter the driver should auto-rebuild with each kernel change. Or am I missing something?

> **gijs2 said:**
> ...how can I make certain I do not crash my laptop?
I am not doing anything at the moment if there is a risk, at the moment i do not have a budget to get a new laptop so i don't want to break this one.

I am trying to be extra careful with my advice, as I try to be with all new users. Not trying to alarm you. The chances are that nothing will go wrong and everything will go smoothly, but there is a non-zero chance that you could hose your system with any procedure that involves new drivers. If you are not making regular backups as a matter of course, then you are already at risk of losing precious data should, say, your HDD fail, so backing up your critical data is the first rule of smart computing whether you intend to add new drivers or not.

Let's put it this way... I have no idea if your particular problem is even the driver. Yours may be a different problem than squakie's. On these forums, most suggested solutions are but educated guesses. So, although it's not quite a shot in the dark, it isn't as if any of us have a crystal ball either. However, if you take the approach that each solution could possibly lead to having to reinstall your system, then you are prepared for the worst and a system crash will neither hurt nor hinder you. You will already have your data backed up and a modern Ubuntu re-install usually takes no more than 20 or 30 minutes. Any crash would involve only the OS and not the HW, so reinstalling Ubuntu should bring you back to square one. Only you can judge whether the risk is worth the reward. In your place, I would have no compunction to try the driver strategy, since I make scheduled backups and do redundacies as a matter of course.

---

### Post by squakie on 2014-06-11
Same adapter, same problems - hence why you should try the driver.

The op asked about harming their hardware and having to buy a new PC.  Chances of that are almost nil.

As with anything you do such as compiling a driver of course there is a risk to the OS installation -  that's why you always see the advice to backup anything you may need.

---

### Post by squakie on 2014-06-13
DuckHook:  I didn't know that's was what the dkms "stuff" was for - I just plain don't know anything about that - so thanks for filling me in!  It's appreciated!

Dave ;)

---


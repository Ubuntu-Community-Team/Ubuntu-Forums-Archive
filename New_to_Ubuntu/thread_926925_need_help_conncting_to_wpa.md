---
title: "need help conncting to wpa"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by trigsenior on 2008-09-22
hello,


My problem is that while connected to my wpa router i get "speeds" of 1 mb/s while on my laptop which is connected to same router get 54 mb/s.

I turned off ip6 because i heard it might help but no.

any ideas / help would be much much loved.

many thanks

---

### Post by trigsenior on 2008-09-22
not sure if to early to bump ... oh well bump

---

### Post by willca on 2008-09-23
just  a couple of suggestions...

check if anybody else in the vicinity might be using the same channel as you are...noise dont help at all

sudo iwlist wlan0 scan

I would also check how the signal strength is and try to change locations if possible.

sudo iwconfig wlan0

I had a similar problem like this before when I was actually using a Broadcom driver that was too new for my old wifi nic. I worked around that by actually using ndiswrapper instead of the fwcutter. But thats another story.

---

### Post by trigsenior on 2008-09-23
I do not think it is a problem with channels or the actually router as when i boot up into vista works great. Also my laptop running  debian works fine.
I can ping google i get 

64 bytes from fk-10147.google.com : Icmp_seq = 460
95.8 ms (DUP!) 


here is sudo iwlist wlan0 scan

```


ath0      Scan completed :
          Cell 01 - Address: 52:8B:80:EC:41:04
                    ESSID:"Cheznous"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 52:8B:80:EC:41:07
                    ESSID:"freephonie"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 03 - Address: 02:FF:EF:9E:11:13
                    ESSID:"freephonie"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 04 - Address: 00:1D:6A:1F:E6:35
                    ESSID:"Livebox-c306"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101820003a4000027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010020ff7f
          Cell 05 - Address: DA:10:42:7A:9D:03
                    ESSID:"freephonie"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 06 - Address: 00:17:33:93:D5:31
                    ESSID:"Lee"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:14:A4:7D:C8:AF
                    ESSID:"passage"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: 00:90:4B:84:78:F4
                    ESSID:"WANADOO-03ED"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=8/70  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 09 - Address: 7E:1B:B2:CB:A4:D7
                    ESSID:"freephonie"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 10 - Address: 00:18:39:23:44:DA
                    ESSID:"ALBARDO"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=21/70  Signal level=-74 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101050003a4000027a4000042435e0062322f00
          Cell 11 - Address: 00:18:84:A3:A2:86
                    ESSID:"Freebox_121"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f20201018f0002a3400027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010020ff7f
          Cell 12 - Address: 02:FF:EF:9E:11:10
                    ESSID:"davenet"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 13 - Address: 02:FF:EF:9E:11:11
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 14 - Address: 02:FF:EF:9E:11:12
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 15 - Address: 00:04:E2:BD:43:4C
                    ESSID:"SMC"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 16 - Address: 00:11:F5:D7:4A:36
                    ESSID:"THOMSON"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 17 - Address: DA:10:42:7A:9D:00
                    ESSID:"freebox"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 18 - Address: 00:09:5B:E9:F5:48
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=11/70  Signal level=-84 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:ath_ie=dd0900037f01010006ff7f
          Cell 19 - Address: 00:17:33:93:D5:38
                    ESSID:"Neuf WiFi"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=14/70  Signal level=-81 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
          Cell 20 - Address: 52:8B:80:EC:41:05
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-61 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 21 - Address: 00:18:84:A3:A2:85
                    ESSID:"FON_121"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101800002a3400027a4000042435e0062322f00
                    Extra:ath_ie=dd0900037f01010020ff7f
          Cell 22 - Address: 52:8B:80:EC:41:06
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-62 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 23 - Address: 7E:1B:B2:CB:A4:D4
                    ESSID:""
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: DA:10:42:7A:9D:01
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 25 - Address: DA:10:42:7A:9D:02
                    ESSID:""
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 26 - Address: 7E:1B:B2:CB:A4:D5
                    ESSID:""
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 27 - Address: 7E:1B:B2:CB:A4:D6
                    ESSID:""
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101000003a4000027a4000042435e0062322f00
          Cell 28 - Address: 00:17:33:57:4D:DC
                    ESSID:"Neuf WiFi"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
wlan0     Scan completed :
          Cell 01 - Address: 52:8B:80:EC:41:04
                    ESSID:"Cheznous"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=-70 dBm 
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003970db6188
          Cell 02 - Address: 00:18:39:23:44:DA
                    ESSID:"ALBARDO"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=47/100  Signal level=-78 dBm 
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000006186d55241
          Cell 03 - Address: 00:09:5B:E9:F5:48
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/100  Signal level=-78 dBm 
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000025dde3c9bb
          Cell 04 - Address: 00:14:A4:7D:C8:AF
                    ESSID:"passage"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/100  Signal level=-68 dBm 
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000003b6034cfab6
          Cell 05 - Address: 52:8B:80:EC:41:06
                    ESSID:""
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level=-68 dBm 
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000003970daf8e7
          Cell 06 - Address: DA:10:42:7A:9D:00
                    ESSID:"freebox"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/100  Signal level=-84 dBm 
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000072c6603c15 

```

```

sudo iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"Cheznous" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 52:8B:80:EC:41:04  
          Bit Rate=54 Mb/s   Tx-Power=27 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B  
          Encryption key:6B50-8BCB-6D73-B424-E28E-628D-3EFB-B768-2DF9-EB7D-39F0-976F-99FC-B7F8-1823-50B6 [2]
          Link Quality=52/100  Signal level=-70 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by trigsenior on 2008-09-23
seems to be working kind of still much slower than normal.

---


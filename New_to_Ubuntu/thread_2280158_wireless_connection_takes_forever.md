---
title: "wireless connection takes forever"
date: 2015-05-28
forum: New to Ubuntu
---

### Post by anou2 on 2015-05-28
Hello, completely new to ubuntu. LOVE it so far and was able to work everything out EXCEPT: when I try to connect to wireless network (both at home and in cafes) it either takes forever to connect (~5min) or it does not connect at all. frustrating. 

When it does not connect after a few min I do a combination of: 
*enabling/ disabling network, and 
*connecting/disconnecting from network. 
....After several tries it usually does connect. 
Sometimes between all this I get the message that Ubuntu experienced a problem it would like to report. ("system program problem detected. do you want to report the problem now?")

Details: 
I installed wicd to see if that makes a difference but it does not. So I am back to the default one. 
I have a Lenovo Yoga, and the hard drive is partitioned with windows8 on the other side. 

Let me know if you need to know anything else to help me figure this out!
Truly appreciated!

---

### Post by wildmanne39 on 2015-05-28
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by anou2 on 2015-05-29
Hi thank you for your reply. 
I ran the wireless info script, and can not identify the problem. 
The wireless network devices (lspci, lsusb, PCMCIA) say this:

```
##### lspci #############################

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f3:000a Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################
```

"broadcom" did not appear in the output. 

What else could I look for? 
Thank you!

---

### Post by wildmanne39 on 2015-05-29
You need to post the complete file here by clicking on # and put the output between the brackets.
Thanks

---

### Post by anou2 on 2015-05-29
ok, found the #. 
Thanks!

```

########## wireless info START ##########

Report from: 29 May 2015 10:09 PDT -0700

Booted last: 28 May 2015 12:01 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f3:000a Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              494362  1 r8723au
wmi                    19193  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2268:9dff:fef5:2fd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:653 errors:0 dropped:2266 overruns:0 frame:0
          TX packets:778 errors:0 dropped:68 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73804091 (73.8 MB)  TX bytes:101549169 (101.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ocean"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ocean' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=12 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       748     1  3 May28 ?        00:40:16 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ocean] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723au
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Kaiah:           Infra, <MAC 'Kaiah' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Madhulkness:     Infra, <MAC 'Madhulkness' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Homebase:        Infra, <MAC 'Homebase' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    SAWAZO:          Infra, <MAC 'SAWAZO' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    JAMES-PC_Network2: Infra, <MAC 'JAMES-PC_Network2' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP
    EnGeniusFEDD88:  Infra, <MAC 'EnGeniusFEDD88' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    *ocean:          Infra, <MAC 'ocean' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA2

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

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

[[/etc/NetworkManager/system-connections/Caffe Vita WiFi]] (600 root)
[connection] id=Caffe Vita WiFi | type=802-11-wireless
[802-11-wireless] ssid=Caffe Vita WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ocean]] (600 root)
[connection] id=ocean | type=802-11-wireless | permissions=user:anuscheh:;
[802-11-wireless] ssid=ocean | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Caffe Vita]] (600 root)
[connection] id=Caffe Vita | type=802-11-wireless
[802-11-wireless] ssid=Caffe Vita | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/zebra]] (600 root)
[connection] id=zebra | type=802-11-wireless
[802-11-wireless] ssid=zebra | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RowHouse]] (600 root)
[connection] id=RowHouse | type=802-11-wireless
[802-11-wireless] ssid=RowHouse | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Battleship]] (600 root)
[connection] id=Battleship | type=802-11-wireless
[802-11-wireless] ssid=Battleship | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ocean' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ocean"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d500126a50
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Kaiah' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Kaiah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002957e55c545
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002957e5a425a
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002957e58bb92
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002957e58c3f4
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Madhulkness' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Madhulkness"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000980fa30909
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Homebase' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Homebase"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007f25096440b
                    Extra: Last beacon: 2144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'SAWAZO' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"SAWAZO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000175d863963a
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'JAMES-PC_Network2' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"JAMES-PC_Network2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000995afc180
                    Extra: Last beacon: 52ms ago

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8723au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[72971.359705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 4 times)
[73014.571036] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[73014.977611] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[73016.533436] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-05-29
I do not see a wifi device, is it internal or usb? It is possible it is going out or is loose.

If you have the legacy bios you can see if there is  a setting in the bios to turn it on, or reset the bios.

I see a bluetooth device but that is it.

---

### Post by anou2 on 2015-05-29
yes, it is internal, I have a Lenovo yoga laptop, and am using the wireless card that comes with it. Would have to look up what that is on the windows side, (I don't know how to do that from here), but can get that information if it helps.
The weird thing is it works well from the windows partition..the connection is not a problem!

What does that mean "If you have the legacy bios you can see if there is a setting in the bios to turn it on, or reset the bios"? Is that for the wireless device? Or for the computer? (sorry, really no idea what this means).

Thanks for looking at the file and for your help!

---

### Post by wildmanne39 on 2015-05-29
It looks like this may be your device but it shows as a usb device.
> 0bda:1724 Realtek Semiconductor Corp.
I am researching it now.

---

### Post by wildmanne39 on 2015-05-29
Please do:
```
sudo modprobe r8723au
```
Then:
```
modinfo r8723au
```
post the output of the second command and did your wifi come on after you ran the first command?
Thanks

---

### Post by anou2 on 2015-05-29
Ok. Nothing I noticed changed after the first command. The wireless did not come on. I am attaching the output I got after the second command. 

Just so I am clear:I do get the wireless to work, but it takes a lot of clicking and unclicking the "Enable Networking" and "Enable Wifi" and "Disconnect" options in the pull down menu.
```
filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/staging/rtl8723au/r8723au.ko
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
version:        v4.1.6_7336.20130426
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     1CE6EBBC2494E17D3D73FFD
alias:          usb:v0BDAp0724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8724d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_regulatory_id:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_btcoex_enable:Enable BT co-existence mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)


```

---

### Post by wildmanne39 on 2015-05-29
Your device is driven by that driver, that is good, now before you reboot the computer after you loaded the driver please run and post a new wireless script file so we can see if it is scanning now and your router settings.
Thanks

---

### Post by anou2 on 2015-06-02
Hi, I have not been able to resolve this. Any help truly appreciated, since I now have to use my ipad every time I want to get to the internet, and that is truly inconvenient. 
Anything else I can try/ check/ look at/ look for?

---

### Post by wildmanne39 on 2015-06-02
Please do what I asked in post 11.
Thanks

---

### Post by anou2 on 2015-06-02
Ha. Thanks! Did not see that there as a second page (ahem.):oops: 			..
SO since I had rebooted my computer, and I was not sure what driver you meant, I redid:
sudo modprobe r8723au
modinfo r8723au

This gives me:
> filename:       /lib/modules/3.16.0-38-generic/kernel/drivers/staging/rtl8723au/r8723au.ko
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
version:        v4.1.6_7336.20130426
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     1CE6EBBC2494E17D3D73FFD
alias:          usb:v0BDAp0724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8724d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_regulatory_id:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_btcoex_enable:Enable BT co-existence mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)



and then ran the wireless identification script you pointed me to at the beginning of our thread.
Below is the wireless-info.txt that was output. 

```

########## wireless info START ##########

Report from: 02 Jun 2015 20:12 PDT -0700

Booted last: 02 Jun 2015 20:09 PDT -0700

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b322 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 2047:0855 Texas Instruments 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f3:000a Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0bda:1724 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              494362  1 r8723au
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2268:9dff:fef5:2fd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:663 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:242572 (242.5 KB)  TX bytes:150132 (150.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"ocean"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'ocean' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=12 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 75.75.75.75
nameserver 75.75.76.76
nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       776     1  0 20:09 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ocean] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723au
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Kaiah:           Infra, <MAC 'Kaiah' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Madhulkness:     Infra, <MAC 'Madhulkness' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *ocean:          Infra, <MAC 'ocean' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    CenturyLink0395: Infra, <MAC 'CenturyLink0395' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

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

[[/etc/NetworkManager/system-connections/Caffe Vita WiFi]] (600 root)
[connection] id=Caffe Vita WiFi | type=802-11-wireless
[802-11-wireless] ssid=Caffe Vita WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ocean]] (600 root)
[connection] id=ocean | type=802-11-wireless | permissions=user:anuscheh:;
[802-11-wireless] ssid=ocean | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Caffe Vita]] (600 root)
[connection] id=Caffe Vita | type=802-11-wireless
[802-11-wireless] ssid=Caffe Vita | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/zebra]] (600 root)
[connection] id=zebra | type=802-11-wireless
[802-11-wireless] ssid=zebra | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RowHouse]] (600 root)
[connection] id=RowHouse | type=802-11-wireless
[802-11-wireless] ssid=RowHouse | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Battleship]] (600 root)
[connection] id=Battleship | type=802-11-wireless
[802-11-wireless] ssid=Battleship | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ocean' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ocean"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000adcbc84e1
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee62e5719f
                    Extra: Last beacon: 44ms ago
          Cell 03 - Address: <MAC 'Kaiah' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Kaiah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee62e0af2b
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee62e08cdb
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee62e41140
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ee62e419a2
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Madhulkness' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Madhulkness"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f0f490d04e
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.16.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-38-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:84:ED:AC:CF:0B:47:36:52:C3:4D:23:BE:C3:56:94:42:36:E6:3B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8723au)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  119.359898] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  119.503360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  121.203417] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  145.689124] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.760632] rtl8723au: Loading firmware rtlwifi/rtl8723aufw_B.bin
[  147.544705] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by wildmanne39 on 2015-06-03
I see you are connected after loading the driver, let's do a couple of things to try to make it work better.

Go into network manger top right corner of the screen and set IVP6 to ignore then save and close window.

We need to turn power management off so do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close.

Now let's make your driver load on startup:
```
sudo su 
echo r8723au >> /etc/modules 
exit
``` 
You need to completely remove wicd if you are going to use network manger they can not both be installed.
Reboot
Thanks

---

### Post by anou2 on 2015-06-03
WildMan, you are awesome. The nly thing about the past directions for you I did not understand was the second code you included.

gksudo gedit /etc/pm/power.d/wireless --> that opens a window named gedit, and tab named wireless
Then I typed into the window:

```
#!/bin/sh/sbin/iwconfig wlan0 power off
```
(I thought you probably meant to include the first line in the code line)

But I don't get what you mean with 

> above exit0, then save gedit, close.

I saved it and closed, but could not find anything like exit0. Could you clarify?
Then I removed wcid and rebooted. 

Status now:
It works better. Now when I start the computer the wireless connection still searches and does not connect automatically, but when I disconnect, and then reconnect to my wireless network, it finds it right away. 

Thanks so much for all your help!

---

### Post by wildmanne39 on 2015-06-03
The file you opened should have looked like the first attachment before you added the line I asked you to add.
Not connecting automatically go to network manager click on edit connection then click on your wifi network and make sure connect automatically is checked.

---

### Post by anou2 on 2015-06-04
Hi, the command did not open a window that looked like that. The window was blank.
I will go back and do it again to check. 

Unfortunately my laptop got tea spilled over it and it is drying, hoping that it can be recovered. I will ping you again with news once it is running again:/

---

### Post by wildmanne39 on 2015-06-04
Okay let us know when you can.

---


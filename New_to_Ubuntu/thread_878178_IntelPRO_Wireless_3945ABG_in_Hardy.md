---
title: "Intel/PRO Wireless 3945ABG in Hardy"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by marcusesses on 2008-08-02
Hi, 

I'm having enormous difficulty connecting to my wireless connection with Ubuntu. I have an Acer Aspire 2920 (with the above mentioned wireless), and the wireless worked no problem with Vista. I posted my problem, which turned into a pretty sizable thread(link is[here]("http://ubuntuforums.org/showthread.php?t=870461&highlight=marcusesses")), but still no luck. I've decided to repost, and I'll put as much hardware information as I can. I've played around with it a bit looking for a solution, but my knowledge of Ubuntu is not nearly adequate enough to solve this problem. 

I thought the problem might be with Ubuntu, so I donwloaded the Debian image, and started to install that, but during the installation, Debian could not "configure my DHCP" as it said, so I thought I'd give Ubuntu another go.

Here's the information....

mjbaron@solanum: ~$ route
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
default         *               0.0.0.0         U     1000   0        0 wlan0


mjbaron@solanum: ~$ iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID: ""  Nickname: ""
          Mode: Managed  Frequency: 5.24 GHz  Access Point: 00:11:95:1F:D4:43   
          Bit Rate=54 Mb/s   Tx-Power=17 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Power Management: off
          Link Quality=86/100  Signal level=-47 dBm  Noise level=-95 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

mjbaron@solanum: ~$ sudo iwlist scan 
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

sudo wlan0     Scan completed :
          Cell 01 - Address: 00:1E:C7:F8:A7:81
                    ESSID:"BELL730"
                    Mode: Master
                    Channel: 3
                    Frequency: 2.422 GHz (Channel 3)
                    Quality=54/100  Signal level=-76 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra: tsf=000000000148c7d3
          Cell 02 - Address: 00:18:D1:4A:59:60
                    ESSID:"SYMPATICO"
                    Mode: Master
                    Channel:5
                    Frequency: 2.432 GHz (Channel 5)
                    Quality=61/100  Signal level=-71 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000006d1b345fb
          Cell 03 - Address: 00:14:D1:43:14:A0
                    ESSID:""
                    Mode:Master
                    Channel: 6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/100  Signal level=-90 dBm  Noise level=-97 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra: tsf=0000001b10390181
          Cell 04 - Address: 00:1D:7E:DA:52:09
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level=-85 dBm  Noise level=-97 dBm
                    Encryption key: on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000178ae7e4188
          Cell 05 - Address: 00:1E:58:EA:D9:CF
                    ESSID:"TheBoys"
                    Mode:Master
                    Channel: 1 1
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/100  Signal level=-69 dBm  Noise level=-97 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000ea30b7ad6
          Cell 06 - Address: 00:13:10:78:AF:7B
                    ESSID:"DTGGlinksys"
                    Mode:Master
                    Channel: 6
                    Frequency: 2.437 GHz (Channel 6)
                    Quality=50/100  Signal level=-77 dBm  Noise level=-97 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000462f3b13b18
          Cell 07 - Address: 00:13:10:09:52:3C
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/100  Signal level=-87 dBm  Noise level=-97 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra: tsf=0000017e3853e18d
          Cell 08 - Address: 00:1A:70:D8:D2:FF
                    ESSID:"linksys"
                    Mode:Master
                    Channel: 6
                    Frequency: 2.437 GHz (Channel 6)
                    Quality=40/100  Signal level=-85 dBm  Noise level=-97 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000052b776c18b
          Cell 09 - Address: 00:1C:B3:AF:71:25
                    ESSID:"DEMC's Network"
                    Mode:Master
                    Channel:4
                    Frequency: 2.427 GHz (Channel 4)
                    Quality=35/100  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key: on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000007451215181
          Cell 10 - Address: 00:1C:B3:AD:57:43
                    ESSID:"Apple Network ad5743"
                    Mode:Master
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=37/100  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key: on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000001885774180
          Cell 11 - Address: 00:16:B6:E6:6F:0A
                    ESSID:"spooky"
                    Mode:Master
                    Channel: 6
                    Frequency: 2.437 GHz (Channel 6)
                    Quality=33/100  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key: on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000e0771ab184
          Cell 12 - Address: 00:1A:70:76:68:BC
                    ESSID:"green tea and puppetry"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/100  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000005e9b47f18a
          Cell 13 - Address: 00:17:9A:21:D5:4A
                    ESSID:"banksbroad"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/100  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000003fe64d181
          Cell 14 - Address: 00:18:39:55:55:34
                    ESSID:"Panty Snot"
                    Mode:Master
                    Channel: 6
                    Frequency: 2.437 GHz (Channel 6)
                    Quality=37/100  Signal level=-87 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000b820d1357
          Cell 15 - Address: 00:17:3F:03:7E:26
                    ESSID:""
                    Mode:Master
                    Channel: 11
                    Frequency: 2.462 GHz (Channel 11)
                    Quality=33/100  Signal level=-89 dBm  Noise level=-97 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000036b846c177

mjbaron@solanum:~$ sudo lshw -C network
  *-> network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:10:7a:34
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5787m-v3.23 ip=192.168.0.104 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:00:97:e4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
mjbaron@solanum: ~$ sudo cat /etc/network/interfaces
> auto lo
iface lo inet loopback


I bought my computer 2 weeks ago, and still can't get the wireless working, so ANY help is immensely appreciated.

Thanks.

---

### Post by phidia on 2008-08-02
Since the previous attempt to help failed I think that taking a look at the Ubuntu wiki on [wireless trouble shooting]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") is in order.
There are guides for specific cards [here]("https://help.ubuntu.com/community/WifiDocs") but as I said previously your card is supposed to be recognized/enabled OOTB.

---

### Post by dwhitney67 on 2008-08-02
Congratulations!  Based on the output from 'iwlist scan', it appears that your wireless chip-set it active and working.

It also appears that your system has designated your wireless interface as 'wlan0'.

Seems like what needs to be done next is to get the Network Manager to manage the 'wlan0' interface.  The user-interface for the Network Manager is (should be) a Gnome applet running on the upper-right of your screen.

Right-click (or left-click) on that applet to see if there is a way to enable the Network Manager to control your wireless interface.

You can also try to run the script in /etc/NetworkManager/dispatcher.d, called '01ifupdown'.
```
sudo /etc/NetworkManager/dispatcher.d/01ifupdown wlan0 up
```
Btw, the first two characters are a zero and a one, not an 'o' and an 'l'.

---

### Post by marcusesses on 2008-08-03
Nop, that didn't work...it said I was connected, but I couldn't do anything...

---

### Post by imho74 on 2008-09-09
Hello,

normally "Intel Corporation PRO/Wireless 3945ABG Network Connection" works by enabling the restricted-modules. You can use this command in the command line:

```
sudo apt-get install linux-restricted-modules
```

or you can use Synaptics:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=58866&d=1202283555[/IMG]

(Pic by spiderbatdad from [URL="http://ubuntuforums.org/showthread.php?t=689068"]Enable restricted Modules)
[/URL]

Regards,
Christian

---


---
title: "New to Ubuntu, internet is slow."
date: 2014-03-12
forum: New to Ubuntu
---

### Post by Sonic_Hedgehog on 2014-03-12
Hey, I'm pretty new to Ubuntu, I recently installed Ubuntu over my existing Windows 7 installation. So far my wireless internet has been rather slow, downloading on Steam before had an average speeeeeed of 1.5MB/s (Australia), but now it's lucky to get 200KB/s. Do I need to reinstall my network card drivers (ralink 802.11n) or change my DNS settings, I think I have changed them to the Google Public DNS, however I might be wrong.

---

### Post by varunendra on 2014-03-13
Welcome to Ubuntu Forums Sonic_Hedgehog! :)

To let us see your overall wireless setup (with sensitive data removed), please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Sonic_Hedgehog on 2014-03-14
Thanks for the reply, I've noticed the internet speed getting better, however if anything in the house starts using internet, my speed drops to a crawl, when it wouldn't on windows.


Here's the wireless info:


```



*************** info trace ***************


***** uname -a *****


Linux msfmainframe 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:2a9c]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Ralink corp. RT3092 Wireless 802.11n 2T/2R PCIe [1814:3092]
    Subsystem: Device [15a9:0015]
    Kernel driver in use: rt2800pci


***** lsusb *****


Bus 002 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 004: ID 1532:0016 Razer USA, Ltd DeathAdder Mouse
Bus 002 Device 003: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0909:001a Audio-Technica Corp. 
Bus 001 Device 003: ID 1058:0748 Western Digital Technologies, Inc. My Passport 1TB USB 3.0
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bgn  ESSID:"BigPond4EA038"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13245  Invalid misc:12973   Missed beacon:0




***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


***** modules *****


# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc


***** iw reg get *****


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


***** route -n *****


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.138      0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0


***** lsmod *****


rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              479757  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: wlan0  [BigPond4EA038] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           13 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *BigPond4EA038:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    BigPondB6C299:   Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2


  IPv4 Settings:
    Address:         10.0.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.138


    DNS:             10.0.0.138
    DNS:             8.8.8.8




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






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"BigPond4EA038"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D426967506F6E64344541303338
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: DD8F0050F204104A00011010440001021041000100103B00010310470010CA597F3C76C75847A05844E5ABBE80D11021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E10420009313132355646374E591054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020084103C000101
                    IE: Unknown: DD090010180209000C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BigPondB6C299"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D426967506F6E64423643323939
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000
                    IE: Unknown: DD8F0050F204104A00011010440001021041000100103B000103104700101848A19B21915D92AE424C784D16A32D1021000B546563686E69636F6C6F721023000E546563686E69636F6C6F72205447102400043538326E1042000931313138564655444E1054000800060050F204000110110012546563686E69636F6C6F722054473538326E100800020084103C000101
                    IE: Unknown: DD090010180200000C0000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BigPond46AB48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e6bd6748b
                    Extra: Last beacon: 20ms ago
                    IE: Unknown: 000D426967506F6E64343641423438
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD830050F204104A0001101044000102103B00010310470010431C2B14032758D79CDB31282C5777431021000754484F4D534F4E1023000A54686F6D736F6E205447102400043738325410420009313035314E543345381054000800060050F20400011011000E54686F6D736F6E2054473738325410080002008410570001001041000100
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00




***** resolv.conf *****


nameserver 127.0.1.1
search BigPond


***** blacklist *****


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


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     259E8826760AAB9E718FD85
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     26219235502295A1CDE028F
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     BD4DED63CAE52A1875B21D1
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8AE9D454A710B1C25F9F518
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1814:0x3092 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


***** dmesg *****


[   18.956386] rt2800pci 0000:05:00.0: irq 49 for MSI/MSI-X
[   18.956428] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3071, rev 0213 detected
[   18.959922] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0008 detected
[   21.725749] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   21.750894] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   21.891112] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.891391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.662167] wlan0: authenticate with <MAC address removed>
[   24.717890] wlan0: send auth to <MAC address removed> (try 1/3)
[   24.719398] wlan0: authenticated
[   24.721857] wlan0: associate with <MAC address removed> (try 1/3)
[   24.724886] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=10)
[   24.724955] wlan0: associated
[   24.724980] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


****************** done ******************

```

---

### Post by Vladlenin5000 on 2014-03-14
Ralink WiFi is always a pain in the... Actually in several parts of the body at once!
I have no experience with such. I hope some expert comments whether or not the current driver is suitable. I think not: **Bit Rate=26 Mb/s** is "g" at best whereas you card should be working as "n" up to 300Mb/s (Tx and Rx).

---

### Post by thenh813 on 2014-03-14
```

wlan0     IEEE 802.11bgn  ESSID:"BigPond4EA038"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   **Tx-Power=20 dBm**   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         ** Link Quality=45/70  Signal level=-65 dBm  **
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          **Tx excessive retries:13245  Invalid misc:12973**  Missed beacon:0

```

Looks like it has to keep resending packets. 20dBm transmit power is a bit low in my opinion, it should be a few dbm higher. It is probablly not in the power range to switch to N mode. A signal level of -65dBm? That is absolutely horrible, you should have at least 1dBm on recieving. Signal level 45/70? It should be at least 55-60 if you are in the house. You are probabally too far from the router for the current signal and transmit levels. Try going right next to the router and seeing if it improves. If no improvement is found, the drivers are tansmitting too weakly and not correctly controling the amplification on the recieved signal. I would definitely try the restricted drivers option from system settings and see if proprietary drivers help. You may have to manually install proprietary drivers, I had to for someone's Dell Laptop to get decent speeds and get rid of dropoffs.

---

### Post by Sonic_Hedgehog on 2014-03-14
Ok thanks, I'll try installing new drivers and moving closer to the router.

Also sometimes the network card just wont start when I turn the computer on, and I need to restart several times in order to get it functional. I should see if there's dust in it or something.

---

### Post by evan8 on 2014-03-14
Everytime I install ubuntu 12.04/13.10 I run this command in the terminal first right away . It was an annoying issue that took me a few weeks to finally find the real fix.

   [COLOR=#0000cd][FONT=Ubuntu Mono][SIZE=4]echo "[/SIZE][/FONT][/COLOR][COLOR=#0000cd][FONT=Ubuntu Mono][SIZE=4]**options rtl8192ce swenc=1 ips=0 fwlps=0**[/SIZE][/FONT][/COLOR][COLOR=#0000cd][FONT=Ubuntu Mono][SIZE=4]"[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][SIZE=4] | [/SIZE][/FONT][/COLOR][COLOR=#800000][FONT=Ubuntu Mono][SIZE=4]sudo tee [/SIZE][/FONT][/COLOR][COLOR=#800000][FONT=Ubuntu Mono][SIZE=4]**/etc/modprobe.d/rtl8192ce.conf**[/SIZE][/FONT][/COLOR]
 

  I had the same issue with slow wifi. BUt this fixes it for good right away

Edit : Where "[COLOR=#800000][FONT=Ubuntu Mono][SIZE=4]**rtl8192ce" is put your driver.**[/SIZE][/FONT][/COLOR]

---

### Post by varunendra on 2014-03-15
Wow! So many suggestions and thoughts! Glad to see people interested in helping. :)

However, a few of the concerns are not quite right and need some correction, with intention of sharing knowledge to improve the quality of help offered. 

But first, my own suggestions regarding the problem -
> **Sonic_Hedgehog said:**
> 
```
***** iwlist *****

wlan0     Scan completed :
          **[COLOR="#0000CD"]Cell 01[/COLOR]** - Address: <MAC address removed>
                    **[COLOR="#FF0000"]Channel:6[/COLOR]**
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"BigPond4EA038"
                    ....*<snip>*....
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"BigPondB6C299"
                    ....*<snip>*....
          **[COLOR="#0000CD"]Cell 03[/COLOR]** - Address: <MAC address removed>
                    **[COLOR="#FF0000"]Channel:6[/COLOR]**
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"BigPond46AB48"
                    ....
                    IE: IEEE 802.11i/**WPA2** Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                    ....
                    IE: **[COLOR="#FF0000"]WPA[/COLOR]** Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**

```
I am not yet familiar with 20/40MHz dual-band routers or how Linux tools recognize them, so I'd have to ask you this -

Is your router a dualband router or do you have 3 routers/access-points as shown by "iwlist scan" above?

For now, assuming these ARE 3 independent routers, if you connect to the last one listed above and have admin access to it, please change its encryption to pure WPA2-PSK with AES (CCMP) like the previous two. Currently it is set to WPA/WPA2 mixed mode with TKIP, something that should be avoided for sake of performance. Of course ignore this if you only connect to the first (and/or also the 2nd) one.

In the router you are currently connected to as per the above outputs, try changing the channel to 1 or 11. They usually offer better signal quality. Reboot the router after Saving any changes you make.

Apart from these changes in the router, try this in Ubuntu -
```
echo "options rt2800pci nohwcrypt=Y" | sudo tee /etc/modrprobe.d/rt2800pci.conf
```
Followed by a reboot or -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci
```
This will load the driver with a parameter that usually helps if the traffic rate is too high for the chip to keep up with packet encryption.

If these changes don't help, also try (temporarily, for a test at least) disabling "N" channel in the router if it allows that (set it to a/b/g or b/g mode only if it is in a/b/g/n or b/g/n mode). Like before, reboot the router after saving the change if you try this.

Test and report back if any of the above ones can help improvising the speed. If not, we'll try a newer driver - the correct way.

> **Sonic_Hedgehog said:**
> Also sometimes the network card just wont start when I turn the computer on, and I need to restart several times in order to get it functional. I should see if there's dust in it or something.
That's a good idea, please do check the card as well as antenna contacts to the card. Dusting does help sometimes.
======================================

Now some explanation to suggestions made by our other friends.
> **Vladlenin5000 said:**
> I hope some expert comments whether or not the current driver is suitable. I think not: **Bit Rate=26 Mb/s** is "g" at best whereas you card should be working as "n" up to 300Mb/s (Tx and Rx).
I do not trust this version of the driver either, but we always tend to try the trivial changes first that can be easily reverted if needed. By doing so we move from easy to difficult hoping to avoid the relatively difficult or potentially problematic solutions (like compiling a driver everytime a kernel upgrade happens) if possible.

The "best" speed for "g" mode is 54 Mb/s, and people do get that much from it if everything else is good. I believe you already know that the "300 Mb/s" speed depends on many things - including not only whether the router supports it or not, but also some surrounding factors that can't always be controlled in real world. At the very basic level, the speed displayed by iwconfig would be the "negotiated" speed between the router and the card, not necessarily what they both "Can" support.

> **thenh813 said:**
> 20dBm transmit power is a bit low in my opinion, it should be a few dbm higher.
...A signal level of -65dBm? That is absolutely horrible, you should have at least 1dBm on recieving.
...Signal level 45/70? It should be at least 55-60 if you are in the house.
...I would definitely try the restricted drivers option from system settings and see if proprietary drivers help.
I'm glad to see someone showing interest in such details, very few people do. :) I hope understanding them better will encourage you gain more knowledge about wifi. I don't know everything, but I'll share what I know -

The signal level you see in iwconfig is (when shown in negative) is noise Vs signal ratio, and is _ALWAYS_ in negative. [s]A value below -55 is good, -50 or below is very good, and yes -65 is not so good, but is okay. Anything above -68 will usually have bad connectivity/speed.[/s] *(EDIT: Not sure about this part anymore, see thenh813's post below)*

You are right about the Signal level, 45/70 is not good. But be aware that it is something that is not always displayed correctly by all drivers. Some would even show 0/70 or 10-15/70, but will still have good connection. That being said, I *believe* this driver does not have such problem and what it is showing is a actual signal quality, but I'm not entirely sure.

If the restricted driver is provided by "Additional Drivers" dialogue, that may be worth trying. Otherwise the one downloaded from Ralink's site may not even compile on the kernel the OP is using. Vladlenin5000 is correct about Ralink in this respect - they are not very keen on updating their drivers for Linux, and whether it will work better or rather crash the system - is mostly a matter of luck. Fortunately, the open source drivers keep getting better and the latest ones usually make the performance at least usable.

> **evan8 said:**
> echo "options rtl8192ce swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
....
Edit : Where "rtl8192ce" is put your driver.
Hey evan8! Glad to see you already started sharing what you earned here :D **[FONT=Comic Sans MS]However...[/FONT]**
..those parameters are applicable to only some Realtek drivers, not Ralink's.

To see which parameters are available for a driver, you can use the "modinfo" command. For example -
```
modinfo rt2800pci
```
Gives, among other things -
```
filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
....
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
**parm:           [COLOR="#0000CD"]nohwcrypt[/COLOR]:**Disable hardware encryption. (bool)
```
Which means only one parameter - "nohwcrypt" is available for this driver and it accepts "bool(ean)" value (Y or N).

Lastly, I would like to declare that I'm not an expert in wireless communications and what I shared above is my personal understanding/interpretation of what I have seen/read here and there over time. So don't rely on what I told above, I may be wrong and I'm always open for corrections. :)

---

### Post by thenh813 on 2014-03-15
@[**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629")
> 
...A signal level of -65dBm? That is absolutely horrible, you should have at least 1dBm on recieving.

My bad, I made a mistake, that is the signal to noise ratio. I was thinking it was the strength of the recieved signal. It should be negative if it is the signal to noise ratio. In this case the lower the better, a number above 0 indicates more noise/distortion than signal. I think anything more than -50dBm is excellent. Unless you are using a flipped scale (which this is not) then anything over +50dBm is good.

> 
Lastly, I would like to declare that I'm not an expert in wireless  communications and what I shared above is my personal  understanding/interpretation of what I have seen/read here and there  over time. So don't rely on what I told above, I may be wrong and I'm  always open for corrections. :smile:


I am also open to corrections, thank you for pointing out my error.

As for noise ratio I found this relating to video transmission/cable:
> 

S/N dBm - - - - - S to N ratio - - - - -                  Picture quality

-60 dBm - - - - -                 1,000 to 1 - - - - - -               Excellent, no noise apparent (like HD).
      -50 dBm - - - - -                     316 to 1 - - - - - -                Good, small noise, qual good (like SD).
      -40 dBm - - - - -                     100 to 1 - - - - - -                Reasonable, fine grain/snow (like VHS).
      -30 dBm - - - - -                       32 to 1 - - - - - - -                Poor pic. great deal of noise (like old, damaged VHS tape).
      -20 dBm - - - - -  10 to 1 - - - - - - -                Unusable picture, mostly colored static (useless).


Same thing with a radio, bad signal=static.


@[**[COLOR=#000000]Sonic_Hedgehog[/COLOR]**]("http://ubuntuforums.org/member.php?u=1910503") In any case, the drivers could be causing the issue. Proprietary drivers may be required, although increasing the signal strength will help also. Maybe you could go into the router settings and increase Tx (transmit) strength or switch to N mode and double bandwidth (40Mhz instead of 20Mhz) if it allows. You definitely have good quality, just a weak signal. Strengthening it is probabally easier to try first than messing with drivers more if updating did nothing. Could you try moving the router closer (if the modem can be hooked up there also)? I just want to see what more power or a closer proximity will make for the signal. Where I live I am forced to use 20Mhz mode bacause all the other channels are used up (yes, there are 13 other people with WiFi) and it really sucks. I reccommend using dual channel (40Mhz) if possible because it uses two channels. That would be like using two TV channels to transmit a picture of double size, sending two 360p singals to make 720p. It is a large enhancement. But if the signals are weak, it can still help because it has two ways to send data, if one fails, the others can be tried. This doubles the signal transmit success rate.

---

### Post by Sonic_Hedgehog on 2014-03-16
Thanks for all the help, you guys rock :D

I installed the proper Ralink drivers following another tutorial, and now my download speed is faster than that on windows!

I can't put the computer closer to the router or vice versa anytime soon, but at the moment the issue seems to be solved. I'll give the computer a quick dusting, and mess with some router settings to see if I can boost the range or something.
Thanks for the help guys :)

---

### Post by QIII on 2014-03-16
For the benefit of others and to allow those who have helped you here learn something new, could you please post the source of that tutorial?

Thanks.

---

### Post by thenh813 on 2014-03-16
You are welcome for the help.
If you want to try something else I just thought of that might increase the speed, try using OpenDNS. I have heard it speeds up initially loading pages, plus they block access to websites that are "bad" (viruses/scams, inappropriate popups, etc) by default. You can actually get a free account if you want controll over what sites are allowed or blocked and at what times of the day, a lot of businesses (and I think schools also) use it. I would keep your secondary DNS set to Google and set your primary to OpenDNS just to see if connections start faster. Pick one of the below addresses for DNS server if you want to try it.

```

OpenDNS IP addresses:

[LIST]
[*]208.67.222.222 
[*]208.67.220.220 
[/LIST]

```

---


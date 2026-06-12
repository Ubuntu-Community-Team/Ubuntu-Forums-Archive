---
title: "How to make a d-link dwa-123 wireless n 150 work on ubuntu 13.10 (saucy)"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by Dhairyya_Singh on 2014-01-30
I recently installed saucy as part of a dualboot setup. My laptop's internal network adaptor is shot and so I have to use an external d-link dwa-123. I have the installation disc and everything and it works perfectly on windows. However, I cannot get it to work on Ubuntu. How can I go about doing so?

---

### Post by squakie on 2014-01-30
Boot up your Ubuntu installation.

Hold down ctrl/alt and press F1

log in using your normal userid and password (nothing shows when you type your password), pressing enter after each one

type:

lsusb | grep Wireless <press enter>  case is important here, so use the captial "W"

if nothing is output then:

lsusb <press enter>

copy those outputs and post them back here.

Explanation:  The disk that came with your adapter contains the driver for the device, but that driver is for Windows only.  The outputs above with provide us with a manufacturer id and product id for the chipset your adapter is actually using.  This is different from just the make and model as you see on a box.  With that information, we can try to help you get the driver installed for linux and get it working.

---

### Post by Dhairyya_Singh on 2014-02-01
Thanks a lot for your easy to understand reply squakie!

Here is the info you asked for:```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0cf3:311d Atheros Communications, Inc.
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6458 Microdia
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 0955:7100 NVidia Corp. Notion Ink Adam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 2001:3310 D-Link Corp.
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Dhairyya_Singh on 2014-02-01
Note, that is my lsusb output. Not the output for "[COLOR=#000000]lsusb | grep Wireless <press enter> case is important here, so use the captial "W""[/COLOR]

---

### Post by westie457 on 2014-02-01
After a search for the ID 2001.3310 got this hit. [http://askubuntu.com/questions/371300/how-do-i-get-a-usb-wi-fi-d-link-dwa-125-rev-d1-rtl8188etv-working](http://askubuntu.com/questions/371300/how-do-i-get-a-usb-wi-fi-d-link-dwa-125-rev-d1-rtl8188etv-working)

Scroll the page to about half way. chilli555 has an answer there.

---

### Post by Dhairyya_Singh on 2014-02-01
I already looked at the link in your post before I posted my question.
I'm sorry but I just cannot understand it :(
Can you give me detailed, easier to follow instructions? I would really appreciate it.

---

### Post by westie457 on 2014-02-01
```
[FONT=Ubuntu Mono]sudo apt-get install git
[/FONT]git clone https://github.com/purchae/rtl8188eu.git
cd rtl8188eu
make
sudo make install
sudo modprobe -r rtl8192cu [FONT=Ubuntu Mono]sudo modprobe 8188eu[/FONT]
```
I cannot make this any simpler than open a terminal (pressing Ctrl+Alt+T) and copy the above commands one at a time and paste into the terminal.

Then when a future update to the kernel breaks the driver run the last four commands to re-compile and load the driver.

One line is one command.

Good luck.

---

### Post by Dhairyya_Singh on 2014-02-01
When pasting and entering the very first command, I'm getting this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package git

What should I do?

---

### Post by Dhairyya_Singh on 2014-02-01
The next command then predictably gives me this:
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git

---

### Post by westie457 on 2014-02-01
> **Dhairyya_Singh said:**
> When pasting and entering the very first command, I'm getting this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package git

What should I do?
Looks like you need to alter your software sources.

Open 'Software Centre' click on 'Edit' and the 'Software Sources'.
In the first tab of the window make sure the top four choices are selected. Close the window and exit Software Centre.

In the terminal ```
sudo apt-get update
``` to reload the repositories.
Then run the commands again.

Good luck.

---

### Post by Dhairyya_Singh on 2014-02-01
I could sucessfully install git following what you said.

However,
The command: 
git clone [https://github.com/purchae/rtl8188eu.git](https://github.com/purchae/rtl8188eu.git)
returned this: remote: Repository not found.
fatal: repository 'https://github.com/purchae/rtl8188eu.git/' not found

So, I went ahead and searched for an alternate github page and found this: [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

Tried to install this with the command line: 
 git clone [https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

It installed the package fine. Then I went forward to the next commands. Everything went along fine. I could enter the rtl8188eu folder and make compiled the drivers and went ahead and installed but then when I ran the command: 
sudo modprobe -r rtl8192cu [FONT=Ubuntu Mono]sudo modprobe 8188eu

It returned: FATAL: Module sudo not found

So I considered running them seperately. I ran: [/FONT]
sudo modprobe -r rtl8192cu [FONT=Ubuntu Mono]

and nothing happened. It just went on to the next line ready for the next command.
So then I ran: [/FONT][FONT=Ubuntu Mono]sudo modprobe 8188eu

and again nothing happened. Same as before and my adapter sitll isnt recognized!

Please HELP!
[/FONT]

---

### Post by Dhairyya_Singh on 2014-02-01
bump...

---

### Post by varunendra on 2014-02-01
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Dhairyya_Singh on 2014-03-10
My wireless script output. Please help!
```


*************** info trace ***************

***** uname -a *****

Linux DSPCUbuntu13 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1785]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:184a]
    Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 0cf3:311d Atheros Communications, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6458 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 2001:3310 D-Link Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"Asus_Dhairyya"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate:43.3 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:30  Invalid misc:5671   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

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
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

***** lsmod *****

ath3k                  13318  0 
bluetooth             371874  23 bnep,ath3k,btusb,rfcomm
rt2800usb              27005  0 
rt2x00usb              20713  1 rt2800usb
rt2800lib              79963  1 rt2800usb
ath9k                 151173  0 
rt2x00lib              55238  3 rt2x00usb,rt2800lib,rt2800usb
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  4 ath9k,rt2x00lib,rt2x00usb,rt2800lib
crc_ccitt              12707  1 rt2800lib
cfg80211              479757  4 ath,ath9k,mac80211,rt2x00lib

***** nm-tool *****

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


- Device: wlan0  [Asus_Dhairyya] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           26 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Asus_Dhairyya:  Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
    dlink:           Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WEP
    VidyaPrakash:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WEP

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             172.17.7.1
    DNS:             203.147.88.2



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
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Asus_Dhairyya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000229219fea
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000D417375735F4468616972797961
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DDA30050F204104A0001101044000102103B0001031047001063041253101920061228C86000AEF5B0102100154153555354656B20436F6D707574657220496E632E10230013576972656C6573732057505320526F757465721024000752542D4E3130451042000F3132333435363738393031323334371054000800060050F2040001101100184153555320576972656C6573732057505320526F75746572100800020086
          Cell 02 - Address: <MAC address removed>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000041fdc176
                    Extra: Last beacon: 2236ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0600E04C020160
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"VidyaPrakash"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000eeb1c26d
                    Extra: Last beacon: 36ms ago
                    IE: Unknown: 000C56696479615072616B617368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F4


***** resolv.conf *****

nameserver 127.0.1.1
search ASUS

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

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     76BAD1F8D6CC9AF64EFBFF7
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8D972A7DDE6652BA484C8AE
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     5CFE65EA16A08E63C627D96
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     26219235502295A1CDE028F
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     3C8D10ED309094E2B73D591
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8AE9D454A710B1C25F9F518
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

***** dmesg *****

[   16.929963] ath: phy0: ASPM enabled: 0x43
[   16.929975] ath: EEPROM regdomain: 0x60
[   16.929979] ath: EEPROM indicates we should expect a direct regpair map
[   16.929986] ath: Country alpha2 being used: 00
[   16.929990] ath: Regpair used: 0x60
[   19.429713] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.430412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.727246] wlan0: authenticate with <MAC address removed>
[   21.745352] wlan0: send auth to <MAC address removed> (try 1/3)
[   21.748465] wlan0: authenticated
[   21.749699] wlan0: associate with <MAC address removed> (try 1/3)
[   21.753763] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   21.753816] wlan0: associated
[   21.753827] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

****************** done ******************


```

---

### Post by varunendra on 2014-03-10
Help with what?

In your original post ("only" one and a half month ago), you said your internal card was "shot". But from what I can see in the report, it is not only working but you seem to be connected with it.

So what do you need help with now?

---

### Post by Dhairyya_Singh on 2014-03-12
Yes, one and a half months ago because I got fed up with trying to fix this problem after hours and hours of looking around for any instructions I could find which I could also understand as a begginer.

Yes, after one and a half months when I booted into Ubuntu again, the internal network adapter miraculously started working again (It still doesn't work in Windows though). However it is still a bit iffy sometimes. If you read my original post, my question is how I can make the d-link dwa-123 start working. NOT how do I connect to the internet. Just because I can connect now doesn't mean my problem is resolved. I still want to understand how to make the adapter work so in the future if my internal adapter stops working again, I can use the external one.

Hence the "Please Help!"

If you know how I can get the external adapter to start working, I would really appreciate your help.

---


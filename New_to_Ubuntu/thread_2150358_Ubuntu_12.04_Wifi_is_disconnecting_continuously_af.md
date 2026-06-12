---
title: "Ubuntu 12.04 Wifi is disconnecting continuously after undefined period on Laptop."
date: 2013-05-31
forum: New to Ubuntu
---

### Post by ymahmood on 2013-05-31
Hi All.

I have just installed Ubuntu 12.04 on my Laptop Lenovo B570e. Wifi connection is not continuous. I mean after some time it shows that connection is disconnected and again after few seconds it connects automatically. I have searched many forums but in vain. Please help me anybody. Thanks

---

### Post by wildmanne39 on 2013-05-31
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Deviljho on 2013-05-31
Yes, the open source WIFI drivers are pretty terrible. This is a very large problem with Ubuntu. Every PC I've tried Ubuntu on with WIFI has had this problem (and numerous other WIFI issues). I think the easiest and least time wasting probable solution would be to use ndiswrapper, which lets you install the Windows WIFI driver.

Please type the following command into the Terminal and post the output.
 > lspci

---

### Post by wildmanne39 on 2013-06-01
>  open source WIFI drivers are pretty terribleNot really a true statement, there are issues with any of the drivers from time to time not exclusive to open source and most issues can be resolved with a little effort.
> I think the easiest and least time wasting probable solution would be to use ndiswrapperNot true this should only be used as a last option and is almost nerver needed anymore.
Thanks

---

### Post by Deviljho on 2013-06-01
> **Wild Man said:**
> Not really a true statement, there are issues with any of the drivers from time to time not exclusive to open source and most issues can be resolved with a little effort.
Not true this should only be used as a last option and is almost nerver needed anymore.
Thanks

I know there are issues with 'any of the drivers' as you put it, but from personal experience with WIFI and Ubuntu, on a number of computers, it's unfortunately true.

As for ndiswrapper, again from personal experience, I've found that downloading & compiling the latest ndiswrapper and installing the Windows driver is far, far less time consuming and confusing than trying to install a firmware update that probably won't work anyway.

---

### Post by varunendra on 2013-06-01
> **Deviljho said:**
> I know there are issues with 'any of the drivers' as you put it, but from personal experience with WIFI and Ubuntu, on a number of computers, it's unfortunately true.
May be a problem with wireless + Ubuntu, not really a problem exclusive to the 'open source' drivers, as wild man put it. The proprietary ones may (and often do) also suffer from same, similar, or different issues. That's why we try the native drivers first, it'll be a relatively more stable solution if worked.

> As for ndiswrapper, again from personal experience, I've found that downloading & compiling the latest ndiswrapper and installing the Windows driver is far, far less time consuming and confusing than trying to install a firmware update that probably won't work anyway.
Depends on what device you are using.

Apart from a very few outdated devices (or some very rare ultra-new ones), almost never is ndiswrapper is required, although you 'may' be able to make it work. The reason why we consider it the 'last resort' is that its performance is really poor on linux compared to the native driver if we have a working one.

Except when some critical changes are introduced in the kernel (like in 3.8 series), the native ones work out of box with most of the hardware they are supposed to work with. But when they don't, we do need to go through several steps to hunt down the issue and solve it. Unfortunately, the reasons for different problems vastly differ for different users when it comes to wireless. There are just too many variables to consider at once. But once the problem is found, the next time it is easier to implement the solution than bothering with workarounds like ndiswrapper (provided the device/driver combo does not have a known, unfixed problem, in which case, we may have to use ndiswrapper).

---

### Post by Deviljho on 2013-06-01
At the risk of repeating myself, the default WIFI drivers have been consistently terrible in my own experience. Trying to compile & install firmware updates is considerably more difficult and confusing than ndiswrapper.

---

### Post by ymahmood on 2013-06-01
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

Hello Wild Man

Thanks for your quick rreply. I have run your command and i got a txt file in my Home folder. I did not understand how attachment works. BUt i post data of .txt file. 

```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 

***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: <MAC address removed>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:65   Missed beacon:0


***** rfkill *****

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath9k                 133133  0 
mac80211              555198  1 ath9k
ath9k_common           14054  1 ath9k
ath9k_hw              399665  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
cfg80211              208382  3 ath9k,mac80211,ath

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


- Device: wlan0  [eduroam] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    stw-wohnheim:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    stw-wohnheim:    Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27
    eduroam:         Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    stw-wohnheim:    Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45
    stw-wohnheim:    Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    stw-wohnheim:    Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 51
    *eduroam:        Infra, <MAC address removed>, Freq 2467 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise

  IPv4 Settings:
    Address:         134.102.92.92
    Prefix:          23 (255.255.254.0)
    Gateway:         134.102.93.250

    DNS:             134.102.20.20
    DNS:             134.102.200.14



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
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
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004245c88780e
                    Extra: Last beacon: 916ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319004C756973656E74616C3134350000000005000025
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"stw-wohnheim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004245c887192
                    Extra: Last beacon: 868ms ago
                    IE: Unknown: 000C7374772D776F686E6865696D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010C
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319004C756973656E74616C3134350000000005000025
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960303
                    IE: Unknown: DD1600409604000207A4000023A400004243000062320000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"stw-wohnheim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004245c53600f
                    Extra: Last beacon: 3324ms ago
                    IE: Unknown: 000C7374772D776F686E6865696D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319004C756973656E74616C3133380000000002000025
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004245c541fc3
                    Extra: Last beacon: 3324ms ago
                    IE: Unknown: 0007656475726F616D
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E000081000F00FF0319004C756973656E74616C3133380000000002000025
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD06004096010101
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD050040960B01
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1
search wohnheim.uni-bremen.de

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

***** dmesg *****

[   30.858574] ath: EEPROM regdomain: 0x65
[   30.858577] ath: EEPROM indicates we should expect a direct regpair map
[   30.858580] ath: Country alpha2 being used: 00
[   30.858581] ath: Regpair used: 0x65
[   30.874451] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   30.874705] Registered led device: ath9k-phy0
[   31.416130] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.419333] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.019704] wlan0: authenticate with <MAC address removed>
[   34.033536] wlan0: send auth to <MAC address removed> (try 1/3)
[   34.035206] wlan0: authenticated
[   34.043307] wlan0: associate with <MAC address removed> (try 1/3)
[   34.048259] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=13)
[   34.048350] wlan0: associated
[   34.048640] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.101879] wlan0: authenticate with <MAC address removed>
[   57.115526] wlan0: send auth to <MAC address removed> (try 1/3)
[   57.120764] wlan0: authenticated
[   57.129456] wlan0: associate with <MAC address removed> (try 1/3)
[   57.333169] wlan0: associate with <MAC address removed> (try 2/3)
[   57.536928] wlan0: associate with <MAC address removed> (try 3/3)
[   57.740642] wlan0: association with <MAC address removed> timed out
[   63.613500] wlan0: authenticate with <MAC address removed>
[   63.627040] wlan0: direct probe to <MAC address removed> (try 1/3)
[   63.828774] wlan0: send auth to <MAC address removed> (try 2/3)
[   63.830495] wlan0: authenticated
[   63.840748] wlan0: associate with <MAC address removed> (try 1/3)
[   63.848192] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=14)
[   63.848288] wlan0: associated
[   74.819119] wlan0: authenticate with <MAC address removed>
[   74.832487] wlan0: send auth to <MAC address removed> (try 1/3)
[   74.841446] wlan0: authenticated
[   74.850525] wlan0: associate with <MAC address removed> (try 1/3)
[   75.054267] wlan0: associate with <MAC address removed> (try 2/3)
[   75.257985] wlan0: associate with <MAC address removed> (try 3/3)
[   75.461728] wlan0: association with <MAC address removed> timed out
[   81.338565] wlan0: authenticate with <MAC address removed>
[   81.352072] wlan0: direct probe to <MAC address removed> (try 1/3)
[   81.553861] wlan0: send auth to <MAC address removed> (try 2/3)
[   81.757592] wlan0: send auth to <MAC address removed> (try 3/3)
[   81.759412] wlan0: authenticated
[   81.769552] wlan0: associate with <MAC address removed> (try 1/3)
[   81.775245] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=15)
[   81.775319] wlan0: associated
[  161.687346] wlan0: authenticate with <MAC address removed>
[  161.700497] wlan0: send auth to <MAC address removed> (try 1/3)
[  161.704414] wlan0: authenticated
[  161.714138] wlan0: associate with <MAC address removed> (try 1/3)
[  161.917884] wlan0: associate with <MAC address removed> (try 2/3)
[  162.121597] wlan0: associate with <MAC address removed> (try 3/3)
[  162.325396] wlan0: association with <MAC address removed> timed out
[  168.206820] wlan0: authenticate with <MAC address removed>
[  168.220066] wlan0: direct probe to <MAC address removed> (try 1/3)
[  168.421585] wlan0: send auth to <MAC address removed> (try 2/3)
[  168.425173] wlan0: authenticated
[  168.433482] wlan0: associate with <MAC address removed> (try 1/3)
[  168.438864] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=16)
[  168.438968] wlan0: associated
[  175.708988] wlan0: authenticate with <MAC address removed>
[  175.722331] wlan0: send auth to <MAC address removed> (try 1/3)
[  175.737553] wlan0: authenticated
[  175.747987] wlan0: associate with <MAC address removed> (try 1/3)
[  175.951768] wlan0: associate with <MAC address removed> (try 2/3)
[  176.155513] wlan0: associate with <MAC address removed> (try 3/3)
[  176.359242] wlan0: association with <MAC address removed> timed out
[  182.240629] wlan0: authenticate with <MAC address removed>
[  182.253904] wlan0: direct probe to <MAC address removed> (try 1/3)
[  182.455361] wlan0: send auth to <MAC address removed> (try 2/3)
[  182.457183] wlan0: authenticated
[  182.467335] wlan0: associate with <MAC address removed> (try 1/3)
[  182.476077] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=17)
[  182.476180] wlan0: associated
[  341.486523] wlan0: authenticate with <MAC address removed>
[  341.499811] wlan0: send auth to <MAC address removed> (try 1/3)
[  341.504160] wlan0: authenticated
[  341.513508] wlan0: associate with <MAC address removed> (try 1/3)
[  341.717277] wlan0: associate with <MAC address removed> (try 2/3)
[  341.921000] wlan0: associate with <MAC address removed> (try 3/3)
[  342.124747] wlan0: association with <MAC address removed> timed out
[  348.002097] wlan0: authenticate with <MAC address removed>
[  348.015478] wlan0: direct probe to <MAC address removed> (try 1/3)
[  348.216852] wlan0: direct probe to <MAC address removed> (try 2/3)
[  348.420619] wlan0: direct probe to <MAC address removed> (try 3/3)
[  348.624406] wlan0: authentication with <MAC address removed> timed out
[  354.501550] wlan0: authenticate with <MAC address removed>
[  354.515043] wlan0: direct probe to <MAC address removed> (try 1/3)
[  354.716561] wlan0: send auth to <MAC address removed> (try 2/3)
[  354.718255] wlan0: authenticated
[  354.728461] wlan0: associate with <MAC address removed> (try 1/3)
[  354.736288] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=18)
[  354.736423] wlan0: associated
[  363.454259] wlan0: authenticate with <MAC address removed>
[  363.467343] wlan0: send auth to <MAC address removed> (try 1/3)
[  363.482673] wlan0: authenticated
[  363.493123] wlan0: associate with <MAC address removed> (try 1/3)
[  363.696869] wlan0: associate with <MAC address removed> (try 2/3)
[  363.900608] wlan0: associate with <MAC address removed> (try 3/3)
[  364.104344] wlan0: association with <MAC address removed> timed out
[  375.862065] wlan0: authenticate with <MAC address removed>
[  375.875406] wlan0: direct probe to <MAC address removed> (try 1/3)
[  376.076858] wlan0: send auth to <MAC address removed> (try 2/3)
[  376.078737] wlan0: authenticated
[  376.088829] wlan0: associate with <MAC address removed> (try 1/3)
[  376.097030] wlan0: RX AssocResp from <MAC address removed> (capab=0x421 status=0 aid=19)
[  376.097134] wlan0: associated
[  380.449456] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  381.362383] wlan0: authenticate with <MAC address removed>
[  381.376451] wlan0: direct probe to <MAC address removed> (try 1/3)
[  381.577730] wlan0: send auth to <MAC address removed> (try 2/3)
[  381.579460] wlan0: authenticated
[  381.589650] wlan0: associate with <MAC address removed> (try 1/3)
[  381.598163] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=20)
[  381.598275] wlan0: associated

****************** done ******************

```

---

### Post by ymahmood on 2013-06-01
> **Deviljho said:**
> Yes, the open source WIFI drivers are pretty terrible. This is a very large problem with Ubuntu. Every PC I've tried Ubuntu on with WIFI has had this problem (and numerous other WIFI issues). I think the easiest and least time wasting probable solution would be to use ndiswrapper, which lets you install the Windows WIFI driver.

Please type the following command into the Terminal and post the output.

Thannks Devilhho ! 

Here are your requred results.

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by varunendra on 2013-06-01
> **Deviljho said:**
> At the risk of repeating myself, the default WIFI drivers have been consistently terrible in my own experience. Trying to compile & install firmware updates is considerably more difficult and confusing than ndiswrapper.
Those are proprietary drivers that you need to compile :)

Open-source ones are almost always available in packaged form, which you can just double-click to install, if they're not already included in the kernel :)

@ ymahmood,
Please edit your post with the output of Wild Man's script to wrap the output part in '**Code**' tags. It preserves the formatting, prevents the codes from turning into smileys, and makes your post look clean, compact and more readable. Follow the "Code tags example" link in my signature to see how to do that.

You are using ath9k driver for your card. I have exactly the same card (AR9285) in my laptop, but unfortunately, no wireless networks around to test myself. The last time I checked its connectivity, I was on kernel 3.2.0-36 (still on the same one) and it worked wonderfully.

However, as of now, please try -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
Then try to connect and see if it helps. This is a temporary change and will be lost at next boot. If it seems to help, we can make it permanent.

Also, is it a university campus wifi?

There is a known problem with Network Manager when there are too many Access Points available with same SSID. In that case, you may try one of two things (Only if the above code doesn't help) -
Open Network Manager drop-down menu > Edit Connections > Wireless tab > double-click your wireless connection to edit it. Then, in the BSSID field, enter the MAC address of the nearest access point whose signal seems strongest as per the script output (or 'sudo iwlist scan' command). Click 'Save' and close the connection settings box. Retry to connect and see if the connection sticks.

Downside of the workaround is that you may have to manually change the BSSID everytime you move from one location to another within the campus (where the SSID is same).

Alternatively, you may try 'wicd' instead of Network Manager. It often works better in such cases.

---

### Post by ymahmood on 2013-06-01
> **varunendra said:**
> Those are proprietary drivers that you need to compile :)

Open-source ones are almost always available in packaged form, which you can just double-click to install, if they're not already included in the kernel :)

@ ymahmood,
Please edit your post with the output of Wild Man's script to wrap the output part in '**Code**' tags. It preserves the formatting, prevents the codes from turning into smileys, and makes your post look clean, compact and more readable. Follow the "Code tags example" link in my signature to see how to do that.

You are using ath9k driver for your card. I have exactly the same card (AR9285) in my laptop, but unfortunately, no wireless networks around to test myself. The last time I checked its connectivity, I was on kernel 3.2.0-36 (still on the same one) and it worked wonderfully.

However, as of now, please try -
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
Then try to connect and see if it helps. This is a temporary change and will be lost at next boot. If it seems to help, we can make it permanent.

Also, is it a university campus wifi?

There is a known problem with Network Manager when there are too many Access Points available with same SSID. In that case, you may try one of two things (Only if the above code doesn't help) -
Open Network Manager drop-down menu > Edit Connections > Wireless tab > double-click your wireless connection to edit it. Then, in the BSSID field, enter the MAC address of the nearest access point whose signal seems strongest as per the script output (or 'sudo iwlist scan' command). Click 'Save' and close the connection settings box. Retry to connect and see if the connection sticks.

Downside of the workaround is that you may have to manually change the BSSID everytime you move from one location to another within the campus (where the SSID is same).

Alternatively, you may try 'wicd' instead of Network Manager. It often works better in such cases.


Thanks varunendra !
I tried following commands.  
```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
but the problem seems not to be solved. 

I have also noticed a common problem. When i make new connection of wifi after deleting previous one, it connects and then disconnects with random periods but when i restart my pc i never connects, i have to delete the previous connection and then new connection. it works again with discontinous. 

Yes it is University campus wifi. :(

---

### Post by claracc on 2013-06-01
My network controller is  Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) and I have had since ubuntu karmic koala the problem of connecting and disconnecting all the time If I used network manager.

I solved the problem installing wicd instead of network managet to control the wifi [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

---

### Post by varunendra on 2013-06-01
> **ymahmood said:**
> I have also noticed a common problem. When i make new connection of wifi after deleting previous one, it connects and then disconnects with random periods but when i restart my pc i never connects, i have to delete the previous connection and then new connection. it works again with discontinous. 

Yes it is University campus wifi. :(
Then try the BSSID trick and let us know if it helps. Crude one, but at least you will have a stable connection if it worked.

If not, then try installing and using wicd, and disable Network Manager.

To install wicd -
```
sudo apt-get install wicd
```

To disable Network Manager -
```
sudo stop network-manager
```
(additionally, remove the tick mark from "Enable Networking" in the drop down list of nm-applet).
For details on how to disable NM : [https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager](https://help.ubuntu.com/community/NetworkManager#Disabling_NetworkManager)

**EDIT:**
claracc beat me to it :D
Thanks claracc for the valuable input !

---

### Post by claracc on 2013-06-01
Thanks to you varunendra for your informative and complete response.

Glad to help

---

### Post by ymahmood on 2013-06-01
If i install wicd i don't see wifi connection logo on my desktop. do you know how to show it? There is another problem with that, when i try to connect, it asks for various information like type of connection, domain name. i dont have any domain name, i have only username and password.

---

### Post by wildmanne39 on 2013-06-01
Part of the issue is that you have more then one network with the same name that makes you connection jump from one to the other continuosly. 

I believe your channel is set on a channel that you can not receive, it is best to try 1 or 11.

You should make this permanent with this command.
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

---

### Post by ymahmood on 2013-06-02
> **Wild Man said:**
> Part of the issue is that you have more then one network with the same name that makes you connection jump from one to the other continuosly. 

I believe your channel is set on a channel that you can not receive, it is best to try 1 or 11.

You should make this permanent with this command.
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Thanks

Thanks wild man. 
> 
I tried to make permanent according to your command but it still not works. I also put MAC address of nearest router with max signal strength. I also tried wicd that is fine but sometime it take much longer time to connect. Other people have ubuntu and they are not facing any problem with the same wifi connection. there are 18000 students in the university and more than 30% have linux/ubuntu. I am totally feddup from ubuntu. Is it this kinda unreliable?

---

### Post by varunendra on 2013-06-02
> **ymahmood said:**
> I also tried wicd that is fine but sometime it take much longer time to connect.
When it does connect, does it remain stable?

When it takes too long to connect, please take a look at system logs, they often do contain hints about the problem -
```
dmesg | grep -iE 'ath|wlan|network|mac80|cfg80'
cat /var/log/syslog | grep -iE 'ath|wlan|network|mac80|cfg80'
```
Post back these outputs if there are errors, warnings or something else suspicious in them.

If others with 'same hardware' can connect without problem, I don't see a reason why you shouldn't be able to.

However, the quality of wireless connection really depends on a lot of things. Mostly, the device and the driver, but like I mentioned before, the device you have and the driver in use both have had a good reputation so far. So even if there is a regression, it should be temporary and should be fixed soon with some update.

You may be already aware that almost all the hardware manufacturers keep 'Windows' in mind while designing their products, so it will naturally work nicely there. Linux drivers are mostly developed and maintained by the open source community, so may take some fiddling and experimenting until it is perfect. And whenever a critical change is introduced in the kernel (not often), it may require a lot of work all over again to make things perfect.

That said, it wouldn't be a bad idea to have a dual boot with windows until Ubuntu get fixed and all set to your liking.

---

### Post by ymahmood on 2013-06-02
> **varunendra said:**
> When it does connect, does it remain stable?

When it takes too long to connect, please take a look at system logs, they often do contain hints about the problem -
```
dmesg | grep -iE 'ath|wlan|network|mac80|cfg80'
cat /var/log/syslog | grep -iE 'ath|wlan|network|mac80|cfg80'
```
Post back these outputs if there are errors, warnings or something else suspicious in them.

If others with 'same hardware' can connect without problem, I don't see a reason why you shouldn't be able to.

However, the quality of wireless connection really depends on a lot of things. Mostly, the device and the driver, but like I mentioned before, the device you have and the driver in use both have had a good reputation so far. So even if there is a regression, it should be temporary and should be fixed soon with some update.

You may be already aware that almost all the hardware manufacturers keep 'Windows' in mind while designing their products, so it will naturally work nicely there. Linux drivers are mostly developed and maintained by the open source community, so may take some fiddling and experimenting until it is perfect. And whenever a critical change is introduced in the kernel (not often), it may require a lot of work all over again to make things perfect.

That said, it wouldn't be a bad idea to have a dual boot with windows until Ubuntu get fixed and all set to your liking.

Yes when it connects it is really stable. 

```

[   12.041647] cfg80211: Calling CRDA to update world regulatory domain
[   13.371724] type=1400 audit(1370168396.367:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
[   13.372318] type=1400 audit(1370168396.367:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
[   15.166635] ath: EEPROM regdomain: 0x65
[   15.166638] ath: EEPROM indicates we should expect a direct regpair map
[   15.166640] ath: Country alpha2 being used: 00
[   15.166641] ath: Regpair used: 0x65
[   15.166644] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   15.166645] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166646] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   15.166647] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166648] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   15.166649] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166650] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   15.166651] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166652] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   15.166653] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166653] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   15.166654] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166655] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   15.166656] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166657] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   15.166658] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166659] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   15.166660] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166660] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   15.166661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166662] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   15.166663] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166664] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   15.166665] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166666] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   15.166667] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   15.166668] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   15.168201] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   15.342501] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.342723] Registered led device: ath9k-phy0
[   15.342730] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050a0000, irq=17
[   15.547856] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   15.547861] cfg80211: World regulatory domain updated:
[   15.547862] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.547863] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.547864] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.547865] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.547866] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.547867] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.642696] type=1400 audit(1370168402.647:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[   19.816248] type=1400 audit(1370168402.823:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
[   19.816595] type=1400 audit(1370168402.823:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
[   27.460231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.094633] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   38.318701] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.149492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.159439] wlan0: authenticate with 00:0f:8f:23:c7:a1
[   41.179852] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
[   41.182005] wlan0: authenticate with 00:0f:8f:23:c7:a1
[   41.189003] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
[   41.191135] wlan0: authenticate with 00:0f:8f:23:c7:a1
[   41.198126] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
[   41.198140] wlan0: authenticated
[   41.206394] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
[   41.410149] wlan0: associate with 00:0f:8f:23:c7:a1 (try 2/3)
[   41.613872] wlan0: associate with 00:0f:8f:23:c7:a1 (try 3/3)
[   41.817623] wlan0: association with 00:0f:8f:23:c7:a1 timed out
[  180.159265] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  180.159308] wlan0: authenticate with 00:0f:8f:23:c7:a1
[  180.175253] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
[  180.378348] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
[  180.728654] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  180.728672] wlan0: authenticate with 00:0f:8f:23:c7:a1
[  180.745099] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
[  180.771952] wlan0: authenticated
[  180.781838] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
[  180.787620] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=10)
[  180.787715] wlan0: associated
[  180.788476] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready



```

---

### Post by varunendra on 2013-06-02
> **ymahmood said:**
> Yes when it connects it is really stable.
Good to hear that !

Was the dmesg output from when it was taking too long to connect? I couldn't notice any usual suspects in it. Maybe syslog can have clues if it was from a problematic session.

---

### Post by ymahmood on 2013-06-02
> **varunendra said:**
> Good to hear that !

Was the dmesg output from when it was taking too long to connect? I couldn't notice any usual suspects in it. Maybe syslog can have clues if it was from a problematic session.

Yes it was reply when connection was made. So, you need response when it was trying to connect. I will give. This problem comes when i disconnect internet and try to connect it again. For example after restarting system, comming back from hibernation. If it is connected then it is very stable but the main problem is that it takes longer time even sometime doest not connect. RIght now i have switched to windows because it was connecting. Too much pathetic. Do we have any other solution? I can not do this exercise every time when i restart my  pc. or i go from my home to university and then back to room. Please suggest any other solution if possible. Otherwise i have to give up to so called ubuntu..

---

### Post by ymahmood on 2013-06-02
> **varunendra said:**
> Good to hear that !

Was the dmesg output from when it was taking too long to connect? I couldn't notice any usual suspects in it. Maybe syslog can have clues if it was from a problematic session.
Here is reply when it was trying to connect. It was connected after so long time. actually i had to close wicd again and again. when it connects it takes no time. but when not it always say obtaining ip address. then even i wait for minutes it doesnt connect. then i have to restart some time pc some times wicd software then it conect. 
```

Jun  2 12:14:48 ubuntu NetworkManager[947]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  2 12:14:48 ubuntu NetworkManager[947]: <warn> Trying to remove a non-existant call id.
Jun  2 12:14:50 ubuntu kernel: [  200.585814] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:14:50 ubuntu kernel: [  200.606110] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:14:50 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:14:50 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:14:50 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 12:14:51 ubuntu kernel: [  200.807445] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 12:14:51 ubuntu kernel: [  200.809247] wlan0: authenticated
Jun  2 12:14:51 ubuntu kernel: [  200.819420] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:14:51 ubuntu kernel: [  200.826606] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=4)
Jun  2 12:14:51 ubuntu kernel: [  200.826703] wlan0: associated
Jun  2 12:14:51 ubuntu wpa_supplicant[2360]: No network configuration found for the current AP
Jun  2 12:14:51 ubuntu kernel: [  200.827883] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 12:14:51 ubuntu kernel: [  200.829055] wlan0: disassociating from 00:0f:8f:23:c7:a1 by local choice (reason=3)
Jun  2 12:14:51 ubuntu NetworkManager[947]: <info> (wlan0): supplicant interface state: inactive -> disconnected
Jun  2 12:14:52 ubuntu avahi-daemon[715]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 12:14:52 ubuntu avahi-daemon[715]: New relevant interface wlan0.IPv6 for mDNS.
Jun  2 12:14:52 ubuntu avahi-daemon[715]: Registering new address record for fe80::76e5:43ff:fec8:4309 on wlan0.*.
Jun  2 12:14:53 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  2 12:14:59 ubuntu NetworkManager[947]: <info> wpa_supplicant die count reset
Jun  2 12:14:59 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun  2 12:15:10 ubuntu NetworkManager[947]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jun  2 12:15:13 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 12:15:24 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 12:15:35 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jun  2 12:15:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 12:15:58 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  2 12:16:10 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun  2 12:16:24 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Jun  2 12:16:42 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 12:16:49 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> caught signal 15, shutting down normally.
Jun  2 12:16:54 ubuntu NetworkManager[947]: <warn> quit request received, terminating...
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): now unmanaged
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): cleaning up...
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): taking down device.
Jun  2 12:16:54 ubuntu avahi-daemon[715]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun  2 12:16:54 ubuntu avahi-daemon[715]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 12:16:54 ubuntu avahi-daemon[715]: Withdrawing address record for fe80::76e5:43ff:fec8:4309 on wlan0.
Jun  2 12:16:54 ubuntu dhclient: receive_packet failed on wlan0: Network is down
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (eth0): now unmanaged
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (eth0): cleaning up...
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (eth0): taking down device.
Jun  2 12:16:54 ubuntu kernel: [  323.805795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> exiting (success)
Jun  2 12:17:01 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun  2 12:17:01 ubuntu dhclient: send_packet: Network is down
Jun  2 12:17:04 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:04 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:05 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:17:05 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:17:19 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:19 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:19 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:17:19 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:17:19 ubuntu kernel: [  349.427248] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:17:19 ubuntu kernel: [  349.518254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:17:26 ubuntu kernel: [  356.428026] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:17:33 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:33 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:33 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:17:33 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:17:33 ubuntu kernel: [  363.546778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:17:34 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:34 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:34 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:17:34 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:17:34 ubuntu kernel: [  364.137007] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:17:36 ubuntu kernel: [  366.160556] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:17:36 ubuntu kernel: [  366.181126] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:17:36 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:36 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:17:36 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 12:17:36 ubuntu kernel: [  366.381180] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 12:17:36 ubuntu kernel: [  366.395422] wlan0: authenticated
Jun  2 12:17:36 ubuntu kernel: [  366.405135] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:17:36 ubuntu kernel: [  366.448981] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=7)
Jun  2 12:17:36 ubuntu kernel: [  366.449124] wlan0: associated
Jun  2 12:17:36 ubuntu kernel: [  366.449963] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 12:17:38 ubuntu avahi-daemon[715]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 12:17:38 ubuntu avahi-daemon[715]: New relevant interface wlan0.IPv6 for mDNS.
Jun  2 12:17:38 ubuntu avahi-daemon[715]: Registering new address record for fe80::76e5:43ff:fec8:4309 on wlan0.*.
Jun  2 12:17:39 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 12:17:39 ubuntu dhclient: DHCPREQUEST of 10.28.36.244 on wlan0 to 255.255.255.255 port 67
Jun  2 12:17:39 ubuntu avahi-daemon[715]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.28.36.244.
Jun  2 12:17:39 ubuntu avahi-daemon[715]: New relevant interface wlan0.IPv4 for mDNS.
Jun  2 12:17:39 ubuntu avahi-daemon[715]: Registering new address record for 10.28.36.244 on wlan0.IPv4.
Jun  2 12:19:55 ubuntu avahi-daemon[703]: Network interface enumeration completed.
Jun  2 12:19:56 ubuntu kernel: [   13.371724] type=1400 audit(1370168396.367:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=631 comm="apparmor_parser"
Jun  2 12:19:56 ubuntu kernel: [   13.372318] type=1400 audit(1370168396.367:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
Jun  2 12:19:58 ubuntu kernel: [   15.166635] ath: EEPROM regdomain: 0x65
Jun  2 12:19:58 ubuntu kernel: [   15.166638] ath: EEPROM indicates we should expect a direct regpair map
Jun  2 12:19:58 ubuntu kernel: [   15.166640] ath: Country alpha2 being used: 00
Jun  2 12:19:58 ubuntu kernel: [   15.166641] ath: Regpair used: 0x65
Jun  2 12:19:58 ubuntu kernel: [   15.342501] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jun  2 12:19:58 ubuntu kernel: [   15.342723] Registered led device: ath9k-phy0
Jun  2 12:19:58 ubuntu kernel: [   15.342730] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050a0000, irq=17
Jun  2 12:20:02 ubuntu kernel: [   19.642696] type=1400 audit(1370168402.647:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
Jun  2 12:20:02 ubuntu kernel: [   19.816248] type=1400 audit(1370168402.823:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=961 comm="apparmor_parser"
Jun  2 12:20:02 ubuntu kernel: [   19.816595] type=1400 audit(1370168402.823:18): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=961 comm="apparmor_parser"
Jun  2 12:20:10 ubuntu kernel: [   27.460231] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:20:20 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:20 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:20 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:20:20 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:20:21 ubuntu kernel: [   38.318701] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:20:21 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:21 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:22 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:20:22 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:20:22 ubuntu kernel: [   39.149492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:20:24 ubuntu kernel: [   41.159439] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:20:24 ubuntu kernel: [   41.179852] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:20:24 ubuntu kernel: [   41.182005] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:20:24 ubuntu kernel: [   41.189003] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:20:24 ubuntu kernel: [   41.191135] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:20:24 ubuntu kernel: [   41.198126] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:20:24 ubuntu kernel: [   41.198140] wlan0: authenticated
Jun  2 12:20:24 ubuntu kernel: [   41.206394] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:20:24 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:24 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:20:24 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 12:20:24 ubuntu kernel: [   41.410149] wlan0: associate with 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 12:20:24 ubuntu kernel: [   41.613872] wlan0: associate with 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 12:20:24 ubuntu kernel: [   41.817623] wlan0: association with 00:0f:8f:23:c7:a1 timed out
Jun  2 12:20:27 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  2 12:20:33 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 12:20:46 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  2 12:20:55 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 12:21:06 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 12:21:17 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  2 12:21:29 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 12:21:42 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jun  2 12:21:57 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 12:22:04 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jun  2 12:22:22 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:22 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:23 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:22:23 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:22:43 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:43 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:43 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:22:43 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:22:43 ubuntu kernel: [  180.159265] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:22:43 ubuntu kernel: [  180.159308] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:22:43 ubuntu kernel: [  180.175253] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:22:43 ubuntu kernel: [  180.378348] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 12:22:43 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:43 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:43 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:22:43 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:22:43 ubuntu kernel: [  180.728654] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:22:43 ubuntu kernel: [  180.728672] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 12:22:43 ubuntu kernel: [  180.745099] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:22:43 ubuntu kernel: [  180.771952] wlan0: authenticated
Jun  2 12:22:44 ubuntu kernel: [  180.781838] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 12:22:44 ubuntu kernel: [  180.787620] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=10)
Jun  2 12:22:44 ubuntu kernel: [  180.787715] wlan0: associated
Jun  2 12:22:44 ubuntu kernel: [  180.788476] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 12:22:45 ubuntu avahi-daemon[703]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 12:22:45 ubuntu avahi-daemon[703]: New relevant interface wlan0.IPv6 for mDNS.
Jun  2 12:22:45 ubuntu avahi-daemon[703]: Registering new address record for fe80::76e5:43ff:fec8:4309 on wlan0.*.
Jun  2 12:22:46 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:46 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:22:46 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 12:22:46 ubuntu dhclient: DHCPREQUEST of 10.28.36.244 on wlan0 to 255.255.255.255 port 67
Jun  2 12:22:46 ubuntu avahi-daemon[703]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.28.36.244.
Jun  2 12:22:46 ubuntu avahi-daemon[703]: New relevant interface wlan0.IPv4 for mDNS.
Jun  2 12:22:46 ubuntu avahi-daemon[703]: Registering new address record for 10.28.36.244 on wlan0.IPv4.
Jun  2 12:55:40 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:55:40 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:55:40 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Withdrawing address record for 10.28.36.244 on wlan0.
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.28.36.244.
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun  2 12:55:40 ubuntu kernel: [ 2154.462569] wlan0: deauthenticating from 00:0f:8f:23:c7:a1 by local choice (reason=3)
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 12:55:40 ubuntu avahi-daemon[703]: Withdrawing address record for fe80::76e5:43ff:fec8:4309 on wlan0.
Jun  2 12:55:40 ubuntu kernel: [ 2154.555074] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 12:55:40 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:55:40 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 12:55:40 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 12:55:40 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 12:55:41 ubuntu kernel: [ 2155.096366] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:52:41 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:41 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:41 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:52:41 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:52:41 ubuntu kernel: [ 2167.453906] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:52:41 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:41 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:41 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:52:41 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:52:41 ubuntu kernel: [ 2167.996516] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:52:42 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:42 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:42 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:52:42 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:52:42 ubuntu kernel: [ 2168.954125] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:52:43 ubuntu kernel: [ 2170.012779] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 14:52:44 ubuntu kernel: [ 2170.033271] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:52:44 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:44 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:52:44 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 14:52:44 ubuntu kernel: [ 2170.235766] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 14:52:44 ubuntu kernel: [ 2170.439520] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 14:52:44 ubuntu kernel: [ 2170.643229] wlan0: authentication with 00:0f:8f:23:c7:a1 timed out
Jun  2 14:52:47 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  2 14:52:53 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun  2 14:53:07 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 14:53:20 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jun  2 14:53:39 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 14:53:52 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 14:54:03 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:03 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:03 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:54:03 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:54:16 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:16 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:16 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:54:16 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:54:16 ubuntu kernel: [ 2262.886410] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:54:16 ubuntu kernel: [ 2262.886439] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 14:54:17 ubuntu kernel: [ 2262.905345] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:54:17 ubuntu kernel: [ 2263.107597] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 14:54:17 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:17 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:17 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:54:17 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:54:17 ubuntu kernel: [ 2263.471950] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:54:17 ubuntu kernel: [ 2263.471978] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 14:54:17 ubuntu kernel: [ 2263.487998] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:54:17 ubuntu kernel: [ 2263.690850] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 14:54:17 ubuntu kernel: [ 2263.894588] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 14:54:18 ubuntu kernel: [ 2264.098322] wlan0: authentication with 00:0f:8f:23:c7:a1 timed out
Jun  2 14:54:19 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:19 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:54:19 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 14:54:28 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 14:54:35 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jun  2 14:54:50 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 14:55:01 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:01 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:01 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:55:01 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:55:10 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:10 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:10 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:55:10 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:55:10 ubuntu kernel: [ 2316.408910] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:55:10 ubuntu kernel: [ 2316.408926] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 14:55:10 ubuntu kernel: [ 2316.425369] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:55:10 ubuntu kernel: [ 2316.626352] wlan0: direct probe to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 14:55:10 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:10 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:11 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 14:55:11 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 14:55:11 ubuntu kernel: [ 2316.979786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 14:55:11 ubuntu kernel: [ 2316.979814] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 14:55:11 ubuntu kernel: [ 2316.995890] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:55:11 ubuntu kernel: [ 2317.197614] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 14:55:11 ubuntu kernel: [ 2317.208524] wlan0: authenticated
Jun  2 14:55:11 ubuntu kernel: [ 2317.217585] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 14:55:11 ubuntu kernel: [ 2317.239353] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=58)
Jun  2 14:55:11 ubuntu kernel: [ 2317.239423] wlan0: associated
Jun  2 14:55:11 ubuntu kernel: [ 2317.239653] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 14:55:12 ubuntu avahi-daemon[703]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::76e5:43ff:fec8:4309.
Jun  2 14:55:12 ubuntu avahi-daemon[703]: New relevant interface wlan0.IPv6 for mDNS.
Jun  2 14:55:12 ubuntu avahi-daemon[703]: Registering new address record for fe80::76e5:43ff:fec8:4309 on wlan0.*.
Jun  2 14:55:13 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:13 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 14:55:13 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 14:55:15 ubuntu dhclient: DHCPREQUEST of 10.28.36.244 on wlan0 to 255.255.255.255 port 67
Jun  2 14:55:15 ubuntu avahi-daemon[703]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.28.36.244.
Jun  2 14:55:15 ubuntu avahi-daemon[703]: New relevant interface wlan0.IPv4 for mDNS.
Jun  2 14:55:15 ubuntu avahi-daemon[703]: Registering new address record for 10.28.36.244 on wlan0.IPv4.
Jun  2 15:09:21 ubuntu kernel: [   30.909552] type=1400 audit(1370178560.899:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=506 comm="apparmor_parser"
Jun  2 15:09:21 ubuntu kernel: [   30.968928] ath: EEPROM regdomain: 0x65
Jun  2 15:09:21 ubuntu kernel: [   30.968932] ath: EEPROM indicates we should expect a direct regpair map
Jun  2 15:09:21 ubuntu kernel: [   30.968934] ath: Country alpha2 being used: 00
Jun  2 15:09:21 ubuntu kernel: [   30.968936] ath: Regpair used: 0x65
Jun  2 15:09:21 ubuntu kernel: [   30.987240] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jun  2 15:09:21 ubuntu kernel: [   30.987698] Registered led device: ath9k-phy0
Jun  2 15:09:21 ubuntu kernel: [   30.987706] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050a0000, irq=17
Jun  2 15:09:21 ubuntu avahi-daemon[800]: Network interface enumeration completed.
Jun  2 15:09:21 ubuntu kernel: [   31.204207] type=1400 audit(1370178561.195:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=892 comm="apparmor_parser"
Jun  2 15:09:21 ubuntu kernel: [   31.206449] type=1400 audit(1370178561.195:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=895 comm="apparmor_parser"
Jun  2 15:09:22 ubuntu kernel: [   32.669853] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:09:31 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:31 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:31 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:09:31 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:09:31 ubuntu kernel: [   41.419547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:09:31 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:31 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:31 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:09:31 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:09:31 ubuntu kernel: [   41.877802] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:09:33 ubuntu kernel: [   43.887192] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:09:33 ubuntu kernel: [   43.907422] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:09:33 ubuntu kernel: [   43.909439] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:09:33 ubuntu kernel: [   43.916406] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:09:33 ubuntu kernel: [   43.918083] wlan0: authenticated
Jun  2 15:09:33 ubuntu kernel: [   43.925037] wlan0: deauthenticating from 00:0f:8f:23:c7:a1 by local choice (reason=3)
Jun  2 15:09:33 ubuntu kernel: [   43.926544] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:09:33 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:33 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:09:33 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:09:34 ubuntu kernel: [   44.130248] wlan0: associate with 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 15:09:34 ubuntu kernel: [   44.333984] wlan0: associate with 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 15:09:34 ubuntu kernel: [   44.537744] wlan0: association with 00:0f:8f:23:c7:a1 timed out
Jun  2 15:09:36 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:09:41 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:09:46 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:09:51 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:09:56 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Jun  2 15:10:08 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 15:10:21 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jun  2 15:10:34 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:34 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:34 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:10:34 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:10:54 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:54 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:54 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:10:54 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:10:54 ubuntu kernel: [  124.643973] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:10:54 ubuntu kernel: [  124.644002] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:10:54 ubuntu kernel: [  124.660153] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:10:54 ubuntu kernel: [  124.861796] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 15:10:55 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:55 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:55 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:10:55 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:10:55 ubuntu kernel: [  125.199120] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:10:55 ubuntu kernel: [  125.199134] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:10:55 ubuntu kernel: [  125.215694] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:10:55 ubuntu kernel: [  125.417105] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 15:10:55 ubuntu kernel: [  125.620901] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 15:10:55 ubuntu kernel: [  125.824600] wlan0: authentication with 00:0f:8f:23:c7:a1 timed out
Jun  2 15:10:57 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:57 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:10:57 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:11:00 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Jun  2 15:11:04 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:11:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Jun  2 15:11:17 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jun  2 15:11:32 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jun  2 15:11:42 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:42 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:42 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:11:42 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:11:44 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:44 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:44 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:11:44 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:11:44 ubuntu kernel: [  174.676360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:11:45 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:45 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:45 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:11:45 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:11:45 ubuntu kernel: [  175.241443] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:11:47 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:47 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:11:47 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:11:50 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jun  2 15:11:55 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  2 15:12:04 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  2 15:12:05 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:05 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:05 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:12:05 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:12:22 ubuntu kernel: [  211.908722] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:12:37 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:37 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:37 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:12:37 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:12:37 ubuntu kernel: [  227.057211] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:12:37 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:37 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:37 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:12:37 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:12:37 ubuntu kernel: [  227.657713] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:12:38 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:38 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:12:38 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:12:38 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:12:38 ubuntu kernel: [  228.251288] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:12:46 ubuntu kernel: [  236.065112] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:13:12 ubuntu kernel: [  262.576395] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:14:11 ubuntu kernel: [  321.615549] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:14:21 ubuntu kernel: [  331.405984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:32:24 ubuntu kernel: [   31.304977] type=1400 audit(1370179944.321:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=550 comm="apparmor_parser"
Jun  2 15:32:24 ubuntu kernel: [   31.384421] ath: EEPROM regdomain: 0x65
Jun  2 15:32:24 ubuntu kernel: [   31.384425] ath: EEPROM indicates we should expect a direct regpair map
Jun  2 15:32:24 ubuntu kernel: [   31.384428] ath: Country alpha2 being used: 00
Jun  2 15:32:24 ubuntu kernel: [   31.384429] ath: Regpair used: 0x65
Jun  2 15:32:24 ubuntu kernel: [   31.399613] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Jun  2 15:32:24 ubuntu kernel: [   31.399940] Registered led device: ath9k-phy0
Jun  2 15:32:24 ubuntu kernel: [   31.399951] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc900050c0000, irq=17
Jun  2 15:32:24 ubuntu kernel: [   31.658199] type=1400 audit(1370179944.673:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=907 comm="apparmor_parser"
Jun  2 15:32:25 ubuntu kernel: [   32.943669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:32:34 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:34 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:34 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:32:34 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:32:34 ubuntu kernel: [   41.475751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:32:34 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:34 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:34 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:32:34 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:32:35 ubuntu kernel: [   41.965622] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:32:37 ubuntu kernel: [   43.974843] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:32:37 ubuntu kernel: [   43.995118] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:32:37 ubuntu kernel: [   43.996824] wlan0: authenticated
Jun  2 15:32:37 ubuntu kernel: [   44.003771] wlan0: deauthenticating from 00:0f:8f:23:c7:a1 by local choice (reason=3)
Jun  2 15:32:37 ubuntu kernel: [   44.006295] wlan0: associate with 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:32:37 ubuntu kernel: [   44.012246] wlan0: RX AssocResp from 00:0f:8f:23:c7:a1 (capab=0x421 status=0 aid=78)
Jun  2 15:32:37 ubuntu kernel: [   44.012324] wlan0: associated
Jun  2 15:32:37 ubuntu kernel: [   44.012559] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun  2 15:32:37 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:37 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:32:37 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:32:37 ubuntu dhclient: DHCPREQUEST of 10.28.36.244 on wlan0 to 255.255.255.255 port 67
Jun  2 15:33:14 ubuntu dhclient: receive_packet failed on wlan0: Network is down
Jun  2 15:33:15 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:15 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:15 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:33:15 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:33:18 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:18 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:19 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:33:19 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:33:19 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:19 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:19 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:33:19 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:33:29 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:29 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:33:29 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:33:29 ubuntu dhclient: send_packet: Network is down
Jun  2 15:33:29 ubuntu dhclient: receive_packet failed on wlan0: Network is down
Jun  2 15:33:32 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Jun  2 15:33:32 ubuntu dhclient: send_packet: Network is down
Jun  2 15:33:38 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Jun  2 15:33:38 ubuntu dhclient: send_packet: Network is down
Jun  2 15:33:52 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 15:33:52 ubuntu dhclient: send_packet: Network is down
Jun  2 15:34:03 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 15:34:03 ubuntu dhclient: send_packet: Network is down
Jun  2 15:34:16 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Jun  2 15:34:16 ubuntu dhclient: send_packet: Network is down
Jun  2 15:34:27 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 15:34:27 ubuntu dhclient: send_packet: Network is down
Jun  2 15:34:34 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Jun  2 15:34:34 ubuntu dhclient: send_packet: Network is down
Jun  2 15:34:50 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
Jun  2 15:34:50 ubuntu dhclient: send_packet: Network is down
Jun  2 15:35:09 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Jun  2 15:35:09 ubuntu dhclient: send_packet: Network is down
Jun  2 15:35:24 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Jun  2 15:35:24 ubuntu dhclient: send_packet: Network is down
Jun  2 15:35:42 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
Jun  2 15:35:42 ubuntu dhclient: send_packet: Network is down
Jun  2 15:35:55 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  2 15:35:55 ubuntu dhclient: send_packet: Network is down
Jun  2 15:36:04 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jun  2 15:36:04 ubuntu dhclient: send_packet: Network is down
Jun  2 15:36:06 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:06 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:06 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:36:06 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:36:08 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:08 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:09 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:36:09 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:36:09 ubuntu kernel: [  255.225002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:36:09 ubuntu kernel: [  255.311597] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:36:09 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:09 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:09 ubuntu dhclient: DHCPRELEASE on wlan0 to 10.28.39.254 port 67
Jun  2 15:36:09 ubuntu dhclient: send_packet: Network is unreachable
Jun  2 15:36:09 ubuntu kernel: [  255.920646] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun  2 15:36:10 ubuntu kernel: [  256.051745] wlan0: authenticate with 00:0f:8f:23:c7:a1
Jun  2 15:36:10 ubuntu kernel: [  256.071693] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 1/3)
Jun  2 15:36:10 ubuntu kernel: [  256.275318] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 2/3)
Jun  2 15:36:10 ubuntu kernel: [  256.479051] wlan0: send auth to 00:0f:8f:23:c7:a1 (try 3/3)
Jun  2 15:36:10 ubuntu kernel: [  256.682785] wlan0: authentication with 00:0f:8f:23:c7:a1 timed out
Jun  2 15:36:11 ubuntu dhclient: Listening on LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:11 ubuntu dhclient: Sending on   LPF/wlan0/74:e5:43:c8:43:09
Jun  2 15:36:11 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun  2 15:36:14 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 15:36:21 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Jun  2 15:36:28 ubuntu dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
wafeeq@ubuntu:~$ 



```

---

### Post by wildmanne39 on 2013-06-02
Apparantly there is a bug in network manager that may becausing your browser to start in offline mode you can check that in your browser to see for sure.

Also see if there is an upgrade for networkmanager.
Thanks

---

### Post by varunendra on 2013-06-02
> **ymahmood said:**
> ....Too much pathetic. Do we have any other solution? I can not do this exercise every time when i restart my  pc. or i go from my home to university and then back to room. Please suggest any other solution if possible. Otherwise i have to give up to so called ubuntu..
Agreed. If it is not working for you and you have to do more work than it is doing for you, there is no point in sticking with it.

We may still have suggestions you may 'try', but none are 'guaranteed' to work. So if you have not already run out of patience and are willing to 'try', here's one more :

> **ymahmood said:**
> ```

Jun  2 12:14:48 ubuntu NetworkManager[947]: <info> (wlan0): supplicant interface state: ready -> inactive
Jun  2 12:14:48 ubuntu NetworkManager[947]: <warn> Trying to remove a non-existant call id.
....
....
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> caught signal 15, shutting down normally.
Jun  2 12:16:54 ubuntu NetworkManager[947]: <warn> quit request received, terminating...
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): now unmanaged
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): cleaning up...
Jun  2 12:16:54 ubuntu NetworkManager[947]: <info> (wlan0): taking down device.

```
Given the fact that you are now using wicd, the network manager shouldn't come into scene at all. So, to my inexperienced eyes, it looks like it is interfering with the operation of wicd. Accordingly, I'd suggest to completely remove it now that you have wicd working better than NM. The recommended way (from [https://help.ubuntu.com/community/WICD#For_Gnome_.2BAC8_Unity](https://help.ubuntu.com/community/WICD#For_Gnome_.2BAC8_Unity)) :
Open up a Terminal and execute the following commands:

First, we download the latest NetworkManager, in case we need to reinstall if WICD doesn't works:
```
sudo apt-get install -d --reinstall network-manager network-manager-gnome
```

We already have WICD, so now we uninstall NetworkManager:
```
sudo apt-get remove --purge network-manager-gnome network-manager
```
Let it finish, then do a reboot and see if it helps.

---

### Post by ymahmood on 2013-06-12
Sorry i was a bit busy. Its still not working. I have completely uninstalled network manager but now wicd is not wirking. Today i tried to coonect to internet but it failed. I wait for two hours. But sorry.

---


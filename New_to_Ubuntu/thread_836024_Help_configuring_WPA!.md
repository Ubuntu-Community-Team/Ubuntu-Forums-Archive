---
title: "Help configuring WPA!"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by s1337m on 2008-06-21
I have just installed Ubuntu 8.04, and am working on getting wireless working.  I followed a guide I found on this forum and now my card works with unsecured/wep networks.  But, when I try to connect to a WPA network, I am always denied (I am using network manager).  I have wpa_supplicant installed, and have seen some possible fixes floating around the forum but none really made sense to me... could someone please help me finish configure my wpa?  Help is much appreciated!

```
sean@sean-laptop:~$ uname -a
Linux sean-laptop 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

```

```
sean@sean-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4a:16:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=64 module=ssb multicast=yes
sean@sean-laptop:~$ 
sean@sean-laptop:~$ 


```

```
sean@sean-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by s1337m on 2008-06-21
Whenever I post something about this on any forum, I never get any response -- is this because this question is a bad one?  sigh...

---

### Post by drs305 on 2008-06-21
> **s1337m said:**
> Whenever I post something about this on any forum, I never get any response -- is this because this question is a bad one?  sigh...

Sorry no one has answered your post. It's not a bad question but it probably isn't specific enough. You might have more success if you tell us what exactly happens when you try to log on with WPA. You can also do a search by putting the error message (if there is one) in the search window.

I use nm and WPA but am not the best person to try to troubleshoot it. There are several different flavors of WPA (WPA Personal, WPA2). You might want to open up Network via System, Admin, Network, Unlock and check the wireless settings. Make sure the network name is correct, you may need to enable roaming, and make sure the password is correct (sometimes my password seems to get doubled up).

---

### Post by s1337m on 2008-06-21
> **drs305 said:**
> Sorry no one has answered your post. It's not a bad question but it probably isn't specific enough. You might have more success if you tell us what exactly happens when you try to log on with WPA. You can also do a search by putting the error message (if there is one) in the search window.

I use nm and WPA but am not the best person to try to troubleshoot it. There are several different flavors of WPA (WPA Personal, WPA2). You might want to open up Network via System, Admin, Network, Unlock and check the wireless settings. Make sure the network name is correct, you may need to enable roaming, and make sure the password is correct (sometimes my password seems to get doubled up).

Thanks for responding!  Since I use network manager, I dont get any feedback on what went wrong -- all I get is network manager spinning around and then giving up.  I am using WPA Personal with TKIP and have checked the settings,


```
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:04:E0:A0
                    ESSID:"DESIRED SSID!"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:18:39:76:30:BB
                    ESSID:"Golf Linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:18:39:FD:84:13
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:F8:B5:BF:9D
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:12:88:36:52:E1
                    ESSID:"2WIRE006"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

---

### Post by bred on 2008-06-21
[COLOR="Blue"]well..I configured my WPA in windows...than just switched to ubuntu paste the key end everything went well...

try this thread [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")


and this [http://ubuntuforums.org/showthread.php?t=603154]("http://ubuntuforums.org/showthread.php?t=603154")
[/COLOR]

---

### Post by fontenot_1031 on 2008-06-21
hey man this worked for me [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
give that a try and see if your broadcom card is supported

---


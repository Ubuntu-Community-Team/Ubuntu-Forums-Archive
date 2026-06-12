---
title: "Wireless connection intermittent"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by s1wood on 2012-03-21
I have had wireless working OK on my netbook for a long time but as from yesterday it is failing to connect.
The router is OK - my desktop is using it.
The connection shows up but won't connect.
While I have been experimenting with it it has connected a few time, mainly when the signal is at full strength but then goes off again when I suspend.
When I have it next to the router the signal takes a long time to get to full strength.
Normally I use it in another room on a half-strength signal.

I tried iwconfig and got these results - the second one is while trying to connect.

Susan@susan-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

susan@susan-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:17:3F:26:00:9A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

Any suggestions?

Susan
Ubuntu 11.04 - I was using the Lubuntu desktop when it started but it is the same on either version

---

### Post by wildmanne39 on 2012-03-21
Hi, signal strength is is low, please post the output of:
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

### Post by s1wood on 2012-03-21
#susan@susan-netbook:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux susan-netbook 2.6.38-13-generic-pae #56-Ubuntu SMP Tue Feb 14 14:32:30 UTC 2012 i686 i686 i386 GNU/Linux
susan@susan-netbook:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: AzureWave AR5007EG 802.11bg Wi-Fi mini PCI express card [1a3b:1026]
    Kernel driver in use: ath5k
--
03:00.0 Ethernet controller [0200]: Atheros Communications L2 Fast Ethernet [1969:2048] (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
    Kernel driver in use: atl2
susan@susan-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
susan@susan-netbook:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
susan@susan-netbook:~$ lsmod
#

---

### Post by wildmanne39 on 2012-03-21
Hi, where is ```
lsmod
```? please follow directions in my previous post for posting the information.
thanks

---

### Post by s1wood on 2012-03-21
#susan@susan-netbook:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux susan-netbook 2.6.38-13-generic-pae #56-Ubuntu SMP Tue Feb 14 14:32:30 UTC 2012 i686 i686 i386 GNU/Linux
susan@susan-netbook:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Subsystem: AzureWave AR5007EG 802.11bg Wi-Fi mini PCI express card [1a3b:1026]
    Kernel driver in use: ath5k
--
03:00.0 Ethernet controller [0200]: Atheros Communications L2 Fast Ethernet [1969:2048] (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8233]
    Kernel driver in use: atl2
susan@susan-netbook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
susan@susan-netbook:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
susan@susan-netbook:~$ lsmod

---

### Post by s1wood on 2012-03-23
Well I couldn't use it yesterday because I was running a big backup upload on the desktop. 
Today it is absolutely fine again, connecting normally.
I'll mark it as solved though I don't actually know what was happening - probably just my broadband connection paying up.

Thanks,

Susan

---

### Post by wildmanne39 on 2012-03-23
Hi, that is good news could have been an issue with your isp or the modem and router needed reset something like that.

Glad it is working.

---


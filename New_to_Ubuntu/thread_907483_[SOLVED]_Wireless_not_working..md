---
title: "[SOLVED] Wireless not working."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by WastePotato on 2008-09-01
Hey guys,

I installed aircrack-ng, and as a result, have lost wireless connection in Xubuntu. When I type iwconfig, two wireless connections appear, which is strange seeing as I only have one.

> lol@lol-PC:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath1      IEEE 802.11g  ESSID: ""  Nickname: ""
          Mode:Monitor  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Monitor  Frequency:2.452 GHz  Access Point: 00:1B:9E:9A:D5:43   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

lol@lol-PC:~$ 

Any ideas? :confused:

Thanks.

---

### Post by WastePotato on 2008-09-01
Guys?

---

### Post by Hazer on 2008-09-01
type in ```
sudo gedit /etc/network/interfaces
``` and remove lines reffering to ath0 to remove the second wireless connection (I don't know how aircrack works so it could ceate a second connection) but see if that works (btw is your network unsecured?)

---

### Post by WastePotato on 2008-09-01
MKay, I'm about to Ubuntu, so I'll try it.

Well, my network is secured. It uses WPA2-PSK/CCMP. Why?

---

### Post by Hazer on 2008-09-01
because your network encryption was set to "off" which could indicate configuration problems  and you also have a "wifi0"?

---

### Post by WastePotato on 2008-09-01
OK.. That was the wierdest thing ever. I've now got my connection back after two reboots. I restarted, logged in to Ubuntu. No wireless. Then I realize I've forgotten to copy your instructions to my USB drive. So I log into Vista, put the instuctions on the drive, restart the computer and log into Ubuntu and see that the wireless is working again.

Wierd. :confused:

Anyway, thanks for your support. :popcorn:

---


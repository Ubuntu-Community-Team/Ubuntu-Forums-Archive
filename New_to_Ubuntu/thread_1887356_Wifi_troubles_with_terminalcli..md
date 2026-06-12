---
title: "Wifi troubles with terminal/cli."
date: 2011-11-26
forum: New to Ubuntu
---

### Post by Alexalad on 2011-11-26
So...i have no gui. And i'm trying to connect to my wifi. 

iwconfig output:

lo  no wireless extensions

wlan0 IEEE 802.11bgn ESSID:"Fishtank"
            Mode: Managed Access Point: Not-Associated   Tx-power=20 dBm
            Retry  long limit:7   RTS thr: off   Fragment thr: off
            Power Management: on

vboxnet0 no wireless extension


--I have no idea what any of that means, but I know the essid and the passkey. It's also wpa1, if that means anything. So I used this command to connect, and I know everythings correct:

iwconfig wlan0 essid Fishtank key "PASSWORD"

--This command outputs:

Error for wireless request "Set Encode" (8B2A)  :
     SET failed on device wlan0 ; Invalid argument.

--please...help. Even if its a shot in the dark i'll try it.

---

### Post by PunkLV on 2011-11-26
I've never had dealt with wifi before, however, the output of 
```
cat /etc/network/interfaces
/proc/net/wireless
```
may provide others with some info.

You may find your answer here as well: [http://linuxcommand.org/man_pages/iwconfig8.html](http://linuxcommand.org/man_pages/iwconfig8.html)

---


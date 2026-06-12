---
title: "Network connection -- Internet doesn't work"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by twschmitt2001 on 2008-08-10
I'm sure this is a common problem, this is the second computer I have installed Ubuntu 8.04 on and the only one which has had this error. 

I have installed Ubuntu 8.04, it seems to connect to the network, either LAN or Wireless. but when I go to Firefox is says it cannot connect to the server.

That's really all I know, would anyone that has had this happen please inform me of a step by step way to make internet work; otherwise I will sadly miss downloading important episodes of Lost. 


Since I am not only a beginner at linux but also completely naive at Networking lingo; please try to explain in as simple english as possible. 


PS: I have also added this Smilie to help illustrate my frustration:mad::mad::mad:.

Thanks

---

### Post by Crafty Kisses on 2008-08-10
With the wireless portion you may be interested in this < [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Basically for the wired and wireless portion, try "pinging" a website, so what you want to do is open "Terminal" and type the following:
```
ping www.google.com
```
See what happens, and post the results on the forum.

---

### Post by halitech on 2008-08-10
Hello,

you say it seems to be connecting on the wired and wireless connections, what leads you to believe you are connected?

Do you know your IP address? in a terminal type this then copy and paste the info back here.
```
ifconfig
```
for the wireless, try```
iwconfig
```

---

### Post by twschmitt2001 on 2008-08-10
Responds to "Codename":
 
I just tried and it says: "ping unknown host www.google.com" 


Responds to "halitech"


tim@Traptooly:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:f5:d6:c1:41  
          inet6 addr: fe80::211:f5ff:fed6:c141/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:11:f5:d6:c1:41  
          inet addr:169.254.8.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:da:de:9f  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:feda:de9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2625538 (2.5 MB)  TX bytes:11885 (11.6 KB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77628 (75.8 KB)  TX bytes:77628 (75.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-11-F5-D6-C1-41-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:106
          TX packets:22448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:14612 (14.2 KB)  TX bytes:1032608 (1008.4 KB)
          Interrupt:21 




tim@Traptooly:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:149  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




Thanks For your help. 
TS

---

### Post by tinker312 on 2008-08-10
What type of internet connection to do you have? Are you hooked up through a router or directly to the modem? If your hooked up to a router powercycle it . . . you may need to establish a pppoe connection in Ubuntu if you use DSL.  Also check your network cables and make sure they are snapped in place, I use old ones with the clips broken and sometimes they slip out :) If it is something simple like that then you will get your Lost fix real quick :)

---

### Post by twschmitt2001 on 2008-08-11
Hi have a dsl/cable internet connection. I have a wireless router but I have also tried hooking up to the cable modem directly. 

Can you please tell me what you mean by "powercycle" the router?

Thanks

---

### Post by tinker312 on 2008-08-11
Powercycle just means to disconnect the router from it's power source, wait a few seconds, then plug it back in.  You could try to powercycle your modem also.  You have to be specific whether it is a cable or dsl service because there is difference.

---

### Post by Crafty Kisses on 2008-08-11
Not sure what type of IP address you have, but you may have to manually enter your information when you create your new connection.

---

### Post by halitech on 2008-08-11
> **twschmitt2001 said:**
> 
Responds to "halitech"


tim@Traptooly:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:f5:d6:c1:41  
          inet6 addr: fe80::211:f5ff:fed6:c141/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:11:f5:d6:c1:41  
          inet addr:169.254.8.199  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:da:de:9f  
          [color="red"]inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0[/color]
          inet6 addr: fe80::20f:b0ff:feda:de9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8565 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2625538 (2.5 MB)  TX bytes:11885 (11.6 KB)
          Interrupt:19 Base address:0xa000 

by the looks of this, your wireless is not connecting but you have a wired connection that looks like it is fine. Did you do this on the computer having troubles or the one thats working?
> 
tim@Traptooly:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:149  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


based on this, the wireless is seeing your connection but is not making the connection. Do you have WEP/WPA/WPA2 or any other security on the router running? If you do, try turning it off and see if you can get it to connect.

---


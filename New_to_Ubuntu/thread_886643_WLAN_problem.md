---
title: "WLAN problem"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mormor on 2008-08-11
By using the password suplied to me by my landlord I manage to connect to the network at full signal strenght, but it does not give me a internet connection.

Any hints, tips or pointers will be greatly apriciated.

---

### Post by Betziana on 2008-08-11
It doesn't give you any kind of connection? Did you try it with anything else but browser? 

Do you perhaps run the same connection on different operating system? How does it work then? 

Make sure when connecting that the password type is right. (eg. ASCII or WEP)

---

### Post by mormor on 2008-08-11
> **Betziana said:**
> It doesn't give you any kind of connection? Did you try it with anything else but browser? 

Do you perhaps run the same connection on different operating system? How does it work then? 

Make sure when connecting that the password type is right. (eg. ASCII or WEP)

1: wireless connection to 'mbrandt' (80%)

Neither emesene nor firefox, nor pinging works.

2: I have only ubuntu.

3: well, if I manage to connect to the network, the pass must be right, right?

---

### Post by Betziana on 2008-08-11
Yeah I guess. 

If you can only connect to your wireless router box, I think your network server is down. (if nothing works I wonder how you post stuff here.)

When you enable wireless networking it should show all router boxes it can detect. Are you sure it's the right box? How do you connect to your wireless? Antenna? Stick?

---

### Post by halitech on 2008-08-11
open a terminal and type in ```
ifconfig
``` to see what the connection has for an IP address. Could be you are connected but not authorized properly

---

### Post by Java Geek on 2008-08-11
My router does the same thing from 11 until 3. Its because i have it set to send no signal at certain times. Ask your Administrator if any specific times, sites,... are naturally blocked

---

### Post by mormor on 2008-08-11
> **Betziana said:**
> Yeah I guess. 

If you can only connect to your wireless router box, I think your network server is down. (if nothing works I wonder how you post stuff here.)

When you enable wireless networking it should show all router boxes it can detect. Are you sure it's the right box? How do you connect to your wireless? Antenna? Stick?

I do have a backup solution with hdspa-connection, but its not ment to be my pri connection.
I connect through a wlancard in my laptop. ANd Yes, I see other routers, but I only have the password for one, as the other ones are also paswordprotected. And wouldnt it be a strange coincident if the entire neighbourhood used the same key for theyre wlan? I think I got the rigth box, also considering it carries the name of my landlord.

>  Re: WLAN problem
open a terminal and type in
Code:

ifconfig

to see what the connection has for an IP address. Could be you are connected but not authorized properly

marius@tobor:~$ ifconfig
> eth0      Link encap:Ethernet  HWaddr 00:1b:24:37:af:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:135972 (132.7 KB)  TX bytes:135972 (132.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:28:6c:bc  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe28:6cbc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:624 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:233480 (228.0 KB)  TX bytes:102406 (100.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-28-6C-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I cant work anything out of that. Here is a screen that might tell you smething. : )
[IMG]http://www.b3ta.cr3ation.co.uk/data/png/1230.screenshot1.png[/IMG]

---

### Post by mormor on 2008-08-11
iwconfig gives me:

wlan0     IEEE 802.11g  ESSID:"mbrandt"  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:13:10:1F:41:D7   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=89/100  Signal level=-43 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by halitech on 2008-08-11
you have a valid IP address
```
[color="red"]wlan0 Link encap:Ethernet HWaddr 00:19:d2:28:6c:bc
inet addr:192.168.1.103 Bcast:192.168.1.255 Mask:255.255.255.0[/color]
```

open a terminal and type```
ping 192.168.1.1
``` and ```
ping www.google.ca
```

---


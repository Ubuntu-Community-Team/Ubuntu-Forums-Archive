---
title: "Assistance please"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by Sum on 2008-05-10
Hi, firstly i ha1ve searched the internet and this forum to find solutions to my problem. It seems that i've found simular threads but have not found a cure. The problem is that i can not surf the internet. 

I can ping sites. I'm using wireless connection btw. Also the wireless network connection says that i'm connected. But when i try to surf the internet i get "Connection has timed out" every time.

iwconfig gives me this info:
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEE 802.11g ESSID:"WIRELESS"
      Mode: Managed Frequency 2.437 GHz Access Point ----------
      Retry min limit 7 RTS thr: off fragment thr=2346 B
      Encryption key: -----------------------------------
      link signal level=-40dBm
      Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag: 0
      Tx excessive retries: 0 Invalid misc: 0 Missed beacon:0

by the way i'm using a D-link DWL-G122 H/W Ver C1 F/W Ver 3.00

---

### Post by brettg on 2008-05-10
It appears that you are connected to the AP. If you can ping sites then you must have an ip address and everything else should be OK

Try connecting to a site that is physically closer to you (ie your ISP homepage).

It is possible that they are having upstream issues that have nothing to do with your setup.

Do a 'traceroute some.network.site' and see if one of the hops causes the timeout.

---

### Post by Sum on 2008-05-10
> **brettg said:**
> It appears that you are connected to the AP. If you can ping sites then you must have an ip address and everything else should be OK

Try connecting to a site that is physically closer to you (ie your ISP homepage).

It is possible that they are having upstream issues that have nothing to do with your setup.

Do a 'traceroute some.network.site' and see if one of the hops causes the timeout.

Tried connecting to my isp's site and got the same error. And thanks for your quick reply btw

---

### Post by DBrocks on 2008-05-10
post the result of:
```
ifconfig
```
And contents of:
/etc/network/interfaces

---

### Post by Sum on 2008-05-10
> **DBrocks said:**
> post the result of:
```
ifconfig
```
And contents of:
/etc/network/interfaces

eth0 Link encap:Ethernet HWaddr:00:0D:61:51:5B:92
     UP BROADCAST MULTICAST MTU:1500 Metric: 1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0(0.0 b) TX bytes:0 (0.0 b)
     Interrupt:19 Base address:0xa000

lo   Link encap: Local Loopback
     inet addr:127.0.0.1 Mask 255.0.0.0
     inet6 addr::1/128 Scope: Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:0(0.0 b) TX bytes:0 (0.0 b)

wlan0 Link encap:Ethernet HWaddr 00.17.9A.74.B2.18
      inet addr:192.168.1.2 Bcast:192.168.1.255 Mask 255.255.255.0
      inet6 addr: fe80::217:9aff:fe74:b218/64 Scope:Link
      UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
      RX packets:716 errors:0 dropped:0 overruns:0 frame:0
      TX packets:2833 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:1000
      RX bytes:751785(734.1 kb) TX bytes:317837(310.3 kb)

wmaster0 Link encap:UNSPEC HWaddr:00-17-9A-74-B2--18-00-00-00-00-00-00-00-00-00-00
         UP BROADCAST MULTICAST MTU:1500 Metric: 1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0(0.0 b) TX bytes:0 (0.0 b)

i tried /etc/network/interfaces and was given the message
"Permission denied"
i then sudo su and was given the same message

---

### Post by DBrocks on 2008-05-10
```
sudo nano /etc/network/interfaces
```

---

### Post by natirips on 2008-05-10
Check your proxy settings in the web browser that you're using. If you're using the network at home it is most likely direct connection, but if you're using some shared network (i.e. at job, school,...) you might need to configure to use proxy. If that's the case, you should get the proxy settings details from your network provider/owner/... .

---

### Post by Sum on 2008-05-10
> **DBrocks said:**
> ```
sudo nano /etc/network/interfaces
```

took me to GNU nano 2.0.6 

auto lo
iface lo inet loopback

theres nothing else after that apart from some information like

^G Get help
^O WriteOut
^R Read files^
^Y Prev Page
^K Cut Text
^C Cur Pos
^X Exit
^J Justify
^W Where is
^V Next Page
^U UnCut Text
^T To Spell

And it says [Read 5 Lines]

[QUOTE= natirips] 	
Re: Assistance please
Check your proxy settings in the web browser that you're using. If you're using the network at home it is most likely direct connection, but if you're using some shared network (i.e. at job, school,...) you might need to configure to use proxy. If that's the case, you should get the proxy settings details from your network provider/owner/... .[/QUOTE]

I'm using my home network.

---

### Post by natirips on 2008-05-10
> **Sum said:**
> 
I'm using my home network.
If you're using Firefox, go to Edit -> Preferences -> Advanced -> Network -> Settings, and try No proxy or Auto-detect proxy settings for this network. If that doesn't work, I'm out of ideas.

---

### Post by om1 on 2008-05-10
most routers have a option to test the network connection... you should try that... also are there anymore computers connected to that AP... if so can they access the internet?

---

### Post by Sum on 2008-05-10
> **natirips said:**
> If you're using Firefox, go to Edit -> Preferences -> Advanced -> Network -> Settings, and try No proxy or Auto-detect proxy settings for this network. If that doesn't work, I'm out of ideas.


didn't make a difference thanks for the suggestions tho!

[QUOTE=om1]
Re: Assistance please
most routers have a option to test the network connection... you should try that... also are there anymore computers connected to that AP... if so can they access the internet?[/QUOTE]

Yes i have my laptop connected. Thats how i'm actually able to post on the forum :)

---


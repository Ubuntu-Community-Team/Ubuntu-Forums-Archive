---
title: "Madwifi creating interface problem"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by vonb on 2008-10-03
Hello!

I have installed Ubuntu recently, but i can't connect to wifi.

I have followed the steps on
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

but I get stuck at "Creating interface". When i promt 

wlanconfig ath0 create wlandev wifi0 wlanmode sta

I get
```
wlanconfig: ioctl: No such device

```


Sorry for starting a new topic if one already existed.

---

### Post by phidia on 2008-10-03
From a terminal what does > ifconfig -a output?
Check the link [here]("http://madwifi.org/ticket/257") which I found searching your error output.

---

### Post by vonb on 2008-10-03
ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:cd:ef:e7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fecd:efe7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71769 errors:0 dropped:1958804108 overruns:0 frame:0
          TX packets:51077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93676258 (89.3 MB)  TX bytes:5793547 (5.5 MB)
          Interrupt:218 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113500 (110.8 KB)  TX bytes:113500 (110.8 KB)

```

---


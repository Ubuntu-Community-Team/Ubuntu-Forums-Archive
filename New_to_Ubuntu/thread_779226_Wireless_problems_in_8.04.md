---
title: "Wireless problems in 8.04"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by jimjesus on 2008-05-02
So I just installed ubuntu on my old laptop since windows was just slowing it down. I finished my install but I can't seem to connect to my wireless network. I went to System>Administration>Network and enabled the wireless and put in my ssid and my wep key and firefox still won't connect. How can I remedy this?

---

### Post by ACJarrett on 2008-05-02
what is your terminal response to ifconfig and iwconfig?

---

### Post by jimjesus on 2008-05-02
I'll try and get it as close as I can. I have to look at it on the laptop while posting it on the desktop since apparently plugging in  a network cable won't give me instant access.

iwconfig is as follows

```
lo       no wireless extensions

eth0     no wireless extensions

wmaster0 no wireless extensions

wlan0    IEEE 802.11g  ESSID:"1337"
         Mode:Managed  CHannel:0  Access Point: Not-Associated
         tx-power=0dbm
         retry min limit:7  RTS thr:off  Fragment thr=2346 B
         Link Quality:0  Singnal level:0 noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0  Missed  beacon:0
```

---

### Post by jimjesus on 2008-05-02
and ifconfig outputs:

```
eth0   link encap: Ethernet  HWaddr 00:0d:9d:80:c3:f7
       UP BROADCAST MULTICAST MTU:1500  Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txquenelen:1000
       RX bytes:0  (0.0B)  TX bytes:0  (0.0B)
       Interrupt:11 Base address: 0x4000

lo      Link encap: Local Loopback
        inet addr:127.0.0.1  Mask 255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436  Metric:1
        RX packets:2826 errors:0 dropped:0 overruns:0 frame:0
        TX packets:2826 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:146132 (142.7 KB)  TX bytes:146132 (142.7 KB)
```

---

### Post by ACJarrett on 2008-05-02
Hrm, you seem to be having a similar problem to what I had before the Final Release of Hardy Heron.  When I installed the LTS release the problem went away for me.  Your computer is detecting your wireless card, but for some reason its not listed under your available connections.

Sorry that i can't be more help.

---

### Post by jimjesus on 2008-05-02
Hmm that is strange. Well I have a related question. I used to have the little connection icon on my top bar near the time and the sound icon. Last time I rebooted, it disappeared. How do I get that back so I can click on it to configure settings?

---

### Post by stderr on 2008-05-02
I'm no wireless expert either, and had a lot of trouble getting wireless working... but I've (surprisingly) had success by restarting networking and being patient...

```
 sudo /etc/init.d/networking restart
```

Good luck.

---


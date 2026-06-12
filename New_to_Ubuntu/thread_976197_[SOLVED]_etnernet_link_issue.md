---
title: "[SOLVED] etnernet link issue"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by SwedishWings on 2008-11-09
Hi,

i run a Fedora 9 Server and Ubuntu 8.04 desktop and experience reduced link speed, regardless of protocol. I've tried samba, ftp, sftp, ssh etc, but end up with a rate of about 2.5 Mbyte / Second when copying files in either direction. 

The link speed is 100MB/s, according to 'ethtool eth0' at my Ubuntu desktop:
```
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```However, if i run Fedora 9 at my desktop, i have full speed (~7 Mbyte / Second).

What can possibly cause this problem?

Thanks in advance!

/Mike

---

### Post by Kellemora on 2008-11-09
Hi SW

Are you going through an older HUB that is only 10mb?

If you only have two computers connected together are you using a crossover type of cable and not a regular LAN cable?
(May no longer be applicable these days?)

Do you have a really LONG LAN cable and have it coiled up on itself?

That's all I can think of right now as far as oddities that cause quirks.

TTUL
Gary

---

### Post by SwedishWings on 2008-11-10
Thanks for your reply Kellemora,

I have a 100MBps router and two computers with 100Mbps NIC's, and good cables less than 10 feet, that's all. 

When i run iperf between the machines i get this:

```
mike@ubuntu:~$ iperf -c fedoraserver
------------------------------------------------------------
Client connecting to fedoraserver, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.115 port 35512 connected with 192.168.1.10 port 5001
[  3]  0.0-10.0 sec    113 MBytes  94.8 Mbits/sec
```
and the other way this:
```
[mike@fedoraserver ~]$ iperf -c ubuntu
------------------------------------------------------------
Client connecting to ubuntu, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.10 port 32901 connected with 192.168.1.115 port 5001
[  3]  0.0-10.0 sec    103 MBytes  86.7 Mbits/sec
```

I don't understand way it's not the same speed both ways. 

But never the less, the speed when copying files seems way to slow at my Ubuntu desktop compared to the Fedora 9 Desktop. It's exaclty the same hardware (dual boot on my desktop).

This has got something to do with Ubuntu.

Any more ideas are most welcome!

Regards,
Mike

---

### Post by SwedishWings on 2008-11-13
*bump*

---

### Post by iponeverything on 2008-11-14
It sounds like a driver issue. What is the card? What driver/version is Fedora 9 using and driver/version is 8.04  using?

---

### Post by The Cog on 2008-11-14
Can you check that both Fedora and Ubuntu are using the same Ethernet configuration? - what does ethtool eth0 say on Fedora? I am wondering if you have an issue between full and half duplex. Which is the switch configured for?

---

### Post by SwedishWings on 2008-11-20
Problem solved. After close inspection of the cable between the server and the router, it turned out to be a tiny piece of hair stuck in the cable contact surface on one of the poles. Even closer inspection revealed that it was in fact my girlfriends fault :)

Why this affected Ubuntu and not Fedora is beyond me...

Anyway, thanks for all your help.

---


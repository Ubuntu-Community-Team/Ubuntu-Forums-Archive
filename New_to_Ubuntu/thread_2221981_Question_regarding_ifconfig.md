---
title: "Question regarding ifconfig"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-05-04
I am currently testing for LPIC-1, and ran into this question:
*************************************************
You are troubleshooting a connectivity problem on a Linux server. You are able to connect to another system on the local network, but are not able to connect to a server on a remote network. 
You suspect that the default gateway information for the system (I'm assuming they refer to the local server system upon which you are working) may be configured incorrectly. Which of the following commands would you use to view the default gateway information on the Linux server? 

a) ipconfig
b) ifconfig
c) dig
d) winipcfg
*************************************************

I chose **c) dig** -- which apparently was the wrong answer, as opposed to **b) ifconfig** (which was listed as the correct answer). The explanation was given as such: 

*************************************************
Use the **ifconfig** command on systems running Linux to view information on the TCP/IP configuration of network adapters. Use **ipconfig** and **winipcfg** to view network configuration on Windows systems. Use the **dig** command on Linux and Unix systems to query the Domain Name Service (DNS) servers.
*************************************************

The question seems to be asking for the default gateway information that the Linux server is using. If so, how do you get **ifconfig** to show the default gateway information that the server's network adapter is using?

---

### Post by Iowan on 2014-05-04
Personally, I think **route** when I see "gateway"...

---

### Post by Bashing-om on 2014-05-04
Priest Apostate; Humm, 

In the context of the question and the proposed answers, I can only surmise in the given situation that one would be looking at the "inet adr"; provided by the output of 'ifconfig'.
If there is no connection to the internet there is no "inet adr" info provided by the output. ->  RX packets and/or TX packets would also be 0.

However, yeah;


[INDENT][INDENT]there are other tools
[/INDENT][/INDENT]

---

### Post by Priest Apostate on 2014-05-04
So, just to make sure, ifconfig normally does NOT give out the default gateway information, correct? 

Just wondering if I can regard this as a typo...

---

### Post by Priest Apostate on 2014-05-04
So, just to make sure, ifconfig normally does NOT give out the default gateway information, correct? 

Just wondering if I can regard this as a typo...

---

### Post by Bashing-om on 2014-05-04
Priest Apostate; Hey.

Direct response is no. One can extrapolate .
```

sysop@1310mini:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:10:b5:4e:66:81  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe4e:6681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18043 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6882906 (6.8 MB)  TX bytes:2642063 (2.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

sysop@1310mini:~$ 

```
[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by Priest Apostate on 2014-05-05
Sorry for not being quicker on the uptake on this, but wouldn't extrapolation only point to the internal address for the server being 192.168.0.01, or something in the 192.168.x.x  ballpark (if the gateway were correctly configured)?

---

### Post by The Cog on 2014-05-05
None of those suggested answers will tell you the default gateway configuration. 
ifconfig will tell you which network you are on, and there is an error if the default gateway is not also on that network, but that's it. These will tell you:
```
route
route -n
ip route
```

---

### Post by Bashing-om on 2014-05-05
Priest Apostate; Well.

In my limited experience, the system is going to go looking for a 'gateway'. Now if - for whatever reason - a gateway is not found; then no "inet addr" is returned.

In my case my gateway is to my router having an address of  192.168.0.1 with 'DHCP' routing. My router returns the IP of this box as "192.168.0.101"
Now my router is hardwired to connect to IP 208.180.42.68 as my 'ISP' ( and provides the Domain Name Service for me ).

But if I can not even see my router, and get no 'inet addr' assigned, I can not even see the internet. So for a linux system choice b) is the correct response, - given those choices - for a Windows system choice  a) is the correct command.

The question, I agree, is somewhat misleading "You are troubleshooting a connectivity problem on a Linux server." -> "to view the default gateway information on the Linux server?" For that direct info I must agree with Iowan. If I want to know that "gateway" adress I would indeed do:
```

sysop@1310mini:~$ route -n
Kernel IP routing table
Destination     [color=blue]Gateway[/color]         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         [color=green]192.168.0.1[/color]     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
sysop@1310mini:~$

```

[INDENT][INDENT]how networking works
[INDENT][INDENT][INDENT]is a wonder in and of it's self !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Priest Apostate on 2014-05-05
Gotcha - thanks everyone. I would have chosen **route**, if that choice were given, but as it wasn't, I just wanted to make sure if my interpretation of the question wasn't off somehow...

---


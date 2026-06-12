---
title: "Lost internet connection"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Piamn77 on 2008-10-12
Hello everyone.

I am very new to linux. I installed Kubuntu 8.04.01 on a new computer 5 days ago, and so far it has been running just fine. But today when I started it up suddenly there was no internet connection. In KNetwork manager it says active, but I cant get anything from the internet - no webpages, no chatclient, no nothing... I have an ethernet connection and when I plug it into my old computer, which is running windows XP there is no problem. I tried looking around on the forum but didn´t really find anything I could use. I tried some commands that I found and this is what I got:

> pia@pia-desktop:~$ **sudo dhclient eth0**

[sudo] password for pia:

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


Listening on LPF/eth0/00:1e:8c:6a:ba:27

Sending on LPF/eth0/00:1e:8c:6a:ba:27

Sending on Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPOFFER of 10.83.255.21 from 10.83.0.1

DHCPREQUEST of 10.83.255.21 on eth0 to 255.255.255.255 port 67

DHCPACK of 10.83.255.21 from 10.83.0.1

bound to 10.83.255.21 -- renewal in 48 seconds.

pia@pia-desktop:~$ **sudo lshw -C network**

pia@pia-desktop:~$ **ifconfig**

eth0 Link encap:Ethernet HWaddr 00:1e:8c:6a:ba:27

inet addr:10.83.255.21 Bcast:255.255.255.255 Mask:255.255.255.0

inet6 addr: fe80::21e:8cff:fe6a:ba27/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets:9115 errors:0 dropped:0 overruns:0 frame:0

TX packets:12 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:1000

RX bytes:600044 (585.9 KB) TX bytes:2568 (2.5 KB)

Interrupt:21 Base address:0xc000


lo Link encap:Local Loopback

inet addr:127.0.0.1 Mask:255.0.0.0

inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING MTU:16436 Metric:1

RX packets:20 errors:0 dropped:0 overruns:0 frame:0

TX packets:20 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0

RX bytes:920 (920.0 B) TX bytes:920 (920.0 B)


pia@pia-desktop:~$ 

I put the three commands I used in bold.

Can someone please help me?

Pia

---

### Post by iponeverything on 2008-10-12
> **Piamn77 said:**
> Hello everyone.

I am very new to linux. I installed Kubuntu 8.04.01 on a new computer 5 days ago, and so far it has been running just fine. But today when I started it up suddenly there was no internet connection. In KNetwork manager it says active, but I cant get anything from the internet - no webpages, no chatclient, no nothing... I have an ethernet connection and when I plug it into my old computer, which is running windows XP there is no problem. I tried looking around on the forum but didn´t really find anything I could use. I tried some commands that I found and this is what I got:



I put the three commands I used in bold.

Can someone please help me?

Pia

post the output of:

route -n 
ping -c 5 [www.google.com](www.google.com)
ping -c 5 64.233.189.104

---

### Post by Piamn77 on 2008-10-12
This is what I got:

> pia@pia-desktop:~$ **route -n**

Kernel IP routing table

Destination Gateway Genmask Flags Metric Ref Use Iface

10.83.255.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0

169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0

0.0.0.0 10.83.255.1 0.0.0.0 UG 0 0 0 eth0

pia@pia-desktop:~$ **ping -c 5 [www.google.com](www.google.com)**

ping: unknown host [www.google.com](www.google.com)

pia@pia-desktop:~$ **ping -c 5 64.233.189.104**

PING 64.233.189.104 (64.233.189.104) 56(84) bytes of data.

ping: sendmsg: Operation not permitted

ping: sendmsg: Operation not permitted

ping: sendmsg: Operation not permitted

ping: sendmsg: Operation not permitted

ping: sendmsg: Operation not permitted


--- 64.233.189.104 ping statistics ---

5 packets transmitted, 0 received, 100% packet loss, time 4009ms


pia@pia-desktop:~$ 

Someone else suggested I´d try this also:

> pia@pia-desktop:~$ **sudo ifdown eth0**

ifdown: interface eth0 not configured

pia@pia-desktop:~$ **sudo ifup eth0**

Ignoring unknown interface eth0=eth0.

pia@pia-desktop:~$

Unfortunately I still don´t have internet connection. :(

---

### Post by iponeverything on 2008-10-12
Do you have firestarter or some other firewall installed?

Please post the output of "iptables -L -n"
can you ping your default gw ie. 

ping 10.83.255.1

how about the dhcp server ie.

ping 10.83.0.1

How are you connected to the internet?

what happens if you try this:

sudo route del default
sudo route add default gw 10.83.0.1

Does it fix your connection?

Strange indeed. Turn off ipv6 by changing:

alias net-pf-10 ipv6
to
alias net-pf-10 off ipv6

in /etc/modprobe.d/aliases

and reboot.. odd ---

---

### Post by Piamn77 on 2008-10-12
I´m not sure if I have firewall. I installed Bullguard with Adept, but then I had no internet connection. And I couldn´t see how to fix it in Bullguard, so I just uninstalled it again (with Adept) then I had connection again. Until today that is...

This is what I got from the command line you gave me.

> root@pia-desktop:/home/pia# **iptables -L -n**
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  10.83.255.26         255.255.255.255
logaborted  tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED tcp flags:0x04/0x04
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12
nicfilt    all  --  0.0.0.0/0            0.0.0.0/0
srcfilt    all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12
srcfilt    all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 12
s1         all  --  0.0.0.0/0            0.0.0.0/0

Chain f0to1 (3 references)
target     prot opt source               destination
logdrop    all  --  0.0.0.0/0            0.0.0.0/0

Chain f1to0 (1 references)
target     prot opt source               destination
logdrop    all  --  0.0.0.0/0            0.0.0.0/0

Chain logaborted (1 references)
target     prot opt source               destination
logaborted2  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '

Chain logaborted2 (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `ABORTED '
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED

Chain logdrop (4 references)
target     prot opt source               destination
logdrop2   all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain logdrop2 (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `DROPPED '
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain logreject (0 references)
target     prot opt source               destination
logreject2  all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 2/min burst 1 LOG flags 0 level 4 prefix `LIMITED '
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain logreject2 (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 7 level 4 prefix `REJECTED '
REJECT     tcp  --  0.0.0.0/0            0.0.0.0/0           reject-with tcp-reset
REJECT     udp  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain nicfilt (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0
logdrop    all  --  0.0.0.0/0            0.0.0.0/0

Chain s0 (1 references)
target     prot opt source               destination
f0to1      all  --  0.0.0.0/0            10.83.255.26
f0to1      all  --  0.0.0.0/0            255.255.255.255
f0to1      all  --  0.0.0.0/0            127.0.0.1
logdrop    all  --  0.0.0.0/0            0.0.0.0/0

Chain s1 (1 references)
target     prot opt source               destination
f1to0      all  --  0.0.0.0/0            0.0.0.0/0

Chain srcfilt (2 references)
target     prot opt source               destination
s0         all  --  0.0.0.0/0            0.0.0.0/0
root@pia-desktop:/home/pia#

> what happens if you try this:

sudo route del default
sudo route add default gw 10.83.0.1

Does it fix your connection?

I will try that, but I don´t know how to do the other things you suggest. Maybe you can tell me the exact commands? I am sorry but I am very new to this. I really appreciate your help. Thank You

---

### Post by iponeverything on 2008-10-12
"sudo iptables -F"

will flush those rules for you, do you know how they got added?

---

### Post by iponeverything on 2008-10-12
digging around -- I think that you have guarddog installed..

remove it and you should be good.

sudo dpkg -r guarddog
sudo dpkg -P guarddog

you might need to reboot to completely flush the rules.

also post the output of:

dpkg -l |grep -i fire

Also -- fix the default policy for chains..

sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

---

### Post by Piamn77 on 2008-10-12
> sudo dpkg -r guarddog
sudo dpkg -P guarddog

you might need to reboot to completely flush the rules.

Thank you very much. This worked. :-D I had Guarddog installed with Adept but decided to remove it again with Adept. I guess that was not enough. I did have internet afterwards. It was not until the day after that I lost the connection. 

When put in the commands it said something about getting rid of all the files using purge. What does that mean? Do I still have something left on my system do you think?

> also post the output of:

dpkg -l |grep -i fire

Output:

> pia@pia-desktop:~$ dpkg -l |grep -i fire
ii  firefox-3.0                                3.0.3+build1+nobinonly-0ubuntu0.8.04.1   safe and easy web browser from Mozilla
ii  ufw                                        0.16.2.3                                 program for managing a netfilter firewall

> pia@pia-desktop:~$ sudo iptables -F
[sudo] password for pia:
pia@pia-desktop:~$ sudo iptables -P INPUT ACCEPT
pia@pia-desktop:~$ sudo iptables -P OUTPUT ACCEPT
pia@pia-desktop:~$ sudo iptables -P FORWARD ACCEPT
pia@pia-desktop:~$


I put it in like that. Was that correct or should it have said something more?

Once again thank you so much. I really am very grateful. :-D

---

### Post by iponeverything on 2008-10-12
I think that we are good to go. There might be some remnants of guarddog around, so don't be too surprised if the rules get re-instated.. 

the "dpkg -P guarddog" should have purged them though..

> When put in the commands it said something about getting rid of all the files using purge. What does that mean? Do I still have something left on my system do you think?

yes it could mean that.. try the:

sudo apt-get purge guarddog

---

### Post by Piamn77 on 2008-10-12
Thank you. I tried it again and I got a warning saying that it was ignoring a wish to uninstall a program that was not installed....

---


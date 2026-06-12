---
title: "DHCP assigns IP.. still no network"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-08-20
My network card configured to use automatic DHCP get IP from the internet service provider... still there is no network.. any firewall there which is blocking the network?

---

### Post by pedro_orange on 2008-08-20
You'd need to describe how you're connecting to the network and how the network is setup.

First check that your box knows about your hardware

```
sudo lshw | less
```

Press <Space> until you find eth0/eth1 and make sure it's happy.

You can then check the configuration of the NIC using:

```
ifconfig
```

Another useful command:

```
sudo ethtool eth0
```

Replace eth0 with whatever interface your NIC represents.

If Ubuntu knows you've got an NIC. It may be a problem with the cable or something.

---

### Post by Guruprasad on 2008-08-20
Thanks for the reply...

I tried sudo lshw | less and it showed me eth0 which is my network card for my LAN. eth0 workes fine. It also showed eth1 which is for my internet.

ifconfig returned
eth0      Link encap:Ethernet  HWaddr 00:13:46:8d:cf:95  
          inet addr:192.168.100.101  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe8d:cf95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22981 (22.4 KB)  TX bytes:5491 (5.3 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:80:48:42:d3:ed  
          inet addr:116.68.64.109  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::280:48ff:fe42:d3ed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:882 errors:0 dropped:18454 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54013 (52.7 KB)  TX bytes:4099 (4.0 KB)
          Interrupt:17 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116000 (113.2 KB)  TX bytes:116000 (113.2 KB)

sudo ethtool eth1 showed
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes


I am using dual boot. THe both networks work fine with windows. So I think there is no problem with cable.

I found the Bcast and Mask for eth1 little odd. Can you please check them?

---

### Post by pedro_orange on 2008-09-06
So you have 2 network cards in your machine?

Is this wired (ethernet) and wireless? Or two wired cards?

Yes I would agree your subnet mask on eth1 looks strange. I would have thought it would be 255.255.255.0

Are you using network manager? What does it say when you go into the settings through either the nm-applet or System > Admin > Network?

Does it say you're connected to some sort of network?

---

### Post by Guruprasad on 2008-09-06
Both my cards are wired...

I use the network manager which comes on panel.

---

### Post by lazyart on 2008-09-06
sudo ifdown all

then power cycle your modem.  Give it a moment to get itself ready, then

sudo ifup eth1

See if you can get online.  If so, then bring up your lan with

sudo ifup eth0

---

### Post by The Cog on 2008-09-06
Still need more info. Can you post the output from these commands:

route -n
cat /etc/resolv.conf
ping  91.189.94.186
ping ubuntuforums.com
mtr -r 91.189.94.186

---

### Post by Guruprasad on 2008-09-08
Here is the out put of commands you mentioned.
> route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

internetserver@internetserver:~$ cat /etc/resolv.conf
nameserver 202.88.238.3
nameserver 202.88.238.5
nameserver 165.21.83.88

internetserver@internetserver:~$ ping 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
From 169.254.8.108 icmp_seq=2 Destination Host Unreachable
From 169.254.8.108 icmp_seq=3 Destination Host Unreachable
From 169.254.8.108 icmp_seq=4 Destination Host Unreachable

--- 91.189.94.186 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4999ms
, pipe 3
internetserver@internetserver:~$ ping ubuntuforums.com
ping: unknown host ubuntuforums.com
internetserver@internetserver:~$ mtr -r 91.189.94.186
HOST: internetserver              Loss%   Snt   Last   Avg  Best  Wrst StDev

---

### Post by The Cog on 2008-09-08
Your default route is pointing out through eth0, but the internet is on eth1. That needs fixing for starters.

Try these commands:
> sudo route del default eth0
sudo route add default eth1

I don't know if it will work - I've never worked with an interface configured like that before, but its worth a try.

---

### Post by Guruprasad on 2008-09-10
I tried the route command as you mentioned. Still it is not working.

Here is the output after route command.

> route -n
cat /etc/resolv.conf
ping 91.189.94.186
ping ubuntuforums.com
mtr -r 91.189.94.186


route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 eth1
internetserver@internetserver:~$ 
internetserver@internetserver:~$ cat /etc/resolv.conf
nameserver 202.88.238.3
nameserver 202.88.238.5
nameserver 165.21.83.88
internetserver@internetserver:~$ 
internetserver@internetserver:~$ ping 91.189.94.186
PING 91.189.94.186 (91.189.94.186) 56(84) bytes of data.
From 192.168.100.101 icmp_seq=2 Destination Host Unreachable
From 192.168.100.101 icmp_seq=3 Destination Host Unreachable
From 192.168.100.101 icmp_seq=4 Destination Host Unreachable

--- 91.189.94.186 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4999ms
, pipe 3
internetserver@internetserver:~$ ping ubuntuforums.com
ping: unknown host ubuntuforums.com



---


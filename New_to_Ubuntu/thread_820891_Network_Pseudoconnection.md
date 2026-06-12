---
title: "Network Pseudoconnection"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by matchu on 2008-06-06
Kay, here's the deal. I got my Atheros card working with madwifi.

I should start by saying that this is an Acer Aspire 5610-2762, and I'm not totally sure which card I should be working with since lspci gave both of these:

> 05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


I started with the Broadcom, and when I gave up on that, I moved on to solutions for the Atheros and that seemed to bring me... closer.

What I have now is the attached screenshot:
[ATTACH]73183[/ATTACH]
which shows that I'm now able to recognize the existence of networks and "connect" to them. However, once I "connect," Firefox can't bring up any pages, e-mail won't connect - heck, not even the ping command works! - and I'm stuck using the wired connection.

There's probably a real simple fix for this, but I didn't really know what terms to Google for this situation. Any thoughts?

Much appreciated :)

---

### Post by Monicker on 2008-06-06
The atheros adapter is your wireless.  I have the same version chipset in a recently purchases Toshiba laptop.

Using these instructions worked for me:

[http://ubuntuforums.org/showpost.php?p=4930325&postcount=1]("http://ubuntuforums.org/showpost.php?p=4930325&postcount=1")

---

### Post by matchu on 2008-06-06
Mhm. These are the exact steps I followed (diff source, exact same process), so I'm not sure what's going wrong.

I suspect that perhaps it's leftover garbage from messing around with the Broadcom getting in the way? How would I make sure that things like ndiswrapper and bcm43xx and all that good stuff are fo-sho not confusing my apps?

---

### Post by Monicker on 2008-06-06
If you can connect to the wireless then at least a partial connection is being made.


What are the results of these commands, after connecting to a wireless network:

```
ifconfig
netstat -rn
```

Also, did you try pinging by both name and ip?

```
ping -c 3 4.2.2.2
ping -c 3 www.google.com
```

If you can ping by ip, but not by name, then it could be an issue with DNS resolution.

---

### Post by matchu on 2008-06-06
ifconfig:
> ath0      Link encap:Ethernet  HWaddr 00:19:7e:6a:61:20  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe6a:6120/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27842 (27.1 KB)  TX bytes:13951 (13.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:16:d4:d6:b5:51  
          inet6 addr: fe80::216:d4ff:fed6:b551/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20448088 (19.5 MB)  TX bytes:4273572 (4.0 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:506936 (495.0 KB)  TX bytes:506936 (495.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7E-6A-61-20-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63800 errors:0 dropped:0 overruns:0 frame:10
          TX packets:774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:4751436 (4.5 MB)  TX bytes:49045 (47.8 KB)
          Interrupt:19 
netstat -rn:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 ath0

Ping by IP was unsuccessful on wireless.
> PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.
From 192.168.1.104 icmp_seq=1 Destination Host Unreachable
From 192.168.1.104 icmp_seq=2 Destination Host Unreachable
From 192.168.1.104 icmp_seq=3 Destination Host Unreachable

--- 4.2.2.2 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
, pipe 3

I'm tempted to think that it'd be a problem with my personal network, but this is a dual-boot machine and the network works just fine on Vista...

Even so, I'll try and see if any of the neighbors' networks will let me on and see if I can't figure anything out that way. Thanks for the help! :)

---

### Post by Monicker on 2008-06-06
Hrmm.  The ip and gateway look good.  By any chance have installed Firestart or made any changes to iptables?

What does this show?
```

sudo iptables -L -n
```

---

### Post by matchu on 2008-06-06
Err... neither sounds familiar.

> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination      

Yeah, I'm suspecting that possibly... it *is* connected, but all my apps are trying to reference ndiswrapper or something even though it's not there anymore =/

---

### Post by cariboo on 2008-06-06
Do you have mac address filtering set up on your router? it can see your router but it can't connect. I would check that.

Jim

---

### Post by Monicker on 2008-06-06
> **matchu said:**
> Err... neither sounds familiar.


Yeah, I'm suspecting that possibly... it *is* connected, but all my apps are trying to reference ndiswrapper or something even though it's not there anymore =/

Doesn't seem to be an iptables issue.  I suppose it could be something to do with ndiswrapper; I haven't used it in years, so I don't know myself where to investigate in that regard.

Mac address filtering would not be an issue, since the same machine can communicate with the network under Windows.

---

### Post by matchu on 2008-06-06
It's been weeks since I installed ndiswrapper, but I found the directory with the source in it and did "sudo make uninstall" - now "modprobe ndiswrapper" makes it look like all traces are gone. But I still suspect that maybe it's trying to communicate with a nonexistant module? What would be controlling that?

---

### Post by Tyler H on 2008-06-06
ndiswrapper l

---

### Post by matchu on 2008-06-06
Sorry, could you explain that post? I'm not sure I see what you mean =/

---

### Post by Tyler H on 2008-06-09
in terminal: ndiswrapper l
It will give an output of your driver and if it is working.

---

### Post by matchu on 2008-06-09
Erm... I don't have ndiswrapper. Did I say something unclear?

> 
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


---


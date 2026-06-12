---
title: "want delete Windows network /home"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by Eglefino on 2013-03-21
Hi,

I visited multi fora with this question, but did not find any solution.

I  had for years a Windows computer (31-years), but trying Ubuntu I had a  dual setting with Windows 7 and the live cd and with Lucid the  internet-setting were used for the installation of Lucid. I tell you  short this story backwarts so with the installation of Precise the same  setting were/are in use, together with my own Netgear WNDR3700v2 router.  
Now I got from my provider a new Ubee modem/router and his settings  are 192.168.178.xx and the home-network which I have in use (a  Windows-network) have 10.0.0.2.
I have also tried before when I used  Lucid (with my Windows experience) to delete that Windows-network and  install a home-network p.e. from the live-cd or as package, p.e. gnome  networks-manager. 
Now I have problems with the transparant firewall  ufw because of the new and the old settings (ports) and problems with  the automatic update-manager (not Synaptic) because it crash half way, I  have post my message even in Launchpad (~ruudino-k) because I have more  problems with Precice (maybe all together is a chain-reaction) Lucid  was better, but we going in the future....:smile:.

In  theorie it's possible to install two home-networks in one platform as  Ubuntu even in Windows, but I don't want to go backkkkkk:grin:.
The  profider-guy who installed my modem/router had even problems with my  computer to install the new settings under DHCP, because the old  settings did not disepear! So I said I try it myself as newbie but  nothing is going...., I bought a Synology NAS and all install settings  which I had to follow with the manual (because it was not in the list)  but I got a direct connection, no problems with that modem/router. Not  all that settings are ready, so I delete there all. I'm bedridden so my  PC-work out of my bed I will it do it all together when my body have energy enough;  I have a disabled friend who helped me with all installations, he is a specialist with Ubuntu, but asking him this isn't his routine. Even I'm new I want to learn it from the terminal.

Extra info below
```

toscana-amante@Ruudino-Eglefin:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:83:8f:31  
          inet addr:192.168.178.13  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::e2cb:4eff:fe83:8f31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113563548 (113.5 MB)  TX bytes:5613917 (5.6 MB)
          Interrupt:76 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2176 (2.1 KB)  TX bytes:2176 (2.1 KB)

lxcbr0    Link encap:Ethernet  HWaddr 9a:46:68:35:26:31  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::9846:68ff:fe35:2631/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:46095 (46.0 KB)

```

```
toscana-amante@Ruudino-Eglefin:~$ sudo iptables -L
[sudo] password for toscana-amante: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             state INVALID
DROP       all  --  anywhere             anywhere             state INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             state INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             state NEW
ACCEPT     udp  --  anywhere             anywhere             state NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
toscana-amante@Ruudino-Eglefin:~$ 

```
I can't image that the above code is such a mesh, there a lot of errors and less protocols... I see nothing.... I think it's not possible to write a ufw log myself, this is terrible.... Oh by the way, iI'm Dutch and English isn't my language there could be some faults :o. I even can to delete all and install Ubuntu a new time (there are now 4x 12.04 on my PC, in all are documents)

Hope someone can help me, or give me a (?step-by-step) way to a solution in the terminal

With thanks,
Ruudino Amsterdam, Netherlands

---

### Post by squakie on 2013-03-22
What I'm guessing is actually fairly simple, but first an quick overview of what I think happened:  your original access was via an access point like a cable modem connected to your router.  The original access point (the cable modem) was also a router.  This results in the 192.xxx.xxx.xxx addresses being assigned to the cable modem's router, and since your router was plugged into that, your router now assumed the addresses of 10.xxx.xxx.xxx.  I would also suspect that your new configuration as the cable modem and wireless router all in one, with no need for your original router.  That means your network access is now via the 192.168.xxx.xxx range.  If you already have a connection "defined" for your old network configuration you need to delete it.  Click on the network manager icon on the top bar and edit connections.  If your old network is listed just delete it.  Now hopefully network manager will find the your "new" network and it will prompt you for the security key.  I hope that's what it was, and I hope it's as simple as deleting the old network saved definition in network manager, then just connecting to the new net.  If I'm way off or that doesn't work, just post back and I'm sure someone with much more knowledge than me will help you.

---


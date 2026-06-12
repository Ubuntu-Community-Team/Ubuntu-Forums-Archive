---
title: "Setting up OpenVPN (client only)"
date: 2016-03-07
forum: New to Ubuntu
---

### Post by zephyr2 on 2016-03-07
Noob here, and I want to set up an OpenVPN client to connect to a subscription VPN service that requires connecting over port 1197. 

I am running Ubuntu 15.10 on a System76 laptop and have some basic UFW rules opening only a few ports in order to limit the services I run. Above all, I want to ensure these pre-existing firewall settings are  respected (so, only services listening on ports x, y, z are allowed  out, etc.). I assume, then, this means I will have to somehow route all my traffic over port 1197, while adjusting my UFW rules or some other settings carefully to allow that behavior?

Could someone please help me understand what setup of OpenVPN client and UFW in combination ensures that any prior UFW rules are being respected? (FWIW, I did successfully connect with OpenVPN via terminal a few  times--I just wasn't sure my UFW rules were ordered correctly to achieve  the goals stated above.) Alternatively, pointing me to a good VPN for dummies guide with lots of handholding would be very much appreciated. :)

---

### Post by sandyd on 2016-03-07
> **zephyr2 said:**
> Noob here, and I want to set up an OpenVPN client to connect to a subscription VPN service that requires connecting over port 1197. 

I am running Ubuntu 15.10 on a System76 laptop and have some basic UFW rules opening only a few ports in order to limit the services I run. Above all, I want to ensure these pre-existing firewall settings are  respected (so, only services listening on ports x, y, z are allowed  out, etc.). I assume, then, this means I will have to somehow route all my traffic over port 1197, while adjusting my UFW rules or some other settings carefully to allow that behavior?

Could someone please help me understand what setup of OpenVPN client and UFW in combination ensures that any prior UFW rules are being respected? (FWIW, I did successfully connect with OpenVPN via terminal a few  times--I just wasn't sure my UFW rules were ordered correctly to achieve  the goals stated above.) Alternatively, pointing me to a good VPN for dummies guide with lots of handholding would be very much appreciated. :)

Depending on your VPN service, OpenVPN should automatically change the default route of your computer so that traffic goes over the VPN, not your own network.

That being said, post the output of
```

sudo iptables -L -v
sudo ufw status verbose
``` so that we can check your firewall rules. I tend to find the principle/rule of least privilege works here too - start from denying all in GUFW and move up to enabling only the things you need.

To check if the VPN is working properly check your IP Address before and after connecting to the VPN. You can also check the default route before and after by running
```

ip route | grep default

```

Sample Output:
```

default via 192.168.2.1 dev wlp6s0  proto static  metric 600
```

After starting the VPN, the gateway (in red) should change to the VPN's gateway.

---

### Post by zephyr2 on 2016-03-09
Hmm... now I'm a little paranoid. When I went to retrieve the output of the commands suggested, I noticed something very strange--my ip address is not from a range provided by my ISP, but from a range provided by one of the VPN gateways. And I noticed this *before* I tried connecting to the VPN with

```
sudo openvpn nameofgateway.conf
```

So I disconnected my wifi and ran 

```
tail -f /var/log/syslog
``` 

and saw the following error repeated:

```
ovpn-Netherlands[1039]: RESOLVE: Cannot resolve host address: nl.privateinternetaccess.com: Temporary failure in name resolution
```

I did previously try to configure a VPN connection to that gateway using Network Manager, but ran into problems (due to a bug, NM doesn't handle OpenVPN well). So I deleted the VPN connection profiles in NM and instead began using OpenVPN via the terminal. But the error above, appearing in my log before I've gone into a terminal to start OpenVPN manually, would seem to suggest my system is trying to reach the VPN gateway on startup.

How to correct this? In the GUI for NM, there are no apparent VPN profiles to edit/delete, since I already removed them...

---

### Post by pauljw on 2016-03-09
I used PIA's scripts from the info on this page.  I'm running 14.04LTS but I think there is a good chance that it will work for you just fine.  Also, PIA has excellent support and are more than willing to assist you with setup and configuration issues.

[https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn](https://www.privateinternetaccess.com/pages/client-support/ubuntu-openvpn)

---

### Post by sandyd on 2016-03-09
Please post the output of
```

ps aux | grep openvpn
```

---

### Post by zephyr2 on 2016-03-16
Thanks, sandyd, for the helpful command requests. I decided to uninstall / reinstall OpenVPN & start fresh, then realized I was getting a DNS leak until I added

```
[SIZE=2]script-security 2
up[/SIZE] /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
```

to my conf file. I hope this resolves that problem, but I guess we'll see. I also switched to another gateway with the same VPN provider.
 
So with those changes and freshly connnected with OpenVPN via the terminal, here is the output requested above:

```
$ sudo iptables -L -v

Chain INPUT (policy DROP 4 packets, 224 bytes)
 pkts bytes target     prot opt in     out     source               destination         
12121   10M ufw-before-logging-input  all  --  any    any     anywhere             anywhere            
12121   10M ufw-before-input  all  --  any    any     anywhere             anywhere            
    4   224 ufw-after-input  all  --  any    any     anywhere             anywhere            
    4   224 ufw-after-logging-input  all  --  any    any     anywhere             anywhere            
    4   224 ufw-reject-input  all  --  any    any     anywhere             anywhere            
    4   224 ufw-track-input  all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-before-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-after-logging-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-reject-forward  all  --  any    any     anywhere             anywhere            
    0     0 ufw-track-forward  all  --  any    any     anywhere             anywhere            

Chain OUTPUT (policy DROP 199 packets, 18499 bytes)
 pkts bytes target     prot opt in     out     source               destination         
1268K 1847M ufw-before-logging-output  all  --  any    any     anywhere             anywhere            
1268K 1847M ufw-before-output  all  --  any    any     anywhere             anywhere            
  199 18499 ufw-after-output  all  --  any    any     anywhere             anywhere            
  199 18499 ufw-after-logging-output  all  --  any    any     anywhere             anywhere            
  199 18499 ufw-reject-output  all  --  any    any     anywhere             anywhere            
  199 18499 ufw-track-output  all  --  any    any     anywhere             anywhere            

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:netbios-ns
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:netbios-dgm
    0     0 ufw-skip-to-policy-input  tcp  --  any    any     anywhere             anywhere             tcp dpt:netbios-ssn
    0     0 ufw-skip-to-policy-input  tcp  --  any    any     anywhere             anywhere             tcp dpt:microsoft-ds
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:bootps
    0     0 ufw-skip-to-policy-input  udp  --  any    any     anywhere             anywhere             udp dpt:bootpc
    0     0 ufw-skip-to-policy-input  all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   224 LOG        all  --  any    any     anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  199 18499 LOG        all  --  any    any     anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp destination-unreachable
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp source-quench
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp time-exceeded
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp parameter-problem
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-request
    0     0 ufw-user-forward  all  --  any    any     anywhere             anywhere            

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1353  114K ACCEPT     all  --  lo     any     anywhere             anywhere            
10763   10M ACCEPT     all  --  any    any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
    0     0 ufw-logging-deny  all  --  any    any     anywhere             anywhere             ctstate INVALID
    0     0 DROP       all  --  any    any     anywhere             anywhere             ctstate INVALID
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp destination-unreachable
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp source-quench
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp time-exceeded
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp parameter-problem
    1    48 ACCEPT     icmp --  any    any     anywhere             anywhere             icmp echo-request
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:bootps dpt:bootpc
    4   224 ufw-not-local  all  --  any    any     anywhere             anywhere            
    0     0 ACCEPT     udp  --  any    any     anywhere             224.0.0.251          udp dpt:mdns
    0     0 ACCEPT     udp  --  any    any     anywhere             239.255.255.250      udp dpt:1900
    4   224 ufw-user-input  all  --  any    any     anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  131 17007 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  131 12576 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW AUDIT] "

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1353  114K ACCEPT     all  --  any    lo      anywhere             anywhere            
 7897 1349K ACCEPT     all  --  any    any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
1259K 1846M ufw-user-output  all  --  any    any     anywhere             anywhere            

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             LOG level warning prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             ctstate INVALID LOG level warning prefix "[UFW AUDIT INVALID] "
    0     0 LOG        all  --  any    any     anywhere             anywhere             LOG level warning prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   224 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type LOCAL
    0     0 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
    0     0 RETURN     all  --  any    any     anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 10
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  any    any     anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  any    any     anywhere             anywhere             reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  146  8760 ACCEPT     tcp  --  any    any     anywhere             anywhere             multiport dports domain,http,https
  569 42307 ACCEPT     udp  --  any    any     anywhere             anywhere             multiport dports domain,bootps,bootpc
1258K 1846M ACCEPT     udp  --  any    any     anywhere             anywhere             udp dpt:1197
```


```
$ sudo ufw status verbose

Status: active
Logging: on (high)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
53,80,443/tcp              ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
1197/udp                   ALLOW OUT   Anywhere
53,80,443/tcp (v6)         ALLOW OUT   Anywhere (v6)
53,67,68/udp (v6)          ALLOW OUT   Anywhere (v6)
1197/udp (v6)              ALLOW OUT   Anywhere (v6)
```

```
$ ip route | grep default

default via 10.0.1.1 dev wlan0  proto static  metric 600
```

```
$ ps aux | grep openvpn

root      5584  0.0  0.0  78668  4452 pts/0    S+   21:55   0:00 sudo openvpn US Seattle.conf
root      5585  0.0  0.0  39256  6004 pts/0    S+   21:55   0:00 openvpn US Seattle.conf
username    5935  0.0  0.0  15192  2280 pts/1    S+   21:59   0:00 grep --color=auto openvpn


```

Please let me know if the above looks correct. Thanks!

---

### Post by zephyr2 on 2016-03-19
bump?

---

### Post by sandyd on 2016-03-19
The firewall rules look fine to me :)

---


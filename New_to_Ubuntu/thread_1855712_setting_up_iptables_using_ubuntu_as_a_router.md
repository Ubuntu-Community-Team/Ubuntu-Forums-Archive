---
title: "setting up iptables using ubuntu as a router"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by discosadness on 2011-10-06
Hi all,

I've followed the setup here: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) to use my Ubuntu box as a router. Basically, I have two devices eth0 (which handles the WAN connection) and eth1 (which handles the LAN side). It's working beautifully, but I'd like to restrict things a little more to prevent intruders from accessing my network.

I've been using this basic script: [https://help.ubuntu.com/community/Router/Firewall](https://help.ubuntu.com/community/Router/Firewall) to setup some IPtables to restrict traffic. I'm looking to basically block all external traffic from accessing the network except on ports 22 and 80, which it seems like this script should do.

However, after running the script (and inputting the correct variables in it), it seems that other ports on the Ubuntu box are open. Using nmap I can see that other external services (for example, port 21) are open to the outside world.

Can anyone tell me what I need to change in the above script to block outside access on other ports? My current iptables are listed below (I replaced my actual IP with OUTSIDEIP for security).

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/24          anywhere            
REJECT     all  --  10.0.0.0/24          anywhere            reject-with icmp-port-unreachable 
ACCEPT     icmp --  anywhere             OUTSIDEIP 
ACCEPT     all  --  anywhere             OUTSIDEIP ctstate RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:bootpc dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     tcp  --  anywhere             OUTSIDEIP ctstate NEW,RELATED,ESTABLISHED tcp dpt:www 
ACCEPT     tcp  --  anywhere             OUTSIDEIP ctstate NEW,RELATED,ESTABLISHED tcp dpt:https 
ACCEPT     tcp  --  anywhere             OUTSIDEIP ctstate NEW,RELATED,ESTABLISHED tcp dpt:ssh 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
DROP       icmp --  anywhere             anywhere            ctstate INVALID 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  OUTSIDEIP  10.0.0.0/24         
ACCEPT     all  --  10.0.0.1             10.0.0.0/24         
REJECT     all  --  anywhere             10.0.0.0/24         reject-with icmp-port-unreachable 
ACCEPT     all  --  OUTSIDEIP  anywhere            
ACCEPT     tcp  --  10.0.0.1             255.255.255.255     tcp spt:bootps dpt:bootpc 
ACCEPT     udp  --  10.0.0.1             255.255.255.255     udp spt:bootps dpt:bootpc 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
```

---

### Post by discosadness on 2011-10-06
By the way, the internal ip is 10.0.0.1 on the box and DHCP is setup to assign LAN users with a 10.0.0.x IP address.

---

### Post by Dangertux on 2011-10-06
Are you scanning the machine from inside your network? If you are with those firewall rules it's going to show the port open.

---


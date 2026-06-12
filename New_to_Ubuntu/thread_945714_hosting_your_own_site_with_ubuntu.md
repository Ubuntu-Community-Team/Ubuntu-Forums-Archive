---
title: "hosting your own site with ubuntu"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by 007casper on 2008-10-12
After I have installed ubuntu, apache and all the necessary bells and whistles, I have created a dummy site... the computer is hooked up to a cable modem with static ip... everything works fine locally.  

When I go to friends house couple blocks down from me, it works like a charm even though it is tiny bit slow since my cable connection download is 5016 kb/s and upload 475 kb/s...

however, when I start firestarter firewall, I can see the site locally but not in my friends house...

under firestarter I have edited the Policy... 

I have set the IP number in order to allow connection from host and I did set http, https port 80 and 443 respectively to the designated IP 

If I disable the firewall the dummy site works in my friends house, but not when firestarter(firewall) is active... 

how I can solve this problem?

thank you so much

---

### Post by cariboo on 2008-10-12
Run in a terminal:

```
sudo iptables -L
```

and post thre results here, so that we can see what your firewall rules looks like.

Jim

---

### Post by 007casper on 2008-10-12
here we go... 

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  rdns-lb-01.orange.rr.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  rdns-lb-01.orange.rr.com  anywhere            
ACCEPT     tcp  --  rdns-lb-02.orange.rr.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  rdns-lb-02.orange.rr.com  anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.1.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.107        rdns-lb-01.orange.rr.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.107        rdns-lb-01.orange.rr.com udp dpt:domain 
ACCEPT     tcp  --  192.168.1.107        rdns-lb-02.orange.rr.com tcp dpt:domain 
ACCEPT     udp  --  192.168.1.107        rdns-lb-02.orange.rr.com udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  cpe-7*-**-**-***.socal.res.rr.com  anywhere            
ACCEPT     tcp  --  cpe-7*-**-**-***.socal.res.rr.com  anywhere            tcp dpt:www 
ACCEPT     udp  --  cpe-7*-**-**-***.socal.res.rr.com  anywhere            udp dpt:www 
ACCEPT     tcp  --  cpe-7*-**-**-***.socal.res.rr.com  anywhere            tcp dpt:https 
ACCEPT     udp  --  cpe-7*-**-**-***.socal.res.rr.com  anywhere            udp dpt:https 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere
```

---

### Post by 007casper on 2008-10-12
any help will be appreciated it :-)

---

### Post by 007casper on 2008-10-13
bump

---

### Post by 007casper on 2008-10-14
no luck... can anybody help in regards to firewall issues

---


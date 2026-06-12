---
title: "open port, firewall, networking issues?"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by JBudOne on 2013-01-06
Hey guys,

   This is an extended post from another forum board [for VLC]("http://forum.videolan.org/viewtopic.php?f=4&t=107392"). In a nutshell, I'm trying to stream a video by RTP ( 224.1.1.1:5004 ), and connect to that stream from another computer/network. The problem is that nothing is coming through, and the guys on VLC are suggesting it may be a network/firewall issue.

  When the stream is running, if I call `netstat -nu` I see the following,
```

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
udp        0      0 <my IP>:42455    224.1.1.1:5004          ESTABLISHED
udp        0      0 <my IP>:42456    224.1.1.1:5005          ESTABLISHED
udp6       0      0 ::1:59525        ::1:59525               ESTABLISHED

```


To me it looks like port 5004 is open just fine, I have no idea what 5005 is for but its clearly related to VLC's stream. I'm not entirely sure why the state is ESTABLISHED rather than LISTENING. But more importantly, I can't understand why the VLC client on another computer/network is unable to connect to this. Any ideas? Tips? Suggestions? Advice? All of which are very appreciated :) Thanks

---

### Post by mastablasta on 2013-01-07
did you open the port? i think by default ports are closed and are not listening to anyhting. you can use iptables or a graphical interface such as gufw for firewall.

---

### Post by JBudOne on 2013-01-08
I've played around with iptables, and tried opening the ports before streaming the service:

```

jbud@jb:~$ sudo iptables -A INPUT -p tcp --dport 5004 -j ACCEPT
jbud@jb:~$ sudo iptables -A INPUT -p udp --dport 5004 -j ACCEPT
jbud@jb:~$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5004
ACCEPT     udp  --  anywhere             anywhere             udp dpt:5004

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
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:5004
ACCEPT     udp  --  anywhere             anywhere             udp dpt:5004
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8554
ACCEPT     udp  --  anywhere             anywhere             udp dpt:8554
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1234
ACCEPT     udp  --  anywhere             anywhere             udp dpt:1234

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


```


I'm not sure what a lot of that means, but it looks to me like port 5004 is open on udp (udp is the protocol used for rtp I think?), which means I shouldn't have any issues with accepting incoming connections. But as a final try, I ran gufw and double checked that port 5004 was (Action==ALLOW IN) and (From==ANYWHERE); and then finally I simply turned off the firewall altogether, with still no luck. I must be missing something? Could there be any other issues than the firewall? I also have a local webserver running (apache) on port 80, and am able to see that from my other computer/network just fine. I can't understand what the issue could possibly be? Is there something I'm missing? Or is there perhaps some way that I can view a log of incoming and blocked connections? Thanks

---


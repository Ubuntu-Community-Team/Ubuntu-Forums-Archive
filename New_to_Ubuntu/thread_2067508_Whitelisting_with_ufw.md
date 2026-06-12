---
title: "Whitelisting with ufw"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by heebiejeebies on 2012-10-07
Hi all,

I have a script set to run at startup that flushes all iptables.  The flush works fine, and if I were to stop the script at that point I would get unrestricted internet access.  However I added a few lines to it to try to get it to whitelist some websites by IP.  After the flush commands I put:

ufw default deny
ufw enable
ufw allow from 74.52.238.59
ufw allow from 74.52.238.56

....and so on to list all the websites I want whitelisted.  However this results in everything being blocked, whether I access them by domain or by navigating straight to the IP.  What am I doing wrong???

Thanks! :)

---

### Post by cipherboy_loc on 2012-10-07
Two thoughts: DNS server and router IPs must be listed, and secondly, what does iptables -L show after the whitelist rules have supposedly been applied?


Thanks,
Cipherboy

---

### Post by heebiejeebies on 2012-10-09
Thanks for your reply!  So I went to Connection Information from the network menu and added in the DNS addresses listed there.  It still doesn't work.  This is the result of Iptables -L :

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

Chain OUTPUT (policy DROP)
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
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "

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
DROP       all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  74.52.238.50         anywhere            
ACCEPT     all  --  142.245.1.15         anywhere            
ACCEPT     all  --  142.245.1.203        anywhere            
ACCEPT     all  --  74.201.154.248       anywhere            
ACCEPT     all  --  74.201.113.175       anywhere

---

### Post by cipherboy_loc on 2012-10-09
UFW seems to have made this more complicated than it should be, but how do you want to whitelist? Specifically, do you want to reject all traffic going from your computer to non-whitelisted computers, or do you want to reject all traffic from other computers that are not whitelisted from reaching your computer? 

Often times it is easier to blacklist than it is to whitelist, due to complex dependencies (external JavaScript for analytic engines, CDN hosted libraries) and rotating IPs (google for instance). That being said, personally I would suggest dropping ufw and doing it all in iptables. Decide where you want to block the external websites (input and output), allow access to your local network (typically 192.168.1.0-255 or 192.168.0.0-255) and DNS servers, and then make a list of what you want to whitelist, make sure of IPs, then implement the block (**man iptables** for more information). Also, decide what you want to do with external requests (say a ping request from another host on your local network, etc) and implement that.

Thanks,
Cipherboy

---

### Post by heebiejeebies on 2012-10-17
Hi all,

I really have no idea what I'm doing with iptables. I've tried various things I've found online and nothing has worked.  I either get complete blocking of all connections or no blocking at all. 

I would really appreciate it if someone could please either:

Paste whatever lines I need that will allow me to first block all traffic, then whitelist http and https so the user can only visit certain websites, by IP or domain; or

Tell me how to completely remove and reinstall ufw, or at least completely reset it.  I can't see any reason at all why it shouldn't just work - it did when I first used it with Firestarter, but somewhere along the line something must have broken.

Thank you!

---

### Post by heebiejeebies on 2012-10-18
Guys, this is really frustrating.

Should I just reinstall Ubuntu?

---

### Post by heebiejeebies on 2012-10-21
Thanks for nothing, you useless bunch of pricks.

---

### Post by steeldriver on 2012-10-21
I think you need to change the rule order to put the whitelisted IPs ahead of the default deny (specific before general)

iirc UFW descends the rules list in order and applies the first matching rule - so as soon as it finds 'default deny' it will ignore your subsequent whitelist lines

---


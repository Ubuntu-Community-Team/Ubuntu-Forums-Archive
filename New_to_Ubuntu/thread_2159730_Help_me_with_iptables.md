---
title: "Help me with iptables"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by deri on 2013-07-04
Sudo iptables -L shows

> Chain INPUT (policy DROP)
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

I have iptables and Guwf installed. I have "deny" on incoming on Guwf. 

I don't know why I have so many lines on the iptables config. Could someone explain what these rules do? I am trying to add some ips to iptables that I want to block. I have seen scripts that do it automatically but I have been too scared to try. Where can I find the iptables config file?

---

### Post by dino99 on 2013-07-04
Dont worry about the rules: its very easy/understandable to "allow" or "deny" for each rule you need to create/maintain
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by JKyleOKC on 2013-07-04
> **deri said:**
> I don't know why I have so many lines on the iptables config. Could someone explain what these rules do? I am trying to add some ips to iptables that I want to block. I have seen scripts that do it automatically but I have been too scared to try. Where can I find the iptables config file?The reason for so many lines is that UFW (the backend program that GUFW calls to do its work) creates them. Attempting to mix manual control of iptables, and UFW or GUFW, is a quick way to become hopelessly confused! I once tried to create a flow-chart of what these rules do, and quickly got lost...

You can add specific IPs to be blocked, using UFW at the command line; I suspect that GUFW also has such a capability (if it doesn't, it's not a complete front end for its purpose) but since I've never used it I cannot be much help with the actual way to get there. You can find examples for UFW by opening a terminal window and issuing the command "man ufw" (without the quotes). The first several screens will look like gibberish if you're not familiar with the command line, but keep paging down (by hitting the space bar) until you come to a section headed "EXAMPLES" and those will make a bit more sense. You can replace the word "accept" with "deny" to change a rule from accepting to blocking things.

However, don't try to mix manual control of iptables with the use of UFW/GUFW (or any other firewall program); it will probably make the firewall program fail to work, and may even make it difficult to boot the system!

As for the iptables config file, there really isn't a single such file. The UFW package maintains its own rules files and uses them to create the iptables rule set at boot time. The scripts you've found simply create the rule set themselves (probably wiping out the effects of UFW, if they're well written, but not all of them are). I maintain my rule set manually and have a file that handles it rather than a script, but this isn't standard.

Since you are using GUFW, your best bet would be to search its help files (or in the forums) for its equivalent of the UFW examples, and use that to do what you want. Hope this helps!

---

### Post by BBQdave on 2013-07-04
> **JKyleOKC said:**
> Since you are using GUFW, your best bet would be to search its help files...

+1

[**Gufw Firewall**]("http://gufw.org/") Check out their documentation :)

---


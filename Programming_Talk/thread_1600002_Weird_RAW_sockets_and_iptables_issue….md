---
title: "Weird RAW sockets and iptables issue…"
date: 2010-10-18
forum: Programming Talk
---

### Post by skypemesm on 2010-10-18
Not sure if this is the right place to ask, but here is my question:
I am trying to redirect all incoming traffic on UDP port 5060 to port 56790, and all outgoing traffic from 5060 to the port 56789. I used these iptables rules:

iptables -t nat -I PREROUTING -p udp ! -s localhost --dport 5060 -j REDIRECT --to-port 56790
iptables -t nat -I OUTPUT -p udp ! -s localhost --sport 5060 -j REDIRECT --to-port 56789

I listen on both ports using RAW SOCKETS after setting the interface to PROMISCUOUS mode using ioctl.

I see packets ONLY on 56789 i.e.SENDING side, and I do not see any packets on 56790, while wireshark shows that many packets are delivered to port 5060.

Why would this happen? Any ideas? Do you think it's a problem with iptables rules or something to do with raw sockets?

---

### Post by dwhitney67 on 2010-10-18
I've never played with iptables until today; thanks for the crash course.  :-)

As for the issue you are experiencing, I could not duplicate it.  I substituted the port numbers you were using for the PREROUTING with my own... 9123 -> 12345.

I ran a UDP receiver application that opens a raw socket (PF_INET and SOCK_RAW), and binds port 12345 on the localhost.

I then ran another app, a UDP raw-socket sender that sent a packet to port 9123 on the localhost.  This packet was received by the receiver application (ie the one expecting to receive on port 12345).

Thus, I would suspect that you have an issue with your application, not so much with the iptable setup.

---

### Post by skypemesm on 2010-10-18
Thanks for your reply. I verified it again in the exact same way as you did. sender on port 9000, two receivers one on 9123 and another on 12345. 

But the messages still arrive on the app on 9123, instead of 12345.

This is ubuntu 10.04 and iptables v1.4.4

Any suggestions?

---

### Post by skypemesm on 2010-10-19
This happens for the two ubuntu 10.04 machines :( What am I doing wrong?

---

### Post by dwhitney67 on 2010-10-19
I run the same OS as you do, on a 32-bit system.  I don't think this matters much.

When you setup the iptables, did you do so as root (or using sudo)?  Sorry, I have to ask.  Were there any errors?

As for your UDP apps, are these indeed using "raw" sockets?  A lot of newbies confuse BSD with "Raw" in the context of discussing Sockets.  (Note, this should not really matter).

If you are indeed running an application that utilizes raw sockets (ie setup with SOCK_RAW), then you would need to launch those applications as root (or using sudo) as well.

If you have covered all of the bases mentioned above, then the next step is to examine the application, because otherwise, I haven't a freakin' clue what could be wrong in your "universe".  As I stated earlier, the test case you presented works just fine for me.

P.S.  Run the following command to verify your iptables setup:
```

sudo iptables -t nat --list

```

---

### Post by skypemesm on 2010-10-19
Thanks for replying again. 
This time I used DGRAM sockets with result the same. I sudo-ed all the commands and never got any errors while installing iptables, and am running this on an AMD 64-bit system.


Output of rules list:

root@ubuntu:~# iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   udp  --  anywhere             anywhere            udp dpt:56789 redir ports 56790 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by dwhitney67 on 2010-10-19
> **skypemesm said:**
> 
Output of rules list:
```

root@ubuntu:~# iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   udp  --  anywhere             anywhere            udp dpt:56789 redir ports 56790 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```


The output above does not jive with what you stated earlier in your opening post.

I would have expected your output to look like:
```

Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   udp  -- !localhost            anywhere            udp dpt:5060 redir ports 56790 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   udp  -- !localhost            anywhere            udp spt:5060 redir ports 56789 

```

---

### Post by skypemesm on 2010-10-19
Yes this output is when I was considering only the incoming rule and redirection for 56789 -> 56790 (similar to your test),
    with a sender application sending packets to 56789. Two receiver apps one on 56789 and another 56790 are present. All these are running on the same machine.

If the rule worked fine, the packets would have been received by 56790. Instead I get the packets on 56789 itself i.e. redirection rule is not working. :(

---


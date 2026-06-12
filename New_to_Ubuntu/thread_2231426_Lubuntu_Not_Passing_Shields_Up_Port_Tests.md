---
title: "Lubuntu Not Passing Shields Up Port Tests"
date: 2014-06-25
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-06-25
I'm wondering if others have tried the Shields Up tests at Gibson Research.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

Last night I ran Lubuntu 13.10 and Mint 17 and both failed the Common Ports test and All Service Ports test with only a few ports operating in Stealth mode.  Mint 17 revealed some information in the File Sharing test.  In both cases I was running live from CD.

In the Port tests, most of the ports were Closed and shown as a Blue square.  The ports operating in Stealth mode are shown as a Green square.  Fortunately, no ports were Red which would indicate an Open port.

Any comments appreciated.

---

### Post by Gyokuro on 2014-06-25
Hi

That's easy to do - you have to enable ufw (ubuntu firewall) via:

sudo enable ufw

but before you do this you have to change in /etc/ufw/before.rules and before6.rules some lines so that that they are look like below lines:

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j DROP
-A ufw-before-input -p icmp --icmp-type source-quench -j DROP
-A ufw-before-input -p icmp --icmp-type time-exceeded -j DROP
-A ufw-before-input -p icmp --icmp-type parameter-problem -j DROP
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

save it and voila you should get stealth scan results. Please note that in case you want to login via ssh you have to enable ssh in ufw. Documentation is here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

- HTH

---

### Post by Lars Noodén on 2014-06-25
The tool is somewhat flawed.  The existence of a stealth mode is rather a myth, so I would not worry too much about it.  Here are two discussions of the concepts:

[http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/](http://www.chrisbrenton.org/2009/07/why-firewall-reject-rules-are-better-than-firewall-drop-rules/)

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) 

Especially for internal connections, reject is more useful.  

About ICMP, if you turn it off, your part of the net will be broken.  It is an essential component even if some systems which do not need to be named have historically had problems with it.  

If you want to see your system from the outside, get a second computer and put zenmap on it.  That will allow you to scan your first computer and make any manner of adjustments to the scan.

---

### Post by KAWill70 on 2014-06-25
Thanks Gyokuro and Lars for the help.

Glad to see that there are solutions.  I had wondered if one should rely on those kinds of tests.

I also read that their site may actually probe your router and not computer so one should check which IP address is actually being used.

---

### Post by sandyd on 2014-06-25
> **KAWill70 said:**
> Thanks Gyokuro and Lars for the help.

Glad to see that there are solutions.  I had wondered if one should rely on those kinds of tests.

I also read that their site may actually probe your router and not computer so one should check which IP address is actually being used.

It doesnt probe your computer - that is unless youve enabled DMZ on your router or your using ipv6

---

### Post by uRock on 2014-06-25
> **sandyd said:**
> It doesn't probe your computer - that is unless you've enabled DMZ on your router or your using ipv6

+1 I recently started using my Cisco 2651 router on my LAN. The only port ShieldsUP! showed being open was the VTY interface that I hadn't applied an ACL to yet. If it were scanning my PC, instead of the router, and I saw the telnet port open, then I would be worried.

---

### Post by KAWill70 on 2014-06-25
> **sandyd said:**
> It doesn't probe your computer - that is unless you've enabled DMZ on your router or you're using ipv6
Many people have no router with connection only to a DSL modem.  In that case, I assume the tests would probe the computer.

---


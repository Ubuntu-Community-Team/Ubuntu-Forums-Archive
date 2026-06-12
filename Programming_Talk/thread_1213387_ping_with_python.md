---
title: "ping with python?"
date: 2009-07-14
forum: Programming Talk
---

### Post by lavinog on 2009-07-14
I am working on a tracker to track computers on a network. In the past I used nmap to create a list of computers online. Now we have some vista computers that respond to ping requests, but are not detected by nmap unless I use -PE and sudo.

As a workaround I am using the ping command (which doesn't require root.)
Is there a python way to ping computers without needing to be root?

Would I be better off using the ping command instead?

---

### Post by ghostdog74 on 2009-07-14
> **lavinog said:**
> 

Would I be better off using the ping command instead?
yes, why not. provided icmp is not blocked.

---

### Post by unutbu on 2009-07-14
If you'd like to do this from within python, check out the python-scapy package:
```

Description: Packet generator/sniffer and network scanner/discovery
 Scapy is a powerful interactive packet manipulation tool, packet
 generator, network scanner, network discovery, packet sniffer, etc. It
 can for the moment replace hping, 85% of nmap, arpspoof, arp-sk, arping,
 tcpdump, tethereal, p0f, ....
 .
 In scapy you define a set of packets, then it sends them, receives
 answers, matches requests with answers and returns a list of packet couples
 (request, answer) and a list of unmatched packets. This has the big advantage
 over tools like nmap or hping that an answer is not reduced to
 (open/closed/filtered), but is the whole packet.
 .
  Homepage: http://www.secdev.org/projects/scapy/
```

And for a demo:
[http://www.secdev.org/projects/scapy/demo.html](http://www.secdev.org/projects/scapy/demo.html)

PS: The above was found with this command:
```
apt-cache search network | awk '/^python/{print $1}' | while read pkg; do apt-cache show "$pkg"; done
```

---

### Post by juancarlospaco on 2009-07-14
like a **Pyng **:) 
*just kidding i can't resist, sorry.*

---


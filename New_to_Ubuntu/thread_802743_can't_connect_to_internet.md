---
title: "can't connect to internet"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by distractible on 2008-05-21
Hi! I'm really new and not at all tech savvy so bear with me here. I made the mistake of trying to upgrade to Hardy Heron but could find no way to connect to the internet. I experimented for a while and searched the forums here but nobody seemed to be answering my questions. Finally I "downgraded" back to Gutsy because that worked fine before. But now I still can't figure out how to connect to either wired or wireless! When I plug in the cable to attempt to connect to the wired network the little icon on the toolbar looks like it is connected, but I can't access any web pages. 
I found the tutorial in the help menu which told me to ping a particular address. But it didn't work--I got a 0% return of whatever packages it was sending. What is my next step? When I installed Gutsy originally last year the wired connection worked immediately although I had to get a friend to help me with the wireless one.
Thanks in advance for your help--like I say, I'm new at this and no good with computers at the best of times!! : )

---

### Post by tdrusk on 2008-05-21
> **distractible said:**
> Hi! I'm really new and not at all tech savvy so bear with me here. I made the mistake of trying to upgrade to Hardy Heron but could find no way to connect to the internet. I experimented for a while and searched the forums here but nobody seemed to be answering my questions. Finally I "downgraded" back to Gutsy because that worked fine before. But now I still can't figure out how to connect to either wired or wireless! When I plug in the cable to attempt to connect to the wired network the little icon on the toolbar looks like it is connected, but I can't access any web pages. 
I found the tutorial in the help menu which told me to ping a particular address. But it didn't work--I got a 0% return of whatever packages it was sending. What is my next step? When I installed Gutsy originally last year the wired connection worked immediately although I had to get a friend to help me with the wireless one.
Thanks in advance for your help--like I say, I'm new at this and no good with computers at the best of times!! : )
Try restarting with the cable plugged in.

---

### Post by neurostu on 2008-05-21
You say you are using a wired connection? What are you plugging your computer into (A LAN, a router, a modem)?  When you plug in your ethernet cable and the icon says that you are connected open a terminal and type:
```

ifconfig

```
and paste the results below.

---

### Post by distractible on 2008-05-21
Wow, you guys are speedy.
I tried restarting with the cable plugged in, but no luck unfortunately!
I'm plugging it into a DSL modem--and I would copy and paste what it says only I can't connect to the internet from it, so I'm using a different computer here. However, I'll type it:
eth0 Link encap: Ethernet HWaddr 00:1B:38:34:54:E0
UP BROADCST MULTICAST MTU:1500 Metric: 1
RX packets: 67 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 86 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 5685 (5.5 KB) TX bytes: 9114 (8.9 KB)
Interrupt: 20 Base address: 0xa000

and then it says

lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0\inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU: 16436 Metric 1

then it goes into te RX packets and TX packets but the numbers are all O from there.
Does this help?

---

### Post by neurostu on 2008-05-21
> **distractible said:**
> 
eth0 Link encap: Ethernet HWaddr 00:1B:38:34:54:E0
UP BROADCST MULTICAST MTU:1500 Metric: 1
RX packets: 67 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 86 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 5685 (5.5 KB) TX bytes: 9114 (8.9 KB)
Interrupt: 20 Base address: 0xa000

lo Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0\inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU: 16436 Metric 1


Is this when the ethernet cable is plugged in?

---

### Post by distractible on 2008-05-21
Oh! Sorry. When I plug in the cable I get the same first line then
inet addr: 192.168.0.2 Bcast: 192.168.0.255 Mask: 255.255.255.0
inet6 addr: fe80::21b:38ff:fe34:5430/64 Scope:Link
Then more of the same stuff as before only with different numbers of RX packets and TX packets and things.

---

### Post by neurostu on 2008-05-21
ok so when you plug in the modem you are getting assigned an IP address: 192.168.0.2  what you should try doing is pinging your router, try:
```

ping 192.168.0.1

```
post the response. 
Then try pinging a numeric ip:
```

ping 18.4.1.1

```
then try pinging a url:
```

ping www.ubuntuforums.org

```

Post all the results.

---

### Post by distractible on 2008-05-21
Scary! When I ping the IP address I get something like this:
64 bytes from 192.168.0.1: icmp_seq= various numbers ttl+ 255 time= various numbers
and then it just repeats. Same thing happens with the numeric IP. Then if I try ubuntuforums I get
ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by neurostu on 2008-05-21
Ok so it looks like your having a DNS problem. DNS = Domain Name Server.  Domain name servers translate things like [www.google.com](www.google.com) into an IP address.   So I don't have my ubuntu machine with me so I can't talk you through reseting your DNS, but I think if you right click on your network Icon, click Manual Configuration, there should be a "DNS" tab look under there and delete anything that is present. 

Read this, and follow the DNS instructions:
[https://help.ubuntu.com/7.10/server/C/network-configuration.html](https://help.ubuntu.com/7.10/server/C/network-configuration.html)


If this doesn't work call your ISP about configure your computer to connect to their DNS.

---

### Post by distractible on 2008-05-21
OK, thank you! I tried resetting the DNS addresses to what they were before (back when the computer was able to connect to the internet!), but that didn't work. I haven't been able to follow the instructions you linked to yet because I keep getting "permission denied" when I enter /etc/resolv.conf in the terminal. But I will keep trying, and will try the ISP tomorrow if no luck.
Thanks for your help!

---

### Post by neurostu on 2008-05-21
when you edit /etc/resolv.conf you have to use sudo, its a protected file!

---


---
title: "modem change mtu"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by whitecore on 2008-07-25
I would like to know how to lower the mtu from 1500 to 576 which if i rember correctly in windows had caused me to have bottlenecks in bandwidth i am using 7.10.I have found guides for network cards but not for modems.

---

### Post by phidia on 2008-07-25
There's a dial up guide [here]("https://help.ubuntu.com/community/DialupAndFax") I remember that at least one of the gui dialers let you edit the mtu value..do you have gnome-ppp or chestnut dialer? In kde it would be kppp.

---

### Post by whitecore on 2008-07-25
I use terminal pppconfig pon/poff.

---

### Post by fatality_uk on 2008-07-25
Tyoe the following into a terminal:
> sudo ifconfig ppp0 mtu 576
That will change the MTU for device ppp0
I set my broadband connection set to 1458 using this method

---

### Post by whitecore on 2008-07-25
I firgured it out already that was the part i didn't understand browsing works way better noy but downloading still drops to zero every few seconds.

---

### Post by bab1 on 2008-07-25
I would use the largest MTU (up to a max of 1500) that the modem will handle.  The smaller the MTU, the more fragmented the packets are.  The MTU is how big an ***Ethernet frame*** is.  1500 bits is 187.5 Bytes (not much human info there).  Most problems related to MTU is from large packets (larger than 1500).  Large packets can be dropped as they exceed the Ethernet standard.  This causes re-transmission and network slowdown.

---

### Post by caljohnsmith on 2008-07-26
> **bab1 said:**
> I would use the largest MTU (up to a max of 1500) that the modem will handle.  The smaller the MTU, the more fragmented the packets are.  The MTU is how big an ***Ethernet frame*** is.  1500 bits is 187.5 Bytes (not much human info there).  Most problems related to MTU is from large packets (larger than 1500).  Large packets can be dropped as they exceed the Ethernet standard.  This causes re-transmission and network slowdown.
Actually, I think you meant to say bytes, not bits: an MTU of 1500 (as set in Ubuntu) is 1500 bytes, not bits. :)

Whitecore, if you want to know a method to figure out exactly what your MTU should be, you can do it with the "ping" command. See this thread for details if you are interested:
[http://ubuntuforums.org/showthread.php?t=869621](http://ubuntuforums.org/showthread.php?t=869621)

---

### Post by whitecore on 2008-07-27
That link was helpfull "caljohnsmith" but if i change the mtu dont i have to change the tcp receive window (rwin).

---

### Post by caljohnsmith on 2008-07-27
> **whitecore said:**
> That link was helpfull "caljohnsmith" but if i change the mtu dont i have to change the tcp receive window (rwin).
The TCP receive window (RWIN) is independent of your MTU setting. RWIN depends on the BDP (Bandwidth Delay Product) for your internet connection, and BDP can be calculated as:
```
max bandwidth of your internet connection (Bytes/second) * round-trip time (RTT) 
```
Therefore RWIN does not depend on the TCP packet size, and TCP packet size is of course limited by the MTU (Maximum Transmission Unit).

Note the RTT is most easily determined using "ping". But since the RTT varies for each packet you send to the internet, finding the optimal RWIN value is not an exact science. In other words, depending on how large of a TCP packet you send, and depending on where you send each packet (e.g. to a website clear across the globe vs. your ISP's local website), you will get different RTTs. And on top of that, I believe the Linux kernel is configured by default to use a dynamic approach to setting the RWIN value, so it tries to optimize RWIN for your particular connection. Yet I have seen in various Linux forums where people have gained a significant speed advantage after they optimized their own RWIN values. So if you are really intent on changing RWIN, I can give more details how to do it, otherwise I probably wouldn't bother.

---

### Post by whitecore on 2008-07-27
That is what i have been trying to change as my windows system has stabalized by changing these two settings in windows. I have found info for linux but didn't understand it.

---

### Post by caljohnsmith on 2008-07-28
whitecore, I decided to just write a tutorial for MTU and RWIN since some of my friends expressed some interest in how it is done in Ubuntu. Here's the guide:
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)

---

### Post by whitecore on 2008-07-28
thanks for all your help.

---


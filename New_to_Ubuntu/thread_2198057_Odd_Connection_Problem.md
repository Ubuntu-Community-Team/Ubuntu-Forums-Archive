---
title: "Odd Connection Problem"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by mlnease on 2014-01-06
Hello,

I have no way of knowing if this is an Ubuntu problem; if it isn't, and someone can recommend a different venue for troubleshooting. I'll be grateful.  

I dual-boot with Xubuntu 12.04/Xfce and Ubuntu 10.04/GNOME2 (yeah, I know).  For the last couple of days I've been unable to connect to either sourceforge.net or slashdot.com via Firefox in either of these OS's--my internet connection seems normal otherwise.

The error message I receive is "Unable to connect -- Firefox can't establish a connection to the server at xxx."

I *can*, however, access both sites via TOR network.

I have disabled (and of course re-enabled) ufw (also IPBlock in Lucid) but to no avail; I've also completely uninstalled and reinstalled Firefox (including deleting .mozilla), also to no avail.

Anyone else having a similar problem?  Any advice would be greatly appreciated.

Thanks in advance.

---

### Post by devine.steve on 2014-01-06
Are you saying that you are only having problems with those two sites? Is what does this do for you?
```

nslookup sourceforge.net
nslookup slashdot.com
```

---

### Post by mlnease on 2014-01-06
> **devine.steve said:**
> Are you saying that you are only having problems with those two sites? Is what does this do for you?
Code:
nslookup sourceforge.net
nslookup slashdot.com

Yes, exactly.

```
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
Name:    sourceforge.net
Address: 216.34.181.60
```

```
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
Name:    slashdot.com
Address: 216.34.181.45
```

Thanks for the quick response!

---

### Post by Iowan on 2014-01-06
Check **ifconfig**
Try changing MTU to 1492 via ```
sudo ifconfig eth0 mtu 1492
```
You can put it back if it doesn't help (or try lower value).

---

### Post by devine.steve on 2014-01-06
Those IP's are good. Try putting the IP addresses in the URL bar. 
Also run this:
traceroute slashdot.com

---

### Post by mlnease on 2014-01-06
Thanks again but no, same error message(s).

p.s.  I have (and had) also tried pasting the IP addresses in the URL bar, with the same result.

---

### Post by steeldriver on 2014-01-06
what about your routing table?

```
route -n
```
or
```
ip route show
```

---

### Post by mlnease on 2014-01-06
> **devine.steve said:**
> Those IP's are good. Try putting the IP addresses in the URL bar. 
Also run this:
traceroute slashdot.com

```
traceroute to slashdot.com (216.34.181.45), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  2.396 ms  2.458 ms  2.531 ms
 2  * * *
 3  216-235-124-HCC-94.hcc.net (216.235.124.94)  15.348 ms  15.504 ms  21.776 ms
 4  216-235-124-HCC-17.hcc.net (216.235.124.17)  22.026 ms  22.107 ms  22.187 ms
 5  216-235-124-HCC-14.hcc.net (216.235.124.14)  22.501 ms  22.582 ms  22.661 ms
 6  216-235-124-HCC-13.hcc.net (216.235.124.13)  28.145 ms  10.977 ms  12.914 ms
 7  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.127 ms  19.417 ms  19.579 ms
 8  216-235-124-HCC-13.hcc.net (216.235.124.13)  19.684 ms  19.762 ms  20.098 ms
 9  216-235-124-HCC-14.hcc.net (216.235.124.14)  20.193 ms  20.273 ms  20.354 ms
10  216-235-124-HCC-13.hcc.net (216.235.124.13)  26.231 ms  26.466 ms  27.028 ms
11  216-235-124-HCC-14.hcc.net (216.235.124.14)  26.551 ms  26.631 ms  26.692 ms
12  216-235-124-HCC-13.hcc.net (216.235.124.13)  20.149 ms  13.340 ms  13.570 ms
13  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.655 ms  19.964 ms  20.182 ms
14  216-235-124-HCC-13.hcc.net (216.235.124.13)  20.272 ms  20.352 ms  20.430 ms
15  216-235-124-HCC-14.hcc.net (216.235.124.14)  20.538 ms  26.216 ms  26.368 ms
16  216-235-124-HCC-13.hcc.net (216.235.124.13)  26.647 ms  26.728 ms  27.221 ms
17  216-235-124-HCC-14.hcc.net (216.235.124.14)  27.061 ms  12.242 ms  18.792 ms
18  216-235-124-HCC-13.hcc.net (216.235.124.13)  14.486 ms  20.645 ms  20.807 ms
19  216-235-124-HCC-14.hcc.net (216.235.124.14)  21.570 ms  21.649 ms  21.727 ms
20  216-235-124-HCC-13.hcc.net (216.235.124.13)  21.914 ms  21.994 ms  27.092 ms
21  216-235-124-HCC-14.hcc.net (216.235.124.14)  27.321 ms  27.393 ms  27.472 ms
22  216-235-124-HCC-13.hcc.net (216.235.124.13)  27.590 ms  33.655 ms  33.703 ms
23  216-235-124-HCC-14.hcc.net (216.235.124.14)  33.837 ms  14.615 ms  27.233 ms
24  216-235-124-HCC-13.hcc.net (216.235.124.13)  34.570 ms  36.159 ms  36.243 ms
25  216-235-124-HCC-14.hcc.net (216.235.124.14)  35.462 ms  35.526 ms  35.606 ms
26  216-235-124-HCC-13.hcc.net (216.235.124.13)  36.230 ms  36.310 ms  36.391 ms
27  216-235-124-HCC-14.hcc.net (216.235.124.14)  35.626 ms  35.705 ms  35.786 ms
28  216-235-124-HCC-13.hcc.net (216.235.124.13)  36.410 ms  36.492 ms  36.552 ms
29  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.370 ms  14.943 ms  15.148 ms
30  216-235-124-HCC-13.hcc.net (216.235.124.13)  15.375 ms  15.452 ms  21.557 ms
```

---

### Post by mlnease on 2014-01-06
```
traceroute to slashdot.com (216.34.181.45), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  2.396 ms  2.458 ms  2.531 ms
 2  * * *
 3  216-235-124-HCC-94.hcc.net (216.235.124.94)  15.348 ms  15.504 ms  21.776 ms
 4  216-235-124-HCC-17.hcc.net (216.235.124.17)  22.026 ms  22.107 ms  22.187 ms
 5  216-235-124-HCC-14.hcc.net (216.235.124.14)  22.501 ms  22.582 ms  22.661 ms
 6  216-235-124-HCC-13.hcc.net (216.235.124.13)  28.145 ms  10.977 ms  12.914 ms
 7  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.127 ms  19.417 ms  19.579 ms
 8  216-235-124-HCC-13.hcc.net (216.235.124.13)  19.684 ms  19.762 ms  20.098 ms
 9  216-235-124-HCC-14.hcc.net (216.235.124.14)  20.193 ms  20.273 ms  20.354 ms
10  216-235-124-HCC-13.hcc.net (216.235.124.13)  26.231 ms  26.466 ms  27.028 ms
11  216-235-124-HCC-14.hcc.net (216.235.124.14)  26.551 ms  26.631 ms  26.692 ms
12  216-235-124-HCC-13.hcc.net (216.235.124.13)  20.149 ms  13.340 ms  13.570 ms
13  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.655 ms  19.964 ms  20.182 ms
14  216-235-124-HCC-13.hcc.net (216.235.124.13)  20.272 ms  20.352 ms  20.430 ms
15  216-235-124-HCC-14.hcc.net (216.235.124.14)  20.538 ms  26.216 ms  26.368 ms
16  216-235-124-HCC-13.hcc.net (216.235.124.13)  26.647 ms  26.728 ms  27.221 ms
17  216-235-124-HCC-14.hcc.net (216.235.124.14)  27.061 ms  12.242 ms  18.792 ms
18  216-235-124-HCC-13.hcc.net (216.235.124.13)  14.486 ms  20.645 ms  20.807 ms
19  216-235-124-HCC-14.hcc.net (216.235.124.14)  21.570 ms  21.649 ms  21.727 ms
20  216-235-124-HCC-13.hcc.net (216.235.124.13)  21.914 ms  21.994 ms  27.092 ms
21  216-235-124-HCC-14.hcc.net (216.235.124.14)  27.321 ms  27.393 ms  27.472 ms
22  216-235-124-HCC-13.hcc.net (216.235.124.13)  27.590 ms  33.655 ms  33.703 ms
23  216-235-124-HCC-14.hcc.net (216.235.124.14)  33.837 ms  14.615 ms  27.233 ms
24  216-235-124-HCC-13.hcc.net (216.235.124.13)  34.570 ms  36.159 ms  36.243 ms
25  216-235-124-HCC-14.hcc.net (216.235.124.14)  35.462 ms  35.526 ms  35.606 ms
26  216-235-124-HCC-13.hcc.net (216.235.124.13)  36.230 ms  36.310 ms  36.391 ms
27  216-235-124-HCC-14.hcc.net (216.235.124.14)  35.626 ms  35.705 ms  35.786 ms
28  216-235-124-HCC-13.hcc.net (216.235.124.13)  36.410 ms  36.492 ms  36.552 ms
29  216-235-124-HCC-14.hcc.net (216.235.124.14)  13.370 ms  14.943 ms  15.148 ms
30  216-235-124-HCC-13.hcc.net (216.235.124.13)  15.375 ms  15.452 ms  21.557 ms
```

Afraid it doesn't mean much to me, though--

---

### Post by mlnease on 2014-01-06
> **steeldriver said:**
> what about your routing table?

```
route -n
```

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```
or
```
ip route show
```

```
default via 192.168.1.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.101  metric 2
```

*Really* appreciate your time and effort, by the way.

---

### Post by Iowan on 2014-01-06
wlan0? That would explain why changing MTU for eth0 had no effect...

---

### Post by devine.steve on 2014-01-06
Wow .. thats odd. 
try traceroute cnn.com

---

### Post by devine.steve on 2014-01-06
This from wikipedia:
[h=3]Site operators may block traffic from Tor exit nodes[/h] Operators of Internet sites have the ability to prevent connections  from Tor exit nodes, or to offer reduced functionality to Tor users. For  example, it is not generally possible to edit [Wikipedia]("http://en.wikipedia.org/wiki/Wikipedia") when using Tor, or when using an IP address that also is used by a Tor exit node, due to the use of the [TorBlock]("http://www.mediawiki.org/wiki/Extension:TorBlock") MediaWiki extension, unless an [exemption]("http://en.wikipedia.org/wiki/Wikipedia:IP_block_exemption") is obtained.
Wonder if this applies?

---

### Post by mlnease on 2014-01-06
A ton of code here, I seem to recall that there's a way to compress it but I forget...

---

### Post by mlnease on 2014-01-06
traceroute to cnn.com (157.166.226.25), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.098 ms  1.975 ms  2.845 ms
 2  * * *
 3  216-235-124-HCC-94.hcc.net (216.235.124.94)  20.798 ms  21.032 ms  21.111 ms
 4  216-235-124-HCC-17.hcc.net (216.235.124.17)  21.231 ms  21.310 ms  26.984 ms
 5  ge-1-3-1-32767-sur01.olympia.wa.seattle.comcast.net (50.200.119.17)  27.457 ms  27.539 ms  27.619 ms
 6  xe-12-0-1-0-ar03.seattle.wa.seattle.comcast.net (68.86.99.149)  37.448 ms  19.181 ms  17.358 ms
 7  he-1-12-0-0-10-cr01.seattle.wa.ibone.comcast.net (68.86.93.173)  20.360 ms he-1-3-0-0-11-cr01.seattle.wa.ibone.comcast.net (68.86.93.169)  26.251 ms he-1-5-0-0-11-cr01.seattle.wa.ibone.comcast.net (68.86.94.65)  27.526 ms
 8  4.68.63.65 (4.68.63.65)  45.612 ms  45.679 ms  45.758 ms
 9  ae-32-52.ebr2.Seattle1.Level3.net (4.69.147.182)  103.840 ms  104.089 ms  104.178 ms
10  ae-2-2.ebr2.Denver1.Level3.net (4.69.132.54)  106.865 ms  106.600 ms  106.695 ms
11  ae-1-100.ebr1.Denver1.Level3.net (4.69.151.181)  109.214 ms  109.311 ms  108.675 ms
12  ae-2-2.ebr2.Dallas1.Level3.net (4.69.132.106)  98.272 ms  95.747 ms  94.078 ms
13  ae-92-92.csw4.Dallas1.Level3.net (4.69.151.165)  102.136 ms ae-62-62.csw1.Dallas1.Level3.net (4.69.151.129)  102.532 ms ae-72-72.csw2.Dallas1.Level3.net (4.69.151.141)  101.826 ms
14  ae-73-73.ebr3.Dallas1.Level3.net (4.69.151.146)  101.373 ms ae-63-63.ebr3.Dallas1.Level3.net (4.69.151.134)  96.514 ms ae-93-93.ebr3.Dallas1.Level3.net (4.69.151.170)  96.784 ms
15  ae-7-7.ebr3.Atlanta2.Level3.net (4.69.134.22)  102.826 ms  103.678 ms  102.370 ms
16  ae-73-73.ebr2.Atlanta2.Level3.net (4.69.148.254)  103.764 ms ae-63-63.ebr1.Atlanta2.Level3.net (4.69.148.242)  102.623 ms ae-73-73.ebr2.Atlanta2.Level3.net (4.69.148.254)  103.827 ms
17  ae-2-52.edge4.Atlanta2.Level3.net (4.69.150.77)  112.012 ms *  112.073 ms
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

---

### Post by mlnease on 2014-01-06
I don't think so--I only run TOR as client and I *am* able to access these sites via TOR, just not normally via Firefox and my ISP.

---

### Post by devine.steve on 2014-01-06
OK so it works when you are using TOR but doesn't when you aren't? Plus the traceroute to cnn is normal. The other looks like some kind of anomaly with your ISP. Like it's just bouncing back and forth between two switches.

---

### Post by mlnease on 2014-01-06
I thought it a bit weird too, seems to be connected to my IP address (so TOR works)?  I guess I should contact my ISP and assume that this problem isn't related to either of my OS's--or to Firefox etc.  Does that make sense to you?

If it isn't obvious, I'm a complete *naïf* when it comes to networking.  Thanks so *very* much for your time and patience.

If I'm able to resolve this via my ISP, I'll be sure to post my results and mark the thread appropriately.

Thanks again!

---

### Post by devine.steve on 2014-01-06
Has it been doing this long? It would be cool if you could try this from another machine. Do you have a phone that works with your home wireless? 0

---

### Post by mlnease on 2014-01-06
Forty-eight hours that I know of--I was a bit out of the loop for a day or so so it could be a bit more (or possibly less).  

No, I'm an old geezer with no smart phone or, at this point even a cel phone!  I could--conceivably--drag my desktop downstairs and try a dial-up (are ye old enough to remember what that means?)  But that wouldn't address the problem anyway, would it?

Thanks for the thought, though.

I suppose I could try it from a virtual machine on one of my OS's, but I think that'd almost certainly yield the same result.

---

### Post by mlnease on 2014-01-07
My issue resolved itself spontaneously this AM.  

Steve, Steeldriver and Iowan, thanks a million for your time and for the crash course in network troublshooting.

---


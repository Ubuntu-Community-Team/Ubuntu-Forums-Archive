---
title: "ipv6 on ubuntu when ISP has native ipv6 capability"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by luvs on 2012-07-09
Not a lot out there on what one has to do to get ipv6 to work in ubuntu when one's ISP is ipv6 native.  I appreciate any help with this.  As it is, I am just getting started with this and cannot ping6 any sites as of yet.

luvs

---

### Post by Kopkins on 2012-07-09
I use a package called miredo, but it's a tunneling program. It tunnels ipv6 through ipv4. I'm unsure if my ISP is native supported. You can give it a shot if you'd like. 

```
sudo apt-get install miredo
```I can ping6 ipv6 sites. 

```
ping6 ipv6.google.com
```Kopkins

---

### Post by miegiel on 2012-07-09
> **luvs said:**
> Not a lot out there on what one has to do to get ipv6 to work in ubuntu when one's ISP is ipv6 native.  I appreciate any help with this.  As it is, I am just getting started with this and cannot ping6 any sites as of yet.

luvs

I have no IPv6 experience yet, but after booting it says in my log (*/var/log/syslog*) the following:
```
Jul  9 07:22:48 machine kernel: [  124.432041] eth0: no IPv6 routers present
```
Which implies to me that IPv6 should work out of the box, as long as the connecting hardware at home (modem, router, bridge, wifi AP, what ever) support IPv6 too.

---

### Post by lemming465 on 2012-07-11
For native IPv6, all the gear in the path to your device has to support IPv6, e.g. your ISP, your broadband modem, and your wifi gear or router.  Contemporary OS's such as Ubuntu, windows 7, or Mac OS-X all have IPv6 on by default, so the client end is probably OK.  "eth0 no IPv6 routers present" means that the upstream device is not emitting ICMPv6 Router Advertisements, which are the only way to find your on-link (ethernet or wifi) gateway routers, which are how you get off-link toward the general internet in IPv6.  The big difference between IPv6 gateways and IPv4 gateways is that you always use the link-local scope fe80::/64 address from a router advertisement in v6, whereas in v4 you typically get the gateway address from a DHCPv4 option.

You can probe your LAN from userspace with "rdisc6 eth0" to send ICMPv6 router solicitations, and see if anyone answers.  Silence/failure means you don't have native v6 yet.

For Kopkins, "miredo" is one of several possible tunneling protocols for encapsulating IPv6 in IPv4 to get across an IPv4-only moat to the actual IPv6 internet.  In general the automatic tunnels such as Teredo protocol (what miredo implements) and 6to4 don't work very well, and are deprecated.  Failure rates on connections can be as high as 45% and round trip latency can go through the roof, e.g. one Teredo connection I tested with had me in North America, my Teredo server in Europe, and my Teredo relay in Japan.  Nothing was going to happen quickly with that much ocean hopping.

Native IPv6 is best.  Next best is if your near-native ISP supports "6rd".  Failing support from your ISP, you'll get the best results from setting up a point-to-point tunnel with one of the brokers such as Hurricane Electric, Gogo6, or Sixxs.

---

### Post by sanderj on 2012-07-23
> **luvs said:**
> Not a lot out there on what one has to do to get ipv6 to work in ubuntu when one's ISP is ipv6 native.  I appreciate any help with this.  As it is, I am just getting started with this and cannot ping6 any sites as of yet.

luvs

***If*** your ISP offers native IPv6, you probably have to apply for IPv6 at your ISP and/or turn on IPv6 in your modem/router. After that, you don't have to do anything on your Ubuntu; the modem/router will provide IPv6 just like it provides IPv4, and Ubuntu will pick it up and use it.

But how do you know that your ISP does provide native IPv6? Can you tell which ISP you have?

---


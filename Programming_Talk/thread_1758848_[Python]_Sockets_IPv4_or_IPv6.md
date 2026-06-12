---
title: "[Python] Sockets: IPv4 or IPv6"
date: 2011-05-15
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-15
Writing a p2p program, IPv4 or IPv6. I've searched Google for IPv6 programming. I've found a plethora of opinions on whether programmers should program with IPv6 or not and just wanted you guys opinions.

---

### Post by simeon87 on 2011-05-15
Support both. IPv6 is gaining ground and IPv4 won't disappear overnight so you'll need both in the years to come.

---

### Post by ki4jgt on 2011-05-15
Do most modern computers support IPv6? What about ISPs? If they do, then I may just do IPv6 The only problem I could think of is the router :-(

---

### Post by simeon87 on 2011-05-15
> **ki4jgt said:**
> Do most modern computers support IPv6? What about ISPs? If they do, then I may just do IPv6 The only problem I could think of is the router :-(

Yes, they are. I'm sure modern hardware is also prepared for it.

---

### Post by lemming465 on 2011-05-15
> Do most modern computers support IPv6?
PC and smartphone OS's released in this decade such as windows 7, Mac OS-X 10.6.5, Ubuntu 10.04, Redhat 6 etc. have decent v6 support.  (Apple prior to 10.6.5 sucked, and is still the weakest.)  Dual stack with v4+v6 will generally be fairly trouble free, at least if the clients are doing DHCPv4 + SLAAC v6.  Even XP can sort of manage that if you run *net install ipv6*.

> What about ISPs?
About 85% of the world's ISPs are currently rolling out v6.  Only a few such as free.fr or xs4all.nl have completed it.  China Telecom expects to add about 30m broadband users this year, but has only about 10m v4 addresses left, and APNIC ran out last month, so there will be a lot of v6-only users in China this year.  In the USA, all of the 4G mobile data rollouts are v6-only too.  Which helps one understand why sites like Google, Yahoo, and Facebook are already v6-ready and why they instigated [world IPv6 test day]("http://www.isoc.org/wp/worldipv6day/") on June 8th.

 > ... I may just do IPv6
Currently the v6-only internet is only 0.2%, and the dual-stack internet is only about 5-10%.  We are still 4-6 years away from v6 being universally available and the dominant protocol, so for now you should plan on being dual-stack.  Being v4-only would be a ticket to rapid irrelevance; in 2013 the internet may be 15% v6-only clients assuming current growth rates continue.

Fortunately, API's for being dual-stack by using v6 interfaces with v4-mapped addresses (::FFFF:p.q.r.s) are pretty common in most language's library support.
You mostly have to watch out for log analysis, web cookies, DB columns etc. not being ready for 128 bit addresses.  Easier than Y2K, really.

> The only problem I could think of is the router
The installed base of consumer broadband modems and wifi routers mostly flubs both native and tunneled IPv6.  Cable modems prior to DOCSIS 3 are hopeless, on the DSL front the broadband forum didn't even have a defined v6 profile until November 2010, and in March's round of interoperability tests at UNH-IOL, all the brand new gear still got DHCPv6 wrong. (June's firmware could be better ...).

When ISP's start offering either native v6 or near-native (6rd) v6, consumers will mostly have to upgrade network gear.  It's a lot like the transition from analog TV to digital: new equipment for mostly the same content.

All is not sweetness and light upstream, either.

* Most enterprise gear can do v6.  But the older stuff may have feature or performance problems with it.

* A lot of backbone providers have inadequate v6-peering, and only give you 85% reachability of the v6 internet.  I suggest including someone v6-aggressive like Hurricane Electric in your peering plans.

* Since v6 routers don't fragment, v6 is more dependent on ICMP feedback for path MTU discovery.  Your servers should probably peg themselves at the v6-minimum of 1280 bytes to minimize client trauma with unknown amounts of tunneling, bad firewalls that block all ICMP, congested routers that rate-limit and preferentially drop ICMP, etc.

* 0.3% of clients (data from APNIC, Google, Yahoo, and Swedish ISP's) have broken IPv6 configs, mostly 6to4 tunnels with partial blocking of protocol 41, mostly (90%) from downlevel Mac OS-X boxes.  If you dual stack your servers, a few clients will either fail to connect or have really long timeouts.  Think *15 minutes* to retrieve a complex web page by falling back to v4, when people with working v4-only or working dual-stack v4+v6 or v6-only get it in 300 milliseconds.  World IPv6 day may flush a lot of these folks out and give them impetus to fix themselves.

---


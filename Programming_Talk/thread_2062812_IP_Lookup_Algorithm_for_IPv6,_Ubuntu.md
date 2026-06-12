---
title: "IP Lookup Algorithm for IPv6, Ubuntu"
date: 2012-09-25
forum: Programming Talk
---

### Post by Tozak on 2012-09-25
Hi there, 

This is my first post. I did some google'ing but could not able to find an answer, unfortunately.

I am searching for **what kind of IP routing lookup algorithm** does ubuntu uses for **IPv6**. 

The reason I search for this information is that I need to choose an algorithm, but I want to know common selected algorithms, and Ubuntu is a good example.

Thanks very much,

---

### Post by trent.josephsen on 2012-09-25
Routing is specified by the Internet Protocol and not OS-specific. I'm not really sure what algorithm you're asking for.

---

### Post by lemming465 on 2012-09-27
If would be helpful if you could tell us in more detail about what you are looking for and why.

On the LAN, ubuntu is like any other IPv6 client, and listens for ICMPv6 router advertisements to find the link-local (fe80::/64) addresses of the on-link upstream routers.  On a simple network there will be only one advertised prefix for clients and one default router.  Unlike windows vista/7/8 ubuntu won't do automatic tunnels by default.  You can do any of 6in4, 6to4 or Teredo tunnels if you want.  Install the "miredo" package for Teredo.  In general 6to4 and Teredo will fail a lot, and ISATAP isn't available, so I recommend 6in4 point to point tunnels if you can't get native v6.

IPv6 and IPv4 have separate routing tables in the kernel.  Display them with **ip -4 route show ; ip -6 route show**  It's pretty much up to the applications to pick which kind of address they want to use.  Dual stack applications using the getaddrinfo(3) C library routine will get mapped v4 addresses 0::ffff:a.b.c.d intermingled with their native v6 addresses.  The kernel will route packets with those destinations out the v4 stack.

The default sort order for getaddrinfo() is controlled by /etc/gai.conf; if that is commented out the built-in preferences follow RFC 3484.  I don't know if [RFC 6724]("http://tools.ietf.org/html/rfc6724") which just obsoleted that is too new to have made it into the quantal beta; probably.  The main change is to further deprecate automatic v6 tunnel addresses.  There are 18 rules in the RFC's about how to pick source and destination addresses, which address all the intricacies of temporary versus permanent, preferred versus deprecated, mobile care-of versus mobile home, matching address scopes (IPv6 has 7) etc.  In the simple case of a PC with one active network interface, one global IPv6 prefix (either native on-link or tunneled), and one IPv4 address on the active interface, these collapse to:
   1) use a protocol and source address which match the destination, if the destination has only v4 or only v6
   2) if the destination has both v4 and v6, but one of your source addresses is native and the other is tunneled, use the native one.  Note that private IPv4 is assumed to be native, so it will be preferred to e.g. Teredo (2001:0::/32) or 6to4 (2002::/16).
   3) if it's native dual-stack all around, believe in the future and prefer v6 to v4

The main differences from IPv4 are that router advertisements are required, that DHCPv6 behavior is controlled by flags in the router advertisements, and that active interfaces will use both fe80::/64 link-local addresses and 2000::/3 global scope addresses simultaneously.

---


---
title: "Writting network application (questions about IPv6)"
date: 2007-05-05
forum: Programming Talk
---

### Post by _tomcio on 2007-05-05
Hi!

I have some free time now and I'm going learn something about using IPv6 in network applications. I'm still new to IPv6 and I have some questions. Such situation:

We have server supporting both IPv4 and IPv6.
1. Can I bind IPv6 socket to address "123.123.123.123"?
[INDENT]1.2 If I convert address "123.123.123.123" to IPv4-mapped IPv6 address and bind IPv6 socket on this address, will both IPv4 and IPv6 clients will be able to connect with my server (for IPv6 client I will map address above address to make it a valid IPv6 address)?[/INDENT]

2. I tried to resolve IP address of 'www.google.pl' using function 'getaddrinfo ()'. Everything works fine, but when I set AF_INET as a protocol family in 'hints' arg of this function. When I changed it to AF_INET6 function returned error  (I'm not sure, but I think it was "EAI_NODATA"). So it seems, that function failed, because 'www.google.pl' can be translated by my DNS server only on IPv4 address, am I right? To connect with 'www.google.pl' using IPv6 client I must convert IPv4 address of 'www.google.pl' to mapped Ipv6 address and everything will work?

---


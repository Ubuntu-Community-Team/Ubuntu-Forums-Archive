---
title: "curl private dns"
date: 2015-05-05
forum: Programming Talk
---

### Post by Yogesh_Nain on 2015-05-05
Can i provide my private DNS in curl for my software?
   this is the command not working
      >   curl --dns-ipv4-addr <dns address> google.com
      >   current version of curl 7.43.0
      >   c-ares version 1.6.0
Please reply soon!

---

### Post by SeijiSensei on 2015-05-05
First, see if your local DNS server can actually resolve external names.  Try
```
host google.com ip.addr.of.server
```
replacing "ip.addr.of.server" with the DNS server's IP address.  You should get
```

$ host google.com
google.com has address 173.194.123.5
google.com has address 173.194.123.0
google.com has address 173.194.123.1
google.com has address 173.194.123.2
google.com has address 173.194.123.9
google.com has address 173.194.123.14
google.com has address 173.194.123.8
google.com has address 173.194.123.7
google.com has address 173.194.123.6
google.com has address 173.194.123.3
google.com has address 173.194.123.4
google.com has IPv6 address 2607:f8b0:4006:80e::200e
google.com mail is handled by 20 alt1.aspmx.l.google.com.
google.com mail is handled by 40 alt3.aspmx.l.google.com.
google.com mail is handled by 50 alt4.aspmx.l.google.com.
google.com mail is handled by 10 aspmx.l.google.com.
google.com mail is handled by 30 alt2.aspmx.l.google.com.

```

If your DNS server sits behind a firewall, the firewall needs to permit UDP traffic in both directions on port 53.

Isn't the computer you're using configured to use the local DNS server by default?  Either have the router give out the local server's address in the DHCP configuration, or statically assign the IP and DNS server by following this: [https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution](https://help.ubuntu.com/lts/serverguide/network-configuration.html#name-resolution)

---


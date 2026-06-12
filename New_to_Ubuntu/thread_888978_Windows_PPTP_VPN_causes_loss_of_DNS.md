---
title: "Windows PPTP VPN causes loss of DNS"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Amorget on 2008-08-13
Hi, I am trying to use Ubuntu 8.04 x64 to VPN to my work so I can use remote desktop and to pass through to my Windows XP virtual machine for development.

However, I have run into a rather large problem:  I lose all DNS whenever I connect to the PPTP VPN.  I cannot browse the web to "new" websites, though current cached ones still work and I cannot ping by name any of the computers, except the server that I VPN into.

Here is the "hosts" section of my /etc/nsswitch.conf

```
hosts:          files mdns4_minimal wins dns mdns4
```

Looking at my /etc/resolv.conf, normally it reads like this:

```
search <domainname>.local


nameserver 192.168.0.1

```

If I connect to the VPN with the "Use Peer DNS" and "Peer DNS through Tunnel" unchecked, that file doesn't change.  However, if I do check those the resolv.conf looks like this

```
nameserver 192.168.1.1
```

Anyone have any ideas on what may be happening here?

Thanks,
Douglas

---

### Post by viciouslime on 2008-08-13
Are you sure this is a DNS issue? When I connect to my university's vpn I have similar issues, but just because the internet traffic is also being routed over the vpn. My solution was to set the vpn so that only traffic to 144.38.x.x was routed over it and everything else when through my own lan.

---

### Post by Methuselah on 2008-08-13
lol@name and avatar. :)
Sorry, I just had to comment on that 'viciouslime'

---

### Post by Amorget on 2008-08-13
> **viciouslime said:**
> Are you sure this is a DNS issue? When I connect to my university's vpn I have similar issues, but just because the internet traffic is also being routed over the vpn. My solution was to set the vpn so that only traffic to 144.38.x.x was routed over it and everything else when through my own lan.

Very interesting.  So I changed it as you suggested so only the IP addresses on the remote server where getting sent over, and it appears to be working the way I expect, sort of.

It seems to need to ping the FQDN for it to work, though, which might be a problem as if the remote computers aren't on the same domain as the remote server it doesn't resolve the computer's IP address.

---


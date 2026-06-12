---
title: "Can Connect to OpenVPN Server But No Internet Access"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by nick249 on 2016-03-11
Hi,

I've been trying to set up OpenVPN on my server running Ubuntu Server 14.04 LTS and I'm able to connect a client but cannot access the internet through the VPN.

I actually had my VPN working before, but had to reboot and I guess that reset some the firewall settings and even after looking over the other threads about this, I cannot figure out what is blocking the internet. I have to admit I fairly new to this.

One thing that I found odd while looking over one of the other posts was that when I run:

```
sudo iptables -X
```

I get:

```
iptables: Too many links
```

I'm not sure if this is related to the issue or not.

Thank you to anyone who can help!

---


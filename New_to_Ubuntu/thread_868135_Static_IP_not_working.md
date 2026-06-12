---
title: "Static IP not working"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by anlaoch on 2008-07-23
Hi.

I've changed my IP to "static" in "System/Administration/Network/Wired Connection/Properties".  ifconfig appears to confirm my changes, ie 192.168.x.x.  The problem is that sites like "whatismyip.com" and "grc.com" show my IP as 194.46.224.xxx

Can anyone tell me why this is, or how to resolve it?

Thanks in advance.

---

### Post by Xerp on 2008-07-23
That is correct. The 192.168.x.x range is a private range and you are behind NAT.

[http://www.faqs.org/rfcs/rfc1918.html](http://www.faqs.org/rfcs/rfc1918.html)
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

---

### Post by DGortze380 on 2008-07-23
> **anlaoch said:**
> Hi.

I've changed my IP to "static" in "System/Administration/Network/Wired Connection/Properties".  ifconfig appears to confirm my changes, ie 192.168.x.x.  The problem is that sites like "whatismyip.com" and "grc.com" show my IP as 194.46.224.xxx

Can anyone tell me why this is, or how to resolve it?

Thanks in advance.

You're talking about 2 different IP address. Your static IP is local to your network. whatismyip.com is showing your external ip assigned by your isp.

---

### Post by anlaoch on 2008-07-25
Sorry for dragging this up again, but am I right in thinking that it's the internal ip address that I should use in port forwarding, since the external ip address changes everytime I boot up the pc?

Thanks again.

---

### Post by Potatoj316 on 2008-07-25
Yes, you should forword ports to your internal IP

---


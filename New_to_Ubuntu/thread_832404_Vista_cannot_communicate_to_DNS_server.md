---
title: "Vista cannot communicate to DNS server?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by mashimaro on 2008-06-17
Hi,

I connected my ubuntu laptop to my windows vista pc so that my pc can receive internet through my laptop (internet connection sharing) using firestarter. Everything is configured, and dhcp works. Now the thing is, is that I can ping my dns from this the ubuntu terminal. But I can't ping the dns from Vista, and the other settings in Vista are fine. Can anyone help me resolve this issue? Thanks!

My dns ip is 192.168.0.1
When I ping from Windows:
>ping 192.168.0.1
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable

My firewall on Windows is off, so I know that is not the problem. Is there a certain step of configuration I'm missing? something to allow windows ping the DNS on my laptop? Thanks!

---

### Post by wootah on 2008-06-17
> **mashimaro said:**
> Hi,

I connected my ubuntu laptop to my windows vista pc so that my pc can receive internet through my laptop (internet connection sharing) using firestarter. Everything is configured, and dhcp works. Now the thing is, is that I can ping my dns from this the ubuntu terminal. But I can't ping the dns from Vista, and the other settings in Vista are fine. Can anyone help me resolve this issue? Thanks!

My dns ip is 192.168.0.1
When I ping from Windows:
>ping 192.168.0.1
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable
Reply from 192.168.0.253: Destination host unreachable

My firewall on Windows is off, so I know that is not the problem. Is there a certain step of configuration I'm missing? something to allow windows ping the DNS on my laptop? Thanks!

In the options for Firestart, did you allow all connections from the Vista PC to pass through?

---

### Post by mashimaro on 2008-06-17
there is no section for that, but i made the ip from my vista machine one of the accepted. i need to somehow fix the dns problem. Thanks for hte reply ;)

---

### Post by superprash2003 on 2008-06-17
right.. in firestarter you need to allow pings firstly and also allow the laptop ip to access..

---


---
title: "How to do this?"
date: 2020-05-25
forum: New to Ubuntu
---

### Post by ferfykins on 2020-05-25
So with windows there's an option to say if you're on a public or private network...  I'm wondering how i do that with ubuntu?  Make it so i'm on a public network so people on the same network cannot access my PC.  Thanks (I'm on XUbuntu). Hopefully this makes sense.     For security purposes.......

---

### Post by TheFu on 2020-05-25
**gufw** has settings like that.  Don't know if it is automatic or not. My home and office subnets are fairly unique, so blocking anything not on those subnets would be standard stuff.

Just be certain that your subnets aren't commonly used.  Don't use 192.168.0.x or 192.168.1.x or 172.16.x.x or 10.0.x.x  Don't, just don't use those subnets.

---


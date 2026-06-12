---
title: "freeradius inner-tunnel configuration"
date: 2016-09-09
forum: New to Ubuntu
---

### Post by kodrenz on 2016-09-09
Hi, am trying to set up freeradius server for wpa2. I follow freeradius beginner guide and everything went smooth,
until I didnt get the same message as author during inner-tunnel testing:

>radtest alice passme 127.0.0.1:18120 100 testing123

Actually I get only accept-accept message instead of his:

server inner-tunnel {
+- entering group authorize {...}
++[chap] returns noop
...

I also notice that I get accept-accept with all ports not only his "100"

I have default configuration.

---

### Post by kodrenz on 2016-09-09
Turns up everything is good thank you all

---


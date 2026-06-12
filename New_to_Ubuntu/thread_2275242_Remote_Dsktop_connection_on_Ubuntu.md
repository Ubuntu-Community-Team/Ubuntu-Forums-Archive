---
title: "Remote Dsktop connection on Ubuntu"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by tandeep on 2015-04-25
how many remote desptop connetion can be made into ubuntu using Windoes RDP?

---

### Post by TheFu on 2015-04-25
I wouldn't use RDP to remotely connect into Linux. It isn't secure and it is slow compared to other options.

I'd use x2go which uses ssh for transport and authentication which is probably the most secure option today. Plus the NX protocol is 2-3x more efficient than RDP for remote desktops. I don't know of any built-in limit with NX or x2go - it would depend on the server network, RAM, CPU.

---


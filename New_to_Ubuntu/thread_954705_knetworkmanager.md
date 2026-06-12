---
title: "knetworkmanager"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Obso1337 on 2008-10-21
I'll have to be brief, as my laptop could freeze at any moment. I am using knetworkmanager because it is my only option compatible with my university's wifi. However, it seems to be causing my laptop to randomly freeze after it is booted. Anyone have any idea why this may be happening?

---

### Post by cmnorton on 2008-10-23
If you enter CTRL+ALT+F1 and log in, you will accomplish two things. One, you can see if you freeze logged in that way, and two, you could examine your logs, and see if there is anything tell-tail there. /var/log/messages and /var/log/syslog would be good places to start.

What applications are running when you freeze?

---


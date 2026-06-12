---
title: "vsftpd + ssl = ECONNREFUSED when trying to login from internet"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by tibitek on 2016-10-16
Hey there,

I'm new to ubuntu and I've got a question.i've just set up vsftpd and ssl (with force ssl options enabled), but there's a problem. I've forwarded ports 20 and 21 to my machine. Logging in from local network is no problem, but when trying to do so via a VPN to some other network (for testing purposes), I only get an ECONNREFUSED error. Why is this?

---

### Post by Rocket2DMn on 2016-10-17
I believe that secure FTP uses port 22 by default.  21 is for unsecure FTP connections by default.

---


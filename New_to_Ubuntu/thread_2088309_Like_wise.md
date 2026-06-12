---
title: "Like wise"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by sajihentry on 2012-11-26
Hi,

 I installed likewise open in one of our ubuntu machine, after the i check the domain using nslookup and i got this information,

Server : 192.168.100.1
Address: 192.168.100.1#53

Name: domainname.com
Address: 192.168.100.1

But i did this same thing in another ubuntu machie,i got this

Server: 127.0.0.1
Address: 127.0.0.1#53

Name: domainname.com
Address: 192.168.100.1

 And i can't get the domain login screen.

Please help for solving this.......:)

---

### Post by JS207 on 2012-11-26
I think there is something amiss with your environment.  My suggestion is to run the free "AD Check" utility that checks issues with your environment from an Ubuntu system's perspective.  You can get it at [www.centrify.com/express]("http://www.centrify.com/express") and download the bits for Ubuntu and run the adcheck utility.  It will give you PASS / FAILS on elements of your environment and can help you debug your environment.  From there you can then either install Likewise or alternatively do an install of Centrify Express which is also a free AD integration utility.

---


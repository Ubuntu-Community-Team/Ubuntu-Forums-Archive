---
title: "Won't install anything and running really slow"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-04-29
When I try to install 7zip I get the following message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

But when I try to manually run in a terminal window I get a message saying that "requested operation requires supervisor privilages".
Also, the computer is running really slow and it took several minutes for Firefox to open.

Help

---

### Post by Leonivek on 2008-04-29
Run it with sudo (supervisor privileges):

sudo dpkg --configure -a

---

### Post by bilal.17 on 2008-04-29
requested operation requires supervisor privilages means you need to run as root which you can use by putting sudo before any command

---


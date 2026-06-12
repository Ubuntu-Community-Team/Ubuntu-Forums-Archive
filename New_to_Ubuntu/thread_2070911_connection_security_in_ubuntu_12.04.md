---
title: "connection security in ubuntu 12.04"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by ahmed elbatreek on 2012-10-14
when i show my connection information i see the image below althuogh i have a firewall on is that means anything ? :confused:

by the way i'm absolute beginner of Linux Ubuntu 

[IMG]http://www14.0zz0.com/2012/10/14/07/816314845.png[/IMG]

---

### Post by zombifier25 on 2012-10-14
The Security part in connections means whether the connection is encrypted, which is only needed for wireless networks, which can be tapped into. Wired networks don't need to be encrypted.

So you are fine.

---

### Post by ahmed elbatreek on 2012-10-14
[SIZE=3]thank you my friend 
[/SIZE]

---

### Post by Lars Noodén on 2012-10-14
On which menu did you find that connection information? 
Could it be that you are not using IPsec?

About the actual settings of your firewall, you might prefer to use REJECT instead of DENY, at least for the outgoing defaults.  It will make it faster and easier for you to detect any misconfigurations or other problems.

[http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject)

---


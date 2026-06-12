---
title: "What do I need to do to ping machines on the same router by name ?"
date: 2018-03-03
forum: New to Ubuntu
---

### Post by elpidiovaldez5 on 2018-03-03
I have several machines that I set up using lubuntu over the years.  They all use the same wifi router. Some can ping the others by name and some only by ip address.  I can't remember if I did anything to enable that or if it happened automatically.  I would like to set them all up properly so that they are aware of each other.  How do I go about this ?

---

### Post by elpidiovaldez5 on 2018-03-03
Solved it.  I needed to change a setting on the router.

Mine is a Tilgin router (but the approach is valid for other routers)  and I needed to set 'default' in:
   LAN Configuration --> View/Edit all parameters --> DHCP Server --> DNS Servers

The guide that pointed me in the right direction is:
[https://unix.stackexchange.com/questions/16890/how-to-make-a-machine-accessible-from-the-lan-using-its-hostname](https://unix.stackexchange.com/questions/16890/how-to-make-a-machine-accessible-from-the-lan-using-its-hostname)

---


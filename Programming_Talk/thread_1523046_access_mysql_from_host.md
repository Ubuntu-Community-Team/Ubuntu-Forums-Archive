---
title: "access mysql from host"
date: 2010-07-03
forum: Programming Talk
---

### Post by railsfan on 2010-07-03
Ubuntu 10.04 Guest with mysql server installed. Bridged Network.  mysql works fine within ubuntu guest.
Win XP host and using VirtualBox
Internet works fine in Guest and host.
 
How do i access mysql from win xp host?
 
Do i need a special software?
 
I have edited the mysql file my.cnf to specify bind-address as 0.0.0.0 and still no luck.
 
- thanks,
railsfan

---

### Post by Bachstelze on 2010-07-03
With Bridged Ethernet, for all networking purposes, it's just as if your virtual machine was a separate physical one, so you should be able to assess mysql from the host the same way you would access it from another machine on the network.

---


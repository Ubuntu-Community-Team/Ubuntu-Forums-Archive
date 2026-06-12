---
title: "ip monitoring"
date: 2006-10-15
forum: Programming Talk
---

### Post by chris rees on 2006-10-15
can anyone tell me if there is a program which allows u to let certian computers on to your wireless conection.but block all others](*,) [-(

---

### Post by Dimitar on 2006-10-18
well, since many ip's are dynamic i think the best way to do it would to insert mac addresses, and then set to allow only, but that all depends on what your using to make the network.. is it a wireless router?

---

### Post by amo-ej1 on 2006-10-18
instead of spreading out dhcp address you could tie the dhcp lease to a mac address, but that would only be a quick fix, in the end you'll need to filter on mac address (which is only safe up to the extent that people need to know 'a' mac address in order to connect. 
In the end you will want to use some kind of access control, e.g. wep/wpa keys.

---


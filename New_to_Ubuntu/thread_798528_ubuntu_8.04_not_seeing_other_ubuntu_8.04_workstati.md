---
title: "ubuntu 8.04 not seeing other ubuntu 8.04 workstation on the same LAN"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-18
I have 4 ubuntu workstation (all running 8.04), none of which see each other
I would like to set up a share between all 4,
In network > windows network > i have no workstation or shares

I would like to set up remote desktop viewer on the 3 workstations, in remote desktop viewer no machines appear there either!

Any help would be useful!

All machines are on the same subnet, and the address are given out on a DHCP lease!

---

### Post by shifty_powers on 2008-05-18
this is probably a really stupid question, but always good to get the simple stuff out of the way first....

you do have samba set up and running?

---

### Post by ibizatunes on 2008-05-18
I have installed the samba services
under repo's i have samba and samba-common installed
So i think so

---

### Post by shifty_powers on 2008-05-18
have a look

[http://samba.netfirms.com/](http://samba.netfirms.com/)

bit involved but may help ;)

---

### Post by ibizatunes on 2008-05-18
Fixed it by restarting the samba services, on each workstation.... 
Still cant get remote desktop viewer to work though, any ideas on there

---


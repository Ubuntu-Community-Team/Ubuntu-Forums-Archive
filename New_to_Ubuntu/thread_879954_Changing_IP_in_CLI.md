---
title: "Changing IP in CLI"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by jbailey22 on 2008-08-04
I am trying to learn how to do things in Ubuntu Server and need some help. I can't figure out how to change the IP and all the network settings in it. I had it one way during install and need to change it. Please help. Thanks.

---

### Post by Bachstelze on 2008-08-04
Modify it in /etc/network/interfaces, and do a [font="Courier New"]sudo /etc/init.d/networking restart[/font].

---

### Post by jbailey22 on 2008-08-05
Is that where i put in DNS and proxy information and whatever else or just the ip, subnet, and gateway?

---

### Post by AdamWood on 2008-08-05
DNS settings are in /etc/resolv.conf and I think proxy settings are application specific.

---


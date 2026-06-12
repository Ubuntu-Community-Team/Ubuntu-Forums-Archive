---
title: "2 mac addreses problem"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-06-01
i installed ubuntu 8.04 lasst week and I am not able to connect to internet
if config shows 1 mac address in ubuntu
n when i open the router's config page in win xp(its not opening in ubuntu) n check the mac address it shows diff address
infact win n ubuntu both 
is this creating a prob in ubuntu

---

### Post by Dedoimedo on 2008-06-01
Hello,

Try these two commands:

ifconfig /all

arp

See what you get in the output.

Cheers,
Dedoimedo

---

### Post by sayakb on 2008-06-01
To change your MAC:
```
sudo apt-get install macchanger macchanger-gtk
```
And then from terminal, run:
```
macchanger-gtk
```
If it fails to change, run this as sudo.

---


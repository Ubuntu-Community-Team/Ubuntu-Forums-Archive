---
title: "firefox disconnects"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by bemi.eliahu on 2008-10-03
hello, 
while being connected to the internet using emule and firefox, the emule keeps staying connected but firefox disconnects every few minutes - then i have to use the poff dsl-provider / pon dsl-provider in order to restart it (it will happen without the emule too, when just the firefox is on)
can anyone help on that? 
thanks

---

### Post by SupaSonic on 2008-10-03
What does 
```
plog
```
say?

---

### Post by bemi.eliahu on 2008-10-03
Hi, the plog command printed that:

bemi@bemi-desktop:~$ plog
Oct  3 12:44:07 bemi-desktop pppd[16437]: Using interface ppp0
Oct  3 12:44:07 bemi-desktop pppd[16437]: Connect: ppp0 <--> eth0
Oct  3 12:44:09 bemi-desktop pppd[16437]: PAP authentication succeeded
Oct  3 12:44:09 bemi-desktop pppd[16437]: peer from calling number 00:30:88:03:45:55 authorized
Oct  3 12:44:09 bemi-desktop pppd[16437]: replacing old default route to eth0 [10.0.0.138]
Oct  3 12:44:09 bemi-desktop pppd[16437]: Cannot determine ethernet address for proxy ARP
Oct  3 12:44:09 bemi-desktop pppd[16437]: local  IP address 87.68.98.158
Oct  3 12:44:09 bemi-desktop pppd[16437]: remote IP address 87.68.96.254
Oct  3 12:44:09 bemi-desktop pppd[16437]: primary   DNS address 80.179.52.100
Oct  3 12:44:09 bemi-desktop pppd[16437]: secondary DNS address 80.179.55.100
bemi@bemi-desktop:~$ 

does this say any thing?
thanks a lot.

---


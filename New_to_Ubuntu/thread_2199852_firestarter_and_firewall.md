---
title: "firestarter and firewall"
date: 2014-01-16
forum: New to Ubuntu
---

### Post by vfx1988 on 2014-01-16
hi i have this really weird problem with my ubuntu 64 bit setup, whenever there is a reboot all of the servers ports which should be open get closed. To fix this i have to open firestarter which auto starts and stop it then run it if i want it. It blocks synergy for me so i just leave it off. Any idea why i have to do this on every boot..? i am not very familiar with iptables but i did find an article on ubuntu which created a iptables script to allow all traffic, that seems unsafe for production use though... 

i am currently experimenting with gUFW as a firewall solution though since i cant seem to use firestarter at all... and it looks promising

Another issue that i seem to have is when ubuntu auto locks i cant login. I have to click on switch user then enter the same password again... is there anything which could be corrupt in the system..?

any advice would be appreciated

---

### Post by ajgreeny on 2014-01-16
Firestarter is now deprecated, and unless I am mistaken, it has not been developed for some long time.

My advice is to remove it completely along with all configuration setup and then get used to gufw, which is much better developed for ubuntu. You may also need to manually purge any settings you have already made with command```
sudo iptables -F
```

---

### Post by ian-weisser on 2014-01-16
> **vfx1988 said:**
> hi i have this really weird problem with my ubuntu 64 bit setup, whenever there is a reboot all of the servers ports which should be open get closed.

That doesn't happen automatically. Sometime in the past, likely a script or application was installed that is doing it...and then forgotten.
One way to resolve is to uninstall *all* your firewall configs and scripts and applications until the problem stops.
Personally, I find iptables quite easy to use directly.

 > **vfx1988 said:**
> i am not very familiar with iptables but i did find an article on ubuntu which created a iptables script to allow all traffic, that seems unsafe for production use though... 

All inbound packets heading to a non-listening or non-active port are discarded anyway. Regardless of firewall settings.
On a production system, you already *know* (by using *sudo netstat -tulp*) exactly which applications are active and/or listening on which ports. It's only unsafe if you install unsafe services, or use them in an unsafe way.

---


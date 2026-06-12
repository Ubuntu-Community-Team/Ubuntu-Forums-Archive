---
title: "software update issue"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Senrique on 2011-10-15
Hi,i'm unable to update my softwares and install any new softwares since i've installed ubuntu 11.10.
we've proxy system and i've entered appropriate proxy in /etc/apt/apt.conf.
i've entered those proxies even in system settings>network.
Still its not working....
when i typed sudo apt-get update,i got
'E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/'
and when i typed sudo apt-get install synaptic,i got this...
'Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate'

the other computers on the network,are able to use the same proxy to update their softwares.

any help?

---

### Post by wildmanne39 on 2011-10-15
Hi, did you have the terminal and software center open at the same time? 

If not restart your computer then see if the lock message goes away.
Thank you

---


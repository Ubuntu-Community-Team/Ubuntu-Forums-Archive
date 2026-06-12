---
title: "Apache Problem"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by siddhartpai on 2011-11-22
i am an absolute beginner at this . please ignore my ignorance.
i just installed apache2 on my system and i can access the "It Works" page on localhost .
Also by pointing towards my local lan ip from another system leads to the It works page.

but i can't seem to get the it works page by pointing towards my ip from the browser :( 

Why is that ??

---

### Post by satanselbow on 2011-11-22
> **siddhartpai said:**
> 

but i can't seem to get the it works page by pointing towards my ip from the browser :( 

Why is that ??


Do you mean your external IP? 

Apache installs on the local loopback interface by default and needs to be manually configured to offer external access including NAT/port forwarding on your router. You may also not be able to check your config from a machine on your local network as not all home routers support the required u-turn in routing so you would need an external machine (to your local network) to test things out with - a 3G phone would be sufficient ;)

---

### Post by siddhartpai on 2011-11-22
Yup ..the external ip ... I'm working on this from the college wifi so no chance of configuring the Router . Anyway Thanks ..

---


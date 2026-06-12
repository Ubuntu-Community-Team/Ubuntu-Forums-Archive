---
title: "Is it possible to put /var/cache/apt/archives on a usb flashdrive?"
date: 2020-06-02
forum: New to Ubuntu
---

### Post by peb-cak on 2020-06-02
Due to having data cap on my internet connection and also having three Ubuntu systems to keep updated I wondered if I coud put /var/cache/apt/archives on a partiton on a flashdrive. I could then mount the partition via an entry in fstab, do the updates in one system and move the flashdrive to other systems to be updated. Do you think this is the right way of doing so?

 I appreciate much your thoughts and suggestions.

---

### Post by TheFu on 2020-06-02
apt-cacher-ng

---

### Post by peb-cak on 2020-06-02
> **TheFu said:**
> apt-cacher-ng

Thanks for your reply and suggestion! 
I have to admit that I have never set up a network so this approach at the moment seems to be above my computing competence. I will surely look into it and see if I can make it work since this looks to be the best solution. If you know of some tutorials for setting up a network suited for newbies please let me know. I will be doing some research on my own as well. Thanks again!

---

### Post by TheFu on 2020-06-02
Use static IPs for servers and desktops.
DHCP with dynamic IPs are fine for laptops and clients that move in and out of the network.  

The system running apt-cacher-ng is a server and life will be 1000x easier if it has a static IP.

Ensure all clients can ping the apt-cacher-ng using the hostname or "{hostname}.local". That means either /etc/hosts or running a DNS server somewhere. Some better home routers can do this.

So, my apt-cacher-ng server is named "istar", so my 15-20 clients can ping it by **ping istar**.  I run an internal DNS server so all my internal systems can find each other.  Long ago, I used the simple /etc/hosts file method. For 3 systems, I'd use that.

---

### Post by peb-cak on 2020-06-02
Great! Thanks for the tips!

---


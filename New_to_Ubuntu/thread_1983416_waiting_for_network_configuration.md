---
title: "waiting for network configuration"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by tropic on 2012-05-20
I've seen other threads with the same topic but my problem is different, the threads that i referred deal with problems like ubuntu freezing at this screen, what I need is a possible fix to prevent it from waiting for network configuration when I boot up without turning on my router. 
btw it doesnt freeze for me (when router is on) as mentioned in the other threads

---

### Post by tropic on 2012-05-20
Will installing a network manager fix the problem?

In this page,
[http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time](http://askubuntu.com/questions/63456/waiting-for-network-configuration-adding-3-to-5-minutes-to-boot-time)

in the most voted answer

> The bits about eth0 meant that your machine was configured to wait for a dynamic address to be assigned to it before the netowrk is considered "UP". In pre-upstart versions of Ubuntu (8.10 and earlier), the system would have waited up to 60 seconds for this before continuing the boot. **When upstart was added, this condition wasn't waited for anymore, because network interfaces that were not always expected to be plugged in are better managed by something like network-manager.**

So, if you have a server, you probably want to wait for a dynamic address, otherwise the system will boot without all of its networks available (which it does if it takes more than 2 minutes to get an address). If you have a laptop that you don't always expect to be plugged in to eth0, then configure eth0 in network manager, and remove only those lines from /etc/network/interfaces, which should get rid of your boot delay.

---

### Post by Dave_in_MD on 2012-05-20
> **tropic said:**
> what I need is a possible fix to prevent it from waiting for network configuration when I boot up without turning on my router. 
btw it doesnt freeze for me (when router is on) as mentioned in the other threads
Set your machine for a static address and enter the assigned address as a reserved address in whatever is acting as your DHCP server.  The DHCP server could be your router, some switches or a domain server.

---


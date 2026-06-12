---
title: "Firewall???"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by malaya on 2008-05-06
- question, what firewall should i install in my hardy???
- thanks..:)

---

### Post by glennric on 2008-05-06
There is a firewall installed by default.  It is actually part of the linux kernel.  A nice gui front end to administer it is firestarter.  Type
```
sudo apt-get install firestarter
```
to install it.

---

### Post by PeterJS on 2008-05-06
There is only one firewall, IPTables, and it's intergrated in to the kernel, so you're using it wether you want to or not. The question is it configured to acutally do anything other than allow all traffic through (the default). Firestarter is a popular tool to configure and monitor IPTables.

But the question is why do you feel the need to configure IPTables? Did you install some server software above and beyond the base install that needs to be protected? are you directly connected to the internet and thus don't have a NAT/Router handling filtering at the network level for you?

Windows has conditioned people to equate firewall with security, the truth is not doing dangerous things will keep you far safer than any tool ever will.

---

### Post by malaya on 2008-05-06
> **PeterJS said:**
> There is only one firewall, IPTables, and it's intergrated in to the kernel, so you're using it wether you want to or not. The question is it configured to acutally do anything other than allow all traffic through (the default). Firestarter is a popular tool to configure and monitor IPTables.

But the question is why do you feel the need to configure IPTables? Did you install some server software above and beyond the base install that needs to be protected? are you directly connected to the internet and thus don't have a NAT/Router handling filtering at the network level for you?

Windows has conditioned people to equate firewall with security, the truth is not doing dangerous things will keep you far safer than any tool ever will.

- hmmm, i think your right. hehe thanks!

---


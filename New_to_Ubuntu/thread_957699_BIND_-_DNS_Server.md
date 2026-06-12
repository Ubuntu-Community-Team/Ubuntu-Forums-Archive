---
title: "BIND - DNS Server"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by sjaxso on 2008-10-24
Hi Guys,

Just asking for a recommendation here. 

I'm running Ubuntu 8.04 on my home network, and there are also the following:
1) XP Laptop
2) Vista Desktop
3) A PS3

It's it worth my while to setup a local DNS server? I overheard a conversation where a chap was telling his friend that he'd done just that, and browsing from the network was lightning fast.

I'm clearly quite a noob so don't want to be taking on anything supercomplex and/or unnecessary. 8-[

---

### Post by bodhi.zazen on 2008-10-24
For a small network, I would say no.

But if you wish :

[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by Iowan on 2008-10-24
Should you wish to add a DNS server, consider **dnsmasq**, which reportedly also does DHCP and ties the two together, making it easier to ping (etc) by hostname.

---


---
title: "BIND9 and DNS questions"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by roodypoo on 2012-06-03
I have 12.04 Desktop installed and would like to run a caching DNS server on this work station. I would like all DNS requests to go to OPENNIC servers instead of my ISP's. I would also like it to cache locally.

The tutorials I have seen all deal with Ubuntu Server and older versions of Ubuntu.

Can someone point me in the right direction?

EDIT:

Maybe I don't understand the process so I should explain a bit more.

I want BIND9 to handle all DNS requests coming from my desktop. I want BIND to use OPENNIC servers and cache the results. I do not want any requests going to my ISP.

---

### Post by Cheesemill on 2012-06-03
12.04 runs a caching nameserver as standard (dnsmasq).

All you need to do is go to Settings > Network > Options and enter the IP addresses of the name servers you wish to use.

---

### Post by roodypoo on 2012-06-03
> **Cheesemill said:**
> 12.04 runs a caching nameserver as standard (dnsmasq).

All you need to do is go to Settings > Network > Options and enter the IP addresses of the name servers you wish to use.

Thank you for the reply.

I wanted something that gave more options and I wanted to learn something.

Is it possible to run a locally cached BIND9 server on a desktop?

If it is, would you recommend a tutorial?

Thanks

---

### Post by sandyd on 2012-06-03
> **roodypoo said:**
> Thank you for the reply.

I wanted something that gave more options and I wanted to learn something.

Is it possible to run a locally cached BIND9 server on a desktop?

If it is, would you recommend a tutorial?

Thanks

[https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server](https://help.ubuntu.com/community/BIND9ServerHowto#Caching_Server)

---

### Post by roodypoo on 2012-06-03
Thank you.

Do I need to set up a static IP for the computer BIND9 will reside on?

I have disable dnsmasq by commenting out the line in Network Manager's config file. Should Network Manager be set up with no DNS information or should I put 127.0.0.1?

Will OpenNIC connect to the root servers automatically?

How big will a DNS cache file get?

---

### Post by sandyd on 2012-06-03
> **roodypoo said:**
> Thank you.

Do I need to set up a static IP for the computer BIND9 will reside on?
**Of course.**
I have disable dnsmasq by commenting out the line in Network Manager's config file. Should Network Manager be set up with no DNS information or should I put 127.0.0.1?
**127.0.0.1**
Will OpenNIC connect to the root servers automatically?
**no idea**
How big will a DNS cache file get?
**no idea**

I use cogent's DNS servers, so I wouldn't know.

---


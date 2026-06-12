---
title: "Bought a domain, is there an easy way to update with a dynamic IP?"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by ironic.demise on 2013-04-27
I just grabbed a domain name from lcn.com and I want to update it to the webserver I run at home.

Until now I've always just used free ddns services such as dnsdynamic.org and used their subdomains, (ironicdemise.dnsdynamic.com for example)
Now that I've bought my own domain name I've looked at services that can keep up to date with my ip, dnsomatic for example.

However, I want to know if there's a way I can get the domain name I bought point to a dynamic ip without manually updating it, I've been looking at OpenDNS and dnsomatic but these don't seem to care about my actual domain name?

Am I missing something with the nameservers?
If I change the nameservers my domain at lcn uses to the OpenDNS ones, will it then work or am I going to have to follow someof the advice on the internet I have read which says I need to continue using ironicdemise.dnsdynamic.com but just, redirect my domain around it? (using a CName record according to some of the guides.)

In other words, what is the fastest, most reliable way to point a domain name to a dynamic IP?

---

### Post by DuckHook on 2013-04-28
I use freedns, which does allow you to register your user-owned domain name with them so that you can update it using the ddns daemons on either your router or your computer. Website is [here]("http://freedns.afraid.org/").

---


---
title: "subdomains in /etc/hosts?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by freakavoid on 2008-07-22
Hi,

I'm looking for a way to assign an ip address for a site with all its subdomains (without knowing all of them). /etc/hosts doesn't allow wildcards. So something like

```
127.0.0.1 *.example.com
```

doesn't work. Any suggestions? 

Thanks in advance.

---

### Post by Xerp on 2008-07-22
You can do that with BIND

```
sudo apt-get install bind9 dnsutils
```

then

```
sudo vi /etc/bind/named.conf.local
```

and add like this:

```
zone &#8220;myexample.com&#8221; {
type master;
file &#8220;/etc/bind/zones/myexample.com.db&#8221;;
};
```

and this:

```
sudo vi /etc/bind/zones/myexample.com.db
```

```

myexample.com. IN SOA ns1.myexample.com. admin.myexample.com. (

2008230601
28800
3600
604800
38400
)

myexample.com. IN NS ns1.myexample.com.
myexample.com. IN MX 10 mail.myexample.com.

@   IN A 192.168.0.3
www IN A 192.168.0.2
ns1 IN A 192.168.0.1

```

You'll need to know a bit about DNS though :/

[http://en.wikipedia.org/wiki/Wildcard_DNS_record](http://en.wikipedia.org/wiki/Wildcard_DNS_record)

---

### Post by freakavoid on 2008-07-22
Thank you. I'm not sure if I want to set up a dns just for this task but it seems like there is no other option. Anyways thank you for the info.

---

### Post by Oldsoldier2003 on 2008-07-22
> **freakavoid said:**
> Thank you. I'm not sure if I want to set up a dns server just for this task but it seems like there is no other option. Anyways thank you for the info.

It probably is the best workaround since using a domain in hosts breaks sudo in gutsy and hardy

---

### Post by freakavoid on 2008-07-22
> **Oldsoldier2003 said:**
> It probably is the best workaround since using a domain in hosts breaks sudo in gutsy and hardy

Hmm... Actually I don't want to direct the domain name to localhost. But out of curiosity: That problem occurs only if the lines with the name of the computer are changed, right?

---

### Post by Oldsoldier2003 on 2008-07-22
> **freakavoid said:**
> Hmm... Actually I don't want to direct the domain name to localhost. But out of curiosity: That problem occurs only if the lines with the name of the computer are changed, right?
correct. it also happens a lot with upgraded ubuntu installations for some reason.

---


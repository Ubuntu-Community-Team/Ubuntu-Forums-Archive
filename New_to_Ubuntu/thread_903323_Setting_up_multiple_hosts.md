---
title: "Setting up multiple hosts"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by WolfieZero on 2008-08-28
Sorry to ask this again if it's already been answered, but nothing came up that matched what I wanted to do really.

In my Apache2 httpd.conf file I got my server set up to take the following requests

```
Listen 1111
Listen 2222

NameVirtualHost *:1111
NameVirtualHost *:2222

<VirtualHost *:2222>
DocumentRoot "/var/www/intranet"
</VirtualHost>

<VirtualHost *:*>
DocumentRoot /var/www/default
</VirtualHost>
```

So the idea here being anything coming to EXTERNALIP:1111 is directed OURSERVER then to a default virtual server. Any internal requests to OURSERVER:2222 is directed to our intranet control panel.

The overall idea being no external user can access the intranet externally.

What I want to be able to do is make is so when we type INTRANET into the browser, we are taken to the intranet site, and if we type OURSERVER then we are taken to the default site. How do I got about doing this?

Thanks in advance!

---

### Post by bitninja on 2008-08-28
Is your Ubuntu box behind a router? If so, I'd forward the intranet port to an IP on your subnet that doesn't actually exist. I *believe* that this will disallow external access to this port and allow people on your network to still access the intranet page.

---

### Post by WolfieZero on 2008-08-28
It's behind a router, yeah.

At the moment we have two servers coming off the router.

One server uses port 8888 and the one I'm configuring uses 1111.

---

### Post by DemonBob on 2008-08-28
Well it's been awhile for me.

The best way to this would be to add a virtual ip to the webserver, and using dns. 

Example. 

Normal internal IP Address for the external site is 192.168.15.5, your realworld ip address for the website is letsay 69.2.41.23, and the router sends everything coming externally to the inside address of 15.5

Virtual IP for the internal site would be 192.168.15.6

If you have a internal DNS server you then say all request for INTRANET goto 192.168.15.6, so when users in side, type [http://intranet](http://intranet) it will goto 192.168.15.6

I.E. /etc/network/interfaces reads

auto eth0
iface eth0 inet static
address 192.168.15.5
gateway 192.168.15.1
netmask 255.255.255.0
network 192.168.15.0
broadcast 192.168.15.255

to add a virtual ip you would add this below it. 

auto eth0:1
iface eth0:1 inet static
address 192.168.15.6
gateway 192.168.15.1
netmask 255.255.255.0
network 192.168.15.0
broadcast 192.168.15.255

Assuming your using a static address scheme. 

This would allow the adapter to have a second address. Then you would bind, the virtual host for the intranet to the respective address. 

It's been along while since i've done this. But i have done it before, and i know it works. But i may have missed something, so i would recommed google, "ubuntu virtual ip" or linux virtual ip.

---


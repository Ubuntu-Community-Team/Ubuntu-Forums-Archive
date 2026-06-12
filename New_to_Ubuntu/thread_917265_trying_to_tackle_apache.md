---
title: "trying to tackle apache"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by Dudeman02379 on 2008-09-11
Hi guys.  I am trying to setup apache on ubuntu server 8 to host a website, maybe more than one.  I work in computer networking so I'm not totally clueless.  I have just never hosted a webiste before and we are a microsoft shop so I only have some linux experience.  What I have done so far is install ubuntu server with lamp in a virtual machine.  I then installed webadmin as an interface.  I setup a static ip address on the server.  I then fowarded port 80 in my router.  The problem I am having is when I go to the machines ip address on my local network I can see the default "It Works!" site.  When I try to access it from the internet I do not get the page.  I do have dns setup so I can resolve the site from the internet.  When I look in my routers logs I can see that port 80 was access from the internet and fowarded.  So I think I need to do something in apache to let outside addresses access the site.  I just have no idea how!  Any help would be appreciated.  Thanks!

---

### Post by spiderbatdad on 2008-09-11
check your error logs in /var/log/apache2 for clues. Have you set a ServerName in httpd.conf?```
ServerName yourDomain.com
```

---

### Post by Dudeman02379 on 2008-09-11
> **spiderbatdad said:**
> check your error logs in /var/log/apache2 for clues. Have you set a ServerName in httpd.conf?```
ServerName yourDomain.com
```

I don't see anything in the log that looks related.  The only error I see is,

[Wed Sep 10 18:10:20 2008] [error] [client 192.168.1.203] File does not exist: /var/www/favicon.ico

I did not set any domain name in the httpd.conf file.  I realy have no experience with apache and I don't know what that file is for.  Maybe I need to do some more research before I try hosting this site.  I thought it would be straight foward with the webadmin interface.  The confusing thing is I cant access the site from outside my network by using ip address or domain name.  Inside my network ip address and server name both work.  I would think the router is setup wrong but I know that port 80 is fowarded correctly.  I've checked a million times.

EDIT:  Oh man... I feel dumb.  I forgot to set a default gateway.  The box didn't know how to route to the internet.  I could get to the internet when I first set it up because it was getting an address from my dhcp server.  DUH.  Sorry guys.  Problem solved!!!

---


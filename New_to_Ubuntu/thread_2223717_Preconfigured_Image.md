---
title: "Preconfigured Image"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by yaniv2 on 2014-05-12
Is there any image or some installation of ubuntu that come pre-configured with a web-server ?
like a one stop shop.


Thanks

---

### Post by TheFu on 2014-05-12
There are many "VM images", but not anything you can just "dd" onto a HDD.

After all, the server hardware DOES matter.  Guessing swap space, RAM, /boot, /, /var partition values will result in a sub-optimal server.  What about RAID, backups, security, ssh-keys, application logins, puppet, ansible controllers?  The list goes on and on. 

Installing any base web server is pretty trivial these days to serve static files, but that does NOT make it secure or add many of the different facilities that most people running webservers need. No php, no fast-cgi, no mod_perl, no RoR integrations, stuff like that.

During the nominal Ubuntu Server installation, you can select "LAMP" as an option. It is pretty easy, though still not secure enough, IMHO. Fine for use inside a network, just not on the internet.  15 minutes total time from boot to done.

Securing a server on the internet is highly dependent on network facilities, load balancers, reverse proxies ... things that are NOT running on the "server" itself.

After a base server install (which should always include ssh-server), adding nginx is just
**sudo apt-get install nginx** Pretty simple.  Same goes for Apache, and the others.

By the time you get the stuff you (and only you) want, it is a custom setup.  If you plan to build 20-20,000 identical servers, look into cobbler.

Hope that answers the question, but I suspect not.

---


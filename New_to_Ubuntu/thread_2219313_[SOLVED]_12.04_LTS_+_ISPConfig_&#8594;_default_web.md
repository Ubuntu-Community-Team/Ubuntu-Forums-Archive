---
title: "[SOLVED] 12.04 LTS + ISPConfig &#8594; default webpage"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by Adonosonix on 2014-04-23
Dear All,

I just installed Ubuntu server 12.04 LTS with ISPConfig. When I call the server with its URL, I get a nice webpage telling me that my server works. This page features a few divs with borders. There is some color.

Now, when I call the server by its IP address, I get something a little different. It is also a page telling me it works, but with really minimal HTML markup. The presentation looks almost like text only file.

I would like to either :

– Replace this page with something else. 
OR
– Make the server not to process the request (as if there was no web service running).

Basically, my server should serve content to users asking for it with one of the domain names I host, not by calling it with its IP address.

Thanks for your help.

---

### Post by lisati on 2014-04-24
One way might be to use [Virtual Hosts,]("https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts") where you have one configured for each domain you wish to serve, and a default page for everything else.

---

### Post by Adonosonix on 2014-04-24
Thank you for your reply. I eventually found the source of the issue.
There is a folder /var/www which contains symbolic links towards folders for each domain (e.g. example.com).
Inside this folder was a stray file /var/www/index.html which is used by default when a domainless http request is sent to the server.
Replacing this file allows me to display appropriate content or redirect the client.

---


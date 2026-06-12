---
title: "[SOLVED] website testing"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by anewguy on 2008-09-18
I have a Netgear wireless router with WPA2 and MAC address filtering turned on.  I have also been working on a simple website for some friends who are starting up a small business.  Looking through these forums and others on the net, I have done the following:

- installed lamp

- set up an account at noip

- copied the web site files into /var/www and tested via [http://localhost](http://localhost)

From what I understand, I need to turn on port forwarding on the router for port 80 and then direct them to the noip address to test their site.

I have been unable to test this on my own, and my understanding from a previous post last month is that you can't test to a noip address from within your own wireless network.

What I'd like to know is:

- is there a way to require a username/password in order for someone to access my PC via noip?

- after I turn on port forwarding for port 80 on the router, are there any additional steps I need to do?

- are there config files, etc., for incoming http access?

I would imagine this is a common place thing so I hope I've gotten everything together that I need to.

Thanks in advance!

Dave :)

---

### Post by OffAxis on 2008-09-18
> From what I understand, I need to turn on port forwarding on the router for port 80 and then direct them to the noip address to test their site.
Yes. Depending on how you have your apache config file set up, you can access the website via [http://localhost/](http://localhost/) , your internal IP address (192.168.x.x), the website name ([http://mysite.com](http://mysite.com)), or your network's WAN address (any http connection will be forwarded through port 80 to your computer).

> is there a way to require a username/password in order for someone to access my PC via noip?
You mean to view the website? Yes. Here's a decent article:
[http://www.apacheweek.com/features/userauth](http://www.apacheweek.com/features/userauth)

and here's the official docs:
[http://httpd.apache.org/docs/2.0/mod/core.html#require](http://httpd.apache.org/docs/2.0/mod/core.html#require)


> are there config files, etc., for incoming http access
You can limit traffic in the conf file (but it's usually not necessary)
[http://httpd.apache.org/docs/2.0/mod/core.html#location](http://httpd.apache.org/docs/2.0/mod/core.html#location)

> - after I turn on port forwarding for port 80 on the router, are there any additional steps I need to do?
no.

---

### Post by anewguy on 2008-09-18
I think you've provided me with everything I need to know - now it's just getting working!

Thanks!  
Dave  :)

---


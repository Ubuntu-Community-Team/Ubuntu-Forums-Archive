---
title: "Error in setting up Virtual Host"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by giles1000 on 2013-03-25
[COLOR=#000000][FONT=Arial]I am learning how to set up a virtual host. I have tried a number of tutorials such as [this]("https://www.digitalocean.com/community/articles/how-to-set-up-apache-virtual-hosts-on-ubuntu-12-04-lts") I have my DNS set to the machines IP, Apache starts without errors, but something is not right as pings are not returning and I cannot view the site. As a newbie I'm now stuck as I don't know what to try next. How do I fix the problem? [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Thanks in advance[/FONT][/COLOR]

---

### Post by Doug S on 2013-03-25
Hi and welcome to Ubuntu forums,

To start with, lets leave Apache out of it for now, and conentrate on this:> [FONT=Arial]pings are not returning[/FONT]If you ping via IP address only do you get a reply? Tell use more about your setup. Is your server behind a router, needing port forwarding? Where are you pinging from? Somewhere else on internet or from the same local area network? Is there any firewall preventing ICMP echo replies?

---


---
title: "teamspeak 3 on ubuntu web server"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2014-07-22
Hi guys
I have a ubuntu LAMP server running some drupal sites.

I decided I'd like to try running  a TS3 server from it since its always on.

I currently run a TS3 server from my windows 7 box.

I cloned my webserver and tested everything was working fine and then moved on to the TS3 setup.

I've now hit a wall. I can access the server using the LAN IP but not the WAN IP. Can't be accessed by anyone else either.

I've checked ports are open in ufw, they are, ports are forwarded in my router ok. Any ideas whats next.

---

### Post by bigmonmulgrew on 2014-07-23
Little bit of further information,
I followed the guide here
[http://blog.bobbyallen.me/2014/01/11/setting-up-teamspeak-3-on-ubuntu-server-12-04-lts/](http://blog.bobbyallen.me/2014/01/11/setting-up-teamspeak-3-on-ubuntu-server-12-04-lts/)

With the exception of placing the files in /var/www

It has occurred to me that theres a typo in his code missing one of the subdirectories but I've also noticed root is creating the files, so it appears its running as root, despite the guide saying to create a teamspeak3 user

---


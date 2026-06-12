---
title: "[SOLVED] help with squid"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by fch7227 on 2008-07-27
I am somewhat new to linux.  I have used squid before but now I am trying to build a proxy for home.  When I start squid, I keep getting "please set visable hostname".  Where in the configuration file do I set the hostname.  Thanks.

---

### Post by jamesrfla on 2008-07-27
Since your a beginner try using webmin to configure squid. I think squid is one of the options in webmin when you have it installed. Also if you just want to edit the config file go to /ect/squid/ their will be a file in their and just open it with the text editor.

---

### Post by ahmadzainul on 2008-07-29
Set visible hostname on sudo gedit /etc/squid/squid.conf. Find pharases visible_hostname and uncomment it and add your name whatever you like. such as lik this visible_hostname your name. I hope its work for you.
:popcorn:

---

### Post by iae610 on 2008-08-21
Hi, I am having a problem setting the Visible Hostname. I have no idea how. Can u show my your squid.conf file that would be great thanks.

---


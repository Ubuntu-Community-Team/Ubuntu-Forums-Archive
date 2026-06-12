---
title: "Apache help!"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by SchuchWun on 2012-02-25
Hi!

First off I would like to mention that I am NOT an ubuntu (or linux) n00b. What I am though is an apache n00b. 

I am running in a VM Ubuntu 11.10 server. I have my DNS setup with IP addresses of:
[LIST]
[*]192.168.1.121 (issued from the router, nameserver, domain1)
[*]192.168.1.122 (ip alias, domain2)
[*]192.168.1.123 (ip alias, nameserver)
[/LIST]

problem is when I go to domain2.ca i get domain1.ca but when I go to the individual IP address (internally mind you) I get what I am supposed to. Also going to anysubdomain.domain1.ca I get served domain1.ca always.

What am I doing wrong?
I will post any config files needed

---

### Post by SchuchWun on 2012-02-26
bump

---

### Post by Dangertux on 2012-02-26
Could you post either your httpd.conf or your virtualhost files. Wherever you are declaring your vhosts, this is almost certainly where the problem lies assuming you have DNS set up correctly.

Thanks.

---


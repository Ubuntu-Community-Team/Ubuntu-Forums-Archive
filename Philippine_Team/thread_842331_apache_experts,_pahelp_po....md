---
title: "apache experts, pahelp po..."
date: 2008-06-27
forum: Philippine Team
---

### Post by adredz on 2008-06-27
when i restart apache i get this:

> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98 )Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
i think this has something to do with my server name, right? should i change it? pano?

ang servername ko is "www.adred.com" which is already existing in the web.

---

### Post by adredz on 2008-06-27
never mind, just have it solved.:)

---

### Post by jeffimperial on 2008-06-27
Nice job! Pwede mo rin i-post ang solution mo para ang sunod na maka-encounter ng parehong issue ay matulungan din :)

---

### Post by adredz on 2008-06-27
i just deleted the line "Listen 443" from ports.conf.
however, restarting apache generates another problem(but i think it has nothing to with the deletion). here's what i got:

> apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

according to apache's wiki, it can be safely ignored so i just leave it as it is for now..unless someone comes up with a detailed solution.

---

### Post by suicidejack on 2008-06-27
yea i've been getting the same warning for some time now. i can't seem to fix or find anyone who knows but it hasn't affected anything so i've just been ignoring it too

---

### Post by jmazaredo on 2008-06-28
i think need lang mag lagay sa httpd.conf nang fqdn. o kya subdomain na name.

---

### Post by daxumaming on 2008-06-28
er... append
```
ServerName www.adred.com
```
to /etc/apache2/apache2.conf

---

### Post by adredz on 2008-06-29
> **daxumaming said:**
> er... append
```
ServerName www.adred.com
```
to /etc/apache2/apache2.conf

strike 2, thanks!:)

---


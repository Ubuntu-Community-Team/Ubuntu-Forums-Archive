---
title: "server not found for only one website"
date: 2013-04-10
forum: New to Ubuntu
---

### Post by badabec on 2013-04-10
Hello, ububtu 12.04 clean install. Firefox browser. Ethernet connection. All bookmarks and searches display ok except for one, for which I get server cannot be found. The same applies to my wife's laptop running wirelessly on Windows 7 and Internet Explorer. The errant website will display on my friend's computer (Windows 8) on his own network. Website is [www.smartsnipe.com](www.smartsnipe.com). It always loaded until two weeks ago. I once got it back by deleting it from my old, imported favourites and from ubuntu's bookmarks. Now it goes straight to server cannot be found.

Any ideas?

Thanks

---

### Post by SeijiSensei on 2013-04-10
They have a DNS problem.  The server that is reported as authoritative for the domain smartsnipe.com is ns.4wtech.com, but that server reports no DNS entries for the domain.  A "whois smartsnipe.com" query brings up four other DNS servers that do return results.  Here's one of them:
```

# host www.smartsnipe.com dns1.nettica.com
Using domain server:
Name: dns1.nettica.com
Address: 64.94.136.11#53
Aliases:

www.smartsnipe.com has address 66.23.235.140

```

Try editing your /etc/hosts file and creating an entry like
```
66.23.235.140 www.smartsnipe.com
```
then try again.  If that works, you can [add an equivalent record to your wife machine]("http://en.wikipedia.org/wiki/Hosts_%28file%29").

---

### Post by badabec on 2013-04-11
Hello, thank you for the information. I am at the very beginning of using the terminal, how do I do it?

---

### Post by gordintoronto on 2013-04-12
It appears that the problems might go beyond DNS issues:
[http://www.webretailer.com/profiles/smartsnipe.asp](http://www.webretailer.com/profiles/smartsnipe.asp)

---


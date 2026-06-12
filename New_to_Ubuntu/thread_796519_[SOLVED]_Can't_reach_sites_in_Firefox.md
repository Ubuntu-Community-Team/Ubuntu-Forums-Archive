---
title: "[SOLVED] Can't reach sites in Firefox"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Melindrea on 2008-05-16
I very recently installed Ubuntu, but I've reached a fairly odd problem: I can't access URLs. If I use the IP-address, I can reach it (though it's sometimes slow), but not the URLs.

nslookup works with both IP-address and URL, and I can reach other computers on the network.

Any suggestions on what I need to do? (I need to reinstall the computer I'm on, and if I get things to work, this one will be getting Ubuntu too)

---

### Post by CloudFX on 2008-05-16
That's a very odd problem.  Try using Opera, and see if that changes anything.

---

### Post by Melindrea on 2008-05-16
Is Opera preinstalled, or can I reach it some other way (apart from downloading it)?

---

### Post by CloudFX on 2008-05-16
Go to Add/Remove... and search for Opera.  See this page for help on adding applications:  [https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by Melindrea on 2008-05-16
"Opera cannot be installed on your computer type(amd64). Either the application requires special hardware features or the vendor decided to not support your computer type." The same for Epiphany.

Edited to add: Don't think it's Firefox's problem. I can't connect to telnet using discworld.atuion.net, but I can using the IP-address.

---

### Post by Golem XIV on 2008-05-16
If nslookup didn't work either, I'd say you have a problem with your DNS server.  Maybe a proxy problem? (Edit -> Preferences -> Advanced -> Settings button)

Check the DNS settings anyway, nslookup may be reading the cache.  Good luck.

---

### Post by Melindrea on 2008-05-16
I can't recall how/(why? =) I set the DNS-server, but removing the set one and adding the DNS mentioned in my router solved the problem.

---


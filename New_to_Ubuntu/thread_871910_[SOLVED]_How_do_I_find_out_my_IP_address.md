---
title: "[SOLVED] How do I find out my IP address?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Deedlit on 2008-07-27
How would I find out my IP address. The router says I am not on the internet, yet I get online. We are trying to set up the network and printer between my linux and a Mac. Please help me find my IP address.

---

### Post by TomSharp on 2008-07-27
Open up a terminal and type 'ifconfig' Your IP will be listed under 'inet addr:' (probably next to 'eth0').

---

### Post by Ryadt on 2008-07-27
type in terminal```
ifconfig
```

---

### Post by stevoo on 2008-07-27
ifconfig 
or
iwconfig 
for some more wirelles info

---

### Post by Deedlit on 2008-07-27
Thank you, that wasn't in the book I'm using and I was lost.

---

### Post by gjoellee on 2008-07-27
this website does also show your IP address [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

---

### Post by drubin on 2008-08-05
> **gjoellee said:**
> this website does also show your IP address [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

That website only shows your external ip address, Not your computers IP address if you are behind a router/firewall.

**edit** This was a week old, not a clue how i got to it.. but those were by 2cents any way

---


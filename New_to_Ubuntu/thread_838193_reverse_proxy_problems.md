---
title: "reverse proxy problems"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Jesus-Ninja on 2008-06-23
OK, I'm new to Linux and Ubuntu, but perhaps this isn;t a beginners question...

I've set up an ubuntu system as my single point of entry to my LAN from outside. It will field incoming http requests, and either serve the pages itself, or reverse proxy pages from other servers on the LAN.

I'm using the reverse proxying in Apache:

        ProxyPass /nas/ [http://nas](http://nas)
        ProxyPassReverse /nas/ [http://nas](http://nas)

so that I can access the web interfaceof my NAS (served on the LAN at [http://nas](http://nas), as this strikes me as being slightly more graceful than VNCing into my Ubuntu box, and then browsing it from there (a bit clunky)

When I go to [http://mydomain/nas/](http://mydomain/nas/)

> Forbidden
You don't have permission to access /nas/ on this server

, although I can view [http://nas](http://nas) *from* the Ubuntu box, and [http://mydomain](http://mydomain) on it's own returns the default "It works" page from Apache.

---

### Post by Jesus-Ninja on 2008-06-23
fixed it. Doh! I hadn't set "allow access from all" in proxy.conf

---


---
title: "[SOLVED] Proxy server for aptitude, apt-get, synaptics, etc"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-15
Okay, so I'm testing out some equipment for work, but the company I work at uses a proxy server.  And it works fine in ubuntu because of the auto-detect option.

How do I figure out the IP or address of the proxy server on our network?  If firefox is autodetecting it, does it store the value anywhere that I can get to?  I need the address so I can get wget to work in synaptics so I can download some server packages from the repositories.

---

### Post by Trail on 2008-05-15
You could try ```

netstat -tp
```
and see where firefox connects to (foreign address).

---

### Post by cwgatling on 2008-05-15
If you do a traceroute to a website, the first hop should be your web proxy. E.g. traceroute [www.google.com](www.google.com)

---

### Post by CryptiniteDemon on 2008-05-15
Hah, nevermind.  I can't believe I didn't see it.  When firefox prompts me for my proxy password it lists the address of the server in the dialog box.  

Thanks though.

---


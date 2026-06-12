---
title: "[SOLVED] Apache stopped working"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by bertwagner on 2008-08-15
I had apache running flawlessly on my computer for a few weeks now.  Over the weekend I had to reset my modem and router and since then I can't reach my apache server from a browser.  I checked my ip address as well as my local ip address and neither of them changed due to the reset.  Also, I made sure the correct ports are open and forwarded.  I am able to view my /var/www directory at [http://localhost:3789](http://localhost:3789), however I can not view it from [http://myIpAddress:3789](http://myIpAddress:3789).  Can anyone shed some light as to what I am doing wrong and if this is an apache configuration or a port forwarding issue?  Thank you.

---

### Post by cariboo on 2008-08-15
Check [canyouseeme]("http://www.canyouseeme.org/") to see if your port is really open to the internet on your router.

Jim

---

### Post by bertwagner on 2008-08-15
> **cariboo907 said:**
> Check [canyouseeme]("http://www.canyouseeme.org/") to see if your port is really open to the internet on your router.

Jim

Thanks it was a simple router error!

---


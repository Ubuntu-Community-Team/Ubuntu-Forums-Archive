---
title: "Got Ip address,unable to acess internet"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by RaviK0198 on 2012-09-05
I am having a very strange problem.I am able to connect to wireless acesspoint and also get IP address but when i am unable to browse or ping to external sites.

---

### Post by The Cog on 2012-09-05
This could be a routing or a DNS issue. Can you post the output from these commands:
```
route -n
cat /etc/resolv.conf
ping [www.google.com](www.google.com)
```

---


---
title: "how to figure out router's IP"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by adobrakic on 2008-10-07
How do I figure out what my router's IP is? I want to configure it in firefox, and I need it's IP to do that.

any help? :)

---

### Post by jay019 on 2008-10-07
If you are already connected to the router then it should appear in Network Settings under default gateway. Alternatively you could try some of the defaults like 192.168.1.1 or 192.168.1.254 etc.

---

### Post by iaculallad on 2008-10-07
> **adobrakic said:**
> How do I figure out what my router's IP is? I want to configure it in firefox, and I need it's IP to do that.

any help? :)

Drop to your terminal and issue the command below:

```
netstat -rn
```

and look at the gateway column.

---


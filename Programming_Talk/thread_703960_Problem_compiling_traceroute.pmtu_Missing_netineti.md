---
title: "Problem compiling traceroute.pmtu: Missing netinet/ip_var.h"
date: 2008-02-21
forum: Programming Talk
---

### Post by hvtuananh on 2008-02-21
When compiling traceroute.pmtu from Richard Steven book (TCP/IP Illustrated) i get an error: Could not find netinet/ip_var.h
Can i get this header file?

---

### Post by ghostdog74 on 2008-02-21
try searching for it in your system first
```

find / -type f -name "ip_var.h"

```

---

### Post by hvtuananh on 2008-02-21
It not found on my system: Ubuntu 7.10

---

### Post by ludakot on 2008-04-21
Sorry for bumping kinda old topic, but I was just looking for the package where ip_var.h is included and found it in libnewlib-headers. Thought some people would like to know.

---

### Post by hvtuananh on 2008-04-21
> **ludakot said:**
> Sorry for bumping kinda old topic, but I was just looking for the package where ip_var.h is included and found it in libnewlib-headers. Thought some people would like to know.
Thanks! I will try

---


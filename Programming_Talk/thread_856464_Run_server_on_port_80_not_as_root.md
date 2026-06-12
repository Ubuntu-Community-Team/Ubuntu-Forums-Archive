---
title: "Run server on port 80 not as root"
date: 2008-07-11
forum: Programming Talk
---

### Post by xlinuks on 2008-07-11
Hi,
To run a server on port 80 one has to be a root user, so, the server must run as root, how do you think guys, is this the only way to run the server on this port?
One of the reasons I need it, is that if someone out there manages to get my server to execute some code - it can do damages system wide since the server runs as root.

---

### Post by siouzi on 2008-07-11
You need to **start** the server as root, then **switch to another user** when running the server.

---

### Post by tamoneya on 2008-07-11
i believe the server itself typically runs under the user www-data.  It just needs to be started via a root command since it is a system service.

---

### Post by xlinuks on 2008-07-11
> **siouzi said:**
> You need to **start** the server as root, then **switch to another user** when running the server.

Switch the **server** to another user? If so - how could I do it?

---

### Post by tamoneya on 2008-07-11
i believe it does it automatically.  It switches to www-data after it has been started via sudo.

---


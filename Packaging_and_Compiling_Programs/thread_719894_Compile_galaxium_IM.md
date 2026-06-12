---
title: "Compile galaxium IM"
date: 2008-03-09
forum: Packaging and Compiling Programs
---

### Post by Joe_Bishop on 2008-03-09
I have checked out the latest galaxium IM (now it supports XMPP, MSN and AIM protocols), then try to compile it with ./autogen.sh
It asked me  about missing mono package, at least 1.2.3 version. Then I installed one from the repo, v1.2.4. But it continue to give this error:
```
checking for MONO... no
configure: error: Please install mono version 1.2.3 or later to install Galaxium.

```

---

### Post by burty89 on 2008-03-09
You need to install libmono-dev.

---


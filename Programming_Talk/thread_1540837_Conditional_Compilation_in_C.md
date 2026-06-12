---
title: "Conditional Compilation in C"
date: 2010-07-28
forum: Programming Talk
---

### Post by naugiedoggie on 2010-07-28
Hello,

I have inherited the role of "maintainer" for an Apache module written by my company for a client.  This module was written for the 2.0 line, but now the client is moving to 2.2.  The APR API for 2.2 is not backward compatible.

To make a single codebase compile for both 2.0 and 2.2, I am introducing defines based on APR version.

```
#if APR_MAJOR_VERSION == 0 /* APR for httpd version 2.0.x */
#define ap_regex_t regex_t
/* and so forth */
#endif
```

2.2 code uses ap_regex_t and 2.0 code uses regex_t.  This works in the sense that the module compiles under both version lines.  I haven't reached the runtime testing stage yet.

My question is, Is this really a good approach?  I have not done any C programming for many years, having switched to Java; I don't know what kind of poop I might be stepping in, here.

Thanks.

mp

---


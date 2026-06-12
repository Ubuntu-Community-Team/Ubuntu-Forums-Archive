---
title: "&quot;grep: The -P option is not supported&quot;"
date: 2007-05-17
forum: Programming Talk
---

### Post by diamantis13 on 2007-05-17
When I try to use regular expressions with grep I get the message "grep: The -P option is not supported". I am using Ubuntu 6.10. I  downloaded grep source compiled and installed, but I again have the same problem. Has anybody encountered something similar??

---

### Post by heimo on 2007-05-17
> **diamantis13 said:**
> When I try to use regular expressions with grep I get the message "grep: The -P option is not supported". I am using Ubuntu 6.10. I  downloaded grep source compiled and installed, but I again have the same problem. Has anybody encountered something similar??

Confirmed bug
[https://launchpad.net/ubuntu/+source/grep/+bug/15051](https://launchpad.net/ubuntu/+source/grep/+bug/15051)

Basic (-G) and extended (-E) regular expressions do work.

---


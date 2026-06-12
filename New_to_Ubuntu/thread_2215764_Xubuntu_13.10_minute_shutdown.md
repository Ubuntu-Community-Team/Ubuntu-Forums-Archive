---
title: "Xubuntu 13.10 minute shutdown"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by maciej-bak-85 on 2014-04-08
Hi,

what I should check and where ( logs etc ) what causes problem that my system takes 1 minute to shutdown ?

Thanks

---

### Post by slickymaster on 2014-04-10
For complete logs look at **/var/log/syslog**, which logs everything except auth related messages, and **/var/log/auth.log**
**/var/log/kern.log** contains kernel log messages.

---


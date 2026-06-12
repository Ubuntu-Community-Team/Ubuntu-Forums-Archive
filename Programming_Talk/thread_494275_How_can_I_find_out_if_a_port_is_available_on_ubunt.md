---
title: "How can I find out if a port is available on ubuntu programmatically?"
date: 2007-07-06
forum: Programming Talk
---

### Post by yinglcs2 on 2007-07-06
Hi,

How can I find out if a port is available on ubuntu programmatically  in c/c++?

Thank you.

---

### Post by Mr. C. on 2007-07-06
Is your goal to use the port, or just interrogate the system for which ports are currently in use?

MrC

---

### Post by steve.horsley on 2007-07-07
The easy way is to try and open the port, and see if you get an address-in-use error. You could probably find a pseudo-file in /proc/sys/net... that tells you.

---


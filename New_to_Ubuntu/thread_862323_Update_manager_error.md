---
title: "Update manager error"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by jimmygreen99 on 2008-07-17
Okay, I am using Ubuntu 8.04.1, and I went to use the update manager, and I downloaded the updates fine but they didn't install because my computer locked up for like 20 mins (to the point even my clock was not working) so I had to do a hard reboot.  Now when I go to use the update manager, I click install updates and this error comes up:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Can someone please help me with this?

Thanks :)

---

### Post by avtolle on 2008-07-17
From the CLI (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

---

### Post by jimmygreen99 on 2008-07-17
Setting up evolution-data-server-common (2.22.3-0ubuntu1) ...
Setting up libegroupwise1.2-13 (2.22.3-0ubuntu1) ...

Setting up libgdata1.2-1 (2.22.3-0ubuntu1) ...

Setting up libedataserver1.2-9 (2.22.3-0ubuntu1) ...

Setting up libcamel1.2-11 (2.22.3-0ubuntu1) ...

Setting up libgdata-google1.2-1 (2.22.3-0ubuntu1) ...

Setting up libecal1.2-7 (2.22.3-0ubuntu1) ...

Setting up libebook1.2-9 (2.22.3-0ubuntu1) ...

Setting up libedata-book1.2-2 (2.22.3-0ubuntu1) ...

Setting up libedata-cal1.2-6 (2.22.3-0ubuntu1) ...

Setting up evolution-data-server (2.22.3-0ubuntu1) ...
dpkg: error processing evolution (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 evolution

---

### Post by phantomjoker on 2008-07-17
**im not sure** - someone else _check_ if this is right but 

> sudo -get --configure 

i think should reinstall your --configure package

someone else check this _please_

---

### Post by jimmygreen99 on 2008-07-17
Dunno what i did but it's fixed, thanks guys!

---


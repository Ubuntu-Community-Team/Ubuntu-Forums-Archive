---
title: "Fix for /etc/ld.so.conf.d"
date: 2007-05-08
forum: Programming Talk
---

### Post by lawrencem on 2007-05-08
In /etc/ld.so.conf, the first line is:

include /etc/ld.so.conf.d/*.conf

If you look into /etc/ld.so.conf.d, you find the file:

i486-linux-gnu

It won't be used, because the filename doesn't end in .conf.

I renamed it to i486-linux-gnu.conf and also added a file local.conf which contains
/usr/local/lib

Is this the correct forum to have this patched?  If not, how do I notify the Ubuntu developers?

---


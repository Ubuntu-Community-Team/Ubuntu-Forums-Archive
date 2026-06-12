---
title: "ldconfig can't find libdnet.1"
date: 2011-03-11
forum: Programming Talk
---

### Post by directedition on 2011-03-11
Hello,

I have built snort and when I try to run it, it can't find the library libdnet.1. It resides in /usr/local/lib, which is included explicitly in /etc/ld.so.conf. If I do 'sudo ldconfig -v | grep libdnet', I get no results. If I copy the library to /usr/lib, then it can find it no problem (and complains about another lib which is in local that it can't find). I suppose I could copy everything into /usr/lib, but I was hoping to take advantage of the separation /usr/local/lib gives me.

---


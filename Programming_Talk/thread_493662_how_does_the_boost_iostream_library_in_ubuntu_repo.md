---
title: "how does the boost iostream library in ubuntu repository get compiled"
date: 2007-07-06
forum: Programming Talk
---

### Post by yinglcs2 on 2007-07-06
Hi,

Can you please tell me how does the boost iostream library in ubuntu repository get compiled?
Does it enable the zlib, bzip2 compression described in the documentation?  

[http://boost.org/libs/iostreams/doc/index.html](http://boost.org/libs/iostreams/doc/index.html)

Thank you.

---

### Post by PaulFr on 2007-07-06
Have you looked at **[http://packages.ubuntu.com/feisty/libs/libboost-iostreams1.33.1](http://packages.ubuntu.com/feisty/libs/libboost-iostreams1.33.1)** where it indicates the library depends on both zlib1g and libbz2 ? You can also check the Debian changelog link at the bottom of that page which indicates when this dependency was introduced.

---


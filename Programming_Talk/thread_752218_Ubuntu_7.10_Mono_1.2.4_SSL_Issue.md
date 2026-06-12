---
title: "Ubuntu 7.10 Mono 1.2.4 SSL Issue"
date: 2008-04-11
forum: Programming Talk
---

### Post by BhRaviKiran on 2008-04-11
I have installed mono 1.2.4 from source on the Ubuntu 7.10 desktop edition. I have all packages installed except the libssl.so and libcrypto.so which are necessary for SSL communication. These are supposed to be found in /usr/lib and are missing after installation. 

I retried building the libssl source files and compiled but still i couldn't get the libssl.so installed. But there is a file by name libssl.so.0.9.8 getting installed. What kind of relation exists between libssl.so.0.9.8 and libssl.so.

Thanks in advance.

Regards,
B. Ravi Kiran.

---

### Post by PartickThistle on 2008-04-11
It's normally just a symbolic link.

---


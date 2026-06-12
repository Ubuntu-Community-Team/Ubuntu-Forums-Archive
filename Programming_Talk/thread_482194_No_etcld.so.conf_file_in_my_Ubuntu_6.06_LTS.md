---
title: "No /etc/ld.so.conf file in my Ubuntu 6.06 LTS"
date: 2007-06-23
forum: Programming Talk
---

### Post by HerrWu on 2007-06-23
I've just installed a free Library in my Ubuntu 6.06 LTS, and I need to modify the file /etc/ld.so.sonf to use it. But I've found that in my system this file does not exist at all. What should I do?

---

### Post by volanin on 2007-06-23
Just create this file and inside it put just a single line containing the PATH to your newly installed library.
After that, run *ldconfig* as root.

The libraries in the PATH you added should now be searched by default, in case a program needs them.

---

### Post by HerrWu on 2007-06-24
Thank you very much! I've successfully configured the library. Vielen Dank!

---


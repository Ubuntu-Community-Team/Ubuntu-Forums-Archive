---
title: "How do I get the Unix C/C++ Man pages?"
date: 2007-04-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-04-21
I want man entries for ANSI C / STL C++ libraries such as this:

[http://www.rt.com/man/memcpy.3.html](http://www.rt.com/man/memcpy.3.html)

Where do I get these for Ubuntu?

---

### Post by rjack on 2007-04-21
sudo apt-get install [manpages-dev]("http://packages.ubuntu.com/feisty/doc/manpages-dev") [glibc-doc]("http://packages.ubuntu.com/feisty/doc/glibc-doc")

---

### Post by amo-ej1 on 2007-04-22
But there are no manpages available for the C++ STL, you'll have to rely on the libstdc++ api docs for that one e.g. available here: [http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/](http://gcc.gnu.org/onlinedocs/libstdc++/latest-doxygen/)

---

### Post by aitjcize on 2010-07-06
Try this:
[http://github.com/Aitjcize/manpages-cpp](http://github.com/Aitjcize/manpages-cpp)

PPA: [https://launchpad.net/~aitjcize/+archive/manpages-cpp](https://launchpad.net/~aitjcize/+archive/manpages-cpp)

---


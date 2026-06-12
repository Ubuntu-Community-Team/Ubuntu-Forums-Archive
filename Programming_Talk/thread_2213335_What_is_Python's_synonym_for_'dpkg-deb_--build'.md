---
title: "What is Python's synonym for 'dpkg-deb --build'?"
date: 2014-03-26
forum: Programming Talk
---

### Post by Artif on 2014-03-26
.

---

### Post by TheFu on 2014-03-26
So, what's the answer?  Py-somthing?

---

### Post by Artif on 2014-04-04
I had a look on DAK - Debian Archive Kit - [https://wiki.debian.org/HowToSetupADebianRepository#dak_.28Debian_Archive_Kit.29](https://wiki.debian.org/HowToSetupADebianRepository#dak_.28Debian_Archive_Kit.29)  They have direct shell commands calls. That solved the question.  In such the case it is not evident what is a better way - try to implement Python and C bindings, if there is any C library at all. Or use shell utilities calls. In both cases there are out of Python bounds. Shell calls seems to be implemented with less handcraft, seems to be easier to maintain (less dependencies), their "API" may be much more stable.

---


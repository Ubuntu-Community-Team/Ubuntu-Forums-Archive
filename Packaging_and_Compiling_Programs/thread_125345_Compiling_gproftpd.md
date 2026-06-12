---
title: "Compiling gproftpd"
date: 2006-02-03
forum: Packaging and Compiling Programs
---

### Post by Freddie on 2006-02-03
I use proftpd as my ftp server and like a good-looking administration application for it. On my other systems I have been using gproftpd with great success. However, I could not find it in the ubuntu repositories so (since I am a PPC user) decided to compile it from source. I downloaded the tarball and typed in:
```

./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --sbindir=/usr

```
And half way though I got the following error message:
```

checking for gtk+-2.0 >= 1.3.13... Package gtk+-2.0 was not found in the package-config search path [...]

```
What do I need to do? Am I without these libraries or do I have them but they are not in my package search path?
Thanks for all of your help.

---


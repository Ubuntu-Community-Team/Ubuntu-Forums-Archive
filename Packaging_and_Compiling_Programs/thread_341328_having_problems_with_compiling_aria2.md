---
title: "having problems with compiling aria2"
date: 2007-01-18
forum: Packaging and Compiling Programs
---

### Post by neomi on 2007-01-18
I want to compiling aria2 with openssl, but when I configure, it gave me an error which complained about that gnutls cannot be found

However, the offical website writes that you can use openssl instead of gnutls

my openssl version is 0.9.8d compiling directly from the offical source file

why? should I need openssl-devel or something like that?

---

### Post by compuguy1088 on 2007-03-25
> **neomi said:**
> I want to compiling aria2 with openssl, but when I configure, it gave me an error which complained about that gnutls cannot be found

However, the offical website writes that you can use openssl instead of gnutls

my openssl version is 0.9.8d compiling directly from the offical source file

why? should I need openssl-devel or something like that?
I previously compiled aria2, version 0.8.1 fine, and made a package with checkpackage. I would suggest to use prevu and backport aria2 from Feisty, which may be easier than building it from source, just a thought.

---


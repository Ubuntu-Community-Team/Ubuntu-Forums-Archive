---
title: "Cannot compile alpine under 11.10"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cpbl on 2011-10-03
Sigh.. This is a battered old topic, but I rely heavily on a mail client called alpine (or (re)(al)pine) and a patch (whose author refuses to put a GNU license on it) that allows it to work with the maildir folder format. (e.g., see [http://cpbl.wordpress.com/2009/11/07/alpine-offlineimap-and-gmail-under-ubuntu/](http://cpbl.wordpress.com/2009/11/07/alpine-offlineimap-and-gmail-under-ubuntu/) )

I have been able to recompile it (according to  instructions at above link) until 11.10, under which my old binary fails:


```
alpine: error while loading shared libraries: libcrypto.so.0.9.8: cannot open shared object file: No such file or directory
```

or, if I link that file in to /usr/lib, I get instead:

```
alpine: error while loading shared libraries: libcrypto.so.0.9.8: wrong ELF class: ELFCLASS32

```

Has anyone got any version of (re)alpine working with the maildir patch?

---


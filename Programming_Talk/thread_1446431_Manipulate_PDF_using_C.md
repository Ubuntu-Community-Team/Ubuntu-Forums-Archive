---
title: "Manipulate PDF using C"
date: 2010-04-04
forum: Programming Talk
---

### Post by tanyeun on 2010-04-04
hi guys,

I want to write a project that can manipulate PDF using C
I couldn't find any resources talking about it
so far
I only find support using Perl and Java(Via iText)

any ideas?

thx,

David

---

### Post by km0r3 on 2010-04-04
Hi tanyeun,

Have you already read about [Haru Free]("http://libharu.sourceforge.net/index.html")?

Maybe you would like to take a look at [PoDoFo]("http://podofo.sourceforge.net/about.html"), too, though it is a C++ library, I think writing a wrapper won't be all too difficult.

---

### Post by nvteighen on 2010-04-04
> **tanyeun said:**
> hi guys,

I want to write a project that can manipulate PDF using C
I couldn't find any resources talking about it
so far
I only find support using Perl and Java(Via iText)

any ideas?

thx,

David

GNUpdf. It's in Debian's repos, so it should probably be in Ubuntu's as well (install package libgnupdf-dev). Also take a look at the project's webpage [http://www.gnupdf.org/](http://www.gnupdf.org/)

---


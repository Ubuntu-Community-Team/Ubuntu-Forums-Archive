---
title: "no libiconv, nor 'man 3 iconv', even though iconv.h is present - why?"
date: 2007-08-19
forum: Programming Talk
---

### Post by jf/ on 2007-08-19
i'm just wondering, is this a lack of some documentation? There's no 'libiconv' package that can be found in the repositories, and 'man 3 iconv' shows nothing ('man 1 iconv' doesn't count). I'm not too sure about the intricacies of it, but i'm assuming here that if iconv.h is present, that there should be an implementation of 'iconv()' somewhere? in which case 'man 3 iconv' should really be present?

---

### Post by lloyd_b on 2007-08-19
> **jf/ said:**
> i'm just wondering, is this a lack of some documentation? There's no 'libiconv' package that can be found in the repositories, and 'man 3 iconv' shows nothing ('man 1 iconv' doesn't count). I'm not too sure about the intricacies of it, but i'm assuming here that if iconv.h is present, that there should be an implementation of 'iconv()' somewhere? in which case 'man 3 iconv' should really be present?

Try installing the package "manpages-dev" - it contains most of the man(2) (System calls) and man(3) (Library calls) man pages.

Why it's not installed as part of "build-essential" I'll never understand...

Lloyd B.

---

### Post by jf/ on 2007-08-19
> **lloyd_b said:**
> Try installing the package "manpages-dev" - it contains most of the man(2) (System calls) and man(3) (Library calls) man pages.

Why it's not installed as part of "build-essential" I'll never understand...

Lloyd B.
ah!!! ok, thanks.... I didn't even know that u have to install man pages!!! (or rather, why it's not installed by default)

---


---
title: "Error compiling Firefox"
date: 2005-05-12
forum: Programming Talk
---

### Post by shakin on 2005-05-12
I plan to make a deb of Firefox 1.0.4, but get this compile error:

```

/usr/include/bits/mathinline.h:536: error: ISO C++ forbids omitting the middle term of a ?: expression

```

Google searches indicate it might be a GCC or glibc bug, but obviously this code can be compiled by other people so maybe there's a workaround.

Actually, I also wanted to compile a qt version for the friendly kubuntu users, but got an error saying it's not a valid toolkit. I'm not overly concerned about getting qt working, but it would be nice.

Thanks.

---

### Post by shakin on 2005-05-12
I figured it out.

The error occurs only with the -ffast-math optimization set. I should never have set it to begin with, but I copied some .mozconfig settings from some guy's blog... *bad* idea. All is good now and Firefox appears to be compiling properly.

It also appears as though qt support was removed when the maintainer abandoned the project. That's too bad because even an old and slightly buggy qt build would be nice for KDE users.

---


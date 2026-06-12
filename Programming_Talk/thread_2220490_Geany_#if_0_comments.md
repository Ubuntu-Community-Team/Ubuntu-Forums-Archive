---
title: "Geany #if 0 comments"
date: 2014-04-28
forum: Programming Talk
---

### Post by spjackson on 2014-04-28
I'm talking about C/C++. In addition to the standard language comment features of /* */ and //, there is a third common idiom for "commenting out" sections of code:
```

#if 0
    commented_out_code();
#endif

```
Some syntax highlighters (e.g. vim) recognise this idiom and display the section as comment. Does anyone know how to configure Geany to treat #if 0 ... #endif as a comment?

---

### Post by spjackson on 2014-05-06
As this feature is on the [Geany Plugin Wishlist]("http://www.geany.org/Support/PluginWishlist") I am guessing that it isn't something that a user can currently configure.

---


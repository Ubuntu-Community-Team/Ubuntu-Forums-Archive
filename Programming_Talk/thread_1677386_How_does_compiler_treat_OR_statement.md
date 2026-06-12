---
title: "How does compiler treat OR statement"
date: 2011-01-28
forum: Programming Talk
---

### Post by akvino on 2011-01-28
Imagine you have if( condition == a || condition == b) statement.

How does compiler treat the statement:
1) Does it search for condition a and if true omits condition b?
2) Does it search for both a and b regardless?

---

### Post by schauerlich on 2011-01-28
Different languages treat it differently, but most use a C-style "short circuiting" operator - that is, it will only evaluate as many expressions as necessary to determine the overall value. For OR, this means that every expression will be evaluated until one of them is true; for AND, this means every expression will be evaluated until one of them is false. See [here](http://en.wikipedia.org/wiki/Short-circuit_evaluation) for more.

---

### Post by akvino on 2011-01-28
> **schauerlich said:**
> Different languages treat it differently, but most use a C-style "short circuiting" operator - that is, it will only evaluate as many expressions as necessary to determine the overall value. For OR, this means that every expression will be evaluated until one of them is true; for AND, this means every expression will be evaluated until one of them is false. See [here](http://en.wikipedia.org/wiki/Short-circuit_evaluation) for more.

I meant to write c++ compilers - but you already answered it.... Thanks for the answer :popcorn:.

---


---
title: "What lisp is most suitable for actual applications"
date: 2010-12-29
forum: Programming Talk
---

### Post by Somelauw on 2010-12-29
What lisp variant is most suitable for actual applications.
It should probably be:
- cross platform
- fast
- have a big standard library

Clojure probably comes close, since it relies on java.
I think common lisp hasn't good support on windows and isn't that standardized.
And scheme is probably too small.

What do you think?

---

### Post by schauerlich on 2010-12-29
Common Lisp has a reputation as the "practical" lisp. It has a lot of nice features that make it easier for day-to-day programming over something like Scheme. I have no experience with Clojure, but it is a young language that is still establishing itself. Common Lisp is well established with an fairly big standard, although many implementations have their own extensions. If you stick to the standard, you shouldn't have too much trouble going between implementations.

---

### Post by nvteighen on 2010-12-30
Common Lisp.

Clojure is nice, but isn't as mature as it should for production code. It lacks libraries and, even more important, they keep tweaking the language (for improvement) occasionally. It's likely that it will be an interesting language in the near future, but this isn't quite its moment yet.

Scheme has several problems. Mainly, it's a mess due to its minimalistic standard that just defines very few standard procedures and data structures. This forces implementations to include non-standard extensions that support very essential tools (OOP or a higher-level OS interface)... Therefore, it's very hard to write practical portable Scheme code.

Common Lisp is the best Lisp for any practical matter. Ok, it's not "pure", but it works and SBCL is a powerful implementation. It optimizes code very well,  but if you're concerned about speed, you'll have to get into the habit of using special declarations that aid the compiler to further optimization.

---


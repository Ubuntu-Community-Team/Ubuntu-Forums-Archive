---
title: "Optimizing and replacing a system package"
date: 2008-05-06
forum: Packaging and Compiling Programs
---

### Post by octavius1907 on 2008-05-06
Dear all,
I have no experience with Ubuntu package management; please bare with me. I want to recompile GMP library (Gnu multiprecision library) so that it's get optimized for my machine. Normally, GMP configure scripts detects the necessary flags automatically. I would like to replace the official package though, not to keep two copies of the same libray. But there are so many packages that depend on this one: I must be careful. All I want is to change optimizations. How do I go about this?
I downloaded the ubuntu source code, but I don't know how to convince ubuntu/synaptic to replace the official package, and more importantly how to convince the ubuntu build tools to detect the optimizations for my machine.
I would appreciate your suggestions: especially if someone may come up witha recipe for this particular package; but all other advice is welcome, too.
Kind regards.

---


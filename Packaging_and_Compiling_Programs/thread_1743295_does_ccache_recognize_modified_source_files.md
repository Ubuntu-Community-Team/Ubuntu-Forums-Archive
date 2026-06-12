---
title: "does ccache recognize modified source files"
date: 2011-04-29
forum: Packaging and Compiling Programs
---

### Post by bring1 on 2011-04-29
I've loved ccache for how quickly it can speed up repetitive package builds, given that I've never altered a single source file.

But, is it safe to use to when I'm rebuilding after modifying a few of the source files in the package (and not changing the filename of the c file)? 

Our customers have special formatting requirements, which I can achieve by changing a few lines in one single file. When I rebuild after altering that file will ccache recognize that it's been modified even though it has the same filename?

Thanks!

---

### Post by MadCow108 on 2011-04-29
ccache hashes the file (+ other stuff like compiler output) to determine if it has changed, so it will detect any change with a very very very high probability (MD4, 1:2^128).

---

### Post by bring1 on 2011-04-30
Thanks a ton! Great answer.

---


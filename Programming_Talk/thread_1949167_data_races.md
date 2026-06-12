---
title: "data races"
date: 2012-03-29
forum: Programming Talk
---

### Post by newport_j on 2012-03-29
Please recommend a good piece of software for detecting in c code data races. The parallelized uses only pthreads.
 
thanks in advance.
 
Newport_j

---

### Post by MadCow108 on 2012-03-30
valgrind offers helgrind and dtd for this. It works well with pthreads out of the box.

---


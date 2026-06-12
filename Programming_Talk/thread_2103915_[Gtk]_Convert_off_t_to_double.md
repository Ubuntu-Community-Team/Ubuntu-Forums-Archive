---
title: "[Gtk] Convert off_t to double"
date: 2013-01-11
forum: Programming Talk
---

### Post by bird1500 on 2013-01-11
Hi,
ProgressBar from Gtk uses a **double** (from 0.0 to 1.0) to set the progress amount (the **set_fraction**(double) method).
I'm measuring the size of a file and the copied amount with **off_t** (64 bit).

My naive math skills:
> 
fileSize = 100%
copiedSoFar = x%
hence:
x% = (copiedSoFar * 100%) / fileSize;
double fraction = x% / 100;
hence:
_double fraction = (double)(copiedSoFar / fileSize_);
But the underlined line yields  "Floating point exception (core dumped)".
So how do I solve the converting issue to a double from off_t?

---

### Post by spjackson on 2013-01-11
Are both copiedSoFar and fileSize of type off_t? If so, the result would normally be 0. You need to convert one of them to double before doing the division, not after the integer division. e.g.
```

double fraction = ((double) copiedSoFar) / fileSize;

```
The error you are getting suggests that fileSize is 0; you should test for this before performing the division.

---

### Post by bird1500 on 2013-01-11
Thanks a lot, you're right, it was zero (I forgot to set the file size) and casting the first number to double solves the issue completely. Yes, both numbers are off_t.

---


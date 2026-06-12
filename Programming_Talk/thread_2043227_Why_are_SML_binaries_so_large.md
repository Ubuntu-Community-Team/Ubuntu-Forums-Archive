---
title: "Why are SML binaries so large?"
date: 2012-08-16
forum: Programming Talk
---

### Post by eazar001 on 2012-08-16
A question for any SML/experienced SML programmers:

Why are SML binaries so huge? 181 kb for simple output file operations? Is this normal? Is there anybody else who programs in SML that notices this?

I use MLton to compile my source into binaries.

---

### Post by Zugzwang on 2012-08-17
Did you try running "strip" on your program? The binary may just contain tons of debug symbols.

---

### Post by eazar001 on 2012-08-17
> **Zugzwang said:**
> Did you try running "strip" on your program? The binary may just contain tons of debug symbols.

Running "strip -gd -o newfile" on my binary produces no tangible gains at all.

This is not a complex program at all, as a matter of fact they are a few test lines. It is not even a real program. Yet MLton is compiling a binary that is 196 kb in size.

By simple I mean:

```
fun form_list 0 L = L | form_list n L = form_list (n-1)(n::L);
val L = form_list 20 nil;
```

These single one-liners give me huge binaries.

---


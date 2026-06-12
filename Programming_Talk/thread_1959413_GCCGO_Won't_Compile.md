---
title: "GCCGO Won't Compile"
date: 2012-04-15
forum: Programming Talk
---

### Post by Orcris on 2012-04-15
I tried compiling a simple hello world program with GCCGO, and I got this error:
```
$ gccgo hello.go
/usr/bin/ld: cannot find -lgcc_s
collect2: error: ld returned 1 exit status

```
All the other programs in GCC work, so how do I get it to compile Go programs?

---

### Post by satsujinka on 2012-04-16
Have you tried this yet:
[http://ubuntuforums.org/showthread.php?t=1750758](http://ubuntuforums.org/showthread.php?t=1750758)

On a different note, out of curiosity why aren't you using go's default compiler?

---


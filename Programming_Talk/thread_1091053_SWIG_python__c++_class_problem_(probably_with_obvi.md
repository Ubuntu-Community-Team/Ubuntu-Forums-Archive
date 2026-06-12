---
title: "SWIG python / c++ class problem (probably with obvious solution)"
date: 2009-03-09
forum: Programming Talk
---

### Post by blake82 on 2009-03-09
Hi All,

I've created a python extension with SWIG. On the c++ side, there is a class that holds a few arrays, which are created with:

```
foo = new int[xyz]
```

 However, whatever I put in these arrays is totally corrupted when it comes back out.

(I'll put in 12 and get back 510321685)

Any ideas what might be causing this? I can't think of ANY reason why this might be happening.

Thanks,

Blake

---


---
title: "LISP dynamic push??"
date: 2009-03-05
forum: Programming Talk
---

### Post by beren.olvar on 2009-03-05
Hi there,

I am just starting with lisp and I cant figure out the following issue:

I want to push *not* elementos into a list, but its *references*, for example, if I write

```

(let (
      (a '())
      (b '()))
  (push 1 a)
  (push a b)
  (push 2 a)
  (print a)
  (print b))

```

I get
```

(2 1)                                                                     
((1))

```

and I would like
```

(2 1)                                                                     
((2 1))

```

Is there a way to achieve that?

thanks!!

---


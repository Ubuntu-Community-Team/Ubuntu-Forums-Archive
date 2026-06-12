---
title: "LaTeX quick question"
date: 2010-04-16
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-16
Hello,

I'm writing up a project and just having a bit of trouble formatting.  I am trying to insert the square box at the end of a proof using $\square$, although I can't seem to be able to right-justify it properly.  I have tried {flushright} but this puts the square in a new paragraph and I don't want the extra line spacing.  I have seen that using \raggedright right aligns text or an object without creating a new paragraph but I haven't got it working properly or found much documentation online.  Does anyone know how I can do this?

This is the line in LaTeX where I am trying to insert it:
```

For example, let $n = 6$ and $p = 3$.  We have $\binom{6}{3} = \frac{6!}{3!(6-3)!} = \frac{720}{36} = 20$, which is not divisible by $6$. 
\raggedright$\square$

```

Thanks :D

---

### Post by Zugzwang on 2010-04-16
I think that it is: "\hfill $\square$"

---

### Post by mcweaver1 on 2010-04-16
That's perfect, thanks very much :D

---


---
title: "Round integer with precision of &lt;int&gt; in C?"
date: 2009-01-01
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-01
I didn't find an answer with first 5 google attempts and I'm lazy.

How to round an integer with precision of an argument?

Just to make things clear, someone might still misunderstood:
```

a = 73;

a = round_int(a, 10);

// now a should be 70

```

---

### Post by dwhitney67 on 2009-01-01
> **crazyfuturamanoob said:**
> I didn't find an answer with first 5 google attempts and I'm lazy.

How to round an integer with precision of an argument?

Just to make things clear, someone might still misunderstood:
```

a = 73;

a = round_int(a, 10);

// now a should be 70

```
I don't quite understand the precision part of your question.  If instead of 10, the precision was 6, would you expect a result of 72?

P.S.  If so, consider N - (N % p).

---

### Post by Krupski on 2009-01-01
> **crazyfuturamanoob said:**
> I didn't find an answer with first 5 google attempts and I'm lazy.

How to round an integer with precision of an argument?

Just to make things clear, someone might still misunderstood:
```

a = 73;

a = round_int(a, 10);

// now a should be 70

```

How about this? (pseudo-code):

```

a = 73
arg = 10
a = int(a / arg)
a = a * arg

```

Translate to C or whatever you like.

Hope this helps..

-- Roger

---


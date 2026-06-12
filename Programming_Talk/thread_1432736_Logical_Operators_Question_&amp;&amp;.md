---
title: "Logical Operators Question &amp;&amp; ||"
date: 2010-03-18
forum: Programming Talk
---

### Post by derekeverett on 2010-03-18
I'm flipping through a Java book here and see that with the logical & operator the second expression is tested regardless of the outcome of the tested first expression. 

While I knew that with && the second expression was not tested if unnecessary, I was unaware of the other.

Is this true with most languages? Or is this Java specific?

---

### Post by Some Penguin on 2010-03-18
[http://en.wikipedia.org/wiki/Short-circuit_evaluation](http://en.wikipedia.org/wiki/Short-circuit_evaluation)

has a very relevant table.

---

### Post by derekeverett on 2010-03-18
> **Some Penguin said:**
> [http://en.wikipedia.org/wiki/Short-circuit_evaluation](http://en.wikipedia.org/wiki/Short-circuit_evaluation)

has a very relevant table.

Thanks for that. If I understand it correctly than I'm not crazy. I didn't think that was the same with C.

---

### Post by MadCow108 on 2010-03-18
it is not quite the same in C
in C the & operator has a different meaning
there it is the binary AND and not logical

---


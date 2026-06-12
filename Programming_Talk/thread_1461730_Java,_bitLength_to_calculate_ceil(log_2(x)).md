---
title: "Java, bitLength to calculate ceil(log_2(x))"
date: 2010-04-24
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-24
Hi everyone,

I need to calculate the ceiling of the log (base 2) of a bigInteger.  Fortunately, the bitLength function seems to do this, according to the Java documentation:

bitLength "Computes (ceil(log2(this < 0 ? -this : this+1)))"

But I'm not quite sure what it means by "this < 0 ? -this : this+1", could anyone kindly explain?  (I know that this is some kind of if statement - does it say if "this" is less than zero then it uses "-this" in the computation, otherwise it will use "this+1" ?)

Thanks in advance

---

### Post by Lux Perpetua on 2010-04-24
> **mcweaver1 said:**
> does it say if "this" is less than zero then it uses "-this" in the computation, otherwise it will use "this+1" ?Yes. You should familiarize yourself with [Java's ternary conditional operator](http://www.google.com/search?q=java+ternary+operator).

---

### Post by mcweaver1 on 2010-04-24
thank you! :)

---


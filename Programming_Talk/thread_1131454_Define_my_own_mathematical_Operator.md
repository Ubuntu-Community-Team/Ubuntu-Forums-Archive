---
title: "Define my own mathematical Operator?"
date: 2009-04-20
forum: Programming Talk
---

### Post by Dwood15 on 2009-04-20
How do I create/define my own mathematical operator in java?

I want to make it so that the common ^ symbol can be used for what it's made for- Exponentiation.

Ideas?

---

### Post by Sinkingships7 on 2009-04-20
This is an un-researched reply, but you should read up on operator overloading.

EDIT: The post below mine is better advice.

---

### Post by Jeremy Jackins on 2009-04-20
Just use 

a = Math.exp(b);

it's not that much extra work, and it makes your code understandable to others.

---

### Post by Habbit on 2009-04-21
There is no operator overloading / replacing in Java, limited support for in in C# and a much wider one in C++. However, you have to take into account that, even if you overload ^ in C++, the syntax you might end up adopting might not be that of "natural" (i.e. maths textbook) exponentiation, because the ^ operator has a defined precedende wrt other operators, and this cannot be changed. Thus, using an "exp" method may be the most natural choice indeed.

---

### Post by Dwood15 on 2009-04-21
> **Jeremy Jackins said:**
> Just use 

a = Math.exp(b);

it's not that much extra work, and it makes your code understandable to others.

I know how to use that but this was just something I wanted to know. 

@ Habbit- Thanks, I don't know much about C++ or C# I'm learning primarily Java atm.

---


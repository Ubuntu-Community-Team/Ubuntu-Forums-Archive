---
title: "Storing a 64-digit base-3 number inside of an int (Java)"
date: 2009-03-22
forum: Programming Talk
---

### Post by souled on 2009-03-22
If I have a 64-digit number in base-3, how do I put that inside of an int? I know that the number will be too big, but I'm not sure what happens when you go over the int limit (2,147,483,647)

---

### Post by happysmileman on 2009-03-22
> **souled said:**
> If I have a 64-digit number in base-3, how do I put that inside of an int? I know that the number will be too big, but I'm not sure what happens when you go over the int limit (2,147,483,647)

It wraps back around, so for example "2147483647 + 1 == -2147483648".

---

### Post by jespdj on 2009-03-22
It depends on how you are putting it into an int exactly. It could just wrap around as happysmileman says. What code are you using to do this?

---

### Post by souled on 2009-03-22
I'm trying to generate a hash function. Since it wraps around, it won't be ideal. However I am allowed some leeway as to how many collisions I can have.

Thanks.

---


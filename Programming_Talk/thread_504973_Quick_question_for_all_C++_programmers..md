---
title: "Quick question for all C++ programmers."
date: 2007-07-19
forum: Programming Talk
---

### Post by sdmike on 2007-07-19
I'm working on a program that takes anything less than a dollar and it tells you how many quarter, dimes, nickles, and pennies you get back.

My issue is I get this weird value called "inf" and I have no idea what that means.

What is "inf"

```
Enter an amount less than $1.00: 0.96
You have[COLOR="Red"] inf[/COLOR] quarters.
You have 0 dimes.
You have 0 nickles.
You have 0 pennies.
```

---

### Post by djhworld on 2007-07-19
Care to post your sourcecode?

---

### Post by sdmike on 2007-07-19
I figured it out I declared an integer when it was suppose to be a float.

---


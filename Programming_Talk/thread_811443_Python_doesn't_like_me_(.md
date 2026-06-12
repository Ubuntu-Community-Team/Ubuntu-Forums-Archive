---
title: "Python doesn't like me :("
date: 2008-05-29
forum: Programming Talk
---

### Post by eragon100 on 2008-05-29
Hi!,

What is wrong with the following code :confused:

a = 0
if choice1 = "no"
a + 0.5
if choice2 = "yes"
a + 0.5
if choice3 = "no"
a + 0.5
if choice4 = "no"
a + 0.5
if choice5 = "yes"
a + 0.5
if choice6 = "yes"
a + 0.5

I have checked for typing errors a million times and tried a trillion things with quotes, parentheses in all shapes and sizes and god-knows-what-else, but It is very persistent:

"Syntax error"

WTF Am I doing wrong :confused::(

---

### Post by eragon100 on 2008-05-29
Bump :KS

---

### Post by Zugzwang on 2008-05-29
> **eragon100 said:**
> Bump :KS

First of all, it may take some time (~1 day) before you get an answer. Don't bump so quickly. 

Second, you didn't state on which line the error occurred. My guess would be:
[LIST]
[*]You didn't intend the code properly
[*]"a + 0.5" is not a command. Try something like "a = a + 0.5"
[/LIST]

---

### Post by scourge on 2008-05-29
> **eragon100 said:**
> WTF Am I doing wrong :confused::(

Pretty much everything. You should seriously read a tutorial or the Python documentation before you start coding.

This should work:
```

a = 0
if choice1 == "no":
    a += 0.5
if choice2 == "yes":
    a += 0.5
if choice3 == "no":
    a += 0.5
if choice4 == "no":
    a += 0.5
if choice5 == "yes":
    a += 0.5
if choice6 == "yes":
    a += 0.5

```

---


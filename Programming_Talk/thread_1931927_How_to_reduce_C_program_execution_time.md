---
title: "How to reduce C program execution time"
date: 2012-02-26
forum: Programming Talk
---

### Post by stamatiou on 2012-02-26
Do you have any tips on how to reduce the execution time of a c program? For example using const vars when necessary...

---

### Post by gardnan on 2012-02-26
Well, I would say that there are no general rules for increasing performance, but there are two pieces of advice that are pretty universal.

If you are concerned with performance, make sure you are compiling using optimization options. This the -OX flag, where X is 2 or 3. 2 is pretty standard for software projects, and 3 is a little unstable. Also there are nearly hundreds of different optimization options within gcc to look through. I would recommend selecting those that suit your needs.

The second piece of advice is try and use a profiler, like gprof, to find spots of your code that may need tuning. It makes no sense to fine tune a function that is only called once for a small time delay!

---

### Post by trent.josephsen on 2012-02-26
> **stamatiou said:**
> Do you have any tips on how to reduce the execution time of a c program? For example using const vars when necessary...

You know the two rules of optimization, right?

Rule 1. Don't do it.
Rule 2. (for experts only) Don't do it yet.

If marking a variable const is your idea of reducing execution time, you're not ready for rule 2.

---

### Post by stamatiou on 2012-02-26
> **trent.josephsen said:**
> You know the two rules of optimization, right?

Rule 1. Don't do it.
Rule 2. (for experts only) Don't do it yet.

If marking a variable const is your idea of reducing execution time, you're not ready for rule 2.
Maybe you are right :/ But then, what type of int  should I use for a counter variable?

---

### Post by Bachstelze on 2012-02-26
If you think the "type of int" you use for a counter variable makes any difference in the execution time of a program, you are not ready for rule 2.

Get a book on algorithms.

---

### Post by MG&amp;TL on 2012-02-26
Bachstelze will probably tell me off/correct me for this, as I'm not ready for rule 2 either, but I pass large objects as pointers, use the -O flag, and according to *The C programming language*, if you have a commonly-used variable, you should declare it as "register" to make accessing it faster.

---

### Post by schauerlich on 2012-02-26
> **MG&TL said:**
> Bachstelze will probably tell me off/correct me for this, as I'm not ready for rule 2 either, but I pass large objects as pointers, use the -O flag, and according to *The C programming language*, if you have a commonly-used variable, you should declare it as "register" to make accessing it faster.

Those are all low-level optimizations. Chances are if you're having performance problems the best way to solve it is to change the way you solve the problem. Better algorithms trump better memory layout or parameter passing schemes 9 times out of 10.

---

### Post by Bachstelze on 2012-02-26
Also, K&R is old. Anything in it that is not purely concerned with C (mostly, anything that concerns the hardware or OS) is obsolete. [font=monospace]register[/font] nowadays is mostly a no-op, because compliers know when to keep a variable in a register. If you need to have that kind of hardware control, you write assembly, not C.

---

### Post by MG&amp;TL on 2012-02-26
> **Bachstelze said:**
> Also, K&R is old. Anything in it that is not purely concerned with C (mostly, anything that concerns the hardware or OS) is obsolete. [font=monospace]register[/font] nowadays is mostly a no-op, because compliers know when to keep a variable in a register. If you need to have that kind of hardware control, you write assembly, not C.

Huh. And I thought I bought the most recent edition for a reason. ;)

Okay, off to remove *register* from my for-loops.

---

### Post by Barrucadu on 2012-02-26
If for some reason you are unable to switch to a better implementation, you can run a profiler over your program and see where it is spending its time.

---

### Post by gardnan on 2012-02-26
> **stamatiou said:**
> Maybe you are right :/ But then, what type of int  should I use for a counter variable?

Well, I know that choosing the type of int for a counter variable doesn't really change much in terms of performance, but you may see a fair amount of code using size_t rather than int to iterate through an array.

Also, I don't remember where exactly, but I do remember reading something about optimization regarding integer values on 64-bit machines, something about machine word alignment. However, I am sure this kind of thing really is only of interest of people implementing compiler optimizations or people doing hand optimizations. If anyone had information relating to that, I would be interested.

---


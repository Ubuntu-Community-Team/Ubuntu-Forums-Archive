---
title: "Urgent! Need help with two simple Assembly Language tasks"
date: 2010-06-18
forum: Programming Talk
---

### Post by AndyBoy_LV on 2010-06-18
Hi everyone!

I`m not really good at Assembly, so i really need some help with this short program. This is a part of my final exam. I`m into web-development myself (PHP+Stuff), so these low-level languages are a disaster for me...

Task 1:
Registers R1, R2, ... R7 have numbers 1,2, ... 7 in them. The question is, what will be in these registers after the following part of ARM assembly program has been run:

```

stmfd sp, {r1, r2, r3, r4}
str r5 [sp, #-4]!
sub sp, sp, #8
stmfd sp!, {r6, r7}
ldr r1, [sp]
ldmfd sp!, {r2, r3, r4}
ldr r5, [sp, #4]
ldmfd sp, {r6}
ldmfd sp!, {r7}

```

If somebody would be so kind and help me, please also write some comments so that i can understand what it`s all about...

Task 2:
Write ARM assembly function, that (using a call to printf with a format "%x\n") prints all "special" natural numbers from 1 to 505356. "Special" means that the sum of pair digits in this number is equal to the sum of unpair digits. For example: 109A (1+9 = 0+A)

Any help would be appreciated... Big thank you in advance.

---

### Post by DanielWaterworth on 2010-06-18
If it's part of an exam I feel reticent about helping you too much, but whenever I have to understand assembly, I write as a comment on each line what's in each register/relevant memory location. You're lucky because there doesn't seem to be any looping.

---

### Post by schauerlich on 2010-06-18
Homework questions, especially ones on final exams, aren't allowed.

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by Elfy on 2010-06-18
Closed.

---


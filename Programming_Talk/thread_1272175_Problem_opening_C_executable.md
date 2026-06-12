---
title: "Problem opening C executable"
date: 2009-09-21
forum: Programming Talk
---

### Post by Redblade3 on 2009-09-21
Recently I started to program in C. However, I wanted to do it here in Ubuntu. I wrote a very simple program that displayed a certain text, compiled it using gcc, but when I tried to run the .out, the terminal gave me:

bash: test.out: command not found

I double and triple-checked the code, recompiled, checked that I was in the correct folder and everything, but the error persists.

I would appreciate any help!

cheers!

---

### Post by lisati on 2009-09-21
If the name of the compiler output is **test.out**, try: ```
./test.out
```

---

### Post by Redblade3 on 2009-09-21
Excellent, worked like a charm. Thanks a lot!!

---


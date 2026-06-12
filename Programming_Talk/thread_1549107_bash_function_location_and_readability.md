---
title: "bash function location and readability"
date: 2010-08-09
forum: Programming Talk
---

### Post by japhyr on 2010-08-09
Hello,

I am used to languages in which functions can be defined at the end of a script.  Having to define functions before they are called seems to make the script less readable.  Instead of focusing on logic first and then seeing the grunt work of functions, all the grunt work comes first, and then overall logic comes last.

Is there a way to make function-first scripts more readable?  Is it standard practice to put function definitions in a separate file and include them?

---

### Post by DaithiF on 2010-08-09
Hi, I guess you could:
```
tac yourscript
```
:)

but on a more serious note, no, since shell scripts are typically fairly short and straight-forward, theres often no particular need to manage complexity by breaking a script down into many functions, and/or to manage the readability of the code in the way you describe.

---

### Post by japhyr on 2010-08-09
Thanks, that's about what I was thinking.

---


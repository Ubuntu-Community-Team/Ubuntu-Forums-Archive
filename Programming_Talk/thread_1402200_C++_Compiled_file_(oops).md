---
title: "C++ Compiled file (oops)"
date: 2010-02-08
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-08
Yeah, n00b question, probably got the answer through the analogy of a cake. 

I accidentally did this through the terminal with the following command...

g++ program.cpp -o program.cpp 

Guess who feels stupid. 

Anyway to get the source code outta that?

------
Reason I'm asking is because I haven't found anywhere to reverse it so I'm assuming its not possible.

---

### Post by dwhitney67 on 2010-02-08
> **Ravenshade said:**
> Yeah, n00b question, probably got the answer through the analogy of a cake. 

I accidentally did this through the terminal with the following command...

g++ program.cpp -o program.cpp 

Guess who feels stupid. 

Anyway to get the source code outta that?

------
Reason I'm asking is because I haven't found anywhere to reverse it so I'm assuming its not possible.

I have made this same mistake before.  As far as recovery of the code, you are out of luck unless your editor made a back-up of the source file.

Some editors append a tilde character to the back-up file.  In other cases, if you are using vim as your editor, a swap file may exist as a hidden file in your source directory.  If none of these apply, then as I said earlier, you're out of luck.


P.S.  There's always the option of trying a disassembler.  However, I have not used one of these in over 15 years.  I know they exist, but for Linux?

---

### Post by Ravenshade on 2010-02-08
Well as a work around...I re-wrote the entire program. Perhaps not word for word but it was all good practice for hard coding ^_^

---

### Post by dwhitney67 on 2010-02-08
> **Ravenshade said:**
> Well as a work around...I re-wrote the entire program. Perhaps not word for word but it was all good practice for hard coding ^_^

That works too!  It keeps the mind sharp.

---

### Post by MadCow108 on 2010-02-09
hehe
maybe we should file a bug report, I can't see how this behavior has any positive use when the input is a source file :)

---


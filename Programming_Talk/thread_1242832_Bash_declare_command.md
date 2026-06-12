---
title: "Bash declare command"
date: 2009-08-17
forum: Programming Talk
---

### Post by osx on 2009-08-17
I'm reading a book on bash scripting called "Linux Shell Scripting with Bash" that was published in 2004. On page 67 it says variables are declared using the Bash declare command.

I'm not totally new to Bash scripting, but not extremely well versed either; however, I have not seen the declare command used routinely in scripts posted online, nor ever used it myself.

I would like to know whether or not I should.

Is there an advantage/disadvantage to using the declare command for each and every variable?

Thanks.

---

### Post by stroyan on 2009-08-17
The "declare" or "typeset" builtin is seldom used except when it is needed to give a variable an attribute.
If you want to you could declare all variables as a style requirement.
The declare statement could be the point where you add a comment to explain what each variable represents. ;-)

But there is no setting that tells the shell that variables must be declared.
(That would be an interesting way to avoid typos that mismatch a variable name.  Fortran 77 has that feature as "implicit none".)
You could attempt to use a static script scanner to check for undeclared variables.
But it can be tricky to parse some shell constructs.

---

### Post by osx on 2009-08-17
Great, thanks.

---


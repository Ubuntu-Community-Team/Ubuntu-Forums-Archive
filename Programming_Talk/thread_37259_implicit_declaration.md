---
title: "implicit declaration"
date: 2005-05-26
forum: Programming Talk
---

### Post by daniminas on 2005-05-26
somebody can tell me what happend when appear this error on a gcc compilation? (C) ¿what am i dooing wrong?

Thanks

---

### Post by LordHunter317 on 2005-05-26
[QUOTE=daniminas]somebody can tell me what happend when appear this error on a gcc compilation? (C) ¿what am i dooing wrong?

Thanks[/QUOTE]
 It ought to be a warning, and it means you're using a function that doesn't have a prototype.

You need to include the right header file.

You know, posting the output makes this stuff much eaiser.

---

### Post by daniminas on 2005-05-28
Okey, thanks...

This is what ai get:
Implicit declaration of function 'save_flags'
and
Implicit declaration of function 'cli'

and in the lines of the source code i found this:

save_flags(flags); cli();

I don't know what really do this two functions.  :|

---

### Post by daniminas on 2005-06-04
](*,) 
any one?

---


---
title: "Python error meaning?"
date: 2010-09-09
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-09
What does this error below mean??

> SyntaxError: can't assign to operator


NOTE: Im not a Python developer... only recently started playing with it! :)

---

### Post by Bachstelze on 2010-09-09
How about you show us your code? ;)

---

### Post by cgroza on 2010-09-09
Hmmm, All i can think without seeing your code is that you did something similar to this:

+ = 'string or int here'

Name your variable something else.

---

### Post by fallenshadow on 2010-09-09
Its says the problem is with line 14.

```
iscVweight-text = ""
```

Can anyone figure it out or should I post the full code?

---

### Post by fallenshadow on 2010-09-09
Oh dear... I just figured it out.

It seems I can't use a "-" sign in variable names.

Silly me! :redface:

---

### Post by Zugzwang on 2010-09-09
I think that "-" is not an allowed part of a variable name as it represents the "minus" operator.

---

### Post by cgroza on 2010-09-09
> **fallenshadow said:**
> Oh dear... I just figured it out.

It seems I can't use a "-" sign in variable names.

Silly me! :redface:

You can't use '+,-,/,*,**' and some keywords as a name for your variables. Basically, just don't put operators in the name of your variables.

---

### Post by schauerlich on 2010-09-09
You know, if this was *Lisp*...

I kid, I kid.

---


---
title: "Regex"
date: 2010-06-16
forum: Programming Talk
---

### Post by epicoder on 2010-06-16
How do I make a regex that matches a character, then any amount of characters, then another character?

in bash, I would use:

a*b

Which would match anything starting with a and ending with b, with any number of any characters in between them. How would I do this in regex?

---

### Post by DanielWaterworth on 2010-06-16
a.*b

---

### Post by amauk on 2010-06-16
a.*b

dot (in this instance) means any character
and that's used with the asterisk for "any number of characters

---

### Post by Bachstelze on 2010-06-16
a.*b

. means "any character" and * means "the last character repeated any number of times".

```
man 7 regex
```

---

### Post by epicoder on 2010-06-16
Thanks, guys!

You know, now that I see it, I wonder why I didn't get that in the first place after googling regex. It seems kinda obvious. Oh well.

---


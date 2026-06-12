---
title: "regex + python"
date: 2009-07-28
forum: Programming Talk
---

### Post by Flynn555 on 2009-07-28
hey i had a quick question about regular expressions in python

this is probably rather "noobie" but regex is not one of my strong points. 

say i want to grab all the lines from an input file that *do not* begin with the character C

i know the expression to grab the lines that *do* begin with C is 

^C.*

but i cant figure out how to just grab the lines that donot begin with C.  is there any sort of negation in regex? 

 ex. !(^C).*  <-- didnt work :(  

any ideas?

---

### Post by unutbu on 2009-07-28
[php]^[^c]*[/php]

That is suppose to be a capital C, but for some reason VBulletin is not allowing me to write that.

Anyway, [^C] means any character except C.

---

### Post by Flynn555 on 2009-07-28
> **unutbu said:**
> [php]^[^c]*[/php]


edit: sorry works great thanks! ... kindof

---

### Post by Flynn555 on 2009-07-28
edit fixed it

---

### Post by ghostdog74 on 2009-07-28
simple task like this you don't need regular expression. if its not your strong points, then focus more on Python's basics...

```

if not mystring.startswith("C") :
  print "doesn't start with c"

```

---


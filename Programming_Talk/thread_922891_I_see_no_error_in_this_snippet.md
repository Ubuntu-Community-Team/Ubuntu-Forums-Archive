---
title: "I see no error in this snippet:"
date: 2008-09-17
forum: Programming Talk
---

### Post by adamogardner on 2008-09-17
Hi, I'm on chapter 7 of _learning Python_ and I'm going through stuff one section at a time and for some reason this string :

>>> s = 'a\nb\tc'
>>> s
'a\nb\tc'

as you can see did not create a new line (\n) for 'b' & 'c' nor a tab(\t) for 'c'.  Am I a big dummy?  Did I miss a section?

ah sorry remove this thread I figured it out I need to type 'print s'

---

### Post by kjohansen on 2008-09-17
if you do:

```

print n

```

you will get the new line and tab.  otherwise you are just showing the raw data of the variable so it does not consider it to be printing and ignores the print control symbols.


**Edit: oops didnt see that the poster corrected it

---


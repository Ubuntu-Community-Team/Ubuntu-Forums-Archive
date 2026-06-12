---
title: "python find word in jumble of non-letters"
date: 2011-01-20
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-01-20
what's the easiest way to isolate a word (unspecified) from a jumble of numbers + symbols? 
for example:
I give the program '54. describe72. & 60', that's all, and i want it to find and isolate the 'describe'. There will be no other letters in the string

I was thinking of doing something like looping through every char in the string, checking if its a letter, and if its not combine two slices that skip that non-letter into the same variable again. 
seems like a rather tedious way to do it... is there an easier one?

---

### Post by Vaphell on 2011-01-21
2 words: import re

[php]
#!/usr/bin/env python

import re

string = '54. Describe72. & 60'
print string, "=>", re.search( r"[a-zA-Z]+", string ).group(0)
[/php]

---

### Post by LemursDontExist on 2011-02-09
Or, don't import re:

```
s = '54. Describe72. & 60'
filter(lambda c: c.isalpha(), s)
```

---

### Post by Asday on 2011-02-10
Importing is for casuals.

[PHP]>>> "54. describe72. & 60".index("describe")
4
>>> #If you wanna be clever
>>> "54. describe72. & 60"["54. describe72. & 60".index("describe"):"54. describe72. & 60".index("describe")+len("describe")]
'describe'
>>> #Or
>>> print("describe")[/PHP]

---

### Post by LemursDontExist on 2011-02-10
It's been bugging me that I needed a lambda to write the filter code - and I just remembered a better way to do it:

```
s = '54. Describe72. & 60'
filter(str.isalpha, s)
```

---


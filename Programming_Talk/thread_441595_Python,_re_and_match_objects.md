---
title: "Python, re and match objects"
date: 2007-05-12
forum: Programming Talk
---

### Post by Ramses de Norre on 2007-05-12
I'm trying to get to know python a bit, but I'm kind of stuck...
How do the regular expressions work??? I know how to define and compile a re and I use the search function to go through a string with it. But then I get a "Match object" returned and I can't find a way to do anything useful with that... How can I restore the found occurrences or the their positions in the input string?

I need to find the matching sequences in a string, can someone point me how to do so?
This is what I've got now:```
p=re.compile("[A-Z][A-Z][A-Z][a-z][A-Z][A-Z][A-Z]")
m=re.search(p,str)
```

---

### Post by pmasiar on 2007-05-12
> **Ramses de Norre said:**
> I need to find the matching sequences in a string, can someone point me how to do so?

Unless you need really complicated regex pattern tricks, much of finding can be done with string methods: find, rfind, index, startswith, split and join. Proper regular expressions are very powerful, but hard.  I try to stay with string methods if I can. If not, I just look for examples. [http://regexlib.com/](http://regexlib.com/) has many examples and regex tester.

Regular expressions is tricky programming language by itself (beware of greedy dot-star) - [http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression) is good start, see links/articles at the end. 

[http://kodos.sourceforge.net/](http://kodos.sourceforge.net/) is your own regex tester.

---

### Post by WW on 2007-05-12
Maybe **findall**?

**testfindall.py**
```

import re

p=re.compile("[A-Z][A-Z][A-Z][a-z][A-Z][A-Z][A-Z]")
str1 = "AAAAAbCCCCdEEEEfGGGhhhIIII"
m1 = p.findall(str1)
print str1, " contains ", m1
str2 = "AAAbCCCdEEEfGGGhIIIjKKKlMMM"
m2 = p.findall(str2)
print str2, " contains ", m2

```
```

$ python testfindall.py
AAAAAbCCCCdEEEEfGGGhhhIIII  contains  ['AAAbCCC', 'EEEfGGG']
AAAbCCCdEEEfGGGhIIIjKKKlMMM  contains  ['AAAbCCC', 'EEEfGGG', 'IIIjKKK']
$

```
(Check out section 4.2.3 of the [Python re docs]("http://docs.python.org/lib/module-re.html").)

---

### Post by ghostdog74 on 2007-05-12
> **Ramses de Norre said:**
> 
I need to find the matching sequences in a string, can someone point me how to do so?
This is what I've got now:```
p=re.compile("[A-Z][A-Z][A-Z][a-z][A-Z][A-Z][A-Z]")
m=re.search(p,str)
```

once you compiled your regexp using p=re.compile(..), you can use the re module methods like finditer or findall...check the re module docs for more info.
```

p.findall(str)

```

---

### Post by Ramses de Norre on 2007-05-13
findall was exactly what I was looking for!:) 
Strange that I couldn't find it on the web...

---


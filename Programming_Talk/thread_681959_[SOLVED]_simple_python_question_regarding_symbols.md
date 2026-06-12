---
title: "[SOLVED] simple python question regarding symbols"
date: 2008-01-29
forum: Programming Talk
---

### Post by seventhc on 2008-01-29
I'm not sure if this actually warrants a thread but, I have no other way.
Is there a way to enter symbols with python
for example the degree symbol, I found this
[php]
degree_symbol = unichr(176).encode("latin-1")
print degree_symbol
[/php]but it only shows as one of those question marks when the character isn't recognized. It isn't entirely important but I'm trying to do some online tutorials and now I'm experimenting  and would like to be able to add this symbol. I have looked around but haven't found much else.
I would think there should be a chart or something.
If anyone knows how to do this, or a site with a chart I appreciate it. :)

---

### Post by Miriam77 on 2008-01-29
> **seventhc said:**
> I'm not sure if this actually warrants a thread but, I have no other way.
Is there a way to enter symbols with python
for example the degree symbol, I found this
[php]
degree_symbol = unichr(176).encode("latin-1")
print degree_symbol


```

degree = unichr(176)
print degree

```

Works but your code printed the unknown character symbol.

---

### Post by seventhc on 2008-01-29
Thank you :) that works. :)

---


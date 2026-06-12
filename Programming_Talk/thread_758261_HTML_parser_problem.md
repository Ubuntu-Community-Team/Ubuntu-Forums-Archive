---
title: "HTML parser problem"
date: 2008-04-17
forum: Programming Talk
---

### Post by King Buttons I on 2008-04-17
I am having a problem with Java's HTML parser. Whenever I extract the text from a website it starts a new line before and after every link.

Here is an example of what it puts out:
```
He (
http://definr.com/He
)
     n 1: a very light colorless element that is one of the six inert
          gasses; the most difficult gas to liquefy; occurs in
          economically extractable amounts in certain natural
          gases (as those found in Texas and Kansas) [syn: 
helium
,
           
He
, 
atomic number 2
]
     2: the 5th letter of the Hebrew alphabet
```

Here is what I want it to look like or something similar to it:
```

He (http://definr.com/He)

     n 1: a very light colorless element that is one of the six inert
          gasses; the most difficult gas to liquefy; occurs in
          economically extractable amounts in certain natural
          gases (as those found in Texas and Kansas) [syn: helium,
           He, atomic number 2]
     2: the 5th letter of the Hebrew alphabet
```

Does anyone know how Java interprets links and can anybody help me?
Buttons

---


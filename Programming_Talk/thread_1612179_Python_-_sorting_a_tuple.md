---
title: "Python - sorting a tuple"
date: 2010-11-02
forum: Programming Talk
---

### Post by meastwood on 2010-11-02
[*** SOLVED ***]

Have tried the following but no joy - am using ver. 2.6.2

>>> people = [(0,"Tom"),(1,"****"),(2,"HARRY"),(3,"george"),(4,".fred"), (5,"harold")]

>>> sorted(people, key=lambda id : id[1].lower)
[(5, 'harold'), (0, 'Tom'), (3, 'george'), (4, '.fred'), (2, 'HARRY'), (1, '****')]

>>> sorted(people, key=lambda id : id[1])
[(4, '.fred'), (2, 'HARRY'), (0, 'Tom'), (1, '****'), (3, 'george'), (5, 'harold')]

>>> sorted(people, key=itemgetter(1))
[(4, '.fred'), (2, 'HARRY'), (0, 'Tom'), (1, '****'), (3, 'george'), (5, 'harold')]

What I want to be returned is :
[(4, '.fred'),  (1, '****'), (3, 'george'), (5, 'harold'), (2, 'HARRY'), (0, 'Tom') ]

thanks for any help


"****" is lower case !!!

---

### Post by cyberslayer on 2010-11-02
This line you wrote

```
sorted(people, key=lambda id : id[1].lower)
```

is almost what you need; however, the function lambda id : id[1].lower is incorrect as it returns the str.lower function object -- not the result of calling the function on the string which is probably what you intended.  You need to do the following instead:

```
sorted(people, key=lambda id : id[1].lower())
```

---

### Post by meastwood on 2010-11-03
That's done it - thank you

---


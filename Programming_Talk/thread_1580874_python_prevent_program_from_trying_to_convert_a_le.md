---
title: "python: prevent program from trying to convert a letter to an int"
date: 2010-09-24
forum: Programming Talk
---

### Post by daweefolk on 2010-09-24
In my python program I want it to convert (if possible) the input from the user to an int. To prevent error I want it to have a "safety feature" that will prevent itself from trying to convert, say, "q" to an int if the user decides to mess around. How is this possible? I'm sure it's simple, I just couldn't find it through google or forum search. Thanks!

---

### Post by schauerlich on 2010-09-24
If you use the raw_input() function, everything you'll get back is a string. You can then try to get extract an int from it. This example will keep looping until the user inputs a number:

```
>>> def query():
...     while True:
...             foo = raw_input("> ")
...             try:
...                     foo = int(foo)
...                     return foo
...             except ValueError:
...                     print "You must enter a number!"
... 
>>> bar = query()
> 1
>>> bar
1
>>> bar = query()
> sdfkjgh
You must enter a number!
> fdjbv
You must enter a number!
> 4
>>> 
```

---


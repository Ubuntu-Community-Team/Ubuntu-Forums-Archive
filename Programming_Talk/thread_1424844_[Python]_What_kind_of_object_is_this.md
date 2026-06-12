---
title: "[Python] What kind of object is this?"
date: 2010-03-08
forum: Programming Talk
---

### Post by navneeth on 2010-03-08
What I first thought was a typo in the book *Beginning Python, 2 ed.*, by Magnus Lie Hetland, turned out to be a valid assignment.

In showing how to use the join() function, the author defines the following object:

```
dirs = '','usr','bin','env'
```

What is this? On first reading, I assumed it was a list (or a queue, perhaps) missing the brackets, but when I tried it in the interpreter, Python didn't seem to mind.

---

### Post by Zugzwang on 2010-03-08
That is a "tuple": [http://docs.python.org/tutorial/datastructures.html#tuples-and-sequences](http://docs.python.org/tutorial/datastructures.html#tuples-and-sequences)

---

### Post by capybara! on 2010-03-08
It's a python built in 'tuple' object. You can get the type with the 'type()' function:

```

type(dirs)
   <type 'tuple'>

```

Type 'help tuple' into your python shell and you'll see what you can do with the tuple object...

---

### Post by navneeth on 2010-03-08
Oh. Now that I turn back the pages, I see that he mentions that you can create a tuple simply by separating the entries by commas.:oops: I have been used it as something enclosed within (). (Oh, and did I say "queue"? What's wrong with me! I actually meant tuple there.)

Thanks, guys.

---

### Post by navneeth on 2010-03-08
> **capybara! said:**
> It's a python built in 'tuple' object. You can get the type with the 'type()' function:

```

type(dirs)
   <type 'tuple'>

```



Never heard of that function before, but I'm sure it will come in handy in future. Thanks once again. :)

---

### Post by Can+~ on 2010-03-08
> **navneeth said:**
> Never heard of that function before, but I'm sure it will come in handy in future. Thanks once again. :)

Those are called the [built-in functions]("http://docs.python.org/library/functions.html"). It's always good to know this general-purpose function, I remember when I swapped an entire piece of code with a single "cmp" function.

Also, try to prefer the "(a, b, c)" notation for tuples, it's more explicit.

---


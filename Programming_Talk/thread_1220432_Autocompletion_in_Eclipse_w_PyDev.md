---
title: "Autocompletion in Eclipse w/ PyDev"
date: 2009-07-22
forum: Programming Talk
---

### Post by AndThenWhat on 2009-07-22
I am trying to get the PyDev plugin on Eclipse to show autocompletion inside of parentheses.  Right now, when I type a '(' nothing happens but I know that it is capable of displaying the possible values. Do I need another plugin or python interpreter???

I have to note that I have the option for code completion on when I type a '('

---

### Post by CptPicard on 2009-07-22
Are you sure that the parameter names are deducible in the context you're in? Python is after all a duck-typed language... the object you're calling the method on might be anything.

---

### Post by AndThenWhat on 2009-07-22
Well some of the things are ambiguous, but some should have code completion like box1.pack_start( <-- should show tooltip with (Object, Boolean, Boolean, Integer) at the very least.

Is there some way I can add my own code completion options??

---

### Post by CptPicard on 2009-07-22
> **AndThenWhat said:**
>  <-- should show tooltip with (Object, Boolean, Boolean, Integer) at the very least.

Well, the types of the parameters aren't declared in Python at all, anywhere, so how would it know they are Object, Boolean... so on? At best you may be able to tell the names of the parameters, but even then it's not a given...

---


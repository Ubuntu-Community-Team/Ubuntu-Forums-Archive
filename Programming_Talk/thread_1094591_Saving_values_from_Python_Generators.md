---
title: "Saving values from Python Generators"
date: 2009-03-12
forum: Programming Talk
---

### Post by x0ne on 2009-03-12
All,

I really need help extracting some data from a Python generator object. I see that generators have 4 methods (next, send, etc), but no way to reference a value like you would in a list or dictionary. I know you can loop through a generator and get all the values, but there must be a better way to do this.

I have a dictionary generator object that looks something like:

{'KEY': 'Value'}

When I try to print out the value based on the key I get this:

"generator object is unsubscriptable"

Besides nested for loops and list creations, how can I access my data and assign each value to a variable?

---

### Post by Wybiral on 2009-03-12
I'm not sure you quite grasp what a generator object is... It's a state, saved in some function. A function that can be resumed and yield values. It's not scriptable because it's not a collection, it's lazily computed...

---

### Post by x0ne on 2009-03-12
Ah, well that would make sense as to why I am having a hard time. I am working with a class that uses them and it just confuses me as to why the person used generators if they can't even work with the data.

---

### Post by Wybiral on 2009-03-13
They're for iterating over or pulling values, in sequence, one at a time. Not for indexing or random access. But they're really useful when you need to represent some series of values to be iterated, especially since it's lazy (you could build a list and iterate it, but that would waste memory, not to mention that generators can be never-ending... Such as a prime-number generator or a fibonacci generator)

---


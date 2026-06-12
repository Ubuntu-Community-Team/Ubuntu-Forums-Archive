---
title: "[python] All new class instances point to the same object?"
date: 2009-04-18
forum: Programming Talk
---

### Post by Dorzu on 2009-04-18
I'm writing a program in Python and have found a strange(to me) error that I cannot seem to fix. This is my first work with classes in Python and I'm obviously missing something important.

I wrote a class, we'll call it "Car". Car has a dictionary of "parts".
#Create class instances
a = Car()
b = Car()
a.parts["engine"] = "V6"
b.parts["engine"] = "V4"

Now, in my script, a.parts["engine"] has "V4". Why? I tested with the obvious 'print a == b' and received True. Even if I move "b = Car()" _after_ the first set of a.parts, they're still referencing the same object. What am I doing wrong? How do I instantiate two of them separately?

---

### Post by Dorzu on 2009-04-18
I don't know how to delete the thread. Sorry.

Apparently I had mistakenly made the dictionary a class variable, instead of an instance. I moved the variable to __init__(), prefixed it with "self." and it's happy.

---


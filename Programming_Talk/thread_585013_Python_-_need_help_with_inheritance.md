---
title: "Python - need help with inheritance"
date: 2007-10-21
forum: Programming Talk
---

### Post by Torajima on 2007-10-21
I'm having trouble with inheritance and constructors. I can't figure out how to add to the base class constructor without overriding it completely.

Say, I create class Person() which has one attribute: name.

I then create a derived class Girl() which has two attributes, name & description. Under __init__, I only want to define description, as name should be pulled from the base class.

How do I do this?

I've messed around with the "super" keyword, but it always generates an error (and yes, I'm using new style classes).

---

### Post by geirha on 2007-10-21
I don't completely understand your question. Is this what you want?
```

class Person:
    def __init__(self,name):
        self.name= name

class Girl(Person):
    def __init__(self,name):
        Person.__init__(self,name)
        self.description= "it's a girl"

```

---

### Post by Torajima on 2007-10-21
Thanks, that's what I needed... it got me on the right track.

I think what had me stumped was that default variable assignments weren't carrying over to the derived class. Well, that and "super" just wouldn't work for me...

---


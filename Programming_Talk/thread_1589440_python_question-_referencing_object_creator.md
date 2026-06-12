---
title: "python question- referencing object creator?"
date: 2010-10-06
forum: Programming Talk
---

### Post by daweefolk on 2010-10-06
if i have a class "person" and a function in person can make an instance of class "question", can i, in a function in the 'question' object, reference back to the 'person' object that created it?

ex: 'bob' is instance of class 'person'
'bob' creates 'howareyou' instance of class 'question'
later, 'howareyou' needs to get a value of a variable in 'bob'. 

is there a way to make it so 'question' instances have a variable named 'parent' or something they can reference in
```
if parent.something=="foo":
print "bar"
```?
so, replacing object name with a variable.
Sorry if I'm confusing.

---

### Post by surfer on 2010-10-06
you could add a member [FONT="Courier New"]person[/FONT] in the [FONT="Courier New"]question[/FONT] class and set it when you create the [FONT="Courier New"]question[/FONT] (in the member function of [FONT="Courier New"]person[/FONT])

```

question.person = self

```

...need more pseudocode on that one?

---

### Post by nvteighen on 2010-10-07
Yes, you need self, but what I'd do is to pass that information as a parameter to the constructor, not to the method.

```

class AnotherSomething(object):
    def __init__(self, creator):
        self.blah = 1
        self.creator = creator

    def some_method(self):
        if self.creator.myvar == 0:
            print "Hey!"

class Something(object):
    def __init__(self):
        self.myvar = 0
        self.myAnotherSomething = AnotherSomething(self)

```

---

### Post by shushens on 2012-02-05
> **surfer said:**
> you could add a member [FONT="Courier New"]person[/FONT] in the [FONT="Courier New"]question[/FONT] class and set it when you create the [FONT="Courier New"]question[/FONT] (in the member function of [FONT="Courier New"]person[/FONT])

```

question.person = self

```

...need more pseudocode on that one?

Yes please! I am also stuck with this, and it is still not clear to me how this referencing works. I am trying to do a bidirectional signal-slot connection in Qt. A creates object of type B, and now B must have a slot for a signal in A. The reverse is easy, but this is tricky for me.

---

### Post by epicoder on 2012-02-06
Here is what I can come up with off the top of my head:
```

class Person():
    def __init__(self):
        self.trigger=0
    def question():
        return Question(self)

class Question():
     def __init__(self, parent):
         self.parent=parent
         #self.parent.trigger == 0

```

---


---
title: "Questions about Python"
date: 2011-09-30
forum: Programming Talk
---

### Post by KeNtUrKeY on 2011-09-30
Hi everybody, 
I'm learning python by myself right now so it is tough for me and everyone so bare with me for little bit =))

i have something like this

class A()
    def a(self)
        value
    def b(self)
        ....

my question is: can i use value in def a in b? if so, can u show me how? if not, is there anyway i can use value in one def to another?
what happen if that value is array?

thank you very much.

---

### Post by Tony Flury on 2011-09-30
Hint : If you include your python code in CODE tags it keeps the indetation.

To aswer your question - yes you can use any method of a class in any other method of that class : 

```

class A()
    def a(self, value)
        print value + 1

    def b(self)
       print "Calling a()"
       self.a(3)

```

As you can see you call it by using the self attribute. All instances when created have a attribute called self, which is themselves.
If you want a to store a value - then that is easy too - you create an instance variable : 

```

class A()
    def a(self, value)
       self.new_value = value + 1

    def b(self)
       self.new_value = 0 
       print self.new_value
       print "Calling a()"
       self.a(3)
       print self.new_value

```
As you will see the new_value will go from 0 to 4 since a changes it.

---


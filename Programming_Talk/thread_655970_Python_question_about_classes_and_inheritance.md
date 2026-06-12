---
title: "Python question about classes and inheritance"
date: 2008-01-02
forum: Programming Talk
---

### Post by NovaAesa on 2008-01-02
Okay I've been messing around with classes and inheritance (I think it's called inheritance, correct me if I'm wrong :)). If I have one class as follows:

[PHP]class foo(object):
    def first_function(self):
        print 'hello'[/PHP]

Now I have a second class as follows:

[PHP]class bar(foo):
    def __init__(self):
        foo.first_function(self)[/PHP]

now when I type the following in for the prompt:

```
>>> a = bar()
hello
>>> 
```

This is what I would expect, however I found that if I change the second class to:

[PHP]class bar(foo):
    def __init__(self):
        self.first_function()[/PHP]

it works exactly the same way. So my question is, which way should I write the second class? Is one more Pythonic than the other, or doesn't it really matter?

---

### Post by Nekiruhs on 2008-01-02
I would go with self.first_function() as it more clearly demonstrates that you are calling a.first_function, being an instance of bar, rather than just pulling the function out of the blue from foo. Self more clearly shows that you are using inheritance.

---

### Post by NovaAesa on 2008-01-02
Yes, that makes sense. It also goes along with the way that you have to refer to instance variables in classes inherited from other classes. e.g. This works:

[PHP]class Foo(object):
    def __init__(self):
        self.answer = 42
        
class Bar(Foo):
    def function_one(self):
        print self.answer[/PHP]

But this doesn't:

[PHP]class Foo(object):
    def __init__(self):
        self.answer = 42
        
class Bar(Foo):
    def function_one(self):
        print Foo.answer[/PHP]

But in this case, why does one work and one not (throws an AttributeError when function_one() is called) rather than one just being 'better' than the other?

---

### Post by NovaAesa on 2008-01-03
I think I get it now. It's because Foo.answer is a class variable whereas self.answer is an instance variable. Because there are no class variables defined named answer in either Foo or Bar, the AttributeError is thrown. Is this right, or am I a bit off here?

---

### Post by pmasiar on 2008-01-04
Correct.

It helps to imagine class as cookie cutter, and instance as the cookie make by the class. Classes are from metal, not edible, so you use them differently :-)

---

### Post by cryptoD on 2008-01-04
You need to make your method static, in Python it's a bit different. [here](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/52304) is an example.

---


---
title: "[ruby] [python] question on attr_accessor"
date: 2010-09-27
forum: Programming Talk
---

### Post by mo.reina on 2010-09-27
i'm going throught bruce tate's book 'seven languages in seven weeks' and came across ruby's attr_accessors.  the only languages i've ever used before python were C (two sems in uni, almost totally useless), and bash, so my first introduction to classes was in python.

after googling and reading up a bit, i've come to the following conclusions:

attr_accessor in ruby is used to render the variables in the class instance readable and writable. [True/False]
i.e.
```
> class Foo
> def initialize(name)
> @name = name
> end
> end
=> nil
> a = Foo.new('mo')
=> #<Foo:0x00000001dbd0c0 @name="mo">
> a.name
NoMethodError: undefined method `name' for #<Foo:0x00000001dbd0c0 @name="mo">
	from (irb):7
	from /usr/bin/irb1.9.1:12:in `<main>'

```
v.s.
```
> class Foo
> attr_accessor :name
> def initialize(name)
> @name = name
> end
> end
=> nil
> a = Foo.new('mo')
=> #<Foo:0x00000001301118 @name="mo">
> a.name
=> "mo"

```


there is no such thing in python, because the variables are readable and writeable from the start. [True/False]

```
>>> class Foo():
...   def __init__(self, name):
...     self.name = name
... 
>>> a = Foo('mo')
>>> a.name
'mo'
```


However there are setters and getters in python (property built-in/decorators), which are usually used to render the instance variables in python read-only. [True/False]

Any other uses of setters and getters in python?

Is the definition of attr_accessor in ruby accurate, wrong, incomplete?

---

### Post by Bachstelze on 2010-09-27
You use "setters" and "getters" because in OOP, the user (i.e. the programmer who will use your code, not the end-user) should not concern himself with how your class works.  The only thing that is of interest to him is the interface of the class: the functions he will actually use when writing his code.

Suppose you have a class like this:

```
from math import pi

class Circle(object):
    def __init__(self, x=0, y=0, r=1):
        self.x = x
        self.y = y
        self.r = r
        
    def get_center(self):
        return (self.x, self.y)
    
    def get_radius(self):
        return self.r
    
    def set_center(self, x=0, y=0):
        self.x = x
        self.y = y
        
    def set_radius(self, r=1):
        self.r = r
        
    def area(self):
        return pi*self.r**2
    
    def perimeter(self):
        return 2*pi*self.r
```

A user could get the radius of a Circle with

```
>>> c = Circle()
>>> c.r
1

```

or with

```
>>> c.get_radius()
1

```

Why is the second one better?  Consider what happens if you decide that r is not descriptive enough, and you want to rename it to radius.  The second one will still work (if you do your job properly), the first one will not.  The name of the class attribute that represents the radius of the circle is an implementation detail, and the user should have to know about it in order to use your class.

---

### Post by raf_kig on 2010-09-27
> **mo.reina said:**
> 
there is no such thing in python, because the variables are readable and writeable from the start. [True/False]

Correct.
> **mo.reina said:**
> 
However there are setters and getters in python (property built-in/decorators), which are usually used to render the instance variables in python read-only. [True/False]

Correct, python uses properties which enable you to expose instance variables read-only.

> **mo.reina said:**
> 
Any other uses of setters and getters in python?

Yes, all typical property use cases apply, like doing sanity checks, propagating updates etc.

---

### Post by mo.reina on 2010-09-27
> **Bachstelze said:**
> You use "setters" and "getters" because in OOP, the user (i.e. the programmer who will use your code, not the end-user) should not concern himself with how your class works.  The only thing that is of interest to him is the interface of the class: the functions he will actually use when writing his code.


ok but this is about convention and readability, not necessity.  

in ruby for example you have to either set setters and getters, or use attr_accessor, or you cannot access the variables.  in python this isn't necessary... yet some people speak of using the property built-in or decorators IN PLACE of setters and getters (i think in this instance they are referring to code sanity, as raf_kig noted), which is kind of confusing since you don't need to use setters and getters in the first place.

i'm sure i'm missing something here, but i'm not quite sure what it is...

this [article]("http://tomayko.com/writings/getters-setters-fuxors") speak of never using setters and getters unless you absolutely need them... when would this be?  aside from, as we noted earlier, setting certain variables to read-only...

---

### Post by dv3500ea on 2010-09-27
In ruby, [color=blue]attr_accessor[/color] is equivalent to using both [color=blue]attr_reader[/color] and [color=blue]attr_writer[/color].

> **mo.reina said:**
> attr_accessor in ruby is used to render the variables in the class instance readable and writable. [True/False]

Strictly speaking, this is false, but it has the same effect as what you are describing. In ruby, all instance variables (variables that begin with '@') are readable and writable but **only** from within instance methods of the object.

```

class Foo
    def initialize(name)
        @name = name
    end
    #reader for @name
    #equivalent to using
    #attr_reader :name
    def name
        @name
    end
    #writer for @name
    #equivalent to using
    #attr_writer :name
    def name= name
        @name = name
    end
end
bar = Foo.new 'David'
puts bar.name #outputs: David
bar.name = 'John'
puts bar.name #outputs: John

```

This example should be fairly self explanatory. Using attr_* automatically creates these getter/setter methods so that you don't have to type out the same code over and over again for each of your instance variables.

---

### Post by Bachstelze on 2010-09-27
This snippet illustrates it:

```
class Contact(object):

    def __init__(self, first_name=None, last_name=None, 
                 display_name=None, email=None):
        self.first_name = first_name
        self.last_name = last_name
        self.display_name = display_name
        self.email = email

    def print_info(self):
        print self.display_name, "<" + self.email + ">"            

    def set_email(self, value):
        if '@' not in value:
            raise Exception("This doesn't look like an email address.")
        self._email = value

    def get_email(self):
        return self._email

    email = property(get_email, set_email)

```

Normally, you do not need getters/setters in Python, because you can modify the class members directly.  However, what if you want, when someone tries to modify a member, to do something before it is actually modified (here, check whether the email address is valid)?

That's why in other languages you have to use getters and setters, because if you write a class and realize afterwards that you need to do something before modifying a member, you will have to rewrite a lot of it, and break backwards-compatibility.

Not so in Python: you can write your setter, and tell Python that you want it to call your setter whenever someone tries to modify a member, and it will all be transparent to the user: they will still modify the member the same way they did before the change.

---


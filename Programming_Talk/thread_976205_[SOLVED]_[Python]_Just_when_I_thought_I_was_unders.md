---
title: "[SOLVED] [Python] Just when I thought I was understanding OOP....."
date: 2008-11-09
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-09
Hey,
I've been performing mental aerobics the past few weeks with Object-Oriented Programming in Python. I've been doing [this]("http://pclc.pace.edu/~bergin/KarelJava2ed/Karel%2B%2BJavaEdition.html") in school, so I was beginning to feel good about the concepts, and after careful examining of tutorials and Pyc-Tac-Toe, I was beginning to feel good about actually using it.
So I decided to make a simple program, since thinking and writing are very separate matters, and I came up with:
```
class Person(self, name, gender):
	def __init__():
		self.name = name
		self.gender = gender
	def sayHi(self):
		print "Hello, my name is %s and I'm a %s" %(self.name, gender)
me = Person("Timmy", "boy")
me.sayHi()
```
and was kindly greeted by this:
> timmy@Stanway01:~/Desktop$ python oop.py
Traceback (most recent call last):
  File "oop.py", line 1, in <module>
    class Person(self, name, gender):
NameError: name 'self' is not defined

What does it mean, "'self' is not defined"? I thought the point of self was that you *didn't* explicitly define it--Python itself took care of all the details of self for you.

I suppose it's very possible that I'm on the wrong end of the stick here... :-/

Thanks

---

### Post by Greyed on 2008-11-09
def __init__(**self**):

Also, the class definition does not need self.  Only the methods do.

---

### Post by Greyed on 2008-11-09
Wow, even I am out of practice.  Haven't seriously coded in Python nor classes in about 4 months.

[php]
class Person():
        def __init__(self, name, gender):
                self.name = name
                self.gender = gender
        def sayHi(self):
                print "Hello, my name is %s and I'm a %s" %(self.name, self.gender)
me = Person("Timmy", "boy")
me.sayHi()
[/php]

The class definition is looking for parent classes.  You're not passing variables there.  You're passing them to __init__ since that is what is called when your constructing a class.  Also you missed self on gender in sayHi().

---

### Post by fiddler616 on 2008-11-09
> **Greyed said:**
> def __init__(**self**):

Also, the class definition does not need self.  Only the methods do.
Edit: Please ignore all of this.
Er...
```
class Person(self, name, gender):
    def __init__(self):
#snip
```returns> 
python oop.py
Traceback (most recent call last):
  File "oop.py", line 1, in <module>
    class Person(self, name, gender):
NameError: name 'self' is not defined
and
```
class Person(name, gender):
    def __init__(self):
```returns> 
python oop.py
Traceback (most recent call last):
  File "oop.py", line 1, in <module>
    class Person(name, gender):
NameError: name 'name' is not defined


---

### Post by fiddler616 on 2008-11-09
> **Greyed said:**
> Wow, even I am out of practice.  Haven't seriously coded in Python nor classes in about 4 months.

[php]
class Person():
        def __init__(self, name, gender):
                self.name = name
                self.gender = gender
        def sayHi(self):
                print "Hello, my name is %s and I'm a %s" %(self.name, self.gender)
me = Person("Timmy", "boy")
me.sayHi()
[/php]The class definition is looking for parent classes.  You're not passing variables there.  You're passing them to __init__ since that is what is called when your constructing a class.  Also you missed self on gender in sayHi().
Oh, that makes sense. Thank you very much.

---

### Post by Quikee on 2008-11-09
As Greyed said.. but to be more specific what is wrong here is the fixed Person class:

[PHP]class Person(object):
	def __init__(self, name, gender):
		self.name = name
		self.gender = gender
	def sayHi(self):
		print "Hello, my name is %s and I'm a %s" %(self.name, gender)
me = Person("Timmy", "boy")
me.sayHi()[/PHP]

In the class "head" you define the inheritance information. In __init__ method you define which parameters it will accept at creation / construction. 

I also suggest that before jumping to conclusions - check if everything is as it is supposed to be. :)

EDIT: Hm.. I'm slow. ;)

---


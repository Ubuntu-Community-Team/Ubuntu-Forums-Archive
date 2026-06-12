---
title: "Question about Python (or maybe Perl)"
date: 2005-05-26
forum: Programming Talk
---

### Post by DirtDawg on 2005-05-26
I've been wondering if there's any way in Python to override methods on an instance level. Or do I need to create a new class every time I want to override a method?
For a (lame) example:
```

class donut:
     def eat(self):
          print "You eat the tasty pastry and it fills you up. "
          sugarRush()  ##an arbitrary function. Just pretend it does something

lemondonut= donut()

###RUN PROGRAM ###
>>> lemondonut.eat()
You eat the tasty pastry and it fills you up. 
You suddenly feel craaaaaazy!!

```
Now let's say I want to make a donut that causes the sun to explode when you eat it:
```

explodingdonut= donut()
def explodingdonut.eat(self):
      print "The sun explodes, incinerating all life in the solar system. "
      nova() ##arbitrary function 2
### This nor any similar syntax works (I've tried) ###

```

I hope this makes some kind of sense. Is there any way to do this in Python or am I out of luck? 

Further, if it's not possible in Python, is it possible in Perl? (I've intentionally avoided learning Perl due to what I consider some of the ugliest (and scariest) syntax ever devised)

This post is not a "flamer" post or a "troller" or whatevcer else those intentionally controversial posts are called, I would  just like some feedback please. Any other simple language (i.e NOT C++) suggestions would be welcome. 

Thank you!

---

### Post by LordHunter317 on 2005-05-27
I don't know any object oriented language where overriding methods is possible on a per-instance basis.  This includes Python and Perl's psuedo-OOP.

The closest I can think of is anonymous classes in Java or anonymous methods in C#.  Perhaps D's closures have similar behavior.  But with these, you're still defining a class, it's just at the point of instantiation, instead of with a seperate declaration.

Having to create a subclass that overrides the parent's method is a good thing.  It's how OOP works.  

C++ isn't complex, BTW.  The STL just doesn't coddle you and expect you have an understand of computer science concepts (or a willingness to learn).

---

### Post by vague- on 2005-05-27
```

>>> class Test:
...     def test(self):
...             print "Test" + self.end
... 
>>> def stillTest(self):
...     print "Still test" + self.end
... 
>>> t = Test()
>>> t.end = "ing!"
>>> t.test()
Testing!
>>> import new
>>> t.test = new.instancemethod(stillTest, t, Test)
>>> t.test()
Still testing!

```

Although I have a vague understanding of how Perl OO works, I have never used it.  Perl gives you really low-level access to how it behaves for the class, though.  Due to this I would think that it is possible.  Even if it may mean editing the lookup table for the class yourself.

---

### Post by ltmon on 2005-05-27
I can think of a way to do that is in Ruby, where you can pass blocks and procs around

```

class Donut
  def eat(proc = Proc.new {puts "This is normal"})
      proc.call
  end
end

donut = Donut.new
donut.eat     # this will print "This is normal"
donut.eat(Proc.new {puts "This is strange"})  # this will print "This is strange"

```

(No guarantees that this runs... but something like it can be done)
 
With a bit of factoring you could have an instance where you set the proc to call on a certain method on a per instance basis.

It's probably bad design though, there is little reason to use this method in most real applications.  It's also pretty confusing to whoever is reading the code.

I think Lisp can do similar things with lambda-functions or something like that... but it's a steep path to learn Lisp.  Ruby I can fully recomment -- I find it like a better Python.

---

### Post by wtd on 2005-05-27
```
 $ irb
irb(main):001:0> class Foo
irb(main):002:1>    def bar
irb(main):003:2>       "Wooble!"
irb(main):004:2>    end
irb(main):005:1> end
=> nil
irb(main):006:0> baz = Foo.new
=> #<Foo:0xb7d1c194>
irb(main):007:0> baz.bar
=> "Wooble!"
irb(main):008:0> def baz.bar
irb(main):009:1>    "Ninja!"
irb(main):010:1> end
=> nil
irb(main):011:0> baz.bar
=> "Ninja!"
irb(main):012:0>
```

---

### Post by ltmon on 2005-05-27
Wow, I learn something new about Ruby every day.

Cheers,

L.

---

### Post by DirtDawg on 2005-05-28
You guys are great, thank you. As a whole, what I'm hearing is that it's possible to override methods, but probably a bad idea in terms of design. 
This is good to know. 
The idea I had was to create a library of objects but allow people with little-to-no programming knowledge to replace methods in instances they create based on a predefined set of rules. I may abandon this idea if it proves too unpractical.
Special thanks to vague- who really nailed it. 
As for C++, it's true I don't understand computer science on any profound level and I'm in no hurry to learn (As an artists I've trained my brain for many years to ignore it's own left hemisphere). It's taken me the better part of a year just to read through "Learning Python" and grasp the ideas within. In other words, I kind of enjoy being coddled. As I read more and learn more, this is changing, but at a leisurely pace.
I keep hearing about Ruby. I may check it out. 
Again, thanks for taking the time to reply.

---

### Post by LordHunter317 on 2005-05-28
[QUOTE=DirtDawg]The idea I had was to create a library of objects but allow people with little-to-no programming knowledge to replace methods in instances they create based on a predefined set of rules.[/quote]Yeah, you can still do this.  You have them subclass and reimplement whatever they want.

Of course, Python, following Smalltalk OOP, doesn't give you a lot of control over what a user can/cannot override in a subclass.  Not that that's generally a super-great idea anyway.

---

### Post by cwaldbieser on 2005-06-04
OK, here is how you achieve the effect you were talking about in Python-- I think 2.4 might be required (this solution uses closures).

```
def instance_method(obj, func):
     def f(*args, **kwargs):
          func(obj, *args, **kwargs)
     return f
```

Now as to usage:

```
class Foo(object):
     def __init__(self, cookie):
          self.cookie = cookie
     def baz(self):
          print "Wheee!!!"

def bar(self):
     print "The magic cookie is %s." % self.cookie

>>> f = Foo('xyzzy')
>>> f.baz()
Wheee!!!
>>> f.baz = instance_method(f, bar)
>>> f.baz()
The magic cookie is xyzzy.
```

The Python Cookbook 2nd ed. recipie 20.8 also has an interesting technique that quietly subclasses the original class behind the scenes.

---

### Post by DirtDawg on 2005-06-04
[QUOTE=cwaldbieser]OK, here is how you achieve the effect you were talking about in Python-- I think 2.4 might be required (this solution uses closures).
.....
The Python Cookbook 2nd ed. recipie 20.8 also has an interesting technique that quietly subclasses the original class behind the scenes.[/QUOTE]


HA! What a great response. I see you can tell where I'm going with this. That's a slick piece of code too. Thank you. :)

---


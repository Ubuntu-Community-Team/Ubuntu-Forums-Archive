---
title: "Python: Why &quot;self&quot;?"
date: 2007-04-20
forum: Programming Talk
---

### Post by Ubuntist on 2007-04-20
Typing "self" over and over again when writing Python methods drives me crazy. What advantage derives from requiring self as an argument to each method and to indicate the scope of each member variable?

The only advantage I can see is that it eliminates the need for an additional reserved word "self," but that strikes me as a pretty small benefit.  I'd rather have an implicitly-defined "self" variable and a more convenient way of referring to a class's member variables, like prefixing them with a "." or a "@" as in Ruby.

Am I the only one bothered by "self"? Am I missing some other benefit?

---

### Post by AdamG on 2007-04-20
> **Ubuntist said:**
> Typing "self" over and over again when writing Python methods drives me crazy. What advantage derives from requiring self as an argument to each method and to indicate the scope of each member variable?

The only advantage I can see is that it eliminates the need for an additional reserved word "self," but that strikes me as a pretty small benefit.  I'd rather have an implicitly-defined "self" variable and a more convenient way of referring to a class's member variables, like prefixing them with a "." or a "@" as in Ruby.

Am I the only one bothered by "self"? Am I missing some other benefit?There actually *isn't* any "self" in Python. The actual letters s-e-l-f are used by common convention, but it has no implicit meaning; the significant thing is that the object itself if the first parameter passed to each instance method. You could just as easily call it this, or my, or i - just def instanceMethod(my,*args) instead of (self,*args).

Personally, I like it. Go into a python shell and run "import this". It's apparently something from a mailing list years ago. The second line goes like this:

"Explicit is better than implicit."

Personally, I agree; I like Python because it's explicit, unambiguous and clear, but not wordy. 

In an unrelated area, it makes passing around objects when making GUIs very easy. When I'm working with a rather extensive GUI, I'll pass the object for, say, the parent frame to each of the notebooks tab frames. That allows each tab to call the frame's methods. I haven't worked enough with Ruby to know how ackward that is, but in Python it's just a matter of passing "self" as a variable to the constructor of the notebook frame. (of course, it doesn't copy the entire object for each notebook; it simply passes a pointer reference that still performs very fast)

I have no idea if it's Pythonic or whatnot, but it's very convenient :)

---

### Post by pmasiar on 2007-04-20
> **Ubuntist said:**
> Typing "self" over and over again when writing Python methods drives me crazy. ... I'd rather have an implicitly-defined "self" variable and a more convenient way of referring to a class's member variables, like prefixing them with a "." or a "@" as in Ruby.

Am I the only one bothered by "self"? Am I missing some other benefit?

Yes, you are the only one :-)

Seriously: you ask not only for reserved word, but also for special syntax. Special way to access object attributes inside that object, different from accessing the same atribute from outside. 

If you are lazy to type 'self', use 's' as first parameter, or 'x' or 'it'. That's the beauty of Guido's solution: it does not force his preferences on you, call 'self' whatever you want. 'self' is just commonly used, but it might be any valid name.

AdamG mentioned **Explicit is better than implicit** mantra. There is also other mantra related to the question: **Special cases aren't special enough to break the rules**

To get whole zen, type at python prompt: import this

For another easter egg, try: from __future__ import braces :-)

---

### Post by Wybiral on 2007-04-20
> **pmasiar said:**
> For another easter egg, try: from __future__ import braces :-)

Ha ha ha... I happen to like braces.

> it does not force his preferences on you

Indentation if a preference... What if I'd rather use braces?

---

### Post by pmasiar on 2007-04-20
Then you cannot use Python - try Ruby maybe. Seriously, do try some dynamically typed language. For me, it was life-changing experience.

But even with braces, you for sure do use some coding/intendation standard, right?

---

### Post by Wybiral on 2007-04-21
Yeah, I'm very strict about my indentation actually. That's not why I prefer braces, it's because it makes things look clearer...

```

function blah()
{
   some_loop
   {
      do something!
   }
   do something else
}

```

```

function()
   some loop
      do somethin!
   do something else

```

(edit: I was wrong about something)

Really, I do use python. Mostly when I want to lots of string searching and manipulating, but other then that, C is just as easy for me. I also do a lot of 3d graphics, and the difference between python and C in that areas is minimal for ease of programming, but the performance difference is not as minimal for detailed dynamic scenes.

As I've said before, it's all about what you're doing... C suites a lot of my needs and interests. Python is something I use for either string manipulation that is too annoying to do in C, or to extend my C programs with scriptability. And it works for me.

---

### Post by yaaarrrgg on 2007-04-22
I don't really see the need for 'self' either  :)   To me, it seems more like a hack than anything else.   Perl uses a similar trick to bolt on OOP on the top of a non-OOP language.   

What would have made more sense would be ...  if a variable is defined in the class scope, it  automatically becomes a member variable, and masks outside definitions.

One downside I've noticed is it makes converting a script to an object needlessly tedious.

---

### Post by Mirrorball on 2007-04-22
> **yaaarrrgg said:**
> What would have made more sense would be ...  if a variable is defined in the class scope, it  automatically becomes a member variable, and masks outside definitions.
Then you wouldn't be able to add a new method to a class after it has already been defined. For instance:
```

class AClass:
  def __str__(self):
    return 'AClass object'

def say_hello(object):
  print 'Hello from', object

AClass.say_hello = say_hello

```

---

### Post by yaaarrrgg on 2007-04-23
> **Mirrorball said:**
> Then you wouldn't be able to add a new method to a class after it has already been defined. For instance:
```

class AClass:
  def __str__(self):
    return 'AClass object'

def say_hello(object):
  print 'Hello from', object

AClass.say_hello = say_hello

```

There's no other syntax that could express the same thought?  

I'd prefer a syntax like this (adding a self-referencial 'this' keyword, removing ':'):

```

class AClass
  def __str__()
    return 'AClass object'

def say_hello()
  print 'Hello from', this

AClass.say_hello = say_hello

```

AFAICT, the only real advantage of passing self around is perhaps it makes writing the Python interpretor simpler.

---

### Post by Mirrorball on 2007-04-23
But where does the *this* parameter of the say_hello function come from? It's not a proper function, it won't work outside the AClass class.

---

### Post by yaaarrrgg on 2007-04-23
> **Mirrorball said:**
> But where does the *this* parameter of the say_hello function come from? It's not a proper function, it won't work outside the AClass class.

Ah, I see what you're saying.... that makes sense.

I was thinking 'this' , by default, would just point to the entire application.  

This default might also be overridable on a global level though  like:

```

__this__ = SomeClass

```

Then in the context of another class, it gets reassigned to a pointer to that class.

Although, to be honest, if I made all the changes I wanted to, it wouldn't be Python anymore. :)

---


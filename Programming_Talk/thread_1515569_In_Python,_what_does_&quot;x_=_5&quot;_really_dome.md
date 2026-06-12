---
title: "In Python, what does &quot;x = 5&quot; really do/mean?"
date: 2010-06-22
forum: Programming Talk
---

### Post by narnie on 2010-06-22
Hi,

I'm a great scripter, but just learning programming (using Python).

I'm very much a newbie at this, so please be patient as I'm sure these will seem so basic a questions and may seem stupid to those experienced.

I'm reading a python book right now that has me thinking about variables.

As the title says, what does "x=5" really mean?

What is the "5" being assigned to? Is "x" considered an "instance" of "int?"

If I do this:
```

>>> class test(int):
    pass

>>> x=test(5)
>>> x
5
>>> 
```Then x here is an instance of class test(), a subclass of int.

But with int, you can do x=5.

If I do that after the above code, then x is no longer an instance of test() but is a variable of type int().

In the above, what is the 5 actually being assigned to in the instance of test()?

I have accessed it by defining a class and doing this just messing around:

```

>>> class test2(int):
    def value(self):
        print self
        self += 1
        print self

        
>>> x=test2(5)
>>> x
5
>>> x.value()
5
6
>>> x
5

```Why doesn't the value of x change to 6 in the above example? I'm I "redefining" self in the value() method to no longer reflect what is self in the instance?

Also, can I "hijack" what x=5 means to to add my own methods, but it still behave like x=5. What I mean might be explained by this code:

```

#do whatever code here to "hijack" int()

>>> x=5
>>> x
5
>>> x.make_negative
>>> x
-5
>>> x=-2
>>> x
-2
>>> x.make_negative
>>> x
2

```Or something like that?

If there is no way to do that and we go back to my original subclass definition, how do I change the value of the instance of the class to another value?

In:```
>>> x=5
>>> x += 1
>>> x
6
```How does the value of x become incremented internally? What magic is happening behind the scenes?

Say I want to do what is verboten in Python. Make in C-like incrementor like this.

```

>>> class Incrementor(int):
    def incAfter (self): # equivalent of x++
        #do whatever to access the value of instance
        return VALUE_OF_INSTANCE # as in x=Incrementor(5)
        VALUE_OF_INSTANCE += 1 # not quite sure how to do this to make it increment after returning the value (perhaps it is imporssible). Help here would be appreciated, too.
    def incBefore(self): # equivalent of ++x
        VALUE_OF_INSTANCE += 1
        return VALUE_OF_INSTANCE # as in x=Incrementor(5)

```So that I could do something like this:

```

>>> x = Incrementor(5)
>>> x
5
>>> print x.incAfter()
5
>>> x
6
>>> print x.incBefore()
7
>>> x
7

```

Helping me with the concepts would really go a long way for me. Any help would be greatly appreciated.

Thankfully,
Narnie

---

### Post by Bachstelze on 2010-06-22
Your mistake is here:

> How does the value of x become incremented internally? What magic is happening behind the scenes?

It does not. A new object vith value 6 is created, and name x is bound to that object. int is an immutable type, meaning that once an object has been created, its value may not change. Otherwise you could as well do [font=monospace]0 = 1[/font].

As for your Incrementor class, you absolutely do not need to (and really, can't) make it inherit from int. Just create a base class with an int attribute:

```
class Incrementor(object):
    def __init__(self, value=0):
        self.__value = value

    def incAfter(self):
        # Can't do anything after the function returns!
        oldvalue = self.__value
        self.__value += 1
        return oldvalue

    def incBefore(self):
        self.__value += 1
        return self.__value
```

---

### Post by StephenF on 2010-06-22
> **narnie said:**
> Hi,
```

>>> class test2(int):
    def value(self):
        print self
        self += 1
        print self

        
>>> x=test2(5)
>>> x
5
>>> x.value()
5
6
>>> x
5
```Why doesn't the value of x change to 6 in the above example? I'm I "redefining" self in the value() method to no longer reflect what is self in the instance?

The instance is passed into the value method as the first argument and bound to local variable self.

When you call self += 1 this calls the __add__ method of test2 which is inherited from int so you get the equivalent:
```

self = int.__add__(self, 1)

```
Which assigns an int that is the sum of self and 1 to local variable self thus depriving the remaining code in the method of any opportunity to interact with the instance.

---

### Post by narnie on 2010-06-22
> **StephenF said:**
> The instance is passed into the value method as the first argument and bound to local variable self.

When you call self += 1 this calls the __add__ method of test2 which is inherited from int so you get the equivalent:
```

self = int.__add__(self, 1)

```
Which assigns an int that is the sum of self and 1 to local variable self thus depriving the remaining code in the method of any opportunity to interact with the instance.

StephenF,

Thank you for letting me know how the += operator works internally. This makes sense to and is helping my (early) understanding of what is going on.

Gratefully,
Narnie

---

### Post by narnie on 2010-06-22
OK, both of the answers above were very helpful, and I know I asked a lot in one post.

I'm curious now what exactly "x" is in:

```

>>> x = 5
>>> x
5
```

Why is "x" callable (if that is the right word) without adding () as in:

```
>>> x()
5
```

Can I duplicate this in my own class so I could do something like:

```

>>> # whatever code necessary to make a int variable bind to my function and use my additional methods
>>> x=5
>>> x
5
>>> x.incAfter() # now I can use my method on this new I have defined
>>> x # and I can call my redefined variable without "()" at the end.
6

```

If not, how does x=5 work in the first place?

Cheerio,
Narnie

---

### Post by -grubby on 2010-06-22
> **narnie said:**
> [...]

Consider this:

```

>>> x = 5
>>> x
5
>>> x.__repr__()
'5'
>>> repr(x)
'5'
>>> class Something:
...     def __repr__(self):
...             return "Cheese!"
... 
>>> Something()
Cheese!
>>> repr(Something())
'Cheese!'

```

---

### Post by Can+~ on 2010-06-22
> **narnie said:**
> OK, both of the answers above were very helpful, and I know I asked a lot in one post.

I'm curious now what exactly "x" is in:

```

>>> x = 5
>>> x
5
```

Why is "x" callable (if that is the right word) without adding () as in:

```
>>> x()
5
```

Duck-typing my friend. Asking "x" in the interactive console, will ask for the __repr__ method (as the poster above me pointed out), and the terminal prints it pretty (without string quotation marks).

On the other hand, callable objects have the __call__ method defined, so you could easily build an hybrid:

[PHP]>>> class weirdo(object):
...     def __repr__(self):
...             return "Foo"
...     def __call__(self):
...             print "Bar"
... 
>>> x = weirdo()
>>> x
Foo
>>> x()
Bar[/PHP]

---

### Post by Bachstelze on 2010-06-22
> **narnie said:**
> 
Can I duplicate this in my own class so I could do something like:

```

>>> # whatever code necessary to make a int variable bind to my function and use my additional methods
>>> x=5
>>> x
5
>>> x.incAfter() # now I can use my method on this new I have defined
>>> x # and I can call my redefined variable without "()" at the end.
6

```

If not, how does x=5 work in the first place?

You can't do that, because when you do [font=monospace]x = 5[/font], the previous "contents" of the variable x are completely forgotten, and some new content (in this case, a plain int with value 5) replaces it.

What you can do is, instead of doing [font=monospace]x = 5[/font] to assign a new "value" to your object, do something like [font=monospace]x.setValue(5)[/font]:

```
class SuperInt(object):
    def __init__(self, value=0):
        self.__value = value

    def postInc(self):
        oldvalue = self.__value
        self.__value += 1
        return oldvalue

    def preInc(self):
        self.__value += 1
        return self.__value

    def setValue(self, value):
        self.__value = value

    def __repr__(self):
        return str(self.__value)
```

Then

```
>>> from SuperInt import *
>>> x = SuperInt(5)
>>> x
5
>>> x.postInc()
5
>>> x
6
>>> x.preInc()
7
>>> x
7
>>> x.setValue(4)
>>> x
4

```

---

### Post by narnie on 2010-06-22
> **-grubby said:**
> Consider this:

```

>>> x = 5
>>> x
5
>>> x.__repr__()
'5'
>>> repr(x)
'5'
>>> class Something:
...     def __repr__(self):
...             return "Cheese!"
... 
>>> Something()
Cheese!
>>> repr(Something())
'Cheese!'

```

Interesting. Thanks.

Where is the value of x, which is 5, stored? It is some variable within the class?

Narnie

---

### Post by narnie on 2010-06-22
> **Can+~ said:**
> Duck-typing my friend. Asking "x" in the interactive console, will ask for the __repr__ method (as the poster above me pointed out), and the terminal prints it pretty (without string quotation marks).

On the other hand, callable objects have the __call__ method defined, so you could easily build an hybrid:

[PHP]>>> class weirdo(object):
...     def __repr__(self):
...             return "Foo"
...     def __call__(self):
...             print "Bar"
... 
>>> x = weirdo()
>>> x
Foo
>>> x()
Bar[/PHP]

Ahh, IC. I tried using the __call__ method, but implemented it wrongly. I used "return" instead of "print." That is great for showing me the code. That makes sense.

Is there a way to make it where I can set x (which is an instance of my class) with just an equals sign? Like x=5 where x will reflect my class, not the int type?

Thanks again,
Narnie

---

### Post by narnie on 2010-06-22
> **Bachstelze said:**
> You can't do that, because when you do [font=monospace]x = 5[/font], the previous "contents" of the variable x are completely forgotten, and some new content (in this case, a plain int with value 5) replaces it.

What you can do is, instead of doing [font=monospace]x = 5[/font] to assign a new "value" to your object, do something like [font=monospace]x.setValue(5)[/font]:

```
class SuperInt(object):
    def __init__(self, value=0):
        self.__value = value

    def postInc(self):
        oldvalue = self.__value
        self.__value += 1
        return oldvalue

    def preInc(self):
        self.__value += 1
        return self.__value

    def setValue(self, value):
        self.__value = value

    def __repr__(self):
        return str(self.__value)
```

Then

```
>>> from SuperInt import *
>>> x = SuperInt(5)
>>> x
5
>>> x.postInc()
5
>>> x
6
>>> x.preInc()
7
>>> x
7
>>> x.setValue(4)
>>> x
4

```

I was thinking along these lines, and thank you for the help.

What I'm still not understand is how is it that x=5 binds 5 to x which is the int type. Can that be redefined or is it set too deeply in the language?

I know that if I did

```
>>> x=SomeType(5)
>>> x
5
>>> x=25
```

That it blows my binding to SomeType(). What I was wondering is can what x=5 means be "reimagined" such that x=5 doesn't point to the int type but to x=5 binds to my SomeType type?

These questions probably sound so stupid to someone who knows what they are doing, but I'm taking my baby steps right now.

Thanks to ALL who have helped me in this thread.

:)

Narnie

---

### Post by Can+~ on 2010-06-22
> **narnie said:**
> Ahh, IC. I tried using the __call__ method, but implemented it wrongly. I used "return" instead of "print." That is great for showing me the code. That makes sense.

Is there a way to make it where I can set x (which is an instance of my class) with just an equals sign? Like x=5 where x will reflect my class, not the int type?

Thanks again,
Narnie

Assignment is an exception to the overloading rule, as the left-most variable may not exist yet, and it would cause all kinds of side-effects, for example:

[PHP]
a = "Hello world"
a = 2
a = 3.14
a = AssingmentClass()
a = 5 # What would happen?[/PHP]

A class that overrides normal assignment, would destroy any future attempt to replace the variable. This is defined deeply in the language, to the point, that it's [not considered an operator]("http://docs.python.org/reference/lexical_analysis.html#operators").

---

### Post by narnie on 2010-06-23
> **Can+~ said:**
> Assignment is an exception to the overloading rule, as the left-most variable may not exist yet, and it would cause all kinds of side-effects, for example:

[PHP]
a = "Hello world"
a = 2
a = 3.14
a = AssingmentClass()
a = 5 # What would happen?[/PHP]

A class that overrides normal assignment, would destroy any future attempt to replace the variable. This is defined deeply in the language, to the point, that it's [not considered an operator]("http://docs.python.org/reference/lexical_analysis.html#operators").

Ok. Sounds definitive, and, frankly, was the answer I was expecting. Python just seems so flexible, a part of me wouldn't have been surprised if there might have been some way.

Thanks for the clarification :)

Narnie

---

### Post by narnie on 2010-06-23
> **Bachstelze said:**
> Your mistake is here:



It does not. A new object vith value 6 is created, and name x is bound to that object. int is an immutable type, meaning that once an object has been created, its value may not change. Otherwise you could as well do [font=monospace]0 = 1[/font].

As you explain it, it makes total sense. Just didn't know how that it was implemented. Wow, every single thing is an object!!! This is my first exposure to object-oriented coding. I figured it had to do with fact that int's, strings, etc are immutable as opposed to lists, dicts, etc. But x = 1 ; x += 1 getting rid of the original x=5 and replacing it with x=6 makes since with this mindset. Thank you so much for the clarification!

Is there any way to "redefine" what x=1 means to make my own methods without having to use __call__ in the class and doing a "x()" to get the value?

> 
As for your Incrementor class, you absolutely do not need to (and really, can't) make it inherit from int. Just create a base class with an int attribute:

```
class Incrementor(object):
    def __init__(self, value=0):
        self.__value = value

    def incAfter(self):
        # Can't do anything after the function returns!
        oldvalue = self.__value
        self.__value += 1
        return oldvalue

    def incBefore(self):
        self.__value += 1
        return self.__value
```

[COLOR="Red"]**_This should have posted earlier but it didn't for some reason. I add it here, but it should go after Bachstelze's original post._**[/COLOR]

I'm puzzled by not being able to class int. In the book I was reading, it talks about how this can be done and thus inherit all the attributes of said type (like int). Isn't int just a special case of the object class? Int isn't really that big a deal because there aren't a lot of methods to have to "reinvent."

Regardless, the above code works, and I understand it fully. (please forgive my newbieness, but I just last night playing around figured out the difference between return and print). In scripting, "echoing" is what you want to do to set a value equal to something (eg, x=`echo hello`) and return is more for error handling. I see how much different it is in Python.

Bachstelze, thank you so much for taking the time to clarify these things. It has really pointed me in the right direction and given me better insight and understanding of Python.

Thank you for holding a little (almost 40 year old) programmer boy's hand.

Gratefully,
Narnie

---

### Post by Bachstelze on 2010-06-23
> **narnie said:**
> 
I'm puzzled by not being able to class int. In the book I was reading, it talks about how this can be done and thus inherit all the attributes of said type (like int). Isn't int just a special case of the object class? Int isn't really that big a deal because there aren't a lot of methods to have to "reinvent."

You can of course subclass int. You can't, however, change the fact that int is immutable, which will render any class that inherits int immutable as well (someone correct me if I'm wrong). There are cases where subclassing int is useful, but not for what you want. So yes, what I should have said is "You can't achieve what you want by subclassing int, you have to find another way."

---

### Post by narnie on 2010-06-23
> **Bachstelze said:**
> You can of course subclass int. You can't, however, change the fact that int is immutable, which will render any class that inherits int immutable as well (someone correct me if I'm wrong). There are cases where subclassing int is useful, but not for what you want. So yes, what I should have said is "You can't achieve what you want by subclassing int, you have to find another way."

Ah, IC. Ok. I gotcha. Thanks for the clarification. I was thinking there might have been something undesirable or "unPython-like" in doing so. Of course, from what I've read, my whole exercise in making these incrementors is "unPython-like" but boy has it sure been a good teaching/training tool for me to get the bottom of some of this stuff.

Bachstelze, thank you for your patients. One day, I'm sure I'll look back on these questions and laugh at myself for how clueless I was.

Cheers,
Narnie

PS, just to be complete, I did this:

```
class Incrementor(object):
    '''
    this module attempts to mimic C-like x++ and ++x functions in Python
    '''
    def __init__(self, value=0):
        '''
        sets the value (default 0) when initialized

        example:

            >>> x = Incrementor (5)
        '''
        self.__value = value

    def __call__(self):
        '''
        allows the variable to be called

        example
            >>> x()
            5
        '''
        print self.__value

    def __repr__(self):
        '''
        allows the varible to be display without ()

        example:
            >>> x
            5
        '''
        return str(self.__value)

    def incAfter(self):
        '''
        increments the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.incAfter()
            5
            >>> print x
            6
        '''
        oldvalue = self.__value
        self.__value += 1
        return oldvalue

    def iA(self):
        '''
        shorthand for incAfter method
        '''
        return self.incAfter()

    def incBefore(self):
        '''
        increments the value of the object before returning the object value

        example:
            >>> print x
            5
            >>> print x.incBefore()
            6
            >>> print x
            6
        '''
        self.__value += 1
        return self.__value

    def iB(self):
        '''
        shorthand for incBefore method
        '''
        return self.incBefore()

    def decAfter(self):
        '''
        decrements the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.decAfter()
            5
            >>> print x
            4
        '''
        oldvalue = self.__value
        self.__value -= 1
        return oldvalue

    def dA(self):
        '''
        shorthand for decAfter method
        '''
        return self.decAfter()

    def decBefore(self):
        '''
        decrements the value of the object before returning the object value

        example:
            >>> print x
            5
            >>> print x.decBefore()
            4
            >>> print x
            4
        '''
        self.__value -= 1
        return self.__value

    def dB(self):
        '''
        shorthand for decBefore method
        '''
        return self.decBefore()

```

And it works the way I was thinking in my mind.

None could have been possible for me to "get" without all this help. Thanks again.

PPS

Please forgive the "childish" docstrings as I'm learning how to use them, too, even tho most of what I commented is pretty obvious from the code. It is really brilliant how easy it is to document in Python. I LOVE IT!!!

---

### Post by Bachstelze on 2010-06-23
Just a little something:

> **narnie said:**
> 
```
[snip]
    def incAfter(self):
        '''
        increments the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.incAfter()
            5
            >>> print x
            6
        '''
        oldvalue = self.__value
        self.__value += 1
        return oldvalue


```

This is not what this function does. It first stores the old value, then increments, then returns the stored old value. You cannot do anything in a function after it returns, it is very important that you understand this. When Python (or pretty much any other imperative language) encounters a [font=monospace]return[/font] statement, it returns the value, and then the programs returns at the point it was before the function was called. Any code that is after the return statement will *never* be executed. For example, this code:

```
def foo():
    return "foo"
    print "bar"

print "hello"
print foo()
print "world!
```

will print

```
hello
foo
world!
```

[font=monospace]bar[/font] will never be printed.

---

### Post by narnie on 2010-06-23
> **Bachstelze said:**
> Just a little something:



This is not what this function does. It first stores the old value, then increments, then returns the stored old value. You cannot do anything in a function after it returns, it is very important that you understand this. When Python (or pretty much any other imperative language) encounters a [font=monospace]return[/font] statement, it returns the value, and then the programs returns at the point it was before the function was called. Any code that is after the return statement will *never* be executed. For example, this code:

```
def foo():
    return "foo"
    print "bar"

print "hello"
print foo()
print "world!
```

will print

```
hello
foo
world!
```

[font=monospace]bar[/font] will never be printed.

Right. I noticed that in the code you helped me with. I didn't know how I was going to do that cuz I didn't think about assigning another variable and returning that after incrementing the original. Silly of me not to think of that. It would have been a solution I'd probably come up with in scripting.

I'm quite familiar with return as I write tons of scripts where I abstract with functions and new that in bash; a return is final for a function, and I assumed it was the same in Python (I'd been shocked and disappointed if it were any other way, actually). I just need to make sure I don't "box myself in" too much when trying to think Python instead of shell (bash/sh).

When I was writing that docstring, I was thinking how it looks like I was meaning I actually returned the value before incrementing it. I was meaning more for the transparency of the end user, because in use, it seems it returns the value, then increments it (when it is actually incrementing it, but returning another value in the temporary variable).

Bachstelze,  I thank you greatly for making sure I understand concepts, because I might misunderstand something. I am very impressed that you would take the time to read over the code AND the docstrings to make sure I got it right and am understanding it. It is very kind and thoughtful of you.

One day, when more experienced, I hope to return the favor to new Python programmers (can't wait for the day when I can do that). I try to help others when I can with scripts.

Ultimately, I am interesting in writing and understanding GUI utilization (esp PyGTK to make it look nice in gnome). The book I'm reading now goes into wxpython, which is OK, but doesn't integrate as nicely, but I hope that the concepts are transportable). The book I read before that didn't fit my learning style DID do pyGTK, but the author didn't really go into the details like I need to really understand things). Any ideas anyone for tutorials, etc?

With grateful thanks,
Nathan

---

### Post by The Cog on 2010-06-23
> I'm quite familiar with return as I write tons of scripts where I abstract with functions and new that in bash; a return is final for a function, and I assumed it was the same in Python (I'd been shocked and disappointed if it were any other way, actually).
Actually, there is:
```

>>> def foo():
...     try:
...             return "foo here"
...     finally:
...             print "finally here"
... 
>>> 
>>> print foo()
finally here
foo here
>>> 

```

The finally clause is guaranteed to be executed however the try block exits - even with an exception:

```
>>> def foo():
...     try:
...             return 99 / 0
...     finally:
...             print "finally here"
... 
>>> foo()
finally here
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 3, in foo
ZeroDivisionError: integer division or modulo by zero
>>> 

```

---

### Post by Bachstelze on 2010-06-23
> **The Cog said:**
> 
The finally clause is guaranteed to be executed however the try block exits - even with an exception:


But it will still execute before the function actually returns. ;) But yes, you could do

```
def incAfter(self):
    try:
        return self.__value
    finally:
        self.__value += 1
```

But it needs some slighty deeper understanding of Python, so I didn't use that.

---

### Post by narnie on 2010-06-23
> **The Cog said:**
> Actually, there is:
```

>>> def foo():
...     try:
...             return "foo here"
...     finally:
...             print "finally here"
... 
>>> 
>>> print foo()
finally here
foo here
>>> 

```

The finally clause is guaranteed to be executed however the try block exits - even with an exception:

```
>>> def foo():
...     try:
...             return 99 / 0
...     finally:
...             print "finally here"
... 
>>> foo()
finally here
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 3, in foo
ZeroDivisionError: integer division or modulo by zero
>>> 

```

Hey, that makes sense though. I just read about try/except & try/finally. I would expect finally to behave as you have shown. Seems like you and I might be cut from the same cloth. I, too, always like to find the exception to the rule, hehe.

Thanks for pointing it out,
Narnie

---

### Post by narnie on 2010-06-23
> **Bachstelze said:**
> But it will still execute before the function actually returns. ;) But yes, you could do

```
def incAfter(self):
    try:
        return self.__value
    finally:
        self.__value += 1
```

But it needs some slighty deeper understanding of Python, so I didn't use that.

I'd read about that as I posted above. I do understand it fully (I already made it through the chapter on exceptions, YEAH!).

I am probably just rushing something and I would have understood this if I'd wait. I just get a "burr under my saddle" and then find it difficult to keep going until I get an answer to my question, either by researching it (but my understanding of Python isn't good enough to do intelligent Google searching on a lot of things) or asking for help from that masters, as I have graciously gotten here.

Bachstelze, I feel stupid for not think of you solution, but am also glad to see the above solution as it just adds to my toolkit and solidifies my understanding of "what is going on."

Thanks all!

Narnie

---

### Post by Bachstelze on 2010-06-23
> **narnie said:**
> 
Bachstelze, I feel stupid for not think of you solution, but am also glad to see the above solution as it just adds to my toolkit and solidifies my understanding of "what is going on."

Honestly, that's not how I would've done it (which is also why I didn't do it like that in the first place). Python is not a language that strives for extreme concision or complicated constructs like that. Some say that a Python program must flow a little like a poem, so the first method is better Python IMO. Complicated constructs exist, but that doesn't mean you have to use them, or using them makes you a better programmer. Sometimes they are the only way to do what you want, but this is not the case here (and using them will probably not make your program any more efficient).

It is of course always useful to know that they exist and what they do, though. ;)

*EDIT:* Linus said a similar thing about [font=monospace]goto[/font]s in C:

> Any if-statement is a goto. As are all structured loops.

And sometimes structure is good. When it's good, you should use it.

And sometimes structure is _bad_, and gets into the way, and using a 
"goto" is just much clearer.

---

### Post by narnie on 2010-06-23
> **Bachstelze said:**
> Honestly, that's not how I would've done it (which is also why I didn't do it like that in the first place). Python is not a language that strives for extreme concision or complicated constructs like that. Some say that a Python program must flow a little like a poem, so the first method is better Python IMO. Complicated constructs exist, but that doesn't mean you have to use them, or using them makes you a better programmer. Sometimes they are the only way to do what you want, but this is not the case here (and using them will probably not make your program any more efficient).

It is of course always useful to know that they exist and what they do, though. ;)

*EDIT:* Linus said a similar thing about [font=monospace]goto[/font]s in C:

IC. I appreciate your helping me to think Python-ish. Not only do I want to learn how to code, but the WAY to code. I want to think like a Python coder. I want to be Guido-ish, I guess ;)

This discourse, I believe, helps me with this.

Again, thanks,
Narnie

---

### Post by narnie on 2010-06-23
Well, I was working on trying to really do a complete job and make multiplier and divider increments. I also hadn't read the code posted earlier about how to use the setValue  and __rept__ close enough to see what they were doing. Read a little more in my book and added the setValue and others, then saw Bachstelze's stuff and realized, hey, that is what I did. Made me feel good.

Anyway, here is my additional work for any. I have read that there are better way to do the same thing in Python using the enumerate function and itertools. However, for anyone wanting an iterator-like functionality who are new like me and don't know how to do it, hope this helps.

```

class Incrementor(object):
    '''
    this module attempts to mimic C-like x++ and ++x functions in Python
    '''
    def __init__(self, value=0):
        '''
        sets the value (default 0) when initialized

        example:

            >>> x = Incrementor (5)
        '''
        self.__value = value

    def __call__(self):
        '''
        allows the variable to be called

        example
            >>> x()
            5
        '''
        return self.__value

    def __repr__(self):
        '''
        allows the varible to be display without ()

        example:
            >>> x
            5
        '''
        return str(self.__value)

    def setValue(self, value):
        '''
        sets/changes the value of the object
        '''
        self.__value = value

    def incAfter(self, increment=1):
        '''
        increments the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.incAfter()
            5
            >>> print x
            6
        '''
        oldvalue = self.__value
        self.__value += increment
        return oldvalue

    def iA(self,increment=1):
        '''
        shorthand for incAfter method
        '''
        return self.incAfter(increment)

    def incBefore(self, increment=1):
        '''
        increments the value of the object before returning the object value

        example:
            >>> print x
            5
            >>> print x.incBefore()
            6
            >>> print x
            6
        '''
        self.__value += increment
        return self.__value

    def iB(self, increment=1):
        '''
        shorthand for incBefore method
        '''
        return self.incBefore(increment)

    def decAfter(self,increment=1):
        '''
        decrements the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.decAfter()
            5
            >>> print x
            4
        '''
        oldvalue = self.__value
        self.__value -= increment
        return oldvalue

    def dA(self, increment=1):
        '''
        shorthand for decAfter method
        '''
        return self.decAfter(increment)

    def decBefore(self, increment=1):
        '''
        decrements the value of the object before returning the object value

        example:
            >>> print x
            5
            >>> print x.decBefore()
            4
            >>> print x
            4
        '''
        self.__value -= increment
        return self.__value

    def dB(self, increment=1):
        '''
        shorthand for decBefore method
        '''
        return self.decBefore(increment)

    def multAfter(self, multiple=1):
        '''
        multiple of the value of the object before returning the object value

        example:
            >>> print x
            5
            >>> print x.multAfter(2)
            5
            >>> print x
            10
        '''
        oldvalue = self.__value
        self.__value *= multiple
        return oldvalue

    def multBefore(self, multiple=1):
        '''
        multiple of the value of the object after returning the object value

        example:
            >>> print x
            5
            >>> print x.multAfter(2)
            5
            >>> print x
            10
        '''
        self.__value *= multiple
        return self.__value

    def divAfter(self, divisor=1):
        '''
        value of the object divided by divisor after returning the object value

        example:
            >>> print x
            5
            >>> print x.divAfter(2.0)
            5
            >>> print x
            2.5
        '''
        oldvalue = self.__value
        self.__value /= divisor
        return oldvalue

    def divBefore(self, divisor=1):
        '''
        value of the object divided by divisor before returning the object value

        example:
            >>> print x
            5
            >>> print x.divBefore(2.0)
            2.5
            >>> print x
            2.5
        '''
        self.__value /=  divisor
        return self.__value
```

Python is brilliant!

Cheerio,
Narnie

---

### Post by StephenF on 2010-06-24
Suggested improvements (making classes like this is work).

According to.
[http://docs.python.org/release/2.5.2/ref/customization.html](http://docs.python.org/release/2.5.2/ref/customization.html)

__repr__ should return a string representation of the object. Ideally something that can be fed into exec() to reproduce another instance. In this case it should return for an incrementor with a current value of 5.
```

>>> i = Incrementor(5)
>>> repr(i)
'Incrementor(5)'

```
Consider adding __int__ and __float__ methods to your class to allow casting to those types. Consider adding a __str__ method to do what __repr__ currently does. :wink: 

The class could use some __add__, __iadd__, __radd__ type methods to enable mathematical operations to take place.

Also of note: incBefore is equivalent to __iadd__.

---

### Post by narnie on 2010-06-24
> **StephenF said:**
> Suggested improvements (making classes like this is work).

According to.
[http://docs.python.org/release/2.5.2/ref/customization.html](http://docs.python.org/release/2.5.2/ref/customization.html)

__repr__ should return a string representation of the object. Ideally something that can be fed into exec() to reproduce another instance. In this case it should return for an incrementor with a current value of 5.
```

>>> i = Incrementor(5)
>>> repr(i)
'Incrementor(5)'

```
Consider adding __int__ and __float__ methods to your class to allow casting to those types. Consider adding a __str__ method to do what __repr__ currently does. :wink: 

The class could use some __add__, __iadd__, __radd__ type methods to enable mathematical operations to take place.

Also of note: incBefore is equivalent to __iadd__.

Ah, I see. I haven't gotten to the __(r/i)add___ methods yet in my reading. I'll look them up. For the "simple" thing I'm trying to do, it works, yet I'm glad to know the above you said.

How do I find the "code" behind the __int__ and __float__ methods? That is something I have been wrestling with, too.

I read about importing inspect and doing an "inspect.getsourcelines . . ." but I'm thinking there has to be another way to see what is behind these types, classes, and methods as this doesn't always give the expected output (esp on functions I have made). How do I see what has been coded before me so that I might learn from it?

Thanks,
Narnie

---

### Post by StephenF on 2010-06-24
> **narnie said:**
> How do I find the "code" behind the __int__ and __float__ methods? That is something I have been wrestling with, too.

```

def __int__(self):
    # If self.value is definitely always an int just return self.__value.
    return int(self.__value)
def __float__(self):
    return float(self.__value)

```
I get the impression this is not the answer you were looking for.
> **narnie said:**
> 
I read about importing inspect and doing an "inspect.getsourcelines . . ." but I'm thinking there has to be another way to see what is behind these types, classes, and methods as this doesn't always give the expected output (esp on functions I have made). How do I see what has been coded before me so that I might learn from it?

I don't appear to be having any luck with that using (probably misusing) it from the interactive interpreter.

If you want to see the inner implementation, the source code to Python is available to download, but you should note most of it is written in C.

Many of the questions you ask are answered in the Python documentation section, Data Model. I recommend working your way through the basic tutorial first though.

---

### Post by Can+~ on 2010-06-24
Another thing:

Python has functions as [first-class citizens]("http://en.wikipedia.org/wiki/First-class_citizen"), therefore, you can avoid wrapping the "incAfter" with "iA", just by declaring the shorthand methods in the __init__

[PHP]class MyClass(object):
	
	def __init__(self, value=0):
		self.value = value
		
		# Shorthand
		self.ia = self.incAfter
	
	def incAfter(self, increment=1):
		oldvalue, self.value = (self.value, self.value+increment)
		
		return oldvalue[/PHP]

If you come from a C background, this works pretty much like a function pointer. It saves you lines and stack space.

Edit: Another thing

> **narnie said:**
> However, for anyone wanting an iterator-like functionality who are new like me and don't know how to do it, hope this helps.

Well, there's something to be said about iterator in python. As you've seen, python objects work by [duck-typing]("http://en.wikipedia.org/wiki/Duck_typing") (aka: if it quacks, it's a duck). Python iterators work also this way, although through the methods, __iter__ and next() ([read:iterables]("http://docs.python.org/dev/library/stdtypes.html#iterator-types")). The "Access the x_i element of, where i=1..n" comes from a more imperative paradigm.

You see that this idea is so basic to the roots of python, as the fact that you get facilities to generate iterable objects, like generator expressions and yield statement (which creates generator objects):

[PHP]generator = (i**2 for i in xrange(0,10))

print generator # produces <generator expression at ...>

for i in generator:
	print i, #0, 1, 4, 9 ...[/PHP]

[PHP]def yieldme():
	
	yield 5
	yield 10
	yield 2
	yield 3
	
	for i in xrange(10, 40, 3):
		yield i
	
	yield "END"

for i in yieldme():
	print i,[/PHP]

---

### Post by narnie on 2010-06-25
> **StephenF said:**
> ```

def __int__(self):
    # If self.value is definitely always an int just return self.__value.
    return int(self.__value)
def __float__(self):
    return float(self.__value)

```
I get the impression this is not the answer you were looking for.

I don't appear to be having any luck with that using (probably misusing) it from the interactive interpreter.

If you want to see the inner implementation, the source code to Python is available to download, but you should note most of it is written in C.

Many of the questions you ask are answered in the Python documentation section, Data Model. I recommend working your way through the basic tutorial first though.

StephenF,

Wow, I didn't even think about that. The other day, I was trying to find the source code behind the range() function to see how they implemented the second argument being the default argument(*args, and parsing it?). I figured it was just a function implemented in Python that I could just review. Didn't even think about that it might be implemented in the compile code of Python itself. Rats. so much for that. I don't know how to interpret C.

Thank for letting me know about the Data model section. I'll do as you suggest.

Regards,
Narnie

---

### Post by StephenF on 2010-06-25
> **narnie said:**
> I was trying to find the source code behind the range() function to see how they implemented the second argument being the default argument.
Well, if that's all you need to do...

Untested
```

def range(*args, **kwds):
    if kwds:
        raise TypeError("range() takes no keyword arguments")
    if not args:
        raise TypeError("range() expected at least 1 arguments, got 0")
    if len(args) == 1:
        start = 0
        stop = args[0]
        step = 1
    elif len(args) == 2:
        start, stop = args
        step = 1
    elif len(args) == 3:
        start, stop, step = args
    else:
        raise TypeError("range() expected at most 3 arguments, got %d" % len(args))

    # Rest of function follows.

```

Edit: To clarify, this is a reimplementation of part of the range function, not a snippet of genuine code. If you want to see how Python could be implemented entirely in Python there is the PyPy project which serves primarily as a test-bed for adding new features to the language.

---

### Post by narnie on 2010-06-25
> **StephenF said:**
> Well, if that's all you need to do...

Untested
```

def range(*args, **kwds):
    if kwds:
        raise TypeError("range() takes no keyword arguments")
    if not args:
        raise TypeError("range() expected at least 1 arguments, got 0")
    if len(args) == 1:
        start = 0
        stop = args[0]
        step = 1
    elif len(args) == 2:
        start, stop = args
        step = 1
    elif len(args) == 3:
        start, stop, step = args
    else:
        raise TypeError("range() expected at most 3 arguments, got %d" % len(args))

    # Rest of function follows.

```

Edit: To clarify, this is a reimplementation of part of the range function, not a snippet of genuine code. If you want to see how Python could be implemented entirely in Python there is the PyPy project which serves primarily as a test-bed for adding new features to the language.

Brilliant! That is along the lines of what I was thinking (that it likely used *args and then did as you did as I would have done in scripting). You tricked me, hehe, however. Because when I first opened it up and saw the code, I thought, now where/how did he get that. Then I read on and saw (even more impressively) that you took the time to sit down and write it yourself.

Good show! That is what I love about the Ubuntu/GNU/Linux/FLOSS community. Your altruism is greatly appreciated.

With thanks,
Narnie.

---


---
title: "[python] Simple class creation"
date: 2009-10-18
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-18
Hey,

I know that this is a very simple operation i just completely forgot how to do it. I know the code i have written below is full of errors but it is how i would like it to be written.

[php]
class Foo(object):
    def __init__(self):
        '''
            Some basic opperations
        '''
        
        self['var'] = "My Variable"
        
        
    def bar():
        print "FooBar"
        
f = Foo()
print f['var']
print f.bar()
[/php]

would output
>>My Variable
>>FooBar

Thanks
~Cody Woolaver

---

### Post by Can+~ on 2009-10-18
[PHP]self.var = "My Variable"[/PHP]

and

[PHP]print f.var[/PHP]

---

### Post by Bachstelze on 2009-10-18
This will work:

```
class Foo(object):
    def __init__(self):
        '''
            Some basic opperations
        '''

        self.var = "My Variable"


    def bar(self):
        print "FooBar"

f = Foo()
print f.var
f.bar()

```

It is, however, bad programming style to access class members outside of the class. A better version would be:

```
class Foo(object):
    def __init__(self):
        '''
            Some basic opperations
        '''

        self.__var = "My Variable"

    def printVar(self):
        print self.__var


    def bar(self):
        print "FooBar"

f = Foo()
f.printVar()
f.bar()

```

The two leading underscores in self.__var make the variable *private*, meaning that it can't be accessed from outside of the class:

```
firas@iori ~ % cat test.py
class Foo(object):
    def __init__(self):
        '''
            Some basic opperations
        '''

        self.__var = "My Variable"

    def printVar(self):
        print self.__var


    def bar(self):
        print "FooBar"

f = Foo()
print f.__var
f.bar()
firas@iori ~ % python test.py
Traceback (most recent call last):
  File "test.py", line 17, in <module>
    print f.__var
AttributeError: 'Foo' object has no attribute '__var'

```

---

### Post by Pyro.699 on 2009-10-18
I knew that one, but i was wondering it it would be possible to treat the object like a dictionary, but at the same time it acts as a class with functions.

---

### Post by unknownPoster on 2009-10-18
I'm not much of a python hacker to be honest. However, it may be possible to overload the '[]' operators.

Someone feel free to correct me if I'm wrong.

---

### Post by Can+~ on 2009-10-18
Every class has it's underlying __dict__ attribute, but that's not usually a good idea.

If you need a dictionary with functions, you can write easily:

[PHP]def myfunc(a, b):
    # ...

def myotherfunc(a, b, c):
    # ...

funcdict = \
{
    "somekey" : myfunc,
    "otherkey": myotherfunc,
    "lambdame": lambda x: x+1
}[/PHP]

---

### Post by Bachstelze on 2009-10-18
> **unknownPoster said:**
> I'm not much of a python hacker to be honest. However, it may be possible to overload the '[]' operators.

Someone feel free to correct me if I'm wrong.

*smacks forehead*

Of course, one could just make the class inherit from the dict class:

```
firas@iori ~ % cat test.py
class Foo(dict):
    def __init__(self):
        '''
            Some basic opperations
        '''

        self['var'] = "My Variable"



    def bar(self):
        print "FooBar"

f = Foo()
print f['var']
f.bar()
firas@iori ~ % python test.py
My Variable
FooBar

```

So your class will be a dict, with any additional methods you want to add to it.

---

### Post by unknownPoster on 2009-10-18
> **Bachstelze said:**
> *smacks forehead*


I assume that I said something wrong... I guess this is your interpretation of /facepalm

Care to explain, so that everyone including myself may benefit?

---

### Post by Pyro.699 on 2009-10-18
Oh wow! Thanks xD

I knew there had to be an easy solution.

Thanks guys
~Cody

---

### Post by Bachstelze on 2009-10-18
> **unknownPoster said:**
> I assume that I said something wrong... I guess this is your interpretation of /facepalm

Care to explain, so that everyone including myself may benefit?

Nope. ;) It means that what you said is right and that I should've thought about it earlier. You never smacked your forehead when you realize you forgot your keys inside your locked car, or something like that?

---

### Post by unknownPoster on 2009-10-18
> **Bachstelze said:**
> Nope. ;) It means that what you said is right and that I should've thought about it earlier. You never smacked your forehead when you realize you forgot your keys inside your locked car, or something like that?

Ok, good, I hate it when I give out false information. :)

Regardless, after some more research, in order to overload the '[]' operators you would have to do something similar to the following:

```


class foo:
    def __getitem__:
        #desired actions

    def __setitem__:
        #desired actions

```

---

### Post by Bachstelze on 2009-10-18
> **unknownPoster said:**
> Ok, good, I hate it when I give out false information. :)

Regardless, after some more research, in order to overload the '[]' operators you would have to do something similar to the following:

```


class foo:
    def __getitem__:
        #desired actions

    def __setitem__:
        #desired actions

```

Yeah, but here, since the '[]' won't be redefined, it's better to not reinvent the wheel and just import them from the dict class.

---

### Post by wmcbrine on 2009-10-18
[Gonna rethink my answer]

---

### Post by Can+~ on 2009-10-18
You can use the "property" method (on the object)

[PHP]class Foobar(object):
	
	def __init__(self):
		self.__foo = "bar!"
	
	def getfoo(self):
		return self.__foo
	
	def setfoo(self, value):
		self.__foo = value
	
	foo = property(getfoo, setfoo, "Who doesn't like foo?")

foobar = Foobar()

print foobar.foo
foobar.foo = "Not bar anymore"
print foobar.foo[/PHP]

So you can have a getter, a setter, but still have the commodity of not having to call them individually.

---


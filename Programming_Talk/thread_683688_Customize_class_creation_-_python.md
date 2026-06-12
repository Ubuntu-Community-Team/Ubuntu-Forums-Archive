---
title: "Customize class creation - python"
date: 2008-01-31
forum: Programming Talk
---

### Post by aquavitae on 2008-01-31
I have the following situation:
```

class Base(object):
   def __init__(self, **kwargs):
      pass

class Child(Base):
   def __init__(self, **kwargs):
      # Do something with kwargs, e.g. filter()
      Base.__init__(self, **kwargs)

```
Now I want to be able to create an instance of Child by calling```
Base('Child', **kwargs)
```  I've had a look at __metaclass__ and __new__, but I can't quite see how to do it.  Any suggestions?

---

### Post by LaRoza on 2008-01-31
<snip />

---

### Post by aquavitae on 2008-01-31
Thanks, but how does this help?  I understand how classes and inheritance work - I've programmed a lot in c++, but I haven't got my head around instance creation in python. I've read the python docs, but they don't give any good examples I can work from.

---

### Post by LaRoza on 2008-01-31
> **aquavitae said:**
> Thanks, but how does this help?  I understand how classes and inheritance work - I've programmed a lot in c++, but I haven't got my head around instance creation in python. I've read the python docs, but they don't give any good examples I can work from.

Oh, you want to create an instance of the class Child?

```

instance = Child(args)

```

<edit>
I don't think I understand what you want to do, it may be me, I just got up
</edit>

---

### Post by aquavitae on 2008-01-31
Maybe I didn't explain properly...

I want to create an instance of Child like this:
```
child_instance = Base('Child', answer=42)
```
The question is how I code Base to handle this.  I also want to keep the interface of Child as clean as possible because I want to be able to add lots of different types of child classes later without having to reproduce lots of code.

The idea is to use Base as a factory.

---

### Post by Wybiral on 2008-01-31
Is there any reason why is has to be "Base" that creates the instances? Couldn't you just use a function such as "BaseFactory" and dispatch from there?

---

### Post by Quikee on 2008-01-31
[PHP]

class Base(object):
	def __new__(cls, child,*a, **k):
		for sc in cls.__subclasses__():
			if sc.__name__ == child:
				return sc
		return cls
	
	def __init__(self, **kwargs):
		pass

class Child(Base):
	def __init__(self, **kwargs):
		#Do something with kwargs, e.g. filter()
		Base.__init__(self, **kwargs)
		print kwargs

c = Base('Child', answer=42)
print c[/PHP]

It is still incomplete..

Why do you need it? Looks like strategy pattern.

---

### Post by aquavitae on 2008-01-31
As far as the functionality is concerned, there's no reason why I can't use a function, but its neater to do it this way in my program because I have a number of other related classes (not inherited from Base) which I initialize by ```
instance = RelatedClass(some_args)
```. Also, because of the way I've designed the program, it makes sense when reading it and typing it to use ```
Base('specific subclass', arguments_specific_to_subclass)
```
Also, I'd just like to know how to do it, just because I'm curious ;)

---

### Post by aquavitae on 2008-01-31
Quikee, thanks for the suggestion - its exactly what I wanted!  Next question, can I control __init__ from within __new__?  What I mean is I that I have all the info for initializing the class in __new__.  All that needs to happen before Base.__init__ is called is some process on kwargs.  So the process would be this:
1. Base.__new__ is called
2. *k is changed as necessary, perhaps by a static method of sc
3. Base.__init__(self, **k) is called, but not explicitly by sc.__init__
This is done with the minimum extra or duplicate coding in the subclass, i.e. don't explicitly call Base.__init__.  In fact, since I know in advance how kwargs should be adjusted by sc, the code for the subclass could be as simple as:
```

class SubClass(Base):
    kwargs = {'answer'=42, 'question'='Why?'}

```
I can then use dict.update() to modify kwargs in Base.__new__

I don't know how much of this makes sense, just kinda thinking aloud...  If you can make sense of it, any suggestions?

---

### Post by pmasiar on 2008-01-31
To make those tricky design decisions, you may want to learn more about [Design_patterns](http://en.wikipedia.org/wiki/Design_pattern_%28computer_science%29) and read couple books. "Headfirst design patterns" was the first book which make sense for me :-)

---

### Post by Quikee on 2008-01-31
[PHP]class Base(object):
	@classmethod
	def doSomethingWithKeywords(cls, **keywords):
		keywords.update({'some' : 'something'})
		return keywords
		
	def __new__(cls, child, **k):
		for sc in cls.__subclasses__():
			if sc.__name__ == child:
				newK = sc.doSomethingWithKeywords(**k)
				superClass = super(cls, sc)
				instance = superClass.__new__(sc)
				return instance
		raise Exception, "Subclass not found!"

	def __init__(self, *a, **k):
		print "BASE init invoked"

class Child(Base):
	@classmethod
	def doSomethingWithKeywords(cls, **keywords):
		return keywords

class Subclass(Base):
	def __init__(self, *a, **k):
		print self.__class__.__name__, a, k

	
print Base('Child', answer=42)
print Base('Subclass', answer=10)[/PHP]

I don't know if I understand you right but this might be what you need. 

Generally manipulating with __init__ in __new__ is a pain. __init__ is automatically invoked if the instance is a instance of cls (or subclass obviously), otherwise __init__ should not be invoked.

---

### Post by aquavitae on 2008-02-01
Yes, thanks, that is close to what I want to do.  Is there any reason that this shouldn't work:
[php]
@staticmethod
def doSomethingWithKeywords(keywords)
   keywords.update({'some': 'something'})
[/php]
As keywords is passed as a dict (rather than as arguments), the reference can be changed so there is no need for a return.  Also, can I use @staticmethod or is there a reason to use @classmethod?  Sorry if these are stupid questions - I'm still learning python!

Hmm, another idea:
[php]
class Base(object):
    @classmethod
    def doSomethingWithKeywords(cls, keywords):
        keywords.update(cls.keywords)
        
    def __new__(cls, child, **k):
        for sc in cls.__subclasses__():
            if sc.__name__ == child:
                newK = sc.doSomethingWithKeywords(**k)
                superClass = super(cls, sc)
                instance = superClass.__new__(sc)
                return instance
        raise Exception, "Subclass not found!"

    def __init__(self, *a, **k):
        print "BASE init invoked"

class Child(Base):
    keywords = {'some': 'something'}
[/php]
Any comments?

---

### Post by aquavitae on 2008-02-01
Just been looking at the code you suggested in detail.  How do you pass newK to Base.__init__?

---

### Post by Quikee on 2008-02-01
If you define doSomethingWithKeywords as a classmethod the method can be inherited / overriden from superclass. Generally a class method  on a class behaves the same as instance method on the instance, which is not true for a static method. There is of course nothing wrong if you define doSomethingWithKeywords as staticmethod. There is also nothing wrong if you just input (by reference) the dictionary.

[PHP]Just been looking at the code you suggested in detail. How do you pass newK to Base.__init__?[/PHP]

I don't because the __init__ is called implicitly by super.__new__ and can't pass the changed values (I could call it manually when instance was created but then both methods would be called).. Your way might work because you manipulate the "k" dictionary.

---

### Post by aquavitae on 2008-02-02
Thanks. I tried editting k, but that didn't work - I think __new__ copies it and passes the copy to __init__.  But I got round it by calling doSomethingWithKeywords from Base.__init__ instead.

So does that mean the staticmethods aren't overriden by subclasses... or am I just getting confused?
[edit]
btw, yes it is a strategy pattern... I think. I have a bunch of classes with similar interfaces but completely different actions that all inherit from Base, but I want the implimentation hidden, so the client only needs to know about Base.
[/edit]

---


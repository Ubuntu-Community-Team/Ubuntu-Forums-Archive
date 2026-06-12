---
title: "Dynamic subclasses in Python"
date: 2008-04-08
forum: Programming Talk
---

### Post by [h2o] on 2008-04-08
Ok, so this is a tricky one.
In a project I have a baseclass Resource which have some subclasses for each Resource type: HttpFile and FtpFile

Now, I could easily figure out which one to use from the url:
```

if url.startswith('http'):
 foo = HttpFile(url)
else:
 foo = FtpFile(url)

```
But, I think it would be nice to be able to do
```

try:
 foo = Resource(url)
except ResourceError:
 print "Resource type not supported!"

```

I know I could create some kind of factory function to do it, but it would be much more fun to have an actual class. It seems like this is possible using metaclasses but I can't figure out how.

Any suggestions?

---

### Post by Quikee on 2008-04-08
Maybe this will help:

[PHP]import sys

class FooBase(object):
	def __new__(cls, *arguments, **keyword):
		for subclass in FooBase.__subclasses__():
			if subclass.platform == sys.platform:
				return super(cls, subclass).__new__(subclass, *arguments, **keyword)
		raise Exception, 'Platform not supported'
	
	def say_foo(self):
		print 'foo'

	def say_platform_foo(self):
		raise NotImplementedError

class WindowsFoo(FooBase):
	platform = 'win32'
	
	def say_platform_foo(self):
		print 'win32 foo'

class LinuxFoo(FooBase):
	platform = 'linux2'
	
	def say_platform_foo(self):
		print 'linux foo'

if __name__ == '__main__':
	foo = FooBase()
	foo.say_platform_foo()[/PHP]

The original example was using metaclass but I have modified it to show it can be done without messing with them and be equaly good and simple.

---

### Post by smartbei on 2008-04-08
Well, creating a function (Resource) that returns an instance of the correct class and throws an error if it wasn't found should be very simple, you would just need to use the if...else... you demonstrated above, and that would solve your problem (and would work just like your second example).

Since this is so much simpler and more readable (read: maintainable) I don't see why you would want to make it more complicated... Though it is fun :).

---

### Post by [h2o] on 2008-04-08
> **smartbei said:**
> Since this is so much simpler and more readable (read: maintainable) I don't see why you would want to make it more complicated... Though it is fun :).
Well, yes, that is my backup plan. But I was sort of hoping to learn something new, and to keep my ego happy :)

Quikee: I found that, and tried mucking about with it, but I could not manage to pass arguments to the constructor. I can't use a global variable like they do in that example.

---

### Post by Quikee on 2008-04-08
> **'[h2o] said:**
> 
Quikee: I found that, and tried mucking about with it, but I could not manage to pass arguments to the constructor. I can't use a global variable like they do in that example.

Of course you can:

[PHP]import sys

class FooBase(object):
	def __new__(cls, url, *arguments, **keyword):
		for subclass in FooBase.__subclasses__():
			if url.startswith(subclass.prefix):
				return super(cls, subclass).__new__(subclass, *arguments, **keyword)
		raise Exception, 'Prefix not supported'

class HttpFoo(FooBase):
	prefix = 'http'

class FtpFoo(FooBase):
	prefix = 'ftp'

if __name__ == '__main__':
	foo = FooBase('http://abc.com')
	print foo.prefix

	foo = FooBase('ftp://abc.com')
	print foo.prefix

	try:
		foo = FooBase('ssh://abc.com')
	except Exception, message:
		print message[/PHP]

> **smartbei said:**
> Well, creating a function (Resource) that returns an instance of the correct class and throws an error if it wasn't found should be very simple, you would just need to use the if...else... you demonstrated above, and that would solve your problem (and would work just like your second example).

Since this is so much simpler and more readable (read: maintainable) I don't see why you would want to make it more complicated... Though it is fun :).

It may be less readable - but also depends on the language - in smalltalk this is common. 

However I don't think it is any less maintainable as you clearly separate specifics and common things with an additional plus to never modify the common superclass if you add a new specific subclass (which means one less thing you can forget).

This is also known as a strategy pattern and it fits perfectly into this example.

---

### Post by Wybiral on 2008-04-08
If the problem is "how do I return an object of type A if this condition is true, otherwise type B" then I would just use a factory function, as opposed to having to loop over the subclasses and stuff. It just seems more readable and natural to me.

---

### Post by ZylGadis on 2008-04-09
I think the problem is rather "How do I instantiate an object of the type that matches this parameter." Now, I'm not aware of Python's specifics, but the language being what it is, it should be very easy to dynamically instantiate objects of a type passed as a string (also called reflection). The rest is just a mapping between the possible parameter values and the possible types - a string-to-string dictionary (or hash table, if you prefer). Or, alternatively, some function which returns the correct type name (as a string) based on the parameter value. In Java, for example, this could be done like so:

[PHP]
public Object getResource(String param, Map<String, String> dictionary) {
  String type = dictionary.get(param);
  Class c = Class.forName(type);
  return c.newInstance();
}
[/PHP]

Obviously I'm missing a whole lot of sanity checks and possible optimizations, but you get the idea. Not a single if-statement.

---

### Post by Quikee on 2008-04-09
> **Wybiral said:**
> If the problem is "how do I return an object of type A if this condition is true, otherwise type B" then I would just use a factory function, as opposed to having to loop over the subclasses and stuff. It just seems more readable and natural to me.

Well yeah.. maybe I would do the same in a situation like this but this approach has a clear advantage (a factory with a subclass loop is the same) - registration of a subclass is done automatically which is good if you have many of this classes as you don't have to maintain the list (you duplicate the list anyway as it is the same as the list of subclasses).

---

### Post by Quikee on 2008-04-09
> **ZylGadis said:**
> I think the problem is rather "How do I instantiate an object of the type that matches this parameter." Now, I'm not aware of Python's specifics, but the language being what it is, it should be very easy to dynamically instantiate objects of a type passed as a string (also called reflection). The rest is just a mapping between the possible parameter values and the possible types - a string-to-string dictionary (or hash table, if you prefer). Or, alternatively, some function which returns the correct type name (as a string) based on the parameter value. In Java, for example, this could be done like so:

[PHP]
public Object getResource(String param, Map<String, String> dictionary) {
  String type = dictionary.get(param);
  Class c = Class.forName(type);
  return c.newInstance();
}
[/PHP]

Obviously I'm missing a whole lot of sanity checks and possible optimizations, but you get the idea. Not a single if-statement.

Of course you would not use if..else in python either. But a string : class dictionary like:

[PHP]{"http" : HttpFoo,"ftp" : FtpFoo}[/PHP]

and ask if there is a class for my prefix.

But still - you have to register subclasses yourself in some way.

Also in Java a similar thing as my above example is not even possible to do "sanely" as Java reflection doesn't support gathering of all subclasses for a specific class - unless you iterate through all classes and ask if current class is a superclass of the searching class which is obviously a mess. ;)

---

### Post by [h2o] on 2008-04-09
Quikee: Thanks! That actually seems to do the trick! :guitar:

---

### Post by mssever on 2008-04-09
Registering subclasses is simple in Ruby; I don't know if Python can do something similar:
[php]#This is a snippet from one of my projects
class UnitsBase
  # The @@ means a class variable (shared across all instances)
  @@unit_types = []
  
  # This is a class method, which doesn't require an instance.
  # It's what does the magic.
  def UnitsBase.inherited(subclass)
    @@unit_types.push subclass
  end
  
  # reader method
  def UnitsBase.unit_types
    @@unit_types
  end
end

# some subclasses:
class Length < UnitsBase
  #do stuff
end

class Volume < UnitsBase
  #do stuff
end

# now, when we call UnitsBase.unit_types, we get
# [Length, Volume][/php]

---

### Post by [h2o] on 2008-04-09
Thanks for your time, but the problem is solved, and Ruby code is not very interesting since my question was specifically about Python.

---


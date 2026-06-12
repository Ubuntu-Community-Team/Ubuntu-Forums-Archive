---
title: "[Python] Appending new methods to an instance"
date: 2009-11-11
forum: Programming Talk
---

### Post by Can+~ on 2009-11-11
I noticed (and CptPicard too) that using:

[PHP]myinst.mymethod = function[/PHP]

Is valid, but it won't map the first argument as the "self" that a method has. So therefore, you can't add methods to a class in a simple way (except using the types module).

I realized that methods are also being interpreted by the "__setattr__" method inside objects, so I hacked a little something to handle new methods:

[PHP]class Foo(object):
	"""It does foo"""
	
	def __init__(self, bar):
		self.bar = bar
	
	def __setattr__(self, name, value):
		
		# Check if it's callable
		if hasattr(value, "__call__"):
			# It's a function, send to __setmeth__
			self.__setmeth__(name, value)
		else:
			# It's a normal attribute
			object.__setattr__(self, name, value)
	
	def __setmeth__(self, name, func):
		"""Method that defines how new methods are inserted"""
		
		# Create a closure with self
		def selfmeth(*args, **kargs):
			func(self, *args, **kargs)
		
		# Store it as a normal function
		object.__setattr__(self, name, selfmeth)[/PHP]

The method being passed is stored in a closure, that sets the self argument as the first one, therefore, working exactly like a method. Notice that the "__setmeth__" is not valid at all, it's not part of the standard language, I just wanted it to sound "pythonic".

With this you can:

[PHP]f = Foo(5)

def newmeth(self):
	print self.bar

f.newmeth = newmeth

f.newmeth()[/PHP]

Now, I wish python would implement something like __setmeth__ for real :(.

---

### Post by CptPicard on 2009-11-11
Nice thinking. Could probably be implemented as an extension or something. This is of course how it should work... I have been trying to figure out the rationale for the new behaviour in Python... I guess there is one but I have not figured it out yet :(

---

### Post by nvteighen on 2009-11-11
Hm... Here I refactored Can+~'s idea into a reusable class. Making this a module is a must...

```

# All credit to Can+~ of course ;)

class ExtensibleClass(object):
    """ Makes any children class be dynamically extensible. """
    
    def __init__(self):
        pass
    
    def __setattr__(self, name, value):
        
        # Check if it's callable
        if hasattr(value, "__call__"):
            # It's a function, send to __setmeth__
            self.__setmeth__(name, value)
        else:
            # It's a normal attribute
            object.__setattr__(self, name, value)
    
    def __setmeth__(self, name, func):
        """Method that defines how new methods are inserted"""
        
        # Create a closure with self
        def selfmeth(*args, **kargs):
            func(self, *args, **kargs)
        
        # Store it as a normal function
        object.__setattr__(self, name, selfmeth)

## TEST SUITE

if __name__ == "__main__":

    class Foo(ExtensibleClass):
        def __init__(self, bar):
            self.bar = bar

    f = Foo(5)

    def newmeth(self):
        print self.bar

    f.newmeth = newmeth

    f.newmeth()

## END OF TEST SUITE

```

---

### Post by CptPicard on 2009-11-11
This is, unfortunately, probably quite a performance killer considering how much you want to set things on objects in general... having to check for callability each and every time does not sound great. This would require actual patching of Python.. :(

---

### Post by Can+~ on 2009-11-11
> **CptPicard said:**
> This is, unfortunately, probably quite a performance killer considering how much you want to set things on objects in general... having to check for callability each and every time does not sound great. This would require actual patching of Python.. :(

Checking callability is looking if the __call__ is defined in the __dict__ of a class, which is just a dictionary test (should be O(1), in theory).

How frequently do you add new methods on runtime?

---

### Post by CptPicard on 2009-11-11
> **Can+~ said:**
> Checking callability is looking if the __call__ is defined in the __dict__ of a class, which is just a dictionary test (should be O(1), in theory).

Yeah but you're overriding __setattr__ and doing Python side stuff on assignment of anything, regardless of whether it is a callable or not. I don't know what the actual implementation of __setattr__ is but I might assume it works on the native side mostly...

But ok, assuming you just inherit when you need to... I can see the point in that light.

> 
How frequently do you add new methods on runtime?

Rarely... but it is a kind of core philosophical point of Python's design...

---

### Post by nvteighen on 2009-11-12
> **CptPicard said:**
> 
Rarely... but it is a kind of core philosophical point of Python's design...

What if I tell you Objective-C (in its Cocoa flavor... haven't found how to do this with GNUStep) has a pretty way to bind messages dynamically? Look at **class_addmethod** in action: [http://developer.apple.com/Mac/library/documentation/Cocoa/Conceptual/ObjCRuntimeGuide/Articles/ocrtDynamicResolution.html](http://developer.apple.com/Mac/library/documentation/Cocoa/Conceptual/ObjCRuntimeGuide/Articles/ocrtDynamicResolution.html)

I think any language focused on dynamic programming should have this feature.

---

### Post by maximinus_uk on 2009-11-12
I've used the python new module for doing this in the past:

[http://docs.python.org/library/new.html]("http://docs.python.org/library/new.html")
[http://diveintomark.org/archives/2003/01/27/dynamically_extending_apis]("http://diveintomark.org/archives/2003/01/27/dynamically_extending_apis")

But I see annoyingly this has been taken out in 3.0 and the docs refer me to a much less interesting types module:

[http://docs.python.org/library/types.html#module-types]("http://docs.python.org/library/types.html#module-types")

Grrr. :-( perhaps I should stick to scheme code after all...

---

### Post by wmcbrine on 2009-11-12
CptPicard, what is it that you're referring to as new behavior? I checked back to Python 2.3, and it still had this issue.

---

### Post by CptPicard on 2009-11-12
Gah!! Apologies. The method addition thing works on classes, not object instances:

```

Python 2.6.4 (r264:75706, Nov  2 2009, 14:38:03)
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> class MyClass:
...     def __init__(self):
...             self.x = 5
...
>>> def meth(self):
...     print self.x
...
>>> MyClass.foo = meth
>>> obj = MyClass()
>>> obj.foo()
5

```

I seemed to be under the impression it's all the same on instances too... it's not. But IMO it would be interesting if it did work.

---

### Post by Can+~ on 2009-11-12
Well, now we can do both, add methods to a class and an instance.

Although, I saw some flaw on my code: if you try to overload the __setattr__ on the class that is extending (java nomenclature) the "ExtensibleClass", then the __setmeth__ will never be called, unless the overload also considers this.

---

### Post by nvteighen on 2009-11-13
> **CptPicard said:**
> Gah!! Apologies. The method addition thing works on classes, not object instances:

If you think it well, adding a new method dynamically to an instance may offer a paradox... While the instance is considered by the compiler to be one of its class, is that instance after being dynamically modified still of the same class? And if not, of which class? These questions are really important, as they show the impact (no idea whether good or bad, we should try it on real code) such an idea has over the system of meanings in the code.

---

### Post by CptPicard on 2009-11-13
I have been thinking about this from the perspective of the type and interface of the function that is being added. I am actually becoming more of the opinion that if the __setattr__ would always capture any function like we expected it to, it would actually be slightly weird... after that, you could not store functions as *values* in a "normal" way in an object, they would always be hijacked as methods. Probably not good.

Also, if you look at how Python's types change in this attachment process ... a function is a function, a member function in a class is an unbound method, and this becomes at instantiation a bound method, which is very specifically a function with a different external interface plus an object instance reference. I think there are some type "meaning" conflicts of the kind you're referring to there if we just stick stuff onto an instance like we were trying to.

EDIT: In particular if function *f(self)* is attached to instance *x* by *x.g = f*, then *x.g* is most definitely no longer the same function! If we did *h = x.g*, then in particular this going through *x* will cause *h != f* as we're dealing with a bound method, which is a competely different function. QED.

---

### Post by Reiger on 2009-11-13
Gah. Are you Pythonics secretly wishing Python had real prototyping? :p

```

function obj() {
  this.place='world';
}
function foo() {
}
foo.prototype=new obj();
foo.prototype.hello = function() { alert("Hello "+this.place); };

var bar = new foo(); 
bar.hello(); // build up to "Hello world".

```

---

### Post by CptPicard on 2009-11-13
Reiger, interesting example. Yeah, it's possible that that is what we're after, in a sense the Python class is a kind of prototype object already... it just specifies what is copied over, but apparently instantiation is not quite that simple in Python...

---

### Post by nvteighen on 2009-11-13
> **Reiger said:**
> Gah. Are you Pythonics secretly wishing Python had real prototyping? :p

```

function obj() {
  this.place='world';
}
function foo() {
}
foo.prototype=new obj();
foo.prototype.hello = function() { alert("Hello "+this.place); };

var bar = new foo(); 
bar.hello(); // build up to "Hello world".

```

Or a Common Lisp-like multiple dispatch system would also satisfy us... :p

---

### Post by CptPicard on 2009-11-13
Or an appropriate shrubbery. One that looks nice. And not too expensive.

---

